---
title: Festlegen von Nutzungsbedingungen in Microsoft Intune
titlesuffix: ''
description: Legen Sie Geschäftsbedingungen fest, die Benutzern im Unternehmensportal für Intune angezeigt werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 550d9c457335f212f0b60c16249e45f22f5baaf5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31033299"
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie festlegen, dass für Benutzer die Annahme der Geschäftsbedingungen Ihres Unternehmens erforderlich ist, bevor diese das Unternehmensportal verwenden können, um ihre Geräte zu registrieren und auf Ressourcen wie Unternehmens-Apps und -E-Mails zuzugreifen. Die Konfiguration der Geschäftsbedingungen ist optional.

Sie können mehrere Sätze von Bedingungen erstellen und diese verschiedenen Gruppen zuweisen, um z. B. verschiedene Sprachen zu unterstützen.

## <a name="create-terms-and-conditions"></a>Erstellen von Geschäftsbedingungen
Führen Sie die folgenden Schritte aus, um Geschäftsbedingungen zu erstellen. Der Anzeigename und die Beschreibung sind für administrative Zwecke vorgesehen, während die Eigenschaften der Bedingungen den Benutzern im Unternehmensportal angezeigt werden.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Geräteregistrierung** und dann auf **Geschäftsbedingungen**.
2. Wählen Sie **Erstellen** aus.
![Screenshot: Azure-Portal mit Schaltfläche zum Erstellen von Geschäftsbedingungen](media/terms-create-terms.png)
3. Geben Sie auf im erweiterten Bereich die folgenden Informationen an:

   - **Anzeigename**: Die Bezeichnung für die Bedingungen im Azure-Portal. Diese Bezeichnung wird den Benutzern nicht angezeigt.

   - **Beschreibung**: Optionale Details, die Ihnen dabei helfen, diese Bedingungen im Azure-Portal zu identifizieren.

4. Klicken Sie auf den Pfeil neben **Define terms of use** (Nutzungsbedingungen definieren), um den Bereich „Nutzungsbedingungen“ zu öffnen, und geben Sie dann die folgende Informationen ein:

   ![Screenshots des Bildschirms mit der Akzeptanz von Nutzungsbedingungen für Endbenutzer mit der Zusammenfassung der Nutzungsbedingungen](./media/terms-summary-create.png)

   - **Titel**: Der Name für Ihre Bedingungen, die Benutzern im Unternehmensportal oberhalb der **Zusammenfassung** angezeigt werden.
   - **Zusammenfassung der Nutzungsbedingungen**: Text, aus dem hervorgeht, welche Folgen die Annahme der Bedingungen für den Benutzer hat. Beispiel: Durch die Registrierung Ihres Geräts stimmen Sie den von Contoso dargelegten Nutzungsbedingungen zu. Lesen Sie die Bedingungen sorgfältig durch, bevor Sie fortfahren.
   - **Geschäftsbedingungen**: Die Geschäftsbedingungen, die den Benutzern angezeigt und von ihnen angenommen oder abgelehnt werden müssen.

5. Wählen Sie **OK** und dann **Erstellen** aus.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Darstellung der Nutzungsbedingungen für die Benutzer
Das folgende Beispiel zeigt **Titel** und **Zusammenfassung der Nutzungsbedingungen** in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot von „Titel“ und „Zusammenfassung der Nutzungsbedingungen“ in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-summary-terms.png)

Das folgende Beispiel zeigt die Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.

![Screenshot der Geschäftsbedingungen in der Verwaltungskonsole und im Unternehmensportal.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Zuweisen von Geschäftsbedingungen

Sie können Geschäftsbedingungen zu Benutzergruppen zuweisen, die diese vor der Verwendung des Unternehmensportals annehmen müssen.

1. Wählen Sie im Azure-Portal die Option **Geräteregistrierung** und dann **Geschäftsbedingungen** aus.
2. Wählen Sie in der Liste der Geschäftsbedingungen die Bedingungen aus, die Sie zuweisen möchten, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.
![Screenshot des Bereichs „Gruppe zuweisen“ im Azure-Portal, das die Schaltflächen „Gruppe auswählen“ und „Auswählen“ für die Zuweisung der Geschäftsbedingungen anzeigt](media/terms-assign-groups.png)
3. Klicken Sie auf die Schaltfläche **Einzuschließende Gruppen auswählen**, und wählen Sie die Gruppen aus, denen Sie die Bedingungen zuweisen möchten. Klicken Sie anschließend auf **Auswählen**. Dynamischen Gruppen können keine Geschäftsbedingungen zugewiesen werden.
4. Klicken Sie im Bereich **Zugewiesene Gruppen** auf **Speichern**.  Die Geschäftsbedingungen werden jetzt den Benutzern in den ausgewählten Gruppen zugewiesen. Benutzer werden beim nächsten Zugriff auf das Unternehmensportal zur Annahme der Geschäftsbedingungen aufgefordert. Die Geschäftsbedingungen müssen nur einmal angenommen werden. Benutzer mit mehreren Geräten müssen sie nicht auf jedem Gerät annehmen.


## <a name="monitor-terms-and-conditions"></a>Überwachen der Geschäftsbedingungen

1. Klicken Sie im Azure-Portal auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**. 
1. Klicken Sie im Bereich „Intune“ auf die Option **Geräteregistrierung** und dann auf **Geschäftsbedingungen**.
2. Wählen Sie in der Liste der Geschäftsbedingungen die Bedingungen aus, für die Sie die Annahme anzeigen möchten, und klicken Sie dann auf **Annahmebericht**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeiten mit mehreren Versionen der Nutzungsbedingungen
Sie können Ihre Geschäftsbedingungen bearbeiten und ihre Versionen verwalten. Es wird empfohlen, dass Sie jedes Mal die Versionsnummer erhöhen und die Zustimmung zu den Geschäftsbedingungen anfordern, wenn Sie wichtige Änderungen an den Geschäftsbedingungen vornehmen. Behalten Sie die aktuelle Versionsnummer bei, wenn Sie z. B. Tippfehler korrigieren oder die Formatierung ändern.

1. Klicken Sie im Azure-Portal auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**.

2. Klicken Sie im Bereich „Intune“ auf die Option **Geräteregistrierung** > **Geschäftsbedingungen**, und wählen Sie dann die Geschäftsbedingungen aus, die Sie ändern möchten. Klicken Sie anschließend auf die Option **Eigenschaften**.

4. Klicken Sie im Bereich **Eigenschaften** auf die Option **Geschäftsbedingungen**, und ändern Sie bei Bedarf **Titel**, **Summary of Terms** (Zusammenfassung der Nutzungsbedingungen) und **Geschäftsbedingungen**. Wenn es die von Ihnen vorgenommenen Änderungen für Benutzer erforderlich machen, die neuen Bedingungen erneut anzunehmen, klicken Sie auf **Fordert eine erneute Annahme durch die Benutzer an und erhöht die Versionsnummer auf**.

4.  Wählen Sie **OK** und dann **Speichern** aus.

Benutzer müssen die aktualisierten Geschäftsbedingungen nur einmal annehmen. Benutzer mit mehreren Geräten müssen die Geschäftsbedingungen nicht auf jedem Gerät annehmen.
