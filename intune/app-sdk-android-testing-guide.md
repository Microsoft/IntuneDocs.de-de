---
title: Testleitfaden für Entwickler zum Microsoft Intune App SDK für Android
description: Das Microsoft Intune App SDK für Android-Tests Anleitung können Sie Ihre mit Intune verwaltete Android-app zu testen.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072470"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Testleitfaden für Entwickler zum Microsoft Intune App SDK für Android

Das Microsoft Intune App SDK für Android-testen-Anleitung soll Ihre mit Intune verwaltete Android-app testen.  

## <a name="prerequisite-test-accounts"></a>Erforderliche Testkonten
Neue Konten können mit und ohne vorab generierten Daten erstellt werden. Gehen Sie folgendermaßen vor, um ein neues Konto zu erstellen:
1. Navigieren Sie zu der [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant) Standort. 
2. [Einrichten von Intune](https://docs.microsoft.com/intune/setup-steps) Verwaltung mobiler Geräte (MDM) aktivieren.
3. [Erstellen von Benutzern](https://docs.microsoft.com/intune/users-add).
4. [Erstellen Sie Gruppen](https://docs.microsoft.com/intune/groups-add).
5. [Zuweisen von Lizenzen](https://docs.microsoft.com/intune/licenses-assign) je nach Bedarf für Ihre Tests.


## <a name="azure-portal-policy-configuration"></a>Azure-Portal-Richtlinienkonfiguration
[Erstellen und Zuweisen von app-Schutzrichtlinien](https://docs.microsoft.com/intune/app-protection-policies) in die [Azure-Portal-Blatt "Intune"](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Ihre [app-Konfigurationsrichtlinie](https://docs.microsoft.com/intune/app-configuration-policies-overview) auch erstellt und in das Blatt "Intune" zugewiesen werden können.

> [!NOTE]
> Wenn Ihre app im Azure-Portal nicht aufgeführt ist, können Sie es mit einer Richtlinie abzielen, durch Auswählen der **Weitere apps** Option und den Paketnamen in das Textfeld bereitstellen.

> [!IMPORTANT]
> Für eine app-Konfigurationsrichtlinie angewendet werden soll, muss der Benutzer beim Registrieren von angewendet werden durch eine [Intune-app-Schutzrichtlinie](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Testfälle

Die folgenden Testfälle enthalten die Konfiguration und die Bestätigung Schritte. Verwenden Sie diese Anleitung zum Beheben von Problemen mit Intune verwaltete Android-app.

### <a name="required-pin-and-corporate-credentials"></a>Erforderliche PIN "und"-Unternehmensanmeldeinformationen anmelden

Sie können eine Pin ein, den Zugriff auf Unternehmensressourcen benötigen. Darüber hinaus können Sie Unternehmens Authentifizierung erzwingen, damit Benutzer mit verwalteten apps verwenden können. Verwenden Sie die folgenden Schritte aus, um Folgendes festzulegen:

1. Konfigurieren von **PIN für Zugriff anfordern** und **Unternehmensanmeldeinformationen für Zugriff erforderlich** zu **Ja**. Weitere Informationen finden Sie unter [Einstellungen für App-Schutzrichtlinien für Android in Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Überprüfen Sie die folgenden Bedingungen:
    - App-Start sollte darstellen, eine Eingabeaufforderung für die PIN-Eingabe/Setup und/oder der Produktions-Benutzer, der während der Registrierung mit der Unternehmensportal-App verwendet wurde.
    - Fehler um eine gültige anmeldeaufforderung präsentieren kann aufgrund einer falsch konfigurierten android-Manifest, insbesondere die Werte für die ADAL-Integration ("skipbroker", "ClientID" und Authority) sein.
    - Fehler, um eine Aufforderung zu präsentieren wurde möglicherweise durch eine falsch integrierte `MAMActivity` Wert. Weitere Informationen zu `MAMActivity`, finden Sie unter [Microsoft Intune App SDK für Android – Entwicklerhandbuch](app-sdk-android.md).

> [!NOTE] 
> Wenn die oben genannten Test nicht ausgeführt wird, schlägt die folgenden Tests wahrscheinlich ebenfalls fehl. Überprüfen Sie [SDK](app-sdk-android.md##sdk-integration) und [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) Integration.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Übertragen und Empfangen von Daten mit anderen apps einschränken
Sie können die Datenübertragung zwischen verwalteten unternehmensanwendungen wie folgt steuern:

1. Legen Sie **zulassen app Daten an andere apps überträgt** zu **per Richtlinie verwalteten apps**.
2. Legen Sie die Option **Zulassen, dass die App Daten von anderen Apps empfängt** auf **Alle Apps** fest. Verwendung von Intents und Inhaltsanbietern wirkt sich von diesen Richtlinien.
3. Überprüfen Sie die folgenden Bedingungen:
    - Öffnen über eine nicht verwaltete app ordnungsgemäß in Ihre app-Funktionen an.
    - Freigeben von Inhalten zwischen verwalteten apps ist zulässig.
    - Freigabe von verwalteten apps für nicht verwaltete apps (z.B. Chrome) wird blockiert.

### <a name="restrict-cut-copy-and-paste"></a>Einschränken von Ausschneiden, Kopieren und Einfügen
Sie können die Zwischenablage des Systems für verwaltete Anwendungen wie folgt einschränken:

1. Legen Sie **beschränken von Ausschneiden, kopieren und Einfügen mit anderen apps** zu **richtlinienverwaltete mit einfügen**.
2. Überprüfen Sie die folgenden Bedingungen:
    - Kopieren von Text aus Ihrer app in ein verwaltetes ist eine nicht verwaltete app (z. B. Nachrichten) blockiert.

### <a name="prevent-save-as"></a>Verhindern von **Speichern unter**
Sie können steuern, **speichern als** Funktionalität wie folgt:

1. Wenn Ihre app erfordert [integrierte Steuerelemente 'Speichern unter'](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)legen **verhindern "Speichern unter"** zu **Ja**.
2. Überprüfen Sie die folgenden Bedingungen:
    - Speichern ist auf nur die entsprechenden verwalteten stellen beschränkt.

### <a name="file-encryption"></a>Dateiverschlüsselung
Sie können die Daten auf dem Gerät wie folgt verschlüsseln:

1. Legen Sie **appdaten verschlüsseln** zu **Ja**.
2. Überprüfen Sie die folgenden Bedingungen:
    - Verhalten der normale Anwendung ist nicht betroffen.

### <a name="prevent-android-backups"></a>Verhindern von Android-Sicherungen
Sie können die app-Sicherung wie folgt steuern:

1. Wenn Sie festgelegt haben [integriert sicherungseinschränkungen](app-sdk-android.md#protecting-backup-data), konfigurieren Sie **Android-Sicherungen verhindern** zu **Ja**.
2. Überprüfen Sie die folgenden Bedingungen:
    - Sicherungen sind beschränkt.

### <a name="unenrollment"></a>Die Aufhebung der Registrierung
Sie können ein remotezurücksetzen für verwaltete apps mit geschäftlicher e-Mails und Dokumente und persönliche Daten entschlüsselt, wenn es nicht mehr wie folgt verwaltet wird:

1. Die Azure-Portal [Geben Sie eine Zurücksetzung](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Wenn Ihre app nicht registriert wird, für die Zurücksetzung Handler bestätigen Sie die folgenden Bedingungen:
    - Eine vollständige Zurücksetzung der app auftritt.
3. Falls für Ihre Anwendung registriert hat `WIPE_USER_DATA` oder `WIPE_USER_AUXILARY_DATA`, bestätigen Sie die folgenden Bedingungen:
    - Der verwaltete Inhalt aus der app entfernt. Weitere Informationen finden Sie unter [Intune App SDK für Android – Entwicklerhandbuch - Selective Wipe](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Mehrere Identitäten
Die Integration von [Unterstützung mehrerer Identitäten](app-sdk-android.md#multi-identity-optional) ist eine Änderung von hohem Risiko, das gründlich getestet werden muss. Am häufigsten auftretenden Probleme werden aufgrund der falsche Einstellung der Identität (Kontext und der angegebenen gerätebedrohungsstufe entspricht) und auch Nachverfolgen von Dateien (`MAMFileProtectionManager`).

Minimal sollten die folgenden Szenarien für mehrere Identitäten erneut überprüft werden:

- **Speichern unter** -Richtlinie funktioniert korrekt für die verwaltete Identitäten.
- Kopieren Sie und einfügen, die Einschränkungen von korrekt erzwungen werden in persönlichen verwaltet.
- Nur Daten der verwalteten Identität verschlüsselt, und persönliche Dateien werden nicht geändert.
- Selektives zurücksetzen bei der Aufhebung der Registrierung entfernt nur die Daten für verwaltete Identität.
- Für den bedingten Start wird der Endbenutzer aufgefordert, beim Ändern von nicht verwalteten zu verwalteten Kontos (nur beim ersten Mal).

### <a name="app-configuration-optional"></a>App-Konfiguration (optional)
Verhalten von verwalteten apps können Sie wie folgt konfigurieren:

1. Wenn Ihre app app-Konfigurationseinstellungen verwendet wird, sollten Sie testen, dass Ihre app richtig alle Werte verarbeitet, die Sie (als Administrator) festlegen können. [App-Konfigurationsrichtlinien](https://docs.microsoft.com/intune/app-configuration-policies-overview) erstellt und in die Verwendung von Intune zugewiesen werden können.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune](lob-apps-android.md)
