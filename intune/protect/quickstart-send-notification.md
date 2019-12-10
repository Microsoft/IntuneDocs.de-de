---
title: 'Schnellstart: Senden von Benachrichtigungen an nicht konforme Geräte'
titleSuffix: Microsoft Intune
description: In diesem Schnellstart verwenden Sie Microsoft Intune zum Senden von E-Mail-Benachrichtigungen an nicht konforme Geräte.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410242"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Schnellstart: Senden von Benachrichtigungen an nicht konforme Geräte

In diesem Schnellstart verwenden Sie Microsoft Intune zum Senden von E-Mail-Benachrichtigungen an Mitarbeiter mit nicht konformen Geräten.

Wenn Intune ein Gerät erkennt, das nicht konform ist, kennzeichnet Intune dieses standardmäßig als „nicht konform“. Das Gerät wird dann durch den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) von Azure Active Directory (Azure AD) blockiert. Mit Intune können Sie Aktionen bei Nichtkonformität hinzufügen, was Ihnen Flexibilität beim Ermitteln der Vorgehensweise verschafft, wenn ein Gerät nicht konform ist. Beispielsweise können Sie Benutzern eine Toleranzperiode gewähren, in der sie die Konformität wiederherstellen können, bevor nicht konforme Geräte blockiert werden.

Eine Aktion, die ausgeführt wird, wenn ein Gerät die Konformitätsanforderungen nicht erfüllt, besteht darin, eine E-Mail an den Gerätebenutzer zu senden. Sie können E-Mail-Benachrichtigungen vor dem Senden auch anpassen. Sie können Empfänger, Betreff und Nachrichtentext, Unternehmenslogos und Kontaktinformationen anpassen. Außerdem bezieht Intune Einzelheiten zu dem nicht konformen Gerät in die E-Mail-Benachrichtigung mit ein.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen

Wenn Sie Gerätekonformitätsrichtlinien verwenden, um den Zugriff auf Unternehmensressourcen durch Geräte zu blockieren, muss der bedingte Zugriff von Azure AD eingerichtet sein. Wenn Sie den Schnellstart [Erstellen einer Gerätekonformitätsrichtlinie](quickstart-set-password-length-android.md) abgeschlossen haben, verwenden Sie Azure Active Directory. Weitere Informationen zu Azure AD finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) und [Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs mit Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) als [globaler Administrator](../fundamentals/users-add.md#types-of-administrators) oder [Intune-Dienstadministrator](../fundamentals/users-add.md#types-of-administrators) an. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des Unternehmensadministrators.

## <a name="create-a-notification-message-template"></a>Erstellen einer Benachrichtigungsvorlage

Zum Senden einer E-Mail an Ihre Benutzer müssen Sie eine Benachrichtigungsvorlage erstellen. Wenn ein Gerät nicht konform ist, werden die Einzelheiten, die Sie in die Vorlage eingeben, in den von Ihnen an die Benutzer gesendeten E-Mails angezeigt.

1. Klicken Sie in Intune auf **Geräte** > **Compliance policies** > **Benachrichtigung** > **Create notification** (Konformitätsrichtlinien > Benachrichtigung erstellen).
2. Geben Sie die folgenden Informationen ein:

   - **Name**: *Contoso Admin*
   - **Betreff**: *Gerätekompatibilität*
   - **Nachricht**: *Ihr Gerät entspricht derzeit nicht den Complianceanforderungen des Unternehmens.*
   - **E-Mail-Kopfzeile: Unternehmenslogo einschließen**: Auf **Aktiviert** festgelegt, um das Logo Ihrer Organisation zu zeigen.
   - **E-Mail-Fußzeile: Unternehmensnamen einschließen**: Auf **Aktiviert** festgelegt, um den Namen Ihrer Organisation zu zeigen.
   - **E-Mail-Fußzeile: Kontaktinformationen einschließen**: Auf **Aktiviert** festgelegt, um die Kontaktinformationen Ihrer Organisation zu zeigen.

   ![Beispiel einer Benachrichtigung zur Konformität in Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Klicken Sie auf **Weiter**, und überprüfen Sie Ihre Benachrichtigung. Klicken Sie auf **Erstellen**. Die Benachrichtigungsvorlage kann nun verwendet werden.

   > [!NOTE]
   > Sie können auch eine zuvor erstellte Benachrichtigungsvorlage bearbeiten.

Ausführliche Informationen zum Festlegen von Firmenname, Firmenkontaktinformationen und Firmenlogo finden Sie in den folgenden Artikeln:

- [Unternehmensinformationen und Datenschutzerklärung](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Supportinformationen](../apps/company-portal-app.md#support-information)
- [Anpassen der Unternehmensmarkenidentität](../apps/company-portal-app.md#company-identity-branding-customization)

## <a name="add-a-noncompliance-policy"></a>Hinzufügen einer Richtlinie für Nichtkonformität

Wenn Sie eine Konformitätsrichtlinie für Geräte erstellen, erstellt Intune automatisch eine Aktion für Nichtkonformität. Intune kennzeichnet Geräte dann als nicht konform, wenn sie die Konformitätsrichtlinie nicht erfüllen. Sie können anpassen, wie lange das Gerät als „nicht konform“ gekennzeichnet wird. Sie können beim Erstellen einer Konformitätsrichtlinie oder beim Aktualisieren einer vorhandenen Konformitätsrichtlinie auch eine andere Aktion hinzufügen.

Mit den folgenden Schritten wird eine Konformitätsrichtlinie für Windows 10-Geräte erstellt.

1. Klicken Sie in Intune auf **Geräte** > **Compliance Policies** > **Richtlinie erstellen** (Konformitätsrichtlinien).

2. Geben Sie die folgenden Informationen ein:

   - **Name**: *Windows 10-Kompatibilität*
   - **Beschreibung**: *Windows 10-Kompatibilitätsrichtlinie*
   - **Plattform**: Windows 10 und höher

3. Klicken Sie auf **Einstellungen** > **Systemsicherheit**, um die sicherheitsbezogenen Geräteeinstellungen anzuzeigen.

4. Konfigurieren Sie die folgenden Optionen:

   - Legen Sie **Anfordern** für die Option **Kennwort zum Entsperren mobiler Geräte erforderlich** fest. Mit dieser Einstellung wird festgelegt, ob Benutzer ein Kennwort eingeben müssen, damit auf die Daten auf ihren mobilen Geräten zugegriffen werden kann.

   - Legen Sie die **minimale Kennwortlänge** auf **6** fest. Mit dieser Einstellung wird die Mindestanzahl an Zahlen oder Zeichen im Kennwort festgelegt.

   ![Systemsicherheitseinstellungen für eine neue Konformitätsrichtlinie](./media/quickstart-send-notification/system-security-settings-01.png)

5. Wählen Sie **OK** > **OK** > **Erstellen** aus, um Ihre Konformitätsrichtlinie zu erstellen.

6. Klicken Sie auf **Eigenschaften** > **Aktion bei Nichtkonformität** > **Hinzufügen**.

7. Vergewissern Sie sich, dass **Send email to end users** (E-Mail an Endbenutzer senden) im Dropdownfeld **Aktion** ausgewählt ist.

8. Klicken Sie auf **Message template** (Nachrichtenvorlage), und wählen Sie die zuvor in diesem Artikel erstellte Vorlage aus, indem Sie auf **Select** (Auswählen) klicken.

9. Speichern Sie Ihre Änderungen, indem Sie **HINZUFÜGEN** > **OK** > **Speichern** auswählen.

## <a name="assign-the-policy"></a>Zuweisen der Richtlinie

Sie können die Konformitätsrichtlinie einer spezifischen Benutzergruppe oder allen Benutzern zuweisen. Wenn Intune erkennt, dass ein Gerät nicht konform ist, wird der Benutzer darüber benachrichtigt, dass er sein Gerät aktualisieren muss, um die Konformitätsrichtlinie zu erfüllen. Verwenden Sie die folgenden Schritte, um die Richtlinie zuzuweisen.

1. Navigieren Sie in Intune zu **Geräte** > **Compliance policies** (Konformitätsrichtlinien), und wählen Sie die zuvor erstellte **Windows 10 Konformitätsrichtlinie** aus.

2. Wählen Sie **Zuweisungen** aus.

3. Wählen Sie **Alle Benutzer** im Dropdownfeld **Assign to** (Zuweisen zu) aus. Damit werden alle Benutzer ausgewählt. Jeder Benutzer mit einem Gerät mit **Windows 10 oder höher**, das nicht der Konformitätsrichtlinie entspricht, wird benachrichtigt.

    > [!NOTE]
    > Sie können Gruppen beim Zuweisen von Konformitätsrichtlinien ein- und ausschließen.

4. Klicken Sie auf **Speichern**.

Wenn Sie die Richtlinie erfolgreich erstellt und gespeichert haben, wird sie in der Liste **Compliance policies – Policies** (Konformitätsrichtlinien: Richtlinien) angezeigt. Beachten Sie, dass **Zugewiesen** in der Liste auf **Ja** festgelegt ist.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie mit Intune eine Konformitätsrichtlinie für die Windows 10-Geräte Ihrer Mitarbeiter erstellt und zugewiesen, die ein Kennwort mit einer Mindestlänge von sechs Zeichen erfordert. Weitere Informationen zum Erstellen von Konformitätsrichtlinien für Windows-Geräte finden Sie unter [Hinzufügen einer Gerätekonformitätsrichtlinie für Windows-Geräte in Intune](compliance-policy-create-windows.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Hinzufügen und Zuweisen einer Client-App](../apps/quickstart-add-assign-app.md)
