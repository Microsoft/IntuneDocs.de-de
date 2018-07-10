---
title: Erste Schritte mit Richtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen von Richtlinien zum Schützen von Unternehmensdaten und Verwalten von Geräten, die Endbenutzer verwenden, um auf Unternehmensressourcen zuzugreifen. Weisen Sie die Richtlinien anschließend Gruppen zu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271523"
---
# <a name="get-started-with-creating-policies"></a>Erste Schritte zum Erstellen von Richtlinien

Intune-Richtlinien sind gut für die Registrierung von Geräten geeignet und stellen sicher, dass diese mit Ihren Unternehmensrichtlinien konform sind. Mit Konformitätsrichtlinien können Sie spezielle Gerätetypen wie z.B. firmeneigene Kiosks, persönliche Geräte, Tablets und benutzerlose Geräte verwalten.

![Konformitätsdashboard mit wenigen Daten](/intune/media/generic-compliance-dashboard.png)

Für mobile Geräte kann mithilfe von Konformitätsrichtlinien Folgendes verwaltet werden:

* Die Anzahl der Geräte, die ein Benutzer in Intune registriert
* Die Geräteeinstellungen, z.B Verschlüsselung auf Geräteebene, Länge des Kennworts, Kameragebrauch
* Das Bereitstellen von Apps, E-Mail-Profilen, VPN-Profilen etc.
* Auswerten der Kriterien für Sicherheitskompatibilitätsrichtlinien auf Geräteebene

Konformitätsrichtlinien werden für jede Plattform (z.B. iOS, Android, Windows) erstellt. Verwenden Sie für diese Übung iOS. Die folgenden Richtlinien sind für iOS-Geräte verfügbar:

* PIN- oder Kennwortkonfiguration
* Geräteverschlüsselung
* Per Jailbreak manipuliertes Gerät
* E-Mail-Profil
* Minimale Version des Betriebssystems
* Maximale Version des Betriebssystems

## <a name="create-a-policy"></a>Erstellen einer Richtlinie

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen**.
4. Geben Sie einen **Richtliniennamen** und ein **Beschreibung** ein. 
5. Wählen Sie **iOS** als **Plattform** aus.
6. Wählen Sie unter **Einstellungen** die Option **Systemsicherheit** aus, und legen Sie dann **Kennwort zum Entsperren mobiler Geräte erforderlich** auf **Erforderlich** fest. 

    Sie können auch andere Regeln festlegen, z.B.: 
    - **Minimale Kennwortlänge**
    - **Erforderlicher Kennworttyp**
    - **Anzahl der nicht alphanumerischen Zeichen im Kennwort**
    
    Wenn Sie Ihre Richtlinie eingerichtet haben, klicken Sie auf **OK**.
  
7. Kehren Sie zu **Richtlinie erstellen** zurück, und klicken Sie auf **Erstellen**. Dieser Schritt erstellt die Richtlinie und führt Sie unter **Gerätekonformität** > **Richtlinien** auf.
8. Wählen Sie die neue Richtlinie aus, und klicken Sie auf **Zuweisungen**. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
Klicken Sie auf „Ausgewählte Gruppen“, um Ihre vorhandenen Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

Damit das registrierte Gerät mit der neuen Unternehmensrichtlinie konform ist, werden Sie nach wenigen Minuten zur Eingabe eines aktualisierten Kennworts aufgefordert. Sie können das Update manuell in der **Unternehmensportal-App für iOS** suchen. Öffnen Sie die Unternehmensportal-App, wählen Sie den Namen des Geräts aus, und klicken Sie auf **Synchronisieren**.

> [!NOTE]
> Wenn neue Richtlinien auf eine dynamische Gerätegruppe angewendet werden, kann es bis zu acht Stunden dauern, bis dies für alle Geräte in der Gruppe durchgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte beim Registrieren von Geräten:](get-started-enroll.md) Machen Sie sich mit dem Registrierungsprozess vertraut, indem Sie ein iOS-Gerät vollständig registrieren.

## <a name="learn-more"></a>Erfahren Sie mehr

* [Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)
* [Gängige Möglichkeiten der Verwendung des bedingten Zugriffs in Intune](conditional-access-intune-common-ways-use.md)
