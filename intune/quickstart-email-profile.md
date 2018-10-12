---
title: Schnellstart – Erstellen eines E-Mail-Geräteprofils für iOS
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Microsoft Intune ein E-Mail-Geräteprofil erstellen können, damit iOS-Geräte sicher auf Unternehmens-E-Mails zugreifen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b797951c878dd90cbb7bb716b5108f94f48921c5
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231949"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS

In dieser Schnellstartanleitung erfahren Sie, wie Sie ein E-Mail-Geräteprofil für iOS-Geräte erstellen. Dieses Profil gibt die Einstellungen an, die für die integrierte E-Mail-App auf dem iOS-Gerät erforderlich sind, um auf Unternehmens-E-Mails zugreifen zu können. E-Mail-Geräteprofile helfen beim geräteübergreifenden Standardisieren von Einstellungen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. Um Ihre E-Mails noch besser zu schützen, können Sie mit einem E-Mail-Profil festlegen, ob Geräte konform sind, und dann bedingten Zugriff einrichten, sodass nur konforme Geräte auf E-Mails zugreifen können. Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](email-settings-configure.md).

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Intune finden Sie im Azure-Portal, indem Sie **Alle Dienste** > **Intune** auswählen.

## <a name="create-an-ios-email-profile"></a>Erstellen eines iOS-E-Mail-Profils
1. Wählen Sie in Intune die Option **Gerätekonfiguration** und anschließend **Profile** aus.
2. Klicken Sie auf **Profil erstellen**.
   
   ![Erstellen eines E-Mail-Profils für iOS](media/quickstart-email-profile/ios-create-profile.png)

3. Geben Sie unter **Name** einen aussagekräftigen Namen für das neue Profil ein. Geben Sie für dieses Beispiel **iOS require work email** (Für iOS geschäftliche E-Mail erfordern) ein.
4. Geben Sie die folgenden Profilinformationen ein:
   - Geben Sie unter **Beschreibung** **Require iOS devices to use work email** (Erfordern, dass iOS-Geräte geschäftliche E-Mail verwenden) ein.
   - Wählen Sie als **Plattform** die Option **iOS** aus.
   - Wählen Sie für **Profiltyp** **E-Mail** aus.
    
     ![Erstellen eines E-Mail-Profils für iOS](media/quickstart-email-profile/ios-email-profile-name.png)

5. Wählen Sie **Einstellungen** aus, und geben Sie die folgenden Einstellungen ein (behalten Sie bei den anderen Einstellungen die Standardwerte bei):
   - **E-Mail-Server:** Geben Sie im Rahmen dieser Schnellstartanleitung **outlook.office365.com** ein. Diese Einstellung gibt den Exchange-Speicherort (URL) des E-Mail-Servers an, den die iOS-Mail-App verwendet, um auf E-Mails zuzugreifen.
   - **Kontoname:** Geben Sie **Company Email** (Unternehmens-E-Mail) ein.
   - **Benutzernamensattribut aus AAD:** Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert mit diesem Namen dynamisch den Benutzernamen für dieses Profil. Für diese Schnellstartanleitung nehmen wir an, dass der **Benutzerprinzipalname** als Benutzername für das Profil verwenden werden soll (zum Beispiel user1@contoso.com).
   - **E-Mail-Adressattribut aus AAD:** Diese Einstellung ist die E-Mail-Adresse aus Azure AD, die für die Anmeldung bei Exchange verwendet wird. Wählen Sie für diese Schnellstartanleitung **Benutzerprinzipalname** aus.
   - **Authentifizierungsmethode:** Wählen Sie im Rahmen dieser Schnellstartanleitung **Benutzername und Kennwort** aus. (Sie können auch **Zertifikat** auswählen, wenn Sie bereits ein Zertifikat für Intune eingerichtet haben.)
    
     ![Erstellen eines E-Mail-Profils für iOS](media/quickstart-email-profile/ios-email-profile.png)

6. Wählen Sie **OK** aus.
7. Wählen Sie **Erstellen** aus. Das neue Profil wird in der Profilliste mit dem Dashboard angezeigt, damit Sie überwachen können, wie das Profil iOS-Geräten und iOS-Benutzern zugewiesen wurde.
8. Wählen Sie **Zuweisungen** aus.
9. Wählen Sie die Registerkarte **Einschließen** und dann **All Users & All Devices** (Alle Benutzer & Alle Geräte) aus. 
10. Wählen Sie **Speichern** aus.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen
Wenn Sie das erstellte Profil nicht für weitere Tutorials oder Tests verwenden möchten, können sie es jetzt löschen.
1. Wählen Sie in Intune die Option **Gerätekonfiguration** und anschließend **Profile** aus.
2. Wählen Sie das erstellte Testprofil **iOS require work email** (Für iOS geschäftliche E-Mail erfordern) aus.
3. Wählen Sie die Ellipse (**...**) neben dem Profil aus, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung haben Sie ein E-Mail-Profil für iOS-Geräte erstellt. Jetzt können Sie mit diesem Profil bestimmen, ob ein iOS-Gerät konform ist, indem Sie eine Konformitätsrichtlinie erstellen, die alle nicht dem Profil entsprechenden iOS-Geräte als nicht konform markiert. Für noch besseren Schutz können Sie eine Richtlinie für bedingten Zugriff erstellen, die verhindert, dass nicht konforme iOS-Geräte auf E-Mails zugreifen.

> [!div class="nextstepaction"]
> [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md)
