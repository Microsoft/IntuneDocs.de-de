---
title: "Installieren von Office 365-Apps auf Geräten mit Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie, wie Sie Microsoft Intune verwenden können, um Office 365-Apps einfacher auf Windows 10-Geräten installieren zu können."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a8045261f93c6ac0282a03f13ac7bb7a7caac0d
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-assign-office-365-proplus-apps-to-windows-10-devices-with-microsoft-intune"></a>Vorgehensweise: Zuweisen von Office 365 ProPlus-Apps zu Windows 10-Geräten mit Microsoft Intune

Diese App erleichtert Ihnen die Zuweisung von Office 365 ProPlus-Apps zu Geräten, die Sie verwalten und die Windows 10 ausführen. Sie können Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen. Die gewünschten Apps werden als Einzeleintrag in der Liste der Apps in der Intune-Konsole angezeigt.


## <a name="before-you-start"></a>Vorbereitung

>[!IMPORTANT]
>Diese Installationsmethode für Office wird nicht unterstützt, wenn keine anderen Versionen von Microsoft Office auf dem Gerät installiert sind.

- Auf den Geräten, auf denen Sie diese Apps bereitstellen, muss das Windows 10 Creators Update oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps aus der Sammlung von Office 365 ProPlus-Suite.
- Wenn Office-Apps geöffnet sind, wenn Intune die App-Sammlung erstellt, kann bei der Installation ein Fehler auftreten, und Endbenutzer verlieren möglicherweise Daten aus nicht gespeicherten Dateien.
- Diese Installationsmethode wird von Windows 10S-, Windows Home-, Windows-Team-, Windows Holographic- und Windows Holographic for Business-Geräten nicht unterstützt.
- Intune unterstützt nicht das Installieren von Office 365-Desktop-Apps aus dem Microsoft Store (sogenannte Office Centennial-Apps) auf einem Gerät, für das bereits Office 365-Apps mit Intune bereitgestellt wurden. Wenn Sie diese Konfiguration installieren, kann sie zu Datenverlusten oder -beschädigungen führen.
- Mehrere erforderliche oder verfügbare App-Zuweisungen sind nicht additiv. Eine spätere App-Zuweisung überschreibt bereits vorhandene installierte App-Zuweisungen. Wenn z.B. der erste Satz von Office-Apps Wort enthält und der spätere nicht, wird Word deinstalliert. Dies gilt nicht für Visio- oder Project-Anwendungen.


## <a name="get-started"></a>Erste Schritte

1.  Melden Sie sich beim Azure-Portal an.
2.  Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3.  Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4.  Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5.  Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6.  Wählen Sie auf dem Blatt **App hinzufügen** **Office 365 ProPlus-Suite (Windows 10)** aus.

## <a name="configure-the-app-suite"></a>Konfigurieren der App-Sammlung

In diesem Schritt wählen Sie die Office-Apps aus, die Sie den Geräten zuweisen möchten.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **Configure App Suite** (App-Sammlung konfigurieren) aus.
2.  Wählen Sie auf dem Blatt **Configure App Suite** die Office-Standard-Apps, die Sie Geräten zuweisen möchten. Sie können zusätzlich Apps für den Microsoft Project Online-Desktopclient und Microsoft Visio Pro für Office 365 installieren, wenn Sie über Lizenzen für sie verfügen.
3.  Klicken Sie abschließend auf **OK**.

>[!IMPORTANT]
> Nachdem Sie die App-Sammlung erstellt haben, können Sie diese Eigenschaften bearbeiten. Um unterschiedliche Eigenschaften zu konfigurieren, löschen Sie die App-Sammlung, und erstellen Sie eine neue.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

Stellen Sie in diesem Schritt Informationen über die App-Sammlung bereit. Diese Informationen helfen Ihnen, die Sammlung in Intune zu identifizieren, und Endbenutzer können sie in der Unternehmensportal-App finden.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **App Suite Information** (Informationen über die App-Sammlung) aus.
2.  Geben Sie auf dem Blatt **App Suite Information** die folgenden Informationen an:
    - **Sammlungsname:** Geben Sie den Namen der App-Sammlung ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Sammlungsnamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Sammlungsbeschreibung:** Geben Sie eine Beschreibung für die Sammlung ein. Sie können die Apps auflisten, die Sie einschließen möchten.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Kategorie:** Wählen Sie optional eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch wird es für Benutzer leichter, die App-Sammlung im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App-Sammlung auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Symbol hochladen:** Laden Sie ein Symbol hoch, das gemeinsam mit der App angezeigt wird, wenn die Benutzer das Unternehmensportal durchsuchen.
3.  Klicken Sie abschließend auf **OK**.

## <a name="configure-app-settings"></a>App-Einstellungen konfigurieren

In diesem Schritt konfigurieren Sie Installationsoptionen für die App-Sammlung. Die Einstellungen gelten für alle Apps, die Sie zur Sammlung hinzugefügt haben.

1.  Wählen Sie auf dem Blatt **App hinzufügen** die Option **App Suite Settings** (Einstellungen für die App-Sammlung) aus.
2.  Geben Sie auf dem Blatt **App Suite Settings** die folgenden Informationen an:
    - **Office-Version:** Wählen Sie aus, ob Sie die 32-Bit- oder die 64-Bit-Version von Office zuweisen möchten. Sie können die 32-Bit-Version auf jeweils 32-Bit- und 64-Bit-Geräten installieren, jedoch können Sie die 64-Bit-Version nur auf 64-Bit-Geräten installieren.
    - **Updatekanal:** Wählen Sie aus, wie Office auf Geräten aktualisiert wird. Informationen zu den unterschiedlichen Updatekanälen finden Sie in der [Übersicht der Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Es stehen die folgenden Optionen zur Auswahl:
        - **Monatlich**
        - **Monatlich (Ziel)**
        - **Halbjährlich**
        - **Halbjährlich (Ziel)**
    - **Automatically accept the app end user license agreement** (Die Endbenutzer-Lizenzvereinbarung der App automatisch akzeptieren): Wählen Sie diese Option aus, wenn Endbenutzer die Lizenzvereinbarung nicht akzeptieren müssen. Intune akzeptiert daraufhin die automatisch die Vereinbarung.
    - **Aktivierung gemeinsam genutzter Computer:** Die Aktivierung gemeinsam genutzter Computer wird verwendet, wenn sich mehrere Benutzer einen Computer teilen. Weitere Informationen finden Sie im Überblick über die Aktivierung gemeinsam genutzter Computer für Office 365 ProPlus.
    - **Sprachen:** Office installiert automatisch alle unterstützen Sprachen, die mit Windows auf Endbenutzergeräten installiert werden. Wählen Sie diese Option, wen Sie zusätzliche Sprachen mit der App-Sammlung installieren möchten.

>[!IMPORTANT]
> Nachdem Sie die App-Sammlung erstellt haben, können Sie diese Eigenschaften bearbeiten. Um unterschiedliche Eigenschaften zu konfigurieren, löschen Sie die App-Sammlung, und erstellen Sie eine neue.

## <a name="finish-up"></a>Fertig stellen

Wenn Sie fertig sind, wählen Sie auf dem Blatt **App hinzufügen** die Option **Speichern** aus. Die von Ihnen erstellte App wird in der Liste der Apps angezeigt.

## <a name="error-codes-when-installing-the-app-suite"></a>Fehlercodes beim Installieren der App-Sammlung

In der nachstehenden Tabelle sind die häufigsten Fehlercodes, die auftreten können, sowie deren Bedeutung aufgeführt.

### <a name="status-for-office-csp"></a>Status für Office CSP:

||||
|-|-|-|
|Status|Phase|Beschreibung|
|1460 (ERROR_TIMEOUT)|Herunterladen|Das Office-Bereitstellungstool konnte nicht heruntergeladen werden|    
|13 (ERROR_INVALID_DATA)|-|Die Signatur des heruntergeladenen Office-Bereitstellungstools konnte nicht überprüft werden.|
|Fehlercode aus CertVerifyCertificateChainPolicy|-|Fehlgeschlagene Zertifizierungsprüfung für das heruntergeladene Office-Bereitstellungstool.|    
|997|WIP|Installation|
|0|Nach der Installation|Die Installation war erfolgreich|    
|1603 (ERROR_INSTALL_FAILURE)|-|Alle Voraussetzungsüberprüfungen sind fehlgeschlagen, z.B.:<br>– SxS (Installation wurde versucht, während 2016 MSI installiert wird)<br>– Versionskonflikt<br>usw.|     
|0x8000ffff (E_UNEXPECTED)|-|Es wurde versucht, eine Deinstallation durchzuführen, wenn keine Klick-und-Los-Office-Version auf dem Computer vorhanden ist.|    
|17002|-|Das Szenario (Installation) konnte nicht abgeschlossen werden. Mögliche Gründe:<br>– Die Installation wurde vom Benutzer abgebrochen<br>– Die Installation wurde von einer anderen Installation abgebrochen<br>– Fehlender Speicherplatz auf dem Datenträger während der Installation<br>– Unbekannte Sprach-ID|
|17004|-|Unbekannte SKUs|   


### <a name="office-deployment-tool-error-codes"></a>Fehlercodes der Office-Bereitstellungstools

|||||
|-|-|-|-|
|Szenario|Rückgabecode|Benutzeroberfläche|Hinweis|
|Deinstallationsaufwand, wenn es keine aktive Klick-und-Los-Installation gibt|– 2147418113, 0x8000ffff oder 2147549183|Fehlercode: 30088-1008<br>Fehlercode: 30125-1011 (404)|Office-Bereitstellungstool|
|Installieren, wenn eine MSI-Version installiert wird|1603|-|Office-Bereitstellungstool|
|Die Installation wurde vom Benutzer oder einer anderen Installation abgebrochen|17002|-|Klick-und-Los|
|Versuch, eine 64-Bit-Version auf einem Gerät mit installierter 32-Bit-Version zu installieren|1603|-|Rückgabecode der Office-Bereitstellungstools|
|Versuch, eine unbekannte SKU zu installieren (kein zulässiger Anwendungsfall für Office CSP, da nur gültige SKUs übergeben werden sollen)|17004|-|Klick-und-Los|
|Nicht genügend Speicherplatz|17002|-|Klick-und-Los|
|Der Klick-und-Los-Client konnte nicht gestartet werden (unerwartet)|17000|-|Klick-und-Los|
|Der Klick-und-Los-Client konnte das Szenario nicht in die Warteschlange einreihen (unerwartet)|17001|-|Klick-und-Los|

## <a name="next-steps"></a>Nächste Schritte

Sie können die Apps jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](/intune-azure/manage-apps/deploy-apps).
