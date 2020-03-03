---
title: So setzen Sie nur die Unternehmensdaten in einer App zurück
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Unternehmensdaten mit Microsoft Intune selektiv in durch Intune verwalteten Apps zurücksetzen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f6992aa93e1ca5a095b1e92a16a07bd0eb1c2f5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513638"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Zurücksetzen nur von Unternehmensdaten in einer in Intune verwalteten App

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Wenn ein Gerät verloren geht oder gestohlen wird oder wenn der Mitarbeiter das Unternehmen verlässt, müssen Sie sicherstellen, dass Unternehmensdaten in Apps vom Gerät entfernt werden. Allerdings sollten Sie persönliche Daten nicht vom Gerät entfernen, insbesondere dann nicht, wenn das Gerät dem Mitarbeiter gehört.

>[!NOTE]
> Das Löschen von Unternehmensdaten aus mit Intune verwalteten Apps wird derzeit nur für die Plattformen iOS/iPadOS, Android und Windows 10 unterstützt. Von Intune verwaltete Apps sind Anwendungen, die das Intune-App-SDK beinhalten und über ein lizenziertes Benutzerkonto für Ihre Organisation verfügen. Die Bereitstellung von Richtlinien für den Anwendungsschutz ist nicht erforderlich, um ein selektives Zurücksetzen von Apps zu aktivieren.

Um Unternehmensdaten aus Apps selektiv zu entfernen, erstellen Sie mithilfe der Schritte in diesem Thema eine Zurücksetzungsanforderung. Nach Abschluss der Anforderung werden die Unternehmensdaten beim nächsten Ausführen der Anwendung aus der App entfernt. Wenn die in den APP-Zugriffseinstellungen festgelegten Bedingungen nicht erfüllt sind, können Sie neben dem Erstellen von Anforderungen des Zurücksetzens auch durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen. Dieses Feature hilft Ihnen dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

>[!IMPORTANT]
> Direkt aus der App mit dem nativen Adressbuch synchronisierte Kontakte werden entfernt. Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. Dies betrifft derzeit nur die Microsoft Outlook-App.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Bereitgestellte WIP-Richtlinien ohne Benutzerregistrierung
WIP-Richtlinien (Windows Information Protection) können bereitgestellt werden, ohne dass MDM-Benutzer ihr Windows 10-Gerät registrieren müssen. Diese Konfiguration ermöglicht es Unternehmen, ihre Unternehmensdokumente auf der Grundlage der WIP-Konfiguration zu schützen, während der Benutzer die Verwaltung seiner eigenen Windows-Geräte beibehalten kann. Sobald Dokumente durch eine WIP-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Client-App** > **Selektive App-Zurücksetzung** aus. Weitere Informationen finden Sie unter [Erstellen und Bereitstellen von WIP-App-Schutzrichtlinien (Windows Information Protection) in Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Erstellen einer Zurücksetzungsanforderung

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Selektive App-Zurücksetzung** > **Zurücksetzungsanforderung erstellen** aus.<br>
   Der Bereich **Zurücksetzungsanforderung erstellen** wird angezeigt.
3. Klicken Sie auf **Benutzer auswählen**, wählen Sie den Benutzer aus, dessen App-Daten Sie löschen möchten, und klicken Sie dann unten im Bereich **Benutzer auswählen** auf **Auswählen**.

    ![Screenshot des Bereichs „Benutzer auswählen“](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Klicken Sie auf **Wählen Sie das Gerät aus**, wählen Sie das Gerät aus, und klicken Sie dann unten im Bereich **Gerät auswählen** auf **Auswählen**.

    ![Screenshot des Bereichs „Zurücksetzungsanforderung erstellen“, in dem das Gerät ausgewählt wird](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Klicken Sie auf **Erstellen**, um eine Zurücksetzungsanforderung zu erstellen.

Der Dienst erstellt für jede geschützte App auf dem Gerät und den zugeordneten Benutzer eine separate Zurücksetzungsanforderung und überwacht diese.

   ![Screenshot des Bereichs „Client-Apps – selektive App-Zurücksetzung“](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>Überwachen der Löschanforderungen

Sie erhalten einen zusammengefassten Bericht, der den Gesamtstatus der Zurücksetzungsanforderung zeigt und die Anzahl der ausstehenden Anforderungen und Fehler enthält. Um weitere Informationen zu erhalten, gehen Sie folgendermaßen vor:

1. Im Bereich **Apps** > **Selektive App-Zurücksetzung** wird eine nach Benutzern gruppierte Liste Ihrer Anforderungen angezeigt. Da das System für jede geschützte App, die auf dem Gerät ausgeführt wird, eine Zurücksetzungsanforderung erstellt, werden möglicherweise für einen Benutzer mehrere Anforderungen angezeigt. Der Status gibt an, ob eine Zurücksetzungsaufforderung noch **aussteht**oder **fehlgeschlagen**ist, bzw. **erfolgreich**ausgeführt wurde.

    ![Screenshot des Zurücksetzungsanforderungsstatus im Bereich „Selektive App-Zurücksetzung“](./media/apps-selective-wipe/wipe-request-status-1.png)

Darüber hinaus können Sie den Gerätenamen und den Gerätetyp anzeigen. Diese Informationen sind beim Lesen von Berichten hilfreich.

>[!IMPORTANT]
> Der Benutzer muss die App für das Zurücksetzen öffnen, und das Zurücksetzen dauert bis zu 30 Minuten, nachdem die Anforderung gestellt wurde.

## <a name="delete-a-wipe-request"></a>Löschen einer Zurücksetzungsanforderung

Zurücksetzungen mit Status „Ausstehend“ werden angezeigt, bis Sie sie manuell löschen. So löschen Sie manuell eine Zurücksetzungsanforderung

1. Öffnen Sie den Bereich **Client-Apps – selektive App-Zurücksetzung**.

2. Klicken Sie mit der rechten Maustaste auf die Zurücksetzungsanforderung, die Sie löschen möchten, und wählen Sie dann **Zurücksetzungsanforderung löschen** aus.

    ![Screenshot der Zurücksetzungsanforderungsliste im Bereich „Selektive App-Zurücksetzung“](./media/apps-selective-wipe/delete-wipe-request.png)

3. Sie werden aufgefordert, den Löschvorgang zu bestätigen. Wählen Sie **Ja** oder **Nein** aus, und klicken Sie dann auf **OK**.

## <a name="see-also"></a>Weitere Informationen:
[Was sind App-Schutzrichtlinien?](app-protection-policy.md)

[Was ist die App-Verwaltung?](app-management.md)
