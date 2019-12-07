---
title: Hinzufügen von Microsoft Edge für Windows 10 zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Microsoft Edge für Windows 10 zu Microsoft Intune hinzufügen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: b4839340ba1f3bad6f28a1120d882d0f600b1d44
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563565"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Hinzufügen von Microsoft Edge für Windows 10 zu Microsoft Intune

Bevor Sie Apps bereitstellen, konfigurieren, überwachen oder schützen können, müssen Sie sie zu Intune hinzufügen. Einer der verfügbaren [App-Typen](~/apps/apps-add.md#app-types-in-microsoft-intune) ist Microsoft Edge *Version 77 und höher*. Wenn Sie den App-Typ in Intune auswählen, können Sie Microsoft Edge *Version 77 und höher* zuweisen und auf Geräten mit Windows 10 installieren.

> [!IMPORTANT]
> Dieser App-Typ befindet sich in der **öffentlichen Vorschau** und bietet Entwickler- und Beta-Channels für Windows 10 an. Die Bereitstellung ist nur in englischer Sprache verfügbar, Endbenutzer können die Anzeigesprache im Browser jedoch unter **Einstellungen** > **Sprachen** ändern. Microsoft Edge ist eine Win32-App, die im Systemkontext und auf entsprechenden Architekturen (x86-App auf x86-Betriebssystemen und x64-App auf x64-Betriebssystemen) installiert ist. Intune erkennt jegliche vorhandene Microsoft Edge-Installationen. Wenn Microsoft Edge im Benutzerkontext installiert ist, wird es durch eine Systeminstallation überschrieben. Wenn es im Systemkontext installiert ist, wird der Erfolg der Installation gemeldet. Außerdem sind automatische Updates von Microsoft Edge standardmäßig **Aktiviert**, und Microsoft Edge kann nicht deinstalliert werden.

> [!NOTE]
> Microsoft Edge *Version 77 und höher* ist auch für macOS verfügbar.
> 
> Sie können die integrierte Anwendungsbereitstellung von Microsoft Edge für Workplace Join-Computer nicht verwenden. Die integrierte Anwendungsbereitstellung erfordert die Intune-Verwaltungserweiterung, die nur für mit AAD verknüpfte Geräte vorhanden ist. Sie können weiterhin Microsoft Edge *Version 77 und höher* mithilfe einer *MSI-Datei* bereitstellen, die in **Apps** hochgeladen wurde. Weitere Informationen finden Sie unter [Hinzufügen branchenspezifischer Windows-Apps zu Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Voraussetzungen
- Windows 10 RS2 und höher ist erforderlich.
- Alle vorinstallierten Versionen von Microsoft Edge *Version 77 und höher* für **Entwickler-** und **Beta**-Channels im Benutzerkontext werden überschrieben, wenn Edge im Systemkontext installiert ist.

## <a name="configure-the-app-in-intune"></a>Konfigurieren der App in Intune
Mithilfe der folgenden Schritte können Sie Microsoft Edge, Version 77 und höher, zu Intune hinzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie in der Liste **App-Typ** unter **Microsoft Edge, Version 77 und höher** die Option **Windows 10** aus.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen
In diesem Schritt stellen Sie Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.

1. Klicken Sie auf **App-Informationen**, um den Bereich **App-Informationen** anzuzeigen.
2. Stellen Sie im Bereich **App-Informationen** Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Beispielsweise können Sie die Zielbenutzer in der Beschreibung auflisten.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option aus, um die App auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
3. Wählen Sie **OK** aus.

## <a name="configure-app-settings"></a>App-Einstellungen konfigurieren
In diesem Schritt konfigurieren Sie Installationsoptionen für die App.

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Einstellungen** aus.
2. Wählen Sie im Bereich **App-Einstellungen** entweder **Beta** oder **Dev** aus der Liste **Channel** aus, um zu bestimmen, von welchem Edge-Channel Sie die App bereitstellen.
    - Der **Beta**-Channel ist die stabilste Microsoft Edge-Vorschauversion und die beste Wahl für ein vollständiges Pilotprojekt in Ihrer Organisation. Durch größere Updates alle sechs Wochen umfasst jedes Release die Erkenntnisse und Verbesserungen im Dev-Channel.
    - Der **Dev**-Channel ist bereit für Unternehmensfeedback von Windows, Windows Server und macOS. Er wird wöchentlich aktualisiert und enthält die neuesten Verbesserungen und Fehlerbehebungen.

    > [!NOTE]
    > Das Microsoft Edge-Browserlogo wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.

3.  Wählen Sie **OK** aus.

## <a name="select-scope-tags-optional"></a>Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter „Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT“.
1.  Wählen Sie **Scope (Tags)**  > **Add** (Bereich (Markierungen) > Hinzufügen) aus.
2.  Verwenden Sie das Feld **Auswählen**, um nach Bereichsmarkierungen zu suchen.
3.  Aktivieren Sie das Kontrollkästchen neben den Bereichsmarkierungen, die Sie dieser App zuweisen möchten.
4.  Klicken Sie auf **Auswählen** > **OK**.

## <a name="add-the-app"></a>Hinzufügen der App
Wenn Sie die Konfiguration der App abgeschlossen haben, wählen Sie **Hinzufügen** im Bereich **App hinzufügen** aus. 

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

> [!NOTE]
> Wenn Sie derzeit die Zuweisung der Microsoft Edge-Bereitstellung aufheben, bleibt diese auf dem Gerät erhalten.

## <a name="troubleshooting"></a>Problembehandlung
**Microsoft Edge Version 77 und höher für Windows 10:**<br>
Intune verwendet die Intune-Verwaltungserweiterung zum Herunterladen und Bereitstellen des Microsoft Edge-Installers auf zugewiesenen Windows 10-Geräten. Anschließend werden die Bereitstellungseinstellungen an den Microsoft Edge-Installer übermittelt, der den Microsoft Edge-Browser direkt aus dem CDN herunterlädt und installiert. Verweisen Sie auf die [Voraussetzungen für die Intune-Verwaltungserweiterung](~/apps/intune-management-extension.md#prerequisites) und die bewährten Methoden für den Zugriff auf den Azure-Aktualisierungsdienst und das CDN, um sicherzustellen, dass Ihre Netzwerkkonfiguration Windows 10-Geräten den Zugriff auf diese Speicherorte gestattet. Um zur Installation des Browsers den Zugriff auf Installationsdateien von einem CDN zu ermöglichen, müssen Sie außerdem den Zugriff auf Windows Update-Endpunkte zulassen. Weitere Informationen finden Sie unter [Verbindungsendpunkte für Windows 10, Version 1809 verwalten – Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) und [Netzwerkendpunkte für Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Nächste Schritte
- [Das Zuweisen von Apps zu Gruppen](~/apps/apps-deploy.md)
