---
title: Registrieren von iOS-Geräten – Programm zur Geräteregistrierung
titleSuffix: Microsoft Intune
description: Hier erfahren Sie, wie Sie unternehmenseigene iOS-Geräte mit dem Programm zur Geräteregistrierung (Device Enrollment Program, DEP) registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 1af474063ec7b6ccac2a36afbec421767f79444a
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642845"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können Intune so einrichten, dass über das [Programm zur Geräteregistrierung](https://deploy.apple.com) von Apple erworbene iOS-Geräte registriert werden. Sie können die Registrierung des Programms zur Geräteregistrierung für eine große Anzahl von Geräten aktivieren, ohne diese auch nur zu berühren. Sie können Geräte wie iPhones und iPad direkt an Benutzer versenden. Wenn der Benutzer das Gerät anschaltet, wird der Setup-Assistent mit vordefinierten Einstellungen ausgeführt, und das Gerät wird für die Verwaltung registriert.

Zur Aktivierung der DEP-Registrierung können Sie sowohl das Intune-Portal als auch das Apple DEP-Portal verwenden. Sie benötigen auch eine Liste von Seriennummern oder eine Bestellnummer, um Geräte in Intune zur Verwaltung zuweisen zu können. Sie erstellen DEP-Registrierungsprofile, die Einstellungen enthalten, die für Geräte während der Registrierung gelten.

Die Registrierung mit DEP funktioniert übrigens nicht mit dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>Überwachter Modus
Apple hat für iOS 5 den überwachten Modus eingeführt. Ein iOS-Gerät im überwachten Modus kann über zusätzliche Steuerelemente verwaltet werden. Dies ist bei unternehmenseigenen Geräten besonders nützlich. Intune unterstützt die Konfiguration von Geräten für den überwachten Modus als Teil des Apple-Programms zur Geräteregistrierung (DEP). 

Die Unterstützung für nicht überwachte DEP-Geräte ist seit iOS 11 veraltet. In iOS 11 und höher müssen für DEP konfigurierte Geräte immer überwacht sein. Das DEP-Flag „is_supervised“ wird in zukünftigen iOS-Versionen ignoriert.

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Voraussetzungen
- Geräte, die unter dem [Programm zur Geräteregistrierung von Apple](http://deploy.apple.com) erworben werden.
- [MDM-Autorität](mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Abrufen eines Apple-DEP-Tokens

Bevor Sie iOS-Geräte mit DEP registrieren können, benötigen Sie ein DEP-Token-Datei (.p7m) von Apple. Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile zu Apple hochladen und diesen Profilen Geräte zuweisen.

Verwenden Sie das Apple DEP-Portal, um ein DEP-Token zu erstellen. Sie verwenden das DEP-Portal auch, um in Intune Geräte für die Verwaltung zuzuweisen.

> [!NOTE]
> Wenn Sie das Token vor der Migration zu Azure aus dem klassischen Intune-Portal löschen, stellt Intune womöglich ein gelöschtes Apple DEP-Token wieder her. Sie können das DEP-Token erneut aus dem Azure-Portal löschen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Schritt 1: Laden Sie das Intune-Zertifikat mit öffentlichem Schlüssel herunter, das zum Erstellen des Tokens erforderlich ist.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Hinzufügen** aus.

    ![Rufen Sie ein Registrierungsprogrammtoken ab.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Erteilen Sie Microsoft die Berechtigung, Benutzer- und Geräteinformationen an Apple zu senden, indem Sie auf **Ich stimme zu** klicken.

   ![Screenshot des Bereichs „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Schritt 2. Verwenden Sie Ihren Schlüssel, um ein Token von Apple herunterzuladen.

1. Wählen Sie **Create a token for Apple's Device Enrollment Program** (Token für das Programm zur Geräteregistrierung von Apple erstellen) aus, um das Portal des Bereitstellungsprogramms von Apple zu öffnen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an. Diese Apple-ID kann später zum Erneuern Ihres DEP-Token verwendet werden.
2.  Wählen Sie im [Portal des Bereitstellungsprogramms](https://deploy.apple.com) von Apple die Option **Erste Schritte** für das **Programm zur Geräteregistrierung** aus.

3. Wählen Sie auf der Seite **Server verwalten** die Option **MDM-Server hinzufügen** aus.
4. Geben Sie den **MDM-Servernamen** ein, und wählen Sie anschließend **Weiter** aus. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

5. Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet, und die Meldung **Laden Sie Ihren öffentlichen Schlüssel hoch** wird angezeigt. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.

6. Wechseln Sie zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Geräte verwalten**.
7. Geben Sie unter **Geräte auswählen nach** an, wie die Geräte identifiziert werden sollen:
    - **Seriennummer**
    - **Reihenfolge**
    - **Upload der CSV-Datei**

   ![Screenshot bei Festlegen von „Geräte auswählen nach“ auf „Seriennummer“, der Einstellung „Aktion auswählen“ auf „Zu Server zuweisen“ und der Auswahl des Servernamens.](./media/enrollment-program-token-specify-serial.png)

8. Wählen Sie als Nächstes für **Aktion auswählen** die Option **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus. Das Apple-Portal weist die angegebenen Geräte dem Intune-Server für die Verwaltung zu und zeigt dann **Zuweisung abgeschlossen** an.

   Wechseln Sie im Apple-Portal zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Zuweisungsverlauf anzeigen**, um eine Liste der Geräte und ihre MDM-Server-Zuordnung anzuzeigen.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Schritt 3: Speichern Sie die zum Erstellen dieses Tokens verwendete Apple-ID.

Geben Sie in Intune im Azure-Portal für die zukünftige Verwendung Ihre Apple-ID an.

![Screenshot der Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Schritt 4: Laden Sie Ihr Token hoch.
Navigieren Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), und wählen Sie **Öffnen** und dann **Erstellen** aus. Mit dem Push-Zertifikat kann Intune iOS-Geräte registrieren und verwalten, indem die Richtlinie auf registrierte mobile Geräte übertragen wird. Intune führt eine automatische Synchronisierung mit Apple durch, um Ihr Registrierungsprogrammkonto anzuzeigen.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils

Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für DEP-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

> [!NOTE]
> Geräte werden blockiert, wenn nicht genügend Unternehmensportallizenzen für ein VPP-Token vorhanden sind oder das Token abgelaufen ist. Intune zeigt eine Warnung an, wenn ein Token in Kürze abläuft oder bald keine Lizenzen mehr zur Verfügung stehen.
 

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.
2. Wählen Sie ein Token aus, und wählen Sie dann **Profile** und **Profil erstellen** aus.

    ![Screenshot „Profil erstellen“](./media/device-enrollment-program-enroll-ios/image04.png)

3. Geben Sie zu administrativen Zwecken unter **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Profilname und Beschreibung](./media/device-enrollment-program-enroll-ios/image05.png)

4. Wählen Sie unter **Benutzeraffinität** aus, ob sich Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registrieren müssen.
    - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und für Dienste wie z.B. die Installation von Apps das Unternehmensportal verwenden sollen. Wenn Sie ADFS verwenden und im Registrierungsprofil die Einstellung **Über das Unternehmensportal statt über den Setup-Assistenten authentifizieren** auf **Nein** festgelegt ist, ist [Endpunkt WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) ([Weitere Informationen](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)) erforderlich.

    - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die keinem einzelnen Benutzer zugeordnet sind. Verwenden Sie diese Option für Geräte, die Aufgaben ohne Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

5. Wenn Sie **Mit Benutzeraffinität registrieren** ausgewählt haben, können Sie die Benutzerauthentifizierung über das Unternehmensportal statt über den Apple-Setup-Assistenten erlauben.

    ![Authentifizieren über das Unternehmensportal](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Wenn Sie einen der folgenden Schritte ausführen möchten, legen Sie **Über das Unternehmensportal statt über den Setup-Assistenten authentifizieren** auf **Ja** fest.
    >    - Sie möchten die mehrstufige Authentifizierung verwenden.
    >    - Sie möchten Benutzer zum Ändern ihres Kennworts auffordern, wenn sie sich zum ersten Mal anmelden.
    >    - Sie möchten Benutzer dazu auffordern, ihre abgelaufenen Kennwörter bei der Registrierung zurückzusetzen.
    >
    > Diese Optionen werden für die Authentifizierung beim Setup-Assistenten von Apple nicht unterstützt.

6. Wenn Sie für die Option **Authenticate with Company Portal instead of Apple Setup Assistant** (Beim Unternehmensportal anstelle des Setup-Assistenten für Apple authentifizieren) **Ja** ausgewählt haben, haben Sie die Möglichkeit, ein VPP-Token (Volume Purchase Program) zu verwenden, um automatisch das Unternehmensportal auf dem Gerät zu installieren, ohne dass der Benutzer eine Apple-ID angeben muss. Wählen Sie unter **Install Company Portal with VPP** (Unternehmensportal mit VPP installieren) ein Token aus, um das Unternehmensportal mit einem VPP-Token zu installieren. Stellen Sie sicher, dass das Token nicht abläuft, und dass Sie über genügend Gerätelizenzen für die Unternehmensportal-App verfügen. Wenn das Token abläuft oder über keine Lizenzen mehr verfügt, installiert Intune stattdessen das App Store-Unternehmensportal und fordert zur Eingabe einer Apple-ID auf.

    ![Screenshot der Installation des Unternehmensportals mit VPP](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Wenn Sie ein Token für **Unternehmensportal mit VPP installieren** auswählen, haben Sie unmittelbar nach Abschluss des Einrichtungsassistenten die Möglichkeit, das Gerät in den Einzelanwendungsmodus (für die Unternehmensportal-App) zu sperren. Wählen Sie für **Run Company Portal in Single App Mode until authentication** (Unternehmensportal bis zur Authentifizierung im Einzelanwendungsmodus ausführen) **Ja** aus, um diese Option festzulegen. Der Benutzer muss sich erst authentifizieren, indem er sich über das Unternehmensportal anmeldet, um das Gerät zu verwenden.
    Dieses Feature wird nur für iOS 11.3.1 und höher unterstützt.

8. Wählen Sie **Geräteverwaltungseinstellungen** aus, und geben Sie an, ob Geräte mit diesem Profil überwacht werden sollen.

    ![Screenshot der Geräteverwaltungseinstellungen](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    Bei **überwachten** Geräten stehen mehr Verwaltungsfunktionen zur Verfügung, und die Aktivierungssperre ist standardmäßig deaktiviert. Es wird von Microsoft empfohlen, DEP als Mechanismus zur Aktivierung des überwachten Modus zu verwenden. Dies gilt insbesondere für Organisationen, die eine große Anzahl von iOS-Geräten bereitstellen.

    Die Benutzer werden auf zweierlei Weise benachrichtigt, dass ihre Geräte überwacht werden:

   - Auf dem Sperrbildschirm wird Folgendes angezeigt: „This iPhone is managed by Contoso“ (Dieses iPhone wird von Contoso verwaltet).
   - Auf dem Bildschirm **Settings** > **General** > **About** (Einstellungen > Allgemein > Info) wird Folgendes angezeigt: „This iPhone is supervised. „This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device“ (Dieses iPhone wird überwacht. Contoso kann Ihren Internetdatenverkehr überwachen und dieses Gerät suchen.)

     > [!NOTE]
     > Ein Gerät, das ohne Überwachung registriert wurde, kann nur mithilfe von Apple Configurator auf den Status „Überwacht“ zurückgesetzt werden. Wenn Sie das Gerät auf diese Weise zurücksetzen möchten, müssen Sie ein iOS-Gerät über ein USB-Kabel mit einem Mac verbinden. Erfahren Sie mehr über dieses Thema in der [Dokumentation zu Apple Configurator](http://help.apple.com/configurator/mac/2.3).

9. Wählen Sie aus, ob für Geräte mit diesem Profil die gesperrte Registrierung verwendet werden soll. Wenn **Gesperrte Registrierung** aktiviert ist, sind die iOS-Einstellungen deaktiviert, mit denen das Verwaltungsprofil aus dem Menü **Einstellungen** entfernt werden kann. Nach der Geräteregistrierung können Sie diese Einstellung ändern, ohne das Gerät zurückzusetzen. Bei solchen Geräten muss der Verwaltungsmodus **Überwacht** auf *Ja* eingestellt sein. 

10. Wählen Sie aus, ob für Geräte mit diesem Profil die Option **Mit Computern synchronisieren** verwendet werden soll. Wenn Sie **Apple Configurator nach Zertifikat zulassen** auswählen, müssen Sie unter **Apple Configurator-Zertifikate** ein Zertifikat auswählen.

11. Wenn Sie im vorherigen Schritt **Apple Configurator nach Zertifikat zulassen** ausgewählt haben, müssen Sie ein Apple Configurator-Zertifikat zum Importieren auswählen.

12. Wählen Sie **OK** aus.

13. Wählen Sie **Anpassung des Setup-Assistenten** aus, um die folgenden Profileinstellungen zu konfigurieren: ![Anpassung des Setup-Assistenten](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Abteilungseinstellungen | Beschreibung |
    |---|---|
    | <strong>Abteilungsname</strong> | Wird angezeigt, wenn der Benutzer während der Aktivierung auf <strong>Info zur Konfiguration</strong> tippt. |
    |    <strong>Abteilungstelefonnummer</strong>     | Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche <strong>Benötigen Sie Hilfe?</strong> klickt. |

  Sie können entscheiden, ob ein Bildschirm des Setup-Assistenten auf dem Gerät angezeigt oder ausgeblendet wird, während der Benutzer es einrichtet.
  - Wenn Sie auf **Ausblenden** klicken, wird der Bildschirm während des Setups nicht angezeigt. Nach dem Setup des Geräts kann der Benutzer weiterhin zum Menü **Einstellungen** navigieren, um das Feature einzurichten.
  - Wenn Sie auf **Anzeigen** klicken, wird der Bildschirm während des Setups angezeigt. Gelegentlich kann der Benutzer den Bildschirm überspringen, ohne weitere Maßnahmen ergreifen zu müssen. Er kann aber später zum Gerätemenü **Einstellungen** navigieren, um das Feature einzurichten. 


    | Bildschirmeinstellungen des Setup-Assistenten | Wenn Sie während des Setups des Geräts auf **Anzeigen** klicken, führt das Gerät die folgenden Aktionen durch: |
    |------------------------------------------|------------------------------------------|
    | <strong>Kennung</strong> | Es fordert den Benutzer auf, eine Kennung einzugeben. Fordern Sie immer eine Kennung an, es sei denn, das Gerät und der Zugriff darauf werden auf andere Weise geschützt (d.h. im Kioskmodus zum Einschränken des Geräts auf eine App). |
    | <strong>Standortdienste</strong> | Es fordert den Benutzer auf, seinen Standort anzugeben. |
    | <strong>Wiederherstellen</strong> | Es zeigt den Bildschirm **Apps & Data** (Apps und Daten) an. Über diesen Bildschirm hat der Benutzer die Möglichkeit, Daten aus der iCloud-Sicherung wiederherzustellen oder aus dieser zu übertragen, wenn er das Gerät einrichtet. |
    | <strong>iCloud und Apple-ID</strong> | Es lässt zu, dass der Benutzer sich mit seiner **Apple-ID** anmelden und **iCloud** verwenden kann.                         |
    | <strong>Geschäftsbedingungen</strong> | Es verlangt, dass der Benutzer die Nutzungsbedingungen von Apple akzeptiert. |
    | <strong>Touch ID</strong> | Es lässt zu, dass der Benutzer die Identifikation per Fingerabdruck für das Gerät einrichtet. |
    | <strong>Apple Pay</strong> | Es lässt zu, dass der Benutzer Apple Pay auf dem Gerät einrichtet. |
    | <strong>Zoom</strong> | Es lässt zu, dass der Benutzer die Anzeige vergrößern bzw. verkleinern kann, während er das Gerät einrichtet. |
    | <strong>Siri</strong> | Es lässt zu, dass der Benutzer Siri einrichtet. |
    | <strong>Diagnosedaten</strong> | Zeigt dem Benutzer den Bildschirm **Diagnose** an. Über diesen Bildschirm kann der Benutzer Diagnosedaten an Apple senden. |


14. Wählen Sie **OK** aus.

15. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte
Nachdem Intune nun die Berechtigung zum Verwalten Ihrer Geräte besitzt, können Sie Intune mit Apple synchronisieren, um Ihre verwalteten Geräte in Intune im Azure-Portal anzuzeigen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, wählen Sie in der Liste ein Token aus, und wählen Sie dann **Geräte** > **Synchronisieren** aus. ![Screenshot des ausgewählten Knotens „Geräte des Registrierungprogramms“ und des ausgewählten Links „Synchronisierung“](./media/device-enrollment-program-enroll-ios/image06.png)

   Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr des Registrierungsprogramms erzwingt Intune die folgenden Einschränkungen:
   - Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung ruft Intune die vollständig aktualisierte Liste der Seriennummern auf, die dem mit Intune verbundenen Apple MDM-Server zugewiesen sind. Wenn ein Registrierungsprogrammgerät aus dem Intune-Portal gelöscht wird, ohne dass es vom Apple MDM-Server aus dem DEP-Portal entfernt wurde, wird es erst wieder in Intune importiert, nachdem die vollständige Synchronisierung ausgeführt wurde.   
   - Die Synchronisierung wird automatisch alle 24 Stunden ausgeführt. Sie können eine Synchronisierung ebenfalls durchführen, indem Sie auf die Schaltfläche **Synchronisierung** klicken (nicht öfter als einmal alle 15 Minuten). Alle Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen werden. Die Schaltfläche **Synchronisierung** bleibt bis zum Abschluss der Synchronisierung deaktiviert. Durch diese Synchronisierung werden vorhandene Gerätestatus aktualisiert und neue Geräte importiert, die dem Apple MDM-Server zugewiesen sind.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Zuweisen eines Registrierungsprofils an Geräte
Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können.

>[!NOTE]
>Sie können auch auf dem Blatt **Apple-Seriennummern** Profilen Seriennummern zuweisen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und klicken Sie dann auf **Zuweisen**.

### <a name="assign-a-default-profile"></a>Zuweisen eines Standardprofils

Sie können ein Standardprofil auswählen, das auf alle Geräte angewendet wird, die sich mit einem bestimmten Token registrieren.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Standardprofil festlegen** aus, wählen Sie ein Profil in der Dropdownliste aus, und wählen Sie dann **Speichern** aus. Dieses Profil wird auf alle Geräte angewendet, die sich mit dem Token registrieren.

## <a name="distribute-devices"></a>Verteilen von Geräten
Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune aktiviert und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden. Geräte ohne Benutzeraffinität benötigen eine Gerätelizenz. Ein aktiviertes Gerät kann kein Registrierungsprofil anwenden, bis das Gerät zurückgesetzt wurde.

Informationen finden Sie unter [Registrieren Ihres iOS-Geräts in Intune mit dem Programm zur Geräteregistrierung](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Erneuern eines DEP-Tokens  
1. Wechseln Sie zu deploy.apple.com.  
2. Wählen Sie unter **Server verwalten** Ihren MDM-Server aus, der der Tokendatei zugeordnet ist, die Sie erneuern möchten.
3. Klicken Sie auf **Neues Token generieren**.

    ![Screenshot von „Neues Token generieren“](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Klicken Sie auf **Ihr Servertoken**.  
5. Klicken Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, und wählen Sie anschließend das Token aus.
    ![Screenshot der Registrierungsprogrammtoken.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Wählen Sie **Token erneuern** aus, und geben Sie die Apple-ID ein, die zum Erstellen des ursprünglichen Tokens verwendet wurde.  
    ![Screenshot von „Token erneuern“](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Laden Sie das neu heruntergeladene Token hoch.  
9. Klicken Sie auf **Token erneuern**. Es wird eine Bestätigung angezeigt, dass das Token erneuert wurde.   
    ![Screenshot der Bestätigung](./media/device-enrollment-program-enroll-ios/confirmation.png)
