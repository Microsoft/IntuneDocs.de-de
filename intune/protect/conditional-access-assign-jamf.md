---
title: Gerätekonformitätsrichtlinie für Jamf-Geräte
titleSuffix: Microsoft Intune
description: Verwenden Sie die Konformitätsrichtlinien von Microsoft Intune zusammen mit dem bedingten Zugriff von Azure Active Directory, um mit Jamf verwaltete Geräte zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: 93265c2491058afde7168134075bed77031b9311
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74161595"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Erzwingen von Konformität auf mit Jamf Pro verwalteten Macs

Wenn Sie [Jamf Pro mit Intune integrieren](conditional-access-integrate-jamf.md), können Sie Richtlinien für bedingten Zugriff verwenden, um auf Ihren Mac-Geräten Konformität mit Ihren organisationsinternen Anforderungen zu erzwingen.  Dieser Artikel unterstützt Sie bei den folgenden Aufgaben:  

- Erstellen von Richtlinien für bedingten Zugriff.
- Konfigurieren von Jamf Pro zur Bereitstellung der App „Intune-Unternehmensportal“ auf Geräten, die Sie mit Jamf verwalten.
- Konfigurieren von Geräten zur Registrierung bei Azure AD, wenn sich der Gerätebenutzer bei der Unternehmensportal-App anmeldet, die er in der App „Jamf Self Service“ startet. Die Geräteregistrierung richtet eine Identität in Azure AD ein, die es dem Gerät ermöglicht, für den Zugriff auf Unternehmensressourcen von Richtlinien für bedingten Zugriff bewertet zu werden.  
 
Die Verfahren in diesem Artikel erfordern Zugriff auf die Intune- und Jamf Pro-Konsole.

## <a name="set-up-device-compliance-policies-in-intune"></a>Einrichten von Gerätekonformitätsrichtlinien in Intune

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konformitätsrichtlinien** aus. Wenn Sie eine zuvor erstellte Richtlinie verwenden, wählen Sie diese Richtlinie in der Konsole aus, und fahren Sie dann mit dem nächsten Schritt dieses Verfahrens fort. Wählen Sie **Richtlinie erstellen** aus, um eine neue Richtlinie zu erstellen, und geben Sie dann Details für eine Richtlinie mit **macOS** als *Plattform* an. Konfigurieren Sie *Einstellungen* und *Aktionen bei Inkompatibilität*, um Ihre unternehmensinternen Anforderungen zu erfüllen, und klicken Sie dann zum Speichern der Richtlinie auf **Erstellen**.

3. Wählen Sie im Richtlinienbereich *Übersicht* die Option **Zuweisungen** aus. Verwenden Sie die verfügbaren Optionen, um zu konfigurieren, für welche Azure Active Directory-Benutzer und -Sicherheitsgruppen diese Richtlinie gelten soll. Die Jamf-Integration mit Intune unterstützt keine Konformitätsrichtlinien für Gerätegruppen.

4. Wenn Sie auf **Speichern** klicken, wird die Richtlinie für die Benutzer bereitgestellt.  

Die von Ihnen bereitgestellten Richtlinien gelten für die Geräte, die von den zugewiesenen Benutzern verwendet werden. Diese Geräte werden auf Konformität geprüft. Konforme Geräte werden in Azure AD für die Einstellung *Markieren des Geräts als kompatibel erforderlich* als konform markiert.  

> [!NOTE]
> Intune erfordert, dass die vollständige Datenträgerverschlüsselung konform ist.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Bereitstellen der Unternehmensportal-App für macOS in Jamf Pro

Erstellen Sie in Jamf Pro eine Richtlinie für die Bereitstellung des Intune-Unternehmensportals. Diese Richtlinie stellt die Unternehmensportal-App so bereit, dass sie in Jamf Self Service verfügbar ist. Erstellen Sie diese Richtlinie, bevor Sie in Jamf Pro eine Richtlinie für Benutzer erstellen, die Geräte bei Azure AD registrieren.  

Um das folgende Verfahren abzuschließen, benötigen Sie Zugriff auf ein macOS-Gerät und das Jamf Pro-Portal. 

### <a name="to-deploy-the-company-portal-app"></a>So stellen Sie die Unternehmensportal-App bereit  

1. Laden Sie auf einem macOS-Gerät die aktuelle Version der [Unternehmensportal-App für macOS](https://go.microsoft.com/fwlink/?linkid=862280) herunter, ohne sie zu installieren. Sie benötigen nur eine Kopie der App, damit Sie die App in Jamf Pro hochladen können.  

2. Öffnen Sie Jamf Pro, und navigieren Sie zu **Computer management** > **Packages** (Computerverwaltung -> Pakete).

3. Erstellen Sie in der Unternehmensportal-App für macOS ein neues Paket, und klicken Sie auf **Save** (Speichern).

4. Öffnen Sie **Computer** > **Policies** (Richtlinien), und wählen Sie dann **New** (Neu).

5. Verwenden Sie die Nutzlast **General** (Allgemein), um Einstellungen für die Richtlinie zu konfigurieren. Zu diesen Einstellungen müssen zählen:
   - Trigger: Wählen Sie **Enrollment Complete** (Registrierung abgeschlossen) und **Recurring Check-in** (Wiederholtes Einchecken) aus.
   - Execution Frequency (Häufigkeit der Ausführung): Wählen Sie **Once per computer** (Einmal pro Computer) aus.

6. Wählen Sie die Nutzlast **Packages** (Pakete), und klicken Sie auf **Configure** (Konfigurieren).

7. Klicken Sie auf **Add** (Hinzufügen), um das Paket mit der Unternehmensportal-App auszuwählen.

8. Wählen Sie im Popupmenü **Action** (Aktion) **Install** (Installieren) aus.
9. Konfigurieren Sie die Einstellungen für das Paket.

10. Klicken Sie auf die Registerkarte **Scope** (Bereich), um anzugeben, auf welchen Computern die Unternehmensportal-App installiert werden soll. Wählen Sie **Speichern** aus. Die Richtlinie wird auf den betreffenden Geräten ausgeführt, wenn der ausgewählte Trigger das nächste Mal auf dem Computer auftritt und die Kriterien in der Nutzlast **General** (Allgemein) erfüllt sind.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Erstellen Sie eine Richtlinie in Jamf Pro, damit Benutzer ihre Geräte bei Azure Active Directory registrieren.  

Nachdem Sie [das Unternehmensportal](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) für macOS über Jamf Pro Self Service bereitgestellt haben, können Sie die Jamf Pro-Richtlinie erstellen, die das Gerät eines Benutzers bei Azure AD registriert. 

Bei der Geräteregistrierung muss ein Gerätebenutzer die Intune-App „Unternehmensportal“ im Jamf Self Service manuell auswählen. Es wird empfohlen, Sie [kontaktieren Ihre Endbenutzer](../fundamentals/end-user-educate.md) per E-Mail, Jamf Pro-Benachrichtigungen oder einer anderen in Ihrer Organisation verwendeten Methode, um sie anzuweisen, diese Aktion zum Registrieren ihrer Geräte durchzuführen. 

> [!WARNING]
> Wenn Sie die Unternehmensportal-App manuell starten (z. B. in den Ordnern „Anwendungen“ oder „Downloads“), wird das Gerät nicht registriert. Wenn ein Gerätebenutzer die Unternehmensportal-App manuell startet, wird die Warnung **AccountNotOnboarded** angezeigt.

### <a name="to-create-the-registration-policy"></a>So erstellen Sie die Registrierungsrichtlinie  

1. Navigieren Sie in Jamf Pro zu **Computers** > **Policies** (Computer -> Richtlinien), und erstellen Sie eine neue Richtlinie für die Geräteregistrierung.

2. Konfigurieren Sie die Nutzlast **Microsoft Intune Integration** (Integration von Microsoft Intune), einschließlich Trigger und Ausführungshäufigkeit.

3. Klicken Sie auf die Registerkarte **Scope** (Bereich), und beschränken Sie die Richtlinie auf alle Zielgeräte.

4. Klicken Sie auf die Registerkarte **Self Service**, um die Richtlinie in Jamf Self Service verfügbar zu machen. Nehmen Sie die Richtlinie in die Kategorie **Device Compliance** (Gerätekonformität) auf. Klicken Sie auf **Speichern**.

## <a name="validate-intune-and-jamf-integration"></a>Überprüfen der Integration von Intune und Jamf  

Bestätigen Sie mithilfe der Jamf Pro-Konsole, dass Jamf Pro und Microsoft Intune erfolgreich miteinander kommunizieren. 

- Wechseln Sie in Jamf Pro zu **Settings** > **Global Management** > **Microsoft Intune Integration** (Einstellungen -> Globale Verwaltung -> Microsoft Intune-Integration), und klicken Sie dann auf **Test**.

    In der Konsole wird eine Meldung zum Erfolg oder Misserfolg der Verbindung angezeigt.  

Sollte der Verbindungstest in der Jamf Pro-Konsole fehlschlagen, überprüfen Sie die Jamf-Konfiguration. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Entfernen eines mit Jamf verwalteten Gerätes aus Intune

Öffnen Sie das Microsoft Endpoint Manager Admin Center, um ein mit Jamf verwaltetes Gerät zu entfernen, und wählen Sie **Geräte** > **Alle Geräte** aus. Wählen Sie dann **Löschen** aus.  Die Massenlöschung von Geräten kann aktiviert werden, indem Sie mehrere Geräte auswählen und auf **Löschen** klicken.

Erfahren Sie, wie Sie [ein mit Jamf verwaltetes Gerät in den Jamf Pro-Dokumenten entfernen](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Sie können auch ein Supportticket beim [Jamf-Support](https://www.jamf.com/support/) einreichen, wenn Sie zusätzliche Hilfe benötigen. 

## <a name="next-steps"></a>Nächste Schritte

- [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Erste Schritte mit dem bedingten Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
