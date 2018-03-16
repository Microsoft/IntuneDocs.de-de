---
title: "Auswählen der Registrierungsmethode für iOS-Geräte in Intune"
titlesuffix: Microsoft Intune
description: "Richten Sie die Registrierung von iOS-Geräten in Microsoft Intune ein."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 602c4c1da553215ad222a7e593531fdd879c996c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="enroll-ios-devices-in-intune"></a>Registrieren von iOS-Geräten in Intune

Intune ermöglicht die Verwaltung mobiler Geräte (mobile device management, MDM) wie iPads und iPhones, was Benutzern den Zugriff auf Unternehmens-E-Mails und -Apps ermöglicht.

Als Intune-Administrator können Sie die Registrierung für iOS-Geräte aktivieren. Sie können Benutzern erlauben, persönliche Geräte zu registrieren, was auch als BYOD-Registrierung („bring your own device“) bekannt ist. Sie können auch die Registrierung von unternehmenseigenen Geräten aktivieren.

## <a name="prerequisites-for-ios-enrollment"></a>Voraussetzungen für die iOS-Registrierung
Bevor Sie iOS-Geräte aktivieren können, schließen Sie die folgenden Schritte ab:
- [Einrichten von Intune:](setup-steps.md) Mit diesen Schritten wird Ihre Intune-Infrastruktur eingerichtet. Besonders für die Geräteregistrierung ist es erforderlich, dass Sie [die MDM-Autorität festlegen](mdm-authority-set.md).
- [Abrufen eines Apple-MDM-Push-Zertifikats:](apple-mdm-push-certificate-get.md) Apple benötigt ein Zertifikat, um die Verwaltung von iOS- und macOS-Geräten zu aktivieren.

## <a name="user-owned-ios-devices-byod"></a>iOS-Gerät im Besitz des Benutzers (BYOD)

Benutzer können ihre persönlichen Geräte für die Intune-Verwaltung registrieren. Dies wird als „bring your own device“ oder BYOD bezeichnet. Sobald Sie über die Voraussetzungen verfügen und den Benutzern Lizenzen zugewiesen haben, können diese die Unternehmensportal-App für Intune aus dem App Store herunterladen und den Registrierungsanweisungen in der App folgen.

## <a name="company-owned-ios-devices"></a>Unternehmenseigenes iOS-Gerät
Für Organisationen, die Geräte für Ihre Benutzer erwerben, unterstützt Intune die folgenden Methoden für die Registrierung von firmeneigenen iOS-Geräten:

- Apple-Programm zur Geräteregistrierung (DEP)
- Apple School Manager
- Registrierung über den Setup-Assistenten für Apple Configurator
- Apple Configurator – Direkte Registrierung

Sie können firmeneigene iOS-Geräte auch mit einem Konto für den [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) registrieren.

## <a name="device-enrollment-program"></a>Geräteregistrierungsprogramm
Organisationen können iOS-Geräte über das Apple Device Enrollment Program (DEP) erwerben. Mit DEP können Sie drahtlos (Over The Air) ein Registrierungsprofil bereitstellen, das Geräte für die Verwaltung registriert. Erfahren Sie mehr über das [Programm zur Geräteregistrierung](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager ist Programm zum Kauf von Geräten und deren Registrierung für Schulen. Wie bei DEP können Sie ein Profil zum Registrieren von Geräten in der Verwaltung bereitstellen. Erfahren Sie mehr über [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Sie können iOS-Geräte mit Apple Configurator auf einem Mac-Computer registrieren. Um Geräte vorzubereiten, verbinden Sie sie über USB, und installieren Sie das Registrierungsprogramm. Sie können Geräte mit Apple Configurator auf zwei Arten registrieren:
- Registrierung per Setup-Assistent: Dieser Prozess setzt das Gerät auf die Werkseinstellungen zurück, bereitet es auf die Ausführung des Setup-Assistenten vor und installiert die Unternehmensrichtlinien für den neuen Benutzer des Geräts.
- Direkte Registrierung: Dieser Prozess setzt das Gerät nicht auf die Werkseinstellungen zurück und registriert das Gerät mit einer vordefinierten Richtlinie. Diese Methode eignet sich für Geräte ohne Benutzeraffinität.

Erfahren Sie mehr über die [Apple Configurator-Registrierung](apple-configurator-setup-assistant-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Verwenden des Unternehmensportals auf Geräten, die über DEP oder Apple Configurator registriert wurden

Auf mit Benutzeraffinität konfigurierten Geräte kann die Unternehmensportal-App installiert und ausgeführt werden, um Apps herunterzuladen und Geräte zu verwalten. Nachdem Benutzer ihre Geräte erhalten haben, müssen sie verschiedene zusätzliche Schritte ausführen, um den Setup-Assistenten abzuschließen und die Unternehmensportal-App zu installieren.

Benutzeraffinität ist erforderlich, um Folgendes zu unterstützen:
  - MAM-Apps (Mobile Application Management, Verwaltung mobiler Anwendungen)
  - Bedingten Zugriff auf E-Mail- und Unternehmensdaten
  - Unternehmensportal-App

**Registrieren von firmeneigenen iOS-Geräten mit Benutzeraffinität durch Benutzer**
1. Wenn Benutzer ihr Gerät einschalten, werden sie aufgefordert, den Setup-Assistenten zu durchlaufen. Während des Setups werden Benutzer zur Eingabe ihrer Anmeldeinformationen aufgefordert. Sie müssen die Anmeldeinformationen (d. h. den eindeutigen persönlichen Namen) verwenden, die ihrem Abonnement in Intune zugeordnet sind.

2. Während des Setups werden Benutzer zur Eingabe einer Apple ID aufgefordert. Sie müssen eine Apple-ID angeben, damit das Gerät das Unternehmensportal installieren kann. Sie können die ID auch nach Abschluss des Setups über das iOS-Menü „Einstellungen“ angeben.

3. Nach Abschluss des Setups muss auf dem iOS-Gerät die Unternehmensportal-App aus dem App Store installiert werden.

4. Der Benutzer kann sich nun mit dem eindeutigen persönlichen Namen, der beim Setup des Geräts verwendet wurde, am Unternehmensportal anmelden.

5. Nach der Anmeldung wird der Benutzer aufgefordert, sein Gerät zu registrieren. Der erste Schritt besteht im Identifizieren des Geräts. Die App zeigt eine Liste mit iOS-Geräten, die bereits vom Unternehmen registriert und dem Intune-Konto des Benutzers zugewiesen wurden. Der Benutzer sollte das entsprechende Gerät auswählen.

  Wenn das Gerät nicht bereits vom Unternehmen registriert wurde, sollte er **Neues Gerät** auswählen, um den standardmäßigen Registrierungsvorgang fortzusetzen.

6. Auf dem nächsten Bildschirm muss der Benutzer die Seriennummer des neuen Geräts bestätigen. Der Benutzer kann auf den Link **Seriennummer bestätigen** tippen, um zum Bestätigen der Seriennummer die App „Einstellungen“ zu starten. Der Benutzer muss dann die letzten vier Zeichen der Seriennummer in die Unternehmensportal-App eingeben.

  Dieser Schritt dient zum Überprüfen, ob das Gerät das vom Unternehmen in Intune registrierte Gerät ist. Wenn die Seriennummer des Geräts nicht übereinstimmt, wurde der falsche Gerät ausgewählt. Der Benutzer sollte zum vorherigen Bildschirm zurückkehren, und ein anderes Gerät auswählen.

7. Nachdem die Seriennummer überprüft wurde, wird die Unternehmensportal-App zur Unternehmensportal-Website umgeleitet, um die Registrierung abzuschließen. Anschließend wird der Benutzer aufgefordert, zur App zurückzukehren.

8. Die Registrierung ist damit abgeschlossen. Der Benutzer kann nun die Funktionen des Geräts in vollem Umfang nutzen.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Informationen zu unternehmenseigenen verwalteten Geräten ohne Benutzeraffinität

Ohne Benutzeraffinität konfigurierte Geräte unterstützen das Unternehmensportal nicht und dürfen nicht die App installieren. Das Unternehmensportal ist für Benutzer gedacht, die über Anmeldeinformationen ihres Unternehmens verfügen und Zugriff auf personalisierte Unternehmensressourcen (z. B. E-Mail) benötigen. Geräte, die ohne Benutzeraffinität registriert wurden, bieten nicht die Anmeldung dedizierter Benutzer. Kiosk-, Verkaufsstellen- (POS-) oder gemeinsam genutzte Geräte sind typisch Anwendungsfälle für Geräte, die ohne Benutzeraffinität registriert werden.

Wenn Benutzeraffinität erforderlich ist, muss vor der Registrierung des Geräts in dessen Registrierungsprofil **Benutzeraffinität** ausgewählt worden sein. Zum Ändern des Affinitätsstatus eines Geräts müssen Sie das Gerät deaktivieren und erneut registrieren.

