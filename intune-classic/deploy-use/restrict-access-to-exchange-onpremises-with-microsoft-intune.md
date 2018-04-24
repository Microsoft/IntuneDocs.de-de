---
title: Schützen von E-Mail an lokales Exchange
description: Schützen und steuern Sie den Zugriff auf Unternehmens-E-Mail in Exchange lokal mit bedingtem Zugriff.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 73535e35605bbc9ca7123935e1816e90b5e60e1d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Schützen des E-Mail-Zugriffs auf lokale Exchange- und ältere Exchange Online Dedicated-Umgebungen mit Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können den E-Mail-Zugriff auf lokales Exchange oder auf die ältere Exchange Online Dedicated-Umgebung mithilfe von Microsoft Intune konfigurieren.
Weitere Informationen zur Funktionsweise des bedingten Zugriffs finden Sie im Artikel [Protect access to email and O365 services (Schützen des Zugriffs auf E-Mail- und Office 365-Dienste)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

> [!NOTE]
> Wenn Sie über eine Exchange Online Dedicated-Umgebung verfügen und herausfinden müssen, ob es sich um die neue oder die ältere Konfiguration handelt, wenden Sie sich an Ihren Kundenbetreuer.

## <a name="before-you-begin"></a>Vorbereitung

Stellen Sie Folgendes sicher:

-   Bei Ihrer Exchange-Version muss es sich um **Exchange 2010 oder höher** handeln. Exchange Server-Clientzugriffsserver-Arrays werden unterstützt.

-   Sie müssen den [lokalen Exchange-Connector von Intune](intune-on-premises-exchange-connector.md) verwenden, der Intune mit lokalem Exchange verbindet. Auf diese Weise können Sie Geräte über die Intune-Konsole verwalten.

    -   Der lokale Exchange Connector, der Ihnen in der Intune-Konsole zur Verfügung steht, ist spezifisch für Ihren Intune-Mandanten und kann mit keinem anderen Mandanten verwendet werden. Es wird empfohlen sicherzustellen, dass der Exchange-Connector für Ihren Mandanten **nur auf einem Computer** installiert ist.

        Sie können den Connector aus der Intune-Verwaltungskonsole herunterladen. Eine exemplarische Vorgehensweise zum Konfigurieren des lokalen Exchange-Connectors finden Sie unter [Konfigurieren des lokalen Exchange-Connectors für lokales oder gehostetes Exchange](intune-on-premises-exchange-connector.md).

    -   Sie können den Connector auf jedem Computer installieren, solange der jeweilige Computer mit dem Exchange-Server kommunizieren kann.

    -   Der Connector unterstützt die **Exchange-Clientzugriffsserver-Umgebung**. Technisch können Sie nach Wunsch den Connector auf dem Exchange-Clientzugriffsserver direkt installieren. Allerdings wird dies nicht empfohlen, da dadurch die Last auf dem Server erhöht wird. Sie müssen den Connector so konfigurieren, dass er mit einem der Exchange-Clientzugriffsserver kommuniziert.

-   Sie müssen **Exchange ActiveSync** für die zertifikatbasierte Authentifizierung oder die Eingabe von Anmeldeinformationen durch Benutzer konfigurieren.

### <a name="device-compliance-requirements"></a>Konformitätsanfoderungen für Geräte

Wenn Sie Richtlinien für bedingten Zugriff konfigurieren und auf einen Benutzer anwenden, muss das **Gerät**, das der Benutzer zum Abrufen von E-Mails verwendet, folgende Voraussetzungen erfüllen:

- Es muss ein in die Domäne eingebundener PC oder bei Intune **registriert** sein.

- **Es muss in Azure Active Directory registriert sein**. Darüber hinaus muss die Exchange ActiveSync-ID des Clients in Azure Active Directory registriert sein.

  Der Azure Active Directory-Geräteregistrierungsdienst wird automatisch für Intune- und Office 365-Kunden aktiviert. Kunden, die bereits den AD FS Device Registration Service bereitgestellt haben, sehen keine registrierten Geräte im lokalen Active Directory. **Dies gilt nicht für Windows-PCs und Windows Phone-Geräte.**

- Es muss mit allen für das Gerät festgelegten Intune-Konformitätsrichtlinien **übereinstimmen**.

### <a name="how-conditional-access-works-with-exchange-on-premises"></a>So funktioniert der bedingte Zugriff bei lokalem Exchange

Das folgende Diagramm veranschaulicht den Ablauf, der von den Richtlinien für bedingten Zugriff für die lokale Exchange-Umgebung verwendet wird, um zu bewerten, ob Geräte zugelassen oder blockiert werden.

![Diagramm mit den Entscheidungspunkten, die bestimmen, ob der Zugriff eines Geräts auf lokales Exchange zugelassen oder blockiert wird](../media/ConditionalAccess8-2.png)

Wenn eine Richtlinie für bedingten Zugriff nicht erfüllt wird, gilt ein 10-minütiges Zeitfenster zwischen dem Sperren des Geräts und dem Erhalt einer der folgenden Quarantänenachrichten durch den Benutzer bei seiner Anmeldung:

- Wenn das Gerät nicht bei Intune oder in Azure Active Directory registriert ist, wird eine Meldung mit Anweisungen zum Installieren der Unternehmensportal-App, zum Registrieren des Geräts und zum Aktivieren des E-Mail-Zugriffs angezeigt. Dieser Prozess verknüpft auch die Exchange ActiveSync-ID mit dem Eintrag des Geräts in Azure Active Directory.

-   Wenn das Gerät nicht konform ist, wird eine Meldung angezeigt, die Benutzer zum Intune-Unternehmensportal oder zur Unternehmensportal-App weiterleitet. Hier finden sie Informationen zum Problem und zu dessen Lösung.

## <a name="support-for-mobile-devices"></a>Unterstützung für mobile Geräte
Die folgenden Betriebssysteme werden unterstützt:
-   Windows Phone 8.1 und höher.

-   Die native E-Mail-App unter iOS.

-   Exchange ActiveSync-E-Mail-Clients wie Gmail unter Android 4 oder höher.
-   Exchange ActiveSync-E-Mail-Clients für **Android for Work-Geräte:** Nur **Gmail**- und **Nine Work**-Apps im **Arbeitsprofil** werden auf Android for Work-Geräten unterstützt. Damit der bedingte Zugriff unter Android for Work funktioniert, müssen Sie ein E-Mail-Profil für die Gmail- oder Nine Work-App sowie diese Apps als erforderliche Installation bereitstellen. 

> [!NOTE]
> Die Microsoft Outlook-App unter Android und iOS wird nicht unterstützt.

## <a name="support-for-pcs"></a>Unterstützung für PCs
Folgendes wird unterstützt:
-   Die **E-Mail**-Anwendung unter Windows 8.1 und höher (bei Registrierung des PC bei Intune)

##  <a name="configure-a-conditional-access-policy"></a>Konfigurieren einer Richtlinie für bedingten Zugriff

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** > **Bedingter Zugriff** > **Richtlinie für lokales Exchange**.
   ![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2. Konfigurieren Sie die Richtlinie mit den Einstellungen, die Sie benötigen: ![Screenshot der Seite mit der Richtlinie für lokales Exchange](../media/IntuneSA5bExchangeOnPremPolicy.png)

   - **Blockieren Sie den lokalen Exchange-Zugriff von E-Mail-Apps, wenn das Gerät nicht konform oder nicht bei Microsoft Intune registriert ist**: Bei Auswahl dieser Option wird der Zugriff auf Exchange-Dienste für Geräte blockiert, die nicht von Intune verwaltet werden oder eine Konformitätsrichtlinie nicht erfüllen.

   - **Standardregelüberschreibung – Den Zugriff auf Exchange durch registrierte und kompatible Geräte immer zulassen**: Wenn Sie diese Option aktivieren, dürfen Geräte, die bei Intune angemeldet sind und die Kompatibilitätsrichtlinie erfüllen, auf Exchange zugreifen.
     Diese Regel setzt die **Standardregel** außer Kraft, was bedeutet, dass, selbst wenn Sie die **Standardregel** so festlegen, dass der Zugriff isoliert bzw. blockiert wird, registrierte und kompatible Geräte weiterhin auf Exchange zugreifen können.

   - **Zielgruppen**: Wählen Sie die Intune-Benutzergruppen aus, die ihr Gerät bei Intune registrieren müssen, um auf Exchange zugreifen zu können.

   - **Ausgenommene Gruppen**: Wählen Sie die Intune-Benutzergruppen aus, die von der Richtlinie für bedingten Zugriff ausgenommen werden sollen. Benutzer in dieser Liste werden ausgenommen, auch wenn sie auch in der Liste **Zielgruppen** befinden.

   - **Plattformausnahmen**: Wählen Sie **Regel hinzufügen** aus, um eine Regel zu konfigurieren, die Zugriffsebenen für angegebene mobile Gerätefamilien und -modelle definiert. Da diese Geräte einen beliebigen Typ aufweisen können, können Sie auch Gerätetypen konfigurieren, die nicht von Intune unterstützt werden.

   - **Standardregel**: Bei Geräten, die durch keine der anderen Regeln abgedeckt werden, können Sie auswählen, ob der Zugriff auf Exchange zugelassen oder blockiert oder das Gerät unter Quarantäne gestellt werden soll. Wenn Sie die Regel so festlegen, dass der Zugriff zugelassen wird, wird iOS-, Windows- und Samsung KNOX-Geräten, die registriert und kompatibel sind, der E-Mail-Zugriff automatisch gewährt. Benutzer müssen keinen Prozess durchlaufen, um an ihre E-Mails zu gelangen.
     - Auf Android-Geräten, die nicht unter Samsung KNOX ausgeführt werden, erhalten Benutzer eine Quarantäne-E-Mail. Diese Mail enthält eine exemplarische Vorgehensweise, mit der die Benutzer die Registrierung und Kompatibilität überprüfen müssen, bevor der Zugriff auf die E-Mail erfolgen kann. Wenn Sie die Regel so festlegen, dass der Zugriff blockiert wird oder Geräte isoliert werden, wird der Zugriff aller Geräte auf Exchange blockiert, unabhängig davon, ob sie bereits bei Intune registriert sind oder nicht. Um zu verhindern, dass registrierte und kompatible Geräte von dieser Regel betroffen sind, aktivieren Sie die Option **Standardregelüberschreibung**.
       >[!TIP]
       >Wenn Sie beabsichtigen, zuerst alle Geräte zu blockieren, bevor Sie den Zugriff auf E-Mail gewähren, wählen Sie die Regel „Zugriff blockieren“ oder „Quarantäne“ aus. Die Standardregel gilt für alle Gerätetypen, sodass Gerätetypen, die Sie als Plattformausnahmen konfiguriert haben und die nicht von Intune unterstützt werden, ebenfalls betroffen sind.

   - **Benutzerbenachrichtigung**: Zusätzlich zu der von Exchange gesendeten Benachrichtigungs-E-Mail sendet Intune eine E-Mail mit Schritten zum Entsperren des Geräts. Sie können die Standardnachricht bearbeiten, um Sie an Ihre Bedürfnisse anzupassen. Da die Benachrichtigungs-E-Mail von Intune mit den Lösungsanweisungen an das Exchange-Postfach des Benutzers gesendet wird, kann es vorkommen, dass das Gerät blockiert wird, bevor der Benutzer die E-Mail-Nachricht erhält. In diesem Fall besteht die Möglichkeit, die Nachricht über ein freigeschaltetes Gerät oder eine andere Exchange-Zugriffsmethode anzuzeigen.
     - Dies gilt insbesondere, wenn die **Standardregel** für die Blockierung oder Quarantäne festgelegt ist. In diesem Fall muss der Benutzer seinen App Store besuchen, die Microsoft-Unternehmensportal-App herunterladen und sein Gerät registrieren. Dies gilt für iOS-, Windows- und Samsung KNOX-Geräte. Für Geräte, auf denen Samsung KNOX nicht ausgeführt wird, müssen Sie die Quarantäne-E-Mail an ein alternatives E-Mail-Konto senden. Der Benutzer muss die E-Mail auf sein blockiertes Gerät kopieren, um den Registrierungs- und Kompatibilitätsprozess abzuschließen.
       > [!NOTE]
       > Damit die Benachrichtigungs-E-Mail von Exchange gesendet werden kann, müssen Sie das Konto angeben, das dafür verwendet werden soll.
       >
       > Weitere Informationen finden Sie unter [Konfigurieren des lokalen Exchange Connectors für lokales oder gehostetes Exchange](intune-on-premises-exchange-connector.md).

3. Wenn Sie fertig sind, wählen Sie **Speichern** aus.

-   Die Richtlinie für bedingten Zugriff wird sofort wirksam und muss nicht explizit bereitgestellt werden.

-   Nachdem ein Benutzer ein Exchange ActiveSync-Profil eingerichtet hat, kann es ein bis drei Stunden dauern, bis das Gerät blockiert wird (wenn es nicht von Intune verwaltet wird).

-   Wenn ein blockierter Benutzer das Gerät anschließend bei Intune registriert und die Nichtkonformität behebt, wird der E-Mail-Zugriff innerhalb von zwei Minuten entsperrt.

-   Wenn der Benutzer die Registrierung des Geräts bei Intune aufhebt, kann es ein bis drei Stunden dauern, bis das Gerät blockiert wird.

**Beispielszenarios für die Konfiguration von Richtlinien für bedingten Zugriff zum Schutz des Gerätezugriffs finden Sie unter [Protect email access example scenarios (Beispielszenarios für den Schutz des E-Mail-Zugriffs)](restrict-email-access-example-scenarios.md).**

## <a name="next-steps"></a>Nächste Schritte
-   [Protect access to SharePoint Online (Schützen des Zugriffs auf SharePoint Online)](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [Protect access to Skype for Business Online (Schützen des Zugriffs auf Skype for Business Online)](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
