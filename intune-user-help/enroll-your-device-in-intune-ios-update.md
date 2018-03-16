---
title: Einrichten des Zugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: "Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 6474688a09c4063c55eff07f3cf84ebcb1911c65
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="set-up-access-to-your-company-resources"></a>Einrichten des Zugriffs auf Unternehmensressourcen

Ihr Unternehmen besitzt umfangreiche proprietäre Informationen, von E-Mail bis hin zu Dateien, Netzwerken und vielem mehr. Ihr Unternehmen verwendet Microsoft Intune für den Schutz dieser Informationen, wenn Sie über Ihr iOS-Gerät darauf zugreifen. Auf diese Weise kann das Unternehmen diese Ressourcen verwalten, für deren Sicherheit sorgen und Ihnen die Möglichkeit bieten, Ihr bevorzugtes Gerät für Ihre Arbeit zu verwenden.

> [!NOTE]
> Wenn Sie versuchen, auf E-Mails Ihres Unternehmens in der Mail-App zuzugreifen, ist es wahrscheinlich, dass Sie zum Verwalten Ihres Geräts aufgefordert werden, um dieses zu schützen. Befolgen Sie die untenstehenden Anweisungen, um über Ihr iOS-Gerät den Zugriff auf Ihre E-Mails und andere Unternehmensressourcen zu ermöglichen.

## <a name="before-you-start"></a>Vorbereitung

- Stellen Sie sicher, dass Sie den gesamten Prozess durchführen, nachdem Sie ihn gestartet haben. Wird der Prozess für mehr als einige Minuten unterbrochen, wird er normalerweise beendet, und Sie müssen noch einmal von vorn beginnen.
- Wenn bei diesem Vorgang ein Fehler auftritt, müssen Sie zur Unternehmensportal-App zurückkehren, um einen neuen Versuch zu starten.
- Stellen Sie sicher, dass Ihr WLAN in Betrieb ist und dass Safari auf Ihrem Gerät funktioniert.
- Laden Sie die [Intune-Unternehmensportal-App](install-and-sign-in-to-the-intune-company-portal-app-ios.md) herunter, und installieren Sie sie.


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Verwenden der Unternehmensportal-App für das Einrichten des Zugriffs auf Unternehmensressourcen

|Anzeige|Erläuterung|
|---|---|
|![Anmeldebildschirm des Unternehmensportals, mit der Schaltfläche „Anmelden“.](./media/ios-01-cp-enroll-1802.png)|Öffnen Sie die Unternehmensportal-App, und tippen Sie auf **Anmelden**.|
|![Aufforderung zur Anmeldung bei Azure AD.](./media/ios-02-cp-enroll-1802.png)|Geben Sie die E-Mail-Adresse für Ihr Unternehmen ein, und tippen Sie auf **Weiter**.|
|![Aufforderung zur Azure AD-Kennworteingabe.](./media/ios-03-cp-enroll-1802.png)|Geben Sie Ihr Kennwort ein, und tippen Sie dann auf **Anmelden**.|
|![Begrüßungsbildschirm beim Laden von Unternehmensressourcen.](./media/ios-04-cp-enroll-1802.png)|Warten Sie, bis alles geladen wurde.|
|![Seite der Nutzungsbedingungen](./media/ios-05-cp-enroll-1802.png)|Lesen Sie die Nutzungsbedingungen, und klicken Sie auf **Alle akzeptieren**.|
|![Bildschirm „Unternehmenszugriff einrichten“. Sowohl die Verwaltung als auch die Einstellungen weisen zurzeit einen Lösungsbedarf auf.](./media/ios-06-cp-enroll-1802.png)|Tippen Sie auf **Begin** (Beginnen), um den Vorgang zum Aktivieren des Zugriffs auf Unternehmensressourcen mit Ihrem Gerät zu starten. Wenn dies jetzt nicht möglich ist, können Sie den Vorgang **verschieben**. Dies bedeutet jedoch, dass Sie keine E-Mail, Dokumente und andere Elemente erhalten können.|
|![Bildschirm zu den für das Unternehmen sichtbaren Informationen.](./media/ios-07-cp-enroll-1802.png)|**Weitere Informationen** zu den für Ihr Unternehmen sichtbaren Elementen erhalten Sie, indem Sie unten auf den Link tippen. Tippen Sie andernfalls auf **Weiter**.|
|![Bildschirm „Wie geht es weiter?“](./media/ios-08-cp-enroll-1802.png)|Dieser Bildschirm führt Sie durch das Setup. Sie verbringen Zeit in Safari, in der App „Einstellungen“ und in der Unternehmensportal-App, um diesen Vorgang abzuschließen. Tippen Sie auf **Weiter**.|
|![Bildschirm mit Ladevorgang nach dem Tippen auf „Weiter“ bei „Wie geht es weiter?“](./media/ios-09-cp-enroll-1802.png)|Warten Sie, bis alles geladen wurde.|
|![Wechsel zu Safari für die Registrierung.](./media/ios-7-cp-enroll-1711.png)|Sie werden zu Safari gesendet, um weitere Verwaltungsinformationen für Ihr Gerät zu erhalten.|
|![Systemaufforderung zum Öffnen der App „Einstellungen“.](./media/ios-8-cp-enroll-1711.png)|Tippen Sie auf **Zulassen**, um die App „Einstellungen“ zu öffnen und das Konfigurationsprofil herunterzuladen. Sie installieren dieses Profil, um Ihrem Unternehmen die Verwaltung von Unternehmensdaten auf Ihrem Gerät zu ermöglichen.|
|![In den Einstellungen geöffnetes Profil.](./media/ios-9-cp-enroll-1711.png)|Tippen Sie auf **Installieren**.|
|![Modales Dialogfeld „Profil wird installiert“ vom unteren Bildschirmrand.](./media/ios-10-cp-enroll-1711.png)|Tippen Sie auf **Installieren**.|
|![Ladebildschirm beim Installieren des Profils.](./media/ios-11-cp-enroll-1711.png)|Warten Sie, bis alles geladen wurde.|
|![Warnbildschirm zur Profilverwaltung.](./media/ios-12-cp-enroll-1711.png)|Diese Warnung wurde von Apple verfasst und informiert Sie über die möglichen Arten von Aktionen, die auf einem verwalteten Gerät durchgeführt werden können. Weitere Informationen hierzu finden Sie in der Liste der [Informationen, die Ihrem Unternehmen angezeigt werden](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).|
|![Systemeingabeaufforderung zur Vertrauensstellung bei der Remoteverwaltung.](./media/ios-13-cp-enroll-1711.png)|Tippen Sie auf **Vertrauen**, um Ihrem Unternehmens die Verwaltung von Unternehmensinformationen und Einstellungen auf Ihrem Gerät zu ermöglichen.|
|![Ladebildschirm zum Abschluss der Profilinstallation.](./media/ios-14-cp-enroll-1711.png)|Warten Sie, bis alles geladen wurde.|
|![Bildschirm „Profil installiert“.](./media/ios-15-cp-enroll-1711.png)|Ihr Profil ist installiert, und es sind nur noch wenige Schritte erforderlich, damit die Unternehmensdaten und Einstellungen auf Ihrem Gerät verwaltet werden können.|
|![Wechsel zu Safari für die Registrierung.](./media/ios-16-cp-enroll-1711.png)|Sie werden zu Safari zurückgesendet, um den Abruf von Verwaltungsinformationen für Ihr Gerät abzuschließen. |
|![Systemaufforderung zum Öffnen des Unternehmensportals.](./media/ios-17-cp-enroll-1711.png)|Tippen Sie auf **Öffnen**.|
|![Bildschirm beim Laden von Unternehmensressourcen.](./media/ios-21-cp-enroll-1802.png)|Warten Sie, bis alles geladen wurde.|
|![Wählen Sie die Gerätekategorie in der Unternehmensportal-App aus.](./media/ios-22-cp-enroll-1802.png)|Wählen Sie die beste Kategorie für Ihr Gerät. Dies hängt normalerweise damit zusammen, wer das Gerät besitzt oder wo es sich in der Regel befindet.|
|![Ausgewählte Kategorie.](./media/ios-23-cp-enroll-1802.png)||
|![Das Gerät wird erfolgreich verwaltet. Jetzt müssen Einstellungen aktualisiert werden.](./media/ios-24-cp-enroll-1802.png)|Sie haben die Verwaltung Ihres Geräts erfolgreich aktiviert. Wahrscheinlich gibt es noch einige Einstellungen, beispielsweise die Kennwortlänge, die von Ihrem Unternehmen aktualisiert werden müssen. Klicken Sie auf **Weiter**, um fortzufahren.|
|![Geräteeinstellungen werden bestätigt.](./media/ios-25-cp-enroll-1802.png)|Das Unternehmensportal überprüft, ob Ihre Einstellungen aktualisiert werden müssen.|
|![Einstellungsüberprüfung abgeschlossen, falsche Betriebssystemversion](./media/ios-26-cp-enroll-1802.png)|Das Unternehmensportal stellt Anweisungen zum Beheben von Problemen mit Ihren Einstellungen bereit. Wenn Sie die Probleme behoben haben, tippen Sie auf **Einstellungen überprüfen**.|
|![Ladebildschirm zum Bestätigen der Geräteeinstellungen](./media/ios-27-cp-enroll-1802.png)|Ihr Gerät prüft, ob die Sicherheit Ihrer Einstellungen für den Zugriff auf Unternehmensressourcen ausreicht.|
|![Einstellungen erfolgreich registriert und aktualisiert](./media/ios-28-cp-enroll-1802.png)|Gratulation! Ihr Gerät ist jetzt bei Intune registriert.|

> [!Note]
> Sie müssen noch einige weitere Schritte ausführen, bevor Ihr Gerät vollständig verwaltet wird. Weitere Informationen finden Sie unter [Registrieren Ihres Geräts mithilfe des Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihre Organisation das Programm zur Geräteregistrierung von Apple verwendet, finden Sie [hier](enroll-your-device-dep-ios.md) weitere Informationen.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).
