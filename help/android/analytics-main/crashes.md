---
description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-description: 此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。
seo-title: 跟踪应用程序的崩溃情况
solution: Experience Cloud,Analytics
title: 跟踪应用程序的崩溃情况
topic: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '487'
ht-degree: 100%

---


# 跟踪应用程序的崩溃情况 {#track-app-crashes}

此信息可帮助您了解如何跟踪崩溃，以及处理假崩溃的最佳做法。

>[!TIP]
>
>应用程序崩溃情况将作为生命周期量度的一部分进行跟踪。在跟踪崩溃情况之前，请将库添加到您的项目并实施生命周期。有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

实施生命周期量度时，将在每个活动的 `OnResume` 方法中对 `Config.collectLifecycleData` 进行调用。在 `onPause` 方法中，将对 `Config.pauseCollectingLifeCycleData` 进行调用。

在 `pauseCollectingLifeCycleData` 中，设置了一个标志来指示正常退出。再次启动或恢复应用程序后，`collectLifecycleData` 会检查此标志。如果应用程序没有按照标志状态的指示成功退出，将在下次调用时发送 `a.CrashEvent` 上下文数据，并报告崩溃事件。

为了确保准确报告崩溃，您必须在每个活动的 `onPause` 方法中调用 `pauseCollectingLifeCycleData`。要了解为何必须这样做，请参阅下面的 Android 活动生命周期插图：

![](assets/android-lifecycle.png)

有关 Android 活动生命周期的更多信息，请参阅[活动](https://developer.android.com/guide/components/activities.html)。

*此 Android 生命周期插图由 [Android 开源项目制作和共享](https://source.android.com/)，并依据[创作共用署名 2.5 许可证](https://creativecommons.org/licenses/by/2.5/)中的条款使用。*

## 导致报告假崩溃的原因是什么？

1. 如果您在使用 IDE（如 Android Studio）进行调试，那么在应用程序处于前台时再次从 IDE 启动应用程序会导致崩溃。

   >[!TIP]
   >
   >再次从 IDE 启动应用程序之前，先将应用程序转入后台可避免此崩溃。

1. 如果应用程序的上一个前台活动转入后台，没有在 `onPause` 中调用 `Config.pauseCollectingLifecycleData();`，且应用程序被手动关闭或被操作系统终止，则下次启动时会导致崩溃。

## 应如何处理碎片？

碎片具有类似于活动的应用程序生命周期事件。但是，碎片不附加到活动就无法处于活动状态。

>[!IMPORTANT]
>
>您需要依赖生命周期事件，容器活动可以针对这些事件运行您的代码。这将由碎片的父视图来处理。

## （可选）实施活动生命周期回调

从 API 级别 14 开始，Android 允许对活动进行全局生命周期回调。有关更多信息，请参阅[应用程序](https://developer.android.com/reference/android/app/Application)。

您可以使用这些回调确保您的所有活动均可正确调用 `collectLifecycleData()` 和 `pauseCollectingLifecycleData()`。您需要只在主活动以及可能在其中启动您的应用程序的任何其他活动中添加此代码：

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

要使用 `Config.collectLifecycleData(Activity activity`、`Map<String` 和 `Object> contextData)` 随生命周期调用发送其他上下文数据，您必须覆盖该活动的 `onResume` 方法，并确保在手动调用 `collectLifecycleData` 之后再调用 `super.onResume()`。

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```

