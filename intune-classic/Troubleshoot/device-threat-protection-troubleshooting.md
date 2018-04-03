---
title: Problembehandlung der Lookout-Integration
description: Dieses Thema beschreibt die Behandlung von Problemen, die im Zusammenhang mit der Lookout-Integration häufig auftreten.
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ec20d87da48fb52207d839da0753eb05524569af
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Problembehandlung der Lookout-Integration mit Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In diesem Thema werden einige häufige Probleme beschrieben, die möglicherweise bei Ihrer Bereitstellung von Lookout Mobile Threat Protection (MTP) auftreten.

**Anmeldefehler**

## <a name="403-errors"></a>403-Fehler
Bei der Anmeldung an der [Lookout MTP-Konsole](https://aad.lookout.com) tritt ein 403-Fehler auf: **Sie sind nicht zum Zugriff auf den Dienst berechtigt**. Dies kann geschehen, wenn der angegebene Benutzername kein Mitglied der Azure Active Directory-Gruppe (Azure AD) ist, die für den Zugriff auf Lookout MTP konfiguriert ist.

Lookout MTP erlaubt nur Benutzern in einer konfigurierten Azure AD-Gruppe den Zugriff auf den Dienst. Um zu ermitteln, für welche Gruppe der Zugriff auf Lookout MTP konfiguriert ist, wenden Sie sich an den Lookout-Support:

* E-Mail: enterprisesupport@lookout.com
* Melden Sie sich bei der [MTP-Konsole](http://aad.lookout.com) an, und navigieren Sie zum Modul **Support**.
* Wechseln Sie zu https://enterprise.support.lookout.com/hc/requests, und stellen Sie eine Supportanfrage.

## <a name="unable-to-sign-in"></a>Die Anmeldung ist nicht möglich
Der folgende Fehler wird angezeigt, wenn der globale Administratorbenutzer von Azure AD das erstmalige Lookout-Setup nicht akzeptiert hat.

![Screenshot des Lookout-Anmeldebildschirms, der den Anmeldefehler darstellt](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

Um dieses Problem zu beheben, muss sich der globale Administratorbenutzer bei https://aad.lookout.com/les?action=consent anmelden und die Aufforderung zum Starten des Setups akzeptieren. Ausführlichere Informationen finden Sie im Thema [Einrichten Ihres Abonnements für Lookout MTP](../deploy-use/setup-your-lookout-mtd-subscription.md)

**Probleme mit dem Gerätestatus**

## <a name="device-missing-from-lookout-device-list"></a>Gerät fehlt in der Lookout-Geräteliste.

Diese Problem kann in allen folgenden Szenarien auftreten:
* Der Benutzer des Geräts ist kein Mitglied der in der **Lookout MTP-Konsole** angegebenen **Registrierungsgruppe**.  Wechseln Sie in der [Lookout-Konsole](http://aad.lookout.com) zu **System** > **Intune-Connector** > **Registrierungsverwaltung**.  Überprüfen Sie die für die Registrierung konfigurierten Azure AD-Gruppen, und stellen Sie sicher, dass der Benutzer des Geräts Mitglied einer der Azure AD-Gruppen ist.  Nachdem der Registrierungsgruppe ein Benutzer hinzugefügt wurde, kann es bis zum Ablauf des konfigurierten Abrufintervalls dauern (standardmäßig 5 Minuten), bis das Gerät im Modul **Geräte** der Lookout MTP-Konsole angezeigt wird.
* Wenn das Gerät nicht von Lookout MTP unterstützt wird.  Nicht unterstützte Geräte werden in der Lookout MTP-Konsole im Abschnitt **Verwaltete Geräte** der Connectoreinstellungen angezeigt.

### <a name="device-reported-as-pending"></a>Gerät wird als **ausstehend** gemeldet.

Ein Gerät wird als **Ausstehend** angezeigt, wenn der Endbenutzer die Lookout for Work-App nicht geöffnet und auf die Schaltfläche **Aktivieren** getippt hat. Weitere Informationen zur Geräteaktivierung mit der Lookout for Work-App finden Sie unter [Sie werden aufgefordert, Lookout for Work auf Ihrem Android-Gerät zu installieren](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) und [Sie werden aufgefordert, Lookout for Work auf Ihrem iOS-Gerät zu installieren](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios).

## <a name="device-whos-active-but-has-no-device-id"></a>Gerät ist aktiv, verfügt aber nicht über eine Geräte-ID.
Wenn ein aktives Gerät in der Lookout MTP-Konsole nicht über eine Geräte-ID verfügt, befindet sich der Benutzer des Geräts nicht in der Registrierungsgruppe. Ein Gerät kann diesen Zustand aufweisen, wenn der Benutzer des Geräts aus der Registrierungsgruppe entfernt wurde oder wenn die Registrierungsgruppe entfernt wurde.

Wechseln Sie in der [Lookout-Konsole](http://aad.lookout.com) zu **System** > **Intune-Connector** > **Registrierung**, und überprüfen Sie die Einstellungen.  Überprüfen Sie die Azure AD-Gruppen, und stellen Sie sicher, dass der Benutzer des Geräts Mitglied einer der Azure AD-Gruppen ist.

Während ein Gerät sich in diesem Zustand befindet, informiert Lookout den Benutzer weiterhin über alle erkannten Bedrohungen, sendet aber keine Bedrohungsinformationen an Intune.

## <a name="device-reported-as-disconnected"></a>Gerät wird als **getrennt** gemeldet.

**Getrennt** bedeutet, dass das Gerät nicht innerhalb des konfigurierten Intervalls mit Lookout MTP synchronisiert wurde. Der Standardwert hierfür beträgt 30 Tage, der Mindestwert 7 Tage. Entweder die Unternehmensportal-App oder die Lookout for Work-App fehlt auf dem Gerät. Das Problem sollte sich durch erneutes Installieren der Apps beheben lassen. Wenn der Benutzer Lookout for Work öffnet und die App aktiviert, synchronisiert sich das Gerät erneut mit Lookout MTP und Intune.

### <a name="forcing-a-device-sync"></a>Erzwingen einer Gerätesynchronisierung
Der Administrator kann das Gerät im Modul **Geräte** der Lookout MTP-Konsole auswählen und sich entscheiden, es zu löschen.   Wenn der Gerätebesitzer die Lookout for Work-App das nächste Mal öffnet und auf **Aktivieren** klickt, erfolgt eine vollständige Neusynchronisierung des Gerätezustands.

## <a name="device-has-a-new-user"></a>Gerät verfügt über einen neuen Benutzer.
Sie sollten das Gerät zurücksetzen und den neuen Benutzer bitten, sich zu registrieren.  Wählen Sie das Gerät in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Abkoppeln/Zurücksetzen** aus, um das Gerät aus der Verwaltung zu entfernen. Nach dem Abkoppeln können Sie das Gerät löschen.

![Screenshot des Gerätemoduls in der Intune-Verwaltungskonsole mit dargestellter Option „Abkoppeln/Zurücksetzen“](../media/mtp/mtp-retire-device-intune-console.png)

Sie können auch in der [Lookout-Konsole](http://aad.lookout.com) zum Modul **Geräte** navigieren und **Löschen** auswählen.

Wenn sich der neue Benutzer in einer Lookout MTP-Registrierungsgruppe befindet, wird das Gerät angezeigt, nachdem Azure AD das Gerät dem neuen Benutzer zugeordnet hat.

## <a name="compliance-remediation-workflows"></a>Arbeitsabläufe zur Wiederherstellung der Kompatibilität
- [Sie werden aufgefordert, Lookout for Work auf Ihrem Android-Gerät zu installieren]( http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Sie müssen eine Bedrohung beheben, die Lookout for Work auf Ihrem Android-Gerät gefunden hat](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [Sie müssen eine Bedrohung beseitigen, die Lookout for Work auf Ihrem iOS-Gerät erkannt hat](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Siehe auch
[Einrichten Ihres Abonnements für Lookout MTP](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)
