---
title: Konfigurieren von Microsoft Launcher für Android Enterprise mit Intune
titleSuffix: ''
description: Verwenden Sie Intune-Konfigurationsrichtlinien mit Microsoft Launcher.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55f76b0c5c71f7828fed17233c2b81d6b066cc3b
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216107"
---
# <a name="configure-microsoft-launcher"></a>Konfigurieren von Microsoft Launcher

Microsoft Launcher ist eine Android-App, mit der Benutzer ihr Smartphone personalisieren, ihre Termine unterwegs organisieren und ihre Arbeit vom Smartphone auf ihren PC übertragen können. 

Auf vollständig verwalteten Android Enterprise-Geräten ermöglicht Launcher es den IT-Administratoren eines Unternehmens auch, die Startbildschirme verwalteter Geräte durch Auswahl von Hintergrundbildern, Apps und Symbolpositionen anzupassen. Damit kann das Erscheinungsbild aller verwalteten Android-Geräte über verschiedene OEM-Geräte- und Systemversionen hinweg standardisiert werden. 

## <a name="how-to-configure-the-microsoft-launcher-app"></a>Konfigurieren der Microsoft Launcher-App 

Navigieren Sie zum [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), und wählen Sie **Apps** > **App-Konfigurationsrichtlinien** aus. Fügen Sie eine Konfigurationsrichtlinie für **Verwaltete Geräte** unter **Android** hinzu, und wählen Sie **Microsoft Launcher** als zugeordnete App aus. Klicken Sie auf **Konfigurationseinstellungen**, um die verschiedenen verfügbaren Einstellungen für Microsoft Launcher zu konfigurieren. 

## <a name="choosing-a-configuration-settings-format"></a>Auswählen eines Formats für die Konfigurationseinstellungen 

Es gibt zwei Methoden, mit denen Sie Konfigurationseinstellungen für Microsoft Launcher definieren können: 

- **Konfigurations-Designer** ermöglicht Ihnen das Konfigurieren von Einstellungen über eine benutzerfreundliche Oberfläche, auf der Sie Features aktivieren oder deaktivieren und Werte festlegen können. Bei dieser Methode gibt es einige deaktivierte Konfigurationsschlüssel mit dem Werttyp „BundleArray“. Diese Konfigurationsschlüssel können nur durch Eingabe von JSON-Daten konfiguriert werden. 

- **JSON-Daten** ermöglicht Ihnen das Definieren aller möglichen Konfigurationsschlüssel mithilfe eines JSON-Skripts. 

Wenn Sie Eigenschaften mit dem **Konfigurations-Designer** hinzufügen, können Sie diese Eigenschaften automatisch in JSON konvertieren, indem Sie in der Dropdownliste **Format der Konfigurationseinstellungen** den Eintrag **JSON-Daten eingeben** auswählen, wie unten gezeigt.

   ![Format der Konfigurationseinstellungen – Konfigurations-Designer verwenden](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>Verwenden von Konfigurations-Designer

Mithilfe von Konfigurations-Designer können Sie vorgegebene Einstellungen und die ihnen zugeordneten Werte auswählen.

   ![Format der Konfigurationseinstellungen – JSON-Daten eingeben](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

In der folgenden Tabelle sind die für Microsoft Launcher verfügbaren Konfigurationsschlüssel, Werttypen, Standardwerte und Beschreibungen aufgeführt. Die Beschreibung enthält das erwartete Geräteverhalten basierend auf den ausgewählten Werten. Konfigurationsschlüssel, die im Konfigurations-Designer deaktiviert sind, werden in der Tabelle nicht aufgeführt.

|    Konfigurationsschlüssel    |    Werttyp    |    Standardwert    |    Beschreibung     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Registrierungstyp    |    Zeichenfolge     |    Standard    |    Ermöglicht Ihnen das Festlegen des Registrierungstyps, für den diese Richtlinie gelten soll. Derzeit bezieht sich der Wert **Standard** auf **CorporateOwnedBuisnessOnly**. Zurzeit gibt es keine weiteren unterstützten Registrierungstypen.        JSON-Schlüsselname: management_mode_key        |
|    Änderung der App-Reihenfolge auf dem Startbildschirm durch Benutzer zulässig    |    Boolesch    |    True    |    Hiermit können Sie festlegen, ob die Einstellung für die **App-Reihenfolge auf dem Startbildschirm** durch Endbenutzer geändert werden darf.<ul><li>Wenn diese Einstellung auf **TRUE** festgelegt ist, wird die App-Reihenfolge in der Richtlinie nur bei der ersten Bereitstellung erzwungen. Danach wird die Richtlinie nicht mehr erzwungen, sodass Änderungen, die durch den Benutzer vorgenommen wurden, erhalten bleiben.</li><li>Wenn diese Einstellung auf **FALSE** festgelegt ist, wird die App-Reihenfolge bei jeder Synchronisierung erzwungen.</li></ul><br>**Hinweis:** Die App-Reihenfolge auf dem Startbildschirm kann nur über den JSON-Editor konfiguriert werden.<br><br>JSON-Schlüsselname:<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Rastergröße einstellen    |    Zeichenfolge    |    Automatisch    |    Ermöglicht es Ihnen, die Rastergröße für Apps festzulegen, die auf dem Startbildschirm positioniert werden sollen. Sie können die Anzahl der App-Zeilen und -Spalten festlegen, um die Rastergröße im folgenden Format zu definieren: `columns;rows`. Wenn Sie die Rastergröße definieren, entspricht die maximale Anzahl von Apps, die in einer Zeile auf dem Startbildschirm angezeigt werden, der Anzahl der von Ihnen festgelegten Zeilen. Ebenso entspricht die maximale Anzahl von Apps, die in einer Spalte auf dem Startbildschirm angezeigt werden, der Anzahl der von Ihnen festgelegten Spalten.<br><br>        JSON-Schlüsselname:<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Hintergrundbild für Gerät festlegen    |    Zeichenfolge    |    Null    |    Ermöglicht es Ihnen, ein Hintergrundbild Ihrer Wahl festzulegen, indem Sie die URL des Bilds eingeben, das als Hintergrundbild verwendet werden soll.<br><br>JSON-Schlüsselname:<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Ändern des Hintergrundbilds für das Gerät durch Benutzer zulässig    |    Bool    |    True    |    Hiermit können Sie festlegen, ob die Einstellung für das Hintergrundbild durch Endbenutzer geändert werden darf.<ul><li>Wenn diese Einstellung auf **TRUE** festgelegt ist, wird das Hintergrundbild in der Richtlinie nur bei der ersten Bereitstellung erzwungen. Danach wird die Richtlinie nicht mehr erzwungen, sodass Änderungen, die durch den Benutzer vorgenommen wurden, erhalten bleiben.</li><li>Wenn diese Einstellung auf **FALSE** festgelegt ist, wird das Hintergrundbild bei jeder Synchronisierung erzwungen.</li></ul><br>JSON-Schlüsselname:<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Feed aktivieren    |    Boolesch    |    True    |    Ermöglicht es Ihnen, den Launcher-Feed auf dem Gerät zu aktivieren, wenn der Benutzer auf dem Startbildschirm nach rechts wischt.<ul><li>Wenn diese Einstellung auf **TRUE** festgelegt ist, wird der Feed aktiviert.</li><li>Wenn diese Einstellung auf **FALSE** festgelegt ist, wird der Feed deaktiviert.</li></ul><br>JSON-Schlüsselname:<br>`com.microsoft.launcher.Feed.Enabled`    |
|    Ändern der Feedaktivierung durch Benutzer zulässig    |    Boolesch    |    True    |     Hiermit können Sie festlegen, ob die Einstellung **Feed aktivieren** durch Endbenutzer geändert werden darf.<ul><li>Wenn diese Einstellung auf **TRUE** festgelegt ist, wird der Feed nur bei der ersten Bereitstellung erzwungen. Danach wird die Richtlinie nicht mehr erzwungen, sodass Änderungen, die durch den Benutzer vorgenommen wurden, erhalten bleiben.</li><li>Wenn diese Einstellung auf **FALSE** festgelegt ist, wird der Feed bei jeder Synchronisierung erzwungen.</li></ul><br>JSON-Schlüsselname:`com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>Eingeben von JSON-Daten

Geben Sie JSON-Daten ein, um alle verfügbaren Einstellungen für Microsoft Launcher sowie die im **Konfigurations-Designer** deaktivierten Einstellungen zu konfigurieren, wie unten gezeigt.

   ![Konfigurations-Designer – JSON-Daten](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

Zusätzlich zu den konfigurierbaren Einstellungen, die in der Tabelle „Konfigurations-Designer“ (siehe oben) aufgeführt sind, enthält die folgende Tabelle die Konfigurationsschlüssel, die Sie nur über JSON-Daten konfigurieren können.

|    Konfigurationsschlüssel    |    Werttyp    |    Standardwert    |    Beschreibung     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Anwendungen für die Zulassungsliste festlegen<br>JSON-Schlüssel:`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Siehe: [Anwendungen für die Zulassungsliste festlegen](configure-microsoft-launcher.md#set-allow-listed-applications)</sup>    |    Hiermit können Sie aus den Apps, die auf dem Gerät installiert sind, diejenige Gruppe von Apps definieren, die auf dem Startbildschirm sichtbar sein soll. Sie können die Apps definieren, indem Sie die Paketnamen der Apps eingeben, die Sie sichtbar machen möchten. Mit `com.android.settings` beispielsweise kann über den Startbildschirm auf Einstellungen zugegriffen werden. Die Apps, die Sie der Zulassungsliste in diesem Abschnitt hinzufügen, müssen bereits auf dem Gerät installiert sein, um auf dem Startbildschirm angezeigt zu werden.<p>Eigenschaften:<ul><li>**Paket**: Der Name des Anwendungspakets</li><li>**Klasse:** Die Anwendungsaktivität, die für eine bestimmte App-Seite gilt. Wenn dieser Wert leer ist, wird die Standard-App-Seite verwendet.</li></ul>      |
|    App-Reihenfolge auf dem Startbildschirm<br>JSON-Schlüssel: `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Siehe: [App-Reihenfolge auf dem Startbildschirm](configure-microsoft-launcher.md#home-screen-app-order)      |    Ermöglicht es Ihnen, die App-Reihenfolge auf dem Startbildschirm anzugeben.<p>Eigenschaften:<br><ul><li>**Typ:** Der einzige unterstützte Typ ist `application`.</li><li>**Position**: Die Position des Anwendungssymbols auf dem Startbildschirm. Die Zählung beginnt bei Position 1 oben links und wird von links nach rechts und von oben nach unten fortgeführt.</li><li>**Paket**: Der Name des Anwendungspakets.</li><li>**Klasse:** Die Anwendungsaktivität, die für eine bestimmte App-Seite gilt. Wenn dieser Wert leer ist, wird die Standard-App-Seite verwendet.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Festlegen von Anwendungen für die Zulassungsliste

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>App-Reihenfolge auf dem Startbildschirm

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

Dies ist ein Beispiel für ein JSON-Skript, in dem alle verfügbaren Konfigurationsschlüssel enthalten sind:

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu vollständig verwalteten Android Enterprise-Geräten finden Sie unter [Einrichten der Intune-Registrierung für vollständig verwaltete Android Enterprise-Geräte](../enrollment/android-fully-managed-enroll.md).
