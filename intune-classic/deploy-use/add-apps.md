---
title: Hinzufügen von Apps
description: Nehmen Sie sich vor der Bereitstellung von Apps mit Intune etwas Zeit, um sich mit den in diesem Thema vorgestellten Konzepten vertraut zu machen.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 69c3f671fdf1ac0d281e484f9090356a3ce246a8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="add-apps-with-microsoft-intune"></a>Hinzufügen von Apps mit Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nehmen Sie sich vor der Bereitstellung von Apps mit Microsoft Intune etwas Zeit, um sich mit den in diesem Thema vorgestellten Konzepten vertraut zu machen. Diese Konzepte helfen Ihnen dabei zu verstehen, welche Apps auf welcher Plattform bereitgestellt werden können. Zudem bieten sie Informationen zu den Voraussetzungen, die erfüllt sein müssen, bevor Sie die Apps bereitstellen können.

## <a name="app-types-that-you-can-deploy"></a>Für die Bereitstellung verfügbare App-Typen

### <a name="software-installer"></a>Softwareinstallationsprogramm

|App-Typ|Details|
|----------------|-------|
|**Windows Installer (&#42;.exe, &#42;.msi)**|Diese Art von App muss die automatische Installation ohne Benutzereingabe unterstützen. Die Dokumentation Ihrer App sollte die relevanten Befehlszeilenoptionen einbeziehen, die für die automatische Installation der App erforderlich sind (z. B. **/q**). Eine Liste der gebräuchlichsten Befehlszeilenschalter finden Sie unter [Befehlszeilenschalter für Microsoft Windows Installer](https://support.microsoft.com/kb/227091).<br><br>Alle zusätzlichen Dateien und Ordner, die für das Setupprogramm der App erforderlich sind, müssen an dem für die Setupdateien angegebenen Speicherort verfügbar sein.<br><br>In den meisten Fällen müssen bei Windows Installer-Dateien (MSI) und Windows Installer Patch-Dateien (MSP-Dateien) von Intune keine Befehlszeilenargumente installiert werden. Überprüfen Sie die Dokumentation Ihrer App.<br><br>Sind Befehlszeilenargumente erforderlich, müssen sie in "Name=Wert"-Paaren (z. B. TRANSFORMS=custom_transform.mst) eingegeben werden.<br><br>Dieser App-Typ gilt nur für PCs, die den Intune-Softwareclient ausführen.|
|**App Package für Android (&#42;.apk)**|Zum Bereitstellen von Android-Apps müssen Sie über ein gültiges APK-Paket verfügen.|
|**App Package für iOS (&#42;.ipa)**|Zum Bereitstellen von iOS-Apps müssen Sie über ein gültiges IPA-Paket verfügen.<br><br>Das IPA-Paket muss von Apple signiert sein, und das im Bereitstellungsprofil angegebene Ablaufdatum darf noch nicht erreicht sein. Intune kann iOS-Anwendungen mit Unternehmenszertifikat verteilen.<br><br>Es werden nicht alle Apps mit Entwicklerzertifikat von Apple unterstützt.<br><br>Ihr Unternehmen muss für das iOS Developer Enterprise Program registriert sein.<br><br>Stellen Sie sicher, dass der Zugriff auf die iOS-Bereitstellungs- und -Zertifizierungswebsites durch die Firewall Ihrer Organisation zugelassen wird.<br><br>Sie müssen keine Manifestdatei (PLIST) mit der App bereitstellen.|
|**Windows Phone-App-Paket (&#42;.xap, .appx, .appxbundle)**|Sie benötigen ein Codesignaturzertifikat für mobile Geräte, um Apps bereitstellen zu können. Weitere Informationen finden Sie unter [Einrichten der Windows Phone-Verwaltung mit Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).|
|**Windows-App-Paket (.appx, .appxbundle)**|Sie benötigen ein Codesignaturzertifikat für mobile Geräte, um Apps bereitstellen zu können. Weitere Informationen finden Sie unter [Einrichten der Windows-Geräteverwaltung mit Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).|
|**Windows Installer über MDM (&#42;.msi)**|Mit dieser App können Sie Windows Installer-basierte Apps auf registrierten PCs erstellen und bereitstellen, auf denen Windows 10 ausgeführt wird. Diese PCs werden mithilfe der Verwaltung mobiler Geräte (MDM) verwaltet.<br /><br />Sie können nur eine einzelne Datei mit der Erweiterung „MSI“ hochladen.<br><br>Produktcode und Produktversion der Datei werden zur Erkennung der App verwendet.<br><br>Es wird das standardmäßige Verhalten bei Neustart der App verwendet. Intune steuert dieses Verhalten nicht.<br><br>Pro Benutzer definierte MSI-Pakete werden für einen einzelnen Benutzer installiert.<br><br>Pro Gerät definierte MSI-Pakete werden für alle Benutzer des Geräts installiert.<br><br>MSI-Pakete im Dualmodus werden zurzeit nur für alle Benutzer des Geräts installiert.<br><br>App-Updates werden unterstützt, wenn jede Version den gleichen MSI-Produktcode aufweist.<br>
Alle App-Typen mit Softwareinstallationsprogramm sind in Ihren Cloudspeicher hochgeladen.

### <a name="external-link"></a>**Externer Link**
Verwenden Sie einen externen Link, wenn Sie über Folgendes verfügen:
- Eine URL, mit der Benutzer eine App aus einem App-Store herunterladen können.
- Einen Link zu einer webbasierten App, die im Webbrowser ausgeführt wird.

Auf externen Links basierende Apps werden nicht in Ihrem Intune-Cloudspeicher gespeichert.
### <a name="managed-ios-app-from-the-app-store"></a>**Verwaltete iOS-App aus dem App Store**
Sie können kostenlose iOS-Apps aus dem App Store mithilfe verwalteter iOS-Apps verwalten und bereitstellen. Sie können mithilfe verwalteter iOS-Apps auch [Richtlinien für die Verwaltung mobiler Anwendungen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) mit [kompatiblen Apps](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx) verknüpfen und ihren Status in der Administratorkonsole überprüfen.<br /><br />Verwaltete iOS-Apps werden nicht in Ihrem Intune-Cloudspeicher gespeichert.

> [!TIP]
> Optionen für mobile Geräte sind nicht verfügbar, bis Sie [die MDM-Autorität](prerequisites-for-enrollment.md) auf Intune festgelegt haben.

## <a name="intune-software-publisher"></a>Intune-Softwareherausgeber
Der Microsoft Intune-Softwareherausgeber wird gestartet, wenn Sie in der Intune-Administratorkonsole Apps hinzufügen oder ändern. Vom Herausgeber wählen und konfigurieren Sie einen Software-Installationsprogrammtyp, für den eine der folgenden Optionen gilt:

- Hochladen von Apps (Programme für Computer oder Apps für mobile Geräte), die im Intune-Cloudspeicher gespeichert werden.
- Verknüpfen mit einem Onlinespeicher oder einer Webanwendung.

Bevor Sie mit der Verwendung des Softwareherausgebers beginnen, müssen Sie die Vollversion von [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851) installieren. Nach der Installation müssen Sie möglicherweise den Computer neu starten, damit der Softwareherausgeber ordnungsgemäß geöffnet wird.

## <a name="cloud-storage-space"></a>Cloudspeicherplatz
Alle Apps, die Sie mithilfe des Software-Installationsprogrammtyps erstellen, werden in den Microsoft Intune-Cloudspeicher hochgeladen. Ein Testabonnement von Intune enthält 2 GB cloudbasierten Speicher, der zum Speichern von verwalteten Apps und Updates verwendet wird. Ihr vollständiges Abonnement enthält 20 GB Speicherplatz.

Im Knoten **Speichernutzung** des Arbeitsbereichs **Verwaltung** können Sie sehen, wie viel Speicherplatz Sie verwenden. Sie können zusätzlichen Speicher für Intune mit Ihrer ursprünglichen Zahlungsweise erwerben.  Wenn Sie per Rechnung oder Kreditkarte gezahlt haben, besuchen Sie das [Portal zur Abonnementverwaltung](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Wenden Sie sich alternativ an Ihren Partner oder Vertriebsmitarbeiter.

Anforderungen für Cloudspeicherplatz:

-   Alle App-Installationsdateien müssen sich im selben Ordner befinden.
-   Die maximale Dateigröße für hochgeladene Dateien beträgt 2 GB.


## <a name="support-for-universal-windows-platform-uwp-apps"></a>Unterstützung für UWP-Apps (Universelle Windows-Plattform)
Windows 10-PCs erfordern keinen Sideload-Schlüssel für die Installation von branchenspezifischen Apps. Allerdings muss der Registrierungsschlüssel **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** den Wert **1** haben, um das Querladen zu aktivieren.

Wenn dieser Registrierungsschlüssel nicht konfiguriert ist, legt Intune diesen Wert automatisch auf **1** fest, wenn Sie zum ersten Mal eine App auf dem Gerät bereitstellen. Wenn Sie diesen Wert auf **0** festlegen, kann Intune den Wert nicht automatisch ändern, und die Bereitstellung branchenspezifischer Apps misslingt.

Branchenspezifische UWP-Apps müssen mit einem codesignierten Zertifikat signiert sein, das auf jedem Gerät, auf dem die App bereitgestellt ist, als vertrauenswürdig eingestuft ist. Sie können ein Zertifikat aus einer internen PKI-Infrastruktur oder von einer öffentlichen Drittanbieter-Stammzertifizierungsstelle verwenden, das auf dem Gerät installiert ist.

Auf Windows 10 Mobile-Geräten können Sie ein nicht von Symantec stammendes Codesignaturzertifikat zum Signieren universeller **APPX**-Apps verwenden. Für **XAP**-Apps sowie für **APPX**-Pakete, die für Windows Phone 8.1 erstellt wurden, die Sie auf Windows 10 Mobile-Geräten installieren möchten, müssen Sie ein Codesignaturzertifikat von Symantec verwenden.

### <a name="dependencies-for-uwp-apps"></a>Abhängigkeiten für UWP-Apps

Wenn Sie ein Windows 10 Universal-APPXBUNDLE-Paket zu Intune hinzufügen, müssen Sie außerdem sicherstellen, dass alle Abhängigkeiten für die App hochgeladen werden.
Stellen Sie beim Hochladen von Abhängigkeiten sicher, dass sich der Ordner **Abhängigkeiten**, der bei Erstellung der App angelegt wurde, im gleichen Ordner wie die .appxbundle-Datei selbst befindet.
Auf diese Weise werden beim Hochladen der App in Intune alle Dateien im Ordner **Abhängigkeiten** ebenfalls hochgeladen. Der folgende Bildschirm veranschaulicht diesen Prozess:


![Auswählen von Windows 10 UWP APPXBUNDLE-Abhängigkeiten](./media/w10-dependencies.png)


## <a name="next-steps"></a>Nächste Schritte

Sie fügen Apps in der Intune-Konsole hinzu, bevor Sie diese bereitstellen können. Sie können Apps für [registrierte Geräte](add-apps-for-mobile-devices-in-microsoft-intune.md) oder für [Windows-PCs hinzufügen, die Sie mit der Intune-Clientsoftware verwalten](add-apps-for-windows-pcs-in-microsoft-intune.md).
