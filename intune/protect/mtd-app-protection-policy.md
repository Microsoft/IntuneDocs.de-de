---
title: Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie eine Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Microsoft Intune erstellen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794419"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune

> [!NOTE] 
> Dieser Artikel gilt für alle Mobile Threat Defense-Partner (MTD), die App-Schutzrichtlinien unterstützen: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

Intune mit MTD hilft Ihnen dabei, Bedrohungen zu erkennen und Risiken auf mobilen Geräten zu bewerten. Sie können eine Intune-App-Schutzrichtlinie erstellen, die eine Risikobewertung durchführt und bestimmt, ob dem Gerät Zugriff auf Unternehmensdaten gewährt wird. 

## <a name="before-you-begin"></a>Vorbereitung

Beim Einrichten von MTD haben Sie in der MTD-Partnerkonsole eine Richtlinie erstellt, die verschiedene Bedrohungen als hoch, mittel und niedrig klassifiziert. Nun müssen Sie die Mobile Threat Defense-Stufe in der Intune-App-Schutzrichtlinie festlegen.

Voraussetzungen für die App-Schutzrichtlinie mit MTD:

- Richten Sie die MTD-Integration in Intune ein. Ohne diese Integration hat die MTD-App-Schutzrichtlinie keine Auswirkung.

## <a name="to-create-an-mtd-app-protection-policy"></a>Erstellen einer MTD-App-Schutzrichtlinie

1. Melden Sie sich im [Azure-Portal](https://portal.azure.com/) mit Ihren Intune-Anmeldeinformationen an.

2. Klicken Sie im **Azure-Dashboard** im linken Menü auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** aus. Das **Intune-Dashboard** wird geöffnet.

4. Wählen Sie im **Intune-Dashboard** **Client-Apps** und dann im Abschnitt **Verwalten** die Option **App-Schutzrichtlinien** aus.

5. Wählen Sie **Richtlinie erstellen** aus, geben Sie den **Namen** und die **Beschreibung** ein, und wählen Sie die **Plattform** aus. 

6. Wählen Sie im Bereich **Bedingter Start** bei der Tabelle **Gerätebedingungen** aus der Dropdownliste **Maximal zulässige Gerätebedrohungsstufe** die gewünschte Stufe für mobile Bedrohungen aus.

    ein.  **Secured** (Geschützt): Diese Stufe ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.

    b.  **Niedrig:** Das Gerät ist konform, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.

    c.  **Mittel:** Das Gerät ist konform, wenn auf dem Gerät Bedrohungen niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.

    d.  **Hoch:** Diese Stufe gewährleistet das geringste Maß an Sicherheit. Sie lässt alle Bedrohungsstufen zu und verwendet Mobile Threat Defense nur zu Berichtszwecken. Auf Geräten muss mit dieser Einstellung die MTD-App aktiviert sein.

7. Klicken Sie zweimal auf **Speichern**, und wählen Sie dann **Erstellen** aus.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Zuweisen einer MTD-App-Schutzrichtlinie

Wählen Sie zum Zuweisen einer Gerätekompatibilitätsrichtlinie zu Benutzern eine Richtlinie aus, die Sie zuvor konfiguriert haben. Vorhandene Richtlinien finden Sie im Bereich **Gerätekonformität > Richtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Mit dieser Aktion öffnen Sie den Bereich, in dem Sie **Azure Active Directory-Sicherheitsgruppen** auswählen und der Richtlinie zuweisen können.

2. Klicken Sie auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen. Die Auswahl von **Auswählen** bewirkt die Bereitstellung der Richtlinie für Benutzer.

> [!NOTE] 
> Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden für den Zugriff auf Unternehmensdaten in Ziel-Apps über den Intune-App-Schutz ausgewertet.

## <a name="next-steps"></a>Nächste Schritte  

- Erfahren Sie mehr über [Mobile Threat Defense](~/protect/mobile-threat-defense.md) in Microsoft Intune.
