---
title: Aktivieren von Win32-Apps auf Geräten im S Modus
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Win32-Apps auf Geräten im S Modus mithilfe von Microsoft Intune aktivieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2ab21321b171c8fe8f5f9dab3032507c0e740cf
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059757"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Aktivieren von Win32-Apps auf Geräten im S Modus

[Windows 10 im S Modus](https://docs.microsoft.com/windows/deployment/s-mode) ist ein gesperrtes Betriebssystem, das nur Store-Apps ausführt. Standardmäßig lassen Windows-Geräte im S Modus die Installation und Ausführung von Win32-Apps nicht zu. Diese Geräte enthalten eine einzelne *Windows 10 S-Basisrichtlinie*, die verhindert, dass das Gerät im S Modus Win32-Apps ausführen kann. Durch die Erstellung und Verwendung einer **zusätzlichen S Modus-Richtlinie** in Intune können Sie jedoch Win32-Apps auf verwalteten Windows 10-Geräten im S Mode installieren und ausführen. Mithilfe der [Microsoft Defender-Anwendungssteuerung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)-PowerShell-Tools können Sie eine oder mehrere zusätzliche Richtlinien für Windows im S Modus erstellen. Sie müssen die zusätzlichen Richtlinien mit dem [Device Guard-Signaturdienst](https://go.microsoft.com/fwlink/?linkid=2095629) oder mit [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) signieren und dann die Richtlinien über Intune hochladen und verteilen. Alternativ können Sie die zusätzlichen Richtlinien mit einem Codesignaturzertifikat Ihrer Organisation signieren. Die bevorzugte Methode ist jedoch die Verwendung eines Device Guard-Signaturdiensts. In der Instanz, in der Sie das Codesignaturzertifikat Ihrer Organisation verwenden, muss das Stammzertifikat, mit dem das Codesignaturzertifikat verkettet ist, auf dem Gerät vorhanden sein.

Durch die Zuweisung der zusätzlichen S Modus-Richtlinie in Intune ermöglichen Sie es dem Gerät, eine Ausnahme in der vorhandenen Geräterichtlinie im S Modus festzulegen. Dies lässt den hochgeladenen zugehörigen signierten App-Katalog zu. Die Richtlinie legt eine Zulassungsliste von Apps (der App-Katalog) fest, die auf dem Gerät im S Modus verwendet werden können.

> [!NOTE]
> Win32-Apps auf Geräten im S Modus werden nur unter Windows 10 mit dem Update vom November 2019 (Build 18363) oder höheren Versionen unterstützt.

<!-- Add WDAC tooling diagram  -->

Die folgenden Schritte sind erforderlich, damit Win32-Apps auf einem Windows 10-Gerät im S Modus ausgeführt werden können:

1. Aktivieren Sie im Rahmen des Windows 10 S-Registrierungsprozesses Geräte im S Modus über Intune.
2. Erstellen Sie eine zusätzliche Richtlinie für die Zulassung von Win32-Apps:
   - Sie können die [Microsoft Defender-Anwendungssteuerung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)-Tools verwenden, um eine zusätzliche Richtlinie zu erstellen. Die Basisrichtlinien-ID in der Richtlinie muss mit der Basisrichtlinien-ID im S Modus (die auf dem Client hart codiert ist) übereinstimmen. Stellen Sie außerdem sicher, dass die Richtlinienversion höher als die vorherige Version ist.
   - Verwenden Sie den Device Guard-Signaturdienst, um Ihre zusätzliche Richtlinie zu signieren. Weitere Informationen finden Sie unter [Signieren von Codeintegritätsrichtlinien mit der Device Guard-Signatur](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Laden Sie die signierte zusätzliche Richtlinie in Intune hoch, indem Sie eine zusätzliche Windows 10 S Modus-Richtlinie erstellen (siehe unten).
3. Lassen Sie Win32-App-Kataloge über Intune zu:
   - Erstellen Sie Katalogdateien (eine für jede App), und signieren Sie sie mit dem Device Guard-Signaturdienst oder anderen Zertifikatinfrastrukturen.
   - Packen Sie den signierten Katalog mit dem [Microsoft Win32-Inhaltsvorbereitungstool](https://go.microsoft.com/fwlink/?linkid=2065730) in die *.intunewin*-Datei. Weiter Informationen finden Sie unter [Win32-App-Verwaltung – Vorbereiten des Inhalts der Win32-App für den Upload](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Intune wendet den signierten App-Katalog an, um die Win32-App auf dem Gerät im S Modus mithilfe der [Intune-Verwaltungserweiterung](~/apps/intune-management-extension.md) zu installieren.

> [!NOTE]
> Branchenspezifische `.appx` und `.appx`-Bundle in Windows 10 im S Modus werden über die Signierung des Microsoft Store für Unternehmen unterstützt.
>
> **Die zusätzliche S Modus-Richtlinie** für Apps muss über die Intune-Verwaltungserweiterung übermittelt werden.
>
> S Modus-Richtlinien werden auf Geräteebene erzwungen. Mehrere Zielrichtlinien werden auf dem Gerät zusammengeführt. Die zusammengeführte Richtlinie wird auf dem Gerät erzwungen.

Führen Sie die folgenden Schritte aus, um eine zusätzliche Windows 10 S Modus-Richtlinie zu erstellen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie im Bereich **Intune** die Option **Client-Apps** > **Zusätzliche S Modus-Richtlinien** > **Richtlinie erstellen** aus.
3. Bevor Sie die **Richtliniendatei** hinzufügen, müssen Sie sie erstellen und signieren. Weitere Informationen finden Sie in folgenden Quellen:
    - [Erstellen einer WDAC-Richtlinie mithilfe von PowerShell-Tools und Konvertieren in ein Binärformat](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Signieren mit dem Device Guard-Signaturdienst](https://go.microsoft.com/fwlink/?linkid=2095629) **(empfohlen)**

4. Fügen Sie auf der Seite **Basics** (Grundeinstellungen) die folgenden Werte hinzu:

    | Wert | Beschreibung |
    |--------------|------------------------------------------------|
    | Richtliniendatei | Die Datei, die die WDAC-Richtlinie enthält |
    | Name | Der Name dieser Richtlinie |
    | Beschreibung | [Optional] Die Beschreibung dieser Richtlinie |

5. Klicken Sie auf **Next: Bereichstags**.<br>
   Auf der Seite **Bereichstags** können Sie optional Bereichstags konfigurieren, um zu bestimmen, wer die App-Richtlinie in Intune sehen kann. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Use role-based access control and scope tags for distributed IT (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT)](~/fundamentals/scope-tags.md).

6. Klicken Sie auf **Weiter: Zuweisungen**.<br>
   Auf der Seite **Zuweisungen** können Sie die Richtlinie Benutzern und Geräten zuweisen. Beachten Sie: Sie können eine Richtlinie einem Gerät unabhängig davon zuweisen, ob das Gerät von Intune verwaltet wird.
7. Klicken Sie auf **Next: Überprüfen + erstellen**, um die für das Profil eingegebenen Werte zu überprüfen.
8. Klicken Sie abschließend auf **Erstellen**, um die zusätzliche S Modus-Richtlinie in Intune zu erstellen. 

Nach der Erstellung der Richtlinie wird diese der Liste der zusätzlichen S Modus-Richtlinien in Intune hinzugefügt. Sobald die Richtlinie zugewiesen ist, wird sie auf den Geräten bereitgestellt. Beachten Sie, dass Sie die App in derselben Sicherheitsgruppe wie die zusätzliche Richtlinie bereitstellen müssen. Sie können damit beginnen, die Apps auf diese Richtlinien anzuwenden und diesen zuzuweisen. Dadurch können Endbenutzer die Apps auf den Geräten im S Modus installieren und ausführen.

## <a name="removal-of-s-mode-policy"></a>Entfernen der S Modus-Richtlinie

Sie müssen eine leere Richtlinie zuweisen und bereitstellen, um die zusätzliche S Modus-Richtlinie zu überschreiben. Nur so können Sie derzeit die zusätzliche S Modus-Richtlinie vom Gerät entfernen.

## <a name="policy-reporting"></a>Berichterstellung für Richtlinien

Die zusätzliche S Modus-Richtlinie, die auf Geräteebene erzwungen wird, verfügt nur über Berichterstellungen auf Geräteebene. Die Berichterstellung auf Geräteebene ist für Erfolgs- und Fehlerbedingungen verfügbar. 

Berichtswerte, die in der Intune-Konsole für die Berichterstellung von S Modus-Richtlinien angezeigt werden:
- **Erfolg:** Die zusätzliche S Modus-Richtlinie ist aktiv.
- **Unbekannt**: Der Status der zusätzlichen S Modus-Richtlinie ist nicht bekannt.
- **TokenError**: Die zusätzliche S Modus-Richtlinie ist strukturell in Ordnung, aber es gibt einen Fehler bei der Autorisierung des Tokens.
- **NotAuthorizedByToken**: Das Token autorisiert die zusätzliche S Modus-Richtlinie nicht.
- **PolicyNotFound**: Die zusätzliche S Modus-Richtlinie wurde nicht gefunden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen finden Sie unter [Win32-Apps im S Modus](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- Weitere Informationen zum Hinzufügen von Apps zu Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).
- Weitere Informationen zu Win32-Apps finden Sie unter [Win32-App-Verwaltung in Intune](~/apps/apps-win32-app-management.md).
