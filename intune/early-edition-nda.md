---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bacaf8ff4119d4cd40483b65ea45e283d98a51f1
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025201"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Die Early Edition für Microsoft Intune – November 2018

> [!Note]
> Benachrichtigung zum Geheimhaltungsvertrag: Die folgenden Änderungen befinden sich in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Releases von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Deinstallieren von Apps auf unternehmenseigenen überwachten iOS-Geräten<!-- 1281677 -->
Sie können beliebige unternehmenseigene überwachte iOS-Geräte entfernen. Sie können eine beliebige App entfernen, indem Sie entweder Benutzer- oder Gerätegruppen mit dem Zuweisungstyp **Deinstallieren** als Ziel verwenden. Für persönliche oder nicht überwachte iOS-Geräte können weiterhin nur Apps entfernt werden, die mit Intune installiert wurden.

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Unterstützung für iOS 12 OAuth in iOS-E-Mail-Profilen <!--2155106 -->
Die iOS-E-Mail-Profile von Intune unterstützen iOS 12 OAuth. Um dieses Feature anzuzeigen, wählen Sie **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus. Auf dem Blatt „Profil erstellen“ können Sie **OAuth** aktivieren oder deaktivieren. Wenn diese Einstellung aktiviert ist, werden diese zwei Schritte ausgeführt:
1. Geräte, die bereits ein Zielgerät darstellen, erhalten ein neues Profil.
2. Endbenutzer werden erneut zur Eingabe ihrer Anmeldeinformationen aufgefordert.

### <a name="track-installation-of-office-proplus---2620217--"></a>Nachverfolgen der Installation von Office ProPlus <!--2620217-->
Sie können den Installationsfortschritt von [Office ProPlus](apps-add-office365.md) mithilfe der [Seite zum Registrierungsstatus](windows-enrollment-status.md) nachverfolgen.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Unterstützung des Programms zur macOS-Geräteregistrierung für Apple School Manager-Konten <!--3006133-->
Intune unterstützt die Verwendung des Programms zur macOS-Geräteregistrierung für Apple School Manager-Konten.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Temporäres Anhalten des Kioskmodus auf Android-Geräten zum Durchführen von Änderungen <!-- 3041935 -->
Bei Verwendung von Android-Geräten im Multi-App-Kioskmodus kann es erforderlich werden, dass ein IT-Administrator Änderungen am Gerät vornimmt. Eine neue Multi-App-Kioskeinstellung erlaubt es einem IT-Administrator, den Kioskmodus unter Verwendung einer PIN temporär anzuhalten und Zugriff auf das gesamte Gerät zu erhalten.
Die aktuellen Kioskeinstellungen können Sie unter [Android-Kioskeinstellungen](android-kiosk-settings.md) anzeigen.

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Festlegen eines benutzerdefinierten Hintergrunds in der Managed Home Screen-App <!-- 3041945 -->
Es wird eine Einstellung hinzugefügt, mit der Sie den Hintergrund der Managed Home Screen-App auf Android Enterprise-, Multi-App- und Kioskmodusgeräten anpassen können.  Um eine **URL für einen benutzerdefinierten Hintergrund** zu konfigurieren, wechseln Sie im Azure-Portal zu Intune und dann zur Gerätekonfiguration. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivieren einer virtuellen Startschaltfläche auf Android Enterprise-Kioskgeräten <!-- 3042021 -->
Eine neue Einstellung erlaubt es den Benutzern, auf ihrem Gerät auf einen Softkey zu tippen, um auf ihrem Multi-App-Kioskgerät zwischen der Managed Home Screen-App und anderen zugewiesenen Apps zu wechseln. Diese Einstellung ist insbesondere dann nützlich, wenn eine Kiosk-App des Benutzers nicht ordnungsgemäß auf die ZURÜCK-Taste reagiert. Sie können diese Einstellung für unternehmenseigene, einzeln genutzte Android-Geräte konfigurieren. Wechseln Sie im Azure-Portal zu Intune und anschließend zur Gerätekonfiguration, um die Einstellung **Virtuelle Startschaltfläche** zu aktivieren oder zu deaktivieren. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Speichern und Anwenden von App-Schutzrichtlinienzuweisungen <!-- 3104570 -->
Sie erhalten eine bessere Kontrolle über Ihre App-Schutzrichtlinienzuweisungen. Durch das Speichern und Anwenden Ihrer App-Schutzrichtlinienzuweisungen sind nur die vorgesehenen Benutzer direkt von der Zuweisung einer App-Schutzrichtlinie betroffen.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Neue Microsoft Edge-Browsereinstellungen für Windows 10 und höher <!-- 3174639 -->
Eine neu hinzugefügte Einstellung unterstützt Sie dabei, den Microsoft Edge-Browser auf Ihren Geräten zu steuern und zu verwalten. Eine Liste der aktuellen Einstellungen finden Sie in den [Geräteeinschränkungen für Windows 10 (und höher)](device-restrictions-windows-10.md#edge-browser).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Auswählen von Apps zur Nachverfolgung auf der Seite mit dem Registrierungsstatus <!-- 2531007 -->
Sie können auswählen, welche Apps auf der Seite mit dem Registrierungsstatus nachverfolgt werden.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Aktualisierte Benutzeroberfläche für Intune-App-Schutzrichtlinien <!-- 3251427 -->

Mithilfe von Intune-App-Schutzrichtlinien können Sie verschiedene Einstellungen zum Schutz von Daten für mit Intune geschützte Apps konfigurieren, zum Beispiel Microsoft Outlook und Word. Wir ändern die Bezeichnungen für Einstellungen und Schaltflächen, um sie verständlicher zu machen. Die Steuerelemente werden von Steuerelementen mit **Ja**/**Nein**-Auswahl in Steuerelemente mit der Auswahl **Blockieren**/**Zulassen** und **Deaktivieren**/**Aktivieren** geändert. Außerdem werden zur besseren Verständlichkeit auch die Bezeichnungen aktualisiert. Die Einstellungen werden darüber hinaus neu formatiert, um die Einstellungen und ihre Bezeichnungen im Steuerelement nebeneinander anzuzeigen und eine bessere Navigation zu ermöglichen. Die Standardeinstellungen und die Anzahl von Einstellungen bleiben gleich, aber durch die oben genannten Änderungen werden Verständlichkeit, Navigation und Verwendung der Einstellungen verbessert, um dem Benutzer eine einfachere Anwendung der ausgewählten App-Schutzrichtlinien zu ermöglichen.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines <!-- 2055484 -->
Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

### <a name="scope-tags-for-apps---1081941---"></a>Bereichsmarkierungen für Apps <!--1081941 -->
Sie können Bereichsmarkierungen erstellen, um den Zugriff auf Intune-Ressourcen einzuschränken. Fügen Sie einer Rollenzuweisung eine Bereichsmarkierung hinzu, und fügen Sie diese anschließend einem Konfigurationsprofil hinzu. Die Rolle hat nur Zugriff auf Ressourcen mit Konfigurationsprofilen, die über übereinstimmende Bereichsmarkierungen (oder keine Bereichsmarkierung) verfügen.
Um eine Bereichsmarkierung zu erstellen, klicken Sie auf **Intune-Rollen** > **Bereich (Markierungen)** > **Erstellen**.
Um einer Rollenzuweisung eine Bereichsmarkierung hinzuzufügen, klicken Sie auf **Intune-Rollen** > **Alle Rollen** > **Policy and Profile Manager** (Richtlinien- und Profil-Manager) > **Zuweisungen** > **Bereich (Gruppen)**.
Um eine Bereichsmarkierung zu einem Konfigurationsprofil hinzuzufügen, klicken Sie auf **Gerätekonfiguration** > **Profile**, wählen Sie ein Profil aus, und klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard zur Mandantenintegrität <!-- 1124854 -->
Auf der Seite zum Mandantenstatus in Intune werden Informationen zum Mandantenstatus an einem zentralen Ort bereitgestellt. Die Seite ist in vier Abschnitte unterteilt:  
- **Mandantendetails**: Enthält Informationen, z. B. Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und Ihre Lizenzzähler. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connectorstatus**: Enthält Informationen zu konfigurierten Connectors, z. B. Apple VPP, Windows Store for Business und Zertifikatsconnectors. Basierend auf ihrem aktuellen Zustand werden die Connectors als *Fehlerfrei*, *Warnung* oder *Fehlerhaft* gekennzeichnet.
- **Intune Service Health**: Enthält aktive Vorfälle oder Ausfälle für Ihren Mandanten. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).
- **Intune News**: Enthält aktive Nachrichten für Ihren Mandanten, z. B. Benachrichtigungen, dass Ihr Mandant die neuesten Intune-Features erhalten hat. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Bereitgestellte WIP-Richtlinien ohne Benutzerregistrierung <!-- 1434452 -->
WIP-Richtlinien (Windows Information Protection) können bereitgestellt werden, ohne dass MDM-Benutzer ihr Windows 10-Gerät registrieren müssen. Diese Konfiguration ermöglicht es Unternehmen, ihre Unternehmensdokumente auf der Grundlage der WIP-Konfiguration zu schützen, während der Benutzer die Verwaltung seiner eigenen Windows-Geräte beibehalten kann. Sobald Dokumente durch eine WIP-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Die iOS- und macOS-Versionsnummern und -Buildnummern werden angezeigt <!-- 1892471 -->
Unter **Gerätekompatibilität** > **Gerätekompatibilität** wird die iOS-und macOS-Betriebssystemversion angezeigt. In einem zukünftigen Update wird auch die Buildnummer beider Plattformen angezeigt.

Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Durch Anzeigen der Buildnummer können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wird.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Änderungen im Updateprozess für lokale Connectors <!-- 2277554 -->
Auf Grundlage von Kundenfeedback wird die Art und Weise, wie Updates für lokale Connectors ausgeführt werden, geändert. Nachdem Sie erstmalig einen lokalen Connector installiert haben, werden Updates automatisch ausgeführt. Diese Änderung beginnt mit dem neuen PFX Certificate Connector für Microsoft Intune und wird dann langsam auf andere Typen lokaler Connectors ausgeweitet. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Überprüfen des Configuration Manager auf Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



