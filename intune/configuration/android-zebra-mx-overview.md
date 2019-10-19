---
title: 'Verwenden von Zebra Mobility Extensions auf Android-Geräten in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Verwenden Sie Microsoft Intune, um Zebra-Geräte mit Android mit Zebra Mobility Extensions (MX) zu verwalten und zu nutzen. Erfahren Sie mehr über alle Schritte, einschließlich Installation der Unternehmensportal-App, Querladen der App, Zuweisen der Rolle „Geräteadministrator“, Erstellen eines StageNow-Profils und mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13e5e7d49ec7e808f7cb5ba419dc881717539564
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72496041"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Nutzen und Verwalten von Zebra-Geräten mithilfe von Zebra Mobility Extensions in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune bietet eine Vielzahl von Funktionen, u.a. für die Verwaltung von Apps und Konfiguration von Geräteeinstellungen. Diese integrierten Funktionen und Einstellungen verwalten Android-Geräte der Firma Zebra Technologies („Zebra-Geräte“).

Verwenden Sie auf Android-Geräten die zu **Mobility Extensions (MX)** gehörigen Profile, um weitere Zebra-spezifische Einstellungen anzupassen oder hinzuzufügen.

Dieser Artikel zeigt, wie Sie in Microsoft Intune Zebra Mobility Extensions (MX) auf Zebra-Geräten verwenden können.

Diese Funktion gilt für:

- Android

Ihr Unternehmen kann Zebra-Geräte im Einzelhandel, in der Fertigung und in anderen Umgebungen nutzen. Angenommen, Sie sind ein Einzelhändler mit einer Umgebung, in der tausende mobiler Zebra-Geräte von Verkäufern genutzt werden. Intune kann Ihnen helfen, diese Geräte im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) zu verwalten.

Mit Intune können Sie Zebra-Geräte registrieren, um Ihre branchenspezifischen Apps auf den Geräten bereitzustellen. Mit Profilen des Typs „Gerätekonfiguration“ können Sie MX-Profile erstellen, um Ihre Zebra-spezifischen Einstellungen zu verwalten.

> [!NOTE]
> Standardmäßig sind die Zebra MX-APIs auf Geräten nicht gesperrt. Bevor ein Gerät bei InTune registriert wird, ist es möglich, dass das Gerät bösartig kompromittiert werden kann. Wenn sich das Gerät in einem sauberen Zustand befindet, empfehlen wir Ihnen, MX-APIs mithilfe des Zugriffs-Managers (accessmgr) zu sperren. Sie können z. b. auswählen, dass nur die Unternehmensportal-APP und die apps, denen Sie Vertrauen, MX-APIs anrufen dürfen.
>
> Weitere Informationen finden Sie unter [Sperren Ihres Geräts](https://developer.zebra.com/community/home/blog/2017/04/11/locking-down-your-device) auf der Website von Zebra.

## <a name="before-you-begin"></a>Vorbereitung

- Achten Sie darauf, dass Sie die neueste Version der Desktop-App StageNow von Zebra Technologies einsetzen.
- Überprüfen Sie unbedingt die vollständige [MX-Funktionsmatrix](http://techdocs.zebra.com/mx/compatibility) von Zebra (öffnet die Website von Zebra), um sicherzustellen, dass die von Ihnen erstellten Profile mit der MX- und Betriebssystemversion sowie dem Modell des Gerätes kompatibel sind.
- Bestimmte Geräte, wie beispielsweise TC20/25-Geräte, unterstützen nicht alle in StageNow verfügbaren MX-Funktionen. Sehen Sie sich die [Funktionsmatrix von Zebra](http://techdocs.zebra.com/mx/tc2x/) an (öffnet die Website von Zebra), in der Sie aktualisierte Supportinformationen finden.

## <a name="step-1-install-the-latest-company-portal-app"></a>Schritt 1: Installieren der aktuellen Unternehmensportal-App

Öffnen Sie auf dem Gerät den Google Play Store. Laden Sie die Intune-Unternehmensportal-App von Microsoft herunter, und installieren Sie sie. Bei Installation über Google Play erhält die Unternehmensportal-App Updates und Korrekturen automatisch.

Falls Google Play nicht verfügbar ist, laden Sie das [Microsoft Intune-Unternehmensportal für Android](https://www.microsoft.com/download/details.aspx?id=49140) herunter (öffnet eine andere Microsoft-Website), das Sie anschließend [querladen](#sideload-the-company-portal-app) (was in diesem Artikel beschrieben wird). Bei dieser Installation erhält die App nicht Updates oder Korrekturen automatisch. Achten Sie darauf, die App regelmäßig manuell zu aktualisieren und patchen.

### <a name="sideload-the-company-portal-app"></a>Querladen der Unternehmensportal-App

Wenn Sie zum Installieren einer App nicht Google Play verwendet, wird dies als „Querladen“ bezeichnet. Verwenden Sie StageNow zum Querladen der Unternehmensportal-App. 

Die folgenden Schritte bieten eine Übersicht. Spezifische Details finden Sie in der Zebra-Dokumentation. [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (öffnet die Website von Zebra) ist ggf. eine geeignete Ressource.

1. Erstellen Sie in StageNow ein Profil zur **Registrierung bei einer MDM-Lösung**.
2. Wählen Sie in **Deployment** das Herunterladen der MDM-Agent-Datei aus.
3. Legen Sie die Schritte **Support App** und **Download Configuration** auf **No** fest.
4. Wählen Sie in **Download MDM** den Befehl **Transfer/Copy File** aus. Fügen Sie Quelle und Ziel des Android-Pakets (APK) für das Unternehmensportal hinzu.
5. Übernehmen Sie in **Launch MDM** die Standardwerte unverändert. Fügen Sie folgende Details hinzu:

    - **Paketname**: `com.microsoft.windowsintune.companyportal`
    - **Klassenname**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Fahren Sie mit der Veröffentlichung des Profils fort, und nutzen Sie es mit der StageNow-App auf dem Gerät. Die Unternehmensportal-App wird auf dem Gerät installiert und geöffnet.

> [!TIP]
> Weitere Informationen zu StageNow und seinen Aufgaben finden Sie unter [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (öffnet die Zebra-Website).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Schritt 2: Bestätigen, dass die Unternehmensportal-App die Rolle „Geräteadministrator“ hat

Die Unternehmensportal-App erfordert zum Verwalten von Android-Geräten die Rolle „Geräteadministrator“. Zum Aktivieren der Rolle „Geräteadministrator“ bieten einige Zebra-Geräte eine Benutzeroberfläche auf dem Gerät. Wenn das Gerät eine Benutzeroberfläche aufweist, fordert die Unternehmensportal-App den Endbenutzer auf, während der [Registrierung](#step-3-enroll-the-device-in-to-intune) die Rolle „Geräteadministrator“ zu gewähren (siehe diesen Artikel).

Wenn keine Benutzeroberfläche verfügbar ist, verwenden Sie den **DevAdmin Manager** in StageNow, um ein Profil zu erstellen, das der Unternehmensportal-App manuell die Rolle „Geräteadministrator“ gewährt.

Die folgenden Schritte bieten eine Übersicht. Spezifische Details finden Sie in der Zebra-Dokumentation. 
[Set battery swap mode as device administrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (öffnet die Website von Zebra) ist ggf. eine geeignete Ressource.

1. Erstellen Sie in StageNow ein Profil, und wählen Sie **Xpert Mode** aus.
2. Fügen Sie dem Profil **DevAdmin Manager** hinzu.
3. Legen Sie **Device Administration Action** auf **Turn On as Device Administrator** fest.
4. Legen Sie **Device Admin Package Name** auf `com.microsoft.windowsintune.companyportal` fest.
5. Legen Sie **Device Admin Class Name** auf `com.microsoft.omadm.client.PolicyManagerReceiver` fest.

Fahren Sie mit der Veröffentlichung des Profils fort, und nutzen Sie es mit der StageNow-App auf dem Gerät. Der Unternehmensportal-App wurde die Rolle „Geräteadministrator“ gewährt.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Schritt 3: Registrieren des Geräts bei Intune

Nach Abschluss der ersten beiden Schritte ist die Unternehmensportal-App auf dem Gerät installiert. Das Gerät kann nun bei Intune registriert werden.

Unter [Registrieren von Android-Geräten](../enrollment/android-enroll.md) sind die Schritte aufgeführt. Wenn Sie über zahlreiche Zebra-Geräte verfügen, können Sie ein [Geräteregistrierungs-Manager-Konto](../enrollment/device-enrollment-manager-enroll.md) verwenden. Bei Verwenden eines solchen Kontos wird die Option zum Aufheben der Registrierung in der Unternehmensportal-App entfernt, sodass Benutzer die Registrierung des Geräts nicht ohne Weiteres aufheben können.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Schritt 4: Erstellen eines Geräteverwaltungsprofils in StageNow

Erstellen Sie in StageNow ein Profil zum Konfigurieren der Einstellungen, die Sie auf dem Gerät verwalten möchten. Spezifische Details finden Sie in der Zebra-Dokumentation. [Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (öffnet die Zebra-Website) ist möglicherweise eine geeignete Ressource.

Wenn Sie das Profil in StageNow erstellen, wählen Sie im letzten Schritt **Export to MDM** aus. In diesem Schritt wird eine XML-Datei generiert. Speichern Sie diese Datei. Sie benötigen sie in einem späteren Schritt.

- Es wird empfohlen, das Profil zu testen, bevor Sie es auf Geräten in Ihrer Organisation bereitstellen. Verwenden Sie zum Testen im letzten Schritt beim Erstellen von Profilen mit StageNow auf Ihrem Computer die Optionen unter **Test**. Verwenden Sie dann die von StageNow generierte Datei in der StageNow-App auf dem Gerät.

  Die StageNow-App auf dem Gerät zeigt Protokolle, die beim Testen des Profils erstellt wurden. Unter [Verwenden von StageNow-Protokollen auf Zebra-Geräten mit Android in Intune](android-zebra-mx-logs-troubleshoot.md) erfahren Sie, wie Sie mithilfe von StageNow-Protokollen Fehler verstehen können.

- Wenn Sie in Ihrem StageNow-Profil auf Anwendungen verweisen, Pakete aktualisieren oder andere Dateien aktualisieren, sollen diese Updates dem Gerät zur Verfügung gestellt werden. Um die Updates zu erhalten, muss sich das Gerät mit dem StageNow-Bereitstellungsserver verbinden, nachdem das Profil zugewiesen wurde. 

  Oder Sie können integrierte Funktionen in Intune verwenden, um diese Änderungen zu erhalten, einschließlich:

  - App-Verwaltungsfunktionen zum [Hinzufügen](../apps/apps-add.md), [Bereitstellen](../apps/apps-deploy.md), Aktualisieren und [Überwachen](../apps/apps-monitor.md) von Apps.
  - Verwalten von [System- und App-Updates](device-restrictions-android-for-work.md#device-owner-only) auf Geräten mit Android Enterprise

Nachdem Sie die Datei getestet haben, ist der nächste Schritt die Bereitstellung des Profils auf Geräten mithilfe von Intune.

- Sie können ein oder mehrere MX-Profile auf einem Gerät bereitstellen.
- Sie können auch mehrere stagenow-Profile exportieren und die Einstellungen in einer einzelnen XML-Datei kombinieren. Anschließend laden Sie die XML-Datei in InTune hoch, um Sie auf Ihren Geräten bereitzustellen.

  > [!WARNING]
  > Wenn mehrere MX-Profile auf dieselbe Gruppe abzielen und dieselbe Eigenschaft konfigurieren, treten Konflikte auf dem Gerät auf.
  >
  > Wenn die gleiche Eigenschaft mehrmals in einem einzelnen MX-Profil konfiguriert ist, gewinnt die letzte Konfiguration.

## <a name="step-5-create-a-profile-in-intune"></a>Schritt 5: Erstellen eines Profils in Intune

Erstellen Sie in Intune ein Gerätekonfigurationsprofil:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Android** aus.
    - **Profiltyp**: Wählen Sie **MX-Profil (nur Zebra)** aus.

4. Fügen Sie in **MX-Profil im XML-Format** die XML-Profildatei hinzu, [die Sie aus StageNow exportiert](#step-4-create-a-device-management-profile-in-stagenow) haben (siehe diesen Artikel).
5. Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. Die Richtlinie wird erstellt und in der Liste angezeigt.

    > [!TIP]
    > Aus Sicherheitsgründen wird der XML-Text des Profils nach dem Speichern nicht angezeigt. Der Text ist verschlüsselt, weshalb Sie nur Sternchen (`****`) sehen. Zu Ihrer Information: Es wird empfohlen, Kopien der MX-Profile zu speichern, bevor Sie sie Intune hinzufügen.

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Wenn das Gerät das nächste Mal nach Konfigurationsaktualisierungen sucht, wird das MX-Profil auf dem Gerät bereitgestellt. Geräte werden bei der Registrierung bei Intune und dann etwa alle 8 Stunden synchronisiert. Sie können [in Intune auch eine Synchronisierung erzwingen](../remote-actions/device-sync.md). Oder öffnen Sie auf dem Gerät die **Unternehmensportal-App** > **Einstellungen** > **Synchronisierung**. 

## <a name="update-a-zebra-mx-configuration-after-its-assigned"></a>Aktualisieren einer Konfiguration von Zebra MX, nachdem Sie zugewiesen wurde

Zum Aktualisieren der MX-spezifischen Konfiguration eines Zebra Geräts können Sie folgende Aktionen ausführen: 

- Erstellen Sie eine aktualisierte stagenow-XML-Datei, bearbeiten Sie das vorhandene InTune MX-Profil, und laden Sie die neue stagenow-XML-Datei hoch. Diese neue Datei überschreibt die vorherige Richtlinie im Profil und ersetzt die vorherige Konfiguration.
- Erstellen Sie eine neue stagenow-XML-Datei, mit der unterschiedliche Einstellungen konfiguriert werden, ein neues InTune MX-Profil erstellt wird, die neue stagenow-XML-Datei hochgeladen und derselben Gruppe zugewiesen wird. Es werden mehrere Profile bereitgestellt. Wenn das neue Profileinstellungen konfiguriert, die bereits in vorhandenen Profilen vorhanden sind, treten Konflikte auf.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
- [Behandeln von Problemen mit Zebra-Geräten mithilfe von StageNow-Protokollen](android-zebra-mx-logs-troubleshoot.md).
