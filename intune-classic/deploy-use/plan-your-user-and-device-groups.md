---
title: Planen von Benutzer- und Gerätegruppen
description: Planen Sie Gruppen, um Ihren organisatorischen Bedürfnissen gerecht zu werden.
keywords: ''
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 679399f306f3837a010cc01799c7567c1e5b5b39
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025313"
---
# <a name="plan-your-user-and-device-groups"></a>Planen von Benutzer- und Gerätegruppen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Gruppen erhalten Sie in Intune maximale Flexibilität beim Verwalten Ihrer Geräte und Benutzer. Sie können Gruppen anhand der folgenden Kriterien einrichten, um den Anforderungen Ihrer Organisation zu entsprechen:

- Geografischer Standort
- Abteilung
- Hardwareeigenschaften
- Betriebssystem
- Unternehmenseigenes Gerät oder im Besitz des Benutzers


## <a name="how-intune-groups-work"></a>Funktionsweise von Intune-Gruppen


Die Standardansicht des Knotens **Gruppen** in der Intune-Verwaltungskonsole:

![Screenshot der Standardansicht des Knotens „Gruppen“ in der Intune-Konsole](../media/Intune_Planning_Groups_Default_small.png)

Richtlinien werden für Gruppen bereitgestellt, daher ist die Gruppenhierarchie eine der wichtigsten Überlegungen zum Entwurf. Sie sollten wissen, dass Sie die übergeordnete Gruppe einer Gruppe nicht ändern können, nachdem Sie die Gruppe erstellt haben. Sobald Sie beginnen, den Intune-Dienst zu verwenden, ist es äußerst wichtig, wie Sie Ihre Gruppen entwerfen. Einige empfohlene Methoden für den Entwurf einer Gruppenhierarchie auf Basis der Anforderungen Ihres Unternehmens werden hier beschrieben.

## <a name="group-membership-rules"></a>Regeln für Gruppenmitgliedschaft

- Eine Gruppe kann entweder Benutzer oder Geräte enthalten, aber nicht beides.

    * **Gerätegruppen**. Hierbei sind sowohl Computer als auch mobile Geräte enthalten. Bevor Sie einer Gruppe einen Computer hinzufügen können, muss dieser registriert werden. Bevor Sie einer Gruppe ein mobiles Gerät hinzufügen können, muss Ihre Umgebung für die Unterstützung mobiler Geräte konfiguriert werden, und die Geräte müssen entweder registriert oder über Exchange ActiveSync ermittelt werden.

    * **Benutzergruppen**. Eine Gruppe kann Benutzer aus Sicherheitsgruppen aufweisen. Sicherheitsgruppen sind mit Ihrer Active Directory-Instanz synchronisiert. Wenn Sie keine Active Directory-Synchronisierung verwenden, können Sie diese Gruppen manuell erstellen.

- Ein Gerät oder ein Benutzer kann zu mehr als einer Gruppe gehören.

- Mitglieder können in einer Gruppe auf Basis folgender Mitgliedschaftsregeln ein- und ausgeschlossen werden:

    * **Mitgliedschaftskriterien**. Hierbei handelt es sich um dynamische Regeln, die von Intune zum Ein- bzw. Ausschließen von Mitgliedern ausgeführt werden. Von diesen Kriterien werden Sicherheitsgruppen und andere Informationen verwendet, die mit Ihrer lokalen Active Directory-Instanz synchronisiert werden. Erfolgen Änderungen an der Sicherheitsgruppe oder den Daten, ändert beim Synchronisieren mit Active Directory auch die Gruppenmitgliedschaft.

    * **Direkte Mitgliedschaft**. Hierbei handelt es sich um statische Regeln, durch die Mitglieder explizit hinzugefügt oder ausgeschlossen werden. Die Mitgliederliste ist statisch.

-   Der Active Directory-Domänendienst (AD DS) ist nicht erforderlich, wenn Sie Benutzergruppen oder Gerätegruppen erstellen, die Benutzer oder Computer einschließen. Damit mobile Geräte zu Gerätegruppen gehören können, muss Ihre Umgebung jedoch so konfiguriert sein, dass mobile Geräte unterstützt werden.

    Zusätzlich müssen die Geräte ermittelt und in Intune hinzugefügt werden.

## <a name="group-relationship-rules"></a>Regeln für Gruppenbeziehungen

- Jede Gruppe, die Sie erstellen, muss eine übergeordnete Gruppe haben. Sie können die übergeordnete Gruppe einer Gruppe nicht ändern, nachdem Sie die Gruppe erstellt haben.

- Beim Hinzufügen von Benutzern oder Geräten zu einer untergeordneten Gruppe gilt Folgendes:

    * Die untergeordnete Gruppe stellt immer eine Teilmenge der übergeordneten Gruppe dar.

    * Wenn Sie einer untergeordneten Gruppe Mitglieder hinzufügen, werden diese automatisch auch der entsprechenden übergeordneten Gruppe hinzugefügt.

    * Mitglieder, die von der übergeordneten Gruppe ausgeschlossen wurden, können der untergeordneten Gruppe nicht hinzugefügt werden.

- Die verfügbare Mitgliedschaft einer untergeordneten Gruppe wird durch die Mitgliedschaft der übergeordneten Gruppe definiert.

- Beim Löschen einer übergeordneten Gruppe werden alle untergeordneten Gruppen gelöscht.

- Es ist möglich, Inhalt und Richtlinien für eine übergeordnete Gruppe bereitzustellen, aber die Bereitstellung für untergeordnete Gruppen auszuschließen.

- Sie können bestimmte Benutzer oder Geräte einer untergeordneten Gruppe hinzufügen, wenn der Benutzer oder das Gerät noch kein Mitglied der übergeordneten Gruppe ist. Wenn Sie dies tun, wird das neue Mitglied der untergeordneten Gruppe der übergeordneten Gruppe hinzugefügt.

    Sie können jedoch keine Mitglieder einer untergeordneten Gruppe hinzufügen, wenn das Mitglied aus der übergeordneten Gruppe ausgeschlossen ist.

- Gruppenmitgliedschaften sind rekursiv. Beispiel:

    * **Pat** ist nur bei einer Gruppe Mitglied: bei der Sicherheitsgruppe **Laptopbenutzer** .

    * Die Gruppe **Laptopbenutzer** ist Mitglied der Sicherheitsgruppe **Genehmigte Benutzer** .

    * Sie erstellen in Intune eine Gruppe, von der eine dynamische Mitgliedschaftsabfrage ausgeführt wird, die die Mitglieder der Gruppe **Genehmigte Benutzer** einschließt. Als Ergebnis enthält die Intune-Benutzergruppe **Pat**.

> [!TIP]
> Überlegen Sie beim Erstellen von Gruppen, wie Richtlinien angewendet werden. Sie verfügen möglicherweise z.B. über Richtlinien, die für Gerätebetriebssysteme oder für verschiedene Rollen oder Organisationseinheiten gelten, die Sie schon in Ihrem Active Directory-Dienst definiert haben. Einige Administratoren finden es sinnvoll, Gerätegruppen zu erstellen, die für iOS, Android und Windows spezifisch sind. Dies erfolgt zusätzlich zum Erstellen von Benutzergruppen für jede Rolle im Unternehmen.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>Integrierte Gruppen
In Intune sind neun integrierte Gruppen verfügbar, die Sie weder bearbeiten noch löschen können: <!--maybe a screen shot would be best?-->

-   **Allen Benutzern**
    -   Nicht gruppierte Benutzer
-   **Alle Geräte**
    -   Alle Computer
    -   Alle mobilen Geräte
        -   Alle direkt verwalteten Geräte
        -   Alle mit Exchange ActiveSync verwalteten Geräte
    -   Alle firmeneigenen Geräte
    -   Nicht gruppierte Geräte

> [!NOTE]
> Das Motto lautet: *möglichst einfach*. Wenn Ihr Unternehmen keine speziellen Anforderungen (wie z.B. die in folgenden Abschnitten beschriebenen) stellt, können Sie einen schlichten Ansatz wählen und die Standardgruppenstruktur und -richtlinien übernehmen. Dadurch kann der Dienst auf lange Sicht besser verwaltet werden. Die Wartung vereinfacht sich, wenn Sie Ihre Benutzer einheitlich behandeln können. Kleine Unterschiede in den Gruppen führen dazu, dass Sie weniger Richtlinien zu verwalten haben.


### <a name="all-users-and-devices-in-your-organization"></a>Alle Benutzer und Geräte in Ihrem Unternehmen
Definieren Sie eine übergeordnete Gruppe für alle Benutzer und Geräte in Ihrem Unternehmen. Sie verfügen wahrscheinlich über Richtlinien, die für alle gelten. Zu diesem Zweck können Sie die Intune-Standardgruppen **Alle Benutzer** und **Alle Geräte** verwenden. Untergruppen, die Geräte nach speziellen Eigenschaften organisieren, z.B. eine BYOD-Gruppe (Bring Your Own Device) und eine Gruppe für unternehmenseigene Geräte (Corporate-Owned, CO), können den übergeordneten Gruppen **Alle Benutzer** und **Alle Geräte** untergeordnet sein.

## <a name="customize-groups-for-your-organization"></a>Anpassen von Gruppen für Ihre Organisation

### <a name="byod-and-corporate-owned-devices"></a>BYOD- und firmeneigene Geräte
Wenn Ihre Organisation Mitarbeitern die Nutzung eigener Geräte gestattet, unternehmenseigene Geräte bereitstellt oder eine Kombination aus beidem zulässt, empfiehlt es sich, separate Richtlinien für diese beiden Gerätekategorien anzuwenden.

Im Fall von BYOD oder eines kombinierten Ansatzes achten Sie darauf, dass Sie Ihre Richtlinien so planen, dass die vor Ort geltenden Datenschutzbestimmungen nicht verletzt werden. Erstellen Sie eine übergeordnete Gruppe für alle Benutzer, die ihre eigenen Geräte einsetzen. Sie können diese Gruppe dann dazu verwenden, Richtlinien anzuwenden, die für alle Benutzer in dieser Kategorie gelten.

![Erstellen einer übergeordneten BYOD-Gruppe](../media/Intune_Planning_Groups_BYOD_small.png)

Ebenso können Sie eine Gruppe für die Benutzer eines CO-Geräts in Ihrer Organisation erstellen:

![Gleichgeordnete Benutzergruppen für BYOD- und CO-Geräte](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>Gruppen für geografische Regionen
Wenn Ihre Organisation Richtlinien für bestimmte Regionen benötigt, können Sie Gruppen basierend auf der geografischen Region erstellen. Sie können diese auf Grundlage regionaler Gruppen anlegen, die Sie möglicherweise bereits in Ihrer Active Directory-Instanz erstellt haben, und Sie mit Azure Active Directory synchronisieren. Sie können regionale Gruppen auch direkt in Azure Active Directory erstellen.

Die nächsten Screenshots zeigen Ihnen, wie Sie Intune-Gruppen basierend auf Gruppen erstellen, die mit Ihrer lokalen Active Directory-Instanz synchronisiert sind. In diesen Beispielen wird vorausgesetzt, dass Sie über eine Active Directory-Sicherheitsgruppe namens **US Users Group** verfügen.

Stellen Sie zunächst allgemeine Informationen bereit.

![Screenshot des Bereichs „Gruppe bearbeiten“](../media/Intune_Planning_Groups_AD_General_small.png)

Wählen Sie unter den **Mitgliedschaftskriterien** die Gruppe **US Users Group**, die mit Active Directory synchronisiert wurde, als Sicherheitsgruppe aus, die unter den Mitgliedschaftsregeln verwendet wird.

![Screenshot des Dialogfelds „Gruppe bearbeiten“](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Überprüfen Sie Ihre Eingaben, und wählen Sie anschließend **Fertig stellen** aus, um die Gruppe zu erstellen.

![Screenshot des Dialogfelds „Gruppe bearbeiten“](../media/Intune_Planning_Groups_AD_Summary_small.png)

In unserem Beispiel haben wir auch eine Gruppe namens **MEA**, die den Nahen Osten und Asien (MEA) umfasst.

> [!NOTE]
> Wenn die Gruppenmitgliedschaft nicht auf Basis der Mitgliedschaft in Sicherheitsgruppen entschieden wird, stellen Sie sicher, dass Sie Gruppenmitgliedern Intune-Lizenzen zugewiesen haben.

### <a name="groups-for-specific-hardware"></a>Gruppen für bestimmte Hardware
Wenn Ihre Organisation Richtlinien benötigt, die auf bestimmte Hardwaretypen angewendet werden, können Sie die Gruppen auf Basis dieser Anforderung erstellen. Sie können die Richtlinien basierend auf bestimmten Gruppen anlegen, die Sie bereits in Ihrer lokalen Active Directory-Instanz erstellt haben, und Sie anschließend mit Azure Active Directory synchronisieren. Sie können Gruppen auch direkt in Azure Active Directory erstellen. In diesem Beispiel verwenden wir **US Users Group** als übergeordnete Gruppe für die Gruppe der **Laptopbenutzer**.

![Dialogfeld „Sicherheitsgruppe auswählen“](../media/Intune_Planning_Groups_Laptop_small.png)

An diesem Punkt sollte die Hierarchie Ihrer Gruppe ähnlich wie der nächste Screenshot aussehen. Sie können sehen, dass jetzt in der Intune-Gruppe der **Laptopbenutzer** entsprechende Mitglieder enthalten sind. Alle auf diese Gruppe angewendeten Richtlinien werden auf BYOD-Laptopbenutzer aus der Region „USA“ angewendet.

![Anzeigen der Gruppe „Laptopbenutzer“](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>Gruppen für bestimmte Betriebssysteme
Wenn Ihr Unternehmen Richtlinien benötigt, die auf bestimmte Betriebssysteme wie Android, iOS oder Windows angewendet werden, können Sie die Gruppen auf Basis dieser Anforderung erstellen. Wie in früheren Beispielen gezeigt, können Sie diese auf Basis betriebssystemspezifischer Gruppen anlegen, die Sie bereits in Ihrer lokalen Active Directory-Instanz erstellt haben, und Sie mit Azure Active Directory synchronisieren. Sie können Sie auch direkt in Ihrer Azure Active Directory-Instanz erstellen.

Mithilfe der in früheren Beispielen vorgestellten Methode können Sie Gruppen erstellen, die auf Benutzern <!--devices?--> basieren, die bestimmte Betriebssystemplattformen verwenden.

> [!NOTE]
> Wenn Sie über Benutzer verfügen, die mehrere mobile Plattformen/Betriebssysteme verwenden, und Sie keine automatisierte Möglichkeit zum Kategorisieren von Benutzern als Android-, iOS- oder Windows-Benutzer haben, sollten Sie die Anwendung der Richtlinien auf Geräteebene erwägen. Dadurch erhalten Sie mehr Flexibilität bei der Anwendung von betriebssystemspezifischen Richtlinien.
>
> Sie können keine Gruppen bereitstellen, die dynamisch auf dem Betriebssystem des Geräts basieren. Führen Sie stattdessen diesen Schritt aus, indem Sie Active Directory oder die Sicherheitsgruppen von Azure Active Directory verwenden.

![Gruppe „Laptopbenutzer“](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

Nachdem alle Ihre Benutzergruppen basierend auf diesen Anforderungen Ihres Unternehmens aufgefüllt wurden, sollte die Gruppenhierarchie in etwa wie folgt aussehen:

![Ansicht der Gruppenhierarchie](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Sie können diese Hierarchie dazu verwenden, die Richtlinien des Unternehmens anzuwenden.

### <a name="device-groups"></a>Gerätegruppen
Sie können auch ähnliche Gruppen für Geräte erstellen, wie hier gezeigt, wobei Sie mit einer umfassenden Gruppe beginnen, die alle benutzereigenen Geräte für das BYOD-Szenario einbezieht:

![Dialogfeld „Gruppe erstellen“](../media/Intune_Planning_Groups_Device_General_small.png)

Stellen Sie sicher, dass Sie die Option **Alle Geräte (Computer und mobile Geräte)** auswählen, damit die Gruppe alle BYOD-Geräte umfasst:

![Seite „Mitgliedschaftskriterien definieren“](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Überprüfen Sie Ihre Eingaben, und wählen Sie anschließend **Fertig stellen**aus, um die BYOD-Gruppe zu erstellen.

![Dialogfeld „Gruppe erstellen“](../media/Intune_Planning_Groups_Device_Summary_small.png)

Setzen Sie die Erstellung der Gerätegruppen fort, bis Sie über eine Gerätegruppenhierarchie verfügen, die der Benutzergruppenhierarchie ähnelt. Ihr Gruppenknoten wird in der Intune-Konsole etwa wie folgt aussehen:

![Intune-Ansicht der Gruppenhierarchie](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>Gruppenhierarchien und Benennungskonventionen
Zur Vereinfachung der Richtlinienverwaltung wird empfohlen, jede Richtlinie gemäß dem Zweck, der Plattform und dem Bereich ihrer Anwendung zu benennen. Verwenden Sie einen Benennungsstandard, der die Struktur befolgt, die Sie erstellt haben, als Sie sich darauf vorbereitet haben, Ihre Richtlinien anzuwenden.

Eine Android-Richtlinie, die auf alle unternehmenseigenen mobilen Android-Geräte in den USA angewendet wird, kann z.B. wie folgt benannt werden: **CO_US_Mob_Android_General**

![Erstellen einer Richtlinie für Android](../media/Intune_planning_policy_android_small.png)

Wenn Sie Ihre Richtlinien auf diese Art benennen, können Sie Richtlinien sowie deren vorgesehenen Zweck und Gültigkeitsbereich im **Richtlinienknoten** erkennen, wie nachfolgend dargestellt:

![Liste der Intune-Richtlinien](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>Nächste Schritte
[Erstellen von Gruppen](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
