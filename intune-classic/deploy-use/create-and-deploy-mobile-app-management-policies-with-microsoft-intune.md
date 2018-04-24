---
title: Erstellen und Bereitstellen von MAM-Richtlinien
description: Verwenden Sie die schrittweisen Anweisungen in diesem Thema zum Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c1b9a343-1737-4a65-a9c6-aca48acad11c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cc133071f4d6c0d1a3bbb3acc7c0bd5cb45b6cef
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-and-deploy-app-protection-policies-with-microsoft-intune"></a>Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Thema wird der Erstellungsvorgang einer App-Schutzrichtlinie im **Azure-Portal** beschrieben. Das Azure-Portal ist die neue Verwaltungskonsole zum Erstellen von App-Schutzrichtlinien, und wir empfehlen, dass Sie Ihre App-Schutzrichtlinien in diesem Portal erstellen. Das Azure-Portal unterstützt die folgenden MAM-Szenarien:

- Bei Intune registrierte Geräte
- Geräte, die mithilfe einer MDM-Lösung eines Drittanbieters verwaltet werden
- Geräte, die gar keiner Verwaltung durch eine MDM-Lösung unterliegen (BYOD).

> [!IMPORTANT]
> Hier sind ein paar Überlegungen, wenn Sie aktuell die **Intune-Verwaltungskonsole** zum Verwalten Ihrer Geräte verwenden:
> 
> * Sie können mithilfe der [Intune-Verwaltungskonsole](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) eine App-Schutzrichtlinie erstellen, die Apps für Geräte unterstützt, die bei Intune registriert sind.
> * Die App-Schutzrichtlinien, die in der Intune-Verwaltungskonsole erstellt wurden, können nicht ins Azure-Portal importiert werden.  Die App-Schutzrichtlinien müssen im Azure-Portal neu erstellt werden.
> 
> * Möglicherweise werden in der Intune-Verwaltungskonsole nicht alle App-Schutzrichtlinieneinstellungen angezeigt. Das Azure-Portal stellt die neue Verwaltungskonsole zum Erstellen von App-Schutzrichtlinien dar.
> 
> * Sie müssen in der Intune-Verwaltungskonsole eine App-Schutzrichtlinie erstellen, um verwaltete Apps bereitzustellen. In diesem Fall möchten Sie möglicherweise eine App-Schutzrichtlinie sowohl in der Intune-Verwaltungskonsole als auch im Azure-Portal erstellen: In der Intune-Verwaltungskonsole, um sicherzustellen, dass Sie verwaltete Apps bereitstellen können und im Azure-Portal, da es die neue Verwaltungskonsole darstellt, die über alle App-Schutzrichtlinieneinstellungen verfügt.
> 
> * Wenn Sie sowohl in der Intune-Verwaltungskonsole als auch im Azure-Portal App-Schutzrichtlinien erstellen, wird die im Azure-Portal erstellte Richtlinie auf die Apps angewendet.

Wählen Sie eins der folgenden Themen aus, um eine Liste der für die Plattformen Android und iOS unterstützten Richtlinieneinstellungen anzuzeigen:

> [!div class="op_single_selector"]
> - [iOS-Richtlinien](ios-mam-policy-settings.md)
> - [Android-Richtlinien](android-mam-policy-settings.md)

- Eine ausführlichere Beschreibung der Funktionsweise von App-Schutzrichtlinien und der von Intune App-Schutzrichtlinien unterstützten Szenarios finden Sie im Thema [Schützen von App-Daten mithilfe der Verwaltungsrichtlinien für mobile Anwendungen mit Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

##  <a name="create-an-app-protection-policy"></a>Erstellen einer App-Schutzrichtlinie
App-Schutzrichtlinien werden im Azure-Portal erstellt. Wenn Sie das Azure-Portal zum ersten Mal verwenden, lesen Sie [Azure portal for Microsoft Intune app protection policies (Azure-Portal für App-Schutzrichtlinien in Microsoft Intune)](azure-portal-for-microsoft-intune-mam-policies.md), um das Azure-Portal besser kennenzulernen. Überprüfen Sie vor dem Erstellen einer App-Schutzrichtlinie die Informationen zu [Voraussetzungen und Support](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md).

Gehen Sie folgendermaßen vor, um App-Schutzrichtlinien zu erstellen:

1. Navigieren Sie zum [Azure-Portal](https://portal.azure.com), und geben Sie Ihre-Anmeldeinformationen ein.

2. Wählen Sie **Weitere Dienste** aus, und geben Sie „Intune“ ein.

3. Wählen Sie **Intune-Schutz für Apps** aus.

4. Wählen Sie **Intune-Verwaltung von mobilen Anwendungen &gt; Einstellungen** aus, um das Blatt **Alle Einstellungen** zu öffnen.

    ![Screenshot des Blatts „Mobile Anwendungsverwaltung mit Intune“](../media/AppManagement/AzurePortal_MAM_Mainblade-2.png)

2.  Wählen Sie auf dem Blatt **Alle Einstellungen** **App-Richtlinie** aus. Hiermit wird das Blatt **App-Richtlinie** geöffnet, auf dem Sie neue Richtlinien erstellen und vorhandene bearbeiten können. Wählen Sie **Richtlinie hinzufügen** aus.

    ![Screenshot des Blatts „App-Richtlinie“ mit hervorgehobener Menüoption „Richtlinie hinzufügen“ ](../media/AppManagement/AzurePortal_MAM_AddPolicy.png)

3.  Geben Sie einen Namen für die Richtlinie sowie eine kurze Beschreibung ein, und wählen Sie den Plattformtyp aus, um eine Richtlinie für iOS oder Android zu erstellen. Sie können für jede Plattform mehr als eine Richtlinie erstellen.

    ![Screenshot des Blatts „Richtlinie hinzufügen“](../media/AppManagement/AzurePortal_MAM_AddPolicy_only.png)

4.  Wählen Sie **Apps** aus, um das Blatt **Apps** zu öffnen, auf dem eine Liste der verfügbaren Apps angezeigt wird. Wählen Sie eine oder mehrere Apps in der Liste aus, mit denen Sie die von Ihnen zu erstellende Richtlinie verknüpfen möchten. Nachdem Sie die Apps ausgewählt haben, wählen Sie **Auswählen** unten auf dem Blatt **Apps** aus, um Ihre Auswahl zu speichern.

    > [!IMPORTANT]
    > Sie müssen mindestens eine App auswählen, um eine Richtlinie erstellen zu können.

5.  Wählen Sie auf dem Blatt **Richtlinie hinzufügen** **Erforderliche Einstellungen konfigurieren** aus, um das Blatt mit den Richtlinieneinstellungen zu öffnen.

    Es gibt zwei Kategorien von Richtlinieneinstellungen: **Datenverlagerung** und **Zugriff**.  Richtlinien für die Datenverlagerung beziehen sich auf die Datenverschiebung in und aus Apps, während mit Zugriffsrichtlinien bestimmt wird, wie der Endbenutzer auf die Apps im beruflichen Kontext zugreift.
    Um Ihnen bei den ersten Schritten zu helfen, enthalten die Richtlinieneinstellung Standardwerte. Sie müssen keine Änderungen vornehmen, wenn die Standardwerte Ihren Anforderungen entsprechen.

    > [!TIP]
    > Diese Richtlinieneinstellungen werden nur durchgesetzt, wenn Apps im beruflichen Kontext verwendet werden.  Wenn der Endbenutzer die App zum Erledigen einer privaten Aufgabe verwendet, ist er von diesen Richtlinien nicht betroffen.

    ![Screenshot des Blatts „Einstellungen“ zusammen mit dem Blatt „Richtlinie hinzufügen“](../media/AppManagement/AzurePortal_MAM_PolicySettings.png)

6.  Wählen Sie **OK** aus, um diese Konfiguration zu speichern. Damit befinden Sie sich wieder auf dem Blatt **Richtlinie hinzufügen** . Wählen Sie **Erstellen** aus, um die Richtlinie zu erstellen und Ihre Einstellungen zu speichern.

    ![Screenshot eines Blatts „Richtlinie hinzufügen“ mit konfigurierten Apps und Einstellungen](../media/AppManagement/AzurePortal_MAM_CreatePolicy.png)

Wenn Sie mit dem Erstellen einer Richtlinie wie im vorherigen Verfahren beschrieben fertig sind, wird sie noch nicht für Benutzer bereitgestellt. Informationen zum Bereitstellen einer Richtlinie finden Sie im Abschnitt „Bereitstellen einer Richtlinie für Benutzer“.

> [!IMPORTANT]
> Wenn Sie eine App-Schutzrichtlinie für eine App mithilfe der Intune-Verwaltungskonsole und eine App-Schutzrichtlinie mithilfe des Azure-Portals erstellen, erhält die im Azure-Portal erstellte Richtlinie den Vorrang. Mit der Berichterstattung in der Intune- oder Configuration Manager-Verwaltungskonsole werden jedoch die Richtlinieneinstellungen zurückgegeben, die in der Intune-Verwaltungskonsole erstellt wurden. Beispiel:
>
> -   Sie haben eine App-Schutzrichtlinie in der Intune-Verwaltungskonsole erstellt, mit der Kopien aus einer Anwendung verhindert werden.
> -   Sie haben eine App-Schutzrichtlinie in der Azure-Konsole erstellt, die Kopien aus einer Anwendung zulässt.
> -   Sie führen beide Richtlinien in derselben App zusammen.
> -   Die Richtlinie, die Sie in der Azure-Verwaltungskonsole erstellt haben, hat Vorrang, und Kopien sind möglich.
> -   Status und Berichte der Intune-Verwaltungskonsole geben jedoch fälschlicherweise an, dass Kopien nicht möglich sind.

## <a name="line-of-business-lob-apps-optional"></a>Verwaltete branchenspezifische Apps (Line-of-Business, LOB) (optional)

Ab der Intune-Version 1703 haben Sie die Möglichkeit, LOB-Apps allgemein in Intune hinzuzufügen, wenn Sie eine neue App-Schutzrichtlinie erstellen. Dadurch erhalten Sie die Option, App-Schutzrichtlinien für LOB-Apps mithilfe des MAM SDK zu definieren, ohne dass Sie vollständige Berechtigungen für die App-Bereitstellung benötigen.
/intune/app-sdk-get-started
> [!TIP]
> Sie können LOB-Apps in Intune hinzufügen, wenn Sie den [Intune App SDK](/intune/app-sdk-get-started)-Workflow durchlaufen.

> [!IMPORTANT]
> Wenn Benutzer nur über bestimmte Berechtigungen zum Bereitstellen von MAM-Apps verfügen und nicht über vollständige Berechtigungen zur App-Bereitstellung, womit Sie beliebige Apps in Intune bereitstellen könnten, könnten Sie den Intune SDK-Workflow nicht durchlaufen, jedoch können Sie noch immer ihre LOB-Apps über den Workflow zur Erstellung der MAM-App-Schutzrichtlinie hinzufügen.

### <a name="to-add-lob-apps-ios-and-android"></a>Hinzufügen von branchenspezifischen Apps (iOS und Android)

1.  Wählen Sie auf dem Blatt „Richtlinie hinzufügen“ die Option „Konfigurieren von **Apps** aus, um das Blatt „Apps“ zu öffnen.

    ![MAM-Blatt „Richtlinie hinzufügen“](../media/AppManagement/mam-lob-apps-1.png)

2.  Klicken Sie auf **Weitere Apps**, und geben Sie dann die **Bündel-ID** (für iOS) und die **Paket-ID** (für Android) ein, und klicken Sie dann auf „Select to add your LOB apps“ (Auswählen, Ihre branchenspezifischen Apps hinzuzufügen).

    ![MAM-Blatt „Weitere Apps“](../media/AppManagement/mam-lob-apps-2.png)

### <a name="to-add-lob-apps-windows"></a>So fügen Sie branchenspezifische Apps hinzu (Windows)

> [!IMPORTANT]
> Sie müssen Windows 10 aus der Dropdown-Liste der Plattform auswählen, wenn Sie eine neue App-Schutzrichtlinie erstellen.

1. Wählen Sie auf dem Blatt „Richtlinie hinzufügen“ **Zulässige Apps** oder **Ausgenommene Apps** aus, um das Blatt „Allowed or Exempt apps“ (Zulässige oder ausgenommene Apps) zu öffnen.

   > [!NOTE]
   > 
   > - **Zulässige Apps**: Dies sind die Apps, die mit dieser Richtlinie übereinstimmen müssen.
   > - **Ausgeschlossene Apps**: Diese Apps sind von dieser Richtlinie ausgeschlossen und können ohne Einschränkungen auf Unternehmensdaten zugreifen.
   > <br></br>
2. Klicken Sie auf dem Blatt „Zulässige Apps“ oder „Ausgeschlossene Apps“ auf **Hinzufügen von Apps**. Sie können empfohlene Microsoft-Apps sowie Store- oder Desktop-Apps hinzufügen.

    ein.  **Empfohlene Apps:** Eine voraufgefüllte Liste der Apps (hauptsächlich Office), die Administratoren einfach in die Richtlinie importieren dürfen.

    b.  **Store-Apps:** Administratoren können eine beliebige App aus dem Windows Store in die Richtlinie einfügen.

    c.  **Windows Desktop-Apps:** Administratoren können traditionelle Windows Desktop-Apps der Richtlinie hinzufügen (z.B. .exe, .dll, usw.)

## <a name="deploy-a-policy-to-users"></a>Bereitstellen einer Richtlinie für Benutzer

1.  Wählen Sie auf dem Blatt **Richtlinie** **Benutzergruppen** aus. Damit wird das Blatt **Benutzergruppen**geöffnet. Wählen Sie auf dem Blatt **Benutzergruppen** **Benutzergruppe hinzufügen** aus, um das Blatt **Benutzergruppe hinzufügen** zu öffnen.

    ![Screenshot des Blatts „Benutzergruppen“ mit hervorgehobener Menüoption „Benutzergruppe hinzufügen“](../media/AppManagement/AzurePortal_MAM_AddUserstoPolicy.png)

2.  Auf dem Blatt **Benutzergruppe hinzufügen** wird eine Liste der Benutzergruppen angezeigt. Dies ist eine Liste aller Sicherheitsgruppen in Ihrem **Azure Active Directory**. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und anschließend **Auswählen**. Die Auswahl von **Auswählen** bewirkt die Bereitstellung der Richtlinie für Benutzer.

    ![Screenshot des Blatts „Benutzergruppe hinzufügen“ mit der Liste der Azure Active Directory-Benutzer](../media/AppManagement/AzurePortal_MAM_SelectUserstoDeploy.png)

    Damit haben Sie eine Richtlinie erstellt und für die Benutzer bereitgestellt.

Von der Richtlinie sind nur Benutzer betroffen, denen Intune-Lizenzen zugewiesen wurden. Benutzer, die sich in einer von Ihnen ausgewählten Sicherheitsgruppe befinden und die nicht über eine Intune-Lizenz verfügen, sind nicht betroffen.

>[!IMPORTANT]
> Wenn Sie Intune mit Configuration Manager verwenden, um Ihre iOS- und Android-Geräte zu verwalten, wird die Richtlinie nur auf Benutzer in der Gruppe angewendet, die Sie ausgewählt haben. Mitglieder untergeordneter Gruppen, die in der ausgewählten Gruppe geschachtelt sind, sind nicht betroffen.

Endbenutzer können die Apps aus dem App Store oder aus Google Play herunterladen. Weitere Informationen finden Sie in folgenden Quellen:
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-android)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-ios)

##  <a name="change-existing-policies"></a>Ändern vorhandener Richtlinien
Sie können eine vorhandene Richtlinie bearbeiten und sie auf die als Ziel festgelegten Benutzer anwenden. Wenn Sie vorhandene Richtlinien ändern, werden diese Änderungen für Benutzer, die bereits bei der App angemeldet sind, jedoch in den nächsten acht Stunden nicht wirksam.

Um die Auswirkungen der Änderungen sofort zu erfahren, muss der Endbenutzer sich bei der App abmelden und sich dann erneut anmelden.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>So ändern Sie die Liste der Apps, die einer Richtlinie zugeordnet sind

1.  Wählen Sie auf dem Blatt **App-Richtlinie** die Richtlinie aus, die Sie ändern möchten. Damit wird ein Blatt speziell für die Richtlinie geöffnet, die Sie soeben ausgewählt haben.

    ![Screenshot einer vorhandenen Richtlinie, die auf einem separaten Blatt geöffnet ist](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Wählen Sie auf diesem Richtlinienblatt **Ziel-Apps** aus, um eine Liste der Apps zu öffnen.

3.  Fügen Sie der Liste Apps hinzu, oder entfernen Sie Apps hieraus, und wählen Sie dann das Symbol **Speichern** aus, um die Änderungen zu speichern.

### <a name="to-change-the-list-of-user-groups"></a>So ändern Sie die Liste der Benutzergruppen

1.  Wählen Sie auf dem Blatt **App-Richtlinie** die Richtlinie aus, die Sie ändern möchten. Damit wird ein Blatt speziell für die Richtlinie geöffnet, die Sie soeben ausgewählt haben.

2.  Wählen Sie auf dem Richtlinienblatt **Benutzergruppen** aus, um das Blatt **Benutzergruppe** zu öffnen, auf dem die Liste der Benutzergruppen angezeigt wird, auf die die Richtlinie gegenwärtig angewendet wird.

3.  Zum Hinzufügen einer neuen Benutzergruppe wählen Sie **Benutzergruppe hinzufügen** und anschließend die Benutzergruppe aus. Wählen Sie **Auswählen** aus, um die Richtlinie für die ausgewählte Gruppe bereitzustellen.

    ![Screenshot des Blatts „Benutzergruppe hinzufügen“ mit zwei ausgewählten Benutzergruppen](../media/AppManagement/AzurePortal_MAM_ChangePolicy_SelectUser.png)

4.  Zum Löschen einer Benutzergruppe markieren Sie die Benutzergruppe, die Sie entfernen möchten. Anschließend wählen Sie die Auslassungspunkte (...) und die Option **Löschen** aus, um die Benutzergruppe zu entfernen.

    ![Screenshot mit Löschoption ](../media/AppManagement/AzurePortal_MAM_ChangePolicy_DeleteUser.png)

### <a name="to-change-policy-settings"></a>So ändern Sie Richtlinieneinstellungen

1.  Wählen Sie auf dem Blatt **App-Richtlinie** die Richtlinie aus, die Sie ändern möchten. Damit wird ein Blatt speziell für die Richtlinie geöffnet, die Sie soeben ausgewählt haben.

    ![Screenshot einer vorhandenen Richtlinie, die auf einem separaten Blatt geöffnet ist ](../media/AppManagement/AzurePortal_MAM_OpenPolicy.png)

2.  Wählen Sie **Richtlinieneinstellungen** aus, um das Blatt **Richtlinieneinstellungen** zu öffnen.

3.  Ändern Sie die Einstellungen, und wählen Sie das Symbol **Speichern** aus, um die Änderungen zu speichern.

    ![Screenshot des Blatts „Richtlinieneinstellungen“ mit der Menüoption „Speichern“ ganz oben](../media/AppManagement/AzurePortal_MAM_ChangePolicy_ChangeSettings.png)

## <a name="policy-settings"></a>Richtlinieneinstellungen
Eine vollständige Liste der Richtlinieneinstellungen für iOS und Android finden Sie in den folgenden Themen:

> [!div class="op_single_selector"]
> - [iOS-Richtlinien](ios-mam-policy-settings.md)
> - [Android-Richtlinien](android-mam-policy-settings.md)

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](monitor-mobile-app-management-policies-with-microsoft-intune.md)

### <a name="see-also"></a>Siehe auch
* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-android)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-ios)
