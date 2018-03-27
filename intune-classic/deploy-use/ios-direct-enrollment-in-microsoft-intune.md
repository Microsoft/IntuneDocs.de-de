---
title: Direkte Registrierung für iOS-Geräte
description: Verwenden Sie den Apple Configurator, um unternehmenseigene iOS-Geräte direkt mit einer vordefinierten Richtlinie zu registrieren, indem Sie sie über USB an einen Mac-Computer anschließen.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 79f720af293b6062e140fac9341f97a55bf598fe
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="directly-enroll-ios-devices-by-using-apple-configurator"></a>Direkte Registrierung von iOS-Geräten mithilfe von Apple Configurator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune unterstützt die Registrierung unternehmenseigener iOS-Geräte mithilfe des Tools [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017), das auf einem Mac-Computer ausgeführt wird. Dieser Prozess setzt das Gerät nicht auf die Werkseinstellungen zurück und registriert das Gerät mit einer vordefinierten Richtlinie. Diese Methode ist für Geräte mit der Einstellung **Keine Benutzeraffinität** vorgesehen und erfordert eine USB-Verbindung des iOS-Geräts mit einem Mac-Computer, um die Registrierung beim Unternehmen einzurichten.

Wenn Sie iOS-Geräte direkt registrieren, können Sie ein Gerät registrieren, ohne die Seriennummer des Geräts abrufen zu müssen. Sie können dem Gerät zu Identifikationszwecken auch einen Namen zuweisen, bevor Intune den Gerätenamen während der Registrierung erfasst. Die Unternehmensportal-App wird für direkt registrierte Geräte nicht unterstützt. Diese Anleitung setzt voraus, dass Sie Apple Configurator 2.0 auf einem Mac-Computer verwenden.

>[!NOTE]
>Diese Registrierungsmethode kann nicht mit dem [Geräteregistrierungs-Manager](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) verwendet werden.

1.  Wenn Sie dies noch nicht getan haben, erstellen Sie ein Registrierungsprofil für iOS-Geräte, die über Apple Configurator registriert werden. Ein Registrierungsprofil für Geräte definiert die Einstellungen für Geräte.

    1.  Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Richtlinie** &gt; **Unternehmensgeräteregistrierung**, und wählen Sie anschließend **Hinzufügen** aus.

        ![Erstellen einer Profilseite für die Geräteregistrierung](../media/pol-sa-corp-enroll.png)

    2.  Geben Sie die Details für die Geräteprofile ein:

        -   **Name** : Name des Geräteregistrierungsprofils. Für Benutzer nicht sichtbar.

        -   **Beschreibung**: Beschreibung des Geräteregistrierungsprofils. Für Benutzer nicht sichtbar.

        -   **Benutzerzuweisung**: Gibt an, wie Geräte registriert werden. Wählen Sie für die direkte Registrierung **Keine Benutzeraffinität**aus.

        -   **Gerätegruppe-Vorabzuweisung**: Alle Geräte mit diesem Profil gehören anfänglich zu dieser Gruppe. Sie können die Geräte nach der Registrierung erneut zuweisen.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Wählen Sie **Profil speichern**, um das Profil hinzuzufügen.

5.  Exportieren Sie ein Profil als MOBILECONFIG-Datei zum Bereitstellen auf iOS-Geräten:

    1.   Wählen Sie das Geräteprofil aus, das Sie erstellt haben.

    2.   Wählen Sie in der Taskleiste **Exportieren** aus.

    3.   Wählen Sie **Profil herunterladen**, und speichern Sie die heruntergeladene MOBILECONFIG-Datei.

6.  Übertragen Sie die Datei, indem Sie die heruntergeladene MOBILECONFIG-Datei auf einen Mac-Computer kopieren.
    > [!NOTE]
    > Die Anmeldungsprofil-URL ist ab dem Export zwei Wochen lang gültig. Nach zwei Wochen müssen Sie eine neue Anmeldungsprofil-URL zum Registrieren von iOS-Geräten mit dem Setup-Assistenten exportieren.

7.  Bereiten Sie das Gerät mit Apple Configurator vor. iOS-Geräte werden mit dem Mac-Computer verbunden und für die Verwaltung mobiler Geräte registriert.

    1.  Öffnen Sie auf einem Mac-Computer **Apple Configurator 2.0**.

    2.  Verbinden Sie das iOS-Gerät mit dem Mac-Computer über ein USB-Kabel. Schließen **Fotos**, **iTunes** und andere Apps, die für das Gerät geöffnet werden, wenn das Gerät erkannt wird.

    3.  Wählen Sie in Apple Configurator das verbundene iOS-Gerät und anschließend die Schaltfläche **Hinzufügen** aus. Optionen, die dem Gerät hinzugefügt werden können, werden in der Dropdownliste angezeigt. Wählen Sie **Profile** aus.

    4.  Verwenden Sie die Dateiauswahl zum Auswählen der aus Intune exportierten MOBILECONFIG-Datei, und wählen Sie anschließend **Hinzufügen** aus. Das Profil wird zum Gerät hinzugefügt.  Wenn das Gerät **nicht überwacht** wird, muss der Installation auf dem Gerät zugestimmt werden.

8.  Sie können das Profil nun auf dem iOS-Gerät installieren. Auf dem Gerät muss der Setup-Assistent ausgeführt worden sein, und es muss einsatzbereit sein. Wenn bei der Registrierung Apps bereitgestellt werden müssen, sollten Sie über eine Apple-ID verfügen, da Sie für App-Bereitstellungen mit einer Apple-ID beim App Store angemeldet sein müssen.

    1.  Entsperren Sie das iOS-Gerät.

    2.  Wählen Sie im Dialogfeld **Profil installieren** für das **Verwaltungsprofil** **Installieren** aus.

    3.  Geben Sie die **Gerätekennung** oder die **Apple-ID** ein, falls erforderlich.

    4.  Akzeptieren Sie die **Warnung**, und wählen Sie **Installieren** aus.

    5.  Akzeptieren Sie die **Remotewarnung**, und wählen Sie **Vertrauen** aus.

    6.  Wenn mit der Meldung **Profil installiert** bestätigt wird, dass das Profil **installiert** wurde, wählen Sie **Fertig** aus.

9.  Öffnen Sie auf dem iOS-Gerät **Einstellungen**, und wechseln Sie zu **Allgemein** &gt; **Geräteverwaltung** &gt; **Management Profile** (Verwaltungsprofil). Vergewissern Sie sich, dass die Profilinstallation aufgelistet ist, und überprüfen Sie die iOS-Richtlinieneinschränkungen und die installierten Apps. Es kann bis zu 10 Minuten dauern, bis Richtlinieneinschränkungen und Apps auf dem Gerät angezeigt werden.

10.  Verteilen von Geräten. Das iOS-Gerät ist jetzt bei Intune registriert und wird verwaltet.
