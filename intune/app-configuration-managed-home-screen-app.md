---
title: Konfigurieren der Managed Home Screen-App von Microsoft
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Managed Home Screen-App von Microsoft konfigurieren können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/01/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b17ab1fb385bb1079a834f0a6fa690223ab64163
ms.sourcegitcommit: 01117021dfaebb5507aa146b7369447c3d5a403d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65626502"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Konfigurieren der Managed Home Screen-App von Microsoft für Android Enterprise

Managed Home Screen ist die App, die für unternehmenseigene dedizierte Android Enterprise-Geräte verwendet wird, die über Intune registriert wurden und im Modus „Multi-App-Kiosk“ ausgeführt werden. Bei diesen Geräten fungiert die Managed Home Screen-App als Startprogramm für andere genehmigte Apps, die darauf ausgeführt werden. Die Managed Home Screen-App bietet IT-Administratoren die Möglichkeit, ihre Geräte anzupassen und die Funktionen einzuschränken, auf die der Endbenutzer zugreifen kann. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Wann die Managed Home Screen-App von Microsoft konfiguriert werden sollte

Wenn Ihnen Einstellungen über „Gerätekonfiguration“ zur Verfügung stehen, konfigurieren Sie die Einstellungen normalerweise dort. Auf diese Weise können Sie Zeit sparen, Fehler minimieren und erhalten eine bessere Benutzeroberfläche für Intune-Support. Allerdings stehen einige der Einstellungen für Managed Home Screen derzeit nur über das Blatt **App-Konfigurationsrichtlinien** in der Intune-Konsole zur Verfügung. Anhand dieses Dokuments lernen Sie, wie Sie die verschiedenen Einstellungen entweder mithilfe des Konfigurations-Designers oder eines JSON-Skripts konfigurieren. 

> [!NOTE]
> Es ist derzeit möglich und ratsam, Anwendungen für die Whitelist und angeheftete Weblinks über **Client-Apps** und **Gerätekonfiguration** festzulegen. Die vollständige Liste von Einstellungen, die in **Gerätekonfiguration** zur Verfügung stehen und sich auf Managed Home Screen auswirken, finden Sie unter [Einstellungen dedizierter Geräte](device-restrictions-android-for-work.md#dedicated-device-settings).  

Navigieren Sie zuerst zur Intune-Konsole im Azure-Portal, und wechseln Sie zu **Client-Apps** > **App-Konfigurationsrichtlinien**. Fügen Sie eine Konfigurationsrichtlinie für **Verwaltete Geräte** unter **Android** hinzu, und wählen Sie **Managed Home Screen** als zugeordnete App aus. Klicken Sie auf **Konfigurationseinstellungen**, um die verschiedenen verfügbaren Einstellungen für Managed Home Screen zu konfigurieren. 

## <a name="choosing-a-configuration-settings-format"></a>Auswählen eines Formats für die Konfigurationseinstellungen

Es gibt zwei Methoden, mit denen Sie Konfigurationseinstellungen für Managed Home Screen definieren können:

- **Konfigurations-Designer** ermöglicht Ihnen das Konfigurieren von Einstellungen über eine benutzerfreundliche Oberfläche, auf der Sie Features aktivieren oder deaktivieren und Werte festlegen können. Bei dieser Methode gibt es einige deaktivierte Konfigurationsschlüssel mit dem Werttyp `BundleArray`. Diese Konfigurationsschlüssel können nur durch Eingabe von JSON-Daten konfiguriert werden. 
- **JSON-Daten** ermöglicht Ihnen das Definieren aller möglichen Konfigurationsschlüssel mithilfe eines JSON-Skripts. 

Wenn Sie Eigenschaften mit Konfigurations-Designer hinzufügen, können Sie diese Eigenschaften automatisch in JSON konvertieren, indem Sie in der Dropdownliste **Format der Konfigurationseinstellungen** den Eintrag **JSON-Daten eingeben** auswählen.

![Screenshot der Optionen für „Format der Konfigurationseinstellungen“](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Verwenden von Konfigurations-Designer

Mithilfe von Konfigurations-Designer können Sie vorgegebene Einstellungen und die ihnen zugeordneten Werte auswählen. 

![Screenshot von hinzugefügten Konfigurationseinstellungen](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

In der nachstehenden Tabelle sind die verfügbaren Konfigurationsschlüssel, Werttypen, Standardwerte und Beschreibungen für Managed Home Screen aufgeführt. Die Beschreibung enthält das erwartete Geräteverhalten basierend auf den ausgewählten Werten. Konfigurationsschlüssel, die im Konfigurations-Designer deaktiviert sind, werden in der Tabelle nicht aufgeführt.

| Konfigurationsschlüssel | Werttyp | Standardwert | Beschreibung |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Rastergröße einstellen | string | Automatisch | Ermöglicht es Ihnen, die Rastergröße für Apps festzulegen, die auf Managed Home Screen positioniert werden sollen. Sie können die Anzahl der App -Zeilen und -Spalten festlegen, um die Rastergröße im Format `rows;column` festzulegen. Wenn Sie die Rastergröße definieren, wäre die maximale Anzahl der Apps, die in einer Zeile auf dem Startbildschirm angezeigt werden, die Anzahl der von Ihnen festgelegten Zeilen, und die maximale Anzahl der Apps, die in einer Spalte auf dem Startbildschirm angezeigt werden, wäre die Anzahl der festgelegten Spalten. |
| Bildschirmheader aktivieren | bool | TRUE | Aktiviert den Header für verschiedene Ansichten, die Managed Home Screen bietet, z.B. der Feed oder Feedkarten. Wenn Sie diese Einstellung aktivieren, wird den Gerätebenutzern der Header angezeigt. |
| Gerätestatusleiste aktivieren | bool | TRUE | Aktiviert die Statusleiste auf dem Startbildschirm (obere Leiste, in der aktuelle Verbindungen wie WLAN usw. angezeigt werden). Wenn Sie diesen Konfigurationsschlüssel aktivieren, kann der Endbenutzer die auf den Statusleisten angezeigten Symbole zur Darstellung von Verbindungen und aktiven Apps sehen. |
| Infobadge aktivieren | bool | FALSE | Aktiviert den Infobadge für App-Symbole. Er zeigt die Anzahl der neuen Benachrichtigungen auf der App an. Wenn Sie diese Einstellung aktivieren, sehen Endbenutzer die Infobadges auf Apps, in denen es ungelesene Benachrichtigungen gibt. Wenn Sie diesen Konfigurationsschlüssel deaktiviert lassen, kann der Endbenutzer keine Infobadges auf Apps sehen, die möglicherweise ungelesene Benachrichtigungen enthalten. |
| Startbildschirm sperren | bool | TRUE | Hindert den Endbenutzer daran, App-Symbole auf dem Startbildschirm zu verschieben. Wenn Sie diesen Konfigurationsschlüssel aktivieren, werden die App-Symbole auf dem Startbildschirm gesperrt, und der Endbenutzer kann sie nicht an verschiedene Rasterpositionen des Bildschirms ziehen und dort ablegen. Wenn `false` festgelegt wurde, können Endbenutzer Anwendungs- und Weblinksymbole auf Managed Home Screen verschieben.  |
| Hintergrundbild für Gerät festlegen | string | Standard | Ermöglicht es Ihnen, ein Hintergrundbild Ihrer Wahl festzulegen, indem Sie die URL des Bilds eingeben, das Ihr Hintergrundbild werden soll. |
| App-Symbolgröße festlegen | integer | 2 | Ermöglicht es Ihnen, die Symbolgröße für Apps festzulegen, die auf dem Startbildschirm angezeigt werden. Sie können folgende Werte in dieser Konfiguration für unterschiedliche Größen auswählen: „0“ (Kleinste), „1“ (Klein), „2“ (Normal), „3“ (Groß) und „4“ (Größte). |
| Symbol für App-Ordner festlegen | integer | 0 | Ermöglicht es Ihnen, die Darstellung von App-Ordnern auf dem Startbildschirm zu definieren. Sie können die Darstellung aus folgenden Werten auswählen: „Dunkel Quadrat(0)“; „Dunkel Kreis (1)“; „Hell Quadrat(2)“; „Hell Kreis (3)“. |
| Gesten aktivieren | bool | FALSE | Ermöglicht es dem Endbenutzer, Aktionen verschiedene Gesten wie „Nach oben wischen“ und „Nach unten wischen“ zuzuweisen. Wenn Sie diesen Konfigurationsschlüssel deaktivieren, können Endbenutzer nur nach rechts wischen, wenn es eine zweite Seite gibt, und dann zur Startseite zurückkehren. |
| Vertikales Scrollen aktivieren | bool | FALSE | Ermöglicht vertikales Scrollen auf Managed Home Screen. Wenn Sie diesen Konfigurationsschlüssel aktivieren, kann der Endbenutzer nur durch vertikales (und nicht durch horizontales) Wischen zu verschiedenen Seiten navigieren. |
| Design für Startbildschirm festlegen | string | Theme.Light.Blue | Ermöglicht es Ihnen, das Design für den Startbildschirm aus einer vordefinierten Gruppe von Designs mit verschiedenen Farben auszuwählen. Sie können diese Designs auswählen, indem Sie den Zeichenfolgenwert im folgenden Format eingeben:   Theme.Light.Green. Darin kann „Hell“ durch „Dunkel“ für ein dunkles Design und ersetzt werden und „Grün“ durch „Blau“, „Gelb“, „Rosa“, „Rot“, „Orange“ und „Lila“. |
| Dock aktivieren | bool | FALSE | Aktiviert den Dock-Abschnitt für Apps unten auf dem Startbildschirm, in dem persistente Apps und der Einstiegspunkt für alle installierten Apps angezeigt werden. Wenn Sie diesen Konfigurationsschlüssel aktivieren, kann der Endbenutzer auf Apps im Dock und außerdem auf den Abschnitt „Alle Apps“ zugreifen, um zur Liste aller installierten Apps auf den Geräten zu wechseln – unabhängig davon, ob sie in der Whitelist enthalten sind oder nicht. |
| Bildschirmausrichtung festlegen | integer | 1 | Ermöglicht es Ihnen, die Ausrichtung des Startbildschirms auf „Hochformat“, „Querformat“ oder „Automatisch drehen“ festzulegen. Sie können die Ausrichtung festlegen, indem Sie die Werte „1“ (für „Hochformat“), „2“ (für „Querformat“) oder „3“ (für „Automatisch drehen“) eingeben. |
| Feed für Startbildschirm aktivieren | bool | FALSE | Aktiviert den Feed des Startbildschirms, der durch Wischen nach links angezeigt werden kann. Dieser Feed zeigt eine andere Art von Inhalten an, z.B. News, Kalender, häufig verwendete Apps, die Karte des Sprach-Assistenten Cortana usw. Wenn Sie dies aktivieren, kann der Endbenutzer zum Feed navigieren, indem er auf dem Startbildschirm nach links wischt. |
| Übersichtsmodus aktivieren | bool | FALSE | Ermöglicht es Endbenutzern, auf dem Startbildschirm verschiedene Seiten hinzuzufügen oder davon zu entfernen, auf die durch Wischen nach rechts auf dem Standardbildschirm zugegriffen werden kann. Wenn Sie dies aktivieren, kann der Endbenutzer rechts neben der Standardseite des Startbildschirms Seiten hinzufügen, die Standardseite ändern und auf die Einstellungen von Managed Home Screen zugreifen. |
| Gerätetelemetrie aktivieren | bool | FALSE | Ermöglicht es, dass die gesamte Telemetrie für Managed Home Screen erfasst wird. Wenn Sie dies aktivieren, kann Microsoft die Nutzungstelemetriedaten des Geräts erfassen, z.B., wie oft eine bestimmte App auf dem jeweiligen Gerät gestartet wurde. |
| Anwendungen für die Whitelist festlegen | bundleArray | FALSE | Ermöglicht es Ihnen, aus den auf dem Gerät installierten Apps diejenige Gruppe von Apps zu definieren, die auf dem Startbildschirm sichtbar sein soll. Sie können die Apps definieren, indem Sie den App-Paketnamen der Apps eingeben, die Sie sichtbar machen möchten. So würden Sie Einstellungen beispielsweise mit „com.android.settings“ auf dem Startbildschirm sichtbar machen. Die Apps, die Sie der Whitelist in diesem Abschnitt hinzufügen, sollten bereits auf dem Gerät installiert sein, damit sie auf dem Startbildschirm sichtbar sind. |
| Angeheftete Weblinks festlegen | bundleArray | FALSE | Ermöglicht es Ihnen, Websites als Schnellstartsymbole auf dem Startbildschirm anzuheften. Bei dieser Konfiguration können Sie die URL definieren und auf dem Startbildschirm hinzufügen, damit sie der Endbenutzer mit einem einfachen Tippen im Browser starten kann. |
| Suchleiste aktivieren | bool | FALSE | Aktiviert die Suchleiste auf dem Startbildschirm. Wenn Sie dies aktivieren, wird Benutzern des Gerät die Suchleiste auf dem Startbildschirm angezeigt. Darin können sie alles das eingeben, was sie im Web suchen möchten. |
| App „Einstellungen“ deaktivieren | bool | FALSE | Deaktiviert die Seite „Einstellungen“ für Managed Home Screen. Wenn Sie dies deaktivieren, kann der Endbenutzer des Geräts nicht auf die Einstellungen von Managed Home Screen zugreifen. |
| Bildschirmschoner aktivieren | bool | FALSE | Dient zum Aktivieren (oder Nichtaktivieren) des Bildschirmschonermodus. Wenn „true“ festgelegt wird, können Sie **screen_saver_image**, **screen_saver_show_time**,**inactive_time_to_show_screen_saver** und **media_detect_screen_saver** konfigurieren. |
| Bild für Bildschirmschoner | string |   | Legen Sie die URL für das Bildschirmschonerbild fest. Wurde keine URL festgelegt, zeigen Geräte den Standardbildschirm an, wenn der Bildschirmschoner aktiviert wird.  |
| Anzeigezeit für den Bildschirmschoner | integer | 0 | Bietet die Möglichkeit, die Zeitspanne in Sekunden festzulegen, während der das Gerät den Bildschirmschoner im Bildschirmschonermodus anzeigt. Wenn „0“ festgelegt wurde, wird der Bildschirmschoner so lange im Bildschirmschonermodus angezeigt, bis das Gerät inaktiv wird.  |
| Inaktive Zeit zum Aktivieren des Bildschirmschoners | integer | 30 | Die Anzahl von Sekunden, während der das Gerät inaktiv ist, bevor der Bildschirmschoner ausgelöst wird. Wenn „0“ festgelegt wurde, wechselt das Gerät niemals in den Bildschirmschonermodus. |
| Medienerkennung vor Anzeige des Bildschirmschoners | bool | TRUE | Wählen Sie aus, ob auf dem Gerätebildschirm der Bildschirmschoner angezeigt werden soll, wenn auf dem Gerät Audio/Video wiedergegeben wird. Wenn „true“ festgelegt wurde, gibt das Gerät – unabhängig vom Wert in **inactive_time_to_show_scree_saver** – kein Audio/Video wieder. Wenn „false“ festgelegt wurde, zeigt der Gerätebildschirm den Bildschirmschoner entsprechend dem Wert an, der in **inactive_time_to_show_screen_saver** festgelegt wurde.   |
| Virtuelle Startschaltfläche aktivieren | bool | FALSE | Legen Sie diese Einstellung auf `True` fest, damit der Endbenutzer auf eine Startschaltfläche für Managed Home Screen zugreifen kann, über die er aus seiner aktuellen Aufgabe zu Managed Home Screen zurückkehren wird.  |
| Typ der virtuellen Startschaltfläche | string | Swipe_up | Verwenden Sie **swipe_up** für den Zugriff auf die Startschaltfläche mit einem Wischen nach oben. Verwenden Sie **float** für den Zugriff auf eine angeheftete persistente Startschaltfläche, die der Endbenutzer auf dem Bildschirm verschieben kann. |
| Anzeigeleiste für Akku- und Signalstärke | bool | True  | Wenn Sie diese Einstellung auf `True` festlegen, wird die Anzeigeleiste für Akku- und Signalstärke eingeblendet. |
| Kennwort für Aufgabensperrmodus beenden | string |   | Geben Sie einen 4- bis 6-stelligen Code ein, der für die vorübergehende Aufhebung des Aufgabensperrmodus zur Problembehandlung verwendet werden soll. |
| WLAN-Einstellung anzeigen | bool | FALSE | Wenn Sie diese Einstellung auf `True` festlegen, kann der Endbenutzer WLAN aktivieren oder deaktivieren oder aber eine Verbindung mit verschiedenen WLAN-Netzwerken herstellen.  |
| Bluetooth-Einstellung anzeigen | bool | FALSE | Wenn Sie diese Einstellung auf `True` festlegen, kann der Endbenutzer Bluetooth aktivieren oder deaktivieren und eine Verbindung mit verschiedenen Bluetooth-fähigen Geräten herstellen.   |

## <a name="enter-json-data"></a>Eingeben von JSON-Daten

Geben Sie JSON-Daten ein, um alle verfügbaren Einstellungen für Managed Home Screen sowie die in **Konfigurations-Designer** deaktivierten Einstellungen zu konfigurieren.

![Screenshot der hinzugefügten JSON-Daten](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Zusätzlich zur Liste von konfigurierbaren Einstellungen, die in der Tabelle **Konfigurations-Designer** (siehe oben) aufgeführt sind, enthält die nachstehende Tabelle die Konfigurationsschlüssel, die Sie nur über JSON-Daten konfigurieren können.

|    Konfigurationsschlüssel    |    Werttyp    |    Standardwert    |    Beschreibung    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Anwendungen für die Whitelist festlegen    |    bundleArray    | ``` json   {        "key":   "applications",        "valueBundleArray": [        {                                    "managedProperty": [   {         "key": "package",         "valueString":   STRING_VALUE   }   ]        }        ]   },   ``` |    Ermöglicht es Ihnen, aus den auf dem Gerät installierten Apps diejenige Gruppe von Apps zu definieren, die auf dem Startbildschirm sichtbar sein soll. Sie können die Apps definieren, indem Sie den App-Paketnamen der Apps eingeben, die Sie sichtbar machen möchten. So würden Sie Einstellungen beispielsweise mit „com.android.settings“ auf dem Startbildschirm sichtbar machen. Die Apps, die Sie der Whitelist in diesem Abschnitt hinzufügen, sollten bereits auf dem Gerät installiert sein, damit sie auf dem Startbildschirm sichtbar sind.    |
|    Angeheftete Weblinks festlegen    |    bundleArray    | ``` json   {        "key": "weblinks",        "valueBundleArray": [         {               "managedProperty": [     {          "key": "link",          "valueString":   STRING_VALUE      },      {           "key": "label",           "valueString": STRING_VALUE      }      ]         }         ]   },   ``` |    Ermöglicht es Ihnen, Websites als Schnellstartsymbole auf dem Startbildschirm anzuheften. Bei dieser Konfiguration können Sie die URL definieren und auf dem Startbildschirm hinzufügen, damit sie der Endbenutzer mit einem einfachen Tippen im Browser starten kann.    |
|    Verwalteten Ordner zum Gruppieren von Apps erstellen    |    bundleArray    | ``` json   {        "key": “managed_folders",        "valueBundleArray": [         {               "managedProperty": [     {            "key": "folder_name",            "valueString": STRING_VALUE      },      {             "key": "content",                      "valueBundleArray":   [                        {                             "managedProperty": [                    {                              “key”: “type”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “label”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “package”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “class”,                             “valueString”: STRING_VALUE                    },                    {                              “key”: “link”,                             “valueString”: STRING_VALUE                    }                 ]              }          ]      }              ]          }      ]   },   ``` |    Ermöglicht es Ihnen, Ordner zu erstellen und zu benennen sowie Apps in diesen Ordnern zu gruppieren. Endbenutzer können Ordner nicht verschieben, sie umbenennen oder die Apps innerhalb der Ordner verschieben.   Ordner werden in der Reihenfolge ihrer Erstellung und die Apps in den Ordnern in alphabetischer Reihenfolge angezeigt.         Hinweis: Alle Apps, die Sie in Ordnern gruppieren möchten, müssen dem Gerät nach Bedarf zugewiesen werden und vorher Managed Home Screen hinzugefügt worden sein.     |

Dies ist ein Beispiel für ein JSON-Skript, in dem alle verfügbaren Konfigurationsschlüssel enthalten sind:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "grid_size",
            "valueString": "Auto"
        },
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}

```
## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu dedizierten Android Enterprise-Geräten finden Sie unter [Einrichten der Intune-Registrierung für dedizierte Android Enterprise-Geräte](android-kiosk-enroll.md).
