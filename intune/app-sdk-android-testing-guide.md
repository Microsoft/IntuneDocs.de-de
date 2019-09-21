---
title: Testleitfaden für Entwickler zum Microsoft Intune App SDK für Android
description: Der Testleitfaden zum Microsoft Intune App SDK für Android unterstützt Sie beim Testen Ihrer mit Intune verwalteten Android-App.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91b7fc7414c3a6d6517cd4b704cb5e99ddcf96d0
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167189"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Testleitfaden für Entwickler zum Microsoft Intune App SDK für Android

Der Testleitfaden zum Microsoft Intune App SDK für Android wurde dazu entworfen, Sie beim Testen Ihrer mit Intune verwalteten Android-App zu unterstützen.  

## <a name="prerequisite-test-accounts"></a>Erforderliche Testkonten
Neue Konten können mit und ohne vorab generierte Daten erstellt werden. Gehen Sie folgendermaßen vor, um ein neues Konto zu erstellen:
1. Öffnen Sie die [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant)-Website. 
2. [Richten Sie Intune ein](setup-steps.md), um die mobile Geräteverwaltung (MDM) zu aktivieren.
3. [Erstellen Sie Benutzer](users-add.md).
4. [Erstellen Sie Gruppen](groups-add.md).
5. [Weisen Sie Lizenzen je nach Bedarf für Ihre Tests zu](licenses-assign.md).


## <a name="azure-portal-policy-configuration"></a>Richtlinienkonfiguration des Azure-Portals
[Erstellen Sie App-Schutzrichtlinien](app-protection-policies.md) über das [Intune-Blatt des Azure-Portals](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview), und weisen Sie sie zu. Ihre [App-Konfigurationsrichtlinie](app-configuration-policies-overview.md) kann ebenfalls über das Intune-Blatt erstellt und zugewiesen werden.

> [!NOTE]
> Wenn Ihre App nicht im Azure-Portal aufgeführt wird, können Sie eine Richtlinie auf die App anwenden, indem Sie auf **Weitere Apps** klicken und den Paketnamen in das Textfeld eingeben.

> [!IMPORTANT]
> Damit eine App-Konfigurationsrichtlinie angewendet wird, muss eine [Intune-App-Schutzrichtlinie](app-protection-policy.md) auf den zu registrierenden Benutzer angewendet werden.

## <a name="test-cases"></a>Testfälle

In den folgenden Testfällen werden Konfigurations- und Bestätigungsschritte veranschaulicht. Mit dieser Anleitung können Sie Probleme mit von Intune verwalteten Android-Apps beheben.

### <a name="required-pin-and-corporate-credentials"></a>Erforderliche PIN und Unternehmensanmeldeinformationen

Sie können eine PIN für den Zugriff auf Unternehmensressourcen erfordern. Außerdem können Sie Unternehmensauthentifizierung erzwingen, bevor Benutzer verwaltete Apps verwenden können. Verwenden Sie die folgenden Schritte, um diese Anforderungen festzulegen:

1. Legen Sie die Optionen **PIN für Zugriff anfordern** und **Unternehmensanmeldeinformationen für Zugriff erforderlich** auf **Ja** fest. Weitere Informationen finden Sie unter [Einstellungen für App-Schutzrichtlinien für Android in Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Überprüfen Sie die folgenden Bedingungen:
    - Beim App-Start sollte eine Eingabeaufforderung für die Eingabe/Einrichtung einer PIN und bzw. oder eines Produktionsbenutzers angezeigt werden, der bei der Registrierung im Unternehmensportal verwendet wurde.
    - Wenn keine gültige Anmeldeaufforderung angezeigt wird, kann dies an einem fehlerhaft konfigurierten Android-Manifest und insbesondere an den Werten für die ADAL-Integration („SkipBroker“, „ClientID“ und „Authority“) liegen.
    - Fehler beim Anzeigen beliebiger Eingabeaufforderungen können von einem fehlerhaft integrierten `MAMActivity`-Wert verursacht werden. Weitere Informationen zu `MAMActivity` finden Sie im [Entwicklerhandbuch zum Microsoft Intune App SDK für Android](app-sdk-android.md).

> [!NOTE] 
> Wenn der obige Test nicht funktioniert, werden auch die folgenden Tests fehlschlagen. Überprüfen Sie das [SDK](app-sdk-android.md##sdk-integration) und die [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)-Integration.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Einschränken der Übertragung von Daten von und zu anderen Apps
Sie können die Datenübertragung zwischen Unternehmensanwendungen wie folgt steuern:

1. Legen Sie **Zulassen, dass die App Daten an andere Apps überträgt** auf **Richtlinienverwaltete Apps** fest.
2. Legen Sie die Option **Zulassen, dass die App Daten von anderen Apps empfängt** auf **Alle Apps** fest. Die Verwendung von Absichten und Inhaltsanbietern wird von diesen Richtlinien beeinträchtigt.
3. Überprüfen Sie die folgenden Bedingungen:
    - Das Öffnen Ihrer App-Funktionen über eine nicht verwaltete App funktioniert.
    - Das Freigeben von Inhalten zwischen verwalteten Apps ist zulässig.
    - Die Freigabe über verwaltete Apps an nicht verwaltete Apps (z. B. Chrome) wird blockiert.

### <a name="restrict-cut-copy-and-paste"></a>Einschränken von Ausschneiden, Kopieren und Einfügen
Sie können die Zwischenablage wie folgt auf verwaltete Apps einschränken:

1. Legen Sie für **Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken** die Option **Richtlinienverwaltete Apps mit Einfügen** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das Kopieren von Text aus Ihrer App in eine nicht verwaltete App (z. B. Nachrichten) wird blockiert.

### <a name="prevent-save-as"></a>Verhindern von **Speichern unter**
Sie können die Funktionalität **Speichern unter** wie folgt steuern:

1. Wenn Ihre App [integrierte Steuerung für „Speichern unter“](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted) erfordert, legen Sie **„Speichern unter“ verhindern** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das Speichern ist auf entsprechende verwaltete Speicherorte eingeschränkt.

### <a name="file-encryption"></a>Dateiverschlüsselung
Sie können Daten auf dem Gerät wie folgt verschlüsseln:

1. Legen Sie **App-Daten verschlüsseln** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das normale Verhalten der Anwendung ist nicht betroffen.

### <a name="prevent-android-backups"></a>Verhindern von Android-Sicherungen
Sie können die App-Sicherung wie folgt steuern:

1. Wenn Sie [integrierte Sicherungseinschränkungen](app-sdk-android.md#protecting-backup-data) festgelegt haben, legen Sie **Android-Datensicherungen verhindern** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Sicherungen sind eingeschränkt.

### <a name="unenrollment"></a>Aufheben der Registrierung
Sie können für verwaltete Apps eine Remotezurücksetzung durchführen, um Unternehmens-E-Mails und -dokumente zu entfernen. Außerdem werden persönliche Daten entschlüsselt, wenn die Registrierung wie folgt aufgehoben wird:

1. [Veranlassen Sie eine Zurücksetzung](apps-selective-wipe.md) über das Azure-Portal.
2. Wenn Ihre App für keine Zurücksetzungshandler registriert ist, überprüfen Sie die folgenden Bedingungen:
    - Eine vollständige Zurücksetzung wird durchgeführt.
3. Wenn Ihre App für `WIPE_USER_DATA` oder `WIPE_USER_AUXILARY_DATA` registriert ist, überprüfen Sie die folgenden Bedingungen:
    - Der verwaltete Inhalt wird aus der App entfernt. Weitere Informationen finden Sie im [Entwicklerhandbuch zum Intune App SDK für Android im Abschnitt „Selektives Zurücksetzen“](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Mehrere Identitäten
Die Integration von [Unterstützung mehrerer Identitäten](app-sdk-android.md#multi-identity-optional) ist eine Änderung mit hohem Risiko, die gründlich getestet werden muss. Die am häufigsten auftretenden Fehler werden durch falsche Einstellung der Identität (Kontext vs. Bedrohungsstufe) und durch die Nachverfolgung von Dateien (`MAMFileProtectionManager`) ausgelöst.

Zumindest die folgenden Szenarios für mehrere Identitäten sollten noch mal überprüft werden:

- Die Richtlinie für **Speichern unter** funktioniert für verwaltete Identitäten ordnungsgemäß.
- Die Einschränkungen für das Kopieren und Einfügen aus verwalteten Identitäten zu persönlichen werden ordnungsgemäß erzwungen.
- Nur Daten, die zur verwalteten Identität gehören, werden verschlüsselt. Persönliche Dateien werden nicht geändert.
- Das selektive Zurücksetzen während der Aufhebung der Registrierung entfernt nur die Daten der verwalteten Identität.
- Der Endbenutzer wird zum bedingten Start aufgefordert, wenn er zum ersten Mal von einem nicht verwalteten Konto zu einem verwalteten wechselt.

### <a name="app-configuration-optional"></a>App-Konfiguration (Optional)
Sie können das Verhalten von verwalteten Apps wie folgt konfigurieren:

1. Wenn Ihre App App-Konfigurationseinstellungen nutzt, sollten Sie testen, ob Ihre App alle Werte ordnungsgemäß verarbeitet, die Sie (als Administrator) festlegen können. [App-Konfigurationsrichtlinien](app-configuration-policies-overview.md) können mithilfe von Intune erstellt und zugewiesen werden.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune](lob-apps-android.md)
