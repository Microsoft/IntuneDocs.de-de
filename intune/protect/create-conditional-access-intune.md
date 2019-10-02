---
title: Einrichten des gerätebasierten bedingten Zugriffs mit Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie eine gerätebasierte Richtlinie für bedingten Zugriff auf Grundlage der Gerätekonformität und der Verwaltung mobiler Apps in Microsoft Intune erstellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e27997b45f0a68f6eb9247c69fafc363787fb457
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722591"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Erstellen einer gerätebasierten Richtlinie für bedingten Zugriff

In Intune können Sie den bedingten Zugriff in Azure Active Directory erweitern, indem Sie den Zugriffssteuerungen Informationen zur Konformität mobiler Geräte hinzufügen. Nachdem Sie eine Intune-Konformitätsrichtlinie erstellt haben, die die Voraussetzungen für die Konformität von Geräten definiert, können Sie den Konformitätsstatus eines Geräts verwenden, um den Zugriff auf Ihre Apps und Dienste zuzulassen oder zu blockieren. Erstellen Sie zu diesem Zweck eine Richtlinie für bedingten Zugriff, die die Einstellung **Markieren des Geräts als kompatibel erforderlich** verwendet.  

Eine Richtlinie für bedingten Zugriff gibt die Apps oder Dienste an, die Sie schützen möchten, die Bedingungen, unter denen auf die Apps oder Dienste zugegriffen werden kann, und die Benutzer, auf die die Richtlinie zutrifft. Der bedingte Zugriff ist ein Azure AD-Premium-Feature, das in Azure Active Directory konfiguriert werden kann. Sie können die gleichen Richtlinien aber auch im Intune-Portal einrichten. Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird.  

> [!IMPORTANT]
> Bevor Sie den bedingten Zugriff einrichten, müssen Sie Intune-Gerätekonformitätsrichtlinien festlegen, um Geräte danach zu bewerten, ob sie bestimmte Voraussetzungen erfüllen. Informationen dazu finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Erstellen einer Richtlinie für bedingten Zugriff

1. Klicken Sie im Intune-Portal auf **Bedingter Zugriff** > **Richtlinien** > **Neue Richtlinie**.
   
    ![Erstellen einer neuen Richtlinie für bedingten Zugriff](./media/create-conditional-access-intune/create-ca.png)
 
2. Klicken Sie unter **Zuweisungen** auf **Benutzer und Gruppen**. 
3. Identifizieren Sie auf der Registerkarte **Einschließen** die Benutzer oder Benutzergruppen, auf die diese Richtlinie für bedingten Zugriff angewendet werden soll. Wenn Sie die einzuschließenden Benutzer und Gruppen ausgewählt haben, können Sie die Registerkarte **Ausschließen** verwenden, um ggf. Benutzer, Rollen oder Gruppen von dieser Richtlinie auszuschließen.  
    - **Alle Benutzer**: Wählen Sie diese Option aus, um die Richtlinie auf alle Benutzer und Gruppen anzuwenden, einschließlich interner Benutzer und Gastbenutzer.
  
    - **Benutzer und Gruppen auswählen**: Wählen Sie diese Option aus, und geben Sie mindestens eine der folgenden Optionen an:
  
      ein. **Sämtliche Gastbenutzer**: Mit dieser Option können Sie externe Gastbenutzer (z.B. Partner oder externe Projektmitarbeiter) ein- oder ausschließen.
       
      b. **Verzeichnisrollen**: Wählen Sie eine oder mehrere Azure AD-Rollen aus, um Benutzer ein- oder auszuschließen, denen diese Rollen zugewiesen wurden.
      
      c. **Benutzer und Gruppen**: Mit dieser Option können Sie nach einzelnen Benutzern oder Gruppen suchen, die Sie ein- oder ausschließen möchten, und diese auswählen.
     
       > [!TIP]  
       > Testen Sie die Richtlinie mit einer kleineren Benutzergruppe, um sicherzustellen, dass sie wie erwartet funktioniert.
4. Wählen Sie **Fertig** aus.
5. Klicken Sie unter **Zuweisungen** auf **Cloud-Apps**. 
6. Identifizieren Sie auf der Registerkarte **Einschließen** die Apps und Dienste, die Sie mit dieser Richtlinie für bedingten Zugriff schützen möchten. Danach können Sie auf der Registerkarte **Ausschließen** verwenden, um ggf. Apps oder Dienste von dieser Richtlinie auszuschließen.
    - **Alle Cloud-Apps**: Wählen Sie diese Option aus, um die Richtlinie auf alle Apps anzuwenden.
      > [!IMPORTANT]  
      > Die Microsoft Azure Management-App für den Zugriff auf das Azure-Portal ist in dieser Liste enthalten. Verwenden Sie unbedingt die Registerkarte **Ausschließen** hier oder unter den Optionen für **Benutzer und Gruppen**, um sicherzustellen, dass Sie (bzw. die von Ihnen festgelegten Benutzer oder Gruppen) weiterhin in der Lage sind, sich beim Azure-Portal anzumelden. 

    - **Apps auswählen**: Aktivieren Sie diese Option, klicken Sie auf **Auswählen**, und verwenden Sie dann die Anwendungsliste, um die Apps und Dienste zu suchen und auszuwählen, die Sie schützen möchten.
    
      ![Erstellen einer neuen Richtlinie für bedingten Zugriff](./media/create-conditional-access-intune/create-ca-select-apps.png)

7. Wählen Sie **Fertig** aus.
8. Klicken Sie unter **Zuweisungen** auf **Bedingungen**.
    - **Anmelderisiko**: Klicken Sie auf „Ja“, um das Azure AD Identity Protection-Feature zum Erkennen von Anmelderisiken mit dieser Richtlinie zu verwenden. Wählen Sie dann die Risikoebenen aus, auf denen diese Richtlinie angewendet werden soll.
    - **Geräteplattformen**: Identifizieren Sie auf der Registerkarte **Einschließen** die Geräteplattformen, auf die diese Richtlinie für bedingten Zugriff angewendet werden soll. Verwenden Sie die Registerkarte **Ausschließen**, um Plattformen von dieser Richtlinie auszuschließen.
    - **Standorte**: Geben Sie auf der Registerkarte **Einschließen** an, wo die Richtlinie angewendet werden soll: auf jeden Standort, auf vertrauenswürdige Netzwerkadressen, die sich unter der Kontrolle Ihrer IT-Abteilung befinden, oder auf bestimmte Netzwerkadressen. Verwenden Sie die Registerkarte **Ausschließen**, um Netzwerkadressen von dieser Richtlinie auszuschließen. 
    - **Client-Apps**: Klicken Sie auf **Ja**, um festzulegen, dass die Richtlinie auf Browser-Apps, mobile Apps und Desktopclients angewendet werden soll. Sie können auch **Clients mit moderner Authentifizierung** (z.B. Outlook für iOS oder Outlook für Android) und **Exchange ActiveSync-Clients** auswählen.
    - **Gerätezustand**: Die Richtlinie für bedingten Zugriff gilt für alle Gerätezustände, es sei denn, Sie wählen hier „Ja“ aus und schließen die Zustände „Gerät in Hybrid-Azure AD eingebunden“ oder „Gerät als konform markiert“ (oder beide) explizit aus.
    
      ![Erstellen einer neuen Richtlinie für bedingten Zugriff](./media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Wenn Sie sowohl Clients mit **moderner Authentifizierung** als auch **Exchange ActiveSync-Clients** schützen möchten, erstellen Sie zwei separate Richtlinien für bedingten Zugriff – eine für jeden Clienttyp. Exchange Active Sync unterstützt zwar die moderne Authentifizierung, ist die einzige von Exchange Active Sync unterstützte Bedingung die Plattform. Andere Bedingungen wie z.B. die mehrstufige Authentifizierung werden nicht unterstützt. Um den Zugriff von Exchange ActiveSync auf Exchange Online effektiv zu schützen, erstellen Sie eine Richtlinie für bedingten Zugriff, die die Cloud-App „Office 365 Exchange Online“ und die Client-App „Exchange ActiveSync“ mit aktivierter Einstellung „Richtlinie nur auf unterstützte Plattformen anwenden“ festlegt.

9. Wählen Sie **Fertig** aus.
10. Klicken Sie unter **Zugriffssteuerungen** auf **Gewähren**. Konfigurieren Sie Aktionen basierend auf den von Ihnen festgelegten Bedingungen.  Sie können eine der folgenden Optionen aktivieren:
    - **Zugriff blockieren**: Die Benutzer, für die diese Richtlinie gilt, erhalten unter den von Ihnen angegebenen Bedingungen keinen Zugriff auf die Apps.
    - **Zugriff gewähren**: Den Benutzern, für die diese Richtlinie gilt, wird Zugriff gewährt, Sie können jedoch eine oder mehrere der folgenden Aktionen anfordern:
      - **Mehrstufige Authentifizierung erforderlich**: Benutzer müssen weitere Aktionen hinsichtlich der Sicherheit durchführen, z.B. per Telefonanruf oder SMS.
      - **Markieren des Geräts als kompatibel erforderlich**: Das Gerät muss mit Intune konform sein. Wenn das Gerät nicht konform ist, erhält der Benutzer die Option, das Gerät bei Intune zu registrieren. 
      - **Gerät mit Hybrid Azure-AD-Einbindung erforderlich**: Das Gerät muss in Azure AD Hybrid eingebunden sein.
      - **Genehmigte Client-App erforderlich**: Das Gerät muss genehmigte Client-Apps verwenden. 
      - **Für mehrere Steuerelemente**: Wählen Sie **Alle ausgewählten Steuerelemente anfordern** aus, damit alle oben genannten Anforderungen erzwungen werden, wenn ein Gerät versucht, auf die App zuzugreifen.
    
      ![Zugriffssteuerungen, Einstellungen für „Gewähren“](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. Klicken Sie unter **Richtlinie aktivieren** auf **Ein**.
     
     ![Aktivieren der Richtlinie](./media/create-conditional-access-intune/enable-policy.png)

12. Wählen Sie **Erstellen** aus.

## <a name="see-also"></a>Siehe auch
[App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md)

[Problembehandlung beim bedingten Zugriff in Intune](https://support.microsoft.com/help/4456106)
