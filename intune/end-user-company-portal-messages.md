---
title: Unternehmensportalmeldungen, die Benutzern möglicherweise auf Geräten angezeigt werden
titleSuffix: Microsoft Intune
description: Verstehen Sie die unterschiedlichen Nachrichten, die Endbenutzern im Unternehmensportal angezeigt werden können.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ed123bcf8c5c1a5df1a356cf8d2522caad20ea2
ms.sourcegitcommit: c9725ddae6c0f82a491de27c87f240254d32716b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2019
ms.locfileid: "71239378"
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Grundlegendes zum Verständnis von Meldungen in der Unternehmensportal-App

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> Die folgenden Informationen gelten nur für Geräte mit Android 6.0 und höher und iOS 10 und höher.

Verstehen Sie die unterschiedlichen App-Nachrichten, die Endbenutzern im Unternehmensportal angezeigt werden können. Diese App-Nachrichten werden häufig an verschiedenen Punkten im Registrierungsprozess angezeigt. Erfahren Sie, wann die Meldungen angezeigt werden, was sie bedeuten, und was geschieht, wenn Benutzer den Zugriff verweigern. Darüber hinaus erfahren Sie, wie Sie die Nachrichten den Benutzern am besten erklären.

- __Zulassen, dass das Unternehmensportal Telefonanrufe tätigt und verwaltet?__
- __Unternehmensportal den Zugriff auf Fotos, Medien und Dateien auf Ihrem Gerät erlauben?__

> [!NOTE]
> Die von unserem Dienst gesammelten Daten werden keinesfalls an Dritte verkauft.

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Zulassen, dass das Unternehmensportal Telefonanrufe tätigt und verwaltet?

### <a name="where-it-appears"></a>Position in der Oberfläche
Die Meldung **Zulassen, dass das Unternehmensportal Telefonanrufe tätigt und verwaltet?** wird angezeigt, wenn Benutzer in der Unternehmensportal-App auf **Registrieren** tippen, während sie ihr Gerät registrieren.

### <a name="what-it-means"></a>Bedeutung
Mit Akzeptieren dieser Aufforderung lassen Benutzer zu, dass die Telefon- und IMEI-Nummern ihrer Geräte an den Intune-Dienst gesendet werden. Diese werden in der Verwaltungskonsole auf der Seite __Hardware__ angezeigt.

> [!NOTE]
> **Die Unternehmensportal-App tätigt oder verwaltet keine Telefonanrufe!** Der Meldungstext wird von Google gesteuert und kann nicht geändert werden.

Zum Anzeigen der Seite **Hardware** wechseln Sie zu **Gruppen** > **Alle mobilen Geräte** > **Geräte**. Wählen Sie das Gerät des Benutzers aus, und wechseln Sie zu **Eigenschaften anzeigen** > **Hardware**.

### <a name="what-happens-if-users-deny-access"></a>Wenn Benutzer den Zugriff nicht zulassen,
Wenn Benutzer den Zugriff verweigern, können sie weiterhin die Unternehmensportal-App verwenden und ihr Gerät registrieren. Telefonnummer und IMEI-Nummer des Geräts werden jedoch nicht in der Verwaltungskonsole auf der Seite __Hardware__ angezeigt. Wenn Benutzer den Zugriff verweigern und sich dann das nächste Mal bei der Unternehmensportal-App anmelden, wird in der Meldung ein Kontrollkästchen **Nicht mehr nachfragen** angezeigt, das die Benutzer aktivieren können, damit die Eingabeaufforderung nicht mehr angezeigt wird.

Wenn Benutzer den Zugriff zunächst erlauben, später aber verweigern, wird die Meldung wieder angezeigt, wenn sie sich nach der Registrierung das nächste Mal bei der Unternehmensportal-App anmelden.

Wenn Benutzer den Zugriff später erlauben möchten, müssen sie zu **Einstellungen** > **Apps** > **Unternehmensportal** > **Berechtigungen** > **Telefon** wechseln, um die Berechtigung zu aktivieren.

### <a name="how-to-explain-this-to-your-users"></a>So erklären Sie dies Ihren Benutzern
Verweisen Sie Ihre Benutzer an [Registrieren Ihres Android-Geräts bei Intune](/intune-user-help/enroll-device-android-company-portal), um weitere Informationen zu erhalten.

## <a name="allow-company-portal-to-access-your-contacts"></a>Zulassen, dass das Unternehmensportal auf Ihre Kontakte zugreift?

### <a name="where-it-appears"></a>Position in der Oberfläche
Die Meldung **Zulassen, dass das Unternehmensportal auf Ihre Kontakte zugreift?** wird angezeigt, wenn Benutzer in der Unternehmensportal-App auf **Registrieren** tippen, während sie ihr Gerät registrieren.

### <a name="what-it-means"></a>Bedeutung
Mit Akzeptieren dieser Aufforderung erlauben Benutzer Intune das Erstellen ihres Arbeitskontos und das Verwalten ihrer Azure Active Directory-Identität, die für den Benutzer auf dem betreffenden Gerät registriert ist.

> [!NOTE]
> **Microsoft greift nie auf Ihre Kontakte zu!** Der Meldungstext wird von Google gesteuert und kann nicht geändert werden.

### <a name="what-happens-if-users-deny-access"></a>Wenn Benutzer den Zugriff nicht zulassen,
Wenn Benutzer den Zugriff verweigern, werden ihre Geräte nicht bei Intune registriert und können nicht verwaltet werden. Wenn Benutzer den Zugriff verweigern und sich dann das nächste Mal bei der Unternehmensportal-App anmelden, wird in der Meldung ein Kontrollkästchen **Nicht mehr nachfragen** angezeigt, das die Benutzer aktivieren können, damit die Eingabeaufforderung nicht mehr angezeigt wird.

Wenn Benutzer den Zugriff zunächst erlauben, später aber verweigern, wird die Meldung wieder angezeigt, wenn sie sich nach der Registrierung das nächste Mal bei der Unternehmensportal-App anmelden.

Wenn Benutzer den Zugriff später erlauben möchten, müssen sie zu **Einstellungen** > **Apps** > **Unternehmensportal** > **Berechtigungen** > **Telefon** wechseln, um die Berechtigung zu aktivieren.

### <a name="how-to-explain-this-to-your-users"></a>So erklären Sie dies Ihren Benutzern
Verweisen Sie Ihre Benutzer an [Registrieren Ihres Android-Geräts bei Intune](/intune-user-help/enroll-device-android-company-portal), um weitere Informationen zu erhalten.  

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Unternehmensportal den Zugriff auf Fotos, Medien und Dateien auf Ihrem Gerät erlauben?

### <a name="where-it-appears"></a>Position in der Oberfläche
Die Meldung **Unternehmensportal den Zugriff auf Fotos, Medien und Dateien auf Ihrem Gerät erlauben?** wird angezeigt, wenn Benutzer auf **Daten senden** tippen, um Datenprotokolle an den IT-Administrator zu senden.

### <a name="what-it-means"></a>Bedeutung
Mit Akzeptieren dieser Aufforderung erlauben Benutzer ihrem Gerät, Datenprotokolle auf die SD-Karte des Geräts zu schreiben. Dies ermöglicht auch das Verschieben dieser Protokolle mithilfe eines USB-Kabels.   

> [!NOTE]
> **Die Unternehmensportal-App greift nicht auf Fotos, Medien und Dateien der Benutzer zu!** Der Meldungstext wird von Google gesteuert und kann nicht geändert werden.

### <a name="what-happens-if-users-deny-access"></a>Wenn Benutzer den Zugriff nicht zulassen,
Wenn Benutzer den Zugriff verweigern, können sie weiterhin Datenprotokolle per E-Mail senden, aber die Protokolle werden nicht auf die SD-Karte des Geräts kopiert.

Wenn Benutzer den Zugriff verweigern und sich dann das nächste Mal bei der Unternehmensportal-App anmelden, wird in der Meldung ein Kontrollkästchen **Nicht mehr nachfragen** angezeigt, das die Benutzer aktivieren können, damit diese Meldung nicht mehr angezeigt wird. Wenn Benutzer den Zugriff zunächst erlauben, später aber verweigern, wird die Meldung wieder angezeigt, wenn sie das nächste Mal Protokolle senden. Wenn Benutzer den Zugriff jedoch später erlauben möchten, müssen sie zu **Einstellungen** > **Apps** > **Unternehmensportal** > **Berechtigungen** > **Speicherung** wechseln, um die Berechtigung zu aktivieren.


### <a name="how-to-explain-this-to-your-users"></a>So erklären Sie dies Ihren Benutzern
Verweisen Sie Ihre Benutzer an [Senden von Protokollen an Ihren IT-Administrator per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>Der Support Ihres Unternehmens muss Ihnen Zugriff auf Unternehmensressourcen gewähren.

### <a name="where-it-appears"></a>Position in der Oberfläche
Wenn Sie die Unternehmensportal-App nicht zur Liste **Zulässige Apps** oder **Ausgenommene Apps** hinzugefügt haben, und ein Benutzer versucht, sich anzumelden, schlägt die Anmeldung fehl. Die folgende Meldung wird angezeigt:

> **Der Support Ihres Unternehmens muss Ihnen Zugriff auf Unternehmensressourcen gewähren**  
> Ihr Unternehmen verwendet Windows Information Protection-Richtlinien, um Ihr Gerät zu schützen. Der Support Ihres Unternehmens muss sicherstellen, dass die Unternehmensportal-App auf diese Ressourcen zugreifen kann.

### <a name="what-it-means"></a>Bedeutung

Fügen Sie das Unternehmensportal zur Liste der **zulässigen Apps** oder **ausgenommenen Apps** hinzu, die in der Windows Information Protection-App-Schutzrichtlinie aufgeführt sind. Weitere Informationen finden Sie unter [Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Intune](windows-information-protection-policy-create.md).

## <a name="approve-a-ios-company-app-line-of-business-app-on-your-ios-device"></a>Genehmigen einer iOS-Unternehmensportal-App (branchenspezifischen App) auf Ihrem iOS-Gerät 

### <a name="where-it-appears"></a>Position in der Oberfläche
Ihr Gerät vertraut iOS-Apps, die von Ihrer Organisation entwickelt wurden und nicht im App Store verfügbar sind, standardmäßig nicht. Wenn Sie solche Apps über das Unternehmensportal installieren und die App starten, wird folgende Meldung angezeigt:

![Meldung in iOS-App: Untrusted Enterprise Developer (Nicht vertrauenswürdiger Unternehmensentwickler)](./media/end-user-company-portal-messages/end-user-company-portal-messages-01.png)

### <a name="what-it-means"></a>Bedeutung
Diese Meldung bedeutet, dass Sie Ihre iOS-Geräteeinstellungen bearbeiten müssen, damit eine App, die von Ihrem Unternehmen entwickelt wurde, auf Ihrem iOS-Gerät genehmigt und installiert wird.

Wenn Sie solche Apps über das Unternehmensportal installieren und die App dann öffnen, führen Sie folgende Schritte aus, um die App nach dem Download zu genehmigen:

1. Beim Öffnen einer installierten Unternehmens-App (branchenspezifischen App) wird Ihnen die Meldung „Untrusted Enterprise Developer“ (Nicht vertrauenswürdiger Unternehmensentwickler) angezeigt. <br>
   Wählen Sie **Abbrechen** aus.
2. Navigieren Sie zu **Settings** > **General** > **Device Management** (Einstellungen > Allgemein > Geräteverwaltung).

   ![Benutzeroberfläche eines iOS-Geräts – Geräteverwaltung](./media/end-user-company-portal-messages/end-user-company-portal-messages-02.png)

3. Klicken Sie auf **Management Profile** > **Enterprise app** (Verwaltungsprofil > Unternehmens-App).
4. Wählen Sie den Entwicklernamen aus.
5. Drücken Sie auf **Trust _developer name_** ([Entwicklername] vertrauen).
6. Bestätigen Sie die App, indem Sie bei der Popupmeldung bei der App-Installation auf **Trust** (Vertrauen) klicken.

   ![Benutzeroberfläche eines iOS-Geräts – Meldung: App vertrauen](./media/end-user-company-portal-messages/end-user-company-portal-messages-03.png)

    Sie sollten die Unternehmens-App nun öffnen und verwenden können.


## <a name="see-also"></a>Siehe auch
[Informieren der Endbenutzer über den Einsatz von Intune](end-user-educate.md)
