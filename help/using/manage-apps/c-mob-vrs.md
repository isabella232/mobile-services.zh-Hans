---
description: 虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。它允许用户在一个报表包中维护他们的数据，但分别管理这些数据，就像它们存放在不同的报表包中一样。
seo-description: 虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。它允许用户在一个报表包中维护他们的数据，但分别管理这些数据，就像它们存放在不同的报表包中一样。
seo-title: 虚拟报表包
title: 虚拟报表包
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: ht
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# 虚拟报表包 {#virtual-report-suites}

虚拟报表包 (VRS) 是指通过将一个或多个区段定义应用到报表包来创建的报表包。它允许用户在一个报表包中维护他们的数据，但分别管理这些数据，就像它们存放在不同的报表包中一样。

使用 VRS 的应用程序与使用常规报表包的应用程序具有相同的功能，但是使用 VRS 的应用程序可管理以下功能：

* 处理规则
* evar/prop/listvar/event
* 启用时间戳的选项
* 维度标志（生命周期、位置等）
* 分类

这些值在可父报表包中进行管理，并与属于同一父报表包的 VRS 共享。

以下区域独立于父报表包，可以在 Adobe Mobile Services UI 中进行访问：

* 配置文件
* 管理目标点
* 管理链接目标
* 管理回发
* 消息链接
* 客户获取

VRS 可帮助您完成以下任务：

* 限制数据访问

   某跨国公司拥有一个应用程序，可以将数据发送到所有地理位置的报表包。但是，该公司想要限制一个地区的业务用户查看另一个地区的数据。此时，该公司的管理员可以创建一个按地区划分用户的 VRS，并将对该 VRS 的权限仅授予管理该地区的业务用户。

   此限制可阻止业务用户查看与其地区无关的数据。例如，欧洲、中东和非洲地区的业务用户不需要查看亚太地区的数据。

* 允许控制应用程序内消息传送/推送消息、位置 POI、客户获取和回发，所有数据都发送到一个报表包。

   某跨国公司希望将所有数据发送到适用于所有地理位置的同一报表包。但是，该公司希望各个地区的营销团队处理他们自己的应用程序内消息传送/推送消息。此时，该公司的管理员可以创建地区性的 VRS，每个团队都可以根据该 VRS 管理自己的应用程序。

   地区性团队可使用 VRS 的配置文件来构建应用程序。数据将会被发送到父报表包，但应用程序内消息传送/推送消息、位置 POI、客户获取和回发会在使用 VRS 创建的应用程序中进行控制。

## 在 Adobe Analytics 中创建虚拟报表包 {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>只有 Adobe Analytics 管理员可以在 Adobe Analytics 中创建和修改虚拟报表包。要创建虚拟表包，请参阅[创建虚拟报表包](https://docs.adobe.com/content/help/zh-Hans/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html)。

每个 VRS 都具有一个唯一的 ID。要在 Adobe Mobile Services UI 中查看父报表包 ID，请在“管理应用程序设置”页面的&#x200B;**[!UICONTROL 应用程序信息]**&#x200B;部分中，单击&#x200B;**[!UICONTROL 更多详细信息]**。

在 Adobe Mobile Services UI 中，您可以使用 VRS 创建应用程序并将数据划分到贵组织中的特定组。例如，在这种情况下，西班牙的业务用户就无法查看日本业务用户的相关数据。

>[!TIP]
>
>您无法修改从父报表包继承的值。

VRS 是附加到父报表包的服务器端区段定义。因此，您无法收集 VRS 数据，因为 SDK 只会将点击发送到父报表包，然后父报表包会记录点击。

## Adobe Mobile Services 中的虚拟报表包和数据收集 {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

在 Adobe Mobile Services 中，您可以基于父报表包或虚拟报表包创建应用程序。在基于虚拟报表包创建应用程序时，我们建议您将 VRS 区段与应用程序的定义保持一致。

>[!TIP]
>
>推送证书附加在 Mobile Services UI 的应用程序级别。

为确保能够正常发送您的推送消息，您必须正确定义受众区段。有关更多信息，请参阅[受众：为推送消息定义和配置受众区段](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。

## 了解时区 {#section_498E1EED22D741C3BDED44F01FACA72A}

“管理应用程序设置”页面上的时区属性与 Adobe Analytics 中用于创建 VRS 的时区属性不同。“管理应用程序设置”页面上的属性继承自父报表包，可用于将数据发送到 Adobe Analytics。您在 Adobe Analytics 中创建 VRS 时指定的属性用于在 Mobile Services UI 中显示报表，并且可能与父报表包不同。

## 在 Mobile Services UI 中选择虚拟报表包 {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

要在创建应用程序时使用 VRS，请从应用程序信息页面的&#x200B;**[!UICONTROL 报表包]**&#x200B;下拉列表中选择 VRS。此列表包含父报表包和虚拟报表包。

>[!IMPORTANT]
>
>要从该列表中选择 VRS，请找到带有蓝色圆点以及使用 `vrs_` *`<company_name>`* `_` *`<unique name>`* 命名约定的选项。

## 虚拟报表包属性 {#section_20ECE6243F664C4FB4347ADB4FF0458A}

以下是 VRS 的属性：

>[!TIP]
>
>只读属性继承自父报表包。

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

以下是有关虚拟报表包的一些其他信息：

* 有关 VRS 的更多信息，请参阅[虚拟报表包](https://docs.adobe.com/content/help/zh-Hans/analytics/components/virtual-report-suites/vrs-about.html)。
* 有关规划 VRS 实施的更多信息，请参阅[虚拟报表包工作流程](https://docs.adobe.com/content/help/zh-Hans/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html)。