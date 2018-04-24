---
title: App-Zugriff für Exchange Online
description: In diesem Thema wird beschrieben, wie Sie eine Richtlinie für bedingten Zugriff für MAM-Apps konfigurieren können.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a64a5ac7f10bb7988c75dd473e1e87dae03959d4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>Erstellen eines bedingten Zugriffs für Exchange Online, um nur Apps zuzulassen, die von MAM unterstützt werden

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieses Thema bietet Ihnen eine ausführliche Anleitung, wie Sie den bedingten Zugriff für Exchange Online einrichten, um nur mobile Apps zuzulassen, die App-Schutzrichtlinie für Intune unterstützen.


## <a name="create-an-exchange-online-policy"></a>Erstellen einer Exchange Online-Richtlinie
1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, das das App-Zugriffsfeature enthält. Wenn Sie noch nicht mit dem Azure-Portal vertraut sind, lesen Sie das Thema [Azure-Portal für App-Schutzrichtlinien](azure-portal-for-microsoft-intune-mam-policies.md).

2.  Wählen Sie **Weitere Dienste** aus, und geben Sie „Intune“ ein.

3.  Wählen Sie **Intune-Schutz für Apps** aus.

4.  Wählen Sie auf dem Blatt **Mobile Anwendungsverwaltung mit Intune** **Alle Einstellungen** aus.

5.  Wählen Sie im Abschnitt **Bedingter Zugriff** **Exchange Online** aus.

    ![Screenshot des Blatts „Einstellungen“, das den Abschnitt „Bedingter Zugriff“ anzeigt, wobei die Option „Exchange Online“ hervorgehoben ist](../media/MAM-conditional-access-1.png)

6. Wählen Sie auf dem Blatt **Zulässige Apps** die Option **Allow apps that support Intune app policies** (Apps zulassen, die Intune-App-Richtlinien unterstützen), um nur Apps zuzulassen, die von Intune-App-Schutzrichtlinien unterstützt werden, damit sie auf Exchange Online zugreifen können. Wenn Sie diese Option auswählen, wird die Liste der unterstützten Apps angezeigt.

    >[!NOTE]
    >Alle E-Mail-Clients von Exchange Active Sync, einschließlich der integrierten E-Mail-Clients unter iOS und >Android, die eine Verbindung mit Exchange Online herstellen, werden daran gehindert, >E-Mails zu senden oder zu empfangen. Benutzer erhalten stattdessen eine einzige E-Mail, die sie darüber informiert, dass sie die >Outlook-E-Mail-App verwenden müssen.

7. Um diese Richtlinie auf Benutzer anzuwenden, öffnen Sie das Blatt **Eingeschränkte Benutzergruppen**, und wählen Sie **Benutzergruppe hinzufügen** aus. Wählen Sie mindestens eine Benutzergruppe aus, auf die diese Richtlinie angewendet werden soll.

    ![Screenshot des Blatts „Eingeschränkte Benutzergruppen“ mit hervorgehobener Option „Benutzergruppe hinzufügen“](../media/mam-ca-add-user-group.png)

8. Möglicherweise möchten Sie, dass einige Benutzer in der Benutzergruppe, die Sie im vorherigen Schritt ausgewählt haben, nicht von dieser Richtlinie betroffen sind. In solchen Fällen fügen Sie die Gruppe der Benutzer der Liste der ausgenommenen Benutzergruppen hinzu. Wählen Sie auf dem Blatt **Exchange Online** **Exempted user groups** (Ausgenommene Benutzergruppen) aus. Wählen Sie **Benutzergruppe hinzufügen** aus, um die Liste der Benutzergruppen zu öffnen. Wählen Sie die Gruppen aus, die Sie von dieser Richtlinie ausnehmen möchten.  

## <a name="modify-an-existing-policy"></a>Bearbeiten einer vorhandenen Richtlinie
### <a name="add-or-delete-user-groups"></a>Hinzufügen oder Löschen von Benutzergruppen

Um aus der Liste der **eingeschränkten Benutzergruppen** **eine Benutzergruppe zu löschen**, öffnen Sie das Blatt **Eingeschränkte Benutzergruppen**, markieren die Benutzergruppe, die Sie löschen möchten, und klicken auf die **Schaltfläche mit den drei Punkten (...)**, um die Option **Löschen** anzuzeigen. Wählen Sie **Löschen** aus, um die Benutzergruppe aus der Liste zu entfernen. Sie können genauso vorgehen, um eine Benutzergruppe aus der Liste **exempted user group** (Ausgenommene Benutzergruppen) zu entfernen.


## <a name="next-steps"></a>Nächste Schritte
[Blockieren von Apps, die über keine moderne Authentifizierung verfügen](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>Siehe auch
[Protect app data with app protection policies (Schützen von App-Daten mithilfe von App-Schutzrichtlinien)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
