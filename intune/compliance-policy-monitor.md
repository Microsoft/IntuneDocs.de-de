---
title: Überwachen von Microsoft Intune -Gerätekonformitätsrichtlinien
titlesuffix: ''
description: Verwenden Sie das Dashboard für die Gerätekonformität, um die Konformität der Geräte insgesamt zu überwachen, Berichte anzuzeigen sowie die Gerätekonformität pro Richtlinie und pro Einstellung anzuzeigen.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 557018264da5c21459e47e3e139ddd327a4a5ea6
ms.sourcegitcommit: c3ae3c3dc46b62d9191813d25a196874ba4927be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Überwachen von Intune-Richtlinien zur Gerätekompatibilität

Mithilfe von Kompatibilitätsberichten können Administratoren die Kompatibilität von Geräten in ihrer Organisation analysieren und schnell kompatibilitätsbezogene Probleme behandeln, die bei Benutzern in ihrer Organisation auftreten. Sie können Informationen zum allgemeinen Kompatibilitätsstatus von Geräten, zum Kompatibilitätsstatus einer einzelnen Einstellung und zum Kompatibilitätsstatus einer einzelnen Richtlinie sowie Detailinformationen zu einzelnen Geräten anzeigen, um sich über bestimmte Einstellungen und Richtlinien zu informieren, die das Gerät betreffen.

> [!NOTE]
> Im März werden im Intune-Dienst basierend auf Ihrem Feedback einige Sicherheitsverbesserungen eingeführt. Je nachdem, wie Ihre Konformitätsrichtlinien konfiguriert sind, müssen Sie möglicherweise Maßnahmen ergreifen, damit Ihre Endbenutzer nicht den Zugriff auf ihre E-Mails verlieren. Weitere Informationen finden Sie unter [Upcoming security enhancements (Bevorstehende Sicherheitsverbesserungen)](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

## <a name="before-you-begin"></a>Vorbereitung

Gehen Sie wie folgt vor, um im Azure-Portal zum **Intune-Dashboard für die Gerätekonformität** zu gelangen:

1.  Melden Sie sich im [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an.

2.  Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3.  Wählen Sie **Intune** &gt; **Gerätekompatibilität** &gt; **Übersicht** aus. Daraufhin wird das **Gerätekompatibilitätsdashboard** geöffnet.

> [!IMPORTANT]
> Geräte müssen in Intune registriert werden, um Gerätekompatibilitätsrichtlinien empfangen zu können.

## <a name="device-compliance-dashboard"></a>Gerätekompatibilitätsdashboard

Auf dem **Gerätekompatibilitätsdashboard** können den Status der Gerätekompatibilität überwachen. Zu diesem Zweck stehen verschiedene Kacheln mit unterschiedlichen Berichten zur Verfügung, die Aufschluss über die Kompatibilität von Geräten in Ihrer Organisation geben. Folgende Berichte sind verfügbar:

-   Allgemeine Gerätekompatibilität (aggregiert)

-   Richtlinienspezifische Gerätekompatibilität

-   Einstellungsspezifische Gerätekompatibilität

![Abbildung: Dashboard für die Gerätekonformität](./media/idc-1.png)

Darüber hinaus können Sie die spezifischen Kompatibilitätsrichtlinien und Einstellungen für ein bestimmtes Gerät sowie den endgültigen Kompatibilitätsstatus für die einzelnen Einstellungen auf dem Gerät anzeigen.

### <a name="overall-device-compliance-aggregate-report"></a>Aggregierter Bericht zur allgemeinen Gerätekompatibilität

Hierbei handelt es sich um ein Ringdiagramm mit dem aggregierten Kompatibilitätsstatus aller in Intune registrierten Geräte. Die Werte für den Gerätekompatibilitätsstatus werden in zwei Datenbanken (Intune und Azure Active Directory) gespeichert. Im Anschluss werden die Statuswerte der Gerätekompatibilitätsrichtlinie ausführlicher beschrieben:

-   **Kompatibel**: Das Gerät hat erfolgreich mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie angewendet.

-   **Nicht kompatibel**: Das Gerät konnte mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden, oder der Benutzer verstößt gegen die vom Administrator festgelegten Richtlinien.

-   **In-grace period** (In Toleranzperiode): Für das Gerät wurde vom Administrator mindestens eine Einstellung für die Gerätekompatibilitätsrichtlinie festgelegt, diese wurden vom Benutzer aber noch nicht angewendet. Das Gerät ist daher zwar noch nicht kompatibel, befindet sich aber in der vom Administrator definierten Toleranzperiode.

    -   Informieren Sie sich ausführlicher über Aktionen für nicht kompatible Geräte.

-   **Gerät nicht synchronisiert**: Das Gerät konnte den Status der Gerätekonformitätsrichtlinie nicht melden. Mögliche Ursachen:

    -   **Unbekannt**: Das Gerät ist offline oder konnte aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren.

    -   **Fehler**: Das Gerät konnte nicht mit Intune und Azure AD kommunizieren und hat eine Fehlermeldung mit der Ursache erhalten.

> [!IMPORTANT]
> In Intune registrierte Geräte, für die keine Gerätekonformitätsrichtlinien festgelegt sind, werden in diesem Bericht der Kategorie **Konform** zugeordnet.

#### <a name="drill-down-option"></a>Anzeigen von Detailinformationen

Wenn Sie auf dem **Gerätekompatibilitätsdashboard** auf die Gerätekompatibilitätskachel klicken, können Sie für jedes Gerät, für das Gerätekompatibilitätsrichtlinien festgelegt sind, Detailinformationen zu einem bestimmten **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort** anzeigen.

![Abbildung: Dashboard für die Gerätekonformität – Detailinformationen](./media/idc-2.png)

Sollten Sie weitere Details zu einem bestimmten Benutzer benötigen, können Sie den Bericht mit dem Gerätekompatibilitätsdiagramm filtern, indem Sie den E-Mail-Alias des Benutzers eingeben.

![Abbildung: Dashboard für die Gerätekonformität – bestimmter Benutzer](./media/idc-3.png)

Sie können auch auf die verschiedenen Kompatibilitätsstatuswerte des Gerätekompatibilitätsdiagramms klicken, um für den Benutzer weitere Details zu den Statuswerten der Gerätekompatibilitätsrichtlinie zu erhalten.

![Abbildung: Dashboard für die Gerätekonformität – verschiedene Statuswerte](./media/idc-4.png)

#### <a name="filter"></a>Filter

Wenn Sie auf die Schaltfläche **Filter** klicken, wird das Filterflyout mit folgenden Optionen geöffnet:

-   Modell

    -   Textfeld zur Eingabe einer beliebigen Suchzeichenfolge
<br></br>
-   Plattform

    -   Android

    -   iOS

    -   macOS

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

Wenn Sie auf ein Gerät klicken, wird der **Bereich „Geräte“** geöffnet, in dem das Gerät ausgewählt ist. Dieser Bereich zeigt weitere Details zu den Einstellungen der auf dieses Gerät angewendeten Konformitätsrichtlinie an.

Wenn Sie auf die eigentliche Geräterichtlinieneinstellung klicken, sehen Sie den Namen der Gerätekompatibilitätsrichtlinie, aus der die vom Administrator festgelegte Gerätekompatibilitätseinstellung stammt.

### <a name="devices-without-compliance-policy"></a>Geräte ohne Konformitätsrichtlinie
Dieser Bericht identifiziert Geräte, denen keine Konformitätsrichtlinie zugewiesen ist. Durch die Einführung der Sicherheitseinstellung, die alle Geräte ohne Konformitätsrichtlinien als „nicht konform“ markiert, ist es wichtig, diese Geräte zu identifizieren. Sie können diesen dann mindestens eine Konformitätsrichtlinie zuweisen.

> [!NOTE]
> Die neue Sicherheitseinstellung kann im Intune-Portal konfiguriert werden. Klicken Sie auf **Gerätekonformität**, und klicken Sie unter **Setup** auf **Einstellungen für Konformitätsrichtlinien**. Verwenden Sie dann die Umschaltfläche, um **Markieren Sie Geräte ohne zugewiesene Konformitätsrichtlinie als** auf **Konform** oder **Nicht konform** festzulegen. Erfahren Sie mehr über diese [Sicherheitsverbesserung im Intune-Dienst](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

![Bild, das den Bericht für Geräte ohne Konformitätsrichtlinie anzeigt](./media/idc-12.png)

Die Kachel **Geräte ohne Konformitätsrichtlinie** ist im Dashboard „Gerätekonformität“ verfügbar und zeigt alle Geräte ohne Konformitätsrichtlinie an sowie den Benutzer des Geräts, den Konformitätsstatus und das Gerätemodell.

> [!NOTE]
> Benutzer, die einer beliebigen Konformitätsrichtlinie zugeordnet sind, werden im Bericht unabhängig von der Geräteplattform nicht angezeigt. Wenn Sie beispielsweise eine Windows-Konformitätsrichtlinie unabsichtlich einem Benutzer mit einem Android-Gerät hinzugefügt haben, wird das Gerät nicht im Bericht angezeigt. Intune betrachtet dieses Android-Gerät jedoch als „nicht konform“. Es wird empfohlen, Richtlinien für jede Geräteplattform zu erstellen und diese für alle Benutzer bereitzustellen, um Probleme zu vermeiden.

### <a name="per-policy-device-compliance-report"></a>Richtlinienspezifischer Gerätekompatibilitätsbericht

Dieser Bericht bietet eine richtlinienspezifische Kompatibilitätsansicht und gibt Aufschluss über die Gesamtanzahl von Geräten mit den jeweiligen Kompatibilitätsstatuswerten. Die Kachel für die **Richtlinienkompatibilität** steht im **Gerätekompatibilitätsdashboard** zur Verfügung und zeigt neben allen vom Administrator erstellten Richtlinien die Plattformen, für die die Richtlinie angewendet wird, sowie die Anzahl kompatibler und nicht kompatibler Geräte an.

![Abbildung: richtlinienspezifischer Gerätekonformitätsbericht](./media/idc-8.png)

Wenn Sie auf die Kachel für die Richtlinienkompatibilität und anschließend auf eine der Gerätekompatibilitätsrichtlinien klicken, erhalten Sie für jedes Gerät, für das diese Gerätekompatibilitätsrichtlinie gilt, Informationen zum **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort**.

## <a name="setting-compliance-report"></a>Bericht zur Einstellungskompatibilität

In diesem Bericht können Sie sich auf der Grundlage der Kompatibilitätseinstellung über die Gesamtanzahl von Geräten mit den jeweiligen Kompatibilitätsstatuswerten informieren. Die Kachel für die **Einstellungskonformität** steht auf dem **Dashboard für die Gerätekonformität** zur Verfügung und zeigt alle Einstellungen für sämtliche vom Administrator erstellten Gerätekonformitätsrichtlinien, die Plattformen, auf denen die Richtlinieneinstellungen angewendet wurden, sowie die Anzahl nicht konformer Geräte an.

![Abbildung: einstellungsspezifischer Gerätekonformitätsbericht](./media/idc-10.png)

Wenn Sie auf die Kachel für die Einstellungskompatibilität und anschließend auf eine der Gerätekompatibilitätsrichtlinien-Einstellungen klicken, erhalten Sie für jedes Gerät, für das diese Gerätekompatibilitätsrichtlinien-Einstellung gilt, Informationen zum **Kompatibilitätsstatus**, **E-Mail-Alias des Benutzers**, **Gerätemodell** und **Standort**.
