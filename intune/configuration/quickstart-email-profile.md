---
title: 'Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS/iPadOS-Geräte'
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mit Microsoft Intune ein E-Mail-Geräteprofil erstellen können, damit iOS/-Geräte sicher auf Unternehmens-E-Mails zugreifen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511067"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS/iPadOS

In diesem Schnellstart erfahren Sie, wie Sie ein E-Mail-Geräteprofil für iOS/iPadOS-Geräte erstellen. Dieses Profil gibt die Einstellungen an, die für die integrierte E-Mail-App auf dem iOS/iPadOS-Gerät erforderlich sind, um auf Unternehmens-E-Mails zugreifen zu können. E-Mail-Geräteprofile helfen beim geräteübergreifenden Standardisieren von Einstellungen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. Um Ihre E-Mails noch besser zu schützen, können Sie mit einem E-Mail-Profil bestimmen, ob Geräte konform sind, und dann den bedingten Zugriff so einrichten, dass nur konforme Geräte auf E-Mails zugreifen können. Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](email-settings-configure.md).

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) als globaler Administrator oder Intune-Dienstadministrator an. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-an-iosipados-email-profile"></a>Erstellen eines iOS/iPadOS-E-Mail-Profils

1. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

   ![Erstellen eines E-Mail-Profils für iOS/iPadOS in Intune](./media/quickstart-email-profile/ios-create-profile.png)

2. Geben Sie unter **Name** einen aussagekräftigen Namen für das neue Profil ein. Geben Sie für dieses Beispiel **iOS require work email** (Für iOS geschäftliche E-Mail erfordern) ein.
3. Geben Sie die folgenden Profilinformationen ein:
    - Geben Sie unter **Beschreibung** **Require iOS/iPadOS devices to use work email** (Erfordern, dass iOS/iPadOS-Geräte geschäftliche E-Mail verwenden) ein.
    - Wählen Sie als **Plattform** die Option **iOS/iPadOS** aus.
    - Wählen Sie für **Profiltyp****E-Mail** aus.

        ![Erstellen eines E-Mail-Profils zur Verwendung mit iOS/iPadOS-Geräten in Intune](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Wählen Sie **Einstellungen** aus, und geben Sie die folgenden Einstellungen ein (behalten Sie bei den anderen Einstellungen die Standardwerte bei):
   - **E-Mail-Server**: Geben Sie im Rahmen dieses Schnellstarts **outlook.office365.com** ein. Diese Einstellung gibt den Exchange-Speicherort (URL) des E-Mail-Servers an, den die iOS/iPadOS-Mail-App verwendet, um auf E-Mails zuzugreifen.
   - **Kontoname**: Geben Sie **Unternehmens-E-Mail-Adresse** ein.
   - **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut, das Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert mit diesem Namen dynamisch den Benutzernamen für dieses Profil. Für diese Schnellstartanleitung nehmen wir an, dass der **Benutzerprinzipalname** als Benutzername für das Profil verwenden werden soll (zum Beispiel user1@contoso.com).
   - **Attribut für E-Mail-Adresse aus AAD**: Diese Einstellung ist die E-Mail-Adresse aus Azure AD, die für die Anmeldung bei Exchange verwendet wird. Wählen Sie für diese Schnellstartanleitung **Benutzerprinzipalname** aus.
   - **Authentifizierungsmethode**: Wählen Sie im Rahmen dieses Schnellstarts **Benutzername und Kennwort** aus. (Sie können auch **Zertifikat** auswählen, wenn Sie bereits ein Zertifikat für Intune eingerichtet haben.)

        ![Erstellen eines E-Mail-Profils für iOS/iPadOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Klicken Sie auf **OK** > **Erstellen**. Das neue Profil wird in der Profilliste mit dem Dashboard angezeigt, damit Sie überwachen können, wie das Profil iOS/iPadOS-Geräten und iOS/iPadOS-Benutzern zugewiesen wurde.
6. Wählen Sie **Zuweisungen** aus.
7. Wählen Sie die Registerkarte **Einschließen** und dann **All Users & All Devices** (Alle Benutzer & Alle Geräte) aus. 
8. Wählen Sie **Speichern** aus.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie das erstellte Profil nicht für weitere Tutorials oder Tests verwenden möchten, können sie es jetzt löschen.

1. Wählen Sie in Intune die Option **Gerätekonfiguration** und anschließend **Profile** aus.
2. Wählen Sie das erstellte Testprofil **iOS/iPadOS require work email** (Für iOS/iPadOS geschäftliche E-Mail erfordern) aus.
3. Wählen Sie die Ellipse (**...**) neben dem Profil aus, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie ein E-Mail-Profil für iOS/iPadOS-Geräte erstellt. Jetzt können Sie mit diesem Profil bestimmen, ob ein iOS/iPadOS-Gerät konform ist, indem Sie eine Konformitätsrichtlinie erstellen, die alle nicht dem Profil entsprechenden iOS/iPadOS-Geräte als nicht konform markiert. Für noch besseren Schutz können Sie eine Richtlinie für bedingten Zugriff erstellen, die verhindert, dass nicht konforme iOS/iPadOS-Geräte auf E-Mails zugreifen. Weitere Informationen über Gerätekonformitätsrichtlinien finden Sie unter [Erste Schritte bei der Gerätekonformität in Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf verwalteten Geräten](../tutorial-protect-email-on-enrolled-devices.md)
