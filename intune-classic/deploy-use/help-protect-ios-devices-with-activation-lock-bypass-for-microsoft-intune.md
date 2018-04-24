---
title: Verwalten der iOS-Aktivierungssperre auf Geräten
description: Microsoft Intune kann Sie beim Verwalten der iOS-Aktivierungssperre unterstützen, einem Feature der App „Mein iPhone suchen“ für iOS 7.1 und höher.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/24/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 37593e8c554cad73182873b01f6388bdb9cb0035
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Unterstützen des Schutz von iOS-Geräten durch Umgehung der Aktivierungssperre für Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune kann Sie bei der Verwaltung der iOS-Aktivierungssperre unterstützen, einer Funktion der Mein iPhone suchen-App für Geräte mit iOS 8.0 und höher. Die Aktivierungssperre wird automatisch aktiviert, wenn ein Benutzer die App „Mein iPhone suchen“ auf einem Gerät öffnet. Nach der Aktivierung müssen die Apple-ID und das Kennwort des Benutzers eingegeben werden, bevor folgende Vorgänge möglich sind: 

-   Deaktivieren von „Mein iPhone suchen“

-   Löschen des Geräts

-   Reaktivieren des Geräts

## <a name="how-activation-lock-affects-you"></a>Auswirkungen der Aktivierungssperre
Obwohl die Aktivierungssperre zum Schutz von iOS-Geräten beiträgt und die Chancen einer Wiederherstellung bei Verlust oder Diebstahl des Geräts erhöht, kann diese Funktion Sie als IT-Administrator vor eine Reihe von Herausforderungen stellen. Beispiel:

-   Ein Benutzer richtet die Aktivierungssperre auf einem Gerät ein. Anschließend verlässt der Benutzer das Unternehmen und gibt das Gerät zurück. Ohne die Apple-ID und das Kennwort des Benutzers gibt es keine Möglichkeit, das Gerät zu reaktivieren.

-   Sie benötigen einen Bericht über alle Geräte, bei denen die Aktivierungssperre aktiviert ist.

-   Während einer Geräteaktualisierung in Ihrem Unternehmen möchten Sie einige Geräte einer anderen Abteilung zuweisen. Es können nur Geräte neu zugewiesen werden, bei denen die Aktivierungssperre nicht aktiviert ist.

Apple hat zur Behebung dieser Probleme eine Umgehung der Aktivierungssperre in iOS 7.1 eingeführt. Auf diese Weise können Sie die Aktivierungssperre von überwachten Geräten ohne Apple-ID und Kennwort des Benutzers entfernen. Überwachte Geräte können einen gerätespezifischen Umgehungscode für die Aktivierungssperre generieren, der auf dem Aktivierungsserver von Apple gespeichert wird.

> [!TIP]
> Im überwachten Modus für iOS-Geräte können Sie mit dem Apple Configurator ein Gerät sperren, um die Funktionen auf bestimmte geschäftliche Zwecke zu beschränken. Der überwachte Modus ist in der Regel nur für firmeneigene Geräte vorgesehen.

Sie können [hier](https://support.apple.com/en-us/HT201365)mehr zur Aktivierungssperre erfahren.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Unterstützung von Intune beim Verwalten der Aktivierungssperre
Intune kann den Status der Aktivierungssperre von überwachten Geräten anfordern, die iOS 8.0 und höher ausführen. Ausschließlich für überwachte Geräte kann Intune den Umgehungscode der Aktivierungssperre abrufen und ihn direkt auf das Gerät anwenden. Wenn das Gerät zurückgesetzt wurde, können Sie direkt auf das Gerät zugreifen, indem Sie einen leeren Benutzernamen und den Code als Kennwort verwenden.

**Folgende Geschäftsvorteile ergeben sich**:

-   Der Benutzer erhält die Sicherheitsvorteile der App „Mein iPhone suchen“.

-   Sie können es den Benutzern ermöglichen, ihre Arbeit zu erledigen, in dem Wissen, dass Sie das Gerät außer Kraft setzen oder entsperren können, wenn es einem neuen Zweck zugewiesen werden soll.

## <a name="before-you-start"></a>Vorbereitung

Bevor Sie die Aktivierungssperre auf Geräten umgehen können, müssen Sie sie zuerst aktivieren. Dazu gehen Sie folgendermaßen vor:

1. Nutzen Sie die Informationen im Thema [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune).
2. Setzen Sie auf der Einstellungsseite im Abschnitt **Registrierung** die Einstellung **Aktivierungssperre zulassen, wenn sich das Gerät im überwachten Modus befindet** auf **Ja**.
3. Speichern Sie die Richtlinie und stellen Sie sie für die Geräte bereit, auf denen Sie die Umgehung der Aktivierungssperre verwalten möchten.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Verwenden der Umgehung der Aktivierungssperre über die Intune-Verwaltungskonsole
> [!IMPORTANT]
> Nachdem die Aktivierungssperre auf einem Gerät umgangen wurde, wird automatisch eine neue Aktivierungssperre angewendet, wenn die App „Mein iPhone suchen“ geöffnet wird. Aus diesem Grund **muss das Gerät physisch verfügbar sein, bevor Sie dieses Verfahren ausführen**.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Gruppen** &gt; **Alle Geräte** &gt; **Alle unternehmenseigenen Geräte** aus.

2.  Wählen Sie das Gerät aus, dessen Aktivierungssperre Sie umgehen möchten. Wählen Sie **Aktivierungssperre umgehen** aus.

3.  Lesen Sie die Warnmeldung. Klicken Sie auf **Ja**, um den Vorgang fortzusetzen.

Sie können den Status der Entsperranforderung auf der Detailseite für das Gerät überprüfen.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>Ermitteln der Geräte mit Aktivierungssperre
Es gibt zwei Möglichkeiten zur Ermittlung, welche Geräte die Aktivierungssperre verwenden:

-   Führen Sie die **Bestandsberichte zu mobilen Geräten**aus. In diesem Bericht werden die Spalten **Status der Aktivierungssperre** und **Überwacht** angezeigt, um den Status der Geräte anzugeben. Die Werte für **Überwacht** sind **Ja** oder **Nein**, und die Werte für **Status der Aktivierungssperre** lauten:

    -   Aktiviert mit Umgehungscode

    -   Aktiviert ohne Umgehungscode (Gerät wird nicht überwacht)

    -   Aktiviert ohne Umgehungscode (Gerät ist nicht erreichbar)

    -   Nicht aktiviert

    Das Feld **Status der Aktivierungssperre** ist für Geräte leer, auf denen nicht iOS 8.0 oder höher ausgeführt wird.

-   Wählen Sie ein Gerät in einer Gruppenansicht aus, um den Status der Aktivierungssperre im Gerätedetailbereich anzuzeigen.

    Wenn Sie ein Gerät im Knoten **Alle unternehmenseigenen Geräte** auswählen und die Aktivierungssperre für das Gerät aktiviert ist, dann wird auch der Umgehungscode angezeigt. Dieser Code kann dazu verwendet werden, um die Umgehung einer Aktivierungssperre manuell auszuführen.

    > [!IMPORTANT]
    >Intune erfasst alle sieben Tage den Status der Aktivierungssperre auf Geräten. Aus diesem Grund werden Geräte in der Intune-Konsole möglicherweise nicht sofort mit dem richtigen Status der Aktivierungssperre angezeigt.


### <a name="see-also"></a>Siehe auch
[Abkoppeln von Geräten](retire-devices-from-microsoft-intune-management.md)
[Geräteschutz durch Remotesperre und Zurücksetzen der Kennung](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)
