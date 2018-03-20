---
title: "Ausnahmen von der Datenübertragungsrichtlinie für Apps"
titleSuffix: Microsoft Intune
description: "Erstellen Sie Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1e37e78f7272b0f53f974eccb20c7e02574a9a9
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Erstellen von Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Als Administrator können Sie Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen. Mithilfe einer Ausnahme können Sie gezielt auswählen, welche nicht verwalteten Apps Daten in und aus verwalteten Apps übertragen können. Die nicht verwalteten Apps, die Sie in die Ausnahmeliste einfügen, müssen von der IT als vertrauenswürdig eingestuft werden. 

>[!WARNING] 
> Sie sind für Änderungen an der Richtlinie für Ausnahmen bei der Datenübertragung verantwortlich. Aufgrund von Zusätzen zu dieser Richtlinie können nicht verwaltete Apps (Apps, die nicht von Intune verwaltet werden) auf Daten zugreifen, die von verwalteten Apps geschützt werden. Dieser Zugriff auf geschützte Daten kann zu Datensicherheitslücken führen. Fügen Sie Datenübertragungsausnahmen nur für Apps hinzu, die von Ihrer Organisation verwendet werden müssen, von denen Intune APP (Application Protection Policies, Anwendungsschutzrichtlinien) jedoch nicht unterstützt wird. Fügen Sie außerdem nur Ausnahmen für Apps hinzu, die Ihrer Einschätzung nach kein Risiko für eine Datensicherheitslücke darstellen.

Dieses Features wird angewendet, wenn Sie eine Intune-Anwendungsschutzrichtlinie erstellen, bei der Sie für die Datenübertragung die Option **Managed apps only** (Nur verwaltete Apps) festlegen. wenn Ihre Richtlinie zur Datenübertragung auf **Managed apps only** (Nur verwaltete Apps) festgelegt ist, ist die Datenübertragung anders als die von Ihnen erstellten Ausnahmen weiterhin auf Apps beschränkt, die von Intune verwaltet werden. Sie können die Einschränkungen mithilfe von Protokollen (unter iOS) oder Paketen (unter Android) erstellen.

Sie können dieses Feature so konfigurieren, dass Ausnahmen für die Intune-MAM-Anwendungsschutzrichtlinie **restrict data transfer** (Datenübertragung einschränken) aktiviert werden. Diese Richtlinie ist nicht erforderlich, wenn Sie zulassen möchten, dass Daten an eine App übertragen werden, die Intune APP nicht unterstützt. Diese Richtlinie lässt zu, dass von Intune verwaltete Anwendungen, bei denen die Einstellung für die Datenübertragung mit **Managed apps only** (Nur verwaltete Apps) festgelegt wurde, nicht verwaltete Anwendungen basierend auf dem URL-Protokoll (iOS) oder auf dem Paketnamen (Android) aufrufen können. Intune fügt der Standardliste mit Ausnahmen wichtige native Anwendungen hinzu. 

## <a name="ios-data-transfer-exceptions"></a>Datenübertragungsausnahmen bei iOS
Bei einer Richtlinie für iOS können Sie Datenübertragungsausnahmen gemäß dem URL-Protokoll konfigurieren. In der vom Entwickler der App bereitgestellten Dokumentation finden Sie Informationen zum Hinzufügen einer Ausnahme sowie zu unterstützten URL-Protokollen. Weitere Informationen zu Datenübertragungsausnahmen bei iOS finden Sie unter [Einstellungen für App-Schutzrichtlinien für iOS - Datenübertragungsausnahmen](app-protection-policy-settings-ios.md#data-transfer-exemptions).

## <a name="android-data-transfer-exceptions"></a>Datenübertragungsausnahmen bei Android
Bei einer Richtlinie für Android können Sie Datenübertragungsausnahmen gemäß App-Paketname. Auf der Seite **Google Play Store** finden Sie den App-Paketnamen der App, für die Sie eine Ausnahme hinzufügen möchten. Weitere Informationen zu Datenübertragungsausnahmen bei Android finden Sie unter [Einstellungen für App-Schutzrichtlinien für Android - Datenübertragungsausnahmen](app-protection-policy-settings-android.md#data-transfer-exemptions).

### <a name="example"></a>Beispiel
Wenn Sie der MAM-Datenübertragungsrichtlinie das **Webex**-Paket als Ausnahme hinzufügen, dürfen Webex-Links in einer verwalteten Outlook-E-Mail-Nachricht direkt in der Webex-Anwendung geöffnet werden. In anderen nicht verwalteten Apps ist die Datenübertragung jedoch weiterhin eingeschränkt.

- Beispiel für **Webex** unter iOS: Um für die **Webex**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: <code>wbx</code>.

- Beispiel für **Webex** unter Android: Um für die **Webex**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: <code>com.cisco.webex.meetings</code>. 

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen und Bereitstellen von App-Schutzrichtlinien](app-protection-policies.md)
- [Einstellungen für App-Schutzrichtlinien für iOS – Datenübertragungsausnahmen](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Einstellungen für App-Schutzrichtlinien für Android – Datenübertragungsausnahmen](app-protection-policy-settings-android.md#data-transfer-exemptions)
