---
title: Registrieren Ihres iOS-Geräts im Telecom Expense Management mit Intune
description: Erfahren Sie, wie Sie ein iOS-Gerät beim Telecom Expense Management registrieren.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6d8c6372-f2ce-4558-8886-1d7c1966699c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0a17196ce30b014f0fd5e615918398c4436dba4f
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149367"
---
# <a name="enroll-your-ios-device-in-telecom-expense-management"></a>Registrieren Ihres iOS-Geräts im Telecom Expense Management

Vielleicht verwendet Ihre Organisation Telecom Expense Management-Software, um sicherzustellen, dass ihre Daten- und Voicepläne zulässige Grenzwerte einhalten. Nachdem Sie die Registrierung des Geräts abgeschlossen haben, werden Sie aufgefordert, die beste Kategorie für das Gerät auszuwählen.

  ![Dies ist ein Screenshot des Bildschirms zum „Auswählen der besten Kategorie für ein Gerät“ eines iOS-Geräts. Er zeigt eine Auswahl von Unternehmens- bzw. persönlicher Registrierung.](./media/ios-enroll-10-tem-select-best-category.png)

Wählen Sie die entsprechende Option aus, und Sie erhalten eine Benachrichtigung zum Installieren der [__Datalert__](https://itunes.apple.com/app/datalert/id771029268?mt=8)-App aus dem App Store. Mit der Datalert-App kann Ihre Organisation die Datenverwendung messen. Wenn Ihre Organisation die Microsoft-Geschäfts- oder Schulregistrierungsoption konfiguriert hat, werden Sie aufgefordert, sich mit Ihrem Geschäfts- oder Schulkonto anzumelden. Wenn diese Option noch nicht aktiviert wurde, müssen Sie Informationen wie Ihre Telefonnummer angeben und Ihr Gerät mithilfe eines Codes überprüfen, um sich von der App aus beim Datalert-Dienst zu registrieren.

  ![Dies ist ein Screenshot des Begrüßungsbildschirms der Datalert-App, in dem Sie nach einer kurzen Erläuterung dazu, wie Sie mit Datalert Ihren Datenplan optimal nutzen können, aufgefordert werden, zum nächsten Bildschirm zu wechseln.](./media/ios-enroll-11-tem-datalert-setup.png)

## <a name="enroll-into-datalert-using-your-microsoft-work-or-school-account"></a>Registrieren bei Datalert mit Ihrem Microsoft-Geschäfts- oder -Schulkonto

> [!NOTE]
> Für diese Art der Registrierung muss die [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to)-App auf Ihrem Mobiltelefon installiert und aktiv sein.

1. Wählen Sie __Mit Microsoft-Konto anmelden__.

   ![Dies ist ein Bild des Einstellungenbildschirms der Datalert-App, das in der oberen Bildschirmhälfte ein Telefonnummernfeld zum Registrieren eines Geräts und unten „mit Microsoft-Konto registrieren“ enthält, sofern Sie über ein Microsoft Office 365-Konto und ein Intune-Abonnement verfügen.](./media/ios-enroll-11a-tem-datalert-enroll-msft-account.png)

2. Sie erhalten eine Benachrichtigung, dass __„Datalert“ „Authentifikator“ öffnen möchte__. Wählen Sie __Öffnen__ aus.

   ![Dies ist ein Bild des Popups, in dem der Benutzer auf Anforderung der Datalert-App zum Öffnen der Authentifikator-App aufgefordert wird.](./media/ios-enroll-11b-tem-datalert-open-authenticator.png)

3. Melden Sie sich mit Ihrem __Microsoft-Schul- oder -Geschäftskonto__ an. Das Datalert-Setup wird kurz durchgeführt und sollte dann abgeschlossen sein. Berühren Sie nach Abschluss __Fertig stellen__.

## <a name="enroll-into-datalert-using-your-phone-number"></a>Registrieren bei Datalert mit Ihrer Telefonnummer

1. Geben Sie die Telefonnummer des Geräts an.

   ![Dies ist ein Screenshot der Datalert-App mit der Aufforderung zur Eingabe einer Telefonnummer.](./media/ios-enroll-12-tem-datalert-phone-number.png)

2. Sie erhalten dann per SMS-Nachricht einen Überprüfungscode. Geben Sie den Code ein, und tippen Sie auf __OK__.

   ![Dies ist ein Screenshot der Datalert-App mit der Aufforderung zur Eingabe des SMS-Überprüfungscodes.](./media/ios-enroll-13-tem-datalert-sms.png)

3. Nachdem Sie den Überprüfungscode angegeben haben, ist das Datalert-Setup abgeschlossen. Tippen Sie auf __Fertig stellen__, und von nun an können Sie Ihre Daten mit der Datalert-App überwachen.

   ![Dieser Screenshot zeigt die Überwachung der Datennutzung von heute durch die Datalert-App.](./media/ios-enroll-14-tem-datalert-monitoring-active.png)

Sobald Sie sich registriert haben, zeigt Ihnen die Datalert-App Ihre Datennutzung an.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
