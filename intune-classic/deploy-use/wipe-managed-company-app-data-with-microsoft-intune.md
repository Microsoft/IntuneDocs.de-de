---
title: Löschen verwalteter Unternehmensdaten aus Apps
description: Erfahren Sie, wie Sie selektiv Unternehmensdaten von Geräten entfernen können.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8d946b551118441b737335f6bd8c4603a49e0dd2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="wipe-company-app-data-with-intune-mam"></a>Zurücksetzen von Unternehmens-App-Daten mit Intune MAM

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Wenn ein Gerät verloren geht oder gestohlen wird oder wenn der Mitarbeiter das Unternehmen verlässt, müssen Sie sicherstellen, dass Unternehmensdaten in Apps vom Gerät entfernt werden. Allerdings sollten Sie persönliche Daten nicht vom Gerät entfernen, insbesondere dann nicht, wenn das Gerät dem Mitarbeiter gehört.

Um Unternehmensdaten aus Apps selektiv zu entfernen, erstellen Sie mithilfe der Schritte in diesem Thema eine Zurücksetzungsanforderung. Nach Abschluss der Anforderung werden die Unternehmensdaten beim nächsten Ausführen der Anwendung aus der App entfernt.

>[!IMPORTANT]
> Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt. Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. Dies betrifft derzeit nur die Microsoft Outlook-App.

## <a name="create-a-wipe-request"></a>Erstellen einer Zurücksetzungsanforderung

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2.  Wählen Sie **Weitere Dienste** aus, geben Sie in das Filtertextfeld **Intune** ein, und wählen Sie **Intune-App-Schutz** aus. Das Blatt „Mobile Anwendungsverwaltung mit Intune“ wird geöffnet.

    ![Screenshot des Blatts „Neue Zurücksetzungsanforderung“](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  Wählen Sie auf dem Blatt **Einstellungen** die Option **Zurücksetzungsanforderungen** aus.

3.  Wählen Sie **Neue Zurücksetzungsanforderung** aus. Dadurch wird das Blatt **Neue Zurücksetzungsanforderung** geöffnet.

    ![Screenshot des Blatts „Neue Zurücksetzungsanforderung“](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  Wählen Sie **Benutzer** aus, um das Blatt **Benutzer** zu öffnen, und den Benutzer auszuwählen, dessen App-Daten gelöscht werden sollen.

5.  Wählen Sie **Gerät** aus. Damit öffnen Sie das Blatt **Gerät**, auf dem alle Geräte aufgeführt werden, die dem ausgewählten Benutzer zugeordnet sind. Es enthält außerdem zwei Spalten – eine mit dem Gerätenamen, einem vom Benutzer festgelegten Anzeigenamen, und eine mit dem Gerätetyp und der Geräteplattform. Wählen Sie das Gerät aus, das zurückgesetzt werden soll.

6.  Sie befinden sich nun wieder auf dem Blatt **Neue Zurücksetzungsanforderung**. Wählen Sie **OK** aus, um eine Zurücksetzungsanforderung zu erstellen. 

Der Dienst erstellt für jede geschützte App auf dem Gerät und den zugeordneten Benutzer eine separate Zurücksetzungsanforderung und überwacht diese.

>[!NOTE]
> Sie können auch **Zurücksetzungsanforderungen** erstellen, indem Sie auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“ auf die Kachel **Zurücksetzungsanforderung** klicken.

## <a name="monitor-your-wipe-requests"></a>Überwachen der Löschanforderungen

Sie erhalten einen zusammengefassten Bericht, der den Gesamtstatus der Zurücksetzungsanforderung zeigt und die Anzahl der ausstehenden Anforderungen und Fehler enthält. Um weitere Informationen zu erhalten, gehen Sie folgendermaßen vor:

1.  Klicken Sie auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“ auf die Kachel **Zurücksetzungsanforderungen**.

2.  Wählen Sie auf dem Blatt **Zurücksetzungsanforderung** die Kachel **Zurücksetzungsanforderung** aus, um das Blatt **Zurücksetzungsanforderung** zu öffnen.

3.  Auf dem Blatt **Zurücksetzungsanforderung** wird eine Liste mit Ihren Anforderungen, gruppiert nach Benutzer, angezeigt. Da das System für jede geschützte App, die auf dem Gerät ausgeführt wird, eine Zurücksetzungsanforderung erstellt, werden möglicherweise für einen Benutzer mehrere Anforderungen angezeigt. Der Status gibt an, ob eine Zurücksetzungsaufforderung noch **aussteht**oder **fehlgeschlagen**ist, bzw. **erfolgreich**ausgeführt wurde.

    ![Screenshot des Blatts „Neue Zurücksetzungsanforderung“](../media/AppManagement/wipe-request-status-1.png)

Darüber hinaus können Sie den Gerätenamen und den Gerätetyp anzeigen. Diese Informationen sind beim Lesen von Berichten hilfreich.

>[!IMPORTANT]
> Der Benutzer muss die App für das Zurücksetzen öffnen, und das Zurücksetzen dauert bis zu 30 Minuten, nachdem die Anforderung gestellt wurde.

## <a name="delete-a-wipe-request"></a>Löschen einer Zurücksetzungsanforderung

Zurücksetzungen mit Status „Ausstehend“ werden angezeigt, bis Sie sie manuell löschen.  So löschen Sie manuell eine Zurücksetzungsanforderung

1.  Klicken Sie auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“ auf die Kachel **Zurücksetzungsanforderungen**.

2.  Wählen Sie auf dem Blatt **Zurücksetzungsanforderung** die Kachel **Zurücksetzungsanforderung** aus, um das Blatt **Zurücksetzungsanforderung** zu öffnen.

3.  Klicken Sie mit der rechten Maustaste auf die Zurücksetzungsanforderung, die Sie löschen möchten, und wählen Sie dann **Zurücksetzungsanforderung abbrechen** aus.

    ![Screenshot des Blatts „Neue Zurücksetzungsanforderung“](../media/AppManagement/delete-wipe-request.png)

4.  Sie werden aufgefordert, den Löschvorgang zu bestätigen. Wählen Sie **Ja** oder **Nein** aus, und klicken Sie dann auf **OK**.


### <a name="see-also"></a>Siehe auch
[Schützen von App-Daten mithilfe der Verwaltungsrichtlinien für mobile Apps](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Verwenden des Azure-Portals](azure-portal-for-microsoft-intune-mam-policies.md)
