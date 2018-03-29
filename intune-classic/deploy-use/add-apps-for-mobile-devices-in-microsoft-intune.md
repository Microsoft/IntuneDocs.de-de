---
title: Hinzufügen von Apps für registrierte Geräte
description: Bevor Sie eine App bereitstellen können, müssen Sie sie zu Intune hinzufügen. Anschließend ist sie in der Intune-Konsole verfügbar, und Sie können sie verwalten und bereitstellen.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 01/11/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f5fec22a17eef39819b38567793a2f579815e59
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="add-apps-for-enrolled-devices-to-intune"></a>Hinzufügen von Apps für registrierte Geräte zu Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Bevor Sie eine App bereitstellen oder verwalten können, müssen Sie sie zu Microsoft Intune hinzufügen. In diesem Thema wird Ihnen gezeigt, wie Sie Apps für registrierte Geräte hinzufügen.


> [!IMPORTANT]
> Die Informationen in diesem Thema helfen Ihnen dabei die Apps hinzuzufügen, die Sie auf registrierten Geräten und registrierten Windows-PCs bereitstellen möchten. Wenn Sie Apps für Windows-PCs hinzufügen möchten, die Sie mithilfe der Intune-Clientsoftware verwalten, finden Sie weitere Informationen unter [Hinzufügen von Apps für Windows-PCs in Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## <a name="add-the-app"></a>Hinzufügen der App
Sie verwenden den Intune-Softwareherausgeber, um die Eigenschaften der App zu konfigurieren und sie, falls zutreffend, in Ihren Cloudspeicher hochzuladen. Gehen Sie wie folgt vor:

1.  Wählen Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) die Option **Apps** &gt; **Apps hinzufügen**, um den Intune-Softwareherausgeber zu starten.

    > [!TIP]
    > Möglicherweise müssen Sie Ihren Intune-Benutzernamen und das Kennwort eingeben, bevor der Softwareherausgeber gestartet wird.

2.  Wählen Sie auf der Seite **Softwaresetup** des Herausgebers eine der folgenden Optionen für **Wählen Sie aus, wie diese Software für Geräte bereitgestellt werden soll** aus:
    - **Softwareinstallationsprogramm**: Für Apps mit der Erweiterung **MSI**:
        - **Wählen Sie den Dateityp des Softwareinstallationsprogramms aus**. Hiermit wird die Art der Software angegeben, die Sie bereitstellen möchten. Wenn Sie z. B. eine iOS-App bereitstellen möchten, wählen Sie **App-Paket für iOS (IPA-Datei)** aus.
        - **Geben Sie den Speicherort der Softwaresetupdateien an**. Geben Sie den Speicherort der Installationsdateien ein, oder wählen Sie **Durchsuchen** aus, um den Speicherort in einer Liste auszuwählen.
        - **Weitere Dateien und Unterordner aus dem gleichen Ordner einschließen**. Diese Option ist nur für den Dateityp **Windows Installer** verfügbar.<br>Mitunter sind für eine Software, bei der Windows Installer verwendet wird, unterstützende Dateien erforderlich, die sich meist im gleichen Ordner befinden wie die Installationsdateien. Wählen Sie diese Option aus, wenn Sie auch diese Dateien bereitstellen möchten.<br>Bei diesem Installationstyp wird etwas Cloudspeicherplatz in Anspruch genommen.

  -   **Externe Verknüpfung**: Für Apps, die Sie durch Angeben eines Links zu einem App-Store erstellen möchten:

        - **Geben Sie die URL an**. Geben Sie die URL für eine der folgenden Optionen an:
            - App Store-URL der App, die Sie bereitstellen möchten. Wenn Sie z.B. die Microsoft-Remotedesktop-App für Android bereitstellen möchten, geben Sie **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android** an.<br>Suchen Sie die URL der App, indem Sie mithilfe einer Suchmaschine nach der App Store-Seite suchen, die die App enthält. Um z. B. die Remotedesktop-App zu finden, können Sie nach **Microsoft-Remotedesktop-App für Android** suchen.
            - Eine Website. Intune stellt ein Verknüpfungssymbol für die Website auf dem Gerät (Webclip genannt) bereit.
            - App im Web. Intune stellt ein Verknüpfungssymbol für die App auf dem Gerät bereit.
        - **Fordern Sie zum Öffnen dieses Links Managed Browser an (nur Android und iOS)**. Wenn Sie einen Link zu einer Website oder Web-App für Benutzer bereitstellen, können sie diesen nur im Intune Managed Browser öffnen. Dieser Browser muss auf ihrem Gerät installiert sein.<br>Weitere Informationen zum Managed Browser finden Sie unter [Verwalten des Internetzugriffs mittels Managed Browser-Richtlinien mit Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).<br>Bei diesem Installationstyp wird kein Cloudspeicherplatz in Anspruch genommen.

  -   **Verwaltete iOS-App aus dem App Store**: Für kostenlose Apps aus dem iTunes-Store, die Sie mit MAM-Richtlinien (mobile Anwendungsverwaltung) verwalten möchten:

        - **Geben Sie die URL an**. Geben Sie die App Store-URL der App ein, die Sie bereitstellen möchten. Wenn Sie z.B. die Microsoft-Arbeitsordner-App für iOS bereitstellen möchten, geben Sie **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8** an.<br>Bei diesem Installationstyp wird kein Cloudspeicherplatz in Anspruch genommen.

        Wenn Sie z. B. die Microsoft Word-App aus dem iTunes Store auf Geräten bereitstellen möchten, würde die Seite wie folgt aussehen:

        ![Intune-Softwareherausgeber](./media/publisher-for-mobile.png)

> [!NOTE]
> Wenn Sie eine App aus einem Store hinzufügen und bereitstellen, müssen Endbenutzer über ein Konto bei diesem Store verfügen, um die App installieren zu können.

3.  Konfigurieren Sie auf der Seite **Softwarebeschreibung** Folgendes:

    > [!TIP]
    > Je nach Art des verwendeten Installationsprogramms werden einige dieser Werte möglicherweise automatisch eingetragen.

    - **Herausgeber**. Geben Sie den Namen des Herausgebers der App ein.
    - **Name**. Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird.<br>Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung**. Geben Sie eine Beschreibung der App ein. Diese Beschreibung wird den Benutzern im Unternehmensportal angezeigt.
    - **URL für Softwareinformationen**. Nur verfügbar, wenn Sie **Softwareinstallationsprogramm** ausgewählt haben. Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**. Nur verfügbar, wenn Sie **Softwareinstallationsprogramm** ausgewählt haben. Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **Kategorie** (optional). Wählen Sie eine der integrierten App-Kategorien aus. Dadurch wird es für die Benutzer leichter, die App im Unternehmensportal zu finden.
    - **Als ausgewählte App anzeigen und im Unternehmensportal hervorheben**. Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Symbol** (optional). Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dies ist das Symbol, das gemeinsam mit der App angezeigt wird, wenn die Benutzer das Unternehmensportal durchsuchen.

        In diesem Beispiel haben Sie eine Beschreibung für die Microsoft Word-App für iOS konfiguriert:

        ![Beispiel zur Softwarebeschreibung](./media/ios-software-description.png)

4.  Legen Sie auf der Seite **Anforderungen** die Anforderungen fest, die erfüllt sein müssen, bevor die App auf einem Gerät installiert werden kann. Zum Beispiel können Sie bei einem App-Paket für iOS die erforderliche Mindestversion von iOS festlegen. Darüber hinaus können Sie den erforderlichen Gerätetyp auswählen, z. B. iPhone oder iPad.

    > [!TIP]
    > Die Seite **Anforderungen** wird nicht bei allen Arten von Apps angezeigt.

5.  Wenn Sie den Dateityp **Windows Installer** auswählen, werden weitere Assistentenseiten angezeigt. Dieser Dateityp wird verwendet, wenn Sie Software auf PCs mit Windows 10 oder höher bereitstellen, die bei Intune registriert sind.

6.  Überprüfen Sie auf der Seite **Zusammenfassung** die von Ihnen angegebenen Informationen. Sobald Sie bereit sind, wählen Sie **Hochladen** aus.

7.  Wählen Sie **Schließen**, um den Vorgang abzuschließen.

Die App wird im Arbeitsbereich **Apps** im Knoten **Apps** angezeigt.

## <a name="example---deploying-msi-applications-to-windows-10-devices"></a>Beispiel: Bereitstellen von MSI-Anwendungen für Windows 10-Geräte
In diesem vierminütigen Video erfahren Sie, wie Sie MSI-Anwendungen (Windows Installer) auf registrierten Geräten mit Windows 10 bereitstellen.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine App erstellt haben, umfasst der nächste Schritt die Bereitstellung. Weitere Informationen finden Sie unter [Bereitstellen von Apps in Microsoft Intune](deploy-apps.md).
