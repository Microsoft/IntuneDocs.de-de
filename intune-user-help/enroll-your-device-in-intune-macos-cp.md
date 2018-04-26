---
title: Registrieren Ihres macOS-Geräts bei Intune über das Unternehmensportal | Microsoft-Dokumentation
description: Beschreibt, wie Sie ein macOS-Gerät über die Unternehmensportal-App bei Intune registrieren
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
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
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrieren Ihres macOS-Geräts bei Intune über die Unternehmensportal-App

Durch den Zugriff auf Apps, Daten und Ressourcen Ihrer Organisation wird Ihnen Ihre Arbeit erleichtert. Ihre Organisation verwendet Intune zum [Verwalten des Zugriffs auf diese Ressourcen](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md), weshalb Sie die Unternehmensportal-App für macOS herunterladen müssen. Diese Anweisungen gelten für macOS-Geräte unter OS X El Capitan 10.11+.


1. Suchen Sie im __Dock__ nach __Safari__, und öffnen Sie ein neues Fenster. Öffnen Sie dann die [Unternehmensportal-Website](https://portal.manage.microsoft.com).

2. Melden Sie sich bei mit Ihrem Geschäfts-, Schul- oder Unikonto bei der Unternehmensportal-Website an.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Klicken Sie nach der Anmeldung in der linken Ecke der Seite auf das **Menü**, und klicken sie auf **My Devices** (Meine Geräte).

   ![Ein Screenshot der Startseite des Webportals; im Webportal wird angezeigt, dass noch keine Apps installiert werden können; darunter die Schaltfläche „Meine Geräte“.](./media/macOS_enroll_001_landing_page.png)

4. Auf der Seite __Meine Geräte__ wird entweder eine Liste der registrierten Geräte angezeigt oder einfach nur ein Banner. Dies hängt davon ab, ob Sie bereits ein macOS- oder ein anderes Gerät registriert haben. Wählen Sie zum Registrieren eines nicht aufgelisteten Geräts das Banner mit dem folgenden Hinweis aus: __Wenn Ihr Gerät aufgelistet ist, klicken Sie hier, um es zu identifizieren. Sie können auch hier klicken, um ein nicht aufgelistetes Gerät zu registrieren.__ Wenn Sie noch keine Geräte registriert haben, wird auf dem Banner Folgendes angezeigt: **You don't have any devices enrolled. Enroll this one by tapping here.** (Sie haben noch keine Geräte registriert. Tippen Sie hier, um dieses Gerät zu registrieren.)

    ![Ein Screenshot der Seite „Meine Geräte“ mit mehreren nicht identifizierten Geräten oberhalb der Banneraufforderung, nicht aufgelistete Geräte zu registrieren oder nicht identifizierte Geräte zu identifizieren.](./media/macOS_enroll_002_tap_here_banner.png)

5. Laden Sie die Unternehmensportal-App auf Ihr macOS-Gerät herunter, um die Registrierung fortzusetzen.

    ![Der Hinweis, der einen Benutzer zum Herunterladen der macOS-Unternehmensportal-App auffordert. Bei diesem Hinweis ist der Text im Schritt oberhalb einer Schaltfläche mit der Beschriftung „Herunterladen“ in der unteren rechten Ecke aufgelistet.](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Ihr Mac überprüft anschließend, ob der Download von **CompanyPortal.pkg** sicher geöffnet werden kann. Öffnen Sie das Installationsprogramm, und absolvieren Sie den Installationsvorgang.

7. Wenn das Installationsprogramm abgeschlossen ist, öffnen Sie den Ordner **Anwendungen** oder das **Launchpad**, und öffnen Sie anschließend **Unternehmensportal**.

8. Ihr Mac wird Ihnen eine Meldung anzeigen, die folgendermaßen lautet: **Unternehmensportal ist eine Anwendung, die aus dem Internet heruntergeladen wurde. Sind Sie sicher, dass Sie diese öffnen möchten?** Klicken Sie auf **Öffnen**.

   > [!NOTE]
   > Intune benötigt Zugriff auf Ihren Computer, um sicherzustellen, dass die Gerätesicherheit für den Zugriff auf Organisationsinformationen ausreicht. Wenn Ihr Computer die Unternehmensportal-App nicht öffnen möchte, versuchen Sie, [den Gatekeeper auszuschalten](https://support.apple.com/HT202491) und die App anschließend zu öffnen.

9. Der erste Bildschirm, der Ihnen in der Unternehmensportal-App angezeigt wird, fordert Sie dazu auf, sich mit dem gleichen Geschäfts-, Schul- oder Unikonto **anzumelden**, mit dem Sie sich auf der Webseite des Unternehmensportals angemeldet haben.

10. Das Unternehmensportal bestätigt Ihre Kontoinformationen und zeigt Ihnen anschließend Ihre **Geräteregistrierungs-** und **Gerätekompatibilitätsstatus** an. Es werden gelbe Dreiecke angezeigt, die Ihnen mitteilen, dass Sie Maßnahmen ergreifen müssen, um sicherzustellen, dass Ihr Mac für die Verwendung bei der Arbeit sicher ist. Klicken Sie auf **Begin** (Starten), um mit der [Registrierung Ihres Geräts bei der Verwaltung](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) zu beginnen.

11. Ihr Mac wird mit der Registrierung bei der Verwaltung starten. Sie werden während dieser Zeit möglicherweise dazu aufgefordert, die Anmeldeinformationen Ihres Computers bereitzustellen. Die Registrierung kann einige Minuten dauern. Während dieser Zeit können Sie auf dem Computer andere Dinge tun. Sobald das Setup des Unternehmenszugriffs abgeschlossen ist, wird Ihnen eine Meldung angezeigt, die Sie darüber informiert.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).
