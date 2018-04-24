---
title: Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten
titlesuffix: Microsoft Intune
description: Fügen Sie Gruppen zum Organisieren von Benutzern und Geräten nach Geografie, Abteilung oder nach Hardwareeigenschaften hinzu.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 613d64e396e969b8b6bde76ee6c4474a60be8ba9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-groups-to-organize-users-and-devices"></a>Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten
Intune verwendet Azure Active Directory-Gruppen (AD) zur Verwaltung von Geräten und Benutzern. Als Intune-Administrator können Sie Gruppen entsprechend der Anforderungen Ihrer Organisation einrichten. Sie können Gruppen erstellen, um Benutzer oder Geräte nach geografischem Standort, Abteilung oder Hardwareeigenschaften zu organisieren. Sie können Gruppen zur bedarfsgerechten Verwaltung von Aufgaben verwenden. So können Sie beispielsweise Richtlinien für viele Benutzer festlegen oder Apps für eine Reihe von Geräten bereitstellen.

In diesem Thema wird das Hinzufügen von Gruppen für die Verwendung in Intune erläutert.

Sie können die folgenden Gruppentypen hinzufügen:
- **Zugewiesene Gruppen**: Manuelles Hinzufügen von Benutzern oder Geräten in eine statische Gruppe
- **Dynamische Gruppen**: (Mit Azure Active Directory Premium) Dynamisches Erstellen von Benutzer- oder Gerätegruppen, die durch einfache oder erweiterte Regeln definiert werden

## <a name="add-a-new-group"></a>Hinzufügen einer neuen Gruppe

Führen Sie die folgenden Schritte aus, um eine neue Gruppe zu erstellen:
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Gruppen** und dann im Bereich **Alle Gruppen** die Option **Neue Gruppe** aus.
   ![Screenshot des Azure-Portals mit ausgewählter Option „Neue Gruppe“](./media/groups-add-new.png)
4. Geben Sie den **Gruppentyp**, den **Namen** und die **Beschreibung** der neuen Gruppe an. Diese Eigenschaften werden nur im Verwaltungsportal und nicht den Benutzern angezeigt.

5. Wählen Sie den **Mitgliedschaftstyp** aus:
   - **Zugewiesen**: Zur Erstellung einer Gruppe mit manuell zugewiesenen Mitgliedern. Weitere Informationen zu [zugewiesenen Azure AD-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Dynamischer Benutzer**: Zur Erstellung einer Benutzergruppe, die durch eine **Dynamische Abfrage** definiert wird.
   - **Dynamisches Gerät**: Zur Erstellung einer Gerätegruppe, die durch eine **Dynamische Abfrage** definiert wird.

   ![Screenshot der Intune-Gruppeneigenschaften](./media/groups-add-properties.png)

   Mit Azure AD können Sie dynamische Gruppen auf der Grundlage von Regeln erstellen, die die Mitgliedschaft definieren. Weitere Informationen zum [Erstellen von attributbasierten dynamischen Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

6. Sie können die Option **Office-Features aktivieren** auswählen, um Mitgliedern von Benutzergruppen Zugriff auf freigegebene Office 365-Apps zu gewähren. Weitere Informationen zu [Office 365-Gruppen](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
7. Klicken Sie auf die Option **Erstellen**, um die neue Gruppe hinzuzufügen.

## <a name="see-also"></a>Siehe auch
- [Verwalten des Zugriffs auf Ressourcen mit Azure Active Directory-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Klassische Intune-Gruppen im Azure-Portal](groups-get-started.md)
