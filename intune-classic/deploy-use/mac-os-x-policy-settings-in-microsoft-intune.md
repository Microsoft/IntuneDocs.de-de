---
title: Mac OS X-Richtlinieneinstellungen
description: Intune bietet eine Reihe integrierter allgemeiner Einstellungen, die Sie auf Mac OS X-Geräten konfigurieren können. Darüber hinaus können Sie das Apple Configurator-Tool verwenden, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: afc5e32cd2db5755ad6fb570aabae27c4d23e827
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Einstellungen für Mac OS X-Konfigurationsrichtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune bietet eine Reihe integrierter allgemeiner Einstellungen, die Sie auf Mac OS X-Geräten konfigurieren können. Darüber hinaus können Sie das Apple Configurator-Tool verwenden, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind.

## <a name="general-configuration-policy-settings"></a>Allgemeine Konfigurationsrichtlinieneinstellungen

Verwenden Sie die allgemeine **Mac OS X-Konfigurationsrichtlinie** von Microsoft Intune zum Konfigurieren von Einstellungen für:

-   **Sicherheitseinstellungen für Geräte**: Wählen Sie aus einer Liste mit vordefinierten Einstellungen, mit denen Sie verschiedene Features und Funktionen auf dem Gerät steuern können.

-   **Kompatible und nicht kompatible Apps**: Geben Sie eine Liste von Apps an, die in Ihrem Unternehmen kompatibel oder nicht kompatibel sind. Mit dem Bericht über nicht kompatible Apps können Sie überprüfen, ob die von Benutzern installierten Apps zu den von Ihnen in der Liste als kompatibel angegebenen Apps gehören (die Installation der App kann jedoch nicht blockiert werden).

Wenn die gesuchte Einstellung nicht in dieser Liste enthalten ist, können Sie sie ggf. mithilfe einer benutzerdefinierten Mac OS X-Richtlinie erstellen, die Ihnen das Importieren von Einstellungen erlaubt, die Sie mit dem Apple Configurator-Tool erstellt haben. Weitere Informationen finden Sie weiter unten in diesem Thema unter „Benutzerdefinierte Richtlinieneinstellungen“.

### <a name="password-settings"></a>Kennworteinstellungen

|Name der Einstellung|Details|
|----------------|---------------|
|**Anfordern eines Kennworts zum Entsperren von Geräten**|Gibt an, ob für den Zugriff auf einen Mac-Computer ein Kennwort verwendet werden muss. **Wichtig:** Im Gegensatz zu iOS-Geräten wird der Benutzer bei Mac OS X-Geräten nicht umgehend zum Aktualisieren seines Kennworts aufgefordert, um dieser Einstellung zu entsprechen.|
|**Erforderlicher Kennworttyp**|Gibt an, ob das Kennwort rein **Numerisch** sein darf oder ob es **Alphanumerisch** sein muss (also Buchstaben und Zahlen enthalten muss). **Wichtig:** Diese Einstellung wird lediglich unter Mac OS X 10.10.3 und höher unterstützt.|
|**Erforderliche Anzahl komplexer Zeichen im Kennwort**|Gibt die Anzahl komplexer Zeichen an, die das Kennwort enthalten muss (**0** bis **4**).<br /><br />Bei komplexen Zeichen handelt es sich um Symbole (z. B. ein Fragezeichen **?**).|
|**Minimale Kennwortlänge**|Gibt die Mindestlänge für das Kennwort an (**4** bis **14** Zeichen).|
|**Einfache Kennwörter zulassen**|Ermöglicht die Verwendung einfacher Kennwörter (z. B.**0000**oder**1234**).|
|**Minuten Inaktivität vor Anforderung des Kennworts**|Gibt an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.|
|**Kennwortablauf (Tage)**|Gibt an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).|
|**Kennwortverlauf speichern**|Verhindert, dass der Benutzer ein bereits verwendetes Kennwort erneut verwendet. Bei Auswahl dieser Einstellung kann auch **Wiederverwendung vorheriger Kennwörter verhindern** festgelegt werden, um die Anzahl von vorherigen Kennwörtern anzugeben, die nicht erneut verwendet werden dürfen (**1** bis **24**).|
|**Minuten Inaktivität bis zur Aktivierung des Bildschirmschoners**|Gibt an, wie lange sich der Computer im Leerlauf befinden muss, bevor der Bildschirmschoner aktiviert wird.|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Einstellungen für kompatible und nicht kompatible Anwendungen
Aktivieren Sie in der Liste der **kompatiblen und nicht kompatiblen Apps für Mac OS X** die Einstellung **Verwaltete Einstellungen für Geräte**, und geben Sie anhand der folgenden Informationen eine Liste kompatibler oder nicht kompatibler Apps an.

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste kompatibler Apps oder eine Liste nicht kompatibler Apps enthalten. Sie können nicht beide Typen in derselben Richtlinie angeben.
>
> Intune ermöglicht das Erstellen eines Berichts mit Geräten, auf denen nicht kompatible Apps installiert sind. Die Installation nicht kompatibler Apps wird weder verhindert, noch werden sie entfernt.

|                                    Name der Einstellung                                    |                                                                                                                                                                                                                                                                                                                                                     Details                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <strong>Nichtkompatibilität melden, wenn Benutzer die aufgelisteten Apps installieren</strong>      |                                                                                                                                                                                                                                                                    Zeigt die Mac OS X-Apps an, die Benutzer nicht installieren dürfen. Wenn Benutzer eine dieser Apps installieren, werden sie in den <strong>Berichten über nicht kompatible Apps</strong> aufgeführt.                                                                                                                                                                                                                                                                    |
| <strong>Nichtkonformität melden, wenn Benutzer die nicht aufgelisteten Apps installieren</strong> |                                                                                                                                                                                                                                                                       Zeigt die Mac OS X-Apps an, die Benutzer installieren dürfen. Wenn Benutzer andere Apps installieren, werden diese in den <strong>Berichten über nicht kompatible Apps</strong> aufgeführt.                                                                                                                                                                                                                                                                        |
|                                <strong>Hinzufügen</strong>                                | Fügt der ausgewählten Liste eine App hinzu. Geben Sie einen Namen Ihrer Wahl, optional den Herausgeber der App sowie die Paket-ID der App an. <strong>Tipp:</strong> Zum Ermitteln der Paket-ID einer App führen Sie auf einem Mac-Computer, auf dem die App installiert ist, die folgenden Schritte aus:<ol><li>Öffnen Sie den Ordner, in dem die App installiert ist (z. B. <strong>/Programme</strong>).</li><li>Wählen Sie das Paket <em>&lt;App-Name&gt;</em><strong>.app</strong> und anschließend <strong>Paketinhalt anzeigen</strong> aus.</li><li>Öffnen Sie die Datei <strong>Info.plist</strong>.</li><li>Überprüfen Sie den Wert, der dem Schlüssel <strong>CFBundleIdentifier</strong> zugewiesen ist.</li></ol>Die Paket-ID weist das Format <strong>com.contoso.appname</strong> auf. |
|                            <strong>Anwendungen importieren</strong>                            |                                                                                                                                                                                                                                                                                Importiert eine Liste von Apps, die Sie in einer durch Trennzeichen getrennten Datei angegeben haben. Verwenden Sie in der Datei das Format App-Name, Herausgeber, Paket-ID der App.                                                                                                                                                                                                                                                                                 |
|                               <strong>Bearbeiten</strong>                                |                                                                                                                                                                                                                                                                                                                         Ermöglicht das Bearbeiten der Werte für Name, Herausgeber und Paket-ID der ausgewählten App.                                                                                                                                                                                                                                                                                                                         |
|                              <strong>Löschen</strong>                               |                                                                                                                                                                                                                                                                                                                                      Löscht die ausgewählte App aus der Liste.                                                                                                                                                                                                                                                                                                                                      |

> [!TIP]
> Weitere Informationen zu Intune-Berichten finden Sie unter [Einblicke in Microsoft Intune-Vorgänge durch Berichte](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Wenn sich ein Mac OS X-Gerät im Energiesparmodus befindet, können keine Richtlinien oder Profile bereitgestellt oder inventarisiert werden. Infolgedessen zeigt die Intune-Konsole möglicherweise vorübergehend den Status **Richtlinieneinstellungen mit Fehlern** an, bis das Gerät wieder aus dem Energiesparmodus aktiviert wird.

### <a name="monitor-compliant-and-noncompliant-apps"></a>Überwachen konformer und nicht konformer Apps
Anhand der **Berichte über nicht kompatible Apps** können Sie überprüfen, ob die angegebenen Apps kompatibel sind.

#### <a name="to-run-a-report"></a>So führen Sie einen Bericht aus

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Berichte** &gt; **Berichte über nicht richtlinienkonforme Apps** aus.

2.  Wählen Sie die Gerätegruppen aus, die Sie überprüfen möchten, geben Sie an, ob Sie nach kompatiblen und/oder nicht kompatiblen Apps suchen möchten, und wählen Sie dann **Bericht anzeigen** aus.

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Benutzerdefinierte Mac OS X-Richtlinieneinstellungen in Microsoft Intune
Verwenden Sie die **benutzerdefinierte Mac OS X-Konfigurationsrichtlinie** von Microsoft Intune, um auf Mac OS X-Geräten Einstellungen bereitzustellen, die Sie mit dem [Apple Configurator-Tool](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) erstellt haben. Mit diesem Tool können Sie zahlreiche Einstellungen zur Betriebssteuerung dieser Geräte erstellen und in ein Konfigurationsprofil exportieren. Sie können dieses Konfigurationsprofil anschließend in eine benutzerdefinierte Intune-Richtlinie für Mac OS X importieren und die Einstellungen für Benutzer und Geräte in Ihrer Organisation bereitstellen.

Mit dieser Funktion können Sie Mac OS X-Einstellungen bereitstellen, die nicht mit der allgemeinen Mac OS X-Konfigurationsrichtlinie von Intune konfigurierbar sind.

### <a name="prerequisites"></a>Voraussetzungen
Bevor Sie beginnen, müssen Sie Apple Configurator installiert und eine Konfigurationsdatei mit den Einstellungen erstellt haben, die Sie für Benutzer oder Geräte bereitstellen möchten. Um Apple Configurator herunterzuladen und mehr darüber zu erfahren, besuchen Sie den [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune gibt keine Auskunft über die Konformität der einzelnen Einstellungen einer benutzerdefinierten Mac OS X-Richtlinie. Die Gesamtkompatibilität der Richtlinie wird jedoch angegeben.

### <a name="general-settings"></a>Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Name**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte Mac OS X-Richtlinie ein, damit Sie sie leichter in der Intune-Konsole identifizieren können.|
    |**Beschreibung**|Geben Sie eine Beschreibung ein, die einen Überblick über die benutzerdefinierte Mac OS X-Richtlinie bietet, sowie weitere relevante Informationen, mit denen Sie danach suchen können.|


### <a name="custom-settings"></a>Benutzerdefinierte Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Name des benutzerdefinierten Konfigurationsprofils (wird Benutzern angezeigt)**|Geben Sie einen Namen für die Richtlinie an, der auf dem Gerät und in Intune-Richtlinienberichten angezeigt wird.|
    |**Konfigurationsprofildatei**|Wählen Sie **Importieren** aus, und suchen Sie dann das mit Apple Configurator erstellte Konfigurationsprofil. **Tipp:** Hilfe zum Erstellen des Konfigurationsprofils finden Sie in diesem Thema unter „Erstellen einer Konfigurationsprofildatei“.|
    |**Details zum Konfigurationsprofil**|Zeigt den XML-Code des importierten Konfigurationsprofils an.|



### <a name="how-to-create-a-configuration-profile-file"></a>Erstellen einer Konfigurationsprofildatei
Die Konfigurationsprofildatei, die von der benutzerdefinierten Richtlinie verwendet wird, kann auf zwei Weisen erstellt werden:

-   Exportieren Sie die Datei (mit der Erweiterung **.mobileconfig**) aus dem Apple Configurator-Tool.

-   Erstellen Sie die Datei selbst unter Verwendung des entsprechenden Schemas aus der [Apple Configuration Profile Key Reference](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
