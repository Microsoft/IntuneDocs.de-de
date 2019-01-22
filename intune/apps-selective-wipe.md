---
title: So setzen Sie nur die Unternehmensdaten in einer App zurück
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Unternehmensdaten mit Microsoft Intune selektiv in durch Intune verwalteten Apps zurücksetzen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd6ac0b1fdb64897a831c0111f7e0a611c85bede
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210702"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Zurücksetzen nur von Unternehmensdaten in einer in Intune verwalteten App

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Wenn ein Gerät verloren geht oder gestohlen wird oder wenn der Mitarbeiter das Unternehmen verlässt, müssen Sie sicherstellen, dass Unternehmensdaten in Apps vom Gerät entfernt werden. Allerdings sollten Sie persönliche Daten nicht vom Gerät entfernen, insbesondere dann nicht, wenn das Gerät dem Mitarbeiter gehört.

>[!NOTE]
> Für das Zurücksetzen von Unternehmensdaten von mit Intune verwalteten Apps werden derzeit die iOS- und Android-Plattform unterstützt. Von Intune verwaltete Apps sind Anwendungen, die das Intune-App-SDK beinhalten und über ein lizenziertes Benutzerkonto für Ihre Organisation verfügen. Die Bereitstellung von Richtlinien für den Anwendungsschutz ist nicht erforderlich, um ein selektives Zurücksetzen von Apps zu aktivieren.

Um Unternehmensdaten aus Apps selektiv zu entfernen, erstellen Sie mithilfe der Schritte in diesem Thema eine Zurücksetzungsanforderung. Nach Abschluss der Anforderung werden die Unternehmensdaten beim nächsten Ausführen der Anwendung aus der App entfernt. Wenn die in den APP-Zugriffseinstellungen festgelegten Bedingungen nicht erfüllt sind, können Sie neben dem Erstellen von Anforderungen des Zurücksetzens auch durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen. Dieses Feature hilft Ihnen dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

>[!IMPORTANT]
> Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt. Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. Dies betrifft derzeit nur die Microsoft Outlook-App.

## <a name="create-a-wipe-request"></a>Erstellen einer Zurücksetzungsanforderung

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2.  Wählen Sie **Alle Dienste** aus, geben Sie in das Filtertextfeld **Intune** ein, und wählen Sie **Intune** aus. Der Intune-Bereich wird geöffnet. Wählen Sie darin den Bereich **Client-Apps** aus.

    ![Screenshot des Bereichs „Microsoft Intune“](./media/apps-selective-wipe01.png)

3.  Wählen Sie im Bereich **Client-Apps** die Option **Selektive App-Zurücksetzung** aus.

4.  Wählen Sie **Neue Zurücksetzungsanforderung** aus. Dadurch wird der Bereich **Neue Zurücksetzungsanforderung** geöffnet.

    ![Screenshot des Bereichs „Neue Zurücksetzungsanforderung“](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Markieren Sie einen Benutzer, und klicken Sie dann auf **Auswählen**, um den Benutzer auszuwählen, dessen App-Daten Sie zurücksetzen möchten.

6.  Wählen Sie anschließend im Bereich **Neue Zurücksetzungsanforderung** die Option **Gerät** aus. Damit wird der Bereich **Gerät auswählen** geöffnet, in dem alle Geräte aufgeführt werden, die dem ausgewählten Benutzer zugeordnet sind. Der Bereich enthält zwei Spalten: eine mit dem Gerätenamen – einem vom Benutzer festgelegten Anzeigenamen – und eine mit dem Gerätetyp und der Geräteplattform. Wählen Sie das Gerät aus, das zurückgesetzt werden soll.

7.  Sie befinden sich nun wieder im Bereich **Neue Zurücksetzungsanforderung**. Klicken Sie auf **OK**, um eine Zurücksetzungsanforderung zu erstellen.

Der Dienst erstellt für jede geschützte App auf dem Gerät und den zugeordneten Benutzer eine separate Zurücksetzungsanforderung und überwacht diese.

## <a name="monitor-your-wipe-requests"></a>Überwachen der Löschanforderungen

Sie erhalten einen zusammengefassten Bericht, der den Gesamtstatus der Zurücksetzungsanforderung zeigt und die Anzahl der ausstehenden Anforderungen und Fehler enthält. Um weitere Informationen zu erhalten, gehen Sie folgendermaßen vor:

1.  Im Bereich **Client-Apps – selektive App-Zurücksetzung** wird eine nach Benutzern gruppierte Liste Ihrer Anforderungen angezeigt. Da das System für jede geschützte App, die auf dem Gerät ausgeführt wird, eine Zurücksetzungsanforderung erstellt, werden möglicherweise für einen Benutzer mehrere Anforderungen angezeigt. Der Status gibt an, ob eine Zurücksetzungsaufforderung noch **aussteht**oder **fehlgeschlagen**ist, bzw. **erfolgreich**ausgeführt wurde.

    ![Screenshot des Zurücksetzungsanforderungsstatus im Bereich „Selektive App-Zurücksetzung“](./media/wipe-request-status-1.png)

Darüber hinaus können Sie den Gerätenamen und den Gerätetyp anzeigen. Diese Informationen sind beim Lesen von Berichten hilfreich.

>[!IMPORTANT]
> Der Benutzer muss die App für das Zurücksetzen öffnen, und das Zurücksetzen dauert bis zu 30 Minuten, nachdem die Anforderung gestellt wurde.

## <a name="delete-a-wipe-request"></a>Löschen einer Zurücksetzungsanforderung

Zurücksetzungen mit Status „Ausstehend“ werden angezeigt, bis Sie sie manuell löschen. So löschen Sie manuell eine Zurücksetzungsanforderung

1.  Öffnen Sie den Bereich **Client-Apps – selektive App-Zurücksetzung**.

2.  Klicken Sie mit der rechten Maustaste auf die Zurücksetzungsanforderung, die Sie löschen möchten, und wählen Sie dann **Zurücksetzungsanforderung löschen** aus.

    ![Screenshot der Zurücksetzungsanforderungsliste im Bereich „Selektive App-Zurücksetzung“](./media/delete-wipe-request.png)

3.  Sie werden aufgefordert, den Löschvorgang zu bestätigen. Wählen Sie **Ja** oder **Nein** aus, und klicken Sie dann auf **OK**.

### <a name="see-also"></a>Siehe auch
[Was sind App-Schutzrichtlinien?](app-protection-policy.md)

[Was ist die App-Verwaltung?](app-management.md)
