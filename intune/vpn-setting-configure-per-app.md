---
title: Die Einrichtung des Pro-App-VPN in Microsoft Intune für iOS-Geräte
titleSuffix: ''
description: Sie können angeben, welche verwalteten Apps Ihr virtuelles privates Netzwerk (VPN) auf mit Intune verwalteten iOS-Geräten verwenden können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 67e2630fc2a7ccd75ac86c797e36c389757d908a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="set-up-per-app-virtual-private-network-vpn-in-intune-for-ios-devices"></a>Die Einrichtung des Pro-App-VPN in Intune für iOS-Geräte

Sie können angeben, welche verwalteten Apps Ihr virtuelles privates Netzwerk (VPN) auf mit Intune verwalteten iOS-Geräten verwenden können. Wenn Sie ein Pro-App-VPN in Intune erstellen, verbindet sich ein Benutzer automatisch über Ihr VPN, wenn dieser auf Unternehmensdokumente zugreift.

Pro-App-VPN ist derzeit für die folgenden Anbieter verfügbar: 

 - Pulse Connect Secure
 - Checkpoint Remote Access VPN
 - F5
 - SonicWall


## <a name="prerequisites-for-the-per-app-vpn"></a>Voraussetzungen für das Pro-App-VPN

Um ihre Identität nachzuweisen, zeigt der VPN-Server das Zertifikat an, das vom Gerät ohne Aufforderung akzeptiert werden muss. Um die automatische Genehmigung des Zertifikats sicherzustellen, erstellen Sie ein vertrauenswürdiges Zertifikatprofil, das das durch die Zertifizierungsstelle (CA) ausgegebene Stammzertifikat des VPN-Servers enthält. 

Exportieren Sie das Zertifikat, und fügen Sie die CA hinzu.

1. Öffnen Sie die Verwaltungskonsole auf Ihrem VPN-Server.
2. Überprüfen Sie, dass Ihr VPN-Server die zertifikatbasierte Authentifizierung verwendet. 
3. Exportieren Sie das vertrauenswürdige Zertifikat der Stammzertifizierungsstelle. Es verfügt über eine CER-Erweiterung, und Sie fügen es hinzu, wenn Sie ein vertrauenswürdiges Zertifikatprofil erstellen.
4. Fügen Sie den Namen der Zertifizierungsstelle hinzu, die das Zertifikat für die Authentifizierung an den VPN-Server ausgestellt hat.
    Wenn die vom Gerät vorgelegte Zertifizierungsstelle mit einer der CAs in der Liste der vertrauenswürdigen Zertifizierungsstellen auf dem VPN-Server übereinstimmt, dann authentifiziert der VPN-Server das Gerät erfolgreich.

## <a name="create-a-group-for-your-vpn-users"></a>Erstellen einer Gruppe für Ihre VPN-Benutzer

Erstellen oder wählen Sie eine vorhandene Gruppe in Azure Active Directory (Azure AD), die die Mitglieder enthalten soll, die Zugriff auf das Pro-App-VPN besitzen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Gruppen** aus, und klicken Sie dann auf **Neue Gruppe**.
3. Wählen Sie einen **Gruppentyp** für die Gruppe aus. 
3. Geben Sie den **Gruppennamen** der Gruppe ein. 
4. Geben Sie die **Gruppenbeschreibung** der Gruppe ein. 
5. Legen Sie den **Mitgliedschaftstyp** auf **Zugewiesen** fest.
7. Suchen Sie im Bereich **Mitglieder** anhand des Namens oder der E-Mail-Adresse nach den VPN-Benutzern.
8. Wählen Sie jeden Benutzer aus, und klicken Sie auf **Auswählen**.
9. Klicken Sie auf **Erstellen**.

## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

Importieren Sie das Stammzertifikat des VPN-Servers, das von der Zertifizierungsstelle ausgegeben wurde, in ein in Intune erstelltes Profil. Das Profil des vertrauenswürdigen Zertifikats weist das iOS-Gerät an, automatisch der CA zu vertrauen, die der VPN-Server präsentiert.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Gerätekonfiguration** aus, und klicken Sie dann auf **Profile**.
3. Klicken Sie auf **Profil erstellen**. Führen Sie unter **Profil erstellen** Folgendes durch:
    1. Geben Sie den **Namen** ein.
    2. Geben Sie die **Beschreibung** ein.
    3. Wählen Sie **iOS** für die **Plattform** aus.
    4. Wählen Sie **vertrauenswürdiges Zertifikat** für den **Profiltyp**.
4. Klicken Sie auf das Ordnersymbol, und navigieren Sie zu Ihrem VPN-Zertifikat (CER-Datei), das Sie von Ihrer VPN-Verwaltungskonsole exportiert haben. Klicken Sie auf **OK**.
5. Klicken Sie auf **Erstellen**.

    ![Erstellen eines vertrauenswürdigen Zertifikatprofils](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>Erstellen eines SCEP-Zertifikatprofils

Das Profil des vertrauenswürdigen Stammzertifikats ermöglicht, dass iOS den VPN-Server automatisch als vertrauenswürdig einstuft. Das SCEP-Zertifikat stellt Anmeldeinformationen aus dem iOS-VPN-Client an den VPN-Server bereit. Das Zertifikat lässt zu, dass das Gerät im Hintergrund eine Authentifizierung durchführt, ohne dass das iOS-Gerät den Benutzer zur Eingabe eines Benutzernamens und Kennworts auffordert. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Gerätekonfiguration** aus, und klicken Sie dann auf **Profile**.
3. Klicken Sie auf **Profil erstellen**. Führen Sie unter **Profil erstellen** Folgendes durch:
    1. Geben Sie den **Namen** ein.
    2. Geben Sie die **Beschreibung** ein.
    3. Wählen Sie **iOS** für die **Plattform** aus.
    4. Wählen Sie **SCEP-Zertifikat** für den **Profiltyp**.
4. Wählen Sie **Jahre** aus, und geben Sie `2` für **Gültigkeitsdauer des Zertifikats** an.
5. Wählen Sie **Allgemeiner Name** für **Format des Antragstellernamens** aus.
6. Wählen Sie **Benutzerprinzipalname (UPN)** für **Alternativer Antragstellername** aus.
7. Wählen Sie **Digitale Signatur** und **Schlüsselverschlüsselung** für **Schlüsselverwendung** aus.
8. Wählen Sie **2048** für **Schlüsselgröße (Bits)**.
9. Klicken Sie auf „Stammzertifikat“, und wählen Sie ein SCEP-Zertifikat. Klicken Sie auf **OK**.
10. Geben Sie unter **Name** für **Erweiterte Schlüsselverwendung** `Client Authentication` ein.
11. Geben Sie unter **Objektkennung** `1.3.6.1.5.5.7.3.2` ein.
12. Klicken Sie auf **Hinzufügen**.
13. Geben Sie die ***Server-URL*** ein, und klicken Sie auf **Hinzufügen**.
14. Klicken Sie auf **OK**.
15. Klicken Sie auf **Erstellen**.

    ![Erstellen eines SCEP-Zertifikatprofils](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Erstellen eines Pro-App-VPN-Profils

Das VPN-Profil enthält das SCEP-Zertifikat, das die Anmeldeinformationen des Clients, die Verbindungsinformationen für das VPN und das Pro-App-VPN-Flag enthält. So können Sie die Pro-App-VPN-Funktion für den Gebrauch durch die iOS-Anwendung aktivieren.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Gerätekonfiguration** aus, und klicken Sie dann auf **Profile**.
3. Klicken Sie auf **Profil erstellen**. Führen Sie unter **Profil erstellen** Folgendes durch:
    1. Geben Sie den **Namen** ein.
    2. Geben Sie die **Beschreibung** ein.
    3. Wählen Sie **iOS** für die **Plattform** aus.
    4. Wählen Sie **VPN** für den **Profiltyp** aus.
4. Wählen Sie **Basis-VPN** aus. Gehen Sie unter **Basis-VPN** wie folgt vor:
    1. Geben Sie den **Verbindungsnamen** ein.
    2. Geben Sie die **IP-Adresse oder FQDN** ein.
    3. Wählen Sie **Zertifikate** für die **Authentifizierungsmethode** aus.
    4. Wählen Sie das SCEP-Zertifikat unter **Authentifizierungszertifikat**, und klicken Sie auf **OK**.
    5. Wählen Sie Ihr VPN für den **Verbindungstyp** aus.
    6. Konfigurieren Sie bei Bedarf die Attribute für das VPN.
    7. Wählen Sie **Getrenntes Tunneln deaktivieren** aus.
5. Klicken Sie auf **Automatisches VPN**. Führen Sie unter **Automatisches VPN** Folgendes durch:
    1. Wählen Sie **Pro-App-VPN** für den **Typ des automatischen VPN** aus.
    2. Geben Sie die URL für das VPN ein, und klicken Sie auf **Hinzufügen**.
    3. Klicken Sie auf **OK**.
6. Klicken Sie auf **OK**.
7. Klicken Sie auf **Erstellen**.

    ![Erstellen eines Pro-App-VPN-Profils](./media/vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>Ordnen Sie dem VPN-Profil eine App zu.

Nachdem Sie Ihr VPN-Profil hinzugefügt haben, ordnen Sie die App und Azure AD-Gruppe dem Profil zu.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
2. Wählen Sie **Mobile Apps** aus.
3. Klicken Sie auf **Apps**.
4. Wählen Sie die App aus der Liste der Apps aus.
5. Klicken Sie auf **Zuweisungen**.
6. Klicken Sie auf **Gruppe hinzufügen**.
7. Wählen Sie im Bereich **Gruppe hinzufügen** für den **Zuweisungstyp** die Option **Erforderlich** aus.
6. Wählen Sie die Gruppe aus, die Sie zuvor definiert haben, und aktivieren Sie die Option**Diese App als erforderlich festlegen**.
8. Wählen Sie Ihre VPN-Definition für das **VPN** aus.
 
    > [!NOTE]  
    > In einigen Fällen benötigt die VPN-Definition bis zu einer Minute, um den Wert abzurufen. Warten Sie etwa 3–5 Minuten, bevor Sie auf **Speichern** klicken.

9. Klicken Sie auf **OK** und dann auf **Speichern**.

    ![Zuordnen einer App zu einem VPN](./media/vpn-per-app-app-to-vpn.png)

## <a name="verify-the-connection-on-the-ios-device"></a>Überprüfen der Verbindung auf dem iOS-Gerät

Sobald Ihr App-bezogenes VPN eingerichtet und Ihrer App zugeordnet ist, überprüfen Sie, ob die Verbindung von einem Gerät aus funktioniert.

### <a name="before-you-attempt-to-connect"></a>Bevor Sie eine Verbindung herstellen

 - stellen Sie sicher, dass iOS 7 oder höher ausgeführt wird
 - stellen Sie sicher, dass Sie *alle* der oben erwähnten Richtlinien derselben Gruppe von Benutzern bereitstellen Wenn Sie nicht so vorgehen, wird wahrscheinlich die Servicequalität des App-bezogenen VPN beeinträchtigt.  
 - stellen Sie sicher, dass Sie die unterstützende Drittanbieter-VPN-App installiert haben Die folgenden VPN-Apps werden unterstützt:
    - Pulse Secure
    - Checkpoint
    - F5
    - SonicWall

### <a name="connect-using-the-per-app-vpn"></a>Herstellen einer Verbindung mithilfe des App-bezogenen VPNs

Überprüfen Sie die Zero Touch-Funktion, indem Sie eine Verbindung herstellen, ohne dabei das VPN auswählen oder Ihre Anmeldeinformationen eingeben zu müssen. Die Zero Touch-Funktion bedeutet Folgendes:

 - Das Gerät fordert Sie nicht auf, dem VPN-Server zu vertrauen. Sie sehen aber dennoch das Dialogfeld **Dynamic Trust** (Dynamische Vertrauensstellung).
 - Sie müssen keine Anmeldeinformationen eingeben.
 - Sie werden mit dem VPN nach Tippen auf die korrekte Schaltfläche verbunden.

Überprüfen Sie die Verbindung auf dem iOS-Gerät.

1. Tippen Sie auf die VPN-App.
2. Tippen Sie auf **Verbinden**.  
Das VPN stellt ohne weitere Aufforderungen erfolgreich eine Verbindung her.

<!-- ## Troubleshooting the Per-App VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Nächste Schritte

- Um die iOS-Einstellungen zu überprüfen, gehen Sie unter [VPN-Einstellungen für iOS-Geräte in Microsoft Intune](vpn-settings-ios.md).
-  Weitere Informationen zur VPN-Einstellung und Intune finden Sie unter [Konfigurieren von VPN-Einstellungen in Microsoft Intune](vpn-settings-configure.md).
