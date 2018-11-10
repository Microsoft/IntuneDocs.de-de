---
title: Festlegen von Nutzungsbedingungen in Microsoft Intune
titlesuffix: ''
description: Legen Sie Geschäftsbedingungen fest, die Benutzern im Unternehmensportal für Intune angezeigt werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f480feae1e1df95567023614744c80ec392e86cb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236423"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie verlangen, dass Benutzer die Nutzungsbedingungen Ihres Unternehmens akzeptieren, bevor sie das Unternehmensportal für folgende Zwecke verwenden:
- Registrieren von Geräten
- Zugriff auf Ressourcen wie Unternehmens-Apps und -E-Mails.
Die Konfiguration der Geschäftsbedingungen ist optional.

Sie können mehrere Sätze von Bedingungen erstellen und diese verschiedenen Gruppen zuweisen, um z. B. verschiedene Sprachen zu unterstützen.

Es gibt zwei Möglichkeiten zum Erstellen der Nutzungsbedingungen Ihres Unternehmens:
- Die in diesem Artikel beschriebene Verwendung von Intune
- Die Verwendung des [Nutzungsbedingungsfeatures für Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou) – Sehen Sie sich den Blogbeitrag [Choosing the right Terms solution for your organization (Auswählen der passenden Lösung für die Nutzungsbedingungen Ihres Unternehmens)](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) an, um zu erfahren, welche Methode sich für Ihre Situation eignet. 

## <a name="create-terms-and-conditions"></a>Erstellen von Geschäftsbedingungen
Führen Sie die folgenden Schritte aus, um Geschäftsbedingungen zu erstellen. Der Anzeigename und die Beschreibung sind für administrative Zwecke vorgesehen, während die Eigenschaften der Bedingungen den Benutzern im Unternehmensportal angezeigt werden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf **Geräteregistrierung** > **Nutzungsbedingungen**.
2. Wählen Sie **Erstellen** aus.
![Screenshot: Azure-Portal mit Schaltfläche zum Erstellen von Geschäftsbedingungen](media/terms-create-terms.png)
3. Geben Sie auf im erweiterten Bereich die folgenden Informationen an:

   - **Anzeigename**: Die Bezeichnung für die Bedingungen im Azure-Portal. Diese Bezeichnung wird den Benutzern nicht angezeigt.

   - **Beschreibung**: Optionale Details, die Ihnen dabei helfen, diese Bedingungen im Azure-Portal zu identifizieren.

4. Klicken Sie auf den Pfeil neben **Define terms of use** (Nutzungsbedingungen definieren), um den Bereich „Nutzungsbedingungen“ zu öffnen, und geben Sie dann die folgenden Informationen ein:

   ![Screenshots des Bildschirms mit der Akzeptanz von Nutzungsbedingungen für Endbenutzer mit der Zusammenfassung der Nutzungsbedingungen](./media/terms-summary-create.png)

   - **Titel**: Der Name für Ihre Bedingungen, die Benutzern im Unternehmensportal oberhalb der **Zusammenfassung** angezeigt werden.
   - **Zusammenfassung der Nutzungsbedingungen**: Text, aus dem hervorgeht, welche Folgen die Annahme der Bedingungen für den Benutzer hat. Beispiel: Durch die Registrierung Ihres Geräts stimmen Sie den von Contoso dargelegten Nutzungsbedingungen zu. Lesen Sie die Bedingungen sorgfältig durch, bevor Sie fortfahren.
   - **Geschäftsbedingungen**: Die Geschäftsbedingungen, die den Benutzern angezeigt und von ihnen angenommen oder abgelehnt werden müssen.

5. Klicken Sie auf **OK** > **Erstellen**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Darstellung der Nutzungsbedingungen für die Benutzer
Das folgende Beispiel zeigt **Titel** und **Zusammenfassung der Nutzungsbedingungen** in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot von „Titel“ und „Zusammenfassung der Nutzungsbedingungen“ in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-summary-terms.png)

Das folgende Beispiel zeigt die Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot der Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Zuweisen von Geschäftsbedingungen

Sie können Geschäftsbedingungen zu Benutzergruppen zuweisen, die diese vor der Verwendung des Unternehmensportals annehmen müssen.

1. Wählen Sie im Azure-Portal die Option **Geräteregistrierung** und dann **Geschäftsbedingungen** aus.
2. Wählen Sie in der Liste der Nutzungsbedingungen die Bedingungen aus, die Sie zuweisen möchten, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.
![Screenshot des Bereichs „Gruppe zuweisen“ im Azure-Portal, das die Schaltflächen „Gruppe auswählen“ und „Auswählen“ für die Zuweisung der Geschäftsbedingungen anzeigt](media/terms-assign-groups.png)
3. Klicken Sie auf **Select groups to include** (Einzuschließende Gruppen auswählen), und wählen Sie die Gruppen aus, denen Sie die Bedingungen zuweisen möchten. Klicken Sie anschließend auf **Auswählen**. Dynamischen Gruppen können keine Nutzungsbedingungen zugewiesen werden.
4. Klicken Sie im Bereich **Zugewiesene Gruppen** auf **Speichern**.  Die Geschäftsbedingungen werden jetzt den Benutzern in den ausgewählten Gruppen zugewiesen. Benutzer werden beim nächsten Zugriff auf das Unternehmensportal zur Annahme der Geschäftsbedingungen aufgefordert. Die Geschäftsbedingungen müssen nur einmal akzeptiert werden. Benutzer mit mehreren Geräten müssen sie nicht auf jedem Gerät annehmen.


## <a name="monitor-terms-and-conditions"></a>Überwachen der Geschäftsbedingungen

1. Klicken Sie im Azure-Portal auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**. 
1. Klicken Sie im Bereich „Intune“ auf **Geräteregistrierung** > **Nutzungsbedingungen**.
2. Wählen Sie in der Liste der Nutzungsbedingungen die Bedingungen aus, für die Sie die Annahme anzeigen möchten, und klicken Sie dann auf **Annahmebericht**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeiten mit mehreren Versionen der Nutzungsbedingungen
Sie können Ihre Geschäftsbedingungen bearbeiten und ihre Versionen verwalten. Jedes Mal, wenn Sie eine wesentliche Änderung an den Nutzungsbedingungen vornehmen, sollten Sie folgende Schritte durchführen:
- Erhöhen Sie die Versionsnummer
- Fordern Sie Benutzer dazu auf, die neuen Nutzungsbedingungen zu akzeptieren. Sie können die aktuelle Versionsnummer beispielsweise beibehalten, wenn Sie Tippfehler oder die Formatierung anpassen.

1. Klicken Sie im Azure-Portal auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**.

2. Klicken Sie im Bereich „Intune“ auf **Geräteregistrierung** > **Nutzungsbedingungen**, und wählen Sie dann die Nutzungsbedingungen aus, die Sie ändern möchten. Klicken Sie anschließend auf **Eigenschaften**.

4. Klicken Sie im Bereich **Eigenschaften** auf **Nutzungsbedingungen**, und ändern Sie bei Bedarf **Titel**, **Summary of Terms** (Zusammenfassung der Nutzungsbedingungen) und die **Nutzungsbedingungen**. Wenn Ihre Änderungen eine erneute Akzeptierung Ihrer Benutzer voraussetzen, klicken Sie auf **Fordert eine erneute Annahme durch die Benutzer an und erhöht die Versionsnummer auf...**.

4.  Klicken Sie auf **OK** > **Speichern**.

Benutzer müssen die aktualisierten Geschäftsbedingungen nur einmal annehmen. Benutzer mit mehreren Geräten müssen die Geschäftsbedingungen nicht auf jedem Gerät annehmen.
