---
title: Registrieren Ihres macOS-Geräts bei Intune über das Unternehmensportal | Microsoft-Dokumentation
description: Beschreibt, wie Sie ein macOS-Gerät über die Unternehmensportal-App bei Intune registrieren
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: fea76693fe929338b29d110c299277e753134cc6
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196781"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrieren Ihres macOS-Geräts bei Intune über die Unternehmensportal-App

Registrieren Sie Ihr macOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Organisationen verlangen oft, dass Sie Ihr Gerät verwalten lassen, bevor Sie auf proprietäre Daten zugreifen können. Sobald es sich dann um ein verwaltetes Gerät handelt, können Organisationen über ihren MDM-Anbieter Richtlinien und Apps auf das Gerät übertragen. Um von Ihrem Gerät aus kontinuierlich auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können, müssen Sie Ihr Gerät entsprechend der Richtlinieneinstellungen konfigurieren.  

In diesem Artikel wird beschrieben, wie Sie Ihr Gerät mit der Intune-Unternehmensportal-App für macOS registrieren, konfigurieren und verwalten, um die Anforderungen Ihrer Organisation zu erfüllen.  
</br>
> [!VIDEO https://www.youtube.com/embed/Pa2pfhwq_yk?rel=0]

## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App

Während der ersten Einrichtung werden Sie von der App aufgefordert, sich bei Ihrer Organisation zu authentifizieren. Anschließend werden Sie über alle notwendigen Geräteeinstellungen informiert. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.    

Nachdem Ihr Gerät registriert ist, wird es mithilfe der Unternehmensportal-App weiter geschützt. Wenn Sie beispielsweise eine App aus einer nicht vertrauenswürdigen Quelle installieren, benachrichtigt Sie die Unternehmensportal-App und entzieht Ihnen in manchen Fällen den Zugriff auf Unternehmensdaten. App-Schutzrichtlinien wie diese sind in Organisationen üblich und erfordern oft die Deinstallation nicht vertrauenswürdiger Apps, damit Sie Ihre Zugriffsrechte zurück erhalten.

Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung, wie beispielsweise eine mehrstufige Authentifizierung, durchsetzt, erhalten Sie eine Benachrichtigung von der Unternehmensportal-App. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Registrieren Ihres Geräts für die Verwaltung  
Führen Sie die folgenden Schritte aus, um macOS-Geräte mit OS X El Capitan 10.11 und höher zu registrieren.   


1. Für den Zugriff auf die Unternehmensportalwebsite öffnen Sie ein neues Fenster in __Safari__, und wechseln Sie zu https://portal.manage.microsoft.com.  

2. Melden Sie sich bei mit Ihrem Geschäfts-, Schul- oder Unikonto bei der Unternehmensportalwebsite an.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Klicken Sie links oben in der Ecke auf **Menü** > **Geräte**.  

4. Auf der Seite __Geräte__ wird entweder eine Liste der verwalteten Geräte oder ein Banner angezeigt. Was Sie dort sehen, hängt davon ab, ob Sie bereits über ein verwaltetes Gerät verfügen. 
    * Wählen Sie zum Hinzufügen eines nicht aufgelisteten Geräts das Banner mit dem folgenden Hinweis aus: **Tap here to tell us which device you're using or add a new device.** (Tippen Sie hier, um das von Ihnen verwendete Gerät anzugeben, oder fügen Sie ein neues Gerät hinzu.)
    * Wenn Sie noch keine Geräte hinzugefügt haben, wird auf dem Banner Folgendes angezeigt: **You don't have any managed devices. Add this one by tapping here.** (Es sind noch keine verwalteten Geräte vorhanden. Tippen Sie hier, um dieses Gerät hinzuzufügen.) Klicken Sie auf das Banner, um Ihr Gerät hinzuzufügen.  

     ![Ein Screenshot der Seite für Geräte auf dem ein roter Rahmen um das Banner markiert, wo Sie klicken können.](./media/CP-enroll-MACOS-1808.png)  
5.  Führen Sie den nachfolgenden Schritt entsprechend der im Unternehmensportal angezeigten Meldung aus.  
    * Wenn Sie ein Gerät zum ersten Mal hinzufügen, werden Sie aufgefordert, die Unternehmensportal-App auf Ihr Gerät herunterzuladen. Klicken Sie auf **Herunterladen**, um den Vorgang fortzusetzen.  

         ![Beispielscreenshot der Aufforderung zum Herunterladen der macOS-Unternehmensportal-App Der Benutzer kann entweder unten links im Dialogfeld die blaue Schaltfläche zum Herunterladen oder unten rechts die graue Schaltfläche zum Abbrechen auswählen.](./media/CP-enroll-download-macOS-1808.png)  

    * Wenn Sie bereits über ein verwaltetes macOS-Gerät verfügen, wird eine Eingabeaufforderung mit einer Liste Ihrer aktuell verwalteten macOS-Geräte angezeigt. Wählen Sie **My device isn't listed here** (Mein Gerät ist hier nicht aufgelistet) > **Herunterladen** aus, um die Unternehmensportal-App auf das Gerät herunterzuladen, das Sie hinzufügen möchten.  

         ![Beispielscreenshot der Aufforderung zum Herunterladen der macOS-Unternehmensportal-App Der Benutzer kann entweder „My device isn't listed here“ (Mein Gerät ist hier nicht aufgelistet) oder ein bestimmtes Gerät aus der Mitte der Seite auswählen. In der Eingabeaufforderung wird unten links eine blaue Schaltfläche „Herunterladen“ und unten rechts eine graue Schaltfläche „Abbrechen“ angezeigt.](./media/cp-mac-os-device-isnt-here-1808.png)  

6. Ihr Gerät überprüft, ob die Installationsdatei **CompanyPortal.pkg** sicher geöffnet werden kann. Öffnen Sie nach der Überprüfung das Installationsprogramm, und schließen Sie die Installation ab.  

7. Wenn das Installationsprogramm abgeschlossen ist, wechseln Sie zu **Launchpad**, und öffnen Sie **Unternehmensportal**.  

8. Bestätigen Sie in der dann angezeigten Eingabeaufforderung, dass Sie die Unternehmensportal-App öffnen möchten. Klicken Sie auf **Öffnen**.  

   > [!TIP]
   > Intune benötigt Zugriff auf Ihren Computer, um sicherzustellen, dass die Gerätesicherheit für den Zugriff auf Organisationsinformationen ausreicht. Wenn Ihr Computer die Unternehmensportal-App nicht öffnet, [schalten Sie den Gatekeeper aus](https://support.apple.com/HT202491). Öffnen Sie anschließend die App.

9. Im Startbildschirm der Unternehmensportal-App werden Sie dann zur **Anmeldung** aufgefordert. Melden Sie sich mit demselben Geschäfts-, Schul- oder Unikonto wie bei der Unternehmensportalwebsite an.

10. Das Unternehmensportal bestätigt Ihre Kontoinformationen und zeigt Ihnen Ihre Status zu **Geräteregistrierung** und **Gerätekompatibilität** an. Gelbe Dreiecke heben die Aktionen hervor, die Sie ergreifen müssen, um Ihr macOS-Gerät für die Schule, die Uni oder die Arbeit zu sichern. Klicken Sie auf **Begin** (Starten), um die Registrierung zu starten. 

11. Geben Sie die Anmeldeinformationen für Ihren Computer ein, wenn Sie dazu aufgefordert werden.  

Das Registrieren Ihres Geräts für die Verwaltung kann einige Minuten beanspruchen. Während dieser Zeit können Sie auf dem Gerät andere Vorgänge ausführen. Sobald das Setup des Unternehmenszugriffs abgeschlossen ist, wird Ihnen eine Meldung angezeigt, die Sie darüber informiert.  

## <a name="unverified-profiles"></a>Nicht überprüfte Profile
Wenn Sie die installierten MDM-Profile (mobile Geräteverwaltung) für Ihr macOS-Gerät anzeigen, wird für einige Profile möglicherweise der Status **Nicht überprüft** angezeigt. Solange das **Verwaltungsprofil** den Status **Geprüft** aufweist, müssen Sie sich keine Gedanken machen.  

Das Verwaltungsprofil definiert die MDM-Kanalverbindung. Solange das Verwaltungsprofil geprüft ist, erben alle anderen Profile, die dem Computer bereitgestellt werden, die Sicherheitseigenschaften des Verwaltungsprofils.

Da diese anderen Profile keine individuelle Überprüfungen erfordern, können sie schneller für Geräte erstellt und bereitgestellt werden. 

## <a name="updating-the-company-portal-app"></a>Aktualisieren der Unternehmensportal-App

Das Aktualisieren des Unternehmensportals erfolgt auf die gleiche Weise wie bei jeder anderen Office-App, nämlich über Microsoft AutoUpdate für Mac. Sie finden weitere Informationen über das [Aktualisieren von Microsoft-Apps für macOS hier](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Nächste Schritte  
Benötigen Sie weitere Hilfe? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  


