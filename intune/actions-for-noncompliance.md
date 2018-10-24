---
title: 'Nicht konforme Nachrichten und Aktionen mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen einer E-Mail-Benachrichtigung für nicht konforme Geräte. Hinzufügen von Aktionen, nachdem ein Gerät als nicht konform markiert wurde, z.B. das Hinzufügen einer Toleranzperiode, in der das Gerät konform werden soll, oder das Erstellen eines Zeitplans, um den Zugriff zu blockieren, bis das Gerät konform ist. Verwenden Sie dazu Microsoft Intune in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fae8faf54c7b41bb547912853285cf09ec9c46d5
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828107"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte in Intune

Es gibt ein Feature für **Aktionen bei Nichtkonformität**, mit dem eine zeitlich strukturierte Aktionsfolge konfiguriert werden kann. Diese Aktionen gelten für Geräte, die Ihre Konformitätsrichtlinie nicht erfüllen. 

## <a name="overview"></a>Übersicht
Wenn Intune ein Gerät erkennt, das nicht konform ist, kennzeichnet Intune dieses standardmäßig als „nicht konform“. Das Gerät wird dann durch den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) von Azure Active Directory (AD) blockiert. Wenn ein Gerät nicht konform ist, können Sie mithilfe von **Aktionen bei Nichtkonformität** entscheiden, wie Sie vorgehen möchten. Sie können beispielsweise festlegen, dass das Gerät nicht sofort blockiert werden soll. Ebenfalls können Sie dem Benutzer eine Toleranzperiode einräumen, in der er dafür sorgen kann, dass das Gerät konform ist.

Es gibt mehrere Arten von Aktionen:

- **Senden einer E-Mail an den Benutzer**: Passen Sie Ihre E-Mail-Benachrichtigung an, bevor Sie sie an den Benutzer senden. Sie können Empfänger, Betreff, Nachrichtentext (einschließlich Unternehmenslogo) und Kontaktinformationen anpassen.

    Darüber hinaus bezieht Intune Einzelheiten zu dem nicht konformen Gerät in die E-Mail-Benachrichtigung ein.

- **Remotesperren des nicht konformen Geräts**: Bei nicht konformen Geräten können Sie eine Remotesperre ausgeben. Zum Entsperren des Geräts wird der Benutzer dann zur Eingabe einer PIN oder eines Kennworts aufgefordert. Weitere Informationen zur Funktion [Remotesperre](device-remote-lock.md). 

- **Markieren des Geräts als nicht konform**: Erstellen Sie einen Zeitplan mit der Anzahl von Tagen, nach der ein Gerät als „nicht konform“ markiert wird. Sie können die Aktion so konfigurieren, dass sie sofort oder erst nach einer gewissen Toleranzperiode wirksam wird, um dem Benutzer Gelegenheit zu geben, Ihre Gerätekonformitätsrichtlinien zu erfüllen.

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

- Für die Verwendung von Gerätekonformitätsrichtlinien, um Geräten den Zugriff auf Unternehmensressourcen zu blockieren, muss der bedingte Zugriff von Azure AD eingerichtet sein. Eine entsprechende Anleitung finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) oder unter [Gängige Möglichkeiten der Verwendung des bedingten Zugriffs in Intune](conditional-access-intune-common-ways-use.md).

## <a name="create-a-notification-message-template"></a>Erstellen einer Benachrichtigungsvorlage

Zum Senden einer E-Mail an Ihre Benutzer müssen Sie eine Benachrichtigungsvorlage erstellen. Wenn ein Gerät nicht konform ist, werden die Einzelheiten, die Sie in die Vorlage eingeben, in den von Ihnen an die Benutzer gesendeten E-Mails angezeigt.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Wählen Sie **Gerätekonformität** > **Benachrichtigungen** aus.
3. Wählen Sie **Benachrichtigung erstellen** aus. Geben Sie die folgenden Informationen ein:

   - **Name**
   - **Antragsteller**
   - **Message**
   - **E-Mail-Kopfzeile: Unternehmenslogo einschließen**
   - **E-Mail-Fußzeile: Unternehmensnamen einschließen**
   - **E-Mail-Fußzeile: Kontaktinformationen einschließen**

   ![Beispiel einer Benachrichtigung zur Konformität in Intune](./media/actionsfornoncompliance-1.PNG)

4. Klicken Sie auf **Erstellen**, sobald Sie die Informationen hinzugefügt haben. Die Benachrichtigungsvorlage ist nun einsatzbereit.

> [!NOTE]
> Sie können auch eine zuvor erstellte Benachrichtigungsvorlage bearbeiten.

## <a name="add-actions-for-noncompliance"></a>Hinzufügen von Aktionen bei Nichtkonformität

Wenn Sie eine Konformitätsrichtlinie für Geräte erstellen, erstellt Intune automatisch eine Aktion für Nichtkonformität. Wenn ein Gerät Ihre Konformitätsrichtlinie nicht einhält, wird das Gerät von dieser Aktion als „nicht konform“ gekennzeichnet. Sie können anpassen, wie lange das Gerät als „nicht konform“ gekennzeichnet wird. Diese Aktion kann nicht entfernt werden.

Sie können beim Erstellen einer Konformitätsrichtlinie oder Aktualisieren einer vorhandenen Konformitätsrichtlinie auch eine andere Aktion hinzufügen. 

1. Öffnen Sie im [Azure-Portal](https://portal.azure.com) **Microsoft Intune** > **Gerätekonformität**.
2. Klicken Sie auf **Richtlinien**, wählen Sie eine Ihrer Richtlinien aus, und klicken dann auf **Eigenschaften**. 

    Haben Sie noch keine Richtlinie? Erstellen Sie eine Richtlinie für [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) oder eine andere Plattform.
  
    > [!NOTE]
    > JAMF-Geräte und Geräte als Teil von Gerätegruppen können zu diesem Zeitpunkt keine Konformitätsaktionen empfangen.

3. Wählen Sie **Aktionen für Nichtkonformität** > **Hinzufügen** aus.
4. Wählen Sie Ihre **Aktion** aus: 

    - **Senden einer E-Mail an den Benutzer**: Senden Sie dem Benutzer eine E-Mail, wenn das Gerät nicht konform ist. Ferner gilt Folgendes: 
    
         - Wählen Sie die zuvor erstellte **Nachrichtenvorlage** aus
         - Geben Sie durch die Auswahl von Gruppen **zusätzliche Empfänger** ein
    
    - **Remotesperren des nicht konformen Geräts**: Sperren Sie das Gerät, wenn es nicht konform ist. Dadurch wird der Benutzer zum Entsperren des Geräts zur Eingabe einer PIN oder eines Kennworts gezwungen. 
    
    - **Zeitplan**: Geben Sie die Anzahl von Tagen (0 bis 365) nach der Nichtkonformität ein, um die Aktion auf Benutzergeräten auszulösen. Nach dieser Toleranzperiode können Sie eine Richtlinie für bedingten Zugriff erzwingen. Wenn Sie als Anzahl von Tagen **0** eingeben, wird der bedingte Zugriff **sofort** wirksam. Sie können den Zugriff auf Unternehmensressourcen beispielsweise sofort blockieren, wenn ein Gerät nicht konform ist.

5. Klicken Sie zum Speichern Ihrer Änderungen auf **Hinzufügen** > **OK**.

## <a name="next-steps"></a>Nächste Schritte
[Überwachen der Aktivität der Gerätekonformität](device-compliance-monitor.md).
