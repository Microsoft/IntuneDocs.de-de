---
title: Ausnahmen von der Datenübertragungsrichtlinie für Apps
titleSuffix: Microsoft Intune
description: Erstellen Sie Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9f6ee3d1672c375071b061b4a551f609792deb9
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238250"
---
# <a name="how-to-create-exceptions-to-the-intune-mobile-application-management-mam-data-transfer-policy"></a>Erstellen von Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune

Als Administrator können Sie Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen. Mithilfe einer Ausnahme können Sie gezielt auswählen, welche nicht verwalteten Apps Daten in und aus verwalteten Apps übertragen können. Die nicht verwalteten Apps, die Sie in die Ausnahmeliste einfügen, müssen von der IT als vertrauenswürdig eingestuft werden. 

>[!WARNING] 
> Sie sind für Änderungen an der Richtlinie für Ausnahmen bei der Datenübertragung verantwortlich. Aufgrund von Zusätzen zu dieser Richtlinie können nicht verwaltete Apps (Apps, die nicht von Intune verwaltet werden) auf Daten zugreifen, die von verwalteten Apps geschützt werden. Dieser Zugriff auf geschützte Daten kann zu Datensicherheitslücken führen. Fügen Sie Datenübertragungsausnahmen nur für Apps hinzu, die von Ihrer Organisation verwendet werden müssen, von denen Intune APP (Application Protection Policies, Anwendungsschutzrichtlinien) jedoch nicht unterstützt wird. Fügen Sie außerdem nur Ausnahmen für Apps hinzu, die Ihrer Einschätzung nach kein Risiko für eine Datensicherheitslücke darstellen.

Innerhalb einer Intune-Anwendungsschutzrichtlinie bedeutet das Festlegen von **Zulassen, dass die App Daten an andere Apps überträgt** auf **Richtlinienverwaltete Apps**, dass die App Daten nur an Apps übertragen kann, die von Intune verwaltet werden. Wenn Datenübertragungen an bestimmte Anwendungen zugelassen werden müssen, die Intune-Anwendungsschutzrichtlinien nicht unterstützen, können Sie Ausnahmen von dieser Richtlinie erstellen, indem Sie **Wählen Sie die Apps aus, die ausgenommen werden sollen** nutzen. Ausnahmen ermöglichen von Intune verwaltete Anwendungen, nicht verwaltete Anwendungen basierend auf dem URL-Protokoll (iOS) oder Paketnamen (Android) aufzurufen. Intune fügt der Liste mit den Ausnahmen standardmäßig wichtige native Anwendungen hinzu. 

> [!NOTE]
> Wenn Sie die Ausnahmen der Richtlinie für die Datenübertragung ändern oder erweitern (z.B. Einschränkungen der Vorgänge Ausschneiden, Kopieren und Einfügen), hat dies keine Auswirkungen auf andere App-Schutzrichtlinien. 

## <a name="ios-data-transfer-exceptions"></a>Datenübertragungsausnahmen bei iOS
Bei einer Richtlinie für iOS können Sie Datenübertragungsausnahmen gemäß dem URL-Protokoll konfigurieren. In der vom Entwickler der App bereitgestellten Dokumentation finden Sie Informationen zum Hinzufügen einer Ausnahme sowie zu unterstützten URL-Protokollen. Weitere Informationen zu Datenübertragungsausnahmen bei iOS finden Sie unter [Einstellungen für App-Schutzrichtlinien für iOS – Datenübertragungsausnahmen](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft verfügt über keine Methode, mit der das URL-Protokoll zum Erstellen von App-Ausnahmen für Drittanbieteranwendungen gesucht werden kann. 

## <a name="android-data-transfer-exceptions"></a>Datenübertragungsausnahmen bei Android
Bei einer Richtlinie für Android können Sie Datenübertragungsausnahmen gemäß App-Paketname. Auf der Seite **Google Play Store** finden Sie den App-Paketnamen der App, für die Sie eine Ausnahme hinzufügen möchten. Weitere Informationen zu Datenübertragungsausnahmen bei Android finden Sie unter [Einstellungen für App-Schutzrichtlinien für Android – Datenübertragungsausnahmen](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Sie finden die Paket-ID einer App, indem Sie im Google Play Store zu der App navigieren. Die Paket-ID ist in der URL der Seite der App enthalten. Die Paket-ID der Microsoft Word-App lautet z.B. **com.microsoft.office.word**.

### <a name="example"></a>Beispiel
Wenn Sie der MAM-Datenübertragungsrichtlinie das **Webex**-Paket als Ausnahme hinzufügen, dürfen Webex-Links in einer verwalteten Outlook-E-Mail-Nachricht direkt in der Webex-Anwendung geöffnet werden. In anderen nicht verwalteten Apps ist die Datenübertragung jedoch weiterhin eingeschränkt.

- Beispiel für **Webex** unter iOS:   Um für die **Webex**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: <code>wbx</code>
    
 - Beispiel für **Maps** unter iOS:  Um für die native **Maps**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: <code>maps</code>

- Beispiel für **Webex** unter Android:   Um für die **Webex**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: <code>com.cisco.webex.meetings</code>
    
- Beispiel für **SMS** unter Android:   Um für die native **SMS**-App eine Ausnahme festzulegen, sodass sie von verwalteten Intune-Apps auf verschiedenen Messaging-Apps und Android-Geräten aufgerufen werden kann, müssen Sie eine Datenübertragungsausnahme für die folgende Zeichenfolge festlegen: 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen und Bereitstellen von App-Schutzrichtlinien](app-protection-policies.md)
- [Einstellungen für App-Schutzrichtlinien für iOS – Datenübertragungsausnahmen](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Einstellungen für App-Schutzrichtlinien für Android – Datenübertragungsausnahmen](app-protection-policy-settings-android.md#data-transfer-exemptions)
