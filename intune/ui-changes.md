---
title: Wo ist meine Intune-Funktion in Azure jetzt?
titleSuffix: Microsoft Intune
description: Hilft Ihnen bei der Suche nach Microsoft Intune-Features im Azure-Portal.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 207a3f950d6fca2d6fcbe024f24fbf05487f2151
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040389"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Wo ist meine Intune-Funktion in Azure jetzt?
Wir hatten die Chance, einige Aufgaben logischer zu organisieren, als wir Intune in das Azure-Portal umgezogen haben. Jedoch kommt jede Verbesserung mit der neuen Aufgabe, die neue Organisation kennenzulernen. Dieses Referenzhandbuch wurde für diejenigen von Ihnen erstellt, die mit Intune im klassischen Portal bestens vertraut sind und sich nun fragen, wie Aufgaben in Intune im Azure-Portal erledigt werden. Wenn dieser Artikel eine Funktion, die Sie suchen, nicht behandelt, hinterlassen Sie einen Kommentar am Ende des Artikels, damit wir ihn aktualisieren können.
## <a name="quick-reference-guide"></a>Handbuch mit Kurzübersicht

|Komponente |Pfad im klassischen Portal|Pfad in Intune im Azure-Portal|
|------------|---------------|---------------|
|Programm zur Geräteregistrierung (DEP) [nur iOS9]|Administrator > Verwaltung mobiler Geräte > iOS > Programm zur Geräteregistrierung|[Geräteregistrierung > Apple-Registrierung > Registrierungsprogrammtoken](#where-did-apple-dep-go) |
|Programm zur Geräteregistrierung (DEP) [nur iOS9]| Administrator > Verwaltung mobiler Geräte > iOS und Mac OS X > Programm zur Geräteregistrierung |[Geräteregistrierung > Apple-Registrierung > Seriennummern des Registrierungsprogramms](#where-did-apple-dep-go) |
|Registrierungsregeln |Administrator > Verwaltung mobiler Geräte > Registrierungsregeln|[Geräteregistrierung > Registrierungseinschränkungen](#where-did-enrollment-rules-go) |
|Gruppen nach iOS-Seriennummer |Gruppen > Alle Geräte > Vorabregistrierte Unternehmensgeräte > Nach iOS-Seriennummer|[Geräteregistrierung > Apple-Registrierung > Seriennummern des Registrierungsprogramms](#where-did-corporate-pre-enrolled-devices-go) |
|Gruppen nach iOS-Seriennummer |Gruppen > Alle Geräte > Vorabregistrierte Unternehmensgeräte > Nach iOS-Seriennummer| [Geräteregistrierung > Apple-Registrierung > AC-Seriennummern](#where-did-corporate-pre-enrolled-devices-go)|
|Gruppen nach IMEI (Alle Plattformen)| Gruppen > Alle Geräte > Vorabregistrierte Unternehmensgeräte > Nach IMEI (Alle Plattformen) | [Geräteregistrierung > Bezeichner von Unternehmensgeräten](#by-imei-all-platforms)|
| Profil für die Unternehmensgeräteregistrierung| Richtlinie > Unternehmensgeräteregistrierung | [Geräteregistrierung > Apple-Registrierung > Profile des Registrierungsprogramms](#where-did-corporate-pre-enrolled-devices-go) |
| Profil für die Unternehmensgeräteregistrierung | Richtlinie > Unternehmensgeräteregistrierung | [Geräteregistrierung > Apple-Registrierung > AC-Profile](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | Administrator > Verwaltung mobiler Geräte > Android for Work | Geräteregistrierung > Android-Registrierung |
| Geschäftsbedingungen | Richtlinien > Geschäftsbedingungen | Geräteregistrierung > Geschäftsbedingungen |
Unternehmensportaleinstellungen|Verwaltung > Unternehmensportal|**Verwalten** > Mobile Apps<br> **Einrichten** > Branding des Unternehmensportals


## <a name="where-do-i-manage-groups"></a>Wo verwalte ich Gruppen?
Intune im Azure-Portal verwendet [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) zum Verwalten von Gruppen.

## <a name="where-did-enrollment-rules-go"></a>Wo sind die Registrierungsregeln hin?
Im klassischen Portal konnten Sie Regeln festlegen, die die MDM-Registrierung mobiler und moderner Windows- und macOS-Geräte gesteuert haben.

![Abbildung der klassischen Registrierungsregeln für mobile Geräte](./media/01-classic-rules.png)

Diese Regeln galten ausnahmslos für alle Benutzer in Ihrem Intune-Konto. Im Azure-Portal werden diese Regeln nun in zwei unterschiedlichen Typen von Richtlinien dargestellt: Gerätetypbeschränkungen und Einschränkungen zum Gerätelimit.

![Abbildung der Registrierungseinschränkungen für mobile Azure-Geräte](./media/02-azure-enroll-restrictions.png)

Die Standardeinschränkung zum Gerätelimit entspricht dem Grenzwert für die Geräteregistrierung im klassischen Portal.

![Abbildung der Einschränkungen zum Gerätelimit für Azure](./media/03-azure-device-limit.png)

Die Standardeinschränkung des Gerätetyps entspricht den Plattformeinschränkungen im klassischen Portal.

![Abbildung von Gerätetypeinschränkungen für Azure](./media/04-azure-platform-restrictions.png)

Die Möglichkeit, private Geräte zuzulassen oder zu blockieren, wird nun unter den Plattformkonfigurationen der Gerätetypeinschränkungen verwaltet.

![Abbildung der Blockiereinstellungen von persönlichen Azure-Geräten](./media/05-azure-personal-block.png)

Neue Funktionen zur Einschränkung werden nur zum Azure-Portal hinzugefügt.

## <a name="where-did-my-conditional-access-policies-go"></a>Wo finde ich meine Richtlinien für den bedingten Zugriff?
Nach der Migration Ihres Mandanten zum Azure-Portal werden die Richtlinien für den bedingten Zugriff weiterhin angewendet. Jedoch können Sie sie nicht über Intune im Azure-Portal anzeigen oder bearbeiten.

Wenn Sie die Richtlinien für den bedingten Zugriff über das Azure-Portal anzeigen oder bearbeiten möchten, müssen Sie die alten Richtlinien aus dem klassischen Portal entfernen. Anschließend müssen Sie sie im Azure-Portal neu erstellen. Weitere Informationen zum Migrieren von Richtlinien für den bedingten Zugriff finden Sie unter [Migrieren von klassischen Richtlinien in das Azure-Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration). 

## <a name="where-did-my-compliance-policies-go"></a>Wo finde ich meine Konformitätsrichtlinien?
Nach der Migration Ihres Mandanten zum Azure-Portal werden die Konformitätsrichtlinien weiterhin angewendet. Jedoch können Sie sie nicht über Intune im Azure-Portal anzeigen oder bearbeiten.

Wenn Sie die Konformitätsrichtlinien über das Azure-Portal anzeigen oder bearbeiten möchten, müssen Sie die alten Richtlinien aus dem klassischen Portal entfernen. Anschließend müssen Sie sie im Azure-Portal neu erstellen. Weitere Informationen über Gerätekonformitätsrichtlinien finden Sie unter [Erste Schritte bei der Gerätekonformität in Intune](https://docs.microsoft.com/intune/known-issues#compliance). 

## <a name="where-did-apple-dep-go"></a>Wo ist Apple-DEP jetzt?
Im klassischen Portal konnten Sie Intune so einrichten, dass es im Programm zur Geräteregistrierung von Apple integriert wurde, und Sie konnten die Synchronisierung mit dem Apple-Dienst manuell anfordern:

![Bild des klassischen DEP-Token](./media/06-classic-dep-token.png)

Im Azure-Portal richten das Geräteregistrierungsprogramm von Apple mit den gleichen Schritten wie in der klassischen Intune-Konsole ein:

![Abbildung des Azure-DEP-Token](./media/07-azure-dep-token.png)

Jedoch wurde die Option **Synchronisierung** im klassischen Portal zum Workflow der Verwaltung von Seriennummern verschoben, da die Ergebnisse der manuellen Synchronisierung dort angezeigt werden:

![Abbildung der Azure-DEP-Synchronisation](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Wo sind die vorabregistrierten Unternehmensgeräte jetzt?
### <a name="by-ios-serial-number"></a>Nach iOS-Seriennummer
Im klassischen Portal können Sie iOS-Geräte über das Programm zur Geräteregistrierung von Apple (Device Enrollment Program, DEP) und das Apple Configurator-Tool registrieren. Beide Methoden bieten Gerätevorabregistrierung durch Seriennummern und umfassen die Zuweisung spezieller Geräteregistrierungsprofile. Vor der Registrierung kann die Registrierungsprofilzuweisung über die Gerätegruppe **Corporate Pre-enrolled Device by iOS Serial Number** (Vorabregistriertes Unternehmensgerät nach iOS-Seriennummer) verwaltet werden:

![Abbildung der klassischen Apple-Seriennummern](./media/09-classic-apple-serials.png)

Hier werden Seriennummern für die Apple-DEP- und die Configurator-Registrierung in einer einzigen Liste aufgeführt: Um Profilzuweisungskonflikte zu reduzieren (DEP-Profile zu AC-Seriennummern und andersherum), haben wir die Seriennummern in zwei Listen im Azure-Portal aufgeteilt:

**DEP-Seriennummern**
![Abbildung von Azure DEP-Seriennummern](./media/10-azure-dep-serials.png)

**Apple Configurator-Seriennummern**
![Abbildung der Azure Apple Configurator-Seriennummern](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Durch IMEI (Alle Plattformen)

Im klassischen Portal können Sie vorab IMEI-Nummern von Geräten auflisten, um sie als unternehmenseigen zu markieren, wenn sie in Intune registriert werden:

![Abbildung der klassischen Liste von IMEI-Nummern](./media/12-classic-corp-imei.png)

Im Azure-Portal müssen Sie die gleichen IMEI-Nummern mit einer CSV-Datei, die durch Trennzeichen getrennte Werte enthält, in die Liste der IDs unternehmenseigener Geräte hochladen. Das neue Portal unterstützt keine manuelle Eingabe der IMEI-Nummern:

![Abbildung der Azure-Liste der IMEI-Nummern](./media/13-azure-corp-imei.png)

Intune im Azure-Portal wird zukünftig andere Typen von Bezeichnern neben IMEI unterstützen, lässt derzeit jedoch nur IMEI-Nummern für die Vorabauflistung zu.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Wo befinden sich die Profile für die Unternehmensgeräteregistrierung jetzt?
Zum Registrieren von iOS-Geräten über das Apple-Geräteregistrierungsprogramm oder mit dem Apple Configurator-Tool müssen Sie ein Tool zur Unternehmensgeräteregistrierung bereitstellen, dem das Gerät zugewiesen wird. Im klassischen Portal fanden Erstellung und Verwaltung dieser Profile in einer einzigen Liste statt:

![Abbildung der klassischen Geräteregistrierungsprofile](./media/14-classic-corp-profiles.png)

Dieses Liste zeigt die Profile, die für den Gebrauch mit dem Apple-Geräteregistrierungsprogramm (**DEP On** (DEP aktiviert)) und Profile, die nur für den Gebrauch mit dem Apple Configurator Tool zulässig sind (**DEP Off** (DEP deaktiviert)).

Um Verwechslungen zwischen den beiden Profiltypen und potenzielle nicht übereinstimmende Zuweisungen zu minimieren (DEP-Profil zu Configurator-Geräte und andersherum), haben wir die Erstellung und Verwaltung der Profile für das Registrierungsprogramm (die jeweils das Apple-Geräteregistrierungsprogramm und Apple School Manager unterstützen) sowie Apple Configurator-Profile getrennt:

**DEP-Profile**
![Abbildung von Azure DEP-Profilen](./media/15-azure-dep-profiles.png)

**Apple Configurator-Profile**
![Abbildung der Azure Apple Configurator-Profile](./media/16-azure-ac-profiles.png)
