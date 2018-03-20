---
title: "Erstellen einer Konformitätsrichtlinie für Android for Work"
titleSuffix: Microsoft Intune
description: "Erstellen einer Konformitätsrichtlinie für Android for Work-Geräte in Microsoft Intune, damit Sie die Anforderungen angeben können, die ein Gerät im Hinblick auf Konformität erfüllen muss."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ca31d4c83ccc6b786933080b96f66953cf1a108
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Erstellen einer Gerätekonformitätsrichtlinie für Android for Work-Geräte in Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Eine Konformitätsrichtlinie für Android for Work-Geräte in Intune gibt die Regeln und Einstellungen an, die Android for Work-Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit bedingten Zugriff verwenden, um Zugriff auf Unternehmensressourcen zu gewähren oder zu blockieren. Sie können auch Berichte zu Geräten abrufen und Maßnahmen gegen die Nichtkonformität vornehmen. Sie können Gerätekonformitätsrichtlinien für jede Plattform im Intune Azure-Portal erstellen. Weitere Informationen über Konformitätsrichtlinien und die Voraussetzungen, die vor dem Erstellen einer Konformitätsrichtlinie erfüllt werden müssen, finden Sie unter [Erste Schritte mit den Microsoft Intune-Gerätekonformitätsrichtlinien](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

--------------------------

|**Richtlinieneinstellung**| **Android for Work** |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** |  Isoliert |
| **Geräteverschlüsselung** |  Isoliert |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung) |
| **E-Mail-Profil** | Nicht verfügbar |
| **Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |
| **Windows-Integritätsnachweis** |Nicht verfügbar |

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)+

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt, wird das Gerät blockiert.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Erstellen einer Konformitätsrichtlinie im Azure-Portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
1. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonformität**. Klicken Sie unter **Verwalten** auf **Richtlinien** > **Richtlinie erstellen**.
2. Geben Sie einen Namen und eine Beschreibung ein, und wählen Sie die Plattform aus, auf die Sie diese Richtlinie anwenden möchten.
3. Klicken Sie auf **Einstellungen konfigurieren**, um die Einstellungen zur **Systemsicherheit**, **Device Health** (Integrität für Geräte) und **Geräteeigenschaften** anzugeben. Wählen Sie abschließend **OK** aus.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

Wählen Sie zum Zuweisen einer Konformitätsrichtlinie zu Benutzern eine Richtlinie aus, die Sie konfiguriert haben. Vorhandene Richtlinien finden Sie im Bereich **Gerätekompatibilität > Richtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Damit öffnen Sie den Bereich, in dem Sie **Azure Active Directory-Sicherheitsgruppen** auswählen und der Richtlinie zuweisen können.
2. Klicken Sie auf **Ausgewählte Gruppen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen.  Wenn Sie auf **Speichern** klicken, wird die Richtlinie für Benutzer bereitgestellt.

Sie haben die Richtlinie auf Benutzer angewendet.  Die von den Benutzern, denen die Richtlinie zugewiesen wurde, verwendeten Geräte werden auf Konformität überprüft.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte erforderlich:** Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.
- **Kennwortstärke:** Mit dieser Einstellung wird erkannt, ob die angegebenen Kennwortanforderungen auf dem Gerät konfiguriert wurden. Aktivieren Sie diese Einstellung, um festzulegen, dass Benutzer für Android-Geräte bestimmte Kennwortanforderungen konfigurieren müssen. Es stehen die folgenden Optionen zur Auswahl:
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Alphanumerisch mit Symbolen**
- **Minuten der Inaktivität, bevor ein Kennwort erforderlich ist:** Gibt die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.
- **Kennwortverlauf speichern**: Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.
- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.
- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte zusammen mit der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** verwendet werden. Die Endbenutzer werden zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.


### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilen Geräten erforderlich:** Diese Einstellung muss nicht konfiguriert werden, da Android for Work-Geräte eine Verschlüsselung erzwingen.


## <a name="device-health-and-security-settings"></a>Einstellungen für Geräteintegrität und Sicherheit

- **Gerät darf keinen Jailbreak oder Rootzugriff verwenden:** Wenn Sie diese Einstellung aktivieren, werden Geräte mit Jailbreak als nicht konform eingestuft.
- **Installation von Apps aus unbekannten Quellen muss auf Geräten gesperrt sein:** Diese Einstellung muss nicht konfiguriert werden, da Android for Work-Geräte die Installation von unbekannten Quellen immer einschränken.
- **USB-Debuggen muss deaktiviert sein:** Diese Einstellung muss nicht konfiguriert werden, da USB-Debuggen auf Android for Work-Geräten bereits deaktiviert ist.
- **Niedrigste zulässige Android-Sicherheitspatchebene**: Verwenden Sie diese Einstellung, um eine niedrigste zulässige Android-Patchebene festzulegen. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht kompatibel. Das Datum muss im folgenden Format angegeben werden: JJJJ-MM-TT.
- **Schutz vor Gerätebedrohungen muss aktiviert sein**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Kompatibilitätsvoraussetzung zu fordern. Wählen Sie aus den folgenden Optionen die maximal zulässige Bedrohungsstufe aus:
  - **Keine (geschützt)**: Dies ist die sicherste Einstellung. Dies bedeutet, dass das Gerät keinerlei Bedrohungen unterliegen darf. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als konform bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen die Stufen „Niedrig“ oder „Mittel“ aufweisen. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option. Im Prinzip lässt diese Option alle Bedrohungsstufen zu. Sie ist somit eigentlich nur zu Berichtszwecken nützlich.

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimal erforderliches Betriebssystem**: Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
