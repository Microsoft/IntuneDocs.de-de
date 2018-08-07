---
title: Installieren von Office 365-Apps auf Geräten mit Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie Microsoft Intune verwenden können, um die Installation von Office 365-Apps auf Windows 10-Geräten zu vereinfachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4455a3c26296faba8bf01cf43d8555aebc13afc6
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321474"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune

Diese App erleichtert Ihnen die Zuweisung von Office 365-Apps zu Geräten, die Sie verwalten und auf denen Windows 10 ausgeführt wird. Sie können auch Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen. Die gewünschten Apps werden in der Intune-Konsole als einzelner Eintrag in der App-Liste angezeigt.


## <a name="before-you-start"></a>Vorbereitung

>[!IMPORTANT]
>Diese Installationsmethode für Office wird nur unterstützt, wenn keine anderen Versionen von Microsoft Office auf dem Gerät installiert sind.

- Auf den Geräten, auf denen Sie diese Apps bereitstellen, muss das Windows 10 Creators Update oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps aus der Office 365-Suite.
- Falls Office-Apps geöffnet sind, wenn Intune die App-Suite installiert, kann bei der Installation ein Fehler auftreten, und Benutzer verlieren möglicherweise Daten aus nicht gespeicherten Dateien.
- Diese Installationsmethode wird von Windows 10S-, Windows Home-, Windows Team-, Windows Holographic- oder Windows Holographic for Business-Geräten nicht unterstützt.
- Intune unterstützt nicht das Installieren von Office 365-Desktop-Apps aus dem Microsoft Store (sogenannte Office Centennial-Apps) auf einem Gerät, für das bereits Office 365-Apps mit Intune bereitgestellt wurden. Wenn Sie diese Konfiguration installieren, kann sie zu Datenverlusten oder -beschädigungen führen.
- Mehrere erforderliche oder verfügbare App-Zuweisungen sind nicht additiv. Eine spätere App-Zuweisung überschreibt bereits vorhandene installierte App-Zuweisungen. Wenn z.B. der erste Satz von Office-Apps Word enthält und der spätere nicht, wird Word deinstalliert. Diese Bedingung gilt nicht für Visio- oder Project-Anwendungen.


## <a name="get-started"></a>Erste Schritte

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Mobile Apps** aus.
4. Wählen Sie im Workloadbereich **Mobile Apps** unter **Verwalten** die Option **Apps** aus.
5. Wählen Sie **Hinzufügen** aus.
6. Wählen Sie im Bereich **Apps hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** die Option **Windows 10** aus.

Sie können die App-Suite jetzt konfigurieren.

## <a name="configure-the-app-suite"></a>Konfigurieren der App-Sammlung

Wählen Sie die Office-Apps aus, die Sie den Geräten zuweisen möchten.

1. Wählen Sie auf dem Blatt **App hinzufügen** die Option **App-Suite konfigurieren** aus.
2. Wählen Sie auf dem Blatt **App-Suite konfigurieren** die Office-Standard-Apps aus, die Sie Geräten zuweisen möchten.  
    Sie können zusätzlich Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen.
3. Wählen Sie **OK** aus.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

In diesem Schritt stellen Sie Informationen über die App-Suite bereit. Diese Informationen helfen Ihnen dabei, die App-Suite in Intune zu identifizieren. Außerdem können Benutzer sie im Unternehmensportal leichter finden.

1. Wählen Sie im Bereich **App hinzufügen** die Option **Informationen zur App-Suite** aus.
2. Gehen Sie im Bereich **Informationen zur App-Suite** folgendermaßen vor:
    - **Name der Suite**: Geben Sie den Namen der App-Suite ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Suitenamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung der Suite**: Geben Sie eine Beschreibung für die App-Suite ein. Sie können die Apps auflisten, die Sie einschließen möchten.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie optional mindestens eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App-Suite im Unternehmensportal.
    - **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen): Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie Anmerkungen zu dieser App ein.
    - **Logo**: Das Office 365-Logo wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
3. Wählen Sie **OK** aus.

## <a name="configure-app-settings"></a>App-Einstellungen konfigurieren

In diesem Schritt konfigurieren Sie Installationsoptionen für die App-Sammlung. Die Einstellungen gelten für alle Apps, die Sie der Suite hinzugefügt haben.

1. Wählen Sie im Bereich **App hinzufügen** die Option **Einstellungen der App-Suite** aus.
2. Gehen Sie im Bereich **Einstellungen der App-Suite** folgendermaßen vor:
    - **Office-Version**: Wählen Sie aus, ob Sie die 32-Bit- oder die 64-Bit-Version von Office zuweisen möchten. Sie können die 32-Bit-Version sowohl auf 32-Bit- als auch auf 64-Bit-Geräten installieren. Die 64-Bit-Version lässt sich jedoch nur auf 64-Bit-Geräten installieren.
    - **Updatekanal**: Wählen Sie aus, wie Office auf Geräten aktualisiert wird. Informationen zu den unterschiedlichen Updatekanälen finden Sie in der [Übersicht der Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Es stehen die folgenden Optionen zur Auswahl:
        - **Monatlich**
        - **Monatlich (Ziel)**
        - **Halbjährlich**
        - **Halbjährlich (Ziel)**
    - **Microsoft-Software-Lizenzbedingungen automatisch akzeptieren**: Wählen Sie diese Option aus, wenn Endbenutzer die Lizenzvereinbarung nicht akzeptieren müssen. Intune akzeptiert daraufhin die automatisch die Vereinbarung.
    - **Aktivierung gemeinsam genutzter Computer**: Wählen Sie diese Option aus, wenn sich mehrere Benutzer einen Computer teilen. Weitere Informationen finden Sie in der [Übersicht über die Aktivierung gemeinsam genutzter Computer für Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Sprachen**: Office installiert automatisch alle unterstützen Sprachen, die mit Windows auf Endbenutzergeräten installiert werden. Wählen Sie diese Option, wen Sie zusätzliche Sprachen mit der App-Sammlung installieren möchten.

## <a name="finish-up"></a>Fertig stellen

Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**. Die von Ihnen erstellte App wird in der Liste der Apps angezeigt.

## <a name="errors-during-installation-of-the-app-suite"></a>Fehler während der Installation der App-Suite

In den nachstehenden Tabellen sind die häufigsten Fehlercodes aufgeführt, die auftreten können, sowie deren Bedeutung.

### <a name="status-for-office-csp"></a>Status für Office CSP

||||
|-|-|-|
|Status|Phase|Beschreibung|
|1460 (ERROR_TIMEOUT)|Herunterladen|Das Office-Bereitstellungstool konnte nicht heruntergeladen werden|    
|13 (ERROR_INVALID_DATA)|-|Die Signatur des heruntergeladenen Office-Bereitstellungstools konnte nicht überprüft werden.|
|Fehlercode aus CertVerifyCertificateChainPolicy|-|Fehlgeschlagene Zertifizierungsprüfung für das heruntergeladene Office-Bereitstellungstool.|    
|997|WIP|Installation|
|0|Nach der Installation|Die Installation war erfolgreich|    
|1603 (ERROR_INSTALL_FAILURE)|-|Alle Voraussetzungsüberprüfungen sind fehlgeschlagen, z.B.:<ul><li>SxS (Beim Installationsversuch war 2016 MSI installiert.)</li><li>Versionskonflikt</li><li>Andere</li></ul>|  
|0x8000ffff (E_UNEXPECTED)|-|Beim Versuch, eine Deinstallation durchzuführen, war keine Klick-und-Los-Version von Office auf dem Computer vorhanden.|     
|17002|-|Das Szenario (Installation) konnte nicht abgeschlossen werden. Mögliche Gründe:<ul><li>Die Installation wurde vom Benutzer abgebrochen.</li><li>Die Installation wurde von einer anderen Installation abgebrochen.</li><li>Fehlender Speicherplatz auf dem Datenträger während der Installation</li><li>Unbekannte Sprach-ID</li></ul>|
|17004|-|Unbekannte SKUs|   


### <a name="office-deployment-tool-error-codes"></a>Fehlercodes der Office-Bereitstellungstools

|||||
|-|-|-|-|
|Szenario|Rückgabecode|Benutzeroberfläche|Hinweis|
|Deinstallationsaufwand, wenn keine aktive Klick-und-Los-Installation vorhanden ist|– 2147418113, 0x8000ffff oder 2147549183|Fehlercode: 30088-1008<br>Fehlercode: 30125-1011 (404)|Office-Bereitstellungstool|
|Installieren, wenn eine MSI-Version installiert wird|1603|-|Office-Bereitstellungstool|
|Die Installation wurde vom Benutzer oder einer anderen Installation abgebrochen|17002|-|Klick-und-Los|
|Versuch, eine 64-Bit-Version auf einem Gerät mit installierter 32-Bit-Version zu installieren|1603|-|Rückgabecode der Office-Bereitstellungstools|
|Versuch, eine unbekannte SKU zu installieren (kein zulässiger Anwendungsfall für Office CSP, da nur gültige SKUs übergeben werden sollen)|17004|-|Klick-und-Los|
|Nicht genügend Speicherplatz|17002|-|Klick-und-Los|
|Der Klick-und-Los-Client konnte nicht gestartet werden (unerwartet)|17000|-|Klick-und-Los|
|Der Klick-und-Los-Client konnte das Szenario nicht in die Warteschlange einreihen (unerwartet)|17001|-|Klick-und-Los|

## <a name="next-steps"></a>Nächste Schritte

- Wie Sie die Apps den von Ihnen ausgewählten Gruppen zuweisen können, erfahren Sie unter [Das Zuweisen von Apps zu Gruppen](/intune-azure/manage-apps/deploy-apps).
