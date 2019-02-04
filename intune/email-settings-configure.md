---
title: Konfigurieren von E-Mail-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein E-Mail-Profil in Microsoft Intune, und stellen Sie dieses Profil auf Android Enterprise-, iOS- und Windows-Geräten bereit. Verwenden Sie ein E-Mail-Profil, um allgemeine E-Mail-Einstellungen zu konfigurieren, einschließlich eines E-Mail-Servers und der Authentifizierungsmethode für die Verbindungsherstellung mit Unternehmens-E-Mails auf von Ihnen verwalteten Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 28a78720b6ccc86b275f57b443ee7a63ca746512
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831325"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Hinzufügen von E-Mail-Einstellungen für Geräte mit Intune

Microsoft Intune umfasst verschiedene E-Mail-Einstellungen, die Sie für Geräte in Ihrer Organisation bereitstellen können. Ein IT-Administrator kann E-Mail-Profile mit spezifischen Einstellungen für die Verbindungsherstellung mit einem E-Mail-Server – z.B. Office 365 und Gmail – erstellen. Endbenutzer können anschließend über ihre mobilen Geräte eine Verbindung mit ihren Organisations-E-Mail-Konten herstellen, sich authentifizieren und eine Synchronisierung durchführen. Durch das Erstellen und Bereitstellen eines E-Mail-Profils können Sie sicherstellen, dass geräteübergreifend Standardeinstellungen verwendet werden. Außerdem kann dies die Anzahl von Anrufen beim Support durch Benutzer verringern, die nicht die richtigen E-Mail-Einstellungen kennen.

Sie können E-Mail-Profile verwenden, um die integrierten E-Mail-Einstellungen auf den folgenden Geräten zu konfigurieren:

- Android Samsung KNOX Standard 4.0 und höher
- Android Enterprise
- iOS 8.0 und höher
- Windows Phone 8.1 und höher
- Windows 10 (Desktop) und Windows 10 Mobile

Dieser Artikel zeigt, wie Sie ein E-Mail-Profil in Microsoft Intune erstellen. Außerdem werden Links zu verschiedenen Plattformen mit Informationen zu spezifischeren Einstellungen bereitgestellt.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie **Name** und **Beschreibung** für das E-Mail-Profil ein.
4. Wählen Sie in der Dropdownliste Ihre **Plattform** aus. Folgende Optionen sind verfügbar:

    - **Android** (nur Samsung Android KNOX Standard)
    - **Android Enterprise**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 und höher**

5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **E-Mail** aus.
6. Die Einstellungen, die Sie konfigurieren können, richten sich nach der verwendeten Plattform. Wählen Sie für spezifische Einstellungen Ihre Plattform aus:

    - [Android Samsung Knox Standard-Einstellungen](email-settings-android.md)
    - [Android Enterprise-Einstellungen](email-settings-android-enterprise.md)
    - [Einstellungen für iOS](email-settings-ios.md)
    - [Einstellungen für Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Einstellungen für Windows 10](email-settings-windows-10.md)

Nachdem Sie Ihre Einstellungen eingegeben und das Profil erstellt haben, wird das Profil in der Liste angezeigt. Im nächsten Schritt [weisen Sie dieses Profil nun einigen Gruppen zu](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Entfernen eines E-Mail-Profils

E-Mail-Profile werden Gerätegruppen und nicht Benutzergruppen zugewiesen. Es gibt verschiedene Möglichkeiten, ein E-Mail-Profil von einem Gerät zu entfernen, auch wenn nur ein E-Mail-Profil vorhanden ist:

- **Option 1**: Öffnen Sie das E-Mail-Profil (**Gerätekonfiguration** > **Profile**), und klicken Sie auf **Zuweisungen**. Auf der Registerkarte **Einschließen** werden die Gruppen angezeigt, denen das Profil zugewiesen ist. Klicken Sie mit der rechten Maustaste auf die Gruppe, und wählen Sie dann **Entfernen**. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

- **Option 2**: [Setzen Sie das Gerät zurück, oder nehmen Sie es außer Betrieb.](devices-wipe.md) Mit diesen Optionen können Sie einige oder alle Daten und Einstellungen entfernen.

## <a name="secure-email-access"></a>Sicherer E-Mail-Zugriff

E-Mail-Profile können mit einer dieser Optionen geschützt werden:

- **Zertifikate**: Beim Erstellen des E-Mail-Profils wählen Sie ein Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dieses Zertifikat wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines vertrauenswürdigen Zertifikatprofils oder eines Stammzertifikats, um zu bestätigen, dass das Gerät des Benutzers eine Verbindung herstellen darf. Das vertrauenswürdige Zertifikat wird dem Computer zugewiesen, der die E-Mail-Verbindung authentifiziert. Dies ist in der Regel der native E-Mail-Server.

  Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Konfigurieren von Zertifikaten mit Intune](certificates-configure.md).

- **Benutzername und Kennwort**: Der Endbenutzer authentifiziert sich beim nativen Mailserver durch Eingabe eines Benutzernamens und Kennworts. Das Kennwort ist nicht im E-Mail-Profil enthalten. Deshalb muss der Endbenutzer das Kennwort eingeben, wenn eine Verbindung mit dem E-Mail-Postfach hergestellt wird.

## <a name="how-intune-handles-existing-email-accounts"></a>Behandlung vorhandener E-Mail-Konten in Intune

Wenn der Benutzer bereits ein E-Mail-Konto konfiguriert hat, wird das E-Mail-Profil je nach Plattform unterschiedlich zugewiesen.

- **iOS**: Basierend auf dem Hostnamen und der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt. Das doppelte E-Mail-Profil verhindert die Zuweisung eines Intune-Profils. In diesem Fall benachrichtigt das Unternehmensportal den Endbenutzer über die fehlende Konformität und fordert ihn auf, das konfigurierte E-Mail-Profil manuell zu entfernen. Weisen Sie Ihre Endbenutzer an, sich *vor* der Installation eines E-Mail-Profils zu registrieren und die Einrichtung des Profils durch Intune zuzulassen, um dieses Szenario zu vermeiden.

- **Windows:** Basierend auf dem Hostnamen und der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt. Intune überschreibt das vorhandene vom Endbenutzer erstellte E-Mail-Profil.

- **Android Samsung Knox Standard**: Basierend auf der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt und durch das Intune-Profil überschrieben. Android identifiziert das Profil nicht anhand des Hostnamens. Erstellen Sie nicht mehrere E-Mail-Profile mit derselben E-Mail-Adresse auf verschiedenen Hosts. Die Profile überschreiben sich gegenseitig.

- **Android-Arbeitsprofile**: Intune stellt zwei Android-E-Mail-Arbeitsprofile bereit: eines für die E-Mail-App Gmail und eines für die E-Mail-App Nine Work. Diese Apps sind im Google Play Store erhältlich und können im Arbeitsprofil des Geräts installiert werden. Diese Apps erstellen keine doppelten Profile. Beide Apps unterstützen Verbindungen mit Exchange. Zur Verwendung der E-Mail-Konnektivität stellen Sie eine dieser E-Mail-Apps für die Benutzergeräte bereit. Erstellen Sie anschließend das geeignete E-Mail-Profil, und stellen Sie es bereit. E-Mail-Apps wie z.B. Nine Work sind möglicherweise nicht kostenlos. Lesen Sie die Lizenzierungsdetails der App, oder kontaktieren Sie bei Fragen das Unternehmen, das die App bereitstellt.

## <a name="changes-to-assigned-email-profiles"></a>Änderungen an zugewiesenen E-Mail-Profilen

Wenn Sie ein zuvor zugewiesenes E-Mail-Profil ändern, werden Endbenutzer möglicherweise in einer Meldung aufgefordert, die Neukonfiguration ihrer E-Mail-Einstellungen zu genehmigen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Im nächsten Schritt können Sie [das Profil einigen Geräten zuweisen](device-profile-assign.md).