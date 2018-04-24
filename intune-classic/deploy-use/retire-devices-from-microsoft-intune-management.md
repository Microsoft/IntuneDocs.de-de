---
title: Abkoppeln von Geräten
description: Intune unterstützt sowohl die selektive als auch die vollständige Zurücksetzung, um das Gerät aus der Intune-Verwaltung zu entfernen, indem die Richtlinie und das Unternehmensportal entfernt werden.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d9dc8fdd7437c9de49df9ea9a4c9641ac9d590de
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="retire-devices-from-intune-management"></a>Abkoppeln von Geräten von der Intune-Verwaltung

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Unabhängig davon, ob Geräte Unternehmenseigentum sind oder den Mitarbeitern persönlich gehören – irgendwann muss ein verwaltetes Gerät aus der Intune-Verwaltung entfernt werden.

Geräte werden nie ohne Ihr Zutun aus Intune entfernt, selbst wenn die Geräte eine Zeitlang keine Verbindung mit dem Intune-Dienst hergestellt haben.

Es kann aus einer Vielzahl von Gründen erforderlich sein, ein Gerät außer Kraft zu setzen:

-   Ein Benutzer verlässt ein Unternehmen planmäßig („verwalteter“ Abschied)
-   Ein Benutzer verlässt das Unternehmen plötzlich (wird entlassen, kündigt etc.)
-   Verlust des Geräts
-   Umfunktionieren eines Geräts (Übertragen auf einen anderen Benutzer, Wiederverwendung für einen anderen Zweck usw.)

Sie können ein Gerät, das als mobiles Gerät verwaltet wird, entweder selektiv oder vollständig zurücksetzen oder ein Gerät sperren und das Kennwort zurücksetzen. Durch das Zurücksetzen des Geräts geben Sie das Abonnement des Benutzers frei, sodass Sie ein anderes Gerät hinzufügen können. Außerdem können Sie mit der Intune-Clientsoftware verwaltete PCs außer Betrieb nehmen.

## <a name="wipe-data-and-apps-from-devices"></a>Löschen von Daten und Apps von Geräten
Sowohl bei der selektiven als auch bei der vollständigen Zurücksetzung wird das Gerät aus der Intune-Verwaltung entfernt, indem dessen Richtlinie und das Unternehmensportal entfernt werden. Somit verfügt das Gerät nicht mehr über die erforderlichen Anmeldeinformationen für die Anmeldung bei Unternehmensressourcen wie Microsoft SharePoint, E-Mail oder Office 365.

[Selektives Zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) ist die bevorzugte Maßnahme für Mitarbeiter, die ihre eigenen Geräte bei Intune registriert haben, da persönliche Informationen auf dem Gerät nicht betroffen sind. Es werden nur Unternehmensdaten entfernt.

Geräte, die einem neuen Verwendungszweck zugewiesen werden sollen, können Sie auch [vollständig zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), um sie auf die Werks- bzw. Standardeinstellungen zurückzusetzen.

### <a name="removing-user-licenses-and-managed-devices"></a>Entfernen von Benutzerlizenzen und verwalteten Geräten
Wenn Sie eine Benutzerlizenz entfernen, werden die registrierten Geräte von Benutzern nicht mehr angemeldet. Als bewährte Methode sollten Sie das selektive Zurücksetzen verwenden, um Unternehmensdaten von verwalteten Geräten zu entfernen, bevor Sie die Intune-Lizenz für einen Benutzer entfernen. Sobald die Benutzerlizenz entfernt ist, ist das Gerät nicht mehr für Remoteaktionen vorgesehen.

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>So löschen Sie Geräte im Azure Active Directory-Portal

1.  Melden Sie sich mit den Anmeldeinformationen Ihrer Organisation bei [http://aka.ms/accessaad](http://aka.ms/accessaad) oder [https://portal.office.com](https://portal.office.com) an, und wählen Sie anschließend **Admin Center** &gt; **Azure AD** aus.

2.  Erstellen Sie ein Azure-Abonnement, wenn Sie noch keins besitzen. Hierfür sollte keine Kreditkarte oder Zahlung erforderlich sein, wenn Sie über ein kostenpflichtiges Konto verfügen. Wählen Sie den Abonnementlink **Register your free Azure Active Directory** (Ihr kostenloses Azure Active Directory registrieren) aus.

4.  Wählen Sie zuerst **Active Directory** und anschließend Ihre Organisation aus.

5.  Wählen Sie die Registerkarte **Benutzer** aus.

6.  Wählen Sie den Benutzer aus, dessen Geräte Sie löschen möchten.

7.  Klicken Sie auf **Geräte**.

8.  Wählen Sie die gewünschten Geräte und anschließend **Gerät löschen** aus. Das Gerät wird bei der nächsten Synchronisierung mit Active Directory gelöscht. Dies geschieht in der Regel innerhalb von vier Stunden. Nach der Synchronisierung wird das Gerät aus der Verwaltung entfernt. Dadurch wird dieses Gerät beim Gerätegrenzwert für diesen Benutzer nicht mehr berücksichtigt.

## <a name="retire-managed-computers"></a>Abkoppeln von verwalteten Computern
Computer, die mit Intune-Clientsoftware verwaltet werden, können in der Intune-Verwaltungskonsole von der Verwaltung entfernt werden. Dadurch wird gleichzeitig die Clientsoftware deinstalliert, und die Intune-Richtlinien werden vom Computer gelöscht. Hier erhalten Sie Informationen zum [Abkoppeln von mit der Intune-Clientsoftware verwalteten Computer](retire-a-windows-pc-with-microsoft-intune.md).

## <a name="block-access-a-device"></a>Blockieren des Zugriffs auf ein Gerät
Wenn ein Gerät verloren gegangen ist oder wenn ein Gerät außer Kraft gesetzt werden muss, weil ein Mitarbeiter Ihr Unternehmen verlassen hat, ohne firmeneigene Hardware zurückzugeben, können Sie für das Gerät auch [die Kennung zurücksetzen und es remote sperren](use-remote-lock-and-passcode-reset-in-microsoft-intune.md). Dadurch wird verhindert, dass Firmeninformationen missbräuchlich verwendet werden, obwohl Sie das Gerät möglicherweise als Verlust abschreiben müssen.

Sie sollten auch die Lizenz für das Intune-Benutzerkonto des Mitarbeiters widerrufen. Gleichzeitig wird die Lizenz freigegeben, und Sie können sie einem neuen Benutzerkonto zuweisen.

## <a name="retire-hardware"></a>Außerbetriebnehmen von Hardware
Manchmal ist es das Gerät selbst, das das Ende seines Lebenszyklus erreicht hat. In solchen Fällen werden durch das [Zurücksetzen auf die Werkseinstellungen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) alle Daten vom Gerät und das Gerät aus Intune entfernt. Dann können Sie die Hardware gemäß der Unternehmensrichtlinie beseitigen.

### <a name="see-also"></a>Siehe auch
[Schützen von Daten durch vollständiges oder selektives Zurücksetzen](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)
