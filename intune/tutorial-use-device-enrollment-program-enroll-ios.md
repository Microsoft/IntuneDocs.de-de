---
title: 'Tutorial: Verwenden des Programms zur Geräteregistrierung zum Registrieren von iOS-Geräten in Intune'
titleSuffix: Microsoft Intune
description: In diesem Tutorial richten Sie das Programm zur Geräteregistrierung (DEP, Device Enrollment Program) von Apple ein, um iOS-Geräte in Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.openlocfilehash: d3fd7d860661f7b97e1191b1977b7f75ca02730f
ms.sourcegitcommit: bd5d0bde931cbd3a31ddaeb91a934068cb8a5da8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55482555"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Tutorial: Verwenden des Programms zur Geräteregistrierung zum Registrieren von iOS-Geräten in Intune
Das Programm zur Geräteregistrierung (DEP, Device Enrollment Program) von Apple vereinfacht das Registrieren von Geräten. Mit Microsoft Intune und dem DEP werden Geräte automatisch registriert, wenn der Benutzer das Gerät zum ersten Mal einschaltet. Sie können Geräte daher für mehrere Benutzer bereitstellen, ohne jedes Gerät einzeln einrichten zu müssen. 

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Abrufen eines Apple-DEP-Tokens
> * Erstellen einer Autopilot-Gerätegruppe
> * Erstellen eines Autopilot-Bereitstellungsprofils
> * Zuweisen des Autopilot-Bereitstellungsprofils zur Gerätegruppe
> * Verteilen von Windows-Geräten an Benutzer

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
- Geräte, die unter dem [Programm zur Geräteregistrierung von Apple](http://deploy.apple.com) erworben werden.
- Die [Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md) muss festgelegt sein
- Abrufen eines [Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Abrufen eines Apple-DEP-Tokens
Bevor Sie iOS-Geräte mit dem DEP registrieren können, benötigen Sie eine Apple-DEP-Tokendatei (.pem). Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile zu Apple hochladen und diesen Profilen Geräte zuweisen.

Verwenden Sie das Apple DEP-Portal, um ein DEP-Token zu erstellen. Sie verwenden das DEP-Portal auch, um in Intune Geräte für die Verwaltung zuzuweisen.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Hinzufügen** aus.

2. Erteilen Sie Microsoft die Berechtigung, Benutzer- und Geräteinformationen an Apple zu senden, indem Sie auf **Ich stimme zu** klicken.

   ![Screenshot des Bereichs „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.

4. Wählen Sie **Create a token for Apple's Device Enrollment Program** (Token für das Programm zur Geräteregistrierung von Apple erstellen) aus, um das Portal des Bereitstellungsprogramms von Apple zu öffnen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an. Diese Apple-ID kann später zum Erneuern Ihres DEP-Token verwendet werden.

5.  Wählen Sie im [Portal des Bereitstellungsprogramms](https://deploy.apple.com) von Apple die Option **Erste Schritte** für das **Programm zur Geräteregistrierung** aus.

4. Wählen Sie auf der Seite **Server verwalten** die Option **MDM-Server hinzufügen** aus.

5. Geben Sie *TestMDMServer* als **MDM-Servernamen** ein, und klicken Sie dann auf **Weiter**. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

6. Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet, und die Meldung **Laden Sie Ihren öffentlichen Schlüssel hoch** wird angezeigt. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.

6. Wechseln Sie zu **Bereitstellungsprogramme** > **Programm zur Geräteregistrierung** > **Geräte verwalten**.
7. Wählen Sie **Seriennummer** unter **Choose Devices By** (Geräte auswählen nach) aus. <!--ask Tiffany about this-->

8. Wählen Sie als Nächstes für **Aktion auswählen** die Option **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus. Das Apple-Portal weist die angegebenen Geräte dem Intune-Server für die Verwaltung zu und zeigt dann **Zuweisung abgeschlossen** an.

   Wechseln Sie im Apple-Portal zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Zuweisungsverlauf anzeigen**, um eine Liste der Geräte und ihre MDM-Server-Zuordnung anzuzeigen.

9. Geben Sie die Apple-ID, die zum Erstellen dieses Tokens verwendet wurde, für die zukünftige Verwendung im Azure-Portal in Intune an.

    ![Screenshot der Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/device-enrollment-program-enroll-ios/image03.png)

10. Navigieren Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), und wählen Sie **Öffnen** und dann **Erstellen** aus. 

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils
Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für DEP-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.

2. Wählen Sie das soeben installierte Token aus, und klicken Sie auf **Profile** > **Profil erstellen**.

3. Geben Sie unter **Profil erstellen** den **Namen** *TestDEPProfile* und die **Beschreibung** *Testing DEP for iOS devices* (Test von DEP für iOS-Geräte) ein. Benutzer können diese Informationen nicht sehen.

4. Wählen Sie für **Benutzeraffinität** die Option **Mit Benutzeraffinität registrieren** aus. Diese Option ist für Geräte, die Benutzern gehören, die das Unternehmensportal für Dienste wie das Installieren von Apps verwenden möchten.

5. Wählen Sie **Nein** unter **Über das Unternehmensportal statt über den Setup-Assistenten von Apple authentifizieren** aus.

6. Klicken Sie auf **Geräteverwaltungseinstellungen**, und wählen Sie **Nein** unter **Überwacht** aus. Überwachte Geräte bieten Ihnen mehr Verwaltungsoptionen, allerdings verwenden Sie sie nicht im Rahmen diesen Tutorials.

7. Wählen Sie **OK** aus.

8. Klicken Sie auf **Anpassung den Setup-Assistenten**, und geben Sie *Tutorial department* (Tutorialabteilung) unter **Abteilungsname** ein. Diese Zeichenfolge wird Benutzern angezeigt, wenn sie während der Geräteaktivierung auf **About configuration** (Informationen zur Konfiguration) tippen.

9. Geben Sie unter **Abteilungstelefonnummer** eine Telefonnummer ein. Diese Nummer wird angezeigt, wenn Benutzer während der Aktivierung auf **Need help** (Hilfe) tippen.

10. Während der Geräteaktivierung können Sie eine Vielzahl von Anzeigen **anzeigen** oder **ausblenden**. Legen Sie für dieses Tutorial **Anzeigen** für **Passcode** und für alles andere **Ausblenden** fest.

11. Klicken Sie auf **OK** > **Erstellen**.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte

Ihnen wird nun angezeigt, welche Geräte diesem Token zugeordnet sind.

1. Klicken Sie in Intune im Azure-Portal auf **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie in der Liste ein Token aus, und klicken Sie dann auf **Geräte** > **Synchronisieren**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Zuweisen eines Registrierungsprofils an iOS-Geräte

Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können.

1. Klicken Sie im Azure-Portal in Intune auf **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, und wählen Sie in der Liste Ihr Token aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und klicken Sie dann auf **Zuweisen**.

## <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune eingerichtet und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie die Autopilot-Geräte nicht mehr verwenden möchten, können Sie sie löschen.

- Wenn Geräte bei Intune registriert sind, müssen Sie sie zunächst [aus Azure Active Directory-Portal löschen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich auch über die anderen Optionen, die für das Registrieren von iOS-Geräten verfügbar sind.

> [!div class="nextstepaction"]
> [Ausführlicher Artikel zur iOS-DEP-Registrierung](device-enrollment-program-enroll-ios.md)