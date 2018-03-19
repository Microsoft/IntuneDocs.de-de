---
title: Helpdeskportal zur Problembehandlung
titlesuffix: Microsoft Intune
description: "Helpdeskmitarbeiter verwenden das Portal zur Problembehandlung, um die technischen Probleme der Benutzer zu lösen."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7997bf0494ff52ad25b09301173b65f2478dca37
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Das Portal zur Problembehandlung ermöglicht Helpdesk-Operatoren und Intune-Administratoren das Anzeigen von Benutzerinformationen zum Reagieren auf Hilfeanfragen von Benutzern. Organisationen, die über einen Helpdesk verfügen, können den **Helpdeskoperator** einer Gruppe von Benutzern zuweisen. Durch die Rolle des Helpdeskoperators kann das Blatt **Problembehandlung** verwendet werden.

Auf dem Blatt **Problembehandlung** werden nun Probleme der Benutzer bei der Registrierung angezeigt. Die Details zum Problem und die vorgeschlagenen Abhilfemaßnahmen können Administratoren und Helpdeskmitarbeiter bei der Behandlung von Problemen unterstützen. Bestimmte Probleme bei der Registrierung werden nicht erfasst, und für einige Fehler liegen möglicherweise keine Wiederherstellungsvorschläge vor. 

Weitere Informationen zum Hinzufügen der Rolle des Helpdeskoperators finden Sie unter [Role-based administration control (RBAC) with Intune (Rollenbasierte Zugriffssteuerung mit Intune)](/intune/role-based-access-control).

Wenn ein Benutzer den Support wegen eines technischen Problems mit Intune kontaktiert, gibt der Helpdeskoperator den Namen des Benutzers ein. Intune zeigt nützliche Daten, die Ihnen beim Lösen vieler Probleme der Ebene 1 helfen können, einschließlich:

- Benutzerstatus
- Zuweisungen
- Kompatibilitätsprobleme
- Gerät nicht gefunden
- Das Gerät erhält keine VPN- oder WLAN-Einstellungen
- App-Installationsfehler

## <a name="to-review-troubleshooting-details"></a>Überprüfen der Details zur Problembehandlung

Wählen Sie auf dem Blatt „Problembehandlung“ **Benutzer auswählen** aus, um Benutzerinformationen anzuzeigen. Benutzerinformationen können Ihnen erleichtern, den aktuellen Status von Benutzern und ihren Geräten zu verstehen.  

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie **Problembehandlung** auf dem Blatt **Intune** aus.
4. Klicken Sie auf **Benutzer auswählen**.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden auf dem Blatt „Problembehandlung“ angezeigt. In der folgenden Tabelle werden diese Informationen erläutert.

> [!Note]  
> Sie können auf das Blatt **Problembehandlung** ebenfalls zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="areas-of-troubleshooting-dashboard"></a>Bereiche des Dashboards „Problembehandlung“

Sie können das Blatt **Problembehandlung** verwenden, um Benutzerinformationen zu überprüfen. 

![](/intune/media/troubleshooting-dash.png)

| Bereich | Name | Beschreibung |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Zeigt den Status des aktuellen Intune-Mandanten als **Aktiv** oder **Inaktiv** an.       |
| 2.   | Benutzerauswahl  | Der Name des aktuell ausgewählten Benutzers. Klicken Sie auf **Benutzer wechseln**, um einen neuen Benutzer auszuwählen.       |
| 3.   | Benutzerstatus  | Zeigt den Status der Intune-Lizenz des Benutzers, die Anzahl von Geräten, die jeweilige Gerätekompatibilität, die Anzahl von Apps und die App-Kompatibilität an.       |
| 4.   | Benutzerinformationen  | Verwenden Sie die Liste, um die zu überprüfenden Details auf dem Blatt auszuwählen. <br>Sie können Folgendes auswählen: <ul><li>Mobile Apps<li>App-Schutzrichtlinien<li>Konformitätsrichtlinien<li> Konfigurationsrichtlinien<li> Registrierungseinschränkungen</ul>      |
| 5.   | Gruppenmitgliedschaft  | Yadda       |

## <a name="mobile-apps-reference"></a>Referenz für mobile Apps

Die Apps, die auf Geräten oder Geräten von Benutzern ausgeführt werden, die von Intune und Azure Active Directory (AD) verwaltetet werden.

### <a name="properties"></a>Eigenschaften

Die Eigenschaften von mobilen Apps

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
| Eigentum          | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

### <a name="app-protection-status"></a>Schutzstatus der App

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die in EMS-Technologien (Enterprise Mobility Solution) integriert werden. Dadurch wird ein grundlegender Schutz Ihrer Unternehmensdaten bereitgestellt, wenn diese auf mobile Apps, einschließlich der mobilen Office-Apps, heruntergeladen wird. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
| Letzte Synchronisierung   | Der Zeitstempel, zu dem das Gerät zuletzt mit Intune synchronisiert wurde.                   |

## <a name="app-protection-policies-reference"></a>Referenz für App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden. Dadurch wird ein grundlegender Schutz Ihrer Unternehmensdaten bereitgestellt, wenn diese auf mobile Apps, einschließlich der mobilen Office-Apps, heruntergeladen wird. 

### <a name="properties"></a>Eigenschaften

Die Tabelle fasst den Status der App-Schutzrichtlinien für Geräte zusammen, die mit Intune verwaltet werden.

| Eigenschaft    | Beschreibung                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | Der Name der Anwendung                                                                                                        |
| Bereitgestellt    | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Plattform    | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Anmeldung  | Der Name des Gerätetyps                                                                                                     |
| Letzte Aktualisierung | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

## <a name="compliance-policies-reference"></a>Referenz für Kompatibilitätsrichtlinien

Stellt sicher, dass die für den Zugriff auf Unternehmens-Apps und -daten verwendeten Geräte bestimmte Regeln einhalten wie beispielsweise die Verwendung einer PIN für den Zugriff auf das Gerät und die Verschlüsselung der auf dem Gerät gespeicherten Daten.

### <a name="properties"></a>Eigenschaften

Die Eigenschaften der Kompatibilitätsrichtlinien.

| Eigenschaft      | Beschreibung                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Zuweisung    | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Name          | Der Name der Anwendung                                                                                                        |
| Betriebssystem            | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| Richtlinientyp   | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Zuletzt geändert | Der Name des Gerätetyps                                                                                                     |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Beschreibung                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |

### <a name="app-protection-policies"></a>App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden. Dadurch wird ein grundlegender Schutz Ihrer Unternehmensdaten bereitgestellt, wenn diese auf mobile Apps, einschließlich der mobilen Office-Apps, heruntergeladen wird. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
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
| Richtlinientyp   | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Zuletzt geändert | Der Name des Gerätetyps                                                                                                     |

### <a name="devices"></a>Geräte

Geräte, die von Intune oder durch Benutzer verwaltet werden, die von Intune oder Azure AD verwaltet werden.

| Eigenschaft           | Beschreibung                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Gerätename        | Der Name des Gerätetyps                                                                                                     |
| Verwaltet von         | Der Zeitstempel, zu dem Richtlinie geändert wurde                                                                                              |
| Der Azure AD-Jointyp | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Eigentum          | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein.                                               |
| Mit Intune kompatibel   | Der Name des Gerätetyps                                                                                                     |
| Mit Azure AD kompatibel | Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**. |
| Betriebssystem                 | Das auf dem Gerät installierte Betriebssystem                                                                                       |
| BS-Version         | Die Versionsnummer des Betriebssystems auf dem Gerät                                                                                  |
| Letzter Check-In      | Der Name des Gerätetyps                                                                                                     |


### <a name="app-protection-policies"></a>App-Schutzrichtlinien

Eine App-Schutzrichtlinie ist für mobile Apps verfügbar, die mit EMS-Technologien integriert werden. Dadurch wird ein grundlegender Schutz Ihrer Unternehmensdaten bereitgestellt, wenn diese auf mobile Apps, einschließlich der mobilen Office-Apps, heruntergeladen wird. 

| Eigenschaft    | Beschreibung                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
| App-Name    | Der Name der Anwendung                                                           |
| Gerätename | Der Name des Gerätetyps                                                       |
| Gerätetyp | Der Name des Gerätetyps                                                       |
| Richtlinien    | Der Typ des Gerätebesitzes Dieser kann **Unternehmen**, **Persönlich** oder **Unbekannt** sein. |
| Letzte Synchronisierung   | Der Zeitstempel, zu dem das Gerät zuletzt mit Intune synchronisiert wurde.                   |

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die rollenbasierte Zugriffskontrolle, um Rollen für die Geräte Ihrer Organisation, der mobilen Anwendungsverwaltung und den Aufgaben zum Datenschutz zu definieren. Weitere Informationen finden Sie unter [Role-based administration control (RBAC) with Intune (Rollenbasierte Zugriffssteuerung mit Intune)](/intune/role-based-access-control).

Erfahren Sie mehr über bekannte Probleme in Microsoft Intune. Weitere Informationen finden Sie unter [Bekannte Probleme in Microsoft Intune](/intune/known-issues).

Erfahren Sie, wie ein Supportticket erstellt wird und wie Sie bei Bedarf Hilfe anfordern. [Support anfordern](/intune/get-support)