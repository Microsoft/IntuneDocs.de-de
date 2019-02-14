---
title: Verwenden einer PIN zur Anmeldung bei Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Windows Hello for Business, um Benutzern die Anmeldung bei Geräten mit einer PIN, einem Fingerabdruck und auf sonstige Weise zu ermöglichen. Erstellen Sie in Intune ein Identity Protection-Konfigurationsprofil für Windows 10-Geräte mit diesen Einstellungen, und weisen Sie das Profil Benutzergruppen und Gerätegruppen zu.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c6ca040c91437a35d12626f54b8385311d6631eb
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290654"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Verwenden von Windows Hello for Business auf Windows 10-Geräten mit Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows Hello for Business ist eine Methode zum Anmelden bei Windows-Geräten durch Ersetzen der Kennwörter, Smartcards und virtuellen Smartcards. Intune umfasst integrierte Einstellungen, damit Administratoren Windows Hello for Business konfigurieren und verwenden können. Beispielsweise können Sie mit diesen Einstellungen:

- Windows Hello for Business für Geräte und Benutzer aktivieren
- Geräte-PIN-Anforderungen festlegen, einschließlich einer minimalen oder maximalen PIN-Länge
- Gesten festlegen, z.B. einen Fingerabdruck, mit denen Benutzer sich bei Geräten anmelden können (oder nicht)

Dieses Feature gilt für das ausgeführte Gerät:

- Windows 10 und höher
- Windows 10 Mobile
- Windows Holographic for Business

Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Funktionen in einem Profil hinzugefügt haben, übertragen Sie diese Einstellungen mithilfe von Push auf Benutzer- und Gerätegruppen in Ihrer Organisation, oder stellen Sie sie für Gruppen bereit.

In diesem Artikel erfahren Sie, wie Sie ein Gerätekonfigurationsprofil erstellen. Eine Liste mit allen Einstellungen und ihren Funktionen finden Sie unter [Einstellungen für Windows 10-Geräte (und höher) zum Aktivieren von Windows Hello for Business](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Erstellen des Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus. Windows Hello for Business wird nur auf Geräten mit Windows 10 und höher unterstützt.
    - **Profiltyp**: Wählen Sie **Identity Protection** aus.
    - **Konfigurieren Sie Windows Hello for Business**: Wählen Sie aus, wie Sie Windows Hello for Business konfigurieren möchten. Folgende Optionen sind verfügbar:

        - **Nicht konfiguriert:** [Stellt Windows Hello for Business](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) auf dem Gerät bereit. Wenn Sie Identity Protection-Profile nur für Benutzer zuweisen, wird der Gerätekontext standardmäßig auf **Nicht konfiguriert** gesetzt.
        - **Deaktiviert:** Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Option aus. Diese Option deaktiviert Windows Hello for Business für alle Benutzer.
        - **Aktiviert**: Wählen Sie diese Option zum [Bereitstellen]((https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)) aus, und konfigurieren Sie Windows Hello for Business-Einstellungen in Intune. Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

            - [Einstellungen für Windows 10-Geräte (und höher) zum Aktivieren von Windows Hello for Business](identity-protection-windows-settings.md)

4. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Profilliste angezeigt. [Weisen](device-profile-assign.md) Sie als nächstes dieses Profil Ihren Anforderungen entsprechend Benutzer- oder Gerätegruppen zu.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->

## <a name="next-steps"></a>Nächste Schritte

- Lesen Sie eine Liste aller [Einstellungen und ihrer Funktionen](identity-protection-windows-settings.md).
- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)