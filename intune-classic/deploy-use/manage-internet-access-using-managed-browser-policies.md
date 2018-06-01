---
title: Verwalten des Webzugriffs mit dem Managed Browser
description: Stellen Sie die Managed Browser-Anwendung bereit, um das Browsen im Web und die Übertragung von Webdaten an andere Apps einzuschränken.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 05/10/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1722defcb29c9cd5a15c68e01114f4ffb80e3859
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2018
ms.locfileid: "34456366"
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Managed Browser ist eine Webbrowseranwendung, die Sie mit Microsoft Intune in Ihrer Organisation bereitstellen können. Mit einer Richtlinie für Managed Browser wird eine Zulassungs- oder Blockierungsliste konfiguriert, um die Websites einzuschränken, die Benutzer von Managed Browser besuchen können.

Da diese App die Integration mit dem Intune SDK aufweist, können Sie auch App-Schutzrichtlinien auf sie anwenden. Mithilfe dieser Richtlinien können beispielsweise Ausschneide-, Kopier- und Einfügevorgänge gesteuert und Bildschirmaufnahmen verhindert werden. Außerdem kann sichergestellt werden, dass Links zu Inhalten, die von Benutzern ausgewählt werden, nur in anderen verwalteten Apps geöffnet werden. Weitere Informationen finden Sie unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

>[!IMPORTANT]
>Die Managed Browser-App ruft nur dann Intune-App-Schutzrichtlinien ab und wendet diese an, wenn eine andere App auf dem Gerät eine App-Schutzrichtlinie abgerufen hat.<br><br> Wenn Benutzer zudem Managed Browser aus dem App Store installieren und die App nicht von Intune verwaltet wird, gilt Folgendes:<br /><br />
>**iOS**: Die Managed Browser-App kann als Basiswebbrowser verwendet werden, aber einige Features sind nicht verfügbar, und der Zugriff auf Daten anderer von Intune verwalteter Apps ist nicht möglich.<br />
**Android**: Die Managed Browser-App kann nicht verwendet werden.<br /><br />
Wenn Benutzer Managed Browser selbst auf einem iOS-Gerät mit einer Version vor iOS 9 installieren, wird er nicht durch die von Ihnen erstellten Richtlinien verwaltet. Um sicherzustellen, dass der Browser von Intune verwaltet wird, muss die App deinstalliert werden, bevor Sie sie als verwaltete Anwendung für Benutzer bereitstellen können. Wenn Benutzer unter iOS 9 und höher Managed Browser selbst installieren, werden sie aufgefordert, die Verwaltung des Browsers durch Richtlinien zuzulassen.

Sie können Richtlinien für verwaltete Browser für die folgenden Gerätetypen erstellen:

-   Geräte unter Android 4 und höher

-   Geräte unter iOS 8.0 und höher

Intune Managed Browser unterstützt das Öffnen von Webinhalten von [Microsoft Intune-Anwendungspartnern](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-policy"></a>Erstellen einer Richtlinie für Managed Browser

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Richtlinie** &gt; **Richtlinie hinzufügen** aus.

2.  Konfigurieren Sie einen der folgenden Richtlinientypen für **Software** :

    -   **Managed Browser (Android 4 und höher)**

    -   **Managed Browser (iOS 8.0 und höher)**

    Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien finden Sie im Thema [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Orientieren Sie sich bei der Konfiguration der Richtlinieneinstellungen für Managed Browser an folgenden Informationen:

    - **Name**. Geben Sie einen eindeutigen Namen für die Richtlinie für Managed Browser ein, damit Sie sie leichter in der Intune-Konsole identifizieren können.
    - **Beschreibung**. Geben Sie eine Beschreibung ein, die einen Überblick über die Richtlinie für Managed Browser bietet, sowie weitere relevante Informationen, mit denen Sie danach suchen können.
    - **Aktivieren Sie eine Zulassungs- oder Blockierungsliste, um die URLs einzuschränken, die mit Managed Browser geöffnet werden können**. Wählen Sie eine der folgenden Optionen aus:
        - **Nur das Öffnen der im Folgenden aufgelisteten URLs über Managed Browser erlauben**. Gibt eine Liste der URLs an, die von Managed Browser geöffnet werden dürfen.
        - **Öffnen der im Folgenden aufgelisteten URLs über Managed Browser blockieren**. Gibt eine Liste der URLs an, die von Managed Browser nicht geöffnet werden dürfen.
**Hinweis:** Eine Richtlinie für Managed Browser kann nicht sowohl zulässige als auch blockierte URLs enthalten.
Weitere Informationen zu den festlegbaren URL-Formaten finden Sie in diesem Thema unter **URL-Format für zulässige und blockierte URLs**.

4.  Wählen Sie danach die Option **Richtlinie speichern**.

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** des Arbeitsbereichs **Richtlinie** angezeigt.

## <a name="create-a-deployment-for-the-managed-browser-app"></a>Erstellen einer Bereitstellung für die Managed Browser-App
Nachdem Sie die Richtlinie für Managed Browser erstellt haben, können Sie eine Softwarebereitstellung für die Managed Browser-App erstellen und der von Ihnen erstellten Richtlinie für Managed Browser zuordnen.

> [!IMPORTANT]
> Richtlinien für Managed Browser werden nicht auf die gleiche Weise wie andere Intune-Richtlinien bereitgestellt. Diese Art von Richtlinie muss dem Softwarepaket für Managed Browser zugeordnet werden.

Wenn Sie die App bereitstellen, wählen Sie die Richtlinie für Managed Browser auf der Seite **Mobile App-Verwaltung** aus, um die App mit der Richtlinie zu verknüpfen.

Weitere Informationen zum Bereitstellen von Apps finden Sie unter [Bereitstellen von Apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Sicherheit und Datenschutz für Managed Browser

-   Auf iOS-Geräten können von Benutzern besuchte Websites, deren Zertifikat abgelaufen oder nicht vertrauenswürdig ist, nicht geöffnet werden.

-   Einstellungen, die Benutzer für den integrierten Browser auf ihren Geräten vornehmen, werden von Managed Browser nicht verwendet. Dies liegt daran, dass Managed Browser keinen Zugriff auf diese Einstellungen hat.

-   Wenn Sie die Option **Einfache PIN für den Zugriff erforderlich** oder **Unternehmensanmeldeinformationen für den Zugriff erforderlich** in einer Richtlinie für die Verwaltung mobiler Anwendungen konfigurieren, die Managed Browser zugeordnet ist, und ein Benutzer auf der Authentifizierungsseite den Hilfelink auswählt, kann er beliebige Websites besuchen. Dies gilt unabhängig davon, ob sie in der Richtlinie für Managed Browser einer Blockierungsliste hinzugefügt wurden.

-   Managed Browser kann den Zugriff auf Websites nur blockieren, wenn direkt darauf zugegriffen wird. Der Zugriff auf die Website kann nicht blockiert werden, wenn dafür Zwischendienste (z. B. ein Übersetzungsdienst) verwendet werden.

-   Um die Authentifizierung zuzulassen und sicherzustellen, dass auf die Intune-Dokumentation zugegriffen werden kann, ist **&#42;.microsoft.com** von den Zulassungs- oder Blockierungslisten ausgenommen. Es ist immer zulässig.

### <a name="turn-off-usage-data"></a>Deaktivieren von Nutzungsdaten
Microsoft sammelt automatisch anonyme Daten über die Leistung und die Verwendung von Managed Browser, um Microsoft-Produkte und -Dienste zu verbessern. Benutzer können die Erfassung von Daten mithilfe der Einstellung für **Nutzungsdaten** auf ihren Geräten deaktivieren. Sie haben keine Kontrolle über die Erfassung dieser Daten.

## <a name="reference-information"></a>Referenzinformationen

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-Format für zulässige und blockierte URLs
Nachfolgend wird erläutert, welche Formate und Platzhalter Sie zum Festlegen von URLs in den Zulassungs- und Blockierungslisten verwenden können:

- Sie können das Platzhaltersymbol (**&#42;**) gemäß den Regeln in der folgenden Liste mit zulässigen Mustern verwenden.

- Stellen Sie sicher, dass Sie bei der Eingabe in die Liste allen URLs **http** oder **https** voranstellen.

- Sie können Portnummern in der Adresse angeben. Wenn Sie keine Portnummer angeben, werden folgende Werte verwendet:

  -   Port 80 für http

  -   Port 443 für https

  Die Verwendung von Platzhaltern für die Portnummer wird nicht unterstützt. Zum Beispiel werden <strong>http&colon;//www&period;contoso&period;com:*;</strong> und <strong>http&colon;//www&period;contoso&period;com: /*;</strong> nicht unterstützt.

- In der folgenden Tabelle sind die zulässigen Muster aufgeführt, die Sie zum Festlegen von URLs verwenden können:

|                  URL                  |                     Details                      |                                                Treffer                                                |                                Stimmt nicht überein mit                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        http://www.contoso.com         |              Entspricht einer einzelnen Seite               |                                            <www.contoso.com>                                           |  host.contoso.com<br /><br /><www.contoso.com/images><br /><br />contoso.com/   |
|          http://contoso.com           |              Entspricht einer einzelnen Seite               |                                             contoso.com/                                              | host.contoso.com<br /><br /><www.contoso.com/images><br /><br /><www.contoso.com>  |
|    <http://www.contoso.com/&#42>;     | Entspricht allen URLs, die mit „www.contoso.com“ beginnen  |      <www.contoso.com> <br /><br /><www.contoso.com/images><br /><br />www.contoso.com/videos/tvshows      |              host.contoso.com<br /><br />host.contoso.com/images              |
|    http://&#42;.contoso.com/&#42;     |     Entspricht allen Unterdomänen unter „contoso.com“     | developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos |                               contoso.host.com                                |
|     http://www.contoso.com/images     |             Entspricht einem einzelnen Ordner              |                                        <www.contoso.com/images>                                         |                          <www.contoso.com/images/dogs>                          |
|       http://www.contoso.com:80       |  Entspricht einer einzelnen Seite mit einer Portnummer   |                                       http://www.contoso.com:80                                       |                                                                               |
|        https://www.contoso.com        |          Entspricht einer einzelnen, sicheren Seite           |                                        https://www.contoso.com                                        |                            http://www.contoso.com                             |
| <http://www.contoso.com/images/&#42>; |    Entspricht einem einzelnen Ordner und allen Unterordnern    |                 <www.contoso.com/images/dogs><br /><br /><www.contoso.com/images/cats>                   |                            <www.contoso.com/videos>                             |

- Im Folgenden Beispiele für Eingaben, die nicht unterstützt werden:

  - &#42;.com

  - &#42;.contoso/&#42;

  - <www.contoso.com/>&#42;images

  - <www.contoso.com/>&#42;images&#42;pigs

  - <www.contoso.com/page>&#42;

  - IP-Adressen

  - https://&#42;

  - http://&#42;

  - http://www.contoso.com:&#42;

  - http://www.contoso.com: /&#42;

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Lösen von Konflikten zwischen der Zulassungs- und Sperrliste
Wenn mehrere Richtlinien für Managed Browser für ein Gerät bereitgestellt werden und Einstellungen in Konflikt stehen, werden sowohl der Modus (zulassen oder blockieren) als auch die URL-Listen ausgewertet. Bei einem Konflikt gilt folgendes Verhalten:

-   Wenn die Modi in jeder Richtlinie identisch sind, aber die URL-Listen voneinander abweichen, werden die URLs auf dem Gerät nicht erzwungen.

-   Wenn die Modi in jeder Richtlinie voneinander abweichen, aber die URL-Listen identisch sind, werden die URLs auf dem Gerät nicht erzwungen.

-   Wenn ein Gerät erstmals Richtlinien für Managed Browser empfängt und zwei Richtlinien in Konflikt stehen, werden die URLs auf dem Gerät nicht erzwungen. Sie können die Konflikte über den Knoten **Richtlinienkonflikte** des Arbeitsbereichs **Richtlinie** anzeigen.

-   Wenn ein Gerät bereits ein Richtlinie für Managed Browser erhalten hat und eine zweite Richtlinie mit in Konflikt stehenden Einstellungen bereitgestellt wird, bleiben die ursprünglichen Einstellungen auf dem Gerät bestehen. Sie können die Konflikte über den Knoten **Richtlinienkonflikte** des Arbeitsbereichs **Richtlinie** anzeigen.
