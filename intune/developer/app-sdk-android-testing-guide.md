---
title: 'Microsoft Intune App SDK für Android: Testleitfaden'
description: Der Testleitfaden zum Microsoft Intune App SDK für Android unterstützt Sie beim Testen Ihrer mit Intune verwalteten Android-App.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9eada01f2b1e876d6d3b47140c671e3ff7eeab02
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503509"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Microsoft Intune App SDK für Android: Testleitfaden

Dieses Handbuch hilft Entwicklern dabei, ihre mit InTune verwalteten Android-Apps zu testen.  

## <a name="prerequisite-test-accounts"></a>Erforderliche Testkonten
Sie können neue Konten mit oder ohne vorab generierte Daten erstellen. Gehen Sie folgendermaßen vor, um ein neues Konto zu erstellen:
1. Rufen Sie die [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant)-Website auf. 
2. [Richten Sie Intune ein](../fundamentals/setup-steps.md), um die mobile Geräteverwaltung (MDM) zu aktivieren.
3. [Erstellen Sie Benutzer](../fundamentals/users-add.md).
4. [Erstellen Sie Gruppen](../fundamentals/groups-add.md).
5. [Weisen Sie Lizenzen je nach Bedarf für Ihre Tests zu](../fundamentals/licenses-assign.md).


## <a name="azure-portal-policy-configuration"></a>Richtlinienkonfiguration des Azure-Portals
[Erstellen Sie App-Schutzrichtlinien](../apps/app-protection-policies.md) über das [Intune-Blatt des Azure-Portals](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview), und weisen Sie sie zu. Sie können Ihre [App-Konfigurationsrichtlinie](../apps/app-configuration-policies-overview.md) auch auf dem Blatt InTune erstellen und zuweisen.

> [!NOTE]
> Wenn Ihre App nicht im Azure-Portal aufgeführt wird, können Sie eine Richtlinie auf die App anwenden, indem Sie auf **Weitere Apps** klicken und den Paketnamen in das Textfeld eingeben.

## <a name="test-cases"></a>Testfälle

In den folgenden Testfällen werden Konfigurations- und Bestätigungsschritte veranschaulicht. Mit dieser Anleitung können Sie Probleme mit von Intune verwalteten Android-Apps beheben.

### <a name="required-pin-and-corporate-credentials"></a>Erforderliche PIN und Unternehmensanmeldeinformationen

Sie können eine PIN für den Zugriff auf Unternehmensressourcen anfordern. Außerdem können Sie Unternehmensauthentifizierung erzwingen, bevor Benutzer verwaltete Apps verwenden können. Gehen Sie wie folgt vor:

1. Legen Sie die Optionen **PIN für Zugriff erforderlich** und **Unternehmensanmeldeinformationen für Zugriff erforderlich** auf **Ja** fest. Weitere Informationen finden Sie unter [Einstellungen für App-Schutzrichtlinien für Android in Microsoft Intune](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Überprüfen Sie die folgenden Bedingungen:
    - Beim App-Start sollte eine Eingabeaufforderung für die Angabe einer PIN oder eines Produktionsbenutzers angezeigt werden, der bei der Registrierung im Unternehmensportal verwendet wurde.
    - Eine gültige Anmeldeaufforderung kann aufgrund eines falsch konfigurierten Android-Manifests nicht angezeigt werden. Dies gilt insbesondere für die Werte für die Adal-Integration (Azure Active Directory Authentication Library) (skipbroker, ClientID und Authority).
    - Wenn keinerlei Eingabeaufforderung angezeigt wird, liegt dies möglicherweise an einem fehlerhaft integrierten `MAMActivity`-Wert. Weitere Informationen zu `MAMActivity` finden Sie im [Entwicklerhandbuch zum Microsoft Intune App SDK für Android](app-sdk-android.md).

> [!NOTE] 
> Wenn der vorherige Test nicht funktioniert, treten wahrscheinlich auch die folgenden Tests ein. Überprüfen Sie das [SDK](app-sdk-android.md##sdk-integration) und die [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)-Integration.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Einschränken der Übertragung von Daten von und zu anderen Apps
Sie können die Datenübertragung zwischen vom Unternehmen verwalteten Anwendungen wie folgt steuern:

1. Legen Sie **Zulassen, dass die App Daten an andere Apps überträgt** auf **Richtlinienverwaltete Apps** fest.
2. Legen Sie die Option **Zulassen, dass die App Daten von anderen Apps empfängt** auf **Alle Apps** fest. Diese Richtlinien wirken sich auf die Verwendung von Absichten und Inhaltsanbietern aus.
3. Überprüfen Sie die folgenden Bedingungen:
    - Das Öffnen Ihrer App-Funktionen über eine nicht verwaltete App funktioniert.
    - Das Freigeben von Inhalten zwischen verwalteten Apps ist zulässig.
    - Die Freigabe über verwaltete Apps an nicht verwaltete Apps (z. B. Chrome) wird blockiert.

### <a name="restrict-cut-copy-and-paste"></a>Einschränken von Ausschneiden, Kopieren und Einfügen
Sie können die Zwischenablage wie folgt auf verwaltete Apps einschränken:

1. Legen Sie für **Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken** die Option **Richtlinienverwaltete Apps mit Einfügen** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das Kopieren von Text aus Ihrer App in eine nicht verwaltete App (z. B. eine Nachrichten-App) wird blockiert.

### <a name="prevent-save"></a>Verhindern der Speicherung
Sie können die Funktionalität **Speichern unter** wie folgt steuern:

1. Wenn Ihre App [integrierte Steuerelemente für „Speichern unter“](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted) erfordert, legen Sie **„Speichern unter“ verhindern** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das Speichern ist auf entsprechende verwaltete Speicherorte eingeschränkt.

### <a name="file-encryption"></a>Dateiverschlüsselung
Sie können Daten auf dem Gerät wie folgt verschlüsseln:

1. Legen Sie **App-Daten verschlüsseln** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Das normale Anwendungsverhalten ist nicht betroffen.

### <a name="prevent-android-backups"></a>Android-Datensicherungen verhindern
Sie können die App-Sicherung wie folgt steuern:

1. Wenn Sie [integrierte Sicherungseinschränkungen](app-sdk-android.md#protecting-backup-data) festgelegt haben, legen Sie **Android-Sicherungen verhindern** auf **Ja** fest.
2. Überprüfen Sie die folgenden Bedingungen:
    - Sicherungen sind eingeschränkt.

### <a name="unenrollment"></a>Aufheben der Registrierung
Sie können verwaltete Apps remote zurücksetzen, um unternehmenseigene E-Mails und Dokumente zu entfernen. Persönliche Daten werden entschlüsselt, wenn die App nicht mehr verwaltet wird. Gehen Sie wie folgt vor:

1. [Veranlassen Sie eine Zurücksetzung](../apps/apps-selective-wipe.md) über das Azure-Portal.
2. Wenn Ihre App keine Zurücksetzungshandler registriert, überprüfen Sie die folgenden Bedingungen:
    - Eine vollständige Zurücksetzung wird durchgeführt.
3. Wenn Ihre App für `WIPE_USER_DATA` oder `WIPE_USER_AUXILARY_DATA` registriert ist, überprüfen Sie die folgenden Bedingungen:
    - Der verwaltete Inhalt wird aus der App entfernt. Weitere Informationen finden Sie im [Entwicklerhandbuch zum Intune App SDK für Android im Abschnitt „Selektives Zurücksetzen“](app-sdk-android.md#selective-wipe).

### <a name="multi-identity-support"></a>Unterstützung mehrerer Identitäten
Die Integration von [Unterstützung mehrerer Identitäten](app-sdk-android.md#multi-identity-optional) ist eine Änderung mit hohem Risiko, die gründlich getestet werden muss. Die häufigsten Probleme treten auf, weil die Identität (Kontext-oder Bedrohungsstufe) und die nach Verfolgungs Dateien (`MAMFileProtectionManager`) nicht ordnungsgemäß festgelegt wurden.

Bestätigen Sie minimal Folgendes:

- Die Richtlinie für **Speichern unter** funktioniert für verwaltete Identitäten ordnungsgemäß.
- Die Einschränkungen beim Kopieren und Einfügen von Inhalten aus verwalteten Identitäten in persönliche Konten werden ordnungsgemäß erzwungen.
- Nur Daten, die zur verwalteten Identität gehören, werden verschlüsselt. Persönliche Dateien werden nicht geändert.
- Das selektive Zurücksetzen während der Aufhebung der Registrierung entfernt nur die Daten der verwalteten Identität.
- Der Benutzer wird zum bedingten Start aufgefordert, wenn er zum ersten Mal von einem nicht verwalteten Konto zu einem verwalteten wechselt.

### <a name="app-configuration-optional"></a>App-Konfiguration (Optional)
Sie können das Verhalten von verwalteten Apps konfigurieren. Wenn Ihre App App-Konfigurationseinstellungen nutzt, sollten Sie testen, ob Ihre App alle Werte ordnungsgemäß verarbeitet, die Sie (als Administrator) festlegen können. Sie können [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-overview.md) in InTune erstellen und zuweisen.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune](../apps/lob-apps-android.md)
