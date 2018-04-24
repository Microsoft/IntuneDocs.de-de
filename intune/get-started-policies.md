---
title: Erste Schritte mit Richtlinien in Microsoft Intune
titlesuffix: ''
description: Erstellen von Richtlinien zum Schützen von Unternehmensdaten und Verwalten von Geräten, die Endbenutzer verwenden, um auf Unternehmensressourcen zuzugreifen.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 661ef25085892e299e45156f27b3d9db959577d4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="get-started-with-creating-policies"></a>Erste Schritte zum Erstellen von Richtlinien

Eines der wichtigsten Ziele bei den ersten Schritten mit Intune ist das Registrieren von Geräten, um sicherzustellen, dass sie mit den Unternehmensrichtlinien konform sind. Mit Kompatibilitätsrichtlinien können Sie nicht nur spezielle Gerätetypen wie z.B. firmeneigene Kioske verwalten, sondern auch persönliche Geräte und Tablets sowie benutzerlose Geräte.

![Konformitätsdashboard mit wenigen Daten](/intune/media/generic-compliance-dashboard.png)

Verwalten von mobilen Geräten in den folgenden Bereichen mithilfe von Konformitätsrichtlinien:

* Regulierung der Anzahl von Geräten, die jeder Benutzer registriert
* Verwalten der Geräteeinstellungen (z.B Verschlüsselung auf Geräteebene, Länge des Kennworts, Kameragebrauch)
* Bereitstellen von Apps, E-Mail-Profilen, VPN-Profilen, etc.
* Auswerten der Kriterien für Sicherheitskompatibilitätsrichtlinien auf Geräteebene

Sie erstellen Kompatibilitätsrichtlinien für jede Plattform einzeln. In dieser Übung verwenden wir nur iOS. Die folgenden Richtlinien sind für iOS-Geräte verfügbar:

* PIN- oder Kennwortkonfiguration
* Geräteverschlüsselung
* Per Jailbreak manipuliertes Gerät
* E-Mail-Profil
* Minimale Version des Betriebssystems
* Maximale Version des Betriebssystems

__Wie erstelle ich eine Richtlinie?__

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie **Gerätekompatibilität** aus.
4. Klicken Sie im Bereich **Gerätekonformität** auf **Richtlinien**.
5. Wählen Sie **Richtlinie erstellen** aus, und geben Sie dann die Details wie **Name** und **Beschreibung** ein. 
6. Wählen Sie **iOS** als **Plattform** aus.
6. Wählen Sie unter **Einstellungen** die Option **Systemsicherheit** aus, und legen Sie dann die Umschaltfläche **Anfordern eines Kennworts zum Entsperren mobiler Geräte** auf **Erforderlich** fest. Sie können auch weitere Regeln festlegen wie z.B. **Mindestlänge von Kennwörtern**, **Erforderlicher Kennworttyp** und **Anzahl nicht alphanumerischer Zeichen im Kennwort**. Wenn Sie Ihre Richtlinie eingerichtet haben, wählen Sie **OK** aus.
7. Kehren Sie zurück zum Bereich **Richtlinie erstellen**, und klicken Sie dann auf **Erstellen**.
8. Wählen Sie nach dem Erstellen der Richtlinie **Zuweisungen** aus, um sie Ihrer Testgruppe zuzuweisen. Wählen Sie Ihre Testgruppe mit Ihren Testbenutzern aus, und weisen Sie dieser Gruppe dann die Richtlinie zu, indem Sie auf **Speichern** klicken.
9. Warten Sie einige Minuten, bis Ihr registriertes Gerät Sie zur Eingabe eines aktualisierten Kennworts auffordert, damit weiterhin Kompatibilität mit der Unternehmensrichtlinie gegeben ist. Sie können dies auch manuell in der **Unternehmensportal-App für iOS** überprüfen, indem Sie auf den Gerätenamen und dann auf die Schaltfläche **Synchronisieren** klicken.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte beim Registrieren von Geräten:](get-started-enroll.md) Machen Sie sich mit dem Registrierungsprozess vertraut, indem Sie ein iOS-Gerät vollständig registrieren.

## <a name="learn-more"></a>Erfahren Sie mehr

* [Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)
* [Gängige Möglichkeiten der Verwendung des bedingten Zugriffs in Intune](conditional-access-intune-common-ways-use.md)
