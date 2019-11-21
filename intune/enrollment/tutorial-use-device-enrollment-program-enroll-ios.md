---
title: Tutorial – Verwenden von Apple Business Manager oder des Programms zur Geräteregistrierung zum Registrieren von iOS-Geräten in Intune
titleSuffix: Microsoft Intune
description: In diesem Tutorial richten Sie die Apple-Features für Unternehmensgeräteregistrierung über ABM ein, um iOS-Geräte in Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc950f9e60f5549a7a74c2963f33c36369d3ebd3
ms.sourcegitcommit: 5c52879f3653e22bfeba4eef65e2c86025534dab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2019
ms.locfileid: "74126170"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Tutorial: Verwenden der Apple-Features für Unternehmensgeräteregistrierung in Apple Business Manager (ABM) zum Registrieren von iOS-Geräten in Intune
Die Geräteregistrierungsfeatures in Apple Business Manager vereinfachen das Registrieren von Geräten. Intune unterstützt auch das ältere Portal für das Programm zur Geräteregistrierung (Device Enrollment Program, DEP), doch wir empfehlen Ihnen einen Neustart mit Apple Business Manager. Mit Microsoft Intune und der Apple-Unternehmensgeräteregistrierung werden Geräte automatisch sicher registriert, wenn der Benutzer das Gerät zum ersten Mal einschaltet. Sie können Geräte daher für mehrere Benutzer bereitstellen, ohne jedes Gerät einzeln einrichten zu müssen. 

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Abrufen eines Tokens für Apple-Geräteregistrierung
> * Synchronisieren verwalteter Geräte mit Intune
> * Erstellen eines Registrierungsprofils
> * Zuweisen des Registrierungsprofils an Geräte

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
- Geräte, die über [Apple Business Manager](https://business.apple.com) oder das [Apple-Programm zur Geräteregistrierung ](http://deploy.apple.com) erworben wurden
- Die [Autorität für die Verwaltung mobiler Geräte](../fundamentals/mdm-authority-set.md) muss festgelegt sein
- Abrufen eines [Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Abrufen eines Tokens für Apple-Geräteregistrierung
Vor der Registrierung von iOS-Geräten mit den Apple-Features für Unternehmensregistrierung benötigen Sie ein Token für die Apple-Geräteregistrierung, d.h. eine PEM-Datei. Mit diesem Token kann Intune Informationen zu Apple-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile zu Apple hochladen und diesen Profilen Geräte zuweisen.

Sie verwenden das ABM- oder DEP-Portal zum Erstellen eines Tokens für Geräteregistrierung. Sie verwenden die Portale auch, um Intune Geräte zur Verwaltung zuzuweisen.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Hinzufügen** aus.

2. Erteilen Sie Microsoft die Berechtigung, Benutzer- und Geräteinformationen an Apple zu senden, indem Sie auf **Ich stimme zu** klicken.

   ![Screenshot des Bereichs „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom ABM- oder DEP-Portal anzufordern.

4. Wählen Sie **Create a token for Apple's Device Enrollment Program** (Token für das Programm zur Geräteregistrierung von Apple erstellen) aus, um das Portal des Bereitstellungsprogramms von Apple zu öffnen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an. Diese Apple-ID kann später zum Erneuern Ihres DEP-Token verwendet werden.

5. Wählen Sie im [Portal des Bereitstellungsprogramms](https://deploy.apple.com) von Apple die Option **Erste Schritte** für das **Programm zur Geräteregistrierung** aus. Möglicherweise ist Ihr Prozess etwas anders als die folgenden Schritte in [Apple Business Manager](https://business.apple.com).

4. Wählen Sie auf der Seite **Server verwalten** die Option **MDM-Server hinzufügen** aus.

5. Geben Sie *TestMDMServer* als **MDM-Servernamen** ein, und klicken Sie dann auf **Weiter**. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

6. Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet, und die Meldung **Laden Sie Ihren öffentlichen Schlüssel hoch** wird angezeigt. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.

6. Wechseln Sie zu **Bereitstellungsprogramme** > **Programm zur Geräteregistrierung** > **Geräte verwalten**.
7. Wählen Sie **Seriennummer** unter **Choose Devices By** (Geräte auswählen nach) aus. <!--ask Tiffany about this-->

8. Wählen Sie als Nächstes für **Aktion auswählen** die Option **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus. Das Apple-Portal weist die angegebenen Geräte dem Intune-Server für die Verwaltung zu und zeigt dann **Zuweisung abgeschlossen** an.

   Wechseln Sie im Apple-Portal zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Zuweisungsverlauf anzeigen**, um eine Liste der Geräte und ihre MDM-Server-Zuordnung anzuzeigen.

9. Geben Sie die Apple-ID, die zum Erstellen dieses Tokens verwendet wurde, für die zukünftige Verwendung im Azure-Portal in Intune an.

    ![Screenshot der Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. Navigieren Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), und wählen Sie **Öffnen** und dann **Erstellen** aus. 

11. Wenn Sie Bereichsmarkierungen anwenden möchten, um genau festzulegen, welche Administratoren auf dieses Token zugreifen können, wählen Sie „Bereiche“ aus.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils
Nachdem Sie Ihr Token installiert haben, können Sie nun ein Registrierungsprofil für unternehmenseigene iOS-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.

2. Wählen Sie das soeben installierte Token aus, und klicken Sie auf **Profile** > **Profil erstellen**.

3. Geben Sie unter **Profil erstellen** den **Namen** *TestDEPProfile* und die **Beschreibung** *Testing DEP for iOS devices* (Test von DEP für iOS-Geräte) ein. Benutzer können diese Informationen nicht sehen.

4. Wählen Sie unter **Plattform** die Option **iOS** aus.

5. Bestimmen Sie, ob Sie Ihre Geräte mit oder ohne **Benutzeraffinität** registrieren möchten. „Benutzeraffinität“ ist für Geräte vorgesehen, die von bestimmten Benutzern verwendet werden. Wenn Ihre Benutzer das Unternehmensportal für Dienste wie das Installieren von Apps verwenden möchten, wählen Sie **Mit Benutzeraffinität registrieren** aus. Wenn Ihre Benutzer das Unternehmensportal nicht benötigen oder wenn Sie das Gerät für viele Benutzer bereitstellen möchten, wählen Sie **Ohne Benutzeraffinität registrieren** aus.

6. Wenn Sie eine Registrierung mit Benutzeraffinität auswählen, bestimmen Sie, ob Sie „Über das Unternehmensportal authentifizieren“ oder dafür den Setup-Assistenten von Apple verwenden möchten. Wenn Sie die mehrstufige Authentifizierung verwenden möchten, ermöglichen Sie es Benutzern, bei der ersten Anmeldung ihr Kennwort zu ändern, oder fordern Sie die Benutzer auf, ihre abgelaufenen Kennwörter während der Registrierung zurückzusetzen, und wählen Sie unter **Über das Unternehmensportal statt über den Setup-Assistenten von Apple authentifizieren** die Option **Ja** aus. Wenn Sie mit der Verwendung der von Apple bereitgestellten HTTP-Standardauthentifizierung über den Setup-Assistenten vertraut sind, wählen Sie **Nein** aus. Wenn Sie **Ja** auswählen und möchten, dass die Unternehmensportal-App automatisch auf den Geräten der Endbenutzer aktualisiert wird, stellen Sie das Unternehmensportal über das Apple Volume Purchase Program (VPP) separat als erforderliche App für diese Benutzer bereit.

7. Wenn Sie ausgewählt haben, dass Sie mit „Benutzeraffinität“ und „Über das Unternehmensportal authentifizieren“ registrieren möchten, bestimmen Sie, ob Sie „Unternehmensportal mit Apple Volume Purchase Program (VPP)“ installieren möchten. Wenn Sie das Unternehmensportal mit einem VPP-Token installieren, muss Ihr Benutzer keine Apple-ID und kein Kennwort eingeben, um das Unternehmensportal während der Registrierung aus dem App Store herunterzuladen. Wählen Sie unter **Unternehmensportal mit VPP installieren** die Option **Token verwenden:** , um ein VPP-Token auszuwählen, dem kostenlose Lizenzen des Unternehmensportals zur Verfügung stehen. Wenn Sie VPP zum Bereitstellen des Unternehmensportals nicht verwenden möchten, wählen Sie unter **Unternehmensportal mit VPP installieren** die Option **VPP nicht verwenden** aus. 

8. Wenn Sie ausgewählt haben, dass Sie mit „Benutzeraffinität“, „Über das Unternehmensportal authentifizieren“ und „Unternehmensportal mit VPP installieren“ registrieren möchten, entscheiden Sie, ob Sie das Unternehmensportal bis zur Authentifizierung im Einzelanwendungsmodus ausführen möchten. Mithilfe dieser Einstellung können Sie sicherstellen, dass der Benutzer so lange auf keine anderen Apps zugreifen kann, bis er die Unternehmensregistrierung abgeschlossen hat. Wenn Sie den Benutzer bis zum Abschluss der Registrierung auf diesen Ablauf einschränken möchten, wählen Sie unter **Unternehmensportal bis zur Authentifizierung im Einzelanwendungsmodus ausführen** die Option **Ja** aus. 

9. Wählen Sie **Geräteverwaltungseinstellungen**, und dann unter **Überwacht** die Option **Ja** aus. Überwachte Geräte bieten Ihnen die meisten Verwaltungsoptionen für Ihre unternehmenseigenen iOS-Geräte.

10. Wählen Sie unter **Gesperrte Registrierung** die Option **Ja** aus, um sicherzustellen, dass Ihre Benutzer die Verwaltung des unternehmenseigenen Geräts nicht entfernen können. 

11. Wählen Sie unter **Mit Computern synchronisieren** eine Option aus, um zu bestimmen, ob die iOS-Geräte mit Computern synchronisiert werden können.

12. Apple benennt das Gerät standardmäßig mit dem Gerätetyp (z.B. „iPad“). Wenn Sie eine andere Namensvorlage bereitstellen möchten, wählen Sie unter **Vorlage für Gerätenamen anwenden** die Option **Ja** aus. Geben Sie den Namen ein, den Sie auf die Geräte anwenden möchten. Dabei stehen die Zeichenfolgen *{{SERIAL}}* und *{{DEVICETYPE}}* für die Seriennummer und den Gerätetyp jedes Geräts. Wählen Sie andernfalls unter **Vorlage für Gerätenamen anwenden** die Option **Nein** aus.

13. Wählen Sie **OK** aus.

14. Klicken Sie auf **Anpassung den Setup-Assistenten**, und geben Sie *Tutorial department* (Tutorialabteilung) unter **Abteilungsname** ein. Diese Zeichenfolge wird Benutzern angezeigt, wenn sie während der Geräteaktivierung auf **About configuration** (Informationen zur Konfiguration) tippen.

15. Geben Sie unter **Abteilungstelefonnummer** eine Telefonnummer ein. Diese Nummer wird angezeigt, wenn Benutzer während der Aktivierung auf **Need help** (Hilfe) tippen.

16. Während der Geräteaktivierung können Sie eine Vielzahl von Anzeigen **anzeigen** oder **ausblenden**. Um die nahtloseste Registrierung zu ermöglichen, legen Sie für alle Bildschirme **Ausblenden** fest.

17. Klicken Sie auf **OK** > **Erstellen**.

## <a name="sync-managed-devices-to-intune"></a>Synchronisieren verwalteter Geräte mit Intune

Nachdem Sie ein Registrierungsprogrammtoken beim ABM-, ASM- oder DEP-Portal eingerichtet und dort dem MDM-Server Geräte zugewiesen haben, können Sie warten, bis diese Geräte mit dem Intune-Dienst synchronisiert werden oder eine Synchronisierung manuell per Push starten. Ohne eine manuelle Synchronisierung kann es bis zu 24 Stunden dauern, bis Geräte im Azure-Portal angezeigt werden.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken**, wählen Sie ein Token aus der Liste und anschließend **Geräte** > **Synchronisierung** aus.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Zuweisen eines Registrierungsprofils an iOS-Geräte

Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können. Diese Geräte werden mit Intune aus Apple synchronisiert und müssen im ABM-, ASM- oder DEP-Portal dem richtigen MDM-Servertoken zugewiesen werden.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken**, und wählen Sie Ihr Token aus der Liste aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und klicken Sie dann auf **Zuweisen**.

## <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune eingerichtet und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden.

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich auch über die anderen Optionen, die für das Registrieren von iOS-Geräten verfügbar sind.

> [!div class="nextstepaction"]
> [Ausführlicher Artikel zur iOS-DEP-Registrierung](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
