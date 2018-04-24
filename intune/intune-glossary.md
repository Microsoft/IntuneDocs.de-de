---
title: Microsoft Intune-Glossar
titleSuffix: Microsoft Intune
description: Erläuterungen zur Bedeutung der Microsoft Intune-Terminologie.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: 2b59ed38329462ad8d8db604979c8eb725f7973a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune-Glossar
Lernen Sie die Definitionen der in Microsoft Intune häufig verwendeten Begriffe kennen.

## <a name="a"></a>A

|||
|-|-|
|App-Zuweisung|Ermöglicht Benutzern das [Auffinden, Herunterladen und Installieren ](/intune/app-management) der Apps, die sie benötigen. Dies wurde zuvor *App-Bereitstellung* genannt.|
|App-Konfigurationsprofil <br/><br/>App-Konfigurationsrichtlinie|Für mobile Apps mit herstellerspezifischen Konfigurationen. Konfiguriert eine [iOS](/intune/app-configuration-policies-use-ios)- oder [Android](/intune/app-configuration-policies-use-android)-App mit bestimmten Einstellungen, ehe sie ausgeführt wird.|
|App-Überwachung|Ermöglicht das [Überprüfen des aktuellen Status und der letzten Aktivität](/intune/apps-monitor) im Zusammenhang mit der App-Zuweisung.|
|Aufgabe zum Entfernen von App-Schutzdaten|[Entfernt App-Daten](/intune/app-protection-policies) vom Gerät des Benutzers.|
|App-Schutzrichtlinie|Verfügbar für mobile Apps, die mit Enterprise Mobility + Security-Technologien (EMS) integriert werden. Stellt sicher, dass Apps des Benutzers mit den [Datenschutzrichtlinien Ihres Unternehmens](/intune/app-protection-policies) konform sind.|
|App SDK|Das [Microsoft Intune App SDK](/intune/app-sdk) bietet Ihnen die Möglichkeit, Ihren intern entwickelten Apps Funktionen hinzuzufügen, mit denen sie von Intune-App-Schutzrichtlinien verwaltet werden können.|
|App deinstallieren, Aktion|Ermöglicht Ihnen das [Deinstallieren von Apps](/intune/apps-deploy) von Geräten des Benutzers.|
|App Wrapping Tool|Eine [Befehlszeilenanwendung](/intune/apps-prepare-mobile-application-management), die einen Wrapper für die branchenspezifische App erstellt, sodass diese von einer Intune-App-Schutzrichtlinie verwaltet werden kann.|
|Zuweisung, Aktion|Eine Auswahl, die Sie beim [Zuweisen einer App](/intune/apps-deploy) treffen. Sie können auswählen, ob die App-Installation obligatorisch (erforderlich) oder optional (verfügbar) ist, oder Sie können die App deinstallieren.|
|Verfügbare Installation|Wenn Sie eine App mit dieser Aktion zuweisen, wird die App im Unternehmensportal angezeigt, und Benutzer können [sie bei Bedarf installieren](/intune/apps-deploy).|
|Azure-Portal|Die neue Konsole für Intune [Weitere Informationen](/intune/what-is-intune).|

## <a name="b"></a>B

|||
|-|-|
|BYOD|[Bring Your Own Device](/intune/device-enrollment). Benutzer können die Intune-Unternehmensportal-App auf ihrem Gerät installieren und dieses dann registrieren, um Zugriff auf Unternehmensressourcen wie E-Mail, Unternehmens-Apps, Unternehmensdaten und Support zu erhalten.|

## <a name="c"></a>C

|||
|-|-|
|Zertifikatprofil|Dieser Richtlinientyp wird verwendet, um [sicheren Zugriff auf Unternehmensressourcen mit Zertifikaten](/intune/certificates-configure) sicherzustellen, wenn Sie Wi-Fi-, E-Mail- oder VPN-Profile verwenden.|
|COD|[Company Owned Devices, Unternehmenseigene Geräte](/intune/device-enrollment) können je nach Anforderungen der Organisation und den Typen der zu verwaltenden Geräte auf verschiedene Weise registriert werden.|
|Unternehmensportal|Eine App oder eine Website, die Benutzern [Zugriff auf Unternehmensdaten und -Apps](/intune/company-portal-customize) bietet.|
|Kompatibilitätsrichtlinie|Stellt sicher, dass die Geräte [bestimmte Regeln einhalten](/intune/device-compliance), wie beispielsweise die Verwendung einer PIN für den Zugriff auf das Gerät und die Verschlüsselung der auf dem Gerät gespeicherten Daten.|
|Konforme und nicht konforme Apps|Teil eines [Geräteeinschränkungsprofils](/intune/device-restrictions-configure). Mit diesen Einstellungen können Sie eine Liste von Apps definieren, die Benutzer ausführen dürfen oder nicht. Intune informiert Sie über Berichte, dass eine nicht kompatible App installiert oder ausgeführt wurde. Auf einigen Plattformen kann Intune die Installation einer nicht kompatiblen App auch blockieren.|
|Bedingter Zugriff|[Ermöglicht den Zugriff auf Unternehmens-E-Mails, Office 365 und andere Dienste](/intune/conditional-access) nur über Geräte, die den von Ihnen festgelegten Regeln entsprechen.|
|Benutzerdefinierte Richtlinie|[Diese Richtlinien werden verwendet](/intune/custom-settings-configure), wenn eine allgemeine Konfigurationsrichtlinie keine integrierte Einstellung enthält, die Ihren Anforderungen entspricht. Sie könnten eine benutzerdefinierte Richtlinie verwenden, um eine Einstellung auf andere Weise zu erstellen, beispielsweise mithilfe von Apple Configurator oder OMA-URI.|

## <a name="d"></a>D

|||
|-|-|
|Bereitstellung|Der Vorgang des Sendens einer App oder einer Richtlinie an ein Gerät oder einen Benutzer, das/den Sie verwalten. Diese Aktion heißt jetzt *zuweisen*.|
|Geräteregistrierungs-Manager|Mit Intune können Organisationen eine Vielzahl mobiler Geräte mit einem einzelnen Benutzerkonto verwalten. Das [Geräteregistrierungs-Manager-Konto](/intune/device-enrollment-program-enroll-ios) ist ein spezielles Intune-Konto, mit dem bis zu 1.000 Geräte registriert werden können.|
|Geräteprofile|[Diese Profile](/intune/device-profile-create) ermöglichen Ihnen das Konfigurieren einer großen Vielzahl von Sicherheits-, Feature- und Zugriffseinstellungen auf von Ihnen verwalteten Geräten.|

## <a name="e"></a>E

|||
|-|-|
|E-Mail-Profil|Diese Richtlinie kann verwendet werden, um [E-Mail-Zugriffseinstellungen](/intune/email-settings-configure) auf mobilen Geräten einzurichten, sodass der Einrichtungsaufwand für den Endbenutzer minimiert wird.|
|EMS|Microsoft Enterprise Mobility + Security (vormals Enterprise Mobility Suite) schützt Ihre Unternehmensdaten und ermöglicht den Benutzern gleichzeitig den [Zugriff auf die Apps und Inhalte, die sie benötigen](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Endbenutzer|[Gerätebenutzer von z.B. Telefonen und PCs](/intune/end-user-educate), die mit Intune verwaltet werden.|
|Registrieren|Microsoft Intune verwendet die [Registrierung](/intune/device-enrollment) dazu, Geräte in die Verwaltung aufzunehmen und den Zugriff auf Ressourcen zu ermöglichen.|

## <a name="f"></a>F

|||
|-|-|
|FastTrack|Ein [Microsoft-Dienst](https://technet.microsoft.com/library/mt228265.aspx) für Intune-Benutzer mit 150 Lizenzen in einem berechtigten Plan. Über diesen Dienst können Microsoft-Spezialisten mit Ihnen zusammenarbeiten, um Sie beim Einrichten und Ausführen von Intune zu unterstützen.|

## <a name="g"></a>G

|||
|-|-|
|Gruppen|Mithilfe von Gruppen können Sie [Benutzer oder Geräte logisch zusammenstellen](/intune/groups-get-started). Sie könnten beispielsweise eine Gruppe aller Windows-PCs erstellen. Sie können dann diesen Gruppen Apps und Profile zuweisen.|

## <a name="h"></a>H

|||
|-|-|
|Hybrid|Eine Konfiguration, bei der Sie in Intune registrierte Geräte über die System Center Configuration Manager-Konsole verwalten können.|

## <a name="i"></a>I

|||
|-|-|
|Azure-Portal|Das Azure-Portal, das Sie für die meisten Intune-Verwaltungsvorgänge verwenden.|
|Intune-Softwareclient|Das [Verwalten einiger Windows-PCs](/intune-classic/get-started/choose-how-to-manage-devices) kann Ihnen die Entscheidung erleichtern, sich für eine Methode zu entscheiden.|
|Intune-Softwareherausgeber|Ein Tool, mit dem Sie [Apps definieren, die Sie bereitstellen möchten, und auf Ihren Cloudspeicher hochladen](/intune-classic/deploy-use/add-apps).|
|Inventarisierung|Damit können Sie die [Hardware und die installierte Software](/intune/device-inventory) von Geräten anzeigen, die Sie verwalten.|

## <a name="k"></a>K

|||
|-|-|
|Kioskmodus|Mit diesem als Teil eines [Geräteeinschränkungsprofils](/intune/device-restrictions-configure) konfigurierten Modus können Sie Geräte sperren. Sie könnten beispielsweise ein Gerät in einer Filiale so konfigurieren, dass nur einige App darauf ausgeführt werden können.|

## <a name="m"></a>M

|||
|-|-|
|Managed Browser|Eine [Webbrowseranwendung](/intune/app-configuration-managed-browser), die Sie mit Intune in Ihrer Organisation zuweisen können. Mit einer Richtlinie für Managed Browser wird eine Zulassungs- oder Blockierungsliste konfiguriert, um die Websites einzuschränken, die Benutzer von Managed Browser besuchen können.|
|MDM-Autorität|Die [MDM-Autorität](/intune/mdm-authority-set) definiert den Verwaltungsdienst, der über die Berechtigung zum Verwalten einer Gruppe von Geräten verfügt. Die Optionen für die MDM-Autorität umfassen Intune selbst und Configuration Manager mit Intune.|
|Richtlinie zur Konfiguration mobiler Apps|Für mobile Apps mit herstellerspezifischen Konfigurationen. Eine [iOS](/intune/app-configuration-policies-use-ios)- oder [Android](/intune/app-configuration-policies-use-android)-Richtlinie, die zum Angeben von Einstellungen für kompatible Apps bei deren Ausführung verwendet wird, beispielsweise zur Angabe eines Firmennamens oder einer Serveradresse.|
|Richtlinie zur Bereitstellung mobiler Apps|Eine iOS-Richtlinie, mit der Sie sicherstellen können, dass die [Bereitstellungsprofile](/intune/app-provisioning-profile-ios) für die von Ihnen zugewiesenen iOS-Apps nicht ablaufen.|
|Mobile Anwendungsverwaltung|Mit der [mobilen Anwendungsverwaltung (Mobile Application Management, MAM)](/intune/app-lifecycle) können Sie mobile Apps für Ihre Benutzer veröffentlichen, per Push bereitstellen, konfigurieren, schützen, überwachen und aktualisieren.
|Verwaltung mobiler Geräte|Mit der [Verwaltung mobiler Geräte (Mobile Device Management, MDM)](/intune/device-lifecycle) können Sie Geräte in Intune registrieren, sodass Sie diese Gräte bereitstellen, konfigurieren, überwachen und verwalten können.



## <a name="o"></a>O

|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Ein Geräteverwaltungsprotokoll gemäß Industriestandard, das von vielen Hardwareherstellern verwendet wird, um die Steuerung von Funktionen von mobilen Geräten und PCs zu ermöglichen.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Diese Elemente dienen zur Identifizierung einzelner Geräteeinstellungen, die dem OMA-DM-Standard entsprechen. Diese Einstellungen können in [benutzerdefinierten Intune-Profilen](/intune/custom-settings-configure) verwendet werden, wenn es keine integrierte Einstellung gibt, die Ihren Anforderungen entspricht.|

## <a name="p"></a>P

|||
|-|-|
|Zurücksetzen der Kennung|Eine Intune-Funktion, mit der Sie auf unterstützten Geräten den Endbenutzer zum [Zurücksetzen der Kennung](/intune/device-passcode-reset) zwingen können.|

## <a name="r"></a>R

|||
|-|-|
|Remotesperre|Eine Intune-Funktion, mit der Sie [unterstützte Geräte sperren](/intune/device-remote-lock) können, auch wenn Sie nicht im Besitz des Geräts sind.|
|Erforderliche Installation|Wenn Sie eine App mit dieser Aktion zuweisen, ist kein [Eingreifen des Benutzers](/intune/apps-deploy) erforderlich, um die Installation abzuschließen. Auf einigen Plattformen muss der Endbenutzer die Installation ggf. akzeptieren.|


## <a name="s"></a>S

|||
|-|-|
|Selektives Zurücksetzen|Bei einer [selektiven Zurücksetzung](/intune/device-company-data-remove) werden nur Unternehmensdaten, die von der App-Schutzrichtlinie geschützt werden, einschließlich Einstellungen und E-Mail-Profile, vom Gerät entfernt. Die persönlichen Daten des Benutzers bleiben beim selektiven Zurücksetzen auf dem Gerät erhalten.|
|Sideloading|Die Aktion der Installation einer branchenspezifischen App, ohne auf diese in einem App-Store zuzugreifen.|
|Abonnement|Die von Ihnen eingegangene Vereinbarung, die Ihnen den Zugriff auf einen Intune-Mandanten ermöglicht.|

## <a name="t"></a>T

|||
|-|-|
|TeamViewer|Eine Drittanbieteranwendung, die mit Intune verwendet werden kann, um [Funktionen der Remoteunterstützung](/intune/device-profile-android-teamviewer) für Android-Geräte bereitzustellen, die Sie mit Intune verwalten.|
|Mandant|Eine einzelne Instanz des Intune-Diensts, auf die Sie mit einem Abonnement zugreifen können.|
|Nutzungsbedingungen|Ein Richtlinientyp, den Sie Benutzern zuweisen und der Informationen enthält, die die Benutzer [lesen und akzeptieren](/intune/terms-and-conditions-create) müssen, bevor sie das Unternehmensportal zum Registrieren und zum Zugreifen auf ihre Arbeit verwenden können.|

## <a name="v"></a>V

|||
|-|-|
|Per Volumenlizenz erworbene Apps und Bücher|Einige App-Stores bieten die Möglichkeit, mehrere Lizenzen für Apps oder Bücher zu erwerben, die in Ihrem Unternehmen verwendet werden sollen. Intune hilft Ihnen beim Verwalten von Apps und Büchern, [die Sie über ein solches Programm erworben haben](/intune/vpp-apps). Sie können die Volumenlizenzinformationen aus dem App-Store importieren, die Anzahl der verwendeten Lizenzen nachverfolgen und sich daran hindern, mehr Kopien einer App zu installieren, als Sie besitzen.|
|VPN-Profil|Eine Richtlinie, die [VPN-Einstellungen](/intune/vpn-settings-configure) für von Ihnen verwaltete Geräte zuweist, wodurch der erforderliche Einrichtungsaufwand für Endbenutzer minimiert wird.|

## <a name="w"></a>W

|               |                                                                                                                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| WLAN-Profil | Eine Richtlinie, die [WLAN-Einstellungen](/intune/wi-fi-settings-configure) für Geräte bereitstellt, sodass Benutzer eine Verbindung mit Ihrem Firmennetzwerk herstellen können, ohne entsprechende Einstellungen kennen oder konfigurieren zu müssen. |

