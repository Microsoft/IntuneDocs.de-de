---
title: Erstellen einer Konformitätsrichtlinie für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen einer Microsoft Intune Gerätekonformitätsrichtlinie für iOS-Geräte, um ein E-Mail-Konto anzugeben, Geräte auf Jailbreaks zu überprüfen, das mindestens erforderliche und das maximal zulässige Betriebssystem zu überprüfen und die Kennworteinschränkungen, einschließlich der Kennwortlänge und Geräteinaktivität festzulegen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 887f45cdc79aa5e45de3e8a1df5d12665d2ed8ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für iOS-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine Intune-Konformitätsrichtlinie für iOS-Geräte gibt die Regeln und Einstellungen an, die iOS-Geräte erfüllen müssen, um konform zu sein. Wenn Sie Richtlinien für den bedingten Zugriff verwenden, können Sie den Zugriff auf Unternehmensressourcen zulassen oder blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Gerätekonformitätsrichtlinien können für sämtliche Plattformen im Intune Azure-Portal erstellt werden. Weitere Informationen über Konformitätsrichtlinien und die Voraussetzungen, die vor dem Erstellen einer Konformitätsrichtlinie erfüllt werden müssen, finden Sie im Artikel [Erste Schritte mit den Intune-Gerätekonformitätsrichtlinien](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

| **Richtlinieneinstellung** | **iOS 8.0 und höher** |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** | Wiederhergestellt |
| **Geräteverschlüsselung** | Wiederhergestellt (durch Festlegen der PIN) |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung)
| **E-Mail-Profil** | Isoliert |
|**Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |
| **Windows-Integritätsnachweis** | Nicht verfügbar |

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Erstellen einer Konformitätsrichtlinie im Azure-Portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen**.
4. Geben Sie einen Namen und eine Beschreibung ein, und wählen Sie die Plattform aus, auf die Sie diese Richtlinie anwenden möchten.
5. Klicken Sie auf **Einstellungen**, um die Einstellungen für **E-Mail-Adresse**, **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, klicken Sie auf **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

Wählen Sie zum Zuweisen einer Konformitätsrichtlinie zu Benutzern eine Richtlinie aus, die Sie konfiguriert haben. Vorhandene Richtlinien finden Sie im Bereich **Gerätekompatibilität > Richtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Damit öffnen Sie einen Bereich, auf dem Sie **Azure Active Directory-Sicherheitsgruppen** auswählen und der Richtlinie zuweisen können.
2. Klicken Sie auf **Ausgewählte Gruppen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen.  Wenn Sie auf **Speichern** klicken, wird die Richtlinie für Benutzer bereitgestellt.

Sie haben die Richtlinie auf Benutzer angewendet.  Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

<!---## Compliance policy settings--->

## <a name="email"></a>E-Mail

- **E-Mail-Konto muss von Intune verwaltet werden**: Wenn diese Option auf **Ja** festgelegt ist, muss das Gerät das auf dem Gerät bereitgestellte E-Mail-Profil verwenden. Das Gerät wird in den folgenden Situationen als nicht kompatibel betrachtet:
  - Das E-Mail-Profil wird für eine andere Benutzergruppe bereitgestellt als die Benutzergruppe, auf die die Kompatibilitätsrichtlinie ausgerichtet ist.
  - Der Benutzer hat bereits ein E-Mail-Konto auf dem Gerät eingerichtet, das dem Intune-E-Mail-Profil entspricht, das auf dem Gerät bereitgestellt wurde. Intune kann das vom Benutzer bereitgestellte Profil nicht überschreiben und daher nicht verwalten. Zum Sicherstellen der Kompatibilität muss der Benutzer die vorhandenen E-Mail-Einstellungen entfernen. Anschließend kann Intune das verwaltete E-Mail-Profil installieren.
- **Wählen Sie das E-Mail-Profil aus, das von Intune verwaltet werden muss**: Wenn die Einstellung **E-Mail-Konto muss von Intune verwaltet werden** aktiviert ist, wählen Sie **Auswählen** aus, um das Intune-E-Mail-Profil anzugeben. Das E-Mail-Profil muss auf dem Gerät vorhanden sein.

Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Geräte mit Jailbreak**: Wenn Sie diese Einstellung aktivieren, sind Geräte mit Jailbreak nicht konform.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Auswählen der maximalen Bedrohungsstufe, ab der ein gerät als nicht konform eingestuft wird. Wenn Sie die Bedrohungsstufe zum Beispiel auf **Mittel** festlegen, sind Geräte mit den Stufen „Mittel“, „Niedrig“ und „Sicher“ konform. Geräte mit einer hohen Bedrohungsstufe sind nicht konform.

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliches Betriebssystem**: Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Benutzer kann sein Gerät aktualisieren. Danach kann er auf Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion**: Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dann dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

> [!NOTE]
> Nachdem eine Konformitäts- oder Konfigurationsrichtlinie auf ein iOS-Gerät angewendet wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine Kennung festzulegen. Benutzer erhalten kontinuierlich eine Aufforderung, bis sie eine Kennung festgelegt haben.

- **Kennwort zum Entsperren mobiler Geräte erforderlich:** Legen Sie **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. iOS-Geräte mit Kennwort sind verschlüsselt.
- **Einfache Kennwörter**: Legen Sie **Ja** fest, damit Benutzer Kennwörter wie **1234** oder **1111** erstellen können.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.
- **Erforderlicher Kennworttyp**: Geben Sie an, ob der Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen muss.
- **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Mindestanzahl von Sonderzeichen (&, #, %, !, usw.) an, die im Kennwort enthalten sein müssen.

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
