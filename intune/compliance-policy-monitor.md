---
title: "Überwachen von Intune-Richtlinien zur Gerätekompatibilität"
titlesuffix: Azure portal
description: "Erfahren Sie, wie Sie Richtlinien zur Gerätekompatibilität überwachen."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2f80d46e3e7c25c2b2e7a7c1af9604de1257a21e
ms.sourcegitcommit: a55c009a2ab223f79dc7439539937b284aee0626
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Überwachen von Intune-Richtlinien zur Gerätekompatibilität

Mithilfe von Kompatibilitätsberichten können Administratoren die Kompatibilität von Geräten in ihrer Organisation analysieren und schnell kompatibilitätsbezogene Probleme behandeln, die bei Benutzern in ihrer Organisation auftreten. Sie können Informationen zum allgemeinen Kompatibilitätsstatus von Geräten, zum Kompatibilitätsstatus einer einzelnen Einstellung und zum Kompatibilitätsstatus einer einzelnen Richtlinie sowie Detailinformationen zu einzelnen Geräten anzeigen, um sich über bestimmte Einstellungen und Richtlinien zu informieren, die das Gerät betreffen.

## <a name="before-you-begin"></a>Vorbereitung

Gehen Sie wie folgt vor, um im Azure-Portal zum **Intune-Dashboard für die Gerätekompatibilität** zu gelangen:

1.  Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an.

2.  Wählen Sie im linken Menü **Weitere Dienste** aus, und geben Sie in das Filtertextfeld die Zeichenfolge **Intune** ein.

3.  Wählen Sie **Intune** &gt; **Gerätekompatibilität** &gt; **Übersicht** aus. Daraufhin wird das **Gerätekompatibilitätsdashboard** geöffnet.

> [!IMPORTANT] 
> Geräte müssen in Intune registriert werden, um Gerätekompatibilitätsrichtlinien empfangen zu können.

## <a name="device-compliance-dashboard"></a>Gerätekompatibilitätsdashboard

Auf dem **Gerätekompatibilitätsdashboard** können den Status der Gerätekompatibilität überwachen. Zu diesem Zweck stehen verschiedene Kacheln mit unterschiedlichen Berichten zur Verfügung, die Aufschluss über die Kompatibilität von Geräten in Ihrer Organisation geben. Folgende Berichte sind verfügbar:

-   Allgemeine Gerätekompatibilität (aggregiert)

-   Richtlinienspezifische Gerätekompatibilität

-   Einstellungsspezifische Gerätekompatibilität

![Gerätekompatibilitätsdashboard](./media/idc-1.png)

Darüber hinaus können Sie die spezifischen Kompatibilitätsrichtlinien und Einstellungen für ein bestimmtes Gerät sowie den endgültigen Kompatibilitätsstatus für die einzelnen Einstellungen auf dem Gerät anzeigen.

### <a name="overall-device-compliance-aggregate-report"></a>Aggregierter Bericht zur allgemeinen Gerätekompatibilität

Hierbei handelt es sich um ein Ringdiagramm mit dem aggregierten Kompatibilitätsstatus aller in Intune registrierten Geräte. Die Werte für den Gerätekompatibilitätsstatus werden in zwei Datenbanken (Intune und Azure Active Directory) gespeichert. Im Anschluss werden die Statuswerte der Gerätekompatibilitätsrichtlinie ausführlicher beschrieben:

-   **Kompatibel**: Das Gerät hat erfolgreich mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie angewendet.

-   **Nicht kompatibel**: Das Gerät konnte mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden, oder der Benutzer verstößt gegen die vom Administrator festgelegten Richtlinien.

-   **In-grace period** (In Toleranzperiode): Für das Gerät wurde vom Administrator mindestens eine Einstellung für die Gerätekompatibilitätsrichtlinie festgelegt, diese wurden vom Benutzer aber noch nicht angewendet. Das Gerät ist daher zwar noch nicht kompatibel, befindet sich aber in der vom Administrator definierten Toleranzperiode.

    -   Informieren Sie sich ausführlicher über Aktionen für nicht kompatible Geräte.

-   **Gerät nicht synchronisiert**: Das Gerät konnte den Status der Gerätekompatibilitätsrichtlinie nicht melden. Mögliche Ursachen:

    -   **Unbekannt**: Das Gerät ist offline oder konnte aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren.

    -   **Fehler**: Das Gerät konnte nicht mit Intune und Azure AD kommunizieren und hat eine Fehlermeldung mit der Ursache erhalten.

> [!IMPORTANT] 
> In Intune registrierte Geräte, für die keine Gerätekompatibilitätsrichtlinien festgelegt sind, werden in diesem Bericht der Kategorie **Kompatibel** zugeordnet.

#### <a name="drill-down-option"></a>Anzeigen von Detailinformationen

Wenn Sie auf dem **Gerätekompatibilitätsdashboard** auf die Gerätekompatibilitätskachel klicken, können Sie für jedes Gerät, für das Gerätekompatibilitätsrichtlinien festgelegt sind, Detailinformationen zu einem bestimmten **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort** anzeigen.

![Gerätekompatibilitätsdashboard – Detailinformationen](./media/idc-2.png)

Sollten Sie weitere Details zu einem bestimmten Benutzer benötigen, können Sie den Bericht mit dem Gerätekompatibilitätsdiagramm filtern, indem Sie den E-Mail-Alias des Benutzers eingeben.

![Gerätekompatibilitätsdashboard – bestimmter Benutzer](./media/idc-3.png)

Sie können auch auf die verschiedenen Kompatibilitätsstatuswerte des Gerätekompatibilitätsdiagramms klicken, um für den Benutzer weitere Details zu den Statuswerten der Gerätekompatibilitätsrichtlinie zu erhalten.

![Gerätekompatibilitätsdashboard – verschiedene Statuswerte](./media/idc-4.png)

#### <a name="filter"></a>Filter

Wenn Sie auf die Schaltfläche **Filter** klicken, wird das Filterflyout mit folgenden Optionen geöffnet:

-   Modell

    -   Textfeld zur Eingabe einer beliebigen Suchzeichenfolge
<br></br>
-   Plattform

    -   Android

    -   iOS

    -   Mac OS

    -   Windows

    -   Windows Phone

-   Status

    -   Kompatibel

    -   Nicht kompatibel

    -   In Grace period (In Toleranzperiode)

    -   Unbekannt

    -   Fehler

Wenn Sie auf die Schaltfläche **Aktualisieren** klicken, wird das Flyout geschlossen, und die Ergebnisse werden gemäß den ausgewählten Filterkriterien aktualisiert.

##### <a name="device-details"></a>Gerätedetails

Wenn Sie auf ein Gerät klicken, wird das Blatt **„Geräte“** geöffnet und das Gerät ausgewählt. Hier finden Sie weitere Details zur angewendeten Einstellung der Gerätekompatibilitätsrichtlinie für das Gerät.

![Gerätekompatibilitätsdashboard](./media/idc-6.png)

Wenn Sie auf die eigentliche Geräterichtlinieneinstellung klicken, sehen Sie den Namen der Gerätekompatibilitätsrichtlinie, aus der die vom Administrator festgelegte Gerätekompatibilitätseinstellung stammt.

![Name der Gerätekompatibilitätseinstellung](./media/idc-7.png)

## <a name="policy-compliance-report"></a>Bericht zur Richtlinienkompatibilität

Dieser Bericht bietet eine richtlinienspezifische Kompatibilitätsansicht und gibt Aufschluss über die Gesamtanzahl von Geräten mit den jeweiligen Kompatibilitätsstatuswerten. Die Kachel für die **Richtlinienkompatibilität** steht im **Gerätekompatibilitätsdashboard** zur Verfügung und zeigt neben allen vom Administrator erstellten Richtlinien die Plattformen, für die die Richtlinie angewendet wird, sowie die Anzahl kompatibler und nicht kompatibler Geräte an.

![Richtlinienspezifischer Gerätekompatibilitätsbericht](./media/idc-8.png)

Wenn Sie auf die Kachel für die Richtlinienkompatibilität und anschließend auf eine der Gerätekompatibilitätsrichtlinien klicken, erhalten Sie für jedes Gerät, für das diese Gerätekompatibilitätsrichtlinie gilt, Informationen zum **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort**.

![Kachel für die Richtlinienkompatibilität](./media/idc-9.png)

## <a name="setting-compliance-report"></a>Bericht zur Einstellungskompatibilität

In diesem Bericht können Sie sich auf der Grundlage der Kompatibilitätseinstellung über die Gesamtanzahl von Geräten mit den jeweiligen Kompatibilitätsstatuswerten informieren. Die Kachel für die **Einstellungskompatibilität** steht im **Gerätekompatibilitätsdashboard** zur Verfügung und zeigt neben allen Gerätekompatibilitätsrichtlinien-Einstellungen aller vom Administrator erstellten Gerätekompatibilitätsrichtlinien die Plattformen, für die die Richtlinieneinstellungen angewendet wurden, sowie die Anzahl nicht kompatibler Geräte an.

![Einstellungsspezifischer Gerätekompatibilitätsbericht](./media/idc-10.png)

Wenn Sie auf die Kachel für die Einstellungskompatibilität und anschließend auf eine der Gerätekompatibilitätsrichtlinien-Einstellungen klicken, erhalten Sie für jedes Gerät, für das diese Gerätekompatibilitätsrichtlinien-Einstellung gilt, Informationen zum **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort**.

![Kachel für die Einstellungskompatibilität](./media/idc-11.png)

## <a name="threat-agent-status-report"></a>Statusbericht zum Bedrohungs-Agent

In diesem Bericht wird der Status und der Zustand des Windows Defender-Agenten angezeigt. Wenn Sie einen Statusrollupbericht in **Gerätekompatibilität** verwenden, werden Ihnen Geräte angezeigt, für die einer der folgenden Aktionen erforderlich ist:
- Signaturupdate
- Neu starten
- Benutzereingriff
- Vollständige Überprüfung
- Andere Agent-Status, die einen Eingriff erfordern

In einem Drillthroughbericht für sämtliche Statuskategorien werden sowohl die einzelnen Computer aufgeführt, die überprüft werden sollten, als auch die, die als **Clean** (Bereinigt) eingestuft werden.
