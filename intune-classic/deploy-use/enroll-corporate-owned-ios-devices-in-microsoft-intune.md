---
title: Registrieren firmeneigener iOS-Geräte
description: Registrieren firmeneigener iOS-Geräte mithilfe des Apple Device Enrollment Program (DEP) oder Apple Configurator
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 93ff84d263c2fe8825d2cf5a86249bbf19cb9173
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020910"
---
# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Registrieren firmeneigener iOS-Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune unterstützt die Registrierung von firmeneigenen iOS-Geräten mithilfe des Apple-Programms zur Geräteregistrierung (Device Enrollment Program, DEP) oder des Tools [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017), das auf einem Mac-Computer ausgeführt wird.

**Voraussetzung:** Ein [Apple Push Notification Service-Zertifikat](set-up-ios-and-mac-management-with-microsoft-intune.md)

Sie können firmeneigene iOS-Geräte registrieren, indem Sie eine der drei folgenden Methoden auswählen:

- Apple Configurator, das Verwenden des Setup-Assistenten oder die direkte Registrierung
- Programm zur Geräteregistrierung
- Unternehmensportal-App

>[!NOTE]
>Die Registrierung mithilfe von Apple Configurator oder dem Geräteregistrierungsprogramm kann nicht zusammen mit der Registrierung mithilfe des [Geräteregistrierungs-Managers](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) verwendet werden.

Standardmäßig dürfen alle iOS-Geräte in Intune registriert werden. Um persönliche oder unternehmenseigene Daten für die Registrierung zu blockieren, melden Sie sich mit Ihren Administratoranmeldeinformationen im [Microsoft Intune-Verwaltungsportal](https://manage.microsoft.com) an. Wählen Sie **Admin** (Administrator) > **Verwaltung mobiler Geräte** > **Registrierungsregeln** aus, und deaktivieren Sie anschließend die anwendbaren Optionen.

## <a name="use-apple-configurator"></a>Verwenden von Apple Configurator

Sie können iOS-Geräte registrieren, indem Sie ein Unternehmensregistrierungsprofil exportieren und dies mobilen Geräte anschließend mit einem Mac verbinden, auf dem Apple Configurator ausgeführt wird. Apple Configurator unterstützt zwei Formen der Registrierung:

- **Setup-Assistent für die Registrierung**: Setzt das Gerät auf die Werkseinstellungen zurück und bereitet es für die Einrichtung durch den neuen Benutzer des Geräts vor. Bei dieser Methode muss der Administrator das iOS-Gerät per USB mit einem Macintosh-Computer verbinden, auf dem [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) ausgeführt wird, um die Registrierung vorzukonfigurieren. Die Geräte werden dann an ihre Benutzer übergeben, die den Setup-Assistenten ausführen. Dieser Prozess konfiguriert das Gerät mit den Anmeldeinformationen Ihres Geschäfts- oder Schulkontos und schließt den Registrierungsvorgang ab. Weitere Informationen finden Sie unter [Registrieren von iOS-Geräten mithilfe von Apple Configurator und Setup-Assistent](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Direkte Registrierung**: Erstellt eine Apple Configurator-kompatible Datei zur Verwendung während der Vorbereitung des Geräts. Das registrierte Gerät wird nicht auf die Werkseinstellungen zurückgesetzt, aber ist keinem Benutzer zugewiesen. Bei dieser Methode muss der Administrator das iOS-Gerät per USB mit einem Macintosh-Computer verbinden, auf dem [Apple Configurator](https://go.microsoft.com/fwlink/?LinkId=518017) ausgeführt wird, um das Gerät zu registrieren. Weitere Informationen finden Sie unter [Registrierung von iOS-Geräte mit der Option „Direkte Registrierung“ von Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md).

## <a name="use-the-device-enrollment-program-dep"></a>Verwenden des Geräteregistrierungsprogramms (Device Enrollment Program, DEP)
Auf über das DEP erworbenen Geräten wird ein Registrierungsprofil „Drahtlos“ bereitgestellt. Wenn ein Benutzer auf dem Gerät den Setup-Assistenten ausführt, wird das Gerät bei Intune registriert. Weitere Informationen finden Sie unter [Registrieren von iOS-Geräten, die über das Apple-Programm zur Geräteregistrierung erworben wurden](ios-device-enrollment-program-in-microsoft-intune.md).

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



### <a name="see-also"></a>Siehe auch
[Voraussetzungen für die Registrierung von Geräten in Microsoft Intune](prerequisites-for-enrollment.md)
