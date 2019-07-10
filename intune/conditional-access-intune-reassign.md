---
title: Migrieren des bedingten Zugriffs zum Azure-Portal
titleSuffix: Microsoft Intune
description: Weisen Sie die Richtlinien für bedingten Zugriff, die Sie zuvor im klassischen Intune-Portal erstellt haben, im Azure-Portal erneut zu.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8bcc9aa527ed27ef35db901117ceb8f4c8d10c97
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546880"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Erneutes Zuweisen von Richtlinien für bedingten Zugriff aus dem klassischen Intune-Portal im Azure-Portal

Im neuen Azure-Portal unterstützt der bedingte Zugriff mehrere Richtlinien pro Anwendung und bietet bessere Anpassungsmöglichkeiten. Wenn Sie zuvor Richtlinien für bedingten Zugriff im klassischen Intune-Portal erstellt haben, können Sie diese zum Azure-Portal migrieren. 

## <a name="before-you-begin"></a>Vorbereitung

Wenn Sie dazu bereit sind, zum Azure-Portal zu wechseln, führen Sie die in diesem Thema angegebenen Schritte aus, um die Richtlinien für bedingten Zugriff, die Sie zuvor im klassischen Intune-Portal erstellt haben, erneut zuzuweisen:

- Erfassen Sie alle bereits erstellten Richtlinien für bedingten Zugriff, damit Sie wissen, welche Einstellungen Sie für die Neuzuweisung benötigen.

- Führen Sie die Schritte in diesem Thema aus, um diese Richtlinien im Azure-Portal neu zu erstellen.

- Deaktivieren Sie die bedingten Richtlinien im klassischen Intune-Portal, nachdem Sie überprüft haben, ob die neuen Richtlinien im Azure-Portal wie erwartet funktionieren.
<br /><br />
    - Planen Sie **vor dem Deaktivieren** der Richtlinien für bedingten Zugriff im klassischen Intune-Portal, auf welche Weise Sie die Benutzer zur neuen Richtlinie migrieren. Es gibt zwei Ansätze:
<br /><br />
        - **Verwenden Sie dieselbe Einschlussgruppe, um die im Azure-Portal erstellten Richtlinien anzuwenden, und erstellen Sie eine neue Ausnahmegruppe, die mit den vom klassischen Intune-Portal angewendeten Richtlinien verwendet wird**.
            - Verschieben Sie einige Benutzer allmählich in die Ausnahmegruppe, die im klassischen Portal angegeben ist. Dies verhindert, dass die Richtlinien, die das Ziel des klassischen Intune-Portals sind, angewendet werden. Die Richtlinien, die für die gleiche Benutzergruppe im Azure-Portal erstellt wurden und konzipiert sind, werden zusätzlich zu den im klassischen Intune-Portal angewendeten Richtlinien angewendet. 
<br /><br />
        - **Erstellen Sie eine neue Gruppe, auf die die Richtlinien für bedingten Zugriff im Azure-Portal angewendet werden sollen**. Wenn Sie sich für diese Vorgehensweise entscheiden, müssen Sie folgende Aktionen ausführen:
            - Entfernen Sie Benutzer nach und nach aus den Sicherheitsgruppen, auf die Richtlinien für bedingten Zugriff des klassischen Intune-Portals angewendet werden.
            - Nachdem Sie bestätigt haben, dass die neue Richtlinie für diese Benutzer funktioniert, können Sie die Richtlinie im klassischen Intune-Portal deaktivieren. 
<br /><br />
- Wenn Sie die Einstellungen der Richtlinie für bedingten Zugriff so konfiguriert haben, dass Exchange ActiveSync (EAS) im klassischen Intune-Portal verwendet wird, lesen Sie die [Anweisungen in diesem Thema](#reassign-intune-device-based-conditional-access-policies-for-eas-clients), um **die Einstellungen der Richtlinie für bedingten Zugriff für EAS im Azure-Portal erneut zuzuweisen**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>So überprüfen Sie Ihre Richtlinien für den gerätebasierten bedingten Zugriff im klassischen Intune-Portal

1. Wechseln Sie zum [klassischen Intune-Portal](https://manage.microsoft.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

2. Wählen Sie **Richtlinie** im linken Menü aus.

3. Wählen Sie **Bedingter Zugriff** und anschließend den Microsoft-Clouddienst (z.B. Exchange Online oder SharePoint Online) aus, für den Sie eine Richtlinie für bedingten Zugriff erstellt haben.

4. Notieren Sie sich die Einstellungen für den bedingten Zugriff, und beziehen Sie sich auf diese Notizen, wenn Sie die gleichen Richtlinien für bedingten Zugriff im Azure-Portal erstellen.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Richtlinien für den App- und gerätebasierten bedingten Zugriff im gemeinsamen Einsatz

Das Blatt **Intune-App-Schutz** im Azure-Portal erlaubt Administratoren, App-basierte bedingte Regeln festzulegen, sodass nur Apps, die die App-Schutzrichtlinien von Intune unterstützen, auf Unternehmensressourcen zugreifen dürfen. Diese Richtlinien für den App-basierten bedingten Zugriff können sich mit Richtlinien für den gerätebasierten bedingten Zugriff überschneiden. Sie können die gerätebasierte und App-basierte bedingte Richtlinie kombinieren (logischer UND-Vorgang) oder eine Option bereitstellen (logischer ODER-Vorgang). Folgende Anforderungen können für Ihre Richtlinie für bedingten Zugriff gelten:

- Ein kompatibles Gerät **UND** die Verwendung der genehmigten App sind erforderlich.
    - Sie müssen Ihre Richtlinie für bedingten Zugriff auf dem Blatt [Bedingter Zugriff für Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) und dem Blatt [Intune-App-Schutz](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0) festlegen.
<br /><br />
- Ein kompatibles Gerät **ODER** die Verwendung der genehmigten App sind erforderlich.
    - Sie müssen Ihre Richtlinie für den bedingten Zugriff im [klassischen Intune-Portal](https://manage.microsoft.com) und auf dem Blatt [Intune-App-Schutz](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0) festlegen.

> [!TIP] 
> Dieses Thema enthält Screenshots, die die Benutzererfahrung im klassischen Intune-Portal und dem Azure-Portal vergleichen.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Erneutes Zuweisen von Richtlinien für den gerätebasierten bedingten Zugriff für Intune

1. Wechseln Sie im Azure-Portal zum Blatt [Bedingter Zugriff](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies), und melden Sie sich mit Ihren Anmeldeinformationen an.

2. Wählen Sie **Neue Richtlinie** aus.

3. Geben Sie einen Namen für die Richtlinie an.

4. Wählen Sie im Abschnitt **Zuweisungen** die Option **Benutzer und Gruppen** aus, um die neue Richtlinie für bedingten Zugriff festzulegen.

    ![Darstellung eines Vergleichs der Benutzergruppen-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Diese Auswahl, die Sie für das Azure-Portal treffen, muss mit der Auswahl übereinstimmen, die Sie bereits für das klassische Portal getroffen haben. Wenn Sie z.B. alle Benutzer im klassischen Intune-Portal ausgewählt haben, wählen Sie im Azure-Portal **Alle Benutzer** aus. Wenn Sie darüber hinaus die Option **Ausgenommene Gruppen** im klassischen Intune-Portal ausgewählt haben, schließen Sie diese ausgewählten Gruppen im Azure-Portal aus.

5. Nachdem Sie Ihre Gruppe ausgewählt haben, wählen Sie **Auswählen** aus, und klicken Sie dann auf **Fertig**.

6. Wählen Sie **Cloud-Apps** unter dem Abschnitt **Zuweisungen** aus.

7. Wählen Sie auf dem **Cloud-Apps**-Blatt **Apps auswählen** aus.

8. Wählen Sie die App aus, auf die Sie die neue Richtlinie für bedingten Zugriff anwenden möchten, und klicken Sie auf **Auswählen**.

9. Klicken Sie auf **Fertig**.

    ![Darstellung eines Vergleichs der Cloud-App-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-3.png)

    > [!TIP] 
    > Wenn Sie mehrere Apps mit derselben Richtlinie haben, ziehen Sie in Betracht, sie in einer einzelnen Richtlinie im Azure-Portal zu konsolidieren.

10. Wählen Sie **Bedingungen** unter dem Abschnitt **Zuweisungen** aus.

11. Wählen Sie auf dem Blatt **Bedingungen** die Option **Geräteplattformen** aus, dann wählen Sie die zutreffende Geräteplattform aus.

12. Sobald Sie damit fertig sind, klicken Sie zweimal auf **Fertig**.

    ![Darstellung eines Vergleichs der Geräteplattform-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-4.png)

    > [!TIP] 
    > Wenn Sie einzelne Plattformen im klassischen Intune-Portal ausgewählt haben, wählen Sie die einzelnen Plattformen im Azure-Portal aus.

    > [!NOTE] 
    > Sie können später den Domänenbeitritt oder kompatible Optionen für Windows angeben.

13. Wählen Sie **Bedingungen** unter dem Abschnitt **Zuweisungen** aus.

14. Wählen Sie auf dem Blatt **Bedingungen** **Client-Apps** aus, wählen Sie dann die zutreffende Client-App aus.

15. Sobald Sie damit fertig sind, klicken Sie auf zweimal auf **Fertig**.

    ![Darstellung eines Vergleichs der Client-App-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-6.png)

16. Wenn Sie die Browsereinstellungen im klassischen Intune-Portal ausgewählt haben, wählen Sie jeweils **Browser** und **Mobile Apps und Desktopclients** im Azure-Portal aus. Wählen Sie für den Fall, dass Sie nicht die Browsereinstellungen im klassischen Intune-Portal ausgewählt haben, nur **Mobile Apps und Desktopclients** aus. 

17. Wählen Sie im Abschnitt **Zugriffssteuerung** die Option **Grant** (Gewähren) aus.

18. Wählen Sie **Markieren des Geräts als kompatibel erforderlich** unter **Grant Access Controls** (Zugriffssteuerungen gewähren) aus, klicken Sie dann auf **Auswählen**.

19. Wenn Sie eine Richtlinie besitzen, die mit einer Domäne verknüpfte Windows-Geräte erfordert, und Sie auch in Intune registrierte und mit Windows kompatible Geräte zulassen, wählen Sie **In Domäne eingebundenes Gerät anfordern** und **Markieren des Geräts als kompatibel erforderlich** zusammen mit **Eine der ausgewählten Kontrollen anfordern** aus.

20. Wenn Sie keine mit Intune registrierten und mit Windows kompatiblen Geräte erlauben, schließen Sie Windows-Richtlinien von der aktuellen Richtlinie aus. Erstellen Sie anschließend eine separate Richtlinie, für die **Geräteplattformen** auf **Windows** festgelegt sind, einschließlich der anderen Bedingungen, die wie oben festgelegt sind. Wählen Sie dann **In Domäne eingebundenes Gerät anfordern** unter **Grant Access Controls** (Zugriffssteuerungen genehmigen) aus.

21. Aktivieren Sie auf dem Blatt **Neu** der Richtlinie für bedingten Zugriff die Umschaltfläche **Richtlinie aktivieren**, und klicken Sie dann auf **Erstellen**.

    ![Vergleich der Benutzeroberfläche zum Aktivieren der Richtlinie für bedingten Zugriff zwischen Intune und Azure](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Erneutes Zuweisen von Richtlinien für den gerätebasierten bedingten Zugriff für EAS-Clients für Intune

Wenn Sie im Rahmen einer Exchange Online-Richtlinie Exchange ActiveSync-Einstellungen im klassischen Intune-Portal konfiguriert haben, müssen Sie eine zweite Richtlinie für bedingten Zugriff im Azure-Portal erstellen.

1. Wechseln Sie im Azure-Portal zum Blatt [Bedingter Zugriff](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies), und melden Sie sich mit Ihren Anmeldeinformationen an.

2. Wählen Sie **Neue Richtlinie** aus.

3. Geben Sie einen Namen für die Richtlinie an.

4. Wählen Sie im Abschnitt **Zuweisungen** die Option **Benutzer und Gruppen** aus, um die neue Richtlinie für bedingten Zugriff festzulegen.

    ![Vergleich der Benutzeroberflächen der Benutzergruppen zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Diese Auswahl, die Sie für das Azure-Portal treffen, muss mit der Auswahl übereinstimmen, die Sie bereits für das Azure-Portal getroffen haben. Wenn Sie z.B. alle Benutzer im klassischen Intune-Portal ausgewählt haben, wählen Sie im Azure-Portal **Alle Benutzer** aus. Wenn Sie darüber hinaus die Option **Ausgenommene Gruppen** im klassischen Intune-Portal ausgewählt haben, schließen Sie diese ausgewählten Gruppen im Azure-Portal aus.

5. Nachdem Sie Ihre Gruppe ausgewählt haben, wählen Sie **Auswählen** aus, und klicken Sie dann auf **Fertig**.

6. Wählen Sie **Cloud-Apps** unter dem Abschnitt **Zuweisungen** aus.

7. Klicken Sie auf dem Blatt **Cloud-Apps** auf **Apps auswählen**, und wählen Sie **Exchange Online** aus. Klicken Sie dann auf **Auswählen** und **Fertig**.

    ![Darstellung eines Vergleichs der Cloud-Apps-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Bedingte Zugriffsrichtlinien für EAS-Clients können keine andere Cloud-App enthalten.

8. Wählen Sie auf dem Blatt **Bedingungen** **Client-Apps** aus, wählen Sie dann die zutreffende Client-App aus. Wenn Sie Clients blockieren möchten, die nicht von Intune unterstützt werden, verwenden Sie die Option **Richtlinie nur auf unterstützte Plattformen anwenden**.

    ![Vergleich der Client-Apps-Benutzeroberfläche zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-15.png)

9. Sobald Sie damit fertig sind, klicken Sie auf zweimal auf **Fertig**.

10. Wählen Sie im Abschnitt **Zugriffssteuerung** die Option **Grant** (Gewähren) aus.

11. Wählen Sie **Markieren des Geräts als kompatibel erforderlich** unter **Grant Access Controls** (Zugriffssteuerungen gewähren) aus, klicken Sie dann auf **Auswählen**.

    ![Vergleich der Benutzeroberfläche zum Gewähren des Zugriffs zwischen dem Intune- und dem Azure-Portal](./media/reassign-ca-16.png)

12. Aktivieren Sie auf dem Blatt **Neu** der Richtlinie für bedingten Zugriff die Umschaltfläche **Richtlinie aktivieren**, und klicken Sie dann auf **Erstellen**.

    ![Vergleich der Benutzeroberfläche zum Aktivieren der Richtlinie für bedingten Zugriff zwischen Intune und Azure](./media/reassign-ca-17.png)

> [!NOTE]
> Wenn Sie **Geräteplattformen** konfigurieren, schlägt das Speichern der Richtlinie mit der Fehlermeldung „Policy configuration is not supported“ (Die Richtlinienkonfiguration wird nicht unterstützt) fehl. Exchange ActiveSync kann die vom verbindenden Gerät verwendete Plattform nicht identifizieren. Aus diesem Grund wird das Konfigurieren von spezifischen Geräteplattformen bei der Erstellung einer Richtlinie für Exchange ActiveSync-Geräte nicht unterstützt.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Deaktivieren von Richtlinien für bedingten Zugriff im klassischen Intune-Portal

Sobald Sie Ihre Richtlinien für bedingten Zugriff im Azure-Portal neu zugewiesen haben, ist es wichtig, dass Sie die Richtlinien für bedingten Zugriff, die Sie zuvor im klassischen Intune-Portal erstellt haben, nach und nach deaktivieren. Darüber hinaus müssen Sie möglicherweise die gleiche Sicherheitsgruppe verwenden, um die im Azure-Portal erstellten Richtlinien für bedingten Zugriff anzuwenden.

> [!NOTE]
> Sehen Sie sich den Abschnitt mit den [Vorbereitungen](#before-you-begin) zu Beginn dieses Themas an, bevor Sie Ihre Richtlinien für bedingten Zugriff im klassischen Intune-Portal deaktivieren.

### <a name="to-disable-the-conditional-access-policies"></a>So deaktivieren Sie die Richtlinien für bedingten Zugriff

1. Wechseln Sie zum [klassischen Intune-Portal](https://manage.microsoft.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

2. Wählen Sie **Richtlinie** im linken Menü aus.

3. Wählen Sie **Bedingter Zugriff** und anschließend den Microsoft-Clouddienst (z.B. Exchange Online oder SharePoint Online) aus, für den Sie eine Richtlinie für bedingten Zugriff erstellt haben.

4. Deaktivieren Sie die Option **Richtlinie für bedingten Zugriff aktivieren**, und klicken Sie dann auf **Speichern**.

    ![Abbildung: Deaktivieren von Richtlinien für bedingten Zugriff im klassischen Intune-Portal](./media/reassign-ca-18.png)

## <a name="see-also"></a>Siehe auch

- [Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs mit Intune](conditional-access-intune-common-ways-use.md)
- [App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md)
- [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
