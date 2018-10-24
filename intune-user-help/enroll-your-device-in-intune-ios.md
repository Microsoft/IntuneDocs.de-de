---
title: Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 85d0df026e49b36e148620ce2d06b4afaaf98ace
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827886"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen

Registrieren Sie Ihr iOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Bevor Sie von einem firmeneigenen oder persönlichen Gerät aus auf proprietäre Daten zugreifen können, müssen Sie Ihr Gerät verwalten lassen. Sobald es sich dann um ein verwaltetes Gerät handelt, überträgt Ihre Organisation über ihren Anbieter für mobile Geräteverwaltung (MDM) Richtlinien und Apps auf das Gerät. 

Um von Ihrem Gerät aus auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können, müssen Sie Ihr Gerät entsprechend der von Ihrer Organisation bevorzugten Einstellungen konfigurieren. In diesem Artikel wird beschrieben, wie Sie Ihr Gerät über das Unternehmensportal registrieren, konfigurieren und verwalten, um diese Anforderungen zu erfüllen.

> [!NOTE]
> Wenn Sie versucht haben, in der E-Mail-App auf Unternehmens-E-Mails zuzugreifen und aufgefordert wurden, Ihr Gerät verwalten zu lassen, sind Sie hier richtig. Befolgen Sie die untenstehenden Anweisungen, um über Ihr iOS-Gerät den Zugriff auf Ihre E-Mails und andere Unternehmensressourcen zu ermöglichen.

## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App

### <a name="security"></a>Sicherheit
Während der ersten Einrichtung werden Sie von der App aufgefordert, sich bei Ihrer Organisation zu authentifizieren. Anschließend werden Sie über alle notwendigen Geräteeinstellungen informiert, die Sie aktualisieren müssen. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.    

### <a name="protection"></a>Schutz
Nachdem Ihr Gerät registriert ist, wird es mithilfe der Unternehmensportal-App weiter geschützt. Wenn Sie beispielsweise eine App aus einer nicht vertrauenswürdigen Quelle installieren, benachrichtigt Sie die Unternehmensportal-App und entzieht Ihnen in manchen Fällen den Zugriff auf Unternehmensdaten. App-Schutzrichtlinien wie diese sind in Organisationen üblich. Sie erfordern oft, dass Sie die nicht vertrauenswürdige App deinstallieren, bevor Sie wieder Zugriff erhalten.

### <a name="setting-notifications"></a>Benachrichtigungseinstellungen
Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung, wie beispielsweise eine mehrstufige Authentifizierung, durchsetzt, erhalten Sie eine Benachrichtigung von der Unternehmensportal-App. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios). 

## <a name="before-you-start"></a>Vorbereitung

- Stellen Sie zu Beginn der Registrierung sicher, dass Sie den gesamten Prozess durchgeführt haben. Wenn Sie länger als ein paar Minuten pausieren, wird das Setup möglicherweise beendet, und Sie müssen von vorne anfangen.  
- Wenn bei diesem Vorgang ein Fehler auftritt, kehren Sie zur Unternehmensportal-App zurück und versuchen es erneut.  
- Stellen Sie sicher, dass Ihr WLAN in Betrieb ist und dass Safari auf Ihrem Gerät funktioniert.
- Laden Sie die [Intune-Unternehmensportal-App](install-and-sign-in-to-the-intune-company-portal-app-ios.md) herunter, und installieren Sie sie.  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Verwenden der Unternehmensportal-App für das Einrichten des Zugriffs auf Unternehmensressourcen

|Anzeige|Erläuterung|
|---|---|
|![Anmeldebildschirm des Unternehmensportals mit der Schaltfläche „Anmelden“ im unteren Bereich](./media/ios-01-cp-enroll-1802.png)|Öffnen Sie die Unternehmensportal-App, und tippen Sie auf **Anmelden**.|
|![Aufforderung zur Anmeldung bei Azure AD](./media/ios-02-cp-enroll-1802.png)|Geben Sie die E-Mail-Adresse für Ihr Unternehmen ein, und tippen Sie auf **Weiter**.|
|![Aufforderung zur Azure AD-Kennworteingabe.](./media/ios-03-cp-enroll-1802.png)|Geben Sie Ihr Kennwort ein, und tippen Sie dann auf **Anmelden**.|
|![Begrüßungsbildschirm beim Laden von Unternehmensressourcen.](./media/ios-04-cp-enroll-1802.png)|Warten Sie, bis die Anzeige geladen wurde.|
|![Seite der Nutzungsbedingungen](./media/ios-05-cp-enroll-1802.png)|Lesen Sie die Nutzungsbedingungen, und klicken Sie auf **Alle akzeptieren**.|
|![Bildschirm „Unternehmenszugriff einrichten“. Sowohl die Verwaltung als auch die Einstellungen weisen zurzeit einen Lösungsbedarf auf.](./media/ios-06-cp-enroll-1802.png)|Tippen Sie auf **Begin** (Beginnen), um den Vorgang zum Aktivieren des Zugriffs auf Unternehmensressourcen mit Ihrem Gerät zu starten. Wenn dies jetzt nicht möglich ist, können Sie den Vorgang **verschieben**. Dies bedeutet jedoch, dass Sie keine E-Mail, Dokumente und andere Elemente erhalten können.|
|![Bildschirm zu den für das Unternehmen sichtbaren Informationen.](./media/ios-07-cp-enroll-1802.png)|**Weitere Informationen** zu den für Ihr Unternehmen sichtbaren Elementen erhalten Sie, indem Sie unten auf den Link tippen. Tippen Sie andernfalls auf **Weiter**.|
|![Bildschirm „Wie geht es weiter?“](./media/ios-08-cp-enroll-1802.png)|Dieser Bildschirm führt Sie durch das Setup. Sie werden nun Safari, die App „Einstellungen“ und die Unternehmensportal-App verwenden. Tippen Sie auf **Weiter**.|
|![Bildschirm mit Ladevorgang nach dem Tippen auf „Weiter“ bei „Wie geht es weiter?“](./media/ios-09-cp-enroll-1802.png)|Warten Sie, bis die Anzeige geladen wurde.|
|![Wechsel zu Safari für die Registrierung.](./media/ios-cp-sent-to-safari-1808.png)|Sie werden zu Safari gesendet, um weitere Verwaltungsinformationen für Ihr Gerät zu erhalten.|
|![Systemaufforderung zum Öffnen der App „Einstellungen“.](./media/ios-8-cp-enroll-1711.png)|Tippen Sie auf **Zulassen**, um die App „Einstellungen“ zu öffnen und das Konfigurationsprofil herunterzuladen. Sie installieren dieses Profil, um Ihrem Unternehmen die Verwaltung von Unternehmensdaten auf Ihrem Gerät zu ermöglichen.|
|![Screenshot der Anzeige zur Profilinstallation in den Geräteeinstellungen](./media/ios-9-cp-enroll-1711.png)|Tippen Sie auf **Installieren**.|
|![Modales Dialogfeld „Profil wird installiert“ vom unteren Bildschirmrand.](./media/ios-10-cp-enroll-1711.png)|Tippen Sie auf **Installieren**.|
|![Ladebildschirm beim Installieren des Profils.](./media/ios-11-cp-enroll-1711.png)|Warten Sie, bis die Anzeige geladen wurde.|
|![Warnbildschirm zur Profilverwaltung.](./media/ios-12-cp-enroll-1711.png)|Diese Warnung wurde von Apple verfasst und informiert Sie über die möglichen Arten von Aktionen, die auf einem verwalteten Gerät durchgeführt werden können. Weitere Informationen hierzu finden Sie in der Liste der [Informationen, die Ihrem Unternehmen angezeigt werden](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Systemeingabeaufforderung zur Vertrauensstellung bei der Remoteverwaltung.](./media/ios-13-cp-enroll-1711.png)|Tippen Sie auf **Vertrauen**, um Ihrem Unternehmens die Verwaltung von Unternehmensinformationen und Einstellungen auf Ihrem Gerät zu ermöglichen.|
|![Ladebildschirm zum Abschluss der Profilinstallation.](./media/ios-14-cp-enroll-1711.png)|Warten Sie, bis die Anzeige geladen wurde.|
|![Bildschirm „Profil installiert“.](./media/ios-15-cp-enroll-1711.png)|Ihr Profil ist installiert, und es sind nur noch wenige Schritte erforderlich, damit die Unternehmensdaten und Einstellungen auf Ihrem Gerät verwaltet werden können.|
|![Wechsel zu Safari für die Registrierung.](./media/ios-16-cp-enroll-1711.png)|Sie werden zu Safari zurückgesendet, um den Abruf von Verwaltungsinformationen für Ihr Gerät abzuschließen. |
|![Systemaufforderung zum Öffnen des Unternehmensportals.](./media/ios-17-cp-enroll-1711.png)|Tippen Sie auf **Öffnen**.|
|![Bildschirm beim Laden von Unternehmensressourcen.](./media/ios-21-cp-enroll-1802.png)|Warten Sie, bis die Anzeige geladen wurde.|
|![Wählen Sie die Gerätekategorie in der Unternehmensportal-App aus.](./media/ios-22-cp-enroll-1802.png)|Wählen Sie die beste Kategorie für Ihr Gerät. Dies hängt normalerweise damit zusammen, wer das Gerät besitzt oder wo es sich in der Regel befindet.|
|![Ausgewählte Kategorie.](./media/ios-23-cp-enroll-1802.png)||
|![Das Gerät wird erfolgreich verwaltet. Jetzt müssen Einstellungen aktualisiert werden.](./media/ios-24-cp-enroll-1802.png)|Sie haben die Verwaltung Ihres Geräts erfolgreich aktiviert. Wahrscheinlich gibt es noch einige Einstellungen, beispielsweise die Kennwortlänge, die von Ihrem Unternehmen aktualisiert werden müssen. Klicken Sie auf **Weiter**, um fortzufahren.|
|![Geräteeinstellungen werden bestätigt.](./media/ios-25-cp-enroll-1802.png)|Das Unternehmensportal überprüft, ob Ihre Einstellungen aktualisiert werden müssen.|
|![Einstellungsüberprüfung abgeschlossen, falsche Betriebssystemversion](./media/ios-26-cp-enroll-1802.png)|Das Unternehmensportal stellt Anweisungen zum Beheben von Problemen mit Ihren Einstellungen bereit. Wenn Sie die Probleme behoben haben, tippen Sie auf **Einstellungen überprüfen**.|
|![Ladebildschirm zum Bestätigen der Geräteeinstellungen](./media/ios-27-cp-enroll-1802.png)|Ihr Gerät prüft, ob die Sicherheit Ihrer Einstellungen für den Zugriff auf Unternehmensressourcen ausreicht.|
|![Einstellungen erfolgreich registriert und aktualisiert](./media/ios-28-cp-enroll-1802.png)|Gratulation! Ihr Gerät ist jetzt bei Intune registriert.|

> [!Note]
> Sie müssen noch einige weitere Schritte ausführen, bevor Ihr Gerät vollständig verwaltet wird. Weitere Informationen finden Sie unter [Registrieren Ihres Geräts mithilfe des Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihre Organisation das Programm zur Geräteregistrierung von Apple verwendet, finden Sie [hier](enroll-your-device-dep-ios.md) weitere Informationen.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
