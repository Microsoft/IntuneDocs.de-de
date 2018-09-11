---
title: Einführung in Intune im Azure-Portal
titlesuffix: ''
description: Microsoft Intune ist im Azure-Portal verfügbar. Weitere grundlegende Informationen zu Intune finden Sie im Azure-Portal.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: get-started
ms.openlocfilehash: 3f8f0dce416c943dbc244d0e2a4366b12b305708
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253781"
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Einführung in Microsoft Intune im Azure-Portal


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Genau wie andere Azure-Dienste ist Microsoft Intune im Azure-Portal verfügbar. Wenn Sie **Intune** im Azure-Portal auswählen, können Sie die mobilen Geräte, PCs und Apps Ihrer Organisation verwalten.

> [!NOTE]
> Wenn zuvor Sie eine frühere Version von Microsoft Intune verwendet haben, sind die folgenden Informationen womöglich hilfreich für Sie:
>     * [Wo befinden sich meine Funktionen in Azure jetzt?](ui-changes.md) bezieht sich darauf, Ihnen die bestimmten Workloads und UIs zu zeigen, die sich mit dem Umzug zu Azure verändert haben.
>     * [Klassische Intune-Gruppen im Azure-Portal](groups-get-started.md) erklärt die Auswirkungen des Umzugs zu Azure Active Directory-Sicherheitsgruppen für die Gruppenverwaltung.

Die Microsoft Intune-Benutzeroberfläche im Azure-Portal bietet folgende Vorteile:

- Eine integrierte Konsole für alle Komponenten von Enterprise Mobility + Security (EMS)
- Eine HTML-Konsole basierend auf Webstandards
- Microsoft Graph-API-Unterstützung zur Automatisierung vieler Aktionen
- Azure Active Directory-Gruppen (AD) für Kompatibilität zwischen all Ihren Azure-Anwendungen
- Unterstützung für die meisten modernen Webbrowser

## <a name="before-you-start"></a>Vorbereitung

Um Intune im Azure-Portal verwenden zu können, benötigen Sie ein Administrator- und ein Mandantenkonto für Intune. [Registrieren Sie sich für ein Konto](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20), wenn Sie noch keines haben.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Unterstützte Webbrowser für das Azure-Portal

Das Azure-Portal kann auf die meisten modernen PCs, Macs und Tablets ausgeführt werden. Mobiltelefone werden nicht unterstützt.
Zurzeit werden die folgenden Browser unterstützt:

- Microsoft Edge (neueste Version)
- Microsoft Internet Explorer 11
- Safari (neueste Version, nur auf Mac)
- Chrome (neueste Version)
- Firefox (neueste Version)

Aktuelle Informationen zu den unterstützten Browsern finden Sie im [Azure-Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune im Azure-Portal

Sie finden den Microsoft Intune-Dienst im [Azure-Portal](https://portal.azure.com). In Azure gibt es viele Dienste, von denen Sie einige nicht regelmäßig verwenden. Eine kurze Einführung zum Anpassen Ihrer Portalumgebung finden Sie unter [Erste Schritte mit Intune im Azure-Portal](get-started-azure.md).

## <a name="the-microsoft-intune-documentation"></a>Die Microsoft Intune-Dokumentation

Dieses Thema wird genauso wie die gesamte Microsoft-Dokumentation laufend auf den neuesten Stand gebracht. Wenn Sie Vorschläge haben soll, hinterlassen Sie in den Kommentaren zum Thema Ihr Feedback. Wir freuen uns, von Ihnen zu hören.

Die Dokumentation orientiert sich am Layout von Microsoft Intune im Azure-Portal (siehe unten), damit Sie die gewünschten Informationen einfacher finden.

![Azure-Portal-Workloads](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Dokumentationsleitfaden

Verwenden Sie die folgende Tabelle, um die wichtigsten Bereiche von Microsoft Intune schnell zu finden und zu verstehen.

| Abschnitt                                                      | Beschreibung                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Einführung und erste Schritte](introduction-intune.md)       | Informationen zu den Grundlagen von Intune, einschließlich:<br /> – Allgemeine Lösungen<br /> – Die Art und Weise wie Microsoft Intune funktioniert<br /> – Geräteverwaltung in Intune<br /> – App-Verwaltung in Intune<br /> – Enterprise Mobility-Verwaltung (EMM) mit und ohne Geräteregistrierung                                                         |
| [Planung und Entwurf](planning-guide.md)                         | Anleitung für das erfolgreiche Planen und Entwerfen Ihrer Microsoft Intune-Umgebung                                                                                                                                                                                                             |
| [Geräteregistrierung](device-enrollment.md)                    | Verstehen, wie Microsoft Intune Ihnen bei der Verwaltung der Geräte Ihrer Mitarbeiter hilft, indem Geräte beim Intune-Dienst registriert werden. Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter zu registrieren.                                                                                                         |
| [Gerätekompatibilität](device-compliance.md)                    | Intune-Gerätekonformitätsrichtlinien definieren die Regeln und Einstellungen, die ein Gerät erfüllen muss, damit es von Microsoft Intune als konform eingestuft wird. Beispiele für die Konformität sind z.B. ein Kennwort für den Gerätezugriff anfordern, Geräte verschlüsseln oder dass eine Mindestbetriebssystemversion erforderlich ist. |
| [Gerätekonfiguration](device-profiles.md)                   | Konfigurieren der Einstellungen und Features mithilfe von Microsoft Intune auf allen Geräten, die Sie verwalten, indem Sie Geräteprofile erstellen. Sie können beispielsweise Funktionen wie Benachrichtigungen, Datenfreigabe, E-Mail-Support, WLAN-Konnektivität, Zertifikate und Endpoint Protection konfigurieren.              |
| [Geräte](device-management.md)                              | Stellen Sie sicher, dass von Ihnen verwaltete Geräte die Ressourcen bereitstellen, die Ihre Endbenutzer für Ihre Arbeit benötigen, während gleichzeitig die Daten Ihres Unternehmens vor Risiken geschützt werden. Verwalten Sie Geräte, indem Sie den Gerätebestand Ihrer Mitarbeiter prüfen und Remotegeräteaktionen durchführen.                                                      |
| [Mobile Apps](app-management.md)                             | Verstehen, wie Apps hinzugefügt, bereitgestellt, überwacht, konfiguriert und geschützt werden                                                                                                                                                                                                                             |
| [Bedingter Zugriff](conditional-access.md)                  | Definieren von Bedingungen auf Geräten oder Apps, die den Zugriff auf Ihre Unternehmensdaten einschränken.                                                                                                                                                                                                            |
| [Benutzer](users-add.md)                                        | Informationen zum Hinzufügen von Benutzern von Geräten und Apps, die Sie verwalten.                                                                                                                                                                                                                                           |
| [Gruppen](groups-get-started.md)                              | Informationen zum Erstellen und Verwalten von Gruppen mit Intune. Mithilfe von Gruppen können Sie schnell ein Gerät, eine App-Konfiguration und Schutzrichtlinien zuweisen.                                                                                                                                             |
| [Intune-Rollen](role-based-access-control.md)                 | Lernen Sie, wie Sie kontrollieren können, wer welche Intune-Aktionen ausführen kann und wie diese Aktionen angewendet werden. Sie können entweder die integrierten Rollen verwenden, die einige allgemeine Intune-Szenarien abdecken, oder Sie können eigene Rollen erstellen.                                                                                 |
| [Softwareupdates](windows-update-for-business-configure.md) | Erfahren Sie, wie Sie Softwareupdates für Windows 10-Geräte konfigurieren.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Was gibt es Neues?

Informationen zu den neuesten Funktionen von Microsoft Intune finden Sie unter [Was gibt es Neues?](whats-new.md).
