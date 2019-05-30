---
title: Schnellstart – Erstellen eines E-Mail-Geräteprofils für iOS
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Microsoft Intune ein E-Mail-Geräteprofil erstellen können, damit iOS-Geräte sicher auf Unternehmens-E-Mails zugreifen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbf04d771a9c1fd43cfe695dd2d27b9cfe1a0528
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050305"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS

In dieser Schnellstartanleitung erfahren Sie, wie Sie ein E-Mail-Geräteprofil für iOS-Geräte erstellen. Dieses Profil gibt die Einstellungen an, die für die integrierte E-Mail-App auf dem iOS-Gerät erforderlich sind, um auf Unternehmens-E-Mails zugreifen zu können. E-Mail-Geräteprofile helfen beim geräteübergreifenden Standardisieren von Einstellungen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. Um Ihre E-Mails noch besser zu schützen, können Sie mit einem E-Mail-Profil festlegen, ob Geräte konform sind, und dann bedingten Zugriff einrichten, sodass nur konforme Geräte auf E-Mails zugreifen können. Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](email-settings-configure.md).

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

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
   - **E-Mail-Server**: Geben Sie im Rahmen dieses Schnellstarts **outlook.office365.com** ein. Diese Einstellung gibt den Exchange-Speicherort (URL) des E-Mail-Servers an, den die iOS-Mail-App verwendet, um auf E-Mails zuzugreifen.
   - **Kontoname**: Geben Sie **Unternehmens-E-Mail-Adresse** ein.
   - **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut, das Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert mit diesem Namen dynamisch den Benutzernamen für dieses Profil. Für diese Schnellstartanleitung nehmen wir an, dass der **Benutzerprinzipalname** als Benutzername für das Profil verwenden werden soll (zum Beispiel user1@contoso.com).
   - **Attribut für E-Mail-Adresse aus AAD**: Diese Einstellung ist die E-Mail-Adresse aus Azure AD, die für die Anmeldung bei Exchange verwendet wird. Wählen Sie für diese Schnellstartanleitung **Benutzerprinzipalname** aus.
   - **Authentifizierungsmethode**: Wählen Sie im Rahmen dieses Schnellstarts **Benutzername und Kennwort** aus. (Sie können auch **Zertifikat** auswählen, wenn Sie bereits ein Zertifikat für Intune eingerichtet haben.)
    
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

In dieser Schnellstartanleitung haben Sie ein E-Mail-Profil für iOS-Geräte erstellt. Jetzt können Sie mit diesem Profil bestimmen, ob ein iOS-Gerät konform ist, indem Sie eine Konformitätsrichtlinie erstellen, die alle nicht dem Profil entsprechenden iOS-Geräte als nicht konform markiert. Für noch besseren Schutz können Sie eine Richtlinie für bedingten Zugriff erstellen, die verhindert, dass nicht konforme iOS-Geräte auf E-Mails zugreifen. Weitere Informationen über Gerätekonformitätsrichtlinien finden Sie unter [Erste Schritte bei der Gerätekonformität in Intune](device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf verwalteten Geräten](tutorial-protect-email-on-enrolled-devices.md)
