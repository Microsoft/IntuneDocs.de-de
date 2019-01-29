---
title: Verwenden von Windows Holographic-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Mithilfe von Microsoft Intune können Sie verschiedene Aufgaben auf Geräten verwalten und abschließen, die Windows Holographic for Business und HoloLens ausführen, einschließlich der Konfiguration des Unternehmensportals, der Erstellung einer Konformitätsrichtlinie, der Anpassung der OMA-URI-Einstellungen, der Bereitstellung von Apps, der Kategorisierung von Geräten, der Erstellung von Profilen, der Einschränkung von Geräten, der Aktivierung von Softwareupdates, der Festlegung von Geschäftsbedingungen und der Verwendung von Hello for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.openlocfilehash: df91908f3d3be7be23e3cecfa83e2d92b656b91e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831597"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Verwalten und Verwenden verschiedener Geräteverwaltungsfeatures für Windows Holographic- und HoloLens-Geräten mit Intune

Microsoft Intune umfasst zahlreiche Funktionen, die dabei helfen, Geräte zu verwalten, die Windows Holographic for Business ausführen, z. B. [Microsoft HoloLens](https://docs.microsoft.com/hololens/). Mithilfe von Intune können Sie sicherstellen, dass Geräte mit den Regeln Ihrer Organisation kompatibel sind, und Sie können das Gerät anpassen, indem Sie ein VPN- oder WLAN-Profil hinzufügen. Eine weitere Hauptfunktion besteht darin, das Gerät als Kiosk zu verwenden und eine bestimmte App bzw. eine bestimmte Gruppe von Apps auszuführen.

Die Aufgaben in diesem Artikel helfen Ihnen dabei, Ihre Geräte, die Windows Holographic for Business ausführen, zu verwalten, anzupassen und zu sichern, einschließlich Softwareupdates und der Verwendung von Windows Hello for Business.

Um Windows Holographic-Geräte mit Intune zu verwenden, müssen Sie ein Editionsupgradeprofil erstellen. Dieses Upgradeprofil führt ein Upgrade der Geräte von Windows Holographic zu Windows Holographic for Business durch. Für Microsoft HoloLens können Sie die Commercial Suite erwerben, um die erforderliche Lizenz für das Upgrade zu erhalten. Weitere Informationen erhalten Sie unter [Aktualisieren von Geräten, die Windows Holographic ausführen, auf Windows Holographic for Business](holographic-upgrade.md).

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) kann Ihnen bei der Verwaltung und Steuerung Ihrer Geräte, die Windows Holographic for Business ausführen, helfen. Mit Intune und Azure AD haben Sie folgende Möglichkeiten: 

- **[Einbinden von Geräten in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)**: Sie können Ihre Windows 10-Unternehmensgeräte – Geräte mit Windows Holographic for Business eingeschlossen – in Azure Active Directory (AD) hinzufügen. Mit diesem Feature kann Azure AD das Gerät kontrollieren. Es hilft dabei, zu bestätigen, dass Ihre Benutzer auf die Unternehmensressourcen über Geräte aus zugreifen, die Ihren Sicherheits- und Konformitätsstandards entsprechen.

  Ausführlichere Informationen erhalten Sie unter [Geräteverwaltung in Azure AD](https://docs.microsoft.com/azure/active-directory/devices/overview).

- **[Massenregistrierung für Windows-Geräte](windows-bulk-enroll.md)**: Sie können eine große Anzahl von neuen Windows-Geräten in Azure Active Directory (AD) und Intune einbinden. Dieses Feature wird „Massenregistrierung“ genannt und verwendet Bereitstellungspakete. Diese Pakete verknüpfen die Geräte, die Windows Holographic for Business ausführen, mit Ihrem Azure AD-Mandanten und registriert beide in Intune.

## <a name="company-portal"></a>Unternehmensportal
**[Konfigurieren der Unternehmensportal-App](company-portal-app.md)**

Über die Unternehmensportal-App von Intune können Benutzer auf Unternehmensdaten zugreifen, Geräte registrieren, Apps installieren, ihre IT-Abteilung kontaktieren und vieles mehr. Sie können die Unternehmensportal-App für Ihre Geräte anpassen, auf denen Windows Holographic for Business ausgeführt wird.

Über die Unternehmensportal-App können Sie zudem die folgenden Aktionen ausführen:

- [Entfernen eines Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-windows) mithilfe der Einstellungs-App oder der Unternehmensportal-App
- [Umbenennen eines Geräts](/intune-user-help/rename-your-device-cpapp)
- [Installieren von Apps](/intune-user-help/install-apps-cpapp-windows) auf einem Gerät
- [Manuelles Synchronisieren von Geräten](/intune-user-help/sync-your-device-manually-windows) über die Einstellungs-App oder die Unternehmensportal-App

## <a name="compliance-policy"></a>Kompatibilitätsrichtlinie
**[Erstellen einer Konformitätsrichtlinie für Geräte](compliance-policy-create-windows.md)**

Bei Konformitätsrichtlinien handelt es sich um Regeln und Einstellungen, die Geräte erfüllen müssen, um als „konform“ zu gelten. Verwenden Sie diese Richtlinien mit bedingtem Zugriff, um den Zugriff auf Unternehmensressourcen für Geräte zu blockieren, die nicht konform sind. In Intune erstellen Sie Konformitätsrichtlinien, um den Zugriff für Geräte, auf denen Windows Holographic for Business ausgeführt wird, zuzulassen oder zu blockieren. Sie können beispielsweise eine Richtlinie erstellen, die erfordert, dass „BitLocker“ aktiviert ist.

Weitere Informationen erhalten Sie unter **[Erste Schritte mit Konformitätsrichtlinien](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Bereitstellen und Verwalten von Apps
**[Hinzufügen von Apps zu Intune](apps-add.md)**

Mithilfe von Intune können Sie Apps zu Ihren Geräten hinzufügen, auf denen Windows Holographic for Business ausgeführt wird. Es gibt unter anderem folgende Möglichkeiten, um Apps bereitzustellen:

- [Das Hinzufügen von Microsoft Store-Apps](store-apps-windows.md)
- [Das Hinzufügen von Apps, die Sie erstellt haben](lob-apps-windows.md)
- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)

Microsoft Intune kann universelle Windows-Apps für Microsoft HoloLens-Geräte bereitstellen, die Windows Holographic for Business ausführen. Sie können Ihre App-Pakete direkt in das Azure-Portal für Intune hochladen oder aus Microsoft Store für Unternehmen bereitstellen. Weitere Informationen zu verwandten Bereichen finden Sie in den folgenden Artikeln:
- Informationen zum Bereitstellen von Line-of-Business -Apps (LOB), die das Intune-Azure-Portal nutzen, finden Sie unter [Informationen zum Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune](lob-apps-windows.md).

    > [!NOTE]
    > Eine maximale Paketgröße von 8 GB ist in Intune zulässig. Diese Paketgröße ist nur für die LOB-Apps verfügbar, die in Intune hochgeladen werden.

- Wie Sie Apps mit Microsoft Store für Unternehmen bereitstellen, erfahren Sie unter [Verwalten von Apps, die im Microsoft Store für Unternehmen mit Microsoft Intune erworben wurden](windows-store-for-business.md). 
- Weitere Informationen zur App-Verwaltung mit Microsoft Intune finden Sie unter [Was ist die Microsoft Intune App-Verwaltung?](app-management.md).
- Weitere Informationen zum Entwickeln von Apps für Microsoft HoloLens finden Sie unter [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps) (Mixed Reality-Apps für Microsoft HoloLens). 

> [!NOTE]
> HoloLens-Geräte, die unter Windows 10 Holographic for Business 1607 ausgeführt werden, unterstützen keine online lizenzierten Apps aus dem Microsoft Store für Unternehmen. Weitere Informationen finden Sie unter [Installieren von Apps für HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps).

## <a name="device-actions"></a>Geräteaktionen
Intune verfügt über einige integrierte Aktionen, mit denen IT-Administratoren unterschiedliche Aufgaben lokal auf dem Gerät oder auch remote über Intune im Azure-Portal ausführen können. Für private Geräte, die in Intune registriert sind, können die Benutzer über das Intune-Unternehmensportal einen Remotebefehl erteilen.

Die folgenden Aktionen sind nützlich für Geräte unter Windows Holographic for Business: 

- **[Zurücksetzen](devices-wipe.md#wipe)**: Durch die Aktion **Zurücksetzen** wird das Gerät aus Intune entfernt und auf die Standardwerkseinstellungen zurückgesetzt. Verwenden Sie diese Aktion, bevor Sie das Gerät einem neuen Benutzer geben oder wenn das Gerät verloren gegangen ist oder gestohlen wurde.

- **[Abkoppeln](devices-wipe.md#retire)**: Durch die Aktion **Abkoppeln** wird das Gerät aus Intune entfernt. Zudem werden auch Daten aus verwalteten Apps, Einstellungen und durch Intune zugewiesenen E-Mail-Profilen entfernt. Die persönlichen Daten des Benutzers verbleiben auf dem Gerät.

- **[Synchronisieren von Geräten zum Erhalt der neuesten Richtlinien und Aktionen](device-sync.md)**: Die Geräteaktion **Synchronisieren** erzwingt das sofortige Einchecken bei Intune für das ausgewählte Gerät. Checkt ein Gerät ein, empfängt es sofort alle ihm zugewiesenen ausstehenden Aktionen oder Richtlinien, die zugewiesen sind. Mit diesem Feature können Sie zugewiesene Richtlinien überprüfen und Probleme beheben, ohne den nächsten geplanten Check-In abwarten zu müssen.

**[Was ist die Microsoft Intune Geräteverwaltung?](device-management.md)** Dies ist eine gute Ressource, um weiter Informationen zur Verwaltung von Geräten über das Azure-Portal zu erhalten. 

## <a name="device-categories-and-groups"></a>Gerätekategorien und Gruppen
**[Kategorisieren von Geräten in Gruppen](device-group-mapping.md)**

Mithilfe von Intune können Sie Gerätekategorien erstellen, um Geräte basierend auf den von Ihnen erstellten Kategorien automatisch zu Gruppen hinzuzufügen, z.B. „Vertrieb“, „Buchhaltung“ oder „Personalabteilung“. Dadurch soll das Verwalten der Geräte, auf denen Windows Holographic for Business ausgeführt wird, erleichtert werden.

## <a name="device-configuration-profiles"></a>Gerätekonfigurierungsprofile 
**[Erste Schritte mit Konfigurationsprofilen](device-profiles.md) und [Erstellen Ihres eigenen Profils](device-profile-create.md)**

Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Features werden mithilfe von Profilen verwaltet. Sie können beispielsweise ein Profil erstellen, das Cortana aktiviert oder Windows Defender SmartScreen auf den Geräten zu verwenden, auf denen Windows Holographic for Business ausgeführt wird.

Sie können OMA-URI in Ihren Profilen verwenden, um einige Einstellungen anzupassen, Geräteeinschränkungen zu erstellen und VPN und WLAN zu konfigurieren.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Benutzerdefinierte Geräteeinstellungen](custom-settings-windows-holographic.md)

Sie können ein benutzerdefiniertes Profil in Intune erstellen, um OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zu konfigurieren. Verwenden Sie die OMA-URI-Einstellungen, um verschiedene Features auf Ihren Geräten mit Windows Holographic for Business zu steuern, z.B. das Aktivieren von VPN oder das Suchen nach Updates auf Microsoft Update.

#### <a name="configure-kiosk-modekiosk-settings-holographicmd"></a>[Konfigurieren des Kioskmodus](kiosk-settings-holographic.md)

Mithilfe der in Intune verfügbaren Funktionen für freigegebene oder Gast-PCs können Sie Windows Holographic for Business-Geräte so konfigurieren, dass sie als Kiosk ausgeführt werden. Diese Geräte können eine App (Einzel-App-Kioskmodus) oder mehrere Apps (Multi-App-Kioskmodus) ausführen.

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Geräteeinschränkungen](device-restrictions-windows-holographic.md)

Durch Geräteeinschränkungen können Sie unterschiedliche Einstellungen und Features auf Ihrem Gerät steuern, einschließlich der Anforderung eines Kennworts, der Installation von Apps aus dem [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) und der Aktivierung von Bluetooth. Diese Einschränkungen werden in einem Intune-Profil erstellt. Dieses Profil kann auf mehreren Geräte angewendet werden, auf denen Windows Holographic for Business ausgeführt wird.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Konfigurieren von VPNs](vpn-settings-configure.md)

Virtuelle private Netzwerke (virtual private networks, VPNs) bieten Ihren Benutzern sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. In Intune können Sie ein VPN-Profil erstellen, das spezielle Einstellungen für Geräte enthält, auf denen Windows Holographic for Business ausgeführt wird. Sie können beispielsweise ein VPN-Profil erstellen, damit alle Geräte mit Windows Holographic for Business „Citrix VPN“ als Verbindungstyp verwenden.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Konfigurieren von WLAN](wi-fi-settings-configure.md)

Sie können ebenfalls ein WLAN-Profil in Intune erstellen, um Ihren Geräten mit Windows Holographic for Business Drahtlosnetzwerkeinstellungen zuzuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Ihre Endbenutzer ohne Netzwerkkonfiguration Zugriff auf das Unternehmensnetzwerk. Sie können beispielsweise ein WLAN-Netzwerk erstellen, das nur für Geräte mit Windows Holographic for Business bestimmt ist.

## <a name="shared-multi-user-devices"></a>Von mehren Benutzern gemeinsam verwendete Geräte
[Freigegebene Geräte](shared-user-device-settings-windows-holographic.md)

Geräte, auf denen Windows Holographic for Business ausgeführt wird (z.B. Microsoft HoloLens) können über mehrere Benutzer verfügen. Intune enthält Einstellungen zur Steuerung verschiedener Funktionen auf diesen gemeinsam genutzten Geräten, wie z.B. Energieverwaltung, Verwendung des lokalen Speichers und Kontenverwaltung. Zudem können die Konfigurationsprofile auf Geräte mit unterschiedlichen Betriebssystemen übernommen werden. In derselben Gerätegruppe können sich beispielsweise Geräte mit RS2 und RS3 befinden.

## <a name="software-updates"></a>Softwareupdates
**[Verwalten von Softwareupdates](windows-update-for-business-configure.md)**

Intune enthält ein Feature namens „Updateringe“ für Windows 10-Geräte. Diese Updateringe enthalten Einstellungen, durch die bestimmt wird, wie Updates installiert werden. Sie können beispielsweise ein Wartungsfenster zum Installieren von Updates erstellen oder einen Neustart durchführen, nachdem Updates installiert wurden. Ein Updatering kann auf mehreren Geräte angewendet werden, auf denen Windows Holographic for Business ausgeführt wird.

## <a name="terms-and-conditions"></a>Nutzungsbedingungen
**[Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff](terms-and-conditions-create.md)**

Sie können festlegen, dass Benutzer, bevor sie diese Geräte registrieren und auf Unternehmens-Apps (einschließlich E-Mail-Programmen) zugreifen, zunächst die Geschäftsbedingungen akzeptieren müssen. Definieren Sie in Intune, wie die Geschäftsbedingungen im Unternehmensportal angezeigt werden, und wenden Sie diese ebenfalls auf Geräte an, auf denen Windows Holographic for Business ausgeführt wird.

## <a name="windows-hello-for-business"></a>Windows Hello for Business
**[Verwenden von Windows Hello for Business](windows-hello.md)**

Hello for Business ist eine alternative Anmeldemethode, die ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen. Mit Hello for Business kann Ihr Gerät mit Windows Holographic for Business sich mit einer PIN anmelden, die eine von Ihnen festgelegte Mindestlänge aufweist.
