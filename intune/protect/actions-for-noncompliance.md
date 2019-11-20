---
title: 'Nicht konforme Nachrichten und Aktionen mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen einer E-Mail-Benachrichtigung für nicht konforme Geräte. Hinzufügen von Aktionen, nachdem ein Gerät als nicht konform markiert wurde, z.B. das Hinzufügen einer Toleranzperiode, in der das Gerät konform werden soll, oder das Erstellen eines Zeitplans, um den Zugriff zu blockieren, bis das Gerät konform ist. Verwenden Sie dazu Microsoft Intune in Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3867bfc2de29c059766e134bd0d2c8801e1c70
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712893"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte in Intune

Für Geräte, die nicht Ihren Konformitätsrichtlinien oder -regeln entsprechen, können Sie **Aktionen bei Inkompatibilität** hinzufügen. Dieses Feature konfiguriert eine zeitlich angeordnete Sequenz an Aktionen wie z. B. E-Mails an den Endbenutzer.

## <a name="overview"></a>Übersicht

Wenn Intune ein Gerät erkennt, das nicht konform ist, kennzeichnet Intune dieses standardmäßig als „nicht konform“. Das Gerät wird dann durch den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) von Azure Active Directory (AD) blockiert. Wenn ein Gerät nicht konform ist, können Sie mithilfe von **Aktionen bei Inkompatibilität** flexibel entscheiden, wie Sie vorgehen möchten. Sie können beispielsweise festlegen, dass das Gerät nicht sofort blockiert werden soll. Ebenfalls können Sie dem Benutzer eine Toleranzperiode einräumen, in der er dafür sorgen kann, dass das Gerät konform ist.

Es gibt mehrere Arten von Aktionen:

- **E-Mail an Endbenutzer senden:** Sie können E-Mail-Benachrichtigungen auch anpassen, bevor Sie sie an Endbenutzer senden. Sie können Empfänger, Betreff, Nachrichtentext (einschließlich Unternehmenslogo) und Kontaktinformationen anpassen.

    Darüber hinaus bezieht Intune Einzelheiten zu dem nicht konformen Gerät in die E-Mail-Benachrichtigung ein.

- **Nicht konformes Gerät remote sperren:** Bei nicht konformen Geräten können Sie eine Remotesperre ausgeben. Zum Entsperren des Geräts wird der Benutzer dann zur Eingabe einer PIN oder eines Kennworts aufgefordert. Weitere Informationen zur Funktion [Remotesperre](../remote-actions/device-remote-lock.md).

- **Mark device non-compliant** (Markieren des Geräts als nicht konform): Erstellen Sie einen Zeitplan mit der Anzahl von Tagen, nach der ein Gerät als „nicht konform“ markiert wird. Sie können die Aktion so konfigurieren, dass sie sofort oder erst nach einer gewissen Toleranzperiode wirksam wird, um dem Benutzer Gelegenheit zu geben, Ihre Gerätekonformitätsrichtlinien zu erfüllen.

In diesem Artikel erfahren Sie, wie Sie Folgendes durchführen:

- Erstellen einer Benachrichtigungsvorlage
- Erstellen einer Aktion für Nichtkonformität, wie z.B. das Senden einer E-Mail oder das Remotesperren eines Geräts


## <a name="before-you-begin"></a>Vorbereitung

- Zum Einrichten von Aktionen bei Nichtkonformität benötigen Sie mindestens eine Gerätekonformitätsrichtlinie. Plattformspezifische Informationen zum Erstellen einer Gerätekonformitätsrichtlinie finden Sie hier:

  - [Android](compliance-policy-create-android.md)
  - [Android-Arbeitsprofile](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Wenn Sie Gerätekonformitätsrichtlinien verwenden, um den Zugriff auf Unternehmensressourcen durch Geräte zu blockieren, muss der bedingte Zugriff von Azure AD eingerichtet sein. Anleitungen dazu finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) oder [Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs mit Intune](conditional-access-intune-common-ways-use.md).

## <a name="create-a-notification-message-template"></a>Erstellen einer Benachrichtigungsvorlage

Zum Senden einer E-Mail an Ihre Benutzer müssen Sie eine Benachrichtigungsvorlage erstellen. Wenn ein Gerät nicht konform ist, werden die Einzelheiten, die Sie in die Vorlage eingeben, in den von Ihnen an die Benutzer gesendeten E-Mails angezeigt.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konformitätsrichtlinien** > **Benachrichtigung** > **Benachrichtigung erstellen** aus.
3. Geben Sie dann unter *Grundlagen* die folgenden Informationen an:

   - **Name**
   - **Antragsteller**
   - **Message**

4. Konfigurieren Sie ebenfalls unter *Grundlagen* die folgenden Optionen für die Benachrichtigung, bei denen standardmäßig *Aktiviert* ausgewählt ist:

   - **E-Mail-Kopfzeile: Unternehmenslogo einschließen**
   - **E-Mail-Fußzeile: Unternehmensnamen einschließen**
   - **E-Mail-Fußzeile: Kontaktinformationen einschließen**

   Das Logo, das Sie für das Branding des Unternehmensportals hochladen, wird für E-Mail-Vorlagen verwendet. Weitere Informationen zum Branding des Unternehmensportals finden Sie unter [Anpassen des Unternehmensbrandings](../apps/company-portal-app.md#company-identity-branding-customization).

   ![Beispiel einer Benachrichtigung zur Konformität in Intune](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

   Wählen Sie **Weiter** aus, um den Vorgang fortzusetzen.

5. Überprüfen Sie Ihre Konfigurationen unter **Überprüfen und Erstellen**, um sicherzustellen, dass die Benachrichtigungsvorlage einsatzbereit ist. Wählen Sie **Erstellen** aus, um die Erstellung der Benachrichtigung abzuschließen.

> [!NOTE]
> Sie können auch eine bereits erstellte Benachrichtigungsvorlage auswählen und deren Informationen **bearbeiten**, um die Vorlage zu aktualisieren.

## <a name="add-actions-for-noncompliance"></a>Hinzufügen von Aktionen bei Nichtkonformität

Wenn Sie eine Konformitätsrichtlinie für Geräte erstellen, erstellt Intune automatisch eine Aktion für Nichtkonformität. Wenn ein Gerät Ihre Konformitätsrichtlinie nicht einhält, wird das Gerät von dieser Aktion als „nicht konform“ gekennzeichnet. Sie können anpassen, wie lange das Gerät als „nicht konform“ gekennzeichnet wird. Diese Aktion kann nicht entfernt werden.

Sie können beim Erstellen einer Konformitätsrichtlinie oder Aktualisieren einer vorhandenen Konformitätsrichtlinie auch eine andere Aktion hinzufügen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konformitätsrichtlinien** > **Richtlinien**, anschließend eine Ihrer Richtlinien und dann **Eigenschaften** aus.

   Haben Sie noch keine Richtlinie? Erstellen Sie eine Richtlinie für [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) oder eine andere Plattform.

   > [!NOTE]
   > JAMF-Geräte und Geräte als Teil von Gerätegruppen können zu diesem Zeitpunkt keine Konformitätsaktionen empfangen.

3. Wählen Sie **Aktionen für Nichtkonformität** > **Hinzufügen** aus.

4. Wählen Sie Ihre **Aktion** aus:

   - **E-Mail an Endbenutzer senden:** Senden Sie dem Benutzer eine E-Mail, wenn das Gerät nicht konform ist. Ferner gilt Folgendes:
     - Wählen Sie die zuvor erstellte **Nachrichtenvorlage** aus
     - Geben Sie durch die Auswahl von Gruppen **zusätzliche Empfänger** ein

   - **Nicht konformes Gerät remote sperren:** Sperren Sie das Gerät, wenn es nicht konform ist. Durch diese Aktion wird der Benutzer zur Eingabe einer PIN oder eines Kennworts gezwungen, um das Gerät zu entsperren

5. Konfigurieren Sie einen **Zeitplan**: Geben Sie die Anzahl von Tagen (0 bis 365) nach der Nichtkonformität ein, nach der die Aktion auf Benutzergeräten ausgelöst werden soll. Nach Ablauf dieser Nachfrist können Sie eine Richtlinie für [bedingten Zugriff](conditional-access-intune-common-ways-use.md) erzwingen. Wenn Sie als Anzahl von Tagen **0** (null) eingeben, wird der bedingte Zugriff **sofort** wirksam. Wenn beispielsweise ein Gerät nicht konform ist, können Sie mithilfe des bedingten Zugriffs sofort den Zugriff auf E-Mails, SharePoint und andere Organisationsressourcen blockieren.

   Wenn Sie eine Konformitätsrichtlinie erstellen, wird automatisch die Aktion **Gerät als nicht konform markieren** erstellt und auf **0** Tage (sofort) festgelegt. Durch diese Aktion wird das Gerät beim Einchecken sofort als nicht konform ausgewertet. Wenn Sie auch den bedingten Zugriff verwenden, wird dieser umgehend wirksam. Wenn Sie eine Nachfrist zulassen möchten, ändern Sie den **Zeitplan** für die Aktion **Gerät als nicht konform markieren**.

   Sie möchten den Benutzer außerdem in Ihrer Konformitätsrichtlinie benachrichtigen. Fügen Sie die Aktion **E-Mail an Endbenutzer senden** hinzu. Legen Sie für diese Aktion **E-Mail senden**, den **Zeitplan** auf 2 Tage fest. Wird das Gerät oder der Endbenutzer an Tag 2 weiterhin als nicht konform ausgewertet, wird Ihre E-Mail an Tag 2 gesendet. Wenn Sie dem Benutzer an Tag 5 der Nichtkonformität erneut eine E-Mail senden möchten, fügen Sie eine weitere Aktion hinzu, und legen Sie den **Zeitplan** auf 5 Tage fest.

   Weitere Informationen zur Konformität und den integrierten Aktionen finden Sie in der [Konformitätsübersicht](device-compliance-get-started.md).

6. Klicken Sie zum Speichern Ihrer Änderungen auf **Hinzufügen** > **OK**.

## <a name="next-steps"></a>Nächste Schritte

[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md).
