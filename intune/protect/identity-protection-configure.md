---
title: Verwenden einer PIN zur Anmeldung bei Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Windows Hello for Business, um Benutzern die Anmeldung bei Geräten mit einer PIN, einem Fingerabdruck und auf sonstige Weise zu ermöglichen. Erstellen Sie in Intune ein Identity Protection-Konfigurationsprofil für Windows 10-Geräte mit diesen Einstellungen, und weisen Sie das Profil Benutzergruppen und Gerätegruppen zu.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f5d3a232cab25c60189132732a0ea3f347c74a
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683798"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Verwenden von Windows Hello for Business auf Windows 10-Geräten mit Microsoft Intune

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

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Geben Sie die folgenden Eigenschaften ein:

   - **Name:** Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus. Windows Hello for Business wird nur auf Geräten mit Windows 10 und höher unterstützt.
   - **Profiltyp**: Wählen Sie **Identity Protection** aus.

4. Konfigurieren Sie im Bereich *Windows Hello for Business* die folgenden Optionen:

   - **Konfigurieren Sie Windows Hello for Business**: Wählen Sie aus, wie Sie Windows Hello for Business konfigurieren möchten:

     - **Nicht konfiguriert** (Standardeinstellung): [Stellt Windows Hello for Business](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) auf dem Gerät bereit. Wenn Sie Identity Protection-Profile nur für Benutzer zuweisen, wird der Gerätekontext standardmäßig auf **Nicht konfiguriert** gesetzt.

     - **Deaktiviert:** Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Option aus. Diese Option deaktiviert Windows Hello for Business für alle Benutzer.

     - **Aktiviert**: Wählen Sie diese Option zum [Bereitstellen](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) aus, und konfigurieren Sie Windows Hello for Business-Einstellungen in Intune. Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste mit allen Einstellungen und ihren Funktionen finden Sie unter [Einstellungen für Windows 10-Geräte zum Aktivieren von Windows Hello for Business in Intune](identity-protection-windows-settings.md).

   - **Verwenden von Sicherheitsschlüssel zur Anmeldung:** Aktivieren Sie den Windows Hello-Sicherheitsschlüssel als Anmeldeinformation zur Anmeldung für alle Computer im Mandanten.

     - **Aktivieren**
     - **Nicht konfiguriert** (Standard)

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Profilliste angezeigt. [Weisen](../configuration/device-profile-assign.md) Sie als nächstes dieses Profil Ihren Anforderungen entsprechend Benutzer- oder Gerätegruppen zu.

> [!IMPORTANT]
> Um die Bereitstellung mehrerer Benutzer für ein Gerät zu ermöglichen, geben Sie an, dass die Windows Hello for Business-Richtlinie auf die Geräte angewendet werden soll. Wenn die Richtlinie nur auf Benutzer angewendet wird, kann nur ein Benutzer für ein Gerät bereitgestellt werden.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>Nächste Schritte

- Lesen Sie eine Liste aller [Einstellungen und ihrer Funktionen](identity-protection-windows-settings.md).
- [Zuweisen von Profilen](../configuration/device-profile-assign.md) und [Überwachen von Profilen](../configuration/device-profile-monitor.md)
