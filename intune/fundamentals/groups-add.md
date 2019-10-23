---
title: Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten
titleSuffix: Microsoft Intune
description: Fügen Sie Gruppen zum Organisieren von Benutzern und Geräten nach Geografie, Abteilung oder nach Hardwareeigenschaften hinzu.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0702eebdd3899c6da527af0078e5e7d47cf95194
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510238"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten
Intune verwendet Azure Active Directory-Gruppen (AD) zur Verwaltung von Geräten und Benutzern. Als Intune-Administrator können Sie Gruppen entsprechend der Anforderungen Ihrer Organisation einrichten. Sie können Gruppen erstellen, um Benutzer oder Geräte nach geografischem Standort, Abteilung oder Hardwareeigenschaften zu organisieren. Sie können Gruppen zur bedarfsgerechten Verwaltung von Aufgaben verwenden. So können Sie beispielsweise Richtlinien für viele Benutzer festlegen oder Apps für eine Reihe von Geräten bereitstellen.

Sie können die folgenden Gruppentypen hinzufügen:
- **Zugewiesene Gruppen**: Manuelles Hinzufügen von Benutzern oder Geräten in eine statische Gruppe
- **Dynamische Gruppen**: (Mit Azure Active Directory Premium) Dynamisches Erstellen von Benutzer- oder Gerätegruppen, die durch einfache oder erweiterte Regeln definiert werden

## <a name="add-a-new-group"></a>Hinzufügen einer neuen Gruppe

Führen Sie die folgenden Schritte aus, um eine neue Gruppe zu erstellen:
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Gruppen** und dann im Bereich **Alle Gruppen** die Option **Neue Gruppe** aus.
   ![Screenshot des Azure-Portals mit ausgewählter Option „Neue Gruppe“](./media/groups-add/groups-add-new.png)
4. Wählen Sie unter **Gruppentyp** eine der folgenden Optionen aus:
    - **Sicherheit**: Sicherheitsgruppen sind eine gute Ressource zum Auffüllen von Benutzergruppen. Da in Sicherheitsgruppen definiert wird, wer auf welche Ressourcen zugreifen kann, lassen sich Sicherheitsgruppen oft gut in Intune-Benutzergruppen übersetzen. Sicherheitsgruppen, die aus Active Directory mit Azure Active Directory synchronisiert oder direkt mithilfe des Microsoft 365 Admin Centers oder des Azure-Portals in Azure Active Directory erstellt werden, stehen Ihnen beim Erstellen von Benutzergruppen in Intune zur Verfügung.
    - **Office 365**

5. Geben Sie einen **Namen** und eine **Beschreibung** für die neue Gruppe ein. Diese Eigenschaften werden nur im Verwaltungsportal und nicht den Benutzern angezeigt.

6. Wählen Sie den **Mitgliedschaftstyp** aus:
   - **Zugewiesen**: Zur Erstellung einer Gruppe mit manuell zugewiesenen Mitgliedern. Weitere Informationen zu [zugewiesenen Azure AD-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Dynamischer Benutzer**: Zur Erstellung einer Benutzergruppe, die durch eine **Dynamische Abfrage** definiert wird.
   - **Dynamisches Gerät**: Zur Erstellung einer Gerätegruppe, die durch eine **Dynamische Abfrage** definiert wird.

   ![Screenshot der Intune-Gruppeneigenschaften](./media/groups-add/groups-add-properties.png)

   Mit Azure AD können Sie dynamische Gruppen auf der Grundlage von Regeln erstellen, die die Mitgliedschaft definieren. Weitere Informationen zum [Erstellen von attributbasierten dynamischen Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. Sie können die Option **Office-Features aktivieren** auswählen, um Mitgliedern von Benutzergruppen Zugriff auf freigegebene Office 365-Apps zu gewähren. Weitere Informationen zu [Office 365-Gruppen](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Klicken Sie auf die Option **Erstellen**, um die neue Gruppe hinzuzufügen.

## <a name="groups-and-policies"></a>Gruppen und Richtlinien

Überlegen Sie beim Erstellen von Gruppen, wie Sie [Richtlinien](../protect/device-compliance-get-started.md) anwenden möchten. Sie verfügen möglicherweise z.B. über Richtlinien, die für ein Gerätebetriebssystem oder für verschiedene Rollen oder Organisationseinheiten in Ihrer Organisation spezifisch sind, die Sie in Active Directory bereits definiert haben. Es kann sinnvoll sein, getrennte Gerätegruppen für iOS, Android und Windows sowie eine Benutzergruppe für jede Rolle in der Organisation zu verwenden.

Vermutlich ist es ebenfalls ratsam, eine Standardrichtlinie zu erstellen, die für alle Gruppen und Geräte gilt, um die grundlegenden Compliance-Anforderungen Ihrer Organisation zu erfüllen. Dadurch können Sie spezifischere Richtlinien für die weitesten Kategorien von Benutzern und Geräten erstellen. Beispielsweise können Sie E-Mail-Richtlinien für jedes der Betriebssysteme der mobilen Geräte erstellen.



## <a name="see-also"></a>Siehe auch
- [Verwalten des Zugriffs auf Ressourcen mit Azure Active Directory-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Klassische Intune-Gruppen im Azure-Portal](groups-get-started.md)
