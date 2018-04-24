---
title: 'Verwalten von Windows Holographic-Geräten mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Mithilfe von Microsoft Intune können Sie verschiedene Aufgaben auf Geräten abschließen, die Windows Holographic for Business ausführen, einschließlich der Konfiguration des Unternehmensportals, der Erstellung einer Konformitätsrichtlinie, der Anpassung der OMA-URI-Einstellungen, der Bereitstellung von Apps, der Kategorisierung von Geräten, der Erstellung von Profilen, der Einschränkung von Geräten, der Aktivierung von Softwareupdates, der Festlegung von Geschäftsbedingungen und der Verwendung von Hello for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41c1ea3bf12b83a0f09c8535275ffb58e5f46931
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Anpassen von Geräten, die Windows Holographic ausführen, mithilfe von Intune

Microsoft Intune unterstützt Geräte, die Windows Holographic for Business ausführen, z.B. [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/).

Sie müssen ein Editionsupgradeprofil erstellen, um Geräte mithilfe von Microsoft Intune zu verwalten, auf denen Windows Holographic ausgeführt wird. Dieses Upgradeprofil führt ein Upgrade der Geräte von Windows Holographic zu Windows Holographic for Business durch. Für Microsoft HoloLens können Sie die Commercial Suite erwerben, um die erforderliche Lizenz für das Upgrade zu erhalten. Weitere Informationen erhalten Sie unter [Aktualisieren von Geräten, die Windows Holographic ausführen, auf Windows Holographic for Business](holographic-upgrade.md).

Sie können die Aufgaben in diesem Artikel verwenden, wenn Sie Unterstützung bei der Verwaltung und Anpassung Ihrer Geräte benötigen, auf denen Windows Holographic for Business ausgeführt wird. Sie können beispielsweise Softwareupdates verwalten, VPN-Einstellungen konfigurieren und vieles mehr.

## <a name="company-portal"></a>Unternehmensportal
**[Konfigurieren der Unternehmensportal-App](company-portal-app.md)**

Im Unternehmensportal von Intune können Benutzer auf Unternehmensdaten zugreifen, Geräte registrieren, Apps installieren, Ihre IT-Abteilung kontaktieren und vieles mehr. Sie können die Unternehmensportal-App für Ihre Geräte anpassen, auf denen Windows Holographic for Business ausgeführt wird.

## <a name="compliance-policy"></a>Kompatibilitätsrichtlinie
**[Erstellen einer Konformitätsrichtlinie für Geräte](compliance-policy-create-windows.md)**

Bei Konformitätsrichtlinien handelt es sich um Regeln und Einstellungen, die Geräte erfüllen müssen, um als „konform“ zu gelten. Sie können diese Richtlinien mit bedingtem Zugriff verwenden, um den Zugriff auf Unternehmensressourcen für Geräte zu blockieren, die nicht konform sind. In Intune können Sie Konformitätsrichtlinien erstellen, um den Zugriff für Geräte, auf denen Windows Holographic for Business ausgeführt wird, zuzulassen oder zu blockieren. Sie können beispielsweise eine Richtlinie erstellen, die erfordert, dass „BitLocker“ aktiviert ist.

Weitere Informationen erhalten Sie unter **[Erste Schritte mit Konformitätsrichtlinien](device-compliance-get-started.md)**.

## <a name="deploy-apps"></a>Bereitstellen von Apps
**[Hinzufügen von Apps zu Intune](apps-add.md)**

Mithilfe von Intune können Sie Apps zu Ihren Geräten hinzufügen, auf denen Windows Holographic for Business ausgeführt wird. Es gibt unter anderem folgende Möglichkeiten, um Apps bereitzustellen:

- [Das Hinzufügen von Microsoft Store-Apps](store-apps-windows.md)
- [Das Hinzufügen von Apps, die Sie erstellt haben](lob-apps-windows.md)
- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)

## <a name="device-categories-and-groups"></a>Gerätekategorien und Gruppen
**[Kategorisieren von Geräten in Gruppen](device-group-mapping.md)**

Mithilfe von Intune können Sie Gerätekategorien erstellen, um Geräte basierend auf den von Ihnen erstellten Kategorien automatisch zu Gruppen hinzuzufügen, z.B. „Vertrieb“, „Buchhaltung“ oder „Personalabteilung“. Dadurch soll das Verwalten der Geräte, auf denen Windows Holographic for Business ausgeführt wird, erleichtert werden.

## <a name="device-configuration-profiles"></a>Gerätekonfigurierungsprofile 
**[Erste Schritte mit Konfigurationsprofilen](device-profiles.md) und [Erstellen Ihres eigenen Profils](device-profile-create.md)**

Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Features werden mithilfe von Profilen verwaltet. Sie können beispielsweise ein Profil erstellen, das Cortana aktiviert oder Windows Defender SmartScreen auf den Geräten zu verwenden, auf denen Windows Holographic for Business ausgeführt wird.

Sie können OMA-URI in Ihren Profilen verwenden, um einige Einstellungen anzupassen, Geräteeinschränkungen zu erstellen und VPN und WLAN zu konfigurieren.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Benutzerdefinierte Geräteeinstellungen](custom-settings-windows-holographic.md)

Sie können ein benutzerdefiniertes Profil in Intune erstellen, um OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zu konfigurieren. Verwenden Sie die OMA-URI-Einstellungen, um verschiedene Features auf Ihren Geräten mit Windows Holographic for Business zu steuern, z.B. das Aktivieren von VPN oder das Suchen nach Updates auf Microsoft Update.

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Geräteeinschränkungen](device-restrictions-windows-holographic.md)

Durch Geräteeinschränkungen können Sie unterschiedliche Einstellungen und Features auf Ihrem Gerät steuern, einschließlich der Anforderung eines Kennworts, der Installation von Apps aus dem [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) und der Aktivierung von Bluetooth. Diese Einschränkungen werden in einem Intune-Profil erstellt. Dieses Profil kann auf mehreren Geräte angewendet werden, auf denen Windows Holographic for Business ausgeführt wird.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Konfigurieren von VPNs](vpn-settings-configure.md)

Virtuelle private Netzwerke (virtual private networks, VPNs) bieten Ihren Benutzern sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. In Intune können Sie ein VPN-Profil erstellen, das spezielle Einstellungen für Geräte enthält, auf denen Windows Holographic for Business ausgeführt wird. Sie können beispielsweise ein VPN-Profil erstellen, damit alle Geräte mit Windows Holographic for Business „Citrix VPN“ als Verbindungstyp verwenden.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Konfigurieren von WLAN](wi-fi-settings-configure.md)

Sie können ebenfalls ein WLAN-Profil in Intune erstellen, um Ihren Geräten mit Windows Holographic for Business Drahtlosnetzwerkeinstellungen zuzuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Ihre Endbenutzer ohne Netzwerkkonfiguration Zugriff auf das Unternehmensnetzwerk. Sie können beispielsweise ein WLAN-Netzwerk erstellen, das nur für Geräte mit Windows Holographic for Business bestimmt ist.

## <a name="software-updates"></a>Softwareupdates
**[Verwalten von Softwareupdates](windows-update-for-business-configure.md)**

Intune enthält ein Feature namens „Updateringe“ für Windows 10-Geräte. Diese Updateringe enthalten Einstellungen, durch die bestimmt wird, wie Updates installiert werden. Sie können beispielsweise ein Wartungsfenster zum Installieren von Updates erstellen oder einen Neustart durchführen, nachdem Updates installiert wurden. Ein Updatering kann auf mehreren Geräte angewendet werden, auf denen Windows Holographic for Business ausgeführt wird.

## <a name="terms-and-conditions"></a>Nutzungsbedingungen
**[Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff](terms-and-conditions-create.md)**

Bevor Benutzer Geräte registrieren und auf Unternehmens-Apps (einschließlich E-Mail-Programmen) zugreifen können, können Sie festlegen, dass die Benutzer die Geschäftsbedingungen akzeptieren. In Intune können Sie definieren, wie die Geschäftsbedingungen im Unternehmensportal angezeigt werden und diese ebenfalls auf Geräte anwenden, auf denen Windows Holographic for Business ausgeführt wird.

## <a name="windows-hello-for-business"></a>Windows Hello for Business
**[Verwenden von Windows Hello for Business](windows-hello.md)**

Hello for Business ist eine alternative Anmeldemethode, die ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen. Mit Hello for Business kann Ihr Gerät mit Windows Holographic for Business sich mit einer PIN anmelden, die eine von Ihnen festgelegte Mindestlänge aufweist.
