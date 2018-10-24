---
title: Gerätekonformitätsrichtlinie für Jamf-Geräte
titlesuffix: Microsoft Intune
description: Verwenden Sie die Konformitätsrichtlinien für Microsoft Intune zusammen mit dem bedingten Zugriff auf Azure Active Directory, um mit Jamf verwaltete Geräte zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4c41d3a4cdfada81b91a3dffeffdfe15e8a470f
ms.sourcegitcommit: 17094728cfd9eb3f77ca39745fdcde9be0a8dda1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "48812820"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Erzwingen von Konformität auf mit Jamf Pro verwalteten Macs

|Gilt für: Intune im Azure-Portal |
|--|
|Suchen Sie nach der Dokumentation zu Intune im klassischen Portal? [Klicken Sie hier](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

Über Azure Active Directory und die Microsoft Intune-Richtlinien für bedingten Zugriff können Sie sicherstellen, dass Ihre Endbenutzer den Anforderungen des Unternehmens entsprechen. Sie können diese Richtlinien auf Macs anwenden, die [mit Jamf Pro verwaltet](conditional-access-integrate-jamf.md) werden. Hierfür müssen Sie sowohl auf die Intune- als auch auf die Jamf Pro-Konsole zugreifen.

## <a name="set-up-device-compliance-policies-in-intune"></a>Einrichten von Gerätekonformitätsrichtlinien in Intune

1. Öffnen Sie Microsoft Azure, und navigieren Sie zu **Intune** > **Gerätekonformität** > **Richtlinien**. Sie können Richtlinien für macOS erstellen und dabei eine Reihe von Aktionen für nicht konforme Benutzer und Gruppen auswählen (z.B. Warn-E-Mails senden).
2. Suchen Sie nach den gewünschten Gruppen, und wenden Sie die Richtlinien an.

> [!Note]
> Intune erfordert, dass die vollständige Datenträgerverschlüsselung konform ist.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Bereitstellen der Unternehmensportal-App für macOS in Jamf Pro

Sie müssen die Unternehmensportal-App für macOS in Jamf Pro als Hintergrundinstallation bereitstellen, nachdem die folgende Prozedur abgeschlossen wurde:

1. Laden Sie auf einem macOS-Gerät die aktuelle Version der [Unternehmensportal-App für macOS](https://go.microsoft.com/fwlink/?linkid=862280) herunter. Installieren Sie die App nicht. Sie benötigen eine Kopie der App, um diese auf Jamf Pro hochladen zu können.
2. Öffnen Sie Jamf Pro, und navigieren Sie zu **Computer management** > **Packages** (Computerverwaltung > Pakete).
3. Erstellen Sie ein neues Paket mit der Unternehmensportal-App für macOS, und klicken Sie auf **Save** (Speichern).
4. Öffnen Sie **Computer** > **Policies** (Richtlinien), und wählen Sie dann **New** (Neu).
5. Verwenden Sie die Nutzlast **General** (Allgemein), um Einstellungen für die Richtlinie zu konfigurieren. Zu diesen Einstellungen müssen zählen:
   - Trigger: Wählen Sie **Enrollment Complete** (Registrierung abgeschlossen) und **Recurring Check-in** (Wiederholtes Einchecken) aus.
   - Execution Frequency (Häufigkeit der Ausführung): Wählen Sie **Once per computer** (Einmal pro Computer) aus.
6. Wählen Sie die Nutzlast **Packages** (Pakete), und klicken Sie auf **Configure** (Konfigurieren).
7. Klicken Sie auf **Add** (Hinzufügen), um das Paket mit der Unternehmensportal-App auszuwählen.
8. Wählen Sie **Install** (Installieren) aus dem Popupmenü **Action** (Aktion).
9. Konfigurieren Sie die Einstellungen für das Paket.
10. Klicken Sie auf die Registerkarte **Scope** (Bereich), um anzugeben, auf welchen Computern die Unternehmensportal-App installiert werden soll. Klicken Sie auf **Speichern**. Die Richtlinie wird auf den betreffenden Geräten ausgeführt, wenn der ausgewählte Trigger das nächste Mal auf dem Computer auftritt und die Kriterien in der Nutzlast **General** (Allgemein) erfüllt werden.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Erstellen Sie eine Richtlinie in Jamf Pro, damit Benutzer ihre Geräte bei Azure Active Directory registrieren.

> [!NOTE]
> Sie müssen das [Unternehmensportal für macOS bereitstellen](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos), bevor Sie die nächsten Schritten durchführen.  

Endbenutzer müssen die Unternehmensportal-App über den Jamf Self-Dienst starten, um das Gerät bei Azure AD als mit Jamf Pro verwaltetes Gerät zu registrieren. Dies erfordert, dass Ihre Endbenutzer Maßnahmen ergreifen. Wir empfehlen, dass Sie [Ihre Endbenutzer ](end-user-educate.md) über E-Mail, Jamf Pro-Benachrichtigungen oder andere Methoden kontaktieren und auffordern, auf die Schaltfläche in Jamf Self Service zu klicken.

> [!WARNING]
> Die Unternehmensportal-App muss im Jamf Self Service gestartet werden, um die Geräteregistrierung einzuleiten. <br><br>Wenn Sie die Unternehmensportal-App manuell starten (z.B. aus den Ordnern „Anwendungen“ oder „Downloads“), wird das Gerät nicht registriert. Wenn ein Endbenutzer die Unternehmensportal-App manuell startet, wird die Warnung „AccountNotOnboarded“ angezeigt.

1. Navigieren Sie in Jamf Pro zu **Computer** > **Policies** (Richtlinien), und erstellen Sie eine neue Richtlinie für die Geräteregistrierung.
2. Konfigurieren Sie die Nutzlast **Microsoft Intune Integration** (Integration von Microsoft Intune), einschließlich Trigger und Ausführungshäufigkeit.
3. Klicken Sie auf die Registerkarte **Scope** (Bereich), und beschränken Sie die Richtlinie auf alle Zielgeräte.
4. Klicken Sie auf die Registerkarte **Self Service**, um die Richtlinie in Jamf Self Service verfügbar zu machen. Nehmen Sie die Richtlinie in die Kategorie **Device Compliance** (Gerätekonformität) auf. Klicken Sie auf **Speichern**.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Entfernen eines mit Jamf verwalteten Gerätes aus Intune

Sie können ein von Jamf verwaltetes Gerät aus der Intune-Konsole entfernen, indem Sie **Löschen** in der Ansicht **Alle Geräte** auswählen. Die Massenlöschung von Geräten kann aktiviert werden, indem Sie mehrere Geräte auswählen und auf **Löschen** klicken.

Erfahren Sie, wie Sie [ein mit Jamf verwaltetes Gerät in den Jamf Pro-Dokumenten entfernen](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Sie können auch ein Supportticket beim [Jamf-Support](https://www.jamf.com/support/) einreichen, wenn Sie zusätzliche Hilfe benötigen. 

## <a name="next-steps"></a>Nächste Schritte

- [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Erste Schritte mit dem bedingten Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
