---
title: Hinzufügen von Microsoft Defender ATP zu macOS-Geräten mit Microsoft Intune
titleSuffix: ''
description: Hier erfahren Sie, wie Sie mit Microsoft Intune Microsoft Defender ATP zu macOS-Geräten hinzufügen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569559"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Hinzufügen von Microsoft Defender ATP zu macOS-Geräten mit Microsoft Intune

Bevor Sie Apps bereitstellen, konfigurieren, überwachen oder schützen können, müssen Sie sie zu Intune hinzufügen. Einer der verfügbaren [App-Typen](~/apps/apps-add.md#app-types-in-microsoft-intune) ist Microsoft Defender Advanced Threat Protection (ATP). Wenn Sie den App-Typ in Intune auswählen, können Sie Microsoft Defender ATP zuweisen und auf Geräten mit macOS installieren. Dieser App-Typ erleichtert Ihnen das Zuweisen von Microsoft Defender ATP zu macOS-Geräten, ohne dass Sie das macOS App Wrapping Tool verwenden müssen. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um die App sicherer und auf dem neuesten Stand zu halten.

## <a name="prerequisites"></a>Voraussetzungen
- Auf dem macOS-Gerät muss macOS 10.13 oder höher ausgeführt werden.
- Auf dem macOS-Gerät müssen mindestens 650 MB Speicherplatz vorhanden sein.
- Stellen Sie die Kernelerweiterung in Intune bereit. Weitere Informationen finden Sie unter [Hinzufügen von macOS-Kernelerweiterungen in Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> Die Kernelerweiterung kann nur dann automatisch genehmigt werden, wenn sie vor der Installation der Microsoft Defender ATP-App auf dem Gerät vorhanden ist. Andernfalls wird die Meldung "System extension blocked" (Systemerweiterung blockiert) auf Macs angezeigt. Sie müssen die Erweiterung genehmigen, indem Sie zu **Security Preferences** (Sicherheitseinstellungen) oder **System Preferences** > **Datenschutz und Sicherheit** (Systemeinstellungen) navigieren und dann auf **Zulassen** klicken. Weitere Informationen finden Sie unter [Beheben von Problemen bei der Kernelerweiterung in Microsoft Defender ATP für Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Hinzufügen von Microsoft Defender ATP zu Intune
Sie können Microsoft Defender ATP mithilfe der folgenden Schritte zu Intune hinzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie in der Liste **App-Typ** unter **Microsoft Defender ATP** die Option **macOS** aus.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen
In diesem Schritt stellen Sie Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.

1. Klicken Sie auf **App-Informationen**, um den Bereich **App-Informationen** anzuzeigen.
2. Stellen Sie im Bereich **App-Informationen** Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. Beispielsweise können Sie die Zielbenutzer in der Beschreibung auflisten.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option aus, um die App auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
3. Klicken Sie auf **OK**.

## <a name="select-scope-tags-optional"></a>Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter „Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT“.
1.  Wählen Sie **Scope (Tags)** > **Add** (Bereich (Markierungen) > Hinzufügen) aus.
2.  Verwenden Sie das Feld **Auswählen**, um nach Bereichsmarkierungen zu suchen.
3.  Aktivieren Sie das Kontrollkästchen neben den Bereichsmarkierungen, die Sie dieser App zuweisen möchten.
4.  Klicken Sie auf **Auswählen** > **OK**.

## <a name="add-the-app"></a>Hinzufügen der App
Wenn Sie die Konfiguration abgeschlossen haben, wählen Sie **Hinzufügen** im Bereich **App hinzufügen** aus. 

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

> [!NOTE]
> Apple bietet derzeit keine Möglichkeit, Microsoft Defender ATP auf macOS-Geräten mit Intune zu deinstallieren.

## <a name="next-steps"></a>Nächste Schritte
- Informationen zum Konfigurieren von Microsoft Defender ATP auf macOS-Geräten finden Sie unter [Konfigurieren von Microsoft Defender ATP auf macOS-Geräten](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Informationen zum Ein- und Ausschließen von App-Zuweisungen für Gruppen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](~/apps/apps-inc-exl-assignments.md).
- [Das Zuweisen von Apps zu Gruppen](~/apps/apps-deploy.md)

