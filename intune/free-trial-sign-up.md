---
title: 'Schnellstart: Testen Sie Microsoft Intune kostenlos'
titlesuffix: ''
description: In diesem Schnellstart erstellen Sie ein kostenloses Testabonnement, können unterstützte Konfigurationen und Netzwerkanforderungen nachvollziehen und optional Ihren Domänennamen konfigurieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 37445cb2536e02937cf3002dc1cb56ab4b78f12f
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581392"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Schnellstart: Testen Sie Microsoft Intune kostenlos 

Mit Microsoft Intune können Sie die Unternehmensdaten Ihrer Mitarbeiter durch die Verwaltung von Geräten und Apps schützen. In diesem Schnellstart erstellen Sie ein kostenloses Abonnement, um Intune in einer Testumgebung zu testen.

Intune bietet die Verwaltung mobiler Geräte (Mobile Device Management, MDM) und mobiler Apps (Mobile App Management, MAM) über einen sicheren cloudbasierten Dienst, der mithilfe des Microsoft Azure-Portals verwaltet wird. Durch die Verwendung von Intune stellen Sie sicher, dass die Unternehmensressourcen Ihrer Mitarbeiter (Daten, Geräte und Apps) ordnungsgemäß konfiguriert und aktualisiert werden und dass ordnungsgemäß darauf zugegriffen werden kann. Dabei wird darauf geachtet, dass die Konformitätsrichtlinien und Anforderungen Ihres Unternehmens eingehalten werden. 

## <a name="prerequisites"></a>Voraussetzungen
Prüfen Sie vor der Einrichtung von Microsoft Intune die folgenden Anforderungen:

   - [Unterstützte Betriebssysteme und Browser](supported-devices-browsers.md) 
   - [Bandbreite und Anforderungen an die Netzkonfiguration](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrieren für eine kostenlose Testversion von Microsoft Intune

Sie können Intune 30 Tage lang kostenlos testen. Wenn Sie bereits über ein Arbeits- oder Schulkonto verfügen, **melden Sie sich mit diesem Konto an**, und fügen Sie Intune Ihrem Abonnement hinzu. Sie können sich auch für ein neues Konto **registrieren**, um Intune für Ihre Organisation zu verwenden.

> [!IMPORTANT]
> Sie können kein bestehendes Arbeits- oder Schulkonto nach der Registrierung für ein neues Konto kombinieren.

1. Wechseln Sie zur Seite [Microsoft Intune-Testversion](https://go.microsoft.com/fwlink/?linkid=2019088), und füllen Sie das Formular aus.

    ![Screenshot der Website für die Registrierung für das Microsoft Intune-Testkonto](./media/account-sign-up-site-full-browser.png)

    Wenn sich der Großteil Ihres IT-Betriebs und Ihrer Benutzer in einem anderen Gebietsschema als Sie befindet, sollten Sie dieses Gebietsschema unter **Land oder Region** auswählen. Azure bietet Ihnen aufgrund Ihrer regionalen Informationen zur die richtigen Dienste an. Diese Einstellung kann später nicht mehr geändert werden.

2. Erstellen Sie ein Konto mit dem Namen Ihres Unternehmens gefolgt von **.onmicrosoft.com**. 

    ![Screenshot der Website für die Registrierung für das Microsoft Intune-Testkonto](./media/account-sign-up-site-user-id.png)

    Wenn Ihre Organisation über eine eigene benutzerdefinierte Domäne verfügt, die Sie ohne **.onmicrosoft.com** verwenden möchten, können Sie diese über das Verwaltungsportal von Microsoft Office 365 ändern. Näheres hierzu wird später in diesem Artikel erläutert.

3. Am Ende des Registrierungsvorgangs werden Ihre neuen Kontoinformationen angezeigt.

    ![Abbildung Ihrer Kontoinformationen](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Anmelden beim Azure-Portal

1. Öffnen Sie ein neues Browserfenster, und geben Sie **https://portal.azure.com** in die Adressleiste ein. 
2. Verwenden Sie die Anmeldeinformationen, die Sie in den oben genannten Schritten erhalten haben.

    ![Abbildung der Anmeldeseite des Azure-Portals](./media/azure-portal-signin.png)

3. Wenn Sie Microsoft Intune im Azure-Portal anzeigen möchten, wählen Sie in der linken Randleiste **Alle Dienste** aus.
4. Suchen Sie im Filterfeld nach **Microsoft Intune**, und wählen Sie dieses aus.
5. Klicken Sie auf den **Stern**, um Intune am Ende der Liste Ihrer bevorzugten Dienste hinzuzufügen, und öffnen Sie das Intune-Dashboard.

Wenn Sie sich für eine Testversion registrieren, wird eine E-Mail mit Ihren Kontoinformationen an die von Ihnen bei der Registrierung angegebene E-Mail-Adresse gesendet. Diese E-Mail bestätigt, dass Ihre Testversion aktiv ist.

## <a name="set-the-mdm-authority-to-intune"></a>Festlegen der MDM-Autorität in Intune

Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.

Führen Sie die folgenden Schritte aus, um die MDM-Autorität in Intune festzulegen.

1. Öffnen Sie ein neues Browserfenster, und geben Sie **https://portal.azure.com** in die Adressleiste ein. 
2. Wählen Sie **Alle Dienste** > **Microsoft Intune** aus.
3. Wählen Sie den orangefarbenen Banner aus, um die Einstellung **Autorität für die Verwaltung mobiler Geräte** zu öffnen. 

    > [!NOTE]
    > Der orangefarbene Banner wird nur angezeigt, wenn Sie die MDM-Autorität noch nicht festgelegt haben.

4. Legen Sie Ihre MDM-Autorität unter **Autorität für die Verwaltung mobiler Geräte** auf **Intune-MDM-Autorität** fest.

## <a name="configure-your-custom-domain-name-optional"></a>Konfigurieren des Namens Ihrer benutzerdefinierten Domäne (optional)

Wie vorstehend erwähnt, können Sie eine benutzerdefinierte Domäne über das Verwaltungsportal von Microsoft Office 365 ändern, wenn Ihre Organisation über eine eigene benutzerdefinierte Domäne verfügt, die Sie ohne **.onmicrosoft.com** verwenden möchten. Sie können den Namen Ihrer benutzerdefinierten Domäne hinzufügen, überprüfen und konfigurieren.  

> [!IMPORTANT]
> Sie können den Namen der Anfangsdomäne **onmicrosoft.com** nicht umbenennen oder entfernen. Sie können in Intune verwendete benutzerdefinierte Domänennamen hinzufügen, überprüfen oder entfernen, damit Ihre Geschäftsidentität eindeutig bleibt.

1. Wechseln Sie zum [Verwaltungsportal von Microsoft Office 365](https://portal.office.com/Admin/Default.aspx), und melden Sie sich über Ihr Administratorkonto an.

2. Wählen Sie im Navigationsbereich **Einrichtung** > **Domänen** > **Domäne hinzufügen** aus.

3. Geben Sie den Namen Ihrer benutzerdefinierten Domäne ein. Wählen Sie anschließend **Weiter** aus.

   ![Screenshot des Office 365 Admin Center, bei dem „Einstellungen“ > „Domänen“ ausgewählt wurde und ein neuer Domänenname hinzugefügt wird](./media/domain-custom-add.png)

4. Überprüfen Sie, ob Sie Besitzer der im vorherigen Schritt eingegebenen Domäne sind. 
    
    Durch das Auswählen von **Send Code via Email** (Code per E-Mail senden) wird an den registrierten Kontakt Ihrer Domäne eine E-Mail gesendet. Kopieren Sie nach dem Empfang der E-Mail den Code, und geben Sie diesen in das Feld **Type your verification code here** (Geben Sie Ihren Prüfcode hier ein) ein. Stimmt der Prüfcode überein, wird die Domäne zu Ihrem Mandanten hinzugefügt. Die angezeigte E-Mail kommt Ihnen möglicherweise nicht bekannt vor. Einige Registrierungsstellen blenden die tatsächliche E-Mail-Adresse aus, die bei der Registrierung der Domäne angegeben wurde.

   ![Screenshot des Office 365 Admin Center: Überprüfen des hinzugefügten Domänennamens](./media/domain-custom-verify.png)

   > [!NOTE]
   > Einzelheiten zur Überprüfung von TXT-Datensätzen finden Sie unter [Erstellen von DNS-Datensätzen bei jedem DNS-Hostinganbieter für Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Verwaltungsoberfläche

Es gibt zwei verschiedene Portale, die Sie verwenden können:
- Das Intune-Dashboard in Azure ([portal.azure.com](https://portal.azure.com)), auf dem Sie die [Funktionen von Intune](what-is-intune.md) erkunden können. In der Regel arbeiten Sie auf dem Intune-Dashboard.
- Das Office 365 Admin Center ([portal.office.com](https://portal.office.com)), in dem Sie Benutzer hinzufügen und verwalten können, wenn Sie dazu nicht Azure Active Directory verwenden. Sie können auch andere Aspekte Ihres Kontos verwalten, einschließlich Abrechnung und Support.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie ein kostenloses Abonnement erstellt, um Intune in einer Testumgebung zu testen, und Sie haben optional den Namen einer benutzerdefinierten Domäne konfiguriert. Weitere Informationen zu Microsoft Intune finden Sie im nächsten Schnellstart zum Hinzufügen von Benutzern und Zuweisen von Lizenzen.

> [!div class="nextstepaction"]
> [Erstellen eines Benutzers](get-started-users.md)
