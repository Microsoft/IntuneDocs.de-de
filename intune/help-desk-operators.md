---
title: Helpdeskportal zur Problembehandlung
titlesuffix: Microsoft Intune
description: Helpdeskmitarbeiter verwenden das Portal zur Problembehandlung, um die technischen Probleme der Benutzer zu lösen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba74c93e2ef7dc469ebd7f5086659181b72a0981
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230022"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Problembehandlung** aus.
4. Klicken Sie auf **Auswählen**, um einen Benutzer auszuwählen, für den ein Problem behoben werden muss.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden im Bereich „Problembehandlung“ angezeigt. In der folgenden Tabelle werden diese Informationen erläutert.

> [!Note]  
> Sie können auch auf den Bereich **Problembehandlung** zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="areas-of-troubleshooting-dashboard"></a>Bereiche des Dashboards „Problembehandlung“

Sie können den Bereich **Problembehandlung** verwenden, um Benutzerinformationen zu überprüfen.

![](/intune/media/troubleshooting-dash.png)

| Bereich | Name | Beschreibung |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Zeigt den Status des aktuellen Intune-Mandanten als **Aktiv** oder **Inaktiv** an.       |
| 2.   | Benutzerauswahl  | Der Name des aktuell ausgewählten Benutzers. Klicken Sie auf **Benutzer wechseln**, um einen neuen Benutzer auszuwählen.       |
| 3.   | Benutzerstatus  | Zeigt den Status der Intune-Lizenz des Benutzers, die Anzahl von Geräten, die jeweilige Gerätekompatibilität, die Anzahl von Apps und die App-Kompatibilität an.       |
| 4.   | Benutzerinformationen  | Verwenden Sie die Liste in diesem Bereich, um die zu überprüfenden Details auszuwählen. <br>Sie können Folgendes auswählen: <ul><li>Client-Apps<li>Konformitätsrichtlinien<li> Konfigurationsrichtlinien<li>App-Schutzrichtlinien <li>Registrierungseinschränkungen</ul>      |
| 5.   | Gruppenmitgliedschaft  | Zeigt die aktuellen Gruppen, denen der ausgewählte Benutzer als Mitglied angehört.       |

## <a name="client-apps-reference"></a>Referenz für Client-Apps

Die Apps, die auf folgenden Geräten ausgeführt werden:
- Geräte, die von Intune und Azure Active Directory verwaltet werden 
- Geräte, deren Benutzer von Intune und Azure Active Directory verwaltet werden

### <a name="properties"></a>Eigenschaften

Die Eigenschaften von Client-Apps

| Eigenschaft      | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | Der Name der Anwendung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Betriebssystem            | Das auf dem Gerät installierte Betriebssystem                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Typ          | Sie können einen Zuweisungstyp für jede App auswählen.  <br> **Verfügbar:** Benutzer installieren die App über die Unternehmensportal-App oder -Website.  <br> **Nicht verfügbar:** Die App wird nicht installiert und nicht im Unternehmensportal angezeigt. <br> **Deinstallieren:** Die App wird auf Geräten in den ausgewählten Gruppen deinstalliert.  <br> **Verfügbar ohne Registrierung:** Weisen Sie diese App Benutzergruppen zu, deren Geräte nicht bei Intune registriert sind. |
| Zuletzt geändert | Der Name des Gerätetyps                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Beschreibung                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| App-Installation | Gibt an, ob auf dem jeweiligen Gerät eine App-Installation fehlgeschlagen ist oder erfolgreich abgeschlossen wurde. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

### <a name="app-protection-status"></a>Schutzstatus der App

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die in EMS-Technologien (Enterprise Mobility Solution) integriert werden. Durch diese Richtlinien werden Ihrer Unternehmensdaten grundlegend geschützt, wenn diese auf mobile Apps, einschließlich mobile Office-Apps, heruntergeladen werden. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| Letzte Synchronisierung   | Der Zeitstempel, zu dem das Gerät zuletzt mit Intune synchronisiert wurde.                   |

## <a name="app-protection-policies-reference"></a>Referenz für App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden können. Diese Richtlinien schützen Ihre Unternehmensdaten grundlegend, wenn diese in mobile Apps heruntergeladen werden (dazu zählen auch mobile Office-Apps). 

### <a name="properties"></a>Eigenschaften

Die Tabelle fasst den Status der App-Schutzrichtlinien für Geräte zusammen, die mit Intune verwaltet werden.

| Eigenschaft    | Beschreibung                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Der Name der Anwendung                                                                                                        |
| Bereitgestellt    | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Plattform    | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Anmeldung  | Der Name des Gerätetyps                                                                                                     |
| Letzte Aktualisierung | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

## <a name="compliance-policies-reference"></a>Referenz für Kompatibilitätsrichtlinien

Stellt sicher, dass die für den Zugriff auf Unternehmens-Apps und -daten verwendeten Geräte bestimmte Regeln einhalten, z.B. die Verwendung einer PIN für den Zugriff auf das Gerät und die Verschlüsselung der auf dem Gerät gespeicherten Daten.

### <a name="properties"></a>Eigenschaften

Die Eigenschaften der Kompatibilitätsrichtlinien.

| Eigenschaft      | Beschreibung                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Zuweisung    | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Name          | Der Name der Anwendung                                                                                                        |
| Betriebssystem            | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| Richtlinientyp   | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Zuletzt geändert | Der Name des Gerätetyps                                                                                                     |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Beschreibung                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

### <a name="app-protection-policies"></a>App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden. Durch diese Richtlinien werden Ihrer Unternehmensdaten grundlegend geschützt, wenn diese auf mobile Apps, einschließlich mobile Office-Apps, heruntergeladen werden. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| Letzte Synchronisierung   | Der Zeitstempel, zu dem das Gerät zuletzt mit Intune synchronisiert wurde.                   |

## <a name="configuration-policies-reference"></a>Referenz für Konfigurationsrichtlinien

Eine App-Konfigurationsrichtlinie ist für mobile Geräte mit herstellerspezifischen Konfigurationen verfügbar. 

### <a name="properties"></a>Eigenschaften

Die Eigenschaften der Konfigurationsrichtlinien

| Eigenschaft      | Beschreibung                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Zuweisung    | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Name          | Der Name der Anwendung                                                                                                        |
| Betriebssystem            | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| Richtlinientyp   | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Zuletzt geändert | Der Name des Gerätetyps                                                                                                     |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Beschreibung                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)).                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |


### <a name="app-protection-policies"></a>App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden. Durch diese Richtlinien werden Ihrer Unternehmensdaten grundlegend geschützt, wenn diese auf mobile Apps, einschließlich mobile Office-Apps, heruntergeladen werden. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes (**Company**, **Personal** oder **Unknown** („Unternehmen“, „Privat“ oder „Unbekannt“)). |
| Letzte Synchronisierung   | Der Zeitstempel, zu dem das Gerät zuletzt mit Intune synchronisiert wurde.                   |

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
