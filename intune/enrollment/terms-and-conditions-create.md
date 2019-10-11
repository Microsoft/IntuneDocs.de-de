---
title: Festlegen von Nutzungsbedingungen in Microsoft Intune
titleSuffix: ''
description: Legen Sie Geschäftsbedingungen fest, die Benutzern im Unternehmensportal für Intune angezeigt werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ef002b508e484d6967bbdd0908729332d866046
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726361"
---
# <a name="terms-and-conditions-for-user-access"></a>Geschäftsbedingungen für den Benutzerzugriff

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Als Intune-Administrator können Sie verlangen, dass Benutzer die Nutzungsbedingungen Ihres Unternehmens akzeptieren, bevor sie das Unternehmensportal für folgende Zwecke verwenden:
- Registrieren von Geräten
- Zugriff auf Ressourcen wie Unternehmens-Apps und -E-Mails.

Die Konfiguration der Geschäftsbedingungen ist optional.

Sie können mehrere Sätze von Bedingungen erstellen und diese verschiedenen Gruppen zuweisen, um z. B. verschiedene Sprachen zu unterstützen.

Es gibt zwei Möglichkeiten zum Erstellen der Nutzungsbedingungen Ihres Unternehmens:
- Die in diesem Artikel beschriebene Verwendung von Intune
- Die Verwendung der Funktion [Nutzungsbedingungen für Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

Informationen zu den verschiedenen Methoden finden Sie im Blogbeitrag [Auswählen der passenden Lösung für die Nutzungsbedingungen Ihrer Organisation](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409). 

## <a name="create-terms-and-conditions"></a>Erstellen von Geschäftsbedingungen
Führen Sie die folgenden Schritte aus, um Geschäftsbedingungen zu erstellen. Der Anzeigename und die Beschreibung sind für administrative Zwecke vorgesehen, während die Eigenschaften der Bedingungen den Benutzern im Unternehmensportal angezeigt werden.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie im Bereich **Intune** auf **Geräteregistrierung** > **Nutzungsbedingungen**.
3. Wählen Sie **Erstellen** aus.
4. Geben Sie auf der Seite für die **Grundlagen** die folgenden Informationen an:

   - **Name**: Die Bezeichnung für die Bedingungen im Azure-Portal. Diese Bezeichnung wird den Benutzern nicht angezeigt.
   - **Beschreibung**: Optionale Details, die Ihnen dabei helfen, diese Bedingungen im Azure-Portal zu identifizieren.

    ![Screenshot: Azure-Portal mit der Seite für Grundlagen für die Geschäftsbedingungen](./media/terms-and-conditions-create/terms-basics-page.png)

5. Klicken Sie auf **Weiter** aus, um zur Seite **Nutzungsbedingungen** zu gelangen. Geben Sie dort die folgenden Informationen an:

   - **Titel**: Der Name für Ihre Bedingungen, die Benutzern im Unternehmensportal oberhalb der **Zusammenfassung** angezeigt werden.
   - **Geschäftsbedingungen**: Die Geschäftsbedingungen, die den Benutzern angezeigt und von ihnen angenommen oder abgelehnt werden müssen.
   - **Zusammenfassung der Nutzungsbedingungen**: Text, aus dem hervorgeht, welche Folgen die Annahme der Bedingungen für den Benutzer hat. Beispiel: Durch die Registrierung Ihres Geräts stimmen Sie den von Contoso dargelegten Nutzungsbedingungen zu. Lesen Sie die Bedingungen sorgfältig durch, bevor Sie fortfahren.

6. Wählen Sie **Weiter** aus, um zur Seite **Bereichstags** zu gelangen.

7. Wählen Sie zunächst **Bereichstags auswählen**, dann wählen Sie die Bereichsmarkierung aus, die Sie diesen Bedingungen zuordnen möchten, und klicken dann auf **Auswählen**. 

8. Klicken Sie auf **Weiter**, um zur Seite **Zuweisungen** zu gelangen, und wählen Sie dann eine der folgenden Optionen für **Zuweisen zu** aus:
    - **Alle Benutzer**: Wählen Sie diese Option aus, um diese allgemeinen Geschäftsbedingungen allen Benutzern zuzuweisen.
    - **Gruppen auswählen**: Wählen Sie diese Option aus, um diese allgemeinen Geschäftsbedingungen allen Personen in den von Ihnen identifizierten Gruppen zuzuordnen, indem Sie **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen** auswählen.

9. Wählen Sie **Weiter** > **Erstellen**aus.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Darstellung der Nutzungsbedingungen für die Benutzer
Das folgende Beispiel zeigt **Titel** und **Zusammenfassung der Nutzungsbedingungen** in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot von „Titel“ und „Zusammenfassung der Nutzungsbedingungen“ in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-and-conditions-create/terms-summary-terms.png)

Das folgende Beispiel zeigt die Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot der Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>Überwachen der Geschäftsbedingungen

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an. 
1. Klicken Sie im Bereich „Intune“ auf **Geräteregistrierung** > **Nutzungsbedingungen**.
2. Wählen Sie in der Liste der Nutzungsbedingungen die Bedingungen aus, für die Sie die Annahme anzeigen möchten, und klicken Sie dann auf **Annahmebericht**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeiten mit mehreren Versionen der Nutzungsbedingungen
Sie können Ihre Geschäftsbedingungen bearbeiten und ihre Versionen verwalten. Jedes Mal, wenn Sie eine wesentliche Änderung an den Nutzungsbedingungen vornehmen, sollten Sie folgende Schritte durchführen:
- Erhöhen Sie die Versionsnummer
- Fordern Sie die Benutzer auf, die neuen Allgemeinen Geschäftsbedingungen zu akzeptieren.

Behalten Sie die aktuelle Versionsnummer bei, wenn Sie z. B. Tippfehler korrigieren oder die Formatierung ändern.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Klicken Sie im Bereich „Intune“ auf **Geräteregistrierung** > **Nutzungsbedingungen**, und wählen Sie dann die Nutzungsbedingungen aus, die Sie ändern möchten. Klicken Sie anschließend auf **Eigenschaften**.

4. Klicken Sie im Bereich **Eigenschaften** auf **Nutzungsbedingungen**, und ändern Sie bei Bedarf **Titel**, **Summary of Terms** (Zusammenfassung der Nutzungsbedingungen) und die **Nutzungsbedingungen**. Wenn Ihre Änderungen eine erneute Akzeptierung Ihrer Benutzer voraussetzen, klicken Sie auf **Fordert eine erneute Annahme durch die Benutzer an und erhöht die Versionsnummer auf...** .

4. Klicken Sie auf **OK** > **Speichern**.

Benutzer müssen die aktualisierten Geschäftsbedingungen nur einmal annehmen. Benutzer mit mehreren Geräten müssen die Geschäftsbedingungen nicht auf jedem Gerät annehmen.
