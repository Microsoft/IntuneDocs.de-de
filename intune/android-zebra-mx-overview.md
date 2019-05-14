---
title: Verwenden von Zebra Mobility-Erweiterungen auf Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Microsoft Intune die Verwaltung und Verwendung von Zebra Android-Geräte mit Zebra Mobility Extensions (MX). Finden Sie alle Schritte, einschließlich installieren die Unternehmensportal-app Sideloaden der app, Gerät-Administratorrolle zuweisen, erstellen Sie ein Profil StageNow und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69814b91978aa3cd74c4dc239b099883ae402af9
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764770"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Verwenden und Verwalten von Zebra-Geräten mit Zebra Mobility-Erweiterungen in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune umfasst einen umfangreichen Satz von Funktionen, einschließlich apps verwalten und Konfigurieren von Einstellungen für Geräte. Diese integrierten Funktionen und Einstellungen werden zum Verwalten von Android-Geräte von Zebra Technologies, auch bekannt als "Zebra Geräte" hergestellt werden.

Auf Android-Geräten verwenden **Mobility-Erweiterungen (MX)** Profile anpassen oder Hinzufügen weiterer Zebra-spezifischen Einstellungen.

Dieser Artikel veranschaulicht die Zebra Mobility Extensions (MX) auf Zebra-Geräte in Microsoft Intune verwenden.

Diese Funktion gilt für:

- Android

Ihr Unternehmen möglicherweise Zebra-Geräte für den Einzelhandel, in der Fabrik und vieles mehr verwenden. Beispielsweise haben einen Händler, und Ihre Umgebung enthält Tausende von Zebra mobile Geräte, die Vertriebsmitarbeiter. Intune kann helfen, diese Geräte als Teil Ihrer Lösung für mobile Geräte (MDM) verwalten.

Zebra-Geräte, um Ihre Line-of-Business-apps auf den Geräten bereitstellen können Sie mithilfe von Intune registrieren. "Gerätekonfiguration" Profilen können Sie die MX-Profile zum Verwalten Ihrer Zebra-spezifischen Einstellungen zu erstellen.

## <a name="before-you-begin"></a>Vorbereitung

- Achten Sie darauf, dass Sie die neueste Version der StageNow desktop-app aus Zebra Technologies haben.
- Sehen Sie sich [Zebra des vollständigen MX-featurematrix](http://techdocs.zebra.com/mx/compatibility) (öffnet die Zebra-Website), die Sie erstellen Profile sind kompatibel mit MX-Version, Version des Betriebssystems und Modell des Geräts zu bestätigen.
- Im StageNow unterstützt nicht einige Geräte wie TC20/25 Geräten aller verfügbaren MX-Features. Sehen Sie sich [Zebra featurematrix](http://techdocs.zebra.com/mx/tc2x/) (öffnet die Zebra-Website) für die aktualisierte Supportinformationen.

## <a name="step-1-install-the-latest-company-portal-app"></a>Schritt 1: Installieren Sie die aktuelle Unternehmensportal-app

Wechseln Sie zu Google Play Store, auf dem Gerät herunterladen Sie und installieren Sie die Intune-Unternehmensportal-app von Microsoft. Wenn von Google Play installiert haben, die Unternehmensportal-app ruft Updates ab, und Sie werden automatisch behoben.

Wenn Sie Google Play nicht verfügbar ist, laden Sie die [Microsoft Intune-Unternehmensportal für Android](https://www.microsoft.com/download/details.aspx?id=49140) (öffnet eine andere Microsoft-Website), und [querladen es](#sideload-the-company-portal-app) (in diesem Artikel). Bei der Installation auf diese Weise wird die app keine Updates empfangen, oder automatisch korrigiert. Sie sollten regelmäßig aktualisieren und Patchen die app manuell.

### <a name="sideload-the-company-portal-app"></a>Querladen der Unternehmensportal-App

"Sideloaden" ist, wenn Sie Google Play verwenden, um eine app zu installieren. Verwenden Sie zum Sideloaden der Unternehmensportal-app StageNow. 

Die folgenden Schritte bieten eine Übersicht über. Spezifische Details finden Sie in der Zebra-Dokumentation. [Registrieren Sie sich für eine MDM-Lösung mit StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (öffnet die Zebra-Website) ist möglicherweise eine gute Ressource.

1. In StageNow, erstellen Sie ein Profil für **beim Registrieren einer MDM-Lösung**.
2. In **Bereitstellung**, wählen Sie die MDM-Agent-Datei herunterladen.
3. Legen Sie die **Unterstützung App** und **Konfiguration herunterladen** Schritte aus, um **keine**.
4. In **herunterladen MDM**Option **Übertragung/Copy File**. Fügen Sie die Quelle und Ziel des Unternehmens-Portal Android (APK)-Pakets.
5. In **starten MDM**, übernehmen Sie die Standardwerte als-ist. Fügen Sie folgende Details hinzu:

    - **Paketname**: `com.microsoft.windowsintune.companyportal`
    - **Klassenname**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Veröffentlichen das Profil und nutzen es mit der StageNow-app auf dem Gerät weiter. Die Unternehmensportal-app ist installiert und auf dem Gerät geöffnet.

> [!TIP]
> Weitere Informationen zu StageNow und welche Aktion er ausführt, finden Sie unter [StageNow Android-Gerät Staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (öffnet die Zebra-Website).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Schritt 2: Vergewissern Sie sich, dass die Unternehmensportal-app geräteadministratorrolle verfügt

Die Unternehmensportal-app erfordert Geräteadministrator auf Android-Geräte verwalten. Um der Administratorrolle von Gerät zu aktivieren, enthalten einige Geräte Zebra eine Benutzeroberfläche (UI) auf dem Gerät. Wenn das Gerät über eine Benutzeroberfläche enthält, fordert der Unternehmensportal-app den Endbenutzer Geräteadministrator während gewähren [Registrierung](#step-3-enroll-the-device-in-to-intune) (in diesem Artikel).

Wenn eine Benutzeroberfläche nicht verfügbar ist, verwenden Sie die **DevAdmin Manager** in StageNow ein Profil zu erstellen, der Unternehmensportal-app manuell Geräteadministrator gewährt.

Die folgenden Schritte bieten eine Übersicht über. Spezifische Details finden Sie in der Zebra-Dokumentation. 
[Set-Austausch Akkustand als Geräteadministrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (öffnet die Zebra-Website) ist möglicherweise eine gute Ressource.

1. Klicken Sie im StageNow, erstellen Sie ein Profil, und wählen Sie **Xpert Modus**.
2. Hinzufügen **DevAdmin Manager** für das Profil.
3. Legen Sie **Verwaltung Geräteaktion** zu **als Geräteadministrator aktivieren**.
4. Legen Sie **Admin-Paket-Name des Geräts** zu `com.microsoft.windowsintune.companyportal`.
5. Legen Sie **Gerät Admin-Klassenname** zu `com.microsoft.omadm.client.PolicyManagerReceiver`.

Veröffentlichen das Profil und nutzen es mit der StageNow-app auf dem Gerät weiter. Die Unternehmensportal-app erhält die Gerät-Administratorrolle.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Schritt 3: Registrieren des Geräts in Intune

Nach Abschluss der ersten beiden Schritte ist die Unternehmensportal-app auf dem Gerät installiert. Das Gerät kann bei Intune registriert werden.

[Registrieren von Android-Geräten](android-enroll.md) sind die Schritte aufgeführt. Wenn Sie viele Zebra Geräte verfügen, Sie möchten verwenden eine [geräteregistrierungs-Manager (DEM) Konto](device-enrollment-manager-enroll.md). Mit einem geräteregistrierungs-Manager-Konto entfernt auch die Option zum Aufheben der Registrierung der Unternehmensportal-App, damit Benutzer die Registrierung des Geräts als einfach aufheben können nicht.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Schritt 4: Erstellen eines geräteprofils für die Verwaltung in StageNow

Verwenden Sie StageNow zum Erstellen eines Profils, das die Einstellungen konfiguriert werden, die Sie auf dem Gerät verwalten möchten. Spezifische Details finden Sie in der Zebra-Dokumentation. [Profile](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (öffnet die Zebra-Website) ist möglicherweise eine gute Ressource.

Wenn Sie das Profil in StageNow, im letzten Schritt erstellen, wählen Sie **exportieren in MDM**. Dadurch wird eine XML-Datei generiert. Speichern Sie diese Datei. Sie benötigen ihn in einem späteren Schritt.

> [!TIP]
> Es wird empfohlen, um das Profil zu testen, bevor Sie es in Ihrer Organisation für Geräte bereitstellen. Verwenden Sie zum Testen, in der letzte Schritt beim Erstellen von Profilen mit StageNow auf Ihrem Computer die **testen** Optionen. Klicken Sie dann nutzen Sie die StageNow generierte Datei mit der StageNow-app, die auf dem Gerät. 
> 
> Die StageNow-app auf dem Gerät zeigt Protokolle generiert, wenn Sie das Profil zu testen. [Verwendung StageNow anmeldet Zebra Android-Geräte in Intune](android-zebra-mx-logs-troubleshoot.md) enthält Informationen zur Verwendung von StageNow Protokolle zu Fehlern.

> [!NOTE]
> Wenn Sie apps zu verweisen, Pakete aktualisieren, oder anderer Dateien in Ihrem Profil StageNow aktualisieren, möchten Sie das Gerät aus, um diese Updates zu erhalten. Um die Updates zu erhalten, muss das Gerät auf den Bereitstellungsserver StageNow verbinden, wenn das Profil angewendet wird. 
> 
> Alternativ können Sie integrierte Funktionen in Intune erhalten diese Änderungen, einschließlich: 
> - App-Verwaltung von Funktionen auf [hinzufügen](apps-add.md), [bereitstellen](apps-deploy.md), aktualisieren und [Monitor](apps-monitor.md) apps.
> - Verwalten von [System- und app-Updates](device-restrictions-android-for-work.md#device-owner-only) auf Geräten ausgeführt Android Enterprise

Nachdem Sie die Datei getestet haben, wird im nächste Schritt zum Bereitstellen des Profils für Geräte mit Intune.

> [!NOTE]
> Stellen Sie ein Profil für jedes Gerät bereit. Wenn es mehrere StageNow Profile, die Sie auf den Geräten bereitstellen möchten, klicken Sie dann exportieren Sie die Profile StageNow, und kombinieren Sie die Einstellungen in einer einzelnen XML-Datei, bevor Sie sie zu Intune hinzufügen. 
> 
> Sie sollten nicht zwei Einstellungen, die die gleiche Eigenschaft in der gleichen XML-Datei zu konfigurieren. Das Ziel ist, um Konflikte zwischen Einstellungen auf dem Gerät zu verhindern.

## <a name="step-5-create-a-profile-in-intune"></a>Schritt 5: Erstellen Sie ein Profil in Intune

Erstellen Sie in Intune ein Gerätekonfigurationsprofil:

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Android** aus.
    - **Profiltyp**: Wählen Sie **MX-Profils (nur Zebra)**.

4. In **MX-Profil im XML-Format**, fügen Sie die XML-Profildatei [Sie von StageNow exportiert](#step-4-create-a-device-management-profile-in-stagenow) (in diesem Artikel).
5. Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Die Richtlinie wird erstellt und in der Liste angezeigt.

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Das nächste Mal das Gerät eincheckt Updates für die Konfiguration, wird das MX-Profil auf dem Gerät bereitgestellt. Geräte mit Intune synchronisieren, wenn Geräte registrieren, und klicken Sie dann etwa alle 8 Stunden. Sie können auch [erzwingen, dass eine Synchronisierung unter Intune](device-sync.md). Oder öffnen Sie auf dem Gerät die **Unternehmensportal-app** > **Einstellungen** > **Sync**. 

> [!TIP]
> - Aus Sicherheitsgründen nicht das Profil-XML-Text angezeigt werden, nachdem Sie ihn gespeichert. Der Text ist verschlüsselt, und Sie sehen nur Sternchen (`****`). Zu Referenzzwecken wird empfohlen, speichern Kopien der MX-Profile aus, bevor Sie diese Intune hinzufügen.
> 
> - Um ein Profil zu aktualisieren, nachdem er Zebra Geräten zugewiesen ist, erstellen Sie eine aktualisierte StageNow XML-Datei, bearbeiten Sie das vorhandene Intune-Profil und fügen Sie die neue StageNow XML-Datei hinzu. Diese neue Datei überschreibt die vorherige StageNow-Richtlinie im Profil.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
- [Verwenden Sie StageNow-Protokolle zur Problembehandlung Zebra Geräte](android-zebra-mx-logs-troubleshoot.md).
