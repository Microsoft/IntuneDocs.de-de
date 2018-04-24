---
title: Erstellen einer App-basierten bedingten Zugriffsrichtlinie für SharePoint Online
description: ''
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 05/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 5e2cf210dd46c062f9dcc9c68bcdaa3234519e5f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>Einrichten von App-basierten bedingten Zugriffsrichtlinien für SharePoint Online

[!INCLUDE [note for both-portals](../includes/note-for-both-portals.md)]

Dieses Thema enthält Anweisungen zum Einrichten von App-basierten bedingten Zugriffsrichtlinien für SharePoint Online. App-basierte bedingte Zugriffsrichtlinien unterstützen Administratoren dabei, nur mobile Apps zuzulassen, auf die App-Schutzrichtlinien von Intune angewendet wurden.

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>So erstellen Sie eine App-basierte bedingte Zugriffsrichtlinie für SharePoint Online

1. Navigieren Sie zum [Azure-Portal](https://portal.azure.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

    > [!NOTE]
    > Wenn Sie noch nicht mit dem Azure-Portal vertraut sind, lesen Sie das Thema [Azure-Portal für App-Schutzrichtlinien](azure-portal-for-microsoft-intune-mam-policies.md).

2. Wählen Sie im linken Menü **Weitere Dienste** aus, und geben Sie in das Filtertextfeld die Zeichenfolge **Intune** ein.

3. Wählen Sie **Intune-Schutz für Apps** > **Mobile Anwendungsverwaltung mit Intune** > **Alle Einstellungen** aus.

4. Wählen Sie auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“ die Kachel „SharePoint Online“ aus.

5. Wählen Sie auf dem Blatt **Zulässige Apps** die Option **Apps zulassen, die Intune-App-Richtlinien unterstützen**, um nur Apps zuzulassen, die von Intune-App-Schutzrichtlinien unterstützt werden.

    > [!NOTE] 
    > Bei Auswahl der Option, nur Apps zuzulassen, die von App-Schutzrichtlinien von Intune unterstützt werden, wird eine Liste der **unterstützten** Apps angezeigt.

    ![Screenshot des Blatts der zulässigen Apps mit der Liste der Apps](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>So weisen Sie App-basierte bedingte Zugriffsrichtlinien zu Benutzern zu

1. Öffnen Sie das Blatt **Eingeschränkte Benutzergruppen**, und wählen Sie dann **Benutzergruppe hinzufügen** aus.

2. Wählen Sie mindestens eine Benutzergruppe aus, auf die diese Richtlinie angewendet werden soll.

    ![Screenshot des Blatts „Eingeschränkte Benutzergruppen“ mit hervorgehobener Option „Benutzergruppe hinzufügen“](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > Möglicherweise möchten Sie, dass einige Benutzer in der Benutzergruppe, die Sie im vorherigen Schritt ausgewählt haben, nicht von dieser Richtlinie betroffen sind. In solchen Fällen fügen Sie die Gruppe der Benutzer der Liste der ausgenommenen Benutzergruppen hinzu. 

3. Wählen Sie auf dem Blatt **SharePoint Online** die Option **Exempted user groups** (Ausgenommene Benutzergruppen) und dann **Benutzergruppe hinzufügen** aus, um die Liste der Benutzergruppen zu öffnen.

4. Wählen Sie die Gruppen aus, die Sie von dieser Richtlinie ausnehmen möchten.  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>So ändern oder löschen Sie Benutzergruppen einer vorhandenen App-basierten bedingten Zugriffsrichtlinie

1. Öffnen Sie das Blatt **Eingeschränkte Benutzergruppen**, und markieren Sie die Benutzergruppe, die Sie löschen möchten.
2. Klicken Sie auf die Auslassungspunkte, um die Optionen für den Löschvorgang anzuzeigen.
3. Wählen Sie **Löschen** aus, um die Benutzergruppe aus der Liste zu entfernen.

> [!NOTE] 
> Sie können die Schritte befolgen, um eine Benutzergruppe aus der Liste **Exempted user groups** (Ausgenommene Benutzergruppen) zu entfernen.

## <a name="next-steps"></a>Nächste Schritte

[Blockieren von Apps, die keine moderne Authentifizierung verwenden](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>Siehe auch

[Protect app data with app protection policies (Schützen von App-Daten mithilfe von App-Schutzrichtlinien)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Konfigurieren des App-basierten bedingten Zugriffs für Exchange Online](mam-ca-for-exchange-online.md)
