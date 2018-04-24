---
title: Richtlinieneinstellungen für Geschäftsbedingungen
description: Sie können Intune-Nutzungsbedingungen für Benutzergruppen bereitstellen, um zu erläutern, wie sich die Registrierung, der Zugriff auf Arbeitsressourcen und die Verwendung des Unternehmensportals auf Geräte und Benutzer auswirken.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6edf0ac1-4f46-4543-a9e5-f484ac37e9a5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e639b603e52df621cddaaf9490773336229fc6a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="terms-and-condition-policy-settings-in-microsoft-intune"></a>Einstellungen für Nutzungsbedingungsrichtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können Intune-Nutzungsbedingungen für Benutzergruppen bereitstellen, um zu erläutern, wie sich die Registrierung, der Zugriff auf Arbeitsressourcen und das Unternehmensportal auf Geräte und Benutzer auswirken. Benutzer müssen die Nutzungsbedingungen akzeptieren, bevor sie sich über das Unternehmensportal registrieren und auf ihre Arbeit zugreifen können.

Sie können mehrere Richtlinien erstellen und bereitstellen, die verschiedene Nutzungsbedingungen enthalten. Sie können auch Versionen derselben Nutzungsbedingungen in verschiedenen Sprachen erstellen und diese dann für die entsprechenden Gruppen bereitstellen.

## <a name="create-a-terms-and-conditions-policy"></a>Erstellen einer Nutzungsbedingungsrichtlinie

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** &gt; **Nutzungsbedingungen**.

    ![Screenshot für Nutzungsbedingungsrichtlinien](./media/pol-sa-terms-conditions.png)

2.  Klicken Sie auf **Hinzufügen**, um eine neue Nutzungsbedingungsrichtlinie zu erstellen.

    Sie können auch eine vorhandene Richtlinie **bearbeiten** oder **löschen**.

3.  Geben Sie auf der Seite zum **Erstellen der Nutzungsbedingungen** die folgenden Informationen an:

    -   **Name**&mdash;Ein eindeutiger Richtlinienname, der in der Intune-Konsole angezeigt wird.

    -   **Beschreibung**&mdash;Details, die Ihnen dabei helfen, die Richtlinie in der Intune-Konsole zu identifizieren.

    -   **Titel**&mdash;Der Titel, der Benutzern im Unternehmensportal angezeigt wird.

    -   **Text zur Erläuterung der Bedeutung, wenn der Benutzer zustimmt**&mdash;Die für Benutzer angezeigte Bezeichnung hinsichtlich der Zustimmung. Beispiel: „Ich stimme den Nutzungsbedingungen zu.“

4.  Wenn Sie fertig sind, klicken Sie auf **Speichern**. Die neue Richtlinie wird im Knoten für die **Nutzungsbedingungen** des Arbeitsbereichs **Richtlinie** angezeigt.

## <a name="deploy-a-terms-and-conditions-policy"></a>Bereitstellen einer Nutzungsbedingungsrichtlinie

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** &gt; **Nutzungsbedingungen**.

2.  Wählen Sie in der Liste der **Nutzungsbedingungsrichtlinien** die bereitzustellende Richtlinie aus, und klicken Sie dann auf **Bereitstellung verwalten**.

3.  Wählen Sie im Dialogfeld **Bereitstellung verwalten** die Gruppen aus, für die Sie die Richtlinie bereitstellen möchten, und klicken Sie anschließend auf **OK**.

    Wenn die anvisierten Benutzer auf das Unternehmensportal zugreifen, zeigt Intune die bereitgestellten Nutzungsbedingungen an. Benutzer müssen diese Nutzungsbedingungen akzeptieren, bevor sie Zugriff auf Unternehmensressourcen erhalten.

## <a name="monitor-a-terms-and-conditions-policy"></a>Überwachen einer Nutzungsbedingungsrichtlinie

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** &gt; **Nutzungsbedingungen**.

2.  Klicken Sie im Fenster **Neuen Bericht erstellen** auf **Bericht anzeigen**. Der Bericht wird mit ausführlichen Informationen geöffnet, welche Benutzer die bereitgestellten Nutzungsbedingungen akzeptiert haben.

### <a name="updates-and-version-control-for-terms-and-conditions"></a>Updates und Versionskontrolle für Nutzungsbedingungen
Beim Bearbeiten einer vorhandenen Nutzungsbedingungsrichtlinie können Sie auswählen, welches Verhalten erfolgt, wenn Sie die Richtlinie bereitstellen. Verwenden Sie das folgende Verfahren beim Aktualisieren vorhandener Nutzungsbedingungsrichtlinien.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Arbeiten mit mehreren Versionen der Nutzungsbedingungen

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** &gt; **Nutzungsbedingungen**.

2.  Wählen Sie die zu bearbeitende Nutzungsbedingungsrichtlinie aus, und klicken Sie dann auf **Bearbeiten**.

3.  Nehmen Sie auf der Seite zum **Bearbeiten der Nutzungsbedingungen** alle erforderlichen Änderungen vor, und geben Sie dann an, ob diese neue Version von allen Benutzern eine Zustimmung zu den Nutzungsbedingungen erfordert oder ob sie nur für neue Benutzer angezeigt wird.

    Es wird empfohlen, dass Sie jedes Mal die Versionsnummer erhöhen und die Zustimmung zu den Nutzungsbedingungen anfordern, wenn Sie wichtige Änderungen an der Nutzungsbedingungsrichtlinie vornehmen. Behalten Sie die aktuelle Versionsnummer bei, wenn Sie z. B. Tippfehler korrigieren oder die Formatierung ändern.

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
