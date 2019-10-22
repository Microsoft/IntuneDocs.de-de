---
title: Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android Enterprise-Geräte
titleSuffix: Microsoft Intune
description: Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune zum Bereitstellen von Einstellungen, wenn Benutzer eine verwaltete Google Play-App ausführen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d31126a259274a2c75f933428632e274d8710aa6
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350024"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android Enterprise-Geräte

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Die App-Konfigurationsrichtlinien in Microsoft Intune bieten Einstellungen für verwaltete Google Play-Apps auf verwalteten Android Enterprise-Geräten. App-Entwickler machen Konfigurationseinstellungen für verwaltete Android-Apps verfügbar. Intune verwendet diese Einstellungen, um es Administratoren zu ermöglichen, Features für die Apps zu konfigurieren. Die App-Konfigurationsrichtlinie wird Ihren Benutzergruppen zugewiesen. Die Richtlinieneinstellungen werden verwendet, wenn die App danach sucht – in der Regel bei der ersten Ausführung der App.

> [!NOTE]  
> Nicht jede App unterstützt App-Konfigurationen. Fragen Sie beim App-Entwickler nach, ob die App Richtlinien für die App-Konfiguration unterstützt.

1. Klicken Sie in [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) auf **Client-Apps** > **App-Konfigurationsrichtlinien** >  **Hinzufügen**.
2. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein guter Name für eine Richtlinie ist beispielsweise **Android Enterprise Nine Work-App-Richtlinie für das gesamte Unternehmen**.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Geräteregistrierungstyp**: Wählen Sie **Verwaltete Geräte** aus.
    - **Plattform**: Wählen Sie **Android** aus.

3. Wählen Sie **Zugeordnete App** aus. Wählen Sie die App aus, für die Sie eine App-Konfigurationsrichtlinie definieren möchten. Wählen Sie diese aus der Liste von verwalteten Google Play-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
4. Klicken Sie auf **Berechtigungen**. Sie können Konfigurationen auf diese Weise festlegen:

    - im [Konfigurations-Designer](#use-the-configuration-designer)
    - im [JSON-Editor](#enter-the-json-editor)

5. Klicken Sie auf **OK** > **Hinzufügen**.

## <a name="use-the-configuration-designer"></a>Verwenden des Konfigurations-Designers

Sie können den Konfigurations-Designer für verwaltete Google Play-Apps verwenden, wenn die App zur Unterstützung der Konfigurationseinstellungen entwickelt wurde. Die Konfiguration gilt für Geräte, die bei Intune registriert sind. Der Designer ermöglicht Ihnen die Konfiguration bestimmter Konfigurationswerte für die Einstellungen, die von einer App zur Verfügung gestellt werden.

1. Wählen Sie **Hinzufügen** aus. Wählen Sie die Liste der Konfigurationseinstellungen aus, die Sie für die App eingeben möchten.

    Wenn Sie für Ihre E-Mail-App Gmail oder Nine Work verwenden, finden Sie Informationen zu diesen Einstellungen unter [Android Enterprise-Geräteeinstellungen zum Konfigurieren von E-Mails](../email-settings-android-enterprise.md).

2. Legen Sie für jeden Schlüssel und jeden Wert in der Konfiguration Folgendes fest:

    - **Werttyp**: Der Datentyp des Konfigurationswerts. Für Werttypen von Zeichenfolgen können Sie auch ein Variablen- oder Zertifikatprofil als Werttyp auswählen.
    - **Konfigurationswert**: Der Wert für die Konfiguration. Wählen Sie aus der Liste von Variablen- oder Zertifikatprofilen eine Variable oder ein Zertifikat für den **Werttyp** aus. Wenn Sie ein Zertifikat auswählen, wird der Zertifikatalias des auf dem Gerät bereitgestellten Zertifikats zur Laufzeit aufgefüllt.

### <a name="supported-variables-for-configuration-values"></a>Unterstützte Variablen für Konfigurationswerte

Wenn Sie eine Variable als Werttypen auswählen möchten, haben Sie folgende Optionen:

| Option | Beispiel |
|----|----|
| Mail | john@contoso.com |
| Benutzerprinzipalname | john@contoso.com |
| Partieller UPN | john |
| Domain | contoso.com |
| Benutzername | John Doe |
| Konto-ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| Benutzerkennung | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Geräte-ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Nur Zulassen von konfigurierten Organisationskonten in Apps mit mehreren Identitäten 

Verwenden Sie für Android-Geräte die folgenden Schlüssel/Wert-Paare:

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Werte** | <ul><li>Ein oder mehrere durch <code>;</code> getrennte UPNs.</li><li>Die einzigen zulässigen Konten sind die von diesem Schlüssel definierten, verwalteten Benutzerkonten.</li><li> Für bei Intune registrierte Geräte kann das Token <code>{{userprincipalname}}</code> verwendet werden, um das angemeldete Benutzerkonto darzustellen.</li></ul> |

   > [!NOTE]
   > Sie müssen Outlook für Android 2.2.222 und höher, Word, Excel, PowerPoint für Android 16.0.9327.1000 und höher oder OneDrive für Android 5.28 und höher verwenden, wenn nur konfigurierte Organisationskonten mit mehreren Identitäten zugelassen werden.<p></p>
   > Als Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. Die unterstützenden Anwendungen verarbeiten die App-Konfiguration und entfernen und blockieren nicht genehmigte Konten.<p></p>

## <a name="enter-the-json-editor"></a>Eingabe mit dem JSON-Editor

Einige Konfigurationseinstellungen für Apps (z. B. Apps vom Typ „Bundle“) können nicht mit dem Konfigurations-Designer konfiguriert werden. Verwenden Sie für diese Werte den JSON-Editor. Einstellungen werden Apps automatisch bereitgestellt, wenn die App installiert wird.

1. Wählen Sie für **Format der Konfigurationseinstellungen** die Option **JSON-Editor aufrufen** aus.
2. Im Editor können Sie JSON-Werte für Konfigurationseinstellungen definieren. Sie können **JSON-Vorlage herunterladen** auswählen, um eine Beispieldatei herunterzuladen, die Sie dann konfigurieren können.
3. Wählen Sie **OK** und dann **Hinzufügen** aus.

Die Richtlinie wird erstellt und in der Liste angezeigt.

Wenn die zugewiesene App auf einem Gerät gestartet wird, wird sie mit den Einstellungen ausgeführt, die Sie in der App-Konfigurationsrichtlinie konfiguriert haben.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Vorkonfigurieren des Erteilungsstatus von Berechtigungen für Apps

Sie können auch App-Berechtigungen so vorkonfigurieren, dass Apps auf Android-Gerätefunktionen zugreifen können. Standardmäßig fordern Android-Apps, die Geräteberechtigungen erfordern (z. B. Zugriff auf den Standort oder die Gerätekamera) die Benutzer zum Annehmen oder Ablehnen der Berechtigungen auf.

Beispiel: Eine App verwendet das Mikrofon des Geräts. Dann wird der Benutzer dazu aufgefordert, der App die Berechtigung zur Verwendung des Mikrofons zu erteilen.

1. Klicken Sie in [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) auf **Client-Apps** > **App-Konfigurationsrichtlinien** >  **Hinzufügen**.
2. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein guter Name für eine Richtlinie ist beispielsweise **Android Enterprise-App-Richtlinie für Berechtigungsaufforderungen für das gesamte Unternehmen**.
    - **Beschreibung**. Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Geräteregistrierungstyp**: Wählen Sie **Verwaltete Geräte** aus.
    - **Plattform**: Wählen Sie **Android** aus.

3. Wählen Sie **Zugeordnete App** aus. Wählen Sie die App aus, für die Sie eine Konfigurationsrichtlinie definieren möchten. Wählen Sie diese aus der Liste der Android-Arbeitsprofil-Apps aus, die Sie genehmigt und mit Intune synchronisiert haben.
4. Klicken Sie auf **Berechtigungen** > **Hinzufügen**. Wählen Sie aus der Liste die verfügbaren App-Berechtigungen aus, und klicken Sie anschließend auf **OK**.
5. Wählen Sie eine Option für jede Berechtigung aus, die mit dieser Richtlinie erteilt werden soll:
    - **Aufforderung** Aufforderung des Benutzers zur Annahme oder Ablehnung
    - **Automatisch gewähren** Automatische Genehmigung ohne Benachrichtigung des Benutzers
    - **Automatisch verweigern** Automatische Ablehnung ohne Benachrichtigung des Benutzers
6. Wählen Sie zum Zuweisen der App-Konfigurationsrichtlinie die App-Konfigurationsrichtlinie aus, und klicken Sie anschließend auf **Zuweisung** > **Gruppen auswählen**. Wählen Sie die Benutzergruppen aus, die zugewiesen werden sollen, und klicken Sie anschließend auf **Auswählen**.
7. Wählen Sie **Speichern** aus, um die Richtlinie zuzuweisen.

## <a name="additional-information"></a>Zusätzliche Informationen

- [Zuweisen einer verwalteten Google Play-App zu Android Enterprise-Geräten](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Bereitstellen von Outlook für iOS- und Android-App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie damit fort, die App [zuzuweisen](apps-deploy.md) und zu [überwachen](apps-monitor.md).
