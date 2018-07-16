---
title: 'Nicht konforme Nachrichten und Aktionen mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen einer E-Mail-Benachrichtigung für nicht konforme Geräte. Hinzufügen von Aktionen, nachdem ein Gerät als nicht konform markiert wurde, z.B. das Hinzufügen einer Toleranzperiode, in der das Gerät konform werden soll, oder das Erstellen eines Zeitplans, um den Zugriff zu blockieren, bis das Gerät konform ist. Verwenden Sie dazu Microsoft Intune in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3c8bc523f2796f8af7cb4801cdb13a60b7e2eb5d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905732"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte in Intune

Es gibt ein Feature für **Aktionen bei Nichtkonformität**, mit dem eine zeitlich strukturierte Aktionsfolge konfiguriert werden kann. Diese Aktionen gelten für Geräte, die Ihre Konformitätsrichtlinie nicht erfüllen. 

## <a name="overview"></a>Übersicht
Wenn Intune ein Gerät erkennt, das nicht konform ist, kennzeichnet Intune dieses standardmäßig als „nicht konform“. Das Gerät wird dann durch den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) von Azure Active Directory (AD) blockiert. Wenn ein Gerät nicht konform ist, können Sie mithilfe von **Aktionen bei Nichtkonformität** entscheiden, wie Sie vorgehen möchten. Sie können beispielsweise festlegen, dass das Gerät nicht sofort blockiert werden soll. Ebenfalls können Sie dem Benutzer eine Toleranzperiode einräumen, in der er dafür sorgen kann, dass das Gerät konform ist.

Es gibt zwei Arten von Aktionen:

- **Benachrichtigen der Benutzer per E-Mail**: Anpassen Ihrer E-Mail-Benachrichtigung, bevor Sie sie an den Endbenutzer senden. Sie können Empfänger, Betreff, Nachrichtentext (einschließlich Unternehmenslogo) und Kontaktinformationen anpassen.

    Darüber hinaus bezieht Intune Einzelheiten zu dem nicht konformen Gerät in die E-Mail-Benachrichtigung ein.

- **Markieren des Geräts als nicht konform**: Erstellen Sie einen Zeitplan mit der Anzahl von Tagen, nach der ein Gerät als „nicht konform“ markiert wird. Sie können die Aktion so konfigurieren, dass sie sofort oder erst nach einer gewissen Toleranzperiode wirksam wird, um dem Benutzer Gelegenheit zu geben, Ihre Gerätekonformitätsrichtlinien zu erfüllen.

## <a name="before-you-begin"></a>Vorbereitung

- Zum Einrichten von Aktionen bei Nichtkonformität benötigen Sie mindestens eine Gerätekonformitätsrichtlinie. Plattformspezifische Informationen zum Erstellen einer Gerätekonformitätsrichtlinie finden Sie hier:

  - [Android](compliance-policy-create-android.md)
  - [Android-Arbeitsprofile](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Für die Verwendung von Gerätekonformitätsrichtlinien, um Geräten den Zugriff auf Unternehmensressourcen zu blockieren, muss der bedingte Zugriff von Azure AD eingerichtet sein. Anweisungen dazu finden Sie unter [Konfigurieren des bedingten Zugriffs in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

- Es muss eine Benachrichtigungsvorlage erstellt werden. Diese Vorlage wird zum Erstellen von Aktionen bei Nichtkonformität verwendet, um Ihren Benutzern E-Mails zu senden.

## <a name="create-a-notification-message-template"></a>Erstellen einer Benachrichtigungsvorlage

1. Melden Sie sich mit Ihren Intune-Anmeldeinformationen im [Azure-Portal](https://portal.azure.com) an. 
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonformität** und dann auf **Benachrichtigungen**. 
4. Klicken Sie auf **Benachrichtigung erstellen**, und geben Sie folgende Informationen ein:

   - Name
   - Antragsteller
   - Nachricht
   - E-Mail-Kopfzeile: Unternehmenslogo einschließen
   - E-Mail-Fußzeile: Unternehmensnamen einschließen
   - E-Mail-Fußzeile: Kontaktinformationen einschließen

   ![Beispiel einer Benachrichtigung zur Konformität in Intune](./media/actionsfornoncompliance-1.PNG)

Klicken Sie auf **Erstellen**, sobald Sie die Informationen hinzugefügt haben. Die Benachrichtigungsvorlage ist nun einsatzbereit.

> [!NOTE]
> Sie können auch eine zuvor erstellte Benachrichtigungsvorlage bearbeiten.

## <a name="add-actions-for-noncompliance"></a>Hinzufügen von Aktionen bei Nichtkonformität

Standardmäßig erstellt Intune automatisch eine Aktion bei Nichtkonformität. Wenn ein Gerät Ihre Konformitätsrichtlinie nicht einhält, wird das Gerät von dieser Aktion als „nicht konform“ gekennzeichnet. Sie können anpassen, wie lange das Gerät als „nicht konform“ gekennzeichnet wird. Diese Aktion kann nicht entfernt werden.

Sie können beim Erstellen einer neuen Konformitätsrichtlinie oder Aktualisieren einer vorhandene Konformitätsrichtlinie eine neue Aktion hinzufügen. 

1. Öffnen Sie **Microsoft Intune** im [Azure-Portal](https://portal.azure.com), und klicken Sie auf **Gerätekonformität**.
2. Klicken Sie auf **Richtlinien**, wählen Sie eine Ihrer Richtlinien aus, und klicken dann auf **Eigenschaften**. 

  Haben Sie noch keine Richtlinie? Erstellen Sie eine Richtlinie für [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) oder eine andere Plattform.
  
  > [!NOTE]
  > JAMF-Geräte und Geräte als Teil von Gerätegruppen können zu diesem Zeitpunkt keine Konformitätsaktionen empfangen.

3. Klicken Sie auf **Aktionen bei Nichtkonformität** und dann auf **Hinzufügen**, um die Aktionsparameter hinzuzufügen. Sie können die zuvor erstellte Benachrichtigungsvorlage auswählen, zusätzliche Empfänger hinzufügen und die Toleranzperiode des Zeitplans aktualisieren. Im Zeitplan können Sie die Anzahl von Tagen (0 bis 365) eingeben und dann die Richtlinien für den bedingten Zugriff erzwingen. Der Zugriff auf Unternehmensressourcen wird **sofort** durch den bedingten Zugriff blockiert, wenn Sie für die Anzahl der Tage **0** eingeben.

4. Klicken Sie zum Speichern Ihrer Änderungen auf **Hinzufügen** > **OK**.

## <a name="next-steps"></a>Nächste Schritte
Überwachen Sie die Aktivität der Gerätekonformität, indem Sie die Berichte ausführen. Hilfreiche Informationen finden Sie unter [Überwachen der Gerätekonformität in Intune](device-compliance-monitor.md).
