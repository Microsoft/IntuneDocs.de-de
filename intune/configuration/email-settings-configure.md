---
title: Konfigurieren von E-Mail-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erstellen Sie ein E-Mail-Profil in Microsoft Intune, und stellen Sie dieses Profil auf Android Enterprise-, iOS-, iPadOS- und Windows-Geräten bereit. Verwenden Sie ein E-Mail-Profil, um allgemeine E-Mail-Einstellungen zu konfigurieren, einschließlich eines E-Mail-Servers und der Authentifizierungsmethode für die Verbindungsherstellung mit Unternehmens-E-Mails auf von Ihnen verwalteten Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 908a20098917540e6f823d94c6643d15f13ecf68
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511084"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Hinzufügen von E-Mail-Einstellungen für Geräte mit Intune

Microsoft Intune umfasst verschiedene E-Mail-Einstellungen, die Sie für Geräte in Ihrer Organisation bereitstellen können. Ein IT-Administrator kann E-Mail-Profile mit spezifischen Einstellungen für die Verbindungsherstellung mit einem E-Mail-Server – z.B. Office 365 und Gmail – erstellen. Endbenutzer können anschließend über ihre mobilen Geräte eine Verbindung mit ihren Organisations-E-Mail-Konten herstellen, sich authentifizieren und eine Synchronisierung durchführen. Durch das Erstellen und Bereitstellen eines E-Mail-Profils können Sie sicherstellen, dass geräteübergreifend Standardeinstellungen verwendet werden. Außerdem kann dies die Anzahl von Anrufen beim Support durch Benutzer verringern, die nicht die richtigen E-Mail-Einstellungen kennen.

Sie können E-Mail-Profile verwenden, um die integrierten E-Mail-Einstellungen auf den folgenden Geräten zu konfigurieren:

- Android Samsung KNOX Standard 4.0 und höher
- Android Enterprise
- iOS 8.0 und höher
- iOS 13.0 und höher
- Windows Phone 8.1 oder höher
- Windows 10 (Desktop) und Windows 10 Mobile

Dieser Artikel zeigt, wie Sie ein E-Mail-Profil in Microsoft Intune erstellen. Außerdem werden Links zu verschiedenen Plattformen mit Informationen zu spezifischeren Einstellungen bereitgestellt.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name:** Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein sinnvoller Richtlinienname ist beispielsweise **E-Mail-Einstellungen für alle Windows-Geräte**.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:

        - **Android** (nur Samsung Android KNOX Standard)
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **E-Mail** aus.

4. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. Wählen Sie Ihre Plattform für detaillierte Einstellungen aus:

    - [Android Samsung Knox Standard-Einstellungen](../email-settings-android.md)
    - [Android Enterprise-Einstellungen](../email-settings-android-enterprise.md)
    - [iOS/iPadOS-Einstellungen](email-settings-ios.md)
    - [Einstellungen für Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Einstellungen für Windows 10](email-settings-windows-10.md)

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Nachdem Sie Ihre Einstellungen eingegeben und das Profil erstellt haben, wird das Profil in der Liste angezeigt. Im nächsten Schritt [weisen Sie dieses Profil nun einigen Gruppen zu](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Entfernen eines E-Mail-Profils

E-Mail-Profile werden Gerätegruppen und nicht Benutzergruppen zugewiesen. Es gibt verschiedene Möglichkeiten, ein E-Mail-Profil von einem Gerät zu entfernen, auch wenn nur ein E-Mail-Profil vorhanden ist:

- **Option 1**: Öffnen Sie das E-Mail-Profil (**Geräte** > **Konfigurationsprofile** > wählen Sie Ihr Profil aus), und wählen Sie **Zuweisungen** aus. Auf der Registerkarte **Einschließen** werden die Gruppen angezeigt, denen das Profil zugewiesen ist. Klicken Sie mit der rechten Maustaste auf die Gruppe, und wählen Sie dann **Entfernen**. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

- **Option 2**: [Setzen Sie das Gerät zurück, oder nehmen Sie es außer Betrieb.](../remote-actions/devices-wipe.md) Mit diesen Optionen können Sie einige oder alle Daten und Einstellungen entfernen.

## <a name="secure-email-access"></a>Sicherer E-Mail-Zugriff

E-Mail-Profile können mit einer dieser Optionen geschützt werden:

- **Zertifikate:** Beim Erstellen des E-Mail-Profils wählen Sie ein Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dieses Zertifikat wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines vertrauenswürdigen Zertifikatprofils oder eines Stammzertifikats, um zu bestätigen, dass das Gerät des Benutzers eine Verbindung herstellen darf. Das vertrauenswürdige Zertifikat wird dem Computer zugewiesen, der die E-Mail-Verbindung authentifiziert. Dies ist in der Regel der native E-Mail-Server.

  Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Konfigurieren von Zertifikaten mit Intune](../protect/certificates-configure.md).

- **Benutzername und Kennwort**: Der Endbenutzer authentifiziert sich beim nativen Mailserver durch Eingabe eines Benutzernamens und Kennworts. Das Kennwort ist nicht im E-Mail-Profil enthalten. Deshalb muss der Endbenutzer das Kennwort eingeben, wenn eine Verbindung mit dem E-Mail-Postfach hergestellt wird.

## <a name="how-intune-handles-existing-email-accounts"></a>Behandlung vorhandener E-Mail-Konten in Intune

Wenn der Benutzer bereits ein E-Mail-Konto konfiguriert hat, wird das E-Mail-Profil je nach Plattform unterschiedlich zugewiesen.

- **iOS/iPadOS:** Basierend auf dem Hostnamen und der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt. Das doppelte E-Mail-Profil verhindert die Zuweisung eines Intune-Profils. In diesem Fall benachrichtigt das Unternehmensportal den Endbenutzer über die fehlende Konformität und fordert ihn auf, das konfigurierte E-Mail-Profil manuell zu entfernen. Weisen Sie Ihre Endbenutzer an, sich *vor* der Installation eines E-Mail-Profils zu registrieren und die Einrichtung des Profils durch Intune zuzulassen, um dieses Szenario zu vermeiden.

- **Windows:** Basierend auf dem Hostnamen und der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt. Intune überschreibt das vorhandene vom Endbenutzer erstellte E-Mail-Profil.

- **Android Samsung Knox Standard**: Basierend auf der E-Mail-Adresse wird ein vorhandenes doppeltes E-Mail-Profil erkannt und durch das Intune-Profil überschrieben. Android identifiziert das Profil nicht anhand des Hostnamens. Erstellen Sie nicht mehrere E-Mail-Profile mit derselben E-Mail-Adresse auf verschiedenen Hosts. Die Profile überschreiben sich gegenseitig.

- **Android-Arbeitsprofile**: Intune stellt zwei Android-E-Mail-Arbeitsprofile bereit: eines für die E-Mail-App Gmail und eines für die E-Mail-App Nine Work. Diese Apps sind im Google Play Store erhältlich und können im Arbeitsprofil des Geräts installiert werden. Diese Apps erstellen keine doppelten Profile. Beide Apps unterstützen Verbindungen mit Exchange. Zur Verwendung der E-Mail-Konnektivität stellen Sie eine dieser E-Mail-Apps für die Benutzergeräte bereit. Erstellen Sie anschließend das geeignete E-Mail-Profil, und stellen Sie es bereit. E-Mail-Apps wie z.B. Nine Work sind möglicherweise nicht kostenlos. Lesen Sie die Lizenzierungsdetails der App, oder kontaktieren Sie bei Fragen das Unternehmen, das die App bereitstellt.

## <a name="changes-to-assigned-email-profiles"></a>Änderungen an zugewiesenen E-Mail-Profilen

Wenn Sie ein zuvor zugewiesenes E-Mail-Profil ändern, werden Endbenutzer möglicherweise in einer Meldung aufgefordert, die Neukonfiguration ihrer E-Mail-Einstellungen zu genehmigen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](../device-profile-assign.md).
