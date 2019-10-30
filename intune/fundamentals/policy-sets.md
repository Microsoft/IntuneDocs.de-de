---
title: Richtliniensätze
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Richtliniensätze verwenden können, um Sammlungen von Verwaltungsobjekten in Microsoft Intune zu gruppieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585656"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Verwenden von Richtliniensätzen zur Gruppierung von Verwaltungsobjektsammlungen in Microsoft Intune

Mit Richtliniensätzen können Sie ein Bündel von Verweisen auf bereits vorhandene Verwaltungsentitäten erstellen, die als einzelne konzeptionelle Einheit identifiziert, ausgerichtet und überwacht werden müssen. Ein Richtliniensatz ist eine zustellbare Sammlung von Apps, Richtlinien und anderen Verwaltungsobjekten, die Sie erstellt haben. Durch das Erstellen eines Richtliniensatzes können Sie viele verschiedene Objekte gleichzeitig auswählen und sie von einem zentralen Ort aus zuweisen. Wenn es in Ihrem Unternehmen zu Änderungen kommt, können Sie Richtliniensätze erneut aufrufen und zugehörige Objekte und Zuweisungen hinzufügen oder entfernen. Sie können einen Richtliniensatz verwenden, um vorhandene Objekte (z. B. Apps, Richtlinien und VPNs) in ein einzelnes Paket zuzuordnen und zuzuweisen. 

> [!IMPORTANT]
> Eine Liste bekannter Probleme im Zusammenhang mit Richtliniensätzen finden Sie unter [Bekannte Probleme bei Richtliniensätzen](~/fundamentals/policy-sets.md#policy-sets-known-issues).

Richtliniensätze ersetzen vorhandene Konzepte oder Objekte nicht. Sie können weiterhin einzelne Objekte zuweisen, und Sie können auch als Teil eines Richtliniensatzes auf einzelne Objekte verweisen. Aus diesem Grund werden alle Änderungen an den einzelnen Objekten in der Richtlinie berücksichtigt. 

Sie können Richtliniensätze für Folgendes verwenden:

- Gruppieren von Objekten, die gemeinsam zugewiesen werden müssen
- Zuweisen der Mindestanforderungen an die Konfiguration der Organisation auf allen verwalteten Geräten
- Zuweisen häufig verwendeter oder relevanter Apps an alle Benutzer

Sie können die folgenden Verwaltungsobjekte in einen Richtliniensatz einschließen:
- Apps
- App-Konfigurationsrichtlinien
- App-Schutzrichtlinien
- Gerätekonfigurierungsprofile
- Gerätekompatibilitätsrichtlinien
- Gerätetypbeschränkungen
- Windows Autopilot Deployment-Profile
- Seite zum Registrierungsstatus

Wenn Sie einen Richtliniensatz erstellen, erstellen Sie eine einzelne Zuweisungseinheit und verwalten Zuordnungen zwischen verschiedenen Objekten. Ein Richtliniensatz ist ein Verweis auf externe Objekte. Alle Änderungen in den enthaltenen Objekten wirken sich auch auf den Richtliniensatz aus. Nachdem Sie einen Richtliniensatz erstellt haben, können Sie dessen Objekte und Zuweisungen wiederholt anzeigen und bearbeiten. 

> [!NOTE]
> Richtliniensätze unterstützen Windows-, Android-, macOS- und iOS-Einstellungen und können plattformübergreifend zugewiesen werden.

## <a name="how-to-create-a-policy-set"></a>Erstellen einer Richtlinie

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie auf dem **Intune**-Blatt **Richtliniensätze** > **Richtliniensätze** > **Erstellen** aus.
3. Fügen Sie auf der Seite **Basics** (Grundeinstellungen) die folgenden Werte hinzu:
    - **Name des Richtliniensatzes**: Geben Sie einen Namen für diesen Richtliniensatz an.
    - **Beschreibung**: Geben Sie optional eine Beschreibung des Richtliniensatzes an.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Klicken Sie auf **Weiter: App-Verwaltung**.<br>
   Auf der Seite **Anwendungsverwaltung** können Sie optional [Apps](~/apps/apps-add.md), [App-Konfigurationsrichtlinien](~/apps/app-configuration-policies-overview.md) und [App-Schutzrichtlinien](~/apps/app-protection-policy.md) zu Ihrem Richtliniensatz hinzufügen. Weitere Informationen zur App-Verwaltung finden Sie unter [Was ist die Microsoft Intune App-Verwaltung?](~/apps/app-management.md). 
5. Klicken Sie auf **Weiter: Geräteverwaltung**.<br>
   Auf der Seite **Geräteverwaltung** können Sie Ihrem Richtliniensatz Geräteverwaltungsobjekte hinzufügen, z. B. [Gerätekonfigurierungsprofile](~/configuration/device-profiles.md) und [Gerätekonformitätsrichtlinien](~/protect/device-compliance-get-started.md). Stellen Sie sicher, dass Sie alle zugeordneten Objekte einschließen, beispielsweise andere Richtlinien, Zertifikate und Sicherheitsbaselineprofile.
6. Klicken Sie auf **Weiter: Geräteregistrierung**.<br>
   Auf der Seite **Geräteregistrierung** können Sie Ihrem Richtliniensatz Geräteregistrierungsobjekte hinzufügen, z. B. [Gerätetypbeschränkungen](~/enrollment/enrollment-restrictions-set.md), [Windows Autopilot Deployment-Profile](~/enrollment/enrollment-autopilot.md) und [Profile für Seite zum Registrierungsstatus](~/enrollment/windows-enrollment-status.md).
7. Klicken Sie auf **Weiter: Zuweisungen**.<br>
   Auf der Seite **Zuweisungen** können Sie den Richtliniensatz Benutzern und Geräten zuweisen. Beachten Sie: Sie können ein Richtliniensatz einem Gerät unabhängig davon zuweisen, ob das Gerät von Intune verwaltet wird.
8. Klicken Sie auf **Weiter: Überprüfen + erstellen**, um die für das Profil eingegebenen Werte zu überprüfen.
9. Klicken Sie abschließend auf **Erstellen**, um den Richtliniensatz in Intune zu erstellen. 

## <a name="policy-sets-known-issues"></a>Bekannte Probleme bei Richtliniensätzen

Für Richtliniensätze, die neu in 1910 sind, liegen folgende bekannte Probleme vor.

- Wenn beim Erstellen eines Richtliniensatzes ein bereichsbezogener Administrator versucht, einen Richtliniensatz zu erstellen, ohne dass Bereichsmarkierungen ausgewählt werden, schlägt die Validierung beim Aufrufen der Seite **Überprüfen + erstellen** fehl, und in der Statusleiste wird ein Fehler angezeigt. Der Administrator muss auf eine andere Seite wechseln und dann zur Seite **Review + Create** zurückkehren. Dadurch wird die Option **Erstellen** aktiviert.  
 
- Die folgenden App-Typen werden derzeit von Richtliniensätzen unterstützt:
    - iOS Store-App
    - Branchenspezifische iOS-App
    - Verwaltete branchenspezifische iOS-App
    - Android Store-App
    - Branchenspezifische Android-App
    - Verwaltete branchenspezifische Android-App
    - Office 365 ProPlus-Suite (Windows 10)
    - Weblink
    - Integrierte iOS-App
    - Integrierte Android-App

- Das Festlegen einer Zuweisung für Richtliniensätze von **Alle Benutzer** auf **Autopilot-Profil** wird nicht unterstützt.

- Für Richtliniensätze gelten folgende Registrierungsbeschränkungen und Probleme bei der Seite zum Registrierungsstatus (ESP):
    - Einschränkungen und ESP unterstützen keine virtuellen Gruppenzuweisungen.
    - Einschränkungen und ESP unterstützen nicht grundsätzlich Ausschlussgruppenzuweisungen. 
    - Einschränkungen und ESP verwenden prioritätsbasierte Konfliktlösung. Einschränkungen und ESP werden möglicherweise nicht auf die gleichen Benutzer angewendet wie die übrigen Nutzlasten eines Richtliniensatzes, wenn die Einschränkungen und ESP auch von Einschränkungen mit höherer Priorität und ESP betroffen sind.
    - Die Standardeinschränkungen und ESP können nicht zu einem Richtliniensatz hinzugefügt werden.

- Zu den MAM-Richtlinientypen, die Richtliniensätze unterstützen, zählen die folgenden: 
    - MAM: verwalteter App-Schutz für WIP (Windows) mit MDM 
    - MAM: verwalteter App-Schutz für iOS
    - MAM: verwalteter App-Schutz für Android
    - MAM: verwaltete App-Konfiguration für iOS
    - MAM: verwaltete App-Konfiguration für Android

- Zu den MAM-Richtlinientypen, die keine Richtliniensätze unterstützen, zählen die folgenden: 
    - MAM: verwalteter App-Schutz für WIP (Windows)

- MAM verarbeitet Zuweisungen von Richtlinien als direkte Zuweisungen für die folgenden Richtlinientypen:
    - MAM: verwalteter App-Schutz für iOS
    - MAM: verwalteter App-Schutz für Android
    - MAM: verwaltete App-Konfiguration für iOS
    - MAM: verwaltete App-Konfiguration für Android

    Wenn einem Richtliniensatz, der für eine Gruppe bereitgestellt wird, eine Richtlinie hinzugefügt wird, wird die Gruppe in der Arbeitsauslastung als direkt zugewiesen angezeigt und nicht als „über den Richtliniensatz zugewiesen“. Folglich verarbeitet MAM keine Löschungen von Gruppenzuweisungen aus Richtliniensätzen.

- MAM unterstützt keine Bereitstellung in den virtuellen Gruppen **Alle Benutzer** und **Alle Geräte** für beliebige Richtlinientypen.

## <a name="next-steps"></a>Nächste Schritte

- [Registrieren von Geräten bei Microsoft Intune](~/enrollment/index.yml)