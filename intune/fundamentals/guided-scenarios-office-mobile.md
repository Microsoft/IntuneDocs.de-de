---
title: 'Geführtes Szenario: Sichere mobile Microsoft Office-Apps'
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über das geführte Szenario, um sichere mobile Microsoft Office-Apps über das Microsoft 365-Geräteverwaltungsportal bereitzustellen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3399cf006543c0a3554c4c6ec812554462d74231
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691822"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Geführtes Szenario: Sichere mobile Microsoft Office-Apps 

Wenn Sie dieses geführte Szenario im Geräteverwaltungsportal befolgen, können Sie den Intune-App-Standardschutz auf iOS- und Android-Geräten aktivieren.

Der App-Schutz, den Sie aktivieren, erzwingt die folgenden Aktionen: 
- Verschlüsselung von Arbeitsdateien.
- Erfordert eine PIN für den Zugriff auf Arbeitsdateien.
- Die PIN muss nach fünf fehlgeschlagenen Versuchen zurückgesetzt werden.
- Blockieren der Sicherung von Arbeitsdateien in iTunes, iCloud oder Android-Sicherungsdiensten.  
- Arbeitsdateien dürfen nur in OneDrive oder SharePoint gespeichert werden.
- Verhindern, dass geschützte Apps Arbeitsdateien auf Geräten mit Jailbreak oder entfernten Nutzungsbeschränkungen laden.
- Blockieren des Zugriffs auf Arbeitsdateien, wenn das Gerät 720 Minuten lang offline ist.
- Entfernung von Arbeitsdateien, wenn das Gerät 90 Tage lang offline ist. 

## <a name="background"></a>Hintergrund

Mobile Microsoft Office-Apps sowie Microsoft Edge für Mobilgeräte unterstützen die Registrierung von zwei Identitäten. Die Registrierung von zwei Identitäten ermöglicht den Apps, Arbeitsdateien getrennt von persönlichen Dateien zu verwalten. 

![Bild der Unternehmensdaten und der persönlichen Daten](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

Die [Übersicht über App-Schutzrichtlinien](~/apps/app-protection-policy.md) unterstützt Sie beim Schutz Ihrer Arbeitsdateien auf Geräten, die bei Intune registriert sind. App-Schutzrichtlinien können Sie auch auf mitarbeitereigenen Geräten verwenden, die nicht für die Verwaltung in Intune registriert sind. Auch wenn Ihr Unternehmen das Gerät nicht verwaltet, müssen Sie in diesem Fall dennoch sicherstellen, dass Arbeitsdateien und -ressourcen geschützt sind.

Sie können die App-Schutzrichtlinien verwenden, um zu verhindern, dass Benutzer Arbeitsdateien an ungeschützten Speicherorten speichern. Außerdem können Sie das Verschieben von Daten in andere Apps einschränken, die nicht durch App-Schutzrichtlinien geschützt sind. Einstellungen für App-Schutzrichtlinien:
- Richtlinien zur Datenverschiebung wie **Kopien von Organisationsdaten speichern** und **Ausschneiden, Kopieren und Einfügen einschränken**.
- Zugriffsrichtlinieneinstellungen, die eine einfache PIN für den Zugriff erfordern und verhindern, dass verwaltete Apps auf Geräten mit Jailbreak oder Rootzugriff ausgeführt werden

Mit App-basiertem bedingten Zugriff und der Verwaltung von Client-Apps wird eine Sicherheitsschicht hinzugefügt, indem sichergestellt wird, dass nur Client-Apps, die Intune-App-Schutzrichtlinien unterstützen, auf Exchange Online und andere Office 365-Dienste zugreifen können.

Wenn Sie nur für die Microsoft Outlook-App den Zugriff auf Exchange Online zulassen, können Sie die integrierten E-Mail-Apps von iOS und Android blockieren. Darüber hinaus können Sie für Apps, auf die keine Intune-App-Schutzrichtlinien angewendet wurden, den Zugriff auf SharePoint Online blockieren.

In diesem Beispiel hat der Administrator App-Schutzrichtlinien auf die Outlook-App angewendet. Zudem gilt eine Regel für bedingten Zugriff, mit der die Outlook-App einer genehmigten Liste von Apps hinzugefügt wird, die beim Zugriff auf Unternehmens-E-Mails verwendet werden kann.

![Prozessflussdiagramm des bedingten Zugriffs in der Outlook-App](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen die folgenden Intune-Administrationsberechtigungen:

   - Verwaltete Apps: Lesen, Erstellen, Löschen und Zuweisen von Berechtigungen
   - Richtliniensätze: Lesen, Erstellen und Zuweisen von Berechtigungen
   - Organisationsberechtigungen: Lesen

## <a name="step-1---introduction"></a>Schritt 1: Einführung

Wenn Sie das geführte Szenario **Intune-App-Schutz** befolgen, verhindern Sie, dass Daten außerhalb Ihres Unternehmens geteilt oder weitergegeben werden. 

Zugewiesene iOS- und Android-Benutzer müssen bei jedem Öffnen einer Office-App eine PIN eingeben. Nach 5 fehlgeschlagenen Versuchen die PIN einzugeben, müssen die Benutzer ihre PIN zurücksetzen. Wenn Sie bereits eine Geräte-PIN anfordern, werden die Benutzer nicht beeinträchtigt.

### <a name="what-you-will-need-to-continue"></a>Voraussetzungen zum Fortfahren

Sie werden nach den Apps gefragt, die Ihre Benutzer benötigen, und was Sie für den Zugriff darauf benötigen. Stellen Sie sicher, dass Sie die folgenden Informationen zur Hand haben:
- Liste der Office-Apps, die für die Verwendung in Unternehmen zugelassen sind.
- Alle PIN-Anforderungen für den Start von genehmigten Apps auf nicht verwalteten Geräten.

## <a name="step-2---basics"></a>Schritt 2: Grundlagen

In diesem Schritt müssen Sie ein **Präfix** und eine **Beschreibung** für Ihre neue App-Schutzrichtlinie eingeben. Wenn Sie das **Präfix** hinzufügen, werden die Details zu den Ressourcen, die das geführte Szenario erstellt, aktualisiert. Diese Details erleichtern das spätere Auffinden Ihrer Richtlinien, wenn Sie die Zuweisungen und Konfigurationen ändern müssen. 

> [!TIP]
> Notieren Sie sich die zu erstellenden Ressourcen, damit Sie später auf sie zugreifen können.

## <a name="step-3---apps"></a>Schritt 3: Apps

Dieses Szenario wählt zuvor die folgenden mobilen Apps zum Schutz auf iOS- und Android-Geräten aus, um Ihnen den Einstieg zu erleichtern:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Dieses geführte Szenario wird diese Anwendungen auch so konfigurieren, dass sie Weblinks in Microsoft Edge öffnen, um zu gewährleisten, dass Arbeitsbereiche in einem geschützten Browser geöffnet werden.

Ändern Sie die Liste der Apps, die durch Richtlinien verwaltet werden und die Sie schützen möchten. Fügen Sie dieser Liste Apps hinzu, oder entfernen Sie diese. 

Wenn Sie die Apps ausgewählt haben, klicken Sie auf **Weiter**.

## <a name="step-4---configuration"></a>Schritt 4: Konfiguration

In diesem Schritt müssen Sie die Anforderungen für den Zugriff und die gemeinsame Nutzung der Unternehmensdateien und E-Mails in diesen Apps konfigurieren. Standardmäßig können Benutzer Daten in die OneDrive- und SharePoint-Konten Ihres Unternehmens speichern.

| Einstellung | Beschreibung | Standardwert |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| PIN-Typ | Numerische PINs bestehen nur aus Ziffern. Passcodes bestehen aus alphanumerischen Zeichen und Sonderzeichen.  Auf iOS/iPadOS benötigt die App zur Konfiguration des Typs "Kennung" die Intune SDK Version 7.1.12 oder höher. Für einen numerischen Typ besteht keine Einschränkung hinsichtlich der Intune SDK-Version. | Numerisch |
| Auswählen der PIN-Mindestlänge | Geben Sie die Mindestanzahl von Ziffern in einer PIN-Sequenz an. | 6 |
| Erneutes Prüfen der Zugriffsanforderungen nach (Minuten der Inaktivität) | Wenn die durch Richtlinien verwaltete App länger als die angegebene Anzahl von Minuten der Inaktivität inaktiv ist, fordert die App dazu auf, die Zugriffsanforderungen (z. B. PIN, Einstellungen für den bedingten Start) nach dem Start der App erneut zu überprüfen. | 30 |
| Drucken der Organisationsdaten | Wenn dies blockiert wird, kann die App keine geschützten Daten drucken. | Blockieren |
| Öffnen von mit Richtlinien verwalteten App-Links in nicht verwalteten Browsern | Wenn dies blockiert wird, müssen mit Richtlinien verwaltete App-Links in einem verwalteten Browser geöffnet werden. | Blockieren |
| Kopieren von Daten in nicht verwaltete Apps | Wenn dies blockiert ist, bleiben verwaltete Daten in verwalteten Apps erhalten. | Zulassen |

## <a name="step-5---assignments"></a>Schritt 5: Zuweisungen

In diesem Schritt können Sie die Benutzergruppen auswählen, die Sie aufnehmen möchten, um sicherzustellen, dass sie Zugriff auf Ihre Unternehmensdaten haben. Der App-Schutz wird Benutzern und nicht Geräten zugewiesen, sodass Ihre Unternehmensdaten unabhängig vom verwendeten Gerät und dessen Registrierungsstatus sicher sind.

Benutzer ohne App-Schutzrichtlinien und zugewiesene Einstellungen für bedingten Zugriff können Daten aus ihrem Unternehmensprofil in persönlichen Apps und nicht verändertem lokalem Speicher auf ihren mobilen Geräten speichern. Die Benutzer könnten sich auch mit persönlichen Apps mit Unternehmensdatendiensten wie Microsoft Exchange verbinden.

## <a name="step-6---review--create"></a>Schritt 6: Überprüfen und erstellen

Im letzten Schritt können Sie eine Zusammenfassung der von Ihnen konfigurierten Einstellungen einsehen. Nachdem Sie Ihre Auswahl überprüft haben, klicken Sie auf **Erstellen**, um das geführte Szenario abzuschließen. Sobald das geführte Szenario abgeschlossen ist, wird eine Tabelle der Ressourcen angezeigt. Sie können diese Ressourcen später bearbeiten, aber sobald Sie die Ansicht der Zusammenfassung verlassen, wird die Tabelle nicht gespeichert.

> [!IMPORTANT]
> Sobald das geführte Szenario abgeschlossen ist, wird eine Zusammenfassung angezeigt. Sie können die in der Zusammenfassung aufgeführten Ressourcen später ändern, jedoch wird die Tabelle mit diesen Ressourcen nicht gespeichert.
## <a name="next-steps"></a>Nächste Schritte

- Verbessern Sie die Sicherheit von Arbeitsdateien, indem Sie Benutzern eine App-basierte Richtlinie für den bedingten Zugriff zuweisen, um Cloud-Dienste vor dem Senden von Arbeitsdateien an ungeschützte Apps zu schützen. Weitere Informationen finden Sie unter [Einrichten App-basierter Richtlinien für den bedingten Zugriff mit Intune](~/protect/app-based-conditional-access-intune-create.md).

