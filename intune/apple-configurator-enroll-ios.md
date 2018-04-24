---
title: Registrierung von iOS-Geräten mit Apple Configurator
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie unternehmenseigene iOS-Geräte mit Apple Configurator und dem Setup-Assistenten registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5ecdd79a029bc3d434ebb0d8ba62ea0e65215f9e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Registrieren von iOS-Geräten mit Apple Configurator

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Temporäre Unterschiede bei der Benutzeroberfläche
>
>Die Benutzeroberflächen für die auf dieser Seite beschriebenen Funktionen werden aktualisiert. Diese Updates werden bis Ende April für alle Benutzerkonten eingeführt.
>
>Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurde Ihr Konto noch nicht für die neue Benutzeroberfläche aktualisiert, und Sie können diese Hilfeseite verwenden.
>
>![Alte Intune-Benutzeroberfläche](./media/appleenroll-oldui.png)
>
>Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurden die Benutzeroberflächen aktualisiert.  Wechseln Sie zu [dieser Hilfeseite](apple-configurator-enroll-ios-newui.md).
>
>![Neue Intune-Benutzeroberfläche](./media/appleenroll-newui.png)

Intune unterstützt die Registrierung von iOS-Geräten mithilfe des Tools [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344), das auf einem Mac-Computer ausgeführt wird. Für die Registrierung mit Apple Configurator müssen Sie jedes iOS-Gerät über USB mit einem Mac-Computer verbinden, um die Unternehmensregistrierung einzurichten. Sie können Geräte mit Apple Configurator auf zwei Arten bei Intune registrieren:
- **Registrierung für Setup-Assistent:** Setzt das Gerät auf die Werkseinstellungen zurück und bereitet es für die Registrierung durch den Einrichtungsassistenten vor.
- **Direkte Registrierung:** Setzt das Gerät nicht auf die Werkseinstellungen zurück und registriert das Gerät über die iOS-Einstellungen. Diese Methode wird nur von Geräten **ohne Benutzeraffinität** unterstützt.

Die Registrierungsmethoden von Apple Configurator können nicht mit dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) verwendet werden.

## <a name="prerequisites"></a>Voraussetzungen

- Physischer Zugriff auf iOS-Geräte
- [Festlegen der Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md)
- [Ein Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- Geräteseriennummern (nur für die Registrierung mit dem Setup-Assistenten)
- USB-Verbindungskabel
- MacOS-Computer führt [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344) aus.

## <a name="create-an-apple-configurator-profile-for-devices"></a>Erstellen eines Apple Configurator-Profils für Geräte

Ein Registrierungsprofil für Geräte definiert die Einstellungen, die während der Registrierung angewandt werden. Diese Einstellungen werden nur einmal angewendet. Führen Sie folgende Schritte aus, um ein Registrierungsprofil zu erstellen, mit dem iOS-Geräte mit Apple Configurator registriert werden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie **auf Geräteregistrierung** > **Apple-Registrierung**.
4. Wählen Sie unter **Apple Configurator-Registrierungseinstellungen verwalten** die Option **AC-Profile** aus.
5. Wählen Sie unter **Apple Configurator-Registrierungsprofile** die Option **Erstellen** aus.
6. Geben Sie einen **Namen** und eine **Beschreibung** für das Profil zu administrativen Zwecken ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld „Name“ zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über dynamische Gruppen in Azure Active Directory.


  ![Der Bildschirm „Profil erstellen“ mit ausgewählter Option „Mit Benutzeraffinität registrieren“](./media/apple-configurator-profile-create.png)

5. Geben Sie die **Benutzeraffinität** an:
   - **Mit Benutzeraffinität registrieren:** Das Gerät muss einem Benutzer mit dem Setup-Assistenten zugewiesen werden und kann dann auf Daten und E-Mails des Unternehmens zugreifen. Die Benutzeraffinität ist für verwaltete Geräte erforderlich, die Benutzern gehören, die das Unternehmensportal verwenden müssen, um Dienste wie z.B. die Installation von Apps nutzen zu können. Wird nur für die Registrierung des Setup-Assistenten unterstützt. Benutzeraffinität erfordert [den Endpunkt WS-Trust 13 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   > [!NOTE]
   > Mehrstufige Authentifizierung (Multifactor authentication, MFA) funktioniert nicht während der Einrichtung der Registrierung mit Benutzeraffinität. Nach der Registrierung funktioniert die MFA auf Geräten wie erwartet. Geräte können Benutzer nicht dazu auffordern, ihr Kennwort zu ändern, wenn sie sich zum ersten Mal anmelden. Außerdem werden Benutzer, deren Kennwörter abgelaufen sind, während der Registrierung nicht aufgefordert, ihr Kennwort zurückzusetzen. Benutzer müssen ihr Kennwort auf einem anderen Gerät zurücksetzen.

   - **Ohne Benutzeraffinität registrieren:** Das Gerät ist keinem Benutzer zugeordnet. Verwenden Sie diese Zuweisung für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps, die eine Benutzerzugehörigkeit erfordern (einschließlich der Unternehmensportal-App, die für die Installation branchenspezifischer Apps verwendet wird), funktionieren nicht. Dies ist für die direkte Anmeldung erforderlich.

6. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="setup-assistant-enrollment"></a>Registrierung mit dem Setup-Assistenten

### <a name="add-apple-configurator-serial-numbers"></a>Hinzufügen von Apple Configurator-Seriennummern

**So fügen Sie Apple Configurator-Seriennummern in Intune hinzu**

1. Erstellen Sie eine Liste mit zwei Spalten, die durch Trennzeichen getrennte werden (CSV), und ohne Header. Fügen Sie die Seriennummer in der linken Spalte und die Details in der rechten Spalte hinzu. Der aktuelle Höchstwert für die Liste ist 5.000 Zeilen. In einem Text-Editor sieht die CSV-Liste wie folgt aus:

   F7TLWCLBX196,Gerätedetails</br>
   DLXQPCWVGHMJ, Gerätedetails

   Erfahren Sie, [wie Sie die Seriennummer eines iOS-Geräts finden](https://support.apple.com/HT204073).
2. Wählen Sie in [Intune im Azure-Portal](https://portal.azure.com) nacheinander die Optionen **Geräteregistrierung** und **Apple-Registrierung** aus.
3. Wählen Sie unter **Apple Configurator-Registrierungseinstellungen verwalten** die Option **Apple Configurator-Geräte** aus.
4. Wählen Sie **Hinzufügen** aus.
5. Wählen Sie ein **Registrierungsprofil** aus, das Sie auf die importierten Seriennummern anwenden möchten. Wenn Sie eine Datei mit neuen Details importieren, die vorhandene Details überschreibt, wählen Sie **Hiermit überschreiben Sie Details für vorhandene Bezeichner** aus.
6. Navigieren Sie zu der CSV-Datei mit den Seriennummern, und wählen Sie **Hinzufügen** aus.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Erneutes Zuweisen eines Profils zu Geräteseriennummern

Ein Registrierungsprofil wird beim Importieren von iOS-Seriennummern für die Registrierung mit Apple Configurator zugewiesen. Mit Intune können Sie auch Profile von zwei verschiedenen Stellen im Azure-Portal zuweisen:
- **Apple Configurator-Geräte**
- **AC-Profile**

#### <a name="assign-from-apple-configurator-devices"></a>Zuweisen über Apple Configurator-Geräte

1. Wählen Sie in [Intune im Azure-Portal](https://portal.azure.com) nacheinander die Optionen **Geräteregistrierung** und **Apple-Registrierung** aus.
2. Wählen Sie unter **Apple Configurator-Geräte** die Seriennummern aus, denen Sie ein Profil zuweisen möchten, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** für das Profil, das Sie zuweisen möchten, **Neues Profil** und dann **Zuweisen** aus.

#### <a name="assign-from-profiles"></a>Zuweisen über Profile
1. Wählen Sie in [Intune im Azure-Portal](https://portal.azure.com) nacheinander die Optionen **Geräteregistrierung** und **Apple-Registrierung** aus.
2. Wählen Sie **AC-Profile** und dann das Profil aus, dem Sie Seriennummern zuweisen möchten.
3. Wählen Sie auf dem Profil die Option **Zugewiesene Geräte** und dann **Zuweisen** aus.
4. Filtern Sie nach den Seriennummern der Geräte, die Sie dem Profil zuweisen möchten, klicken Sie auf die Geräte und dann auf **Zuweisen**.

### <a name="export-the-profile"></a>Exportieren des Profils
Nachdem Sie das Profil erstellt und die Seriennummern zugewiesen haben, müssen Sie das Profil aus Intune als URL exportieren. Anschließend importieren Sie es in Apple Configurator auf einem Mac, um es für Geräte bereitzustellen.

1. Wählen Sie in Intune im [Azure-Portal](https://portal.azure.com), die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **AC-Profile** und dann das zu exportierende Profil aus.
2. Wählen Sie auf dem Profil **Profil exportieren** aus.

   ![Blatt „Profil exportieren“ für die Registrierung des Setup-Assistenten mit hervorgehobener Profil-URL](./media/ios-apple-configurator-expor-sat.png)
3. Kopieren Sie die Profil-URL. Sie können sie später in Apple Configurator hinzufügen, um das von iOS-Geräten verwendete Intune-Profil zu definieren.

   Importieren Sie dieses Profil anschließend mithilfe der folgenden Prozedur in Apple Configurator, um das von iOS-Geräten verwendete Intune-Profil zu definieren.

### <a name="enroll-devices-with-setup-assistant"></a>Registrieren von Geräten mithilfe des Setup-Assistenten

1. Öffnen Sie auf einem Mac-Computer **Apple Configurator 2**. Wählen Sie in der Menüleiste **Apple Configurator 2**, und wählen Sie dann **Voreinstellungen**.
   > [!WARNING]
   > Während des Registrierungsprozesses werden die Geräte auf Werkseinstellungen zurückgesetzt. Als bewährte Methode empfiehlt es sich, das Gerät zurückzusetzen und einzuschalten. Nach dem Verbinden eines Geräts sollte der **Begrüßungsbildschirm** angezeigt werden.

2. Wählen Sie im Bereich **Voreinstellungen** die Option **Server** und dann das Pluszeichen (+) aus, um den MDM-Server-Assistenten zu starten. Klicken Sie auf **Weiter**.
3. Geben Sie den **Hostnamen oder die URL** und die **Registrierungs-URL** für den MDM-Server unter „Registrierung von iOS-Geräten bei Microsoft Intune über den Setup-Assistenten“. Geben Sie für die Registrierungs-URL die aus Intune exportierte Registrierungsprofil-URL ein. Klicken Sie auf **Weiter**.  

   Sie können die Warnung, dass die Server-URL nicht überprüft wird, problemlos ignorieren. Um den Vorgang fortzusetzen, wählen Sie **Weiter**, bis der Assistent abgeschlossen ist.
4. Verbinden Sie die mobilen iOS-Geräte über einen USB-Adapter mit dem Mac-Computer.
5. Wählen Sie die iOS-Geräte aus, die Sie verwalten möchten, und wählen Sie dann **Vorbereiten** aus. Wählen Sie im Bereich **iOS-Gerät vorbereiten** die Option **Manuell** aus, und wählen Sie dann **Weiter**.
6. Wählen Sie im Bereich **Beim MDM-Server registrieren** den erstellten Servernamen und dann **Weiter** aus.
7. Wählen Sie im Bereich **Geräte überwachen** den Grad der Überwachung aus, und wählen Sie dann **Weiter**.
8. Wählen Sie im Bereich **Organisation erstellen** die **Organisation** aus, oder erstellen Sie eine neue Organisation, und wählen Sie dann **Weiter** aus.
9. Wählen Sie im Bereich **iOS-Setup-Assistenten konfigurieren** die Schritte aus, die dem Benutzer angezeigt werden sollen, und wählen Sie dann **Vorbereiten** aus. Authentifizieren Sie sich, wenn Sie dazu aufgefordert werden, um die Vertrauenseinstellungen zu aktualisieren.  
10. Trennen Sie das USB-Kabel, wenn die Vorbereitung des iOS-Geräts abgeschlossen ist.  

### <a name="distribute-devices"></a>Verteilen von Geräten
Die Geräte sind nun für die Unternehmensregistrierung bereit. Schalten Sie die Geräte aus, und verteilen Sie sie an Benutzer. Wenn die Benutzer die Geräte einschalten, wird der Setup-Assistent gestartet.

Nachdem Benutzer ihre Geräte erhalten haben, müssen sie den Setup-Assistenten ausführen. Auf mit Benutzeraffinität konfigurierten Geräte kann die Unternehmensportal-App installiert und ausgeführt werden, um Apps herunterzuladen und Geräte zu verwalten.

## <a name="direct-enrollment"></a>Direkte Registrierung
Wenn Sie iOS-Geräte direkt mit Apple Configurator registrieren, können Sie ein Gerät registrieren, ohne die Seriennummer des Geräts abrufen zu müssen. Sie können dem Gerät zu Identifikationszwecken auch einen Namen zuweisen, bevor Intune den Gerätenamen während der Registrierung erfasst. Die Unternehmensportal-App wird für direkt registrierte Geräte nicht unterstützt. Eine Zurücksetzung des Geräts auf Werkseinstellungen ist bei dieser Vorgehensweise nicht erforderlich.

Apps, die eine Benutzerzugehörigkeit erfordern (einschließlich der Unternehmensportal-App für die Installation branchenspezifischer Apps), werden nicht installiert.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportieren des Profil als MOBILECONFIG-Datei auf iOS-Geräte
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie unter **Profil exportieren** die Option **Profil herunterladen** aus, um das Registrierungsprofil herunterzuladen.


  ![Blatt „Profil exportieren“ für die Registrierung des Setup-Assistenten mit hervorgehobener Profil-URL](./media/ios-apple-configurator-expor-de.png)

2. Übertragen Sie die Datei auf einen Mac-Computer, auf dem [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) ausgeführt wird, um sie direkt per Push als Verwaltungsprofil auf iOS-Geräte zu verschieben.
3. Bereiten Sie das Gerät mit Apple Configurator mithilfe der folgenden Schritte vor.
   1. Öffnen Sie auf einem Mac-Computer Apple Configurator 2.0.
   2. Verbinden Sie das iOS-Gerät mit dem Mac-Computer über ein USB-Kabel. Schließen Sie Fotos, iTunes und andere Apps, die für das Gerät geöffnet werden, wenn das Gerät erkannt wird.
   3. Wählen Sie in Apple Configurator das verbundene iOS-Gerät und anschließend die Schaltfläche **Hinzufügen** aus. Optionen, die dem Gerät hinzugefügt werden können, werden in der Dropdownliste angezeigt. Wählen Sie **Profile** aus.

      ![Blatt „Profil exportieren“ für die Registrierung des Setup-Assistenten mit hervorgehobener Profil-URL](./media/ios-apple-configurator-add-profile.png)

   4. Verwenden Sie die Dateiauswahl zum Auswählen der aus Intune exportierten MOBILECONFIG-Datei, und wählen Sie anschließend **Hinzufügen** aus. Das Profil wird zum Gerät hinzugefügt. Wenn das Gerät nicht überwacht wird, muss der Installation auf dem Gerät zugestimmt werden.

4. Installieren Sie das Profil nun anhand der folgenden Schritte auf dem iOS-Gerät. Auf dem Gerät muss der Setup-Assistent ausgeführt worden sein, und es muss einsatzbereit sein. Wenn bei der Registrierung Apps bereitgestellt werden müssen, sollten Sie über eine Apple-ID verfügen, da Sie für App-Bereitstellungen mit einer Apple-ID beim App Store angemeldet sein müssen.
   1. Entsperren Sie das iOS-Gerät.
   2. Wählen Sie im Dialogfeld **Profil installieren** für das **Verwaltungsprofil** die Option **Installieren** aus.
   3. Geben Sie die Gerätekennung oder die Apple-ID ein, falls notwendig.
   4. Akzeptieren Sie die **Warnung**, und wählen Sie **Installieren** aus.
   5. Akzeptieren Sie die **Remotewarnung**, und wählen Sie **Vertrauen** aus.
   6. Wenn mit der Meldung **Profil installiert** bestätigt wird, dass das Profil installiert wurde, wählen Sie **Fertig** aus.

5. Öffnen Sie auf dem iOS-Gerät **Einstellungen**, und wechseln Sie zu **Allgemein** > **Geräteverwaltung** > **Verwaltungsprofil**. Vergewissern Sie sich, dass die Profilinstallation aufgelistet ist, und überprüfen Sie die iOS-Richtlinieneinschränkungen und die installierten Apps. Es kann bis zu 10 Minuten dauern, bis Richtlinieneinschränkungen und Apps auf dem Gerät angezeigt werden.

6. Verteilen von Geräten. Das iOS-Gerät ist jetzt bei Intune registriert und wird verwaltet.


