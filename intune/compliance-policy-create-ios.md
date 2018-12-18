---
title: Erstellen einer Konformitätsrichtlinie für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder konfigurieren Sie eine Microsoft Intune Gerätekonformitätsrichtlinie für iOS-Geräte, um ein E-Mail-Konto anzugeben, Geräte auf Jailbreaks zu überprüfen, das mindestens erforderliche und das maximal zulässige Betriebssystem zu überprüfen und die Kennworteinschränkungen, einschließlich der Kennwortlänge und Geräteinaktivität festzulegen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 41ae1ffc17eee93b45f00e4eef5590f6a5d0b7b4
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112509"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für iOS-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine Intune-Konformitätsrichtlinie für iOS-Geräte gibt die Regeln und Einstellungen an, die iOS-Geräte erfüllen müssen, um konform zu sein. Wenn Sie Richtlinien für den bedingten Zugriff verwenden, können Sie den Zugriff auf Unternehmensressourcen zulassen oder blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Gerätekonformitätsrichtlinien können für sämtliche Plattformen im Intune Azure-Portal erstellt werden. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

---------------------------

| **Richtlinieneinstellung** | **iOS 8.0 und höher** |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** | Wiederhergestellt |
| **Geräteverschlüsselung** | Wiederhergestellt (durch Festlegen der PIN) |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung)
| **E-Mail-Profil** | Isoliert |
|**Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |
| **Windows-Integritätsnachweis** | Nicht verfügbar |

---------------------------

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Wählen Sie als **Plattform** die Option **iOS** aus. 
5. Wählen Sie **Einstellungen konfigurieren**, um die in diesem Thema beschriebenen Einstellungen zu **E-Mail**, **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, wählen Sie **OK** und dann **Erstellen**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>E-Mail

- **Verwaltetes E-Mail-Profil für Mobilgeräte erforderlich:** Wenn Sie diese Option auf „Erforderlich“ festlegen, werden Geräte, die nicht über ein von Intune verwaltetes E-Mail-Profil verfügen, als nicht konform betrachtet. Ein Gerät verfügt möglicherweise nicht über ein verwaltetes E-Mail-Profil, wenn es nicht korrekt ausgerichtet ist oder wenn der Benutzer das E-Mail-Konto auf dem Gerät manuell einrichtet.

  Das Gerät wird in den folgenden Situationen als nicht kompatibel betrachtet:
  - Das E-Mail-Profil wird für eine andere Benutzergruppe bereitgestellt als die Benutzergruppe, auf die die Kompatibilitätsrichtlinie ausgerichtet ist.
  - Der Benutzer hat bereits ein E-Mail-Konto auf dem Gerät eingerichtet, das dem Intune-E-Mail-Profil entspricht, das auf dem Gerät bereitgestellt wurde. Intune kann das vom Benutzer bereitgestellte Profil nicht überschreiben und daher nicht verwalten. Zum Sicherstellen der Kompatibilität muss der Benutzer die vorhandenen E-Mail-Einstellungen entfernen. Anschließend kann Intune das verwaltete E-Mail-Profil installieren.

- **E-Mail-Profil auswählen, das von Intune verwaltet werden muss:** Wenn die Einstellung **E-Mail-Konto muss von Intune verwaltet werden** aktiviert ist, wählen Sie **Auswählen** aus, um das Intune-E-Mail-Profil anzugeben. Das E-Mail-Profil muss auf dem Gerät vorhanden sein.

Weitere Informationen zu E-Mail-Profilen finden Sie unter [Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Geräte mit Jailbreak:** Wenn Sie diese Einstellung aktivieren, sind Geräte mit Jailbreak nicht konform.
- **Gerät darf höchstens die Gerätebedrohungsstufe aufweisen** (iOS 8.0 und höher): Wählen Sie die maximale Bedrohungsstufe aus, um Geräte als nicht konform zu kennzeichnen. Geräte, die diese Bedrohungsstufe überschreiten, werden als nicht konform gekennzeichnet:
  - **Secured** (Geschützt): Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein dürfen. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig:** Das Gerät wird als konform bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel:** Das Gerät wird als konform bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch:** Dies ist die am wenigsten sichere Option, die alle Bedrohungsstufen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliche Betriebssystemversion:** Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Benutzer kann sein Gerät aktualisieren. Danach kann er auf Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dann dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.
- **Niedrigste Buildversion des Betriebssystems:** Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige minimale Buildnummer am Gerät einzugeben. Diese Konformitätsprüfung unterstützt Geräte mit iOS 8.0 und höher. 
- **Höchste Buildversion des Betriebssystems:** Wenn Apple Sicherheitsupdates veröffentlicht, wird in der Regel die Nummer des Builds aktualisiert, nicht die Betriebssystemversion. Verwenden Sie diese Funktion, um eine zulässige maximale Buildnummer am Gerät einzugeben. Diese Konformitätsprüfung unterstützt Geräte mit iOS 8.0 und höher.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

> [!NOTE]
> Nachdem eine Konformitäts- oder Konfigurationsrichtlinie auf ein iOS-Gerät angewendet wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine Kennung festzulegen. Benutzer erhalten kontinuierlich eine Aufforderung, bis sie eine Kennung festgelegt haben.

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:** Legen Sie diese Option auf **Anfordern** fest, damit Benutzer ein Kennwort eingeben müssen, bevor sie auf ihr Gerät zugreifen können. iOS-Geräte mit Kennwort sind verschlüsselt.
- **Einfache Kennwörter:** Legen Sie diese Option auf **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen ein, die das Kennwort enthalten muss.
- **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus **numerischen** Zeichen bestehen oder eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).
- **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Geben Sie die Mindestanzahl von Sonderzeichen (&, #, %, ! usw.) ein, die im Kennwort enthalten sein müssen.

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Minuten der Inaktivität vor Anforderung des Kennworts:** Geben Sie die Leerlaufzeit ein, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl der Tage aus, nach der das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung:** Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können.

### <a name="restricted-applications"></a>Eingeschränkte Anwendungen 
Sie können Apps einschränken, indem Sie ihre Bündel-IDs der Richtlinie hinzufügen. Wenn die App dann auf einem Gerät installiert wird, wird das Gerät als nicht konform gekennzeichnet. 
- **App-Name:** Geben Sie einen benutzerfreundlichen Namen ein, damit Sie die Bündel-ID einfacher identifizieren können. 
- **App-Bündel-ID:** Geben Sie die eindeutige Bündel-ID ein, die vom App-Anbieter zugewiesen wurde. Informationen zum Ermitteln der Bündel-ID finden Sie unter [How to find the bundle ID for an iOS app (Ermitteln der Bündel-ID für eine iOS-App)](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).  

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)
