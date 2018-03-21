---
title: Erste Schritte mit der Benutzerverwaltung
titlesuffix: Microsoft Intune
description: "Hinzufügen eines Benutzers zu Intune und Zuweisen einer Lizenz für den Benutzer, damit dieser auf Unternehmensressourcen auf mobilen Geräten zugreifen kann."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 53b5be6e5cdf8f60304126e133a727123bfef58d
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="get-started-managing-users"></a>Erste Schritte mit der Benutzerverwaltung

Denken Sie an die verschiedenen Personen in Ihrer Organisation. Jeder von ihnen, der Unternehmensdaten verwendet, benötigt einen Benutzer, um den Zugriff auf die Daten in Intune zu verwalten.

## <a name="how-do-i-create-a-user"></a>Wie erstelle ich einen Benutzer?

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wenn Sie den Bereich **Microsoft Intune** geöffnet haben, wählen Sie **Benutzer** aus. Wählen Sie auf der Seite **Alle Benutzer** die Option **+ Neuer Benutzer** aus.
4. Machen Sie genauere Angaben zum Benutzer: geben Sie z.B. einen **Namen** und einen **Benutzernamen** ein. Der Domänennamenteil des Benutzernamens muss entweder der anfängliche Standarddomänenname „contoso.onmicrosoft.com“ oder ein verifizierter Domänenname ohne Verbund wie z.B. „contoso.com“ sein.
5. Wählen Sie unter **Gruppen** die Testgruppe, die Sie dem Benutzer hinzufügen möchten.
6. Speichern Sie das automatisch generierte Benutzerkennwort, das Sie zur Anmeldung bei einem Testgerät benötigen. Dieses Kennwort müssen Sie Benutzern geben, damit sie es in ein normales Kennwort ändern können, das sie sich leichter merken können.
7. Klicken Sie im Bereich **Benutzer** auf **Erstellen**.

## <a name="assigning-licenses-to-users"></a>Zuweisen von Lizenzen zu Benutzern

Nachdem Sie einen Benutzer erstellt haben, können Sie über das [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) einem Benutzer eine Intune-Lizenz zuweisen. Wenn ein Benutzer keine Lizenz hat, kann er sein Gerät auch nicht für die Verwaltung registrieren.

1. Melden Sie sich im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) mit den gleichen Anmeldeinformationen an, die Sie auch zur Anmeldung in Intune verwendet haben.
2. Klicken Sie auf **Benutzer** > **Aktive Benutzer**, und klicken Sie anschließend auf den Benutzer, den Sie erstellt haben.
3. Möglicherweise nimmt das Laden aller Informationen des Benutzers einige Zeit in Anspruch. Sobald Sie geladen wurden, klicken Sie für die **Produktlizenzen** des Benutzers auf **Bearbeiten**.
4. Weisen Sie dem Benutzer einen **Ort** zu und stellen Sie Intune auf **ein**.

 > [!NOTE]
 > Dadurch wird eine Ihrer Lizenzen für den Benutzer verwendet. Wenn Sie ihre dynamische Umgebung verwenden, können Sie später die Verwendung dieser Lizenz rückgängig machen, um Sie einem echten Benutzer zuzuweisen.

5. Wählen Sie **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte mit Gruppen:](get-started-groups.md) Organisieren Sie Benutzer in Gruppen, um die Richtlinien und Apps leichter zu verwalten, auf die sie zugreifen können.
