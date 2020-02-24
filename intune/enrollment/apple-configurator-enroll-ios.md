---
title: Registrieren von iOS-/iPadOS-Geräten – Apple Configurator und Setup-Assistent
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmenseigene iOS-/iPadOS-Geräte mit Apple Configurator und dem Setup-Assistenten registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ccd41b6ebc9bdf62c1603e508cb881a1be62ee7
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415402"
---
# <a name="set-up-iosipados-device-enrollment-with-apple-configurator"></a>Einrichten der iOS-/iPadOS-Geräteregistrierung mit Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune unterstützt die Registrierung von iOS-/iPadOS-Geräten mithilfe des Tools [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344), das auf einem Mac-Computer ausgeführt wird. Für die Registrierung mit Apple Configurator müssen Sie jedes iOS-/iPadOS-Gerät über USB mit einem Mac-Computer verbinden, um die Unternehmensregistrierung einzurichten. Sie können Geräte mit Apple Configurator auf zwei Arten bei Intune registrieren:
- **Registrierung für Einrichtungsassistent:** Setzt das Gerät zurück und bereitet es auf die Registrierung beim Einrichtungsassistenten vor.
- **Direkte Registrierung:** Setzt das Gerät nicht zurück und registriert das Gerät über die iOS-/iPadOS-Einstellungen. Diese Methode wird nur von Geräten **ohne Benutzeraffinität** unterstützt.

Die Registrierungsmethoden von Apple Configurator können nicht mit dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) verwendet werden.

## <a name="prerequisites"></a>Voraussetzungen

- Physischer Zugriff auf iOS-/iPadOS-Geräte
- [Festlegen der Autorität für die Verwaltung mobiler Geräte](../fundamentals/mdm-authority-set.md)
- [Ein Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- Geräteseriennummern (nur für die Registrierung mit dem Setup-Assistenten)
- USB-Verbindungskabel
- MacOS-Computer führt [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) aus.

## <a name="create-an-apple-configurator-profile-for-devices"></a>Erstellen eines Apple Configurator-Profils für Geräte

Ein Registrierungsprofil für Geräte definiert die Einstellungen, die während der Registrierung angewandt werden. Diese Einstellungen werden nur einmal angewendet. Führen Sie folgende Schritte aus, um ein Registrierungsprofil zu erstellen, mit dem iOS-/iPadOS-Geräte mit Apple Configurator registriert werden.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Profile** > **Erstellen** aus.

    ![Erstellen eines Profils für Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. Geben Sie zu administrativen Zwecken unter **Registrierungsprofil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld „Name“ zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über dynamische Gruppen in Azure Active Directory.

    ![Screenshot des Bildschirms „Profil erstellen“ mit ausgewählter Option „Mit Benutzeraffinität registrieren“](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. Wählen Sie unter **Benutzeraffinität** aus, ob sich Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registrieren müssen.

    - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und das Unternehmensportal verwenden sollen, um Dienste wie z. B. die Installation von Apps nutzen zu können. Das Gerät muss mit dem Setup-Assistenten einem Benutzer zugewiesen werden und kann dann auf Unternehmensdaten und E-Mails zugreifen. Wird nur für die Registrierung des Setup-Assistenten unterstützt. Benutzeraffinität erfordert [den Endpunkt WS-Trust 13 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [Weitere Informationen](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)

    - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die keinem einzelnen Benutzer zugeordnet sind. Verwenden Sie diese Option für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps, die eine Benutzerzugehörigkeit erfordern (einschließlich der Unternehmensportal-App, die für die Installation branchenspezifischer Apps verwendet wird), funktionieren nicht. Dies ist für die direkte Anmeldung erforderlich.

     > [!NOTE]
     > Wenn **Mit Benutzeraffinität registrieren** ausgewählt ist, stellen Sie sicher, dass das Gerät innerhalb der ersten 24 Stunden der Registrierung mit dem Setup-Assistenten einem Benutzer zugeordnet wird. Andernfalls schlägt die Registrierung möglicherweise fehl, und es wird eine Zurücksetzung auf Werkseinstellungen erforderlich, um das Gerät zu registrieren.

4. Wenn Sie **Mit Benutzeraffinität registrieren** ausgewählt haben, können Sie die Benutzerauthentifizierung über das Unternehmensportal statt über den Apple-Setup-Assistenten erlauben.

    > [!NOTE]
    > Wenn Sie einen der folgenden Schritte ausführen möchten, legen Sie **Über das Unternehmensportal statt über den Setup-Assistenten authentifizieren** auf **Ja** fest.
    >    - Sie möchten die mehrstufige Authentifizierung verwenden.
    >    - Sie möchten Benutzer zum Ändern ihres Kennworts auffordern, wenn sie sich zum ersten Mal anmelden.
    >    - Sie möchten Benutzer dazu auffordern, ihre abgelaufenen Kennwörter bei der Registrierung zurückzusetzen.
    >
    > Diese Optionen werden für die Authentifizierung beim Setup-Assistenten von Apple nicht unterstützt.


6. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="setup-assistant-enrollment"></a>Registrierung mit dem Setup-Assistenten

### <a name="add-apple-configurator-serial-numbers"></a>Hinzufügen von Apple Configurator-Seriennummern

1. Erstellen Sie eine Liste mit zwei Spalten, die durch Trennzeichen getrennte werden (CSV), und ohne Header. Fügen Sie die Seriennummer in der linken Spalte und die Details in der rechten Spalte hinzu. Der aktuelle Höchstwert für die Liste ist 5.000 Zeilen. In einem Text-Editor sieht die CSV-Liste wie folgt aus:

    F7TLWCLBX196,Gerätedetails</br>
    DLXQPCWVGHMJ, Gerätedetails

   Erfahren Sie, [wie Sie die Seriennummer eines iOS-/iPadOS-Geräts finden](https://support.apple.com/HT204073).
2. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Geräte** > **Hinzufügen** aus.

5. Wählen Sie ein **Registrierungsprofil** aus, das Sie auf die importierten Seriennummern anwenden möchten. Wenn die Details der neuen Seriennummer alle vorhandenen Details überschreiben sollen, aktivieren Sie **Hiermit überschreiben Sie Details für vorhandene Bezeichner**.
6. Navigieren Sie unter **Geräte importieren** zu der CSV-Datei mit den Seriennummern, und wählen Sie **Hinzufügen** aus.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Erneutes Zuweisen eines Profils zu Geräteseriennummern

Sie können ein Registrierungsprofil beim Importieren von iOS-/iPadOS-Seriennummern für die Registrierung mit Apple Configurator zuweisen. Sie können Profile auch an zwei verschiedenen Stellen im Azure-Portal zuweisen:
- **Apple Configurator-Geräte**
- **AC-Profile**

#### <a name="assign-from-apple-configurator-devices"></a>Zuweisen über Apple Configurator-Geräte
1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Geräte**, wählen Sie die Seriennummern aus und dann **Profil zuweisen**.
2. Wählen Sie unter **Profil zuweisen** für das Profil, das Sie zuweisen möchten, **Neues Profil** und dann **Zuweisen** aus.

#### <a name="assign-from-profiles"></a>Zuweisen über Profile
1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Profile** und dann ein Profil aus.
2. Wählen Sie im Profil die Option **Zugewiesene Geräte** und dann **Zuweisen** aus.
3. Filtern Sie nach den Seriennummern der Geräte, die Sie dem Profil zuweisen möchten, klicken Sie auf die Geräte und dann auf **Zuweisen**.

### <a name="export-the-profile"></a>Exportieren des Profils
Nachdem Sie das Profil erstellt und die Seriennummern zugewiesen haben, müssen Sie das Profil aus Intune als URL exportieren. Anschließend importieren Sie es in Apple Configurator auf einem Mac, um es für Geräte bereitzustellen.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Profile** und dann das zu exportierende Profil aus.
2. Wählen Sie auf dem Profil **Profil exportieren** aus.
3. Kopieren Sie die **Profil-URL**. Sie können sie später in Apple Configurator hinzufügen, um das von iOS-/iPadOS-Geräten verwendete Intune-Profil zu definieren.

   Importieren Sie dieses Profil anschließend mithilfe der folgenden Prozedur in Apple Configurator, um das von iOS-/iPadOS-Geräten verwendete Intune-Profil zu definieren.

### <a name="enroll-devices-with-setup-assistant"></a>Registrieren von Geräten mithilfe des Setup-Assistenten

1. Öffnen Sie auf einem Mac-Computer **Apple Configurator 2**. Wählen Sie in der Menüleiste **Apple Configurator 2**, und wählen Sie dann **Voreinstellungen**.
    > [!WARNING]
    > Während des Registrierungsprozesses werden die Geräte auf Werkseinstellungen zurückgesetzt. Als bewährte Methode empfiehlt es sich, das Gerät zurückzusetzen und einzuschalten. Nach dem Verbinden eines Geräts sollte der **Begrüßungsbildschirm** angezeigt werden.
    > Wenn das Gerät bereits mit dem Apple-ID-Konto registriert wurde, muss das Gerät vor Beginn des Registrierungsprozesses aus der Apple-iCloud gelöscht werden. Der Eingabeaufforderungsfehler „[Gerätename] konnte nicht aktiviert werden“ wird angezeigt.

2. Wählen Sie im Bereich **Voreinstellungen** die Option **Server** und dann das Pluszeichen (+) aus, um den MDM-Server-Assistenten zu starten. Wählen Sie **Weiter** aus.
3. Geben Sie den **Hostnamen oder die URL** und die **Registrierungs-URL** für den MDM-Server unter „Registrierung von iOS-/iPadOS-Geräten bei Microsoft Intune über den Setup-Assistenten“ ein. Geben Sie für die Registrierungs-URL die aus Intune exportierte Registrierungsprofil-URL ein. Wählen Sie **Weiter** aus.  
    Sie können die Warnung, dass die Server-URL nicht überprüft wird, problemlos ignorieren. Um den Vorgang fortzusetzen, wählen Sie **Weiter**, bis der Assistent abgeschlossen ist.
4. Verbinden Sie die mobilen iOS-/iPadOS-Geräte über einen USB-Adapter mit dem Mac-Computer.
5. Wählen Sie die iOS-/iPadOS-Geräte aus, die Sie verwalten möchten, und wählen Sie dann **Vorbereiten** aus. Wählen Sie im Bereich **iOS-/iPadOS-Gerät vorbereiten** die Option **Manuell** und dann **Weiter** aus.
6. Wählen Sie im Bereich **Beim MDM-Server registrieren** den erstellten Servernamen und dann **Weiter** aus.
7. Wählen Sie im Bereich **Geräte überwachen** den Grad der Überwachung aus, und wählen Sie dann **Weiter**.
8. Wählen Sie im Bereich **Organisation erstellen** die **Organisation** aus, oder erstellen Sie eine neue Organisation, und wählen Sie dann **Weiter** aus.
9. Wählen Sie im Bereich **iOS-/iPadOS-Setup-Assistenten konfigurieren** die Schritte aus, die dem Benutzer angezeigt werden sollen, und wählen Sie dann **Vorbereiten** aus. Authentifizieren Sie sich, wenn Sie dazu aufgefordert werden, um die Vertrauenseinstellungen zu aktualisieren.  
10. Trennen Sie das USB-Kabel, wenn die Vorbereitung des iOS-/iPadOS-Geräts abgeschlossen ist.  

### <a name="distribute-devices"></a>Verteilen von Geräten
Die Geräte sind nun bereit zur Unternehmensregistrierung. Schalten Sie die Geräte aus, und verteilen Sie sie an Benutzer. Wenn die Benutzer die Geräte einschalten, wird der Setup-Assistent gestartet.

Nachdem Benutzer ihre Geräte erhalten haben, müssen sie den Setup-Assistenten ausführen. Auf mit Benutzeraffinität konfigurierten Geräte kann die Unternehmensportal-App installiert und ausgeführt werden, um Apps herunterzuladen und Geräte zu verwalten.

## <a name="direct-enrollment"></a>Direkte Registrierung
Wenn Sie iOS-/iPadOS-Geräte direkt mit Apple Configurator registrieren, können Sie ein Gerät registrieren, ohne die Seriennummer des Geräts abrufen zu müssen. Sie können dem Gerät zu Identifikationszwecken auch einen Namen zuweisen, bevor Intune den Gerätenamen während der Registrierung erfasst. Die Unternehmensportal-App wird für direkt registrierte Geräte nicht unterstützt. Durch diese Methode wird das Gerät nicht auf Werkseinstellungen zurückgesetzt.

Apps, die eine Benutzerzugehörigkeit erfordern (einschließlich der Unternehmensportal-App für die Installation branchenspezifischer Apps), werden nicht installiert.

### <a name="export-the-profile-as-mobileconfig-to-iosipados-devices"></a>Exportieren des Profils als MOBILECONFIG-Datei auf iOS-/iPadOS-Geräte

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **iOS** > **iOS-Registrierung** > **Apple Configurator** > **Profile**, wählen Sie das zu exportierende Profil und anschließend **exportieren** aus.
2. Wählen Sie unter **Direkte Registrierung** die Option **Profil herunterladen** aus, und speichern Sie die Datei. Eine Registrierungsprofildatei ist nur zwei Wochen gültig. Danach muss sie neu erstellt werden.
3. Übertragen Sie die Datei auf einen Mac-Computer, auf dem [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) ausgeführt wird, um sie direkt per Push als Verwaltungsprofil auf iOS-/iPadOS-Geräte zu verschieben.
4. Bereiten Sie das Gerät mit Apple Configurator mithilfe der folgenden Schritte vor:
    1. Öffnen Sie auf einem Mac-Computer Apple Configurator 2.0.
    2. Verbinden Sie das iOS-/iPadOS-Gerät über ein USB-Kabel mit dem Mac-Computer. Schließen Sie Fotos, iTunes und andere Apps, die für das Gerät geöffnet werden, wenn das Gerät erkannt wird.
    3. Wählen Sie in Apple Configurator das verbundene iOS-/iPadOS-Gerät und anschließend die Schaltfläche **Hinzufügen** aus. Optionen, die dem Gerät hinzugefügt werden können, werden in der Dropdownliste angezeigt. Wählen Sie **Profile** aus.

        ![Screenshot des Blatts „Profil exportieren“ für die Registrierung des Setup-Assistenten mit hervorgehobener Profil-URL](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Verwenden Sie die Dateiauswahl zum Auswählen der aus Intune exportierten MOBILECONFIG-Datei, und wählen Sie anschließend **Hinzufügen** aus. Das Profil wird zum Gerät hinzugefügt. Wenn das Gerät nicht überwacht wird, muss der Installation auf dem Gerät zugestimmt werden.
5. Installieren Sie das Profil nun mit den folgenden Schritte auf dem iOS-/iPadOS-Gerät. Auf dem Gerät muss der Setup-Assistent ausgeführt worden sein, und es muss einsatzbereit sein. Wenn bei der Registrierung Apps bereitgestellt werden müssen, sollten Sie über eine Apple-ID verfügen, da Sie für App-Bereitstellungen mit einer Apple-ID beim App Store angemeldet sein müssen.
    1. Entsperren Sie das iOS-/iPadOS-Gerät.
    2. Wählen Sie im Dialogfeld **Profil installieren** für das **Verwaltungsprofil** die Option **Installieren** aus.
    3. Geben Sie die Gerätekennung oder die Apple-ID ein, falls notwendig.
    4. Akzeptieren Sie die **Warnung**, und wählen Sie **Installieren** aus.
    5. Akzeptieren Sie die **Remotewarnung**, und wählen Sie **Vertrauen** aus.
    6. Wenn mit der Meldung **Profil installiert** bestätigt wird, dass das Profil installiert wurde, wählen Sie **Fertig** aus.

6. Öffnen Sie auf dem iOS-/iPadOS-Gerät **Einstellungen**, und wechseln Sie zu **Allgemein** > **Geräteverwaltung** > **Verwaltungsprofil**. Vergewissern Sie sich, dass die Profilinstallation aufgelistet ist, und überprüfen Sie die iOS-/iPadOS-Richtlinieneinschränkungen und die installierten Apps. Es kann bis zu 10 Minuten dauern, bis Richtlinieneinschränkungen und Apps auf dem Gerät angezeigt werden.

7. Verteilen von Geräten. Das iOS-/iPadOS-Gerät ist jetzt bei Intune registriert und wird verwaltet.





