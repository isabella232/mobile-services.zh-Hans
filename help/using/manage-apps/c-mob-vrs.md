---
description: 虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。这允许用户在一个报表包中维护数据，但像在不同报表包中一样管理数据。
seo-description: 虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。这允许用户在一个报表包中维护数据，但像在不同报表包中一样管理数据。
seo-title: 虚拟报表包
title: 虚拟报表包
uuid: 3f467design-43e7-4cd0-889b-89f8c61fbbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。这允许用户在一个报表包中维护数据，但像在单独的报表包中一样管理数据。

使用VRSS的应用程序执行的操作与使用常规报告套件的应用程序相同，但管理下列功能除外：

* 处理规则
* evar/prop/listvar/event
* 启用时间戳选项
* 维度标志（生命周期、位置等）
* 分类

这些值在可父报表包中进行管理，并与属于同一父报表包的 VRS 共享。

可以在Adobe Mobile Services UI中独立于父报表包访问下列区域：

* 配置文件
* 管理目标点
* 管理链接目标
* 管理回发
* 消息链接
* 客户获取

VRS可以帮助您完成以下任务：

* 限制数据访问

   某跨国公司拥有一个应用程序，可以将数据发送到所有地理位置的报表包。但是，公司希望限制一个地区的商业用户在另一地区查看数据。该公司的管理员可以创建一个VRS，按区域划分用户，并仅向管理该区域的商业用户授予VRS权限。

   此限制可阻止业务用户查看与其地区无关的数据。例如，EMEA中的业务用户无需查看APAC区域的数据。

* 允许控制应用内/推送消息、位置POIS、获取和回回，同时所有数据都发送到一个报告套件。

   某跨国公司希望将所有数据发送到适用于所有地理位置的同一报表包。但是，公司希望每个地区的营销团队都能处理自己的应用程序内/推送消息。该公司的管理员可以创建区域VRSS，每个团队都可以基于该VRS管理自己的应用程序。

   地区性团队可使用 VRS 的配置文件来构建应用程序。数据将发送到父报表包，但应用程序内/推送消息、位置POI、获取和回回是在从VRS创建的应用程序中控制的。

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>只有Adobe Analytics管理员可以在Adobe Analytics中创建和修改虚拟报告套件。To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

每个 VRS 都具有一个唯一的 ID。要在Adobe Mobile Services UI中查看父报表套件ID，请在“管理应用程序设置”页面上，单击 **[!UICONTROL “更多详细信息”]** 部分中的 **[!UICONTROL “更多详细信息]**”。

在 Adobe Mobile Services UI 中，您可以使用 VRS 创建应用程序并将数据划分到贵组织中的特定组。例如，在这种情况下，西班牙的业务用户就无法查看日本业务用户的相关数据。

>[!TIP]
>
>您不能修改父报表包继承的值。

VRS 是附加到父报表包的服务器端区段定义。因此，您无法收集 VRS 数据，因为 SDK 只会将点击发送到父报表包，然后父报表包会记录点击。

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

在Adobe Mobile Services中，您可以基于父报表套件或虚拟报告套件创建应用程序。在基于虚拟报表包创建应用程序时，我们建议您将 VRS 区段与应用程序的定义保持一致。

>[!TIP]
>
>推送证书附加在Mobile Services UI的应用程序级别。

为确保能够正常发送您的推送消息，您必须正确定义受众区段。有关更多信息，请参阅 [受众：为推送消息定义和配置受众区段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

“管理应用程序设置”页面上的时区属性不同于用于在Adobe Analytics中创建VRS的时区属性。“管理应用程序设置”页面上的属性继承自父报表包，可用于将数据发送到 Adobe Analytics。在Adobe Analytics中创建VRS时指定的属性用于在Mobile Services UI中显示报表，并且可能不同于父报表包。

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

要在创建应用程序时使用 VRS，请从&#x200B;**应用程序信息页面的报表包**&#x200B;下拉列表中选择 VRS。此列表包含父报表包和虚拟报表包。

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

以下是 VRS 的属性：

>[!TIP]
>
>只读属性从父报表包继承。

| 属性 | 是否继承自父报表包 | 是否可编辑？ | 注释 |
|--- |--- |--- |--- |
| `target.clientCode` | 否 | 是 |  |
| `target.timeout` | 否 | 是 |  |
| `audienceManager.server` | 否 | 是 |  |
| `audienceManager.analyticsForwardingEnabled` | 是 | 是 |  |
| `audienceManager.timeout` | 否 | 是 |  |
| `acquisition.server` | 否 | 否 |  |
| `acquisition.appid` | 否 | 否 |  |
| `analytics.rsids` | 是 | 否 |  |
| `analytics.server` | 否 | 否 |  |
| `analytics.ssl` | 否 | 是 |  |
| `analytics.offlineEnabled` | 是 |  |  |
| `analytics.charset` | 是 | 否 |  |
| `analytics.lifecycleTimeout` | 否 | 是 | 如果用户希望他们的数据一致，则应该继承自父报表包。 |
| `analytics.privacyDefault` | 否 | 是 |  |
| `analytics.batchLimit` | 否 | 是 |  |
| `analytics.timezone` | 是 | 是，当您首次创建应用程序时。 | 此时区属性用于将数据发送到 Adobe Analytics，与创建 VRS 时设置的时区属性不同。 |
| `analytics.timezoneOffset` | 是 | 否 |  |
| `analytics.referrerTimeout` | 否 | 是 |  |
| `analytics.backdateSessionInfo` | 是 | 是 |  |

## 其他信息 {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

以下是有关虚拟报告套件的一些其他信息：

* 有关 VRS 的更多信息，请参阅[虚拟报表包](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)。
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).