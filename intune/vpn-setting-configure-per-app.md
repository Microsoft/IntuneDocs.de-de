---
title: Einrichten des Pro-App-VPN für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie die Voraussetzungen, erstellen eine Gruppe für VPN-Benutzer (virtuelles privates Netzwerk), fügen ein SCEP-Zertifikatprofil hinzu, konfigurieren ein Pro-App-VPN-Profil und weisen dem VPN-Profil in Microsoft Intune auf iOS-Geräten mehrere Apps zu. Außerdem werden die Schritte zur Überprüfung der VPN-Verbindung auf dem Gerät beschrieben.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36ba25941950e403d1ab1861efac8db7dd3daede
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841707"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Einrichten eines Pro-App-VPN für iOS-Geräte in Intune

Sie können in Microsoft Intune VPNs erstellen und verwenden, die nur bestimmten Apps zugewiesen sind. Dieses Feature heißt „Pro-App-VPN“. Sie wählen die verwalteten Apps aus, die das VPN auf Geräten verwenden können, die von Intune verwaltet werden. Wenn Sie ein Pro-App-VPN verwenden, stellen Benutzer automatisch eine Verbindung über das VPN her und erhalten Zugriff auf Unternehmensressourcen wie etwa Dokumente.

Diese Funktion gilt für:

- iOS 9 und höher

Informieren Sie sich in der Dokumentation Ihres VPN-Anbieters, um zu erfahren, ob Ihr VPN Pro-App-VPNs unterstützt.

In diesem Artikel erfahren Sie, wie Sie ein Pro-App-VPN-Profil erstellen und dieses Profil Ihren Apps zuweisen. Anhand der folgenden Schritte können Sie Ihren Endbenutzern nahtlos Pro-App-VPNs zur Verfügung stellen. Bei den meisten VPNs, die ein Pro-App-VPN unterstützen, öffnen Benutzer eine App, und die Verbindung zum VPN wird automatisch hergestellt.

Bei einigen VPNs ist auch eine Authentifizierung mit Anmeldeinformationen für ein Pro-App-VPN möglich. Das bedeutet, dass Benutzer einen Benutzernamen und ein Kennwort eingeben müssen, um eine Verbindung mit dem VPN herzustellen.

## <a name="per-app-vpn-with-zscaler"></a>Pro-App-VPN mit Zscaler

Zscaler Private Access (ZPA) kann für die Authentifizierung mit Azure Active Directory integriert werden. Bei ZPA benötigen Sie weder ein Profil mit einem [vertrauenswürdigen Zertifikat](#create-a-trusted-certificate-profile) noch ein Profil mit einem [SCEP- oder PKCS-Zertifikat](#create-a-scep-or-pkcs-certificate-profile) (dies wird in diesem Artikel beschrieben). Wenn Sie ein Pro-App-VPN-Profil für Zscaler eingerichtet haben, wird beim Öffnen einer verknüpften App nicht automatisch eine Verbindung mit ZPA hergestellt. Stattdessen muss sich der Benutzer zunächst bei der Zscaler-App anmelden. Dann ist der Remotezugriff auf die verknüpften Apps beschränkt.

## <a name="prerequisites-for-per-app-vpn"></a>Voraussetzungen für das Pro-App-VPN

> [!IMPORTANT]
> Ihr VPN-Anbieter hat möglicherweise andere Anforderungen wie spezielle Hardware oder bestimmte Lizenzen für die Nutzung des Pro-App-VPN. Vor der Einrichtung des Pro-App-VPN ist es daher erforderlich, dass Sie sich mit der Anbieterdokumentation vertraut machen und die beschriebenen Anforderungen erfüllen.

Um ihre Identität nachzuweisen, zeigt der VPN-Server das Zertifikat an, das vom Gerät ohne Aufforderung akzeptiert werden muss. Erstellen Sie ein Profil mit einem vertrauenswürdigen Zertifikat, das das durch die Zertifizierungsstelle (CA) ausgegebene Stammzertifikat des VPN-Servers enthält, um die automatische Genehmigung des Zertifikats sicherzustellen. 

#### <a name="export-the-certificate-and-add-the-ca"></a>Exportieren Sie das Zertifikat, und fügen Sie die CA hinzu.

1. Öffnen Sie die Verwaltungskonsole auf Ihrem VPN-Server.
2. Stellen Sie sicher, dass Ihr VPN-Server die zertifikatbasierte Authentifizierung verwendet. 
3. Exportieren Sie das vertrauenswürdige Zertifikat der Stammzertifizierungsstelle. Es verfügt über eine CER-Erweiterung, und Sie fügen es hinzu, wenn Sie ein vertrauenswürdiges Zertifikatprofil erstellen.
4. Fügen Sie den Namen der Zertifizierungsstelle hinzu, die das Zertifikat für die Authentifizierung an den VPN-Server ausgestellt hat.

    Wenn die vom Gerät vorgelegte Zertifizierungsstelle mit einer CA in der Liste der vertrauenswürdigen Zertifizierungsstellen auf dem VPN-Server übereinstimmt, authentifiziert der VPN-Server das Gerät.

## <a name="create-a-group-for-your-vpn-users"></a>Erstellen einer Gruppe für Ihre VPN-Benutzer

Erstellen oder wählen Sie eine vorhandene Gruppe in Azure Active Directory aus, die die Benutzer oder Geräte enthält, die Zugriffsberechtigungen für das Pro-App-VPN haben. Unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](groups-add.md) erfahren Sie, wie Sie eine neue Gruppe erstellen.

## <a name="create-a-trusted-certificate-profile"></a>Erstellen eines vertrauenswürdigen Zertifikatprofils

Importieren Sie das Stammzertifikat des VPN-Servers, das von der Zertifizierungsstelle ausgegeben wurde, in ein in Intune erstelltes Profil. Das Profil des vertrauenswürdigen Zertifikats weist das iOS-Gerät an, automatisch der CA zu vertrauen, die der VPN-Server präsentiert.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:
    - **Name**
    - **Beschreibung**
    - **Plattform**: Wählen Sie **iOS** aus.
    - **Profiltyp**: Wählen Sie **Vertrauenswürdiges Zertifikat**.
4. Klicken Sie auf das Ordnersymbol, und navigieren Sie zu Ihrem VPN-Zertifikat (CER-Datei), das Sie über Ihre VPN-Verwaltungskonsole exportiert haben. 
5. Klicken Sie auf **OK** > **Erstellen**.

    ![Erstellen eines Profils mit einem vertrauenswürdigen Zertifikat für iOS-Geräte in Microsoft Intune](./media/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Erstellen eines SCEP- oder PKCS-Zertifikatprofils

Durch das Profil des vertrauenswürdigen Stammzertifikats stuft das Gerät den VPN-Server automatisch als vertrauenswürdig ein. Das SCEP- oder PKCS-Zertifikat stellt Anmeldeinformationen aus dem iOS-VPN-Client an den VPN-Server bereit. Durch das Zertifikat kann das Gerät im Hintergrund eine Authentifizierung durchführen, ohne dass der Benutzer zur Eingabe eines Benutzernamens und Kennworts aufgefordert wird. 

In den folgenden Artikeln erfahren Sie mehr zum Konfigurieren und Zuweisen eines Clientauthentifizierungszertifikats:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP in Microsoft Intune](certificates-scep-configure.md)
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)

Achten Sie darauf, dass die Clientauthentifizierung für das Zertifikat konfiguriert wurde. Dies können Sie direkt in den SCEP-Zertifikatprofilen festlegen (**Erweiterte Schlüsselverwendung** > **Clientauthentifizierung**). Legen Sie für PKCS die Clientauthentifizierung in der Zertifikatvorlage in der Zertifizierungsstelle fest.

![Erstellen Sie ein SCEP-Zertifikatprofil in Microsoft Intune, das u.a. das Format des Antragstellernamens, die Schlüsselverwendung und die erweiterte Schlüsselverwendung enthält.](./media/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Erstellen eines Pro-App-VPN-Profils

Das VPN-Profil enthält das SCEP- oder PKCS-Zertifikat, das die Anmeldeinformationen des Clients, die Verbindungsinformationen für das VPN und das Pro-App-VPN-Flag enthält. So können Sie die Pro-App-VPN-Funktion für den Gebrauch durch die iOS-Anwendung aktivieren.

1. Wählen Sie in **Intune** **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus. 
2. Geben Sie die folgenden Eigenschaften ein: 
    - **Name**
    - **Beschreibung**
    - **Plattform**: Wählen Sie **iOS** aus.
    - **Profiltyp**: Wählen Sie **VPN** aus.
3. Wählen Sie unter **Verbindungstyp** Ihre VPN-Client-App aus.
4. Wählen Sie **Basis-VPN** aus. Im Artikel zu den [iOS-VPN-Einstellungen](vpn-settings-ios.md) werden alle Einstellungen aufgelistet und beschrieben. Achten Sie darauf, dass Sie die folgenden Einstellungen wie unten angegeben vornehmen, wenn Sie ein Pro-App-VPN verwenden: 
    
    - **Authentifizierungsmethode**: Wählen Sie **Zertifikate**. 
    - **Authentifizierungszertifikat**: Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikat, und klicken Sie anschließend auf **OK**.      
    - **Getrenntes Tunneln:** Klicken Sie auf **Disable** (Deaktivieren), um zu erzwingen, dass der gesamte Datenverkehr den VPN-Tunnel durchläuft, wenn die VPN-Verbindung aktiv ist. 

      ![Festlegen eines Verbindungstyps, einer IP-Adresse oder eines FQDN, einer Authentifizierungsmethode und Aktivieren/Deaktivieren des getrennten Tunnelns im Pro-App-VPN-Profil in Microsoft Intune](./media/vpn-per-app-create-vpn-profile.png)

    Informationen zu den anderen Einstellungen finden Sie im Artikel zu den [iOS-VPN-Einstellungen](vpn-settings-ios.md).

5. Wählen Sie **Automatisches VPN** > **Typ des automatischen VPN** > **Pro-App-VPN** aus.

    ![Festlegen des Typs des automatischen VPN auf Pro-App-VPN für iOS-Geräte in Intune](./media/vpn-per-app-automatic.png)

6. Klicken Sie auf **OK** > **OK** > **Erstellen**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Ordnen Sie dem VPN-Profil eine App zu.

Nachdem Sie Ihr VPN-Profil hinzugefügt haben, ordnen Sie die App und Azure AD-Gruppe dem Profil zu.

1. Klicken Sie in **Intune** auf **Client-Apps** > **Apps**.
2. Wählen Sie eine App aus der Liste, und klicken Sie auf **Zuweisungen** > **Gruppe hinzufügen**.
3. Wählen Sie unter **Zuweisungstyp** **Erforderlich** oder **Für registrierte Geräte verfügbar** aus.
4. Wählen Sie **Eingeschlossene Gruppe** > **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen**. Wählen Sie dann die [von Ihnen im Rahmen dieses Artikels erstellte Gruppe aus](#create-a-group-for-your-vpn-users), und klicken Sie auf **Auswählen**.
5. Wählen Sie unter **VPNs** das Pro-App-VPN-Profil aus, [das Sie im Rahmen dieses Artikels erstellt haben](#create-a-per-app-vpn-profile).

    ![Zuweisen einer App zu einem Pro-App-VPN-Profil in Microsoft Intune](./media/vpn-per-app-app-to-vpn.png)

6. Klicken Sie auf **OK** > **Speichern**.

Eine Zuordnung zwischen einer App und einem Profil wird während des nächsten Geräte-Check-Ins entfernt, wenn die folgenden Bedingungen erfüllt sind:

- Die App wurde mit erforderlicher Installationsabsicht ausgerichtet.
- Sowohl das Profil als auch die App sind auf dieselbe Gruppe ausgerichtet.
- Sie entfernen die Pro-App-VPN-Konfiguration aus der App-Zuweisung.

Eine Zuordnung zwischen einer App und einem Profil besteht so lange, bis der Benutzer eine erneute Installation über das Intune-Unternehmensportal anfordert, wenn die folgenden Bedingungen erfüllt sind:

- Die App wurde mit verfügbarer Installationsabsicht ausgerichtet.
- Sowohl das Profil als auch die App sind auf dieselbe Gruppe ausgerichtet.
- Der Endbenutzer hat die App-Installation aus dem Intune-Unternehmensportal angefordert. Dies führt dazu, dass App und Profil auf dem Gerät installiert werden.
- Sie entfernen oder ändern die Pro-App-VPN-Konfiguration über die App-Zuweisung.

## <a name="verify-the-connection-on-the-ios-device"></a>Überprüfen der Verbindung auf dem iOS-Gerät

Sobald Ihr Pro-App-VPN eingerichtet und Ihrer App zugeordnet ist, überprüfen Sie, ob die Verbindung von einem Gerät aus funktioniert.

### <a name="before-you-attempt-to-connect"></a>Bevor Sie eine Verbindung herstellen

 - Stellen Sie sicher, dass Sie alle der oben erwähnten Richtlinien derselben Gruppe bereitstellen. Ansonsten funktioniert das Pro-App-VPN nicht.
 - Wenn Sie die VPN-App Pulse Secure oder eine benutzerdefinierte VPN-Client-App verwenden, können Sie das Tunneln auf App- oder auf Paketebene verwenden. Legen Sie für Tunneln auf App-Ebene den Wert **ProviderType** auf **app-proxy** oder für Tunneln auf Paketebene auf **packet-tunnel** fest. Informieren Sie sich in der Dokumentation Ihres VPN-Anbieters, um sicherzustellen, dass Sie den richtigen Wert verwenden.

### <a name="connect-using-the-per-app-vpn"></a>Herstellen einer Verbindung mithilfe des Pro-App-VPNs

Überprüfen Sie die Zero Touch-Funktion, indem Sie eine Verbindung herstellen, ohne dabei das VPN auswählen oder Ihre Anmeldeinformationen eingeben zu müssen. Die Zero Touch-Funktion bedeutet Folgendes:

 - Das Gerät fordert den Benutzer nicht auf, dem VPN-Server zu vertrauen. Dem Benutzer wird also nicht das Dialogfeld **Dynamic Trust** (Dynamische Vertrauensstellung) angezeigt.
 - Der Benutzer muss keine Anmeldeinformationen eingeben.
 - Das Benutzergerät wird mit dem VPN verbunden, sobald der Benutzer eine der verknüpften Apps öffnet.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Nächste Schritte

- Um die iOS-Einstellungen zu überprüfen, gehen Sie unter [VPN-Einstellungen für iOS-Geräte in Microsoft Intune](vpn-settings-ios.md).
- Weitere Informationen zur VPN-Einstellung und Intune finden Sie unter [Erstellen von VPN-Profilen in Intune](vpn-settings-configure.md).
