---
title: Helpdeskportal zur Problembehandlung
titleSuffix: Microsoft Intune
description: Helpdeskmitarbeiter verwenden das Portal zur Problembehandlung, um die technischen Probleme der Benutzer zu lösen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c766f824f9a76ed4da3084ae81e2dde5656e673
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735830"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Das Portal zur Problembehandlung ermöglicht Helpdesk-Operatoren und Intune-Administratoren das Anzeigen von Benutzerinformationen zum Reagieren auf Hilfeanfragen von Benutzern. Organisationen, die über einen Helpdesk verfügen, können den **Helpdeskoperator** einer Gruppe von Benutzern zuweisen. Die Rolle des Helpdeskoperators kann den Bereich **Problembehandlung** verwenden.

Der Bereich **Problembehandlung** zeigt auch Probleme bei der Benutzerregistrierung an. Die Details zum Problem und die vorgeschlagenen Abhilfemaßnahmen können Administratoren und Helpdeskmitarbeiter bei der Behandlung von Problemen unterstützen. Bestimmte Probleme bei der Registrierung werden nicht erfasst, und für einige Fehler liegen möglicherweise keine Wiederherstellungsvorschläge vor.

Weitere Informationen zum Hinzufügen der Rolle des Helpdeskoperators finden Sie unter [Role-based administration control (RBAC) with Intune (Rollenbasierte Zugriffssteuerung mit Intune)](/intune/role-based-access-control).

Wenn ein Benutzer den Support wegen eines technischen Problems mit Intune kontaktiert, gibt der Helpdeskoperator den Namen des Benutzers ein. Intune zeigt nützliche Daten, die Ihnen beim Lösen vieler Probleme der Ebene 1 helfen können, einschließlich:

- Benutzerstatus
- Zuweisungen
- Kompatibilitätsprobleme
- Das Gerät reagiert nicht.
- Das Gerät erhält keine VPN- oder WLAN-Einstellungen
- App-Installationsfehler

## <a name="to-review-troubleshooting-details"></a>Überprüfen der Details zur Problembehandlung

Klicken Sie im Bereich „Problembehandlung“ auf **Benutzer auswählen**, um Benutzerinformationen anzuzeigen. Benutzerinformationen können Ihnen erleichtern, den aktuellen Status von Benutzern und ihren Geräten zu verstehen.  

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Problembehandlung** aus.
4. Klicken Sie auf **Auswählen**, um einen Benutzer auszuwählen, für den ein Problem behoben werden muss.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden im Bereich „Problembehandlung“ angezeigt. In der folgenden Tabelle werden diese Informationen erläutert.

> [!Note]  
> Sie können auch auf den Bereich **Problembehandlung** zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="areas-of-troubleshooting-dashboard"></a>Bereiche des Dashboards „Problembehandlung“

Sie können den Bereich **Problembehandlung** verwenden, um Benutzerinformationen zu überprüfen.

![Dashboard zur Problembehandlung mit nummerierten, in der folgenden Tabelle beschriebenen Bereichen](./media/help-desk-operators/troubleshooting-dash.png)

| Bereich | Name | Beschreibung |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Zeigt den Status des aktuellen Intune-Mandanten als **Aktiv** oder **Inaktiv** an.       |
| 2.   | Benutzerauswahl  | Der Name des aktuell ausgewählten Benutzers. Klicken Sie auf **Benutzer wechseln**, um einen neuen Benutzer auszuwählen.       |
| 3.   | Benutzerstatus  | Zeigt den Status der Intune-Lizenz des Benutzers, die Anzahl von Geräten, die jeweilige Gerätekompatibilität, die Anzahl von Apps und die App-Kompatibilität an.       |
| 4.   | Benutzerinformationen  | Verwenden Sie die Liste in diesem Bereich, um die zu überprüfenden Details auszuwählen. <br>Sie können Folgendes auswählen: <ul><li>Client-Apps<li>Konformitätsrichtlinien<li> Konfigurationsrichtlinien<li>App-Schutzrichtlinien <li>Registrierungseinschränkungen</ul>      |
| 5.   | Gruppenmitgliedschaft  | Zeigt die aktuellen Gruppen, denen der ausgewählte Benutzer als Mitglied angehört.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>Referenz für Registrierungsfehler

In der Tabelle mit Registrierungsfehlern werden Registrierungsversuche aufgelistet, bei denen ein Fehler aufgetreten ist. Es kann sein, dass ein Gerät aus der unten stehenden Tabelle bei einem späteren Registrierungsversuch erfolgreich registriert werden kann. Zudem kann es sein, dass einige fehlgeschlagene Registrierungen nicht aufgelistet sind. Nicht für alle fehlgeschlagenen Registrierungen stehen Informationen zur Fehlerbehebung zur Verfügung.

| Tabellenspalte | Beschreibung |
|-------------|----------|
| Enrollment start (Start der Registrierung) | Der Zeitpunkt, zu dem der Benutzer mit der Registrierung begonnen hat |
| Betriebssystem | Das Betriebssystem des Geräts. |
| BS-Version | Die Betriebssystemversion des Geräts |
| Fehler | Die Ursache für den Fehler |

### <a name="failure-details"></a>Failure details (Fehlerdetails)

Wenn Sie eine Zeile mit einem Fehler auswählen, werden mehr Details angezeigt.

| Abschnitt | Beschreibung |
|-------------|----------|
| Failure details (Fehlerdetails) | Eine ausführlichere Beschreibung des Fehlers |
| Potential remediations (Mögliche Fehlerbehebungen) | Empfohlene Schritte zum Beheben des Fehlers. Für einige Fehler gibt es keine empfohlenen Fehlerbehebungen. |
| Resources (Ressourcen) (Optional) | Links zu Artikeln oder Portalbereichen, in denen Sie entsprechende Aktionen durchführen können |

### <a name="enrollment-errors"></a>Registrierungsfehler

| Fehler | Details |
|-------------|----------|
| iOS Timeout or Failure (iOS-Timeout oder -Fehler.). | Ein Timeout zwischen Gerät und Intune, weil der Benutzer zu lange für die Registrierung gebraucht hat |
| Benutzer nicht gefunden oder nicht lizenziert. | Der Benutzer ist nicht lizenziert oder wurde aus dem Dienst entfernt. |
| Gerät bereits registriert. | Der Benutzer hat versucht, ein Gerät über das Unternehmensportal zu registrieren, das noch für einen anderen Benutzer registriert ist. |
| Not onboarded into Intune (Nicht in Intune integriert.). | Der Benutzer hat versucht, ein Gerät zu registrieren, auf dem Intune-MDM nicht konfiguriert war. |
| Fehler bei der Registrierungsautorisierung. | Der Benutzer hat versucht, ein Gerät über eine veraltete Version des Unternehmensportals zu registrieren. |
| Gerät nicht unterstützt. | Das Gerät erfüllt nicht die Mindestanforderungen für die Intune-Registrierung. |
| Registrierungseinschränkungen nicht erfüllt. | Die Registrierung wurde aufgrund einer vom Administrator konfigurierten Registrierungseinschränkung blockiert. |
| Geräteversion zu niedrig. | Der Administrator hat eine Registrierungseinschränkung konfiguriert, die eine höhere Geräteversion erfordert. |
| Geräteversion zu hoch. | Der Administrator hat eine Registrierungseinschränkung konfiguriert, die eine niedrigere Geräteversion erfordert. |
| Registrierung als persönliches Gerät nicht möglich. | Der Administrator hat eine Registrierungseinschränkung konfiguriert, um persönliche Registrierungen zu blockieren, und das Gerät, bei dem der Fehler aufgetreten ist, wurde nicht als unternehmenseigen vordefiniert. |
| Geräteplattform blockiert. | Der Administrator hat eine Registrierungseinschränkung konfiguriert, die die Plattform dieses Geräts blockiert. |
| Massentoken abgelaufen. | Das Massentoken im Bereitstellungspaket ist abgelaufen. |
| Autopilot-Gerät oder -Details nicht gefunden. | Das Autopilot-Gerät wurde beim Versuch, sich zu registrieren, nicht gefunden. |
| Autopilot-Profil nicht gefunden oder nicht zugewiesen. | Das Gerät verfügt über kein aktives Autopilot-Profil. |
| Unerwartete Autopilot-Registrierungsmethode. | Das Gerät hat versucht, sich über eine nicht zugelassene Methode zu registrieren. |
| Autopilot-Gerät entfernt. | Das Gerät, das versucht, sich zu registrieren, wurde für dieses Konto aus Autopilot entfernt. |
| Gerätekapazität erreicht | Die Registrierung wurde aufgrund einer vom Administrator konfigurierten zulässigen Anzahl von Geräten blockiert. |
| Apple-Onboarding | Die Registrierung aller iOS-Geräte wurde blockiert, weil ein Apple-MDM-Push-Zertifikat in Intune fehlt oder abgelaufen ist. |
| Gerät nicht vorab registriert. | Das Gerät wurde nicht vorab als Unternehmensgerät registriert, und alle Registrierungen von Privatgeräten wurden von einem Administrator blockiert. |
| Das Feature wird nicht unterstützt. | Vermutlich hat der Benutzer versucht, sein Gerät über eine Registrierungsmethode zu registrieren, die von Ihrer Intune-Konfiguration nicht unterstützt wird. |

## <a name="collect-available-data-from-mobile-device"></a>Erfassen verfügbarer Daten mobiler Geräte

Verwenden Sie die folgenden Ressourcen beim Erfassen von Gerätedaten, wenn Sie Geräteprobleme eines Benutzers beheben:
- [Senden von iOS-Registrierungsfehlern an Ihren IT-Administrator](/intune-user-help/send-errors-to-your-it-admin-ios)
- [Verwenden der ausführlichen Protokollierung zur Unterstützung des Supports Ihres Unternehmens bei der Behebung von Geräteproblemen](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [Senden von Android-Protokollen an den Support Ihres Unternehmens mithilfe eines USB-Kabels](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [Senden von Android-Diagnosedatenprotokollen an Ihren IT-Administrator per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [Senden von Android-Registrierungsfehlern an Ihren IT-Administrator](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die rollenbasierte Zugriffskontrolle, um Rollen für die Geräte Ihrer Organisation, der mobilen Anwendungsverwaltung und den Aufgaben zum Datenschutz zu definieren. Weitere Informationen finden Sie unter [Role-based administration control (RBAC) with Intune (Rollenbasierte Zugriffssteuerung mit Intune)](/intune/role-based-access-control).

Erfahren Sie mehr über bekannte Probleme in Microsoft Intune. Weitere Informationen finden Sie unter [Bekannte Probleme in Microsoft Intune](/intune/known-issues).

Erfahren Sie, wie ein Supportticket erstellt wird und wie Sie bei Bedarf Hilfe anfordern. [Support anfordern](/intune/get-support)
