---
title: Problembehandlung beim bedingten Zugriff
titleSuffix: Microsoft Intune
description: Was zu tun ist, wenn Ihre Benutzer durch bedingten Intune-Zugriff nicht auf Ressourcen zugreifen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8ebc708f76ed1f55f512edda75206d3ed5890a0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530721"
---
# <a name="troubleshoot-conditional-access"></a>Problembehandlung beim bedingten Zugriff

Sie können den Zugriff auf Office 365-Dienste wie Exchange Online, SharePoint Online, Skype for Business Online, Exchange On-Premises und andere Dienste schützen, indem Sie Intune und bedingten Zugriff verwenden. Mithilfe dieser Funktion können Sie sicherstellen, dass der Zugriff auf die Unternehmensressourcen beschränkt ist, die mit Intune registriert wurden und den von Ihnen festgelegten Regeln für den bedingten Zugriff entsprechen. Diese werden entweder in der Intune-Verwaltungskonsole oder in Azure Active Directory festgelegt. In diesem Artikel wird beschrieben, wie Sie vorgehen müssen, wenn Ihre Benutzer keinen Zugriff auf Ressourcen erhalten, die mit bedingtem Zugriff geschützt sind, oder wenn Benutzer auf geschützte Ressourcen zugreifen können, aber blockiert werden sollten.

## <a name="requirements-for-conditional-access"></a>Anforderungen für bedingten Zugriff

Damit der bedingte Zugriff funktioniert, müssen die folgenden Anforderungen erfüllt sein:

- Das Gerät muss von Intune registriert und verwaltet werden.
- Sowohl der Benutzer als auch das Gerät müssen den zugewiesenen Intune-Konformitätsrichtlinien entsprechen.
- Dem Benutzer muss standardmäßig eine Konformitätsrichtlinie für Geräte zugewiesen werden. Dies kann davon abhängen, wie die Einstellung **Kennzeichnen von Geräten, die keine Konformitätsrichtlinie zugewiesen haben, als:** unter **Gerätekonformität** > **Einstellungen für Konformitätsrichtlinie** im Intune-Verwaltungsportal konfiguriert wird.
- Exchange ActiveSync muss auf dem Gerät aktiviert werden, wenn der Benutzer den nativen E-Mail-Client des Geräts anstelle von Outlook verwendet. Dies geschieht für Windows Phone-, iOS- und Android-Geräte automatisch.
- Ihr Intune Exchange Connector muss ordnungsgemäß konfiguriert sein. Weitere Informationen finden Sie unter [Problembehandlung für den Exchange Connector in Microsoft Intune](troubleshoot-exchange-connector.md).

Sie können diese Bedingungen für alle Geräte im Azure-Portal und im Geräteinventurbericht anzeigen.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Geräte scheinen konform zu sein, aber Benutzer sind immer noch gesperrt

- Nicht-Knox-Android-Geräten wird der Zugriff erst gewährt, wenn der Benutzer in der erhaltenen Quarantäne-E-Mail auf den Link **Jetzt starten** klickt. Dies gilt auch dann, wenn der Benutzer bereits bei Intune registriert ist. Wenn der Benutzer die E-Mail mit dem Link auf seinem Mobiltelefon nicht erhält, kann er über einen PC auf seine E-Mail zugreifen und sie an ein E-Mail-Konto auf seinem Gerät weiterleiten.
- Wenn ein Gerät zum ersten Mal registriert wird, kann es einige Zeit dauern, bis Konformitätsinformationen für ein Gerät registriert werden. Warten Sie einige Minuten, und versuchen Sie es erneut.
- Bei iOS-Geräten kann ein vorhandenes E-Mail-Profil die Bereitstellung eines von Intune verwalteten E-Mail-Profils blockieren, das diesem Benutzer zugewiesen wurde, wodurch das Gerät nicht konform ist. In diesem Szenario informiert das Unternehmensportal den Benutzer darüber, dass die Konformität aufgrund des manuell konfigurierten E-Mail-Profils nicht besteht, und fordert den Benutzer dazu auf, dieses Profil zu entfernen. Sobald der Benutzer das bestehende E-Mail-Profil entfernt, wird das Intune-E-Mail-Profil erfolgreich bereitgestellt. Um dieses Problem zu vermeiden, weisen Sie Ihre Benutzer an, vor der Registrierung alle vorhandenen E-Mail-Profile auf ihrem Gerät zu entfernen.
- Ein Gerät kann beim Überprüfen der Kompatibilität hängen bleiben, wodurch verhindert wird, dass der Benutzer einen weiteren Eincheckvorgang initiiert. Wenn Sie über ein Gerät in diesem Zustand verfügen, gehen Sie wie folgt vor:
  - Stellen Sie sicher, dass das Gerät die neueste Version der Unternehmensportal-App verwendet.
  - Starten Sie das Gerät neu.
  - Überprüfen Sie, ob das Problem in verschiedenen Netzwerken (z. B. Mobilfunk, WLAN usw.) weiterhin besteht.

  Wenn das Problem bestehen bleibt, wenden Sie sich an den Microsoft Support, wie unter [Anfordern von Support für Microsoft Intune](get-support.md) beschrieben.
- Bestimmte Android-Geräte mögen verschlüsselt zu sein scheinen, aber die Unternehmensportal-App erkennt diese Geräte als nicht verschlüsselt und kennzeichnet sie als nicht konform. In diesem Szenario wird dem Benutzer eine Benachrichtigung in der Unternehmensportal-App angezeigt, die ihn auffordert, eine Startkennung für das Gerät festzulegen. Tippen Sie auf die Benachrichtigung und bestätigen Sie die vorhandene PIN oder das Kennwort, und wählen Sie dann auf dem Bildschirm **Sicherer Start** die Option **PIN für Start des Geräts anfordern**. Anschließend tippen Sie in der Unternehmensportal-App auf die Schaltfläche **Konformität prüfen** für das Gerät. Das Gerät sollte nun als verschlüsselt erkannt werden. 
  > [!NOTE]
  > Einige Gerätehersteller verschlüsseln ihre Geräte mit einer Standard-PIN anstelle einer vom Benutzer festgelegten PIN. Intune betrachtet die Verschlüsselung mit der Standard-PIN als unsicher und kennzeichnet diese Geräte als nicht konform, bis der Benutzer eine neue, nicht standardmäßige PIN erstellt.
- Ein Android-Gerät, das angemeldet und konform ist, kann weiterhin blockiert werden und einen Quarantänehinweis erhalten, wenn es zum ersten Mal versucht, auf Unternehmensressourcen zuzugreifen. Wenn dies der Fall ist, stellen Sie sicher, dass die Unternehmensportal-App nicht ausgeführt wird, und klicken Sie dann in der Quarantäne-E-Mail auf den Link **Jetzt starten**, um die Auswertung auszulösen. Dies sollte nur dann erforderlich sein, wenn der bedingte Zugriff zum ersten Mal aktiviert wird.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Geräte werden blockiert und es wird keine Quarantäne-E-Mail empfangen

- Stellen Sie sicher, dass das Gerät in der Intune-Verwaltungskonsole als Exchange ActiveSync-Gerät verfügbar ist. Ist dies nicht der Fall, ist es wahrscheinlich, dass bei der Geräteermittlung ein Fehler aufgetreten ist, da voraussichtlich ein Exchange Connector-Problem aufgetreten ist. Weitere Informationen finden Sie unter [Behandeln von Problemen mit dem lokalen Intune Exchange Connector](troubleshoot-exchange-connector.md).
- Bevor das Gerät vom Exchange Connector blockiert wird, sendet er eine Aktivierungs-E-Mail (Quarantäne). Wenn das Gerät offline ist, erhält es die Aktivierungs-E-Mail möglicherweise nicht. 
- Überprüfen Sie, ob der E-Mail-Client auf dem Gerät so konfiguriert ist, dass er E-Mails mit **Push** anstelle von **Poll** abruft. In diesem Fall könnte dies dazu führen, dass der Benutzer die E-Mail nicht erhält. Wechseln Sie zu **Poll** (Abrufen) und überprüfen Sie, ob das Gerät die E-Mail empfängt.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Die Geräte sind nicht konform, aber Benutzer werden nicht blockiert

- Bei Windows-PCs blockiert der bedingte Zugriff nur die native E-Mail-App, Office 2013 mit moderner Authentifizierung oder Office 2016. Zum Blockieren früherer Versionen von Outlook oder aller E-Mail-Apps auf Windows-PCs ist die Konfiguration der AAD-Geräteregistrierung und der Active Directory-Verbunddienste (AD FS) gemäß [Einrichten von SharePoint Online und Exchange Online für bedingten Zugriff mit Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication) erforderlich. 
- Wenn das Gerät gezielt zurückgesetzt oder von Intune außer Betrieb gesetzt wird, hat es nach der Deaktivierung möglicherweise noch mehrere Stunden lang Zugriff. Dies liegt daran, dass Exchange die Zugriffsrechte 6 Stunden lang zwischenspeichert. Ziehen Sie in diesem Szenario andere Möglichkeiten zum Datenschutz auf abgekoppelten Geräten in Betracht.
- Surface Hub-Geräte unterstützen den bedingten Zugriff, Sie müssen die Konformitätsrichtlinie jedoch für Gerätegruppen (nicht für Benutzergruppen) bereitstellen, um eine korrekte Auswertung zu ermöglichen.
- Überprüfen Sie die Zuweisungen für Ihre Konformitätsrichtlinien und Ihre Richtlinien für bedingten Zugriff. Wenn sich ein Benutzer nicht in der Gruppe befindet, der die Richtlinien zugewiesen sind, oder wenn er sich in einer Gruppe befindet, die ausgeschlossen wird, wird der Benutzer nicht blockiert. Nur Geräte für Benutzer einer zugeordneten Gruppe werden auf Konformität geprüft.

## <a name="noncompliant-device-is-not-blocked"></a>Nicht konformes Gerät wird nicht blockiert

Wenn Sie ein Gerät ermitteln, das nicht kompatibel ist, aber weiterhin Zugriff hat, gehen Sie folgendermaßen vor.
- Überprüfen Sie die Ziel- und Ausschlussgruppen. Wenn sich ein Benutzer nicht in der richtigen Zielgruppe oder in der Ausschlussgruppe befindet, wird er nicht blockiert. Nur die Geräte der Benutzer in einer Zielgruppe werden hinsichtlich der Kompatibilität überprüft.
- Stellen Sie sicher, dass das Gerät ermittelt wird. Verweist der Exchange Connector auf einen Exchange 2010-Clientzugriffsserver, obwohl sich der Benutzer auf einem Exchange 2013-Server befindet? In diesem Fall kann Intune die Verbindung des Geräts mit Exchange nicht erkennen, wenn die Exchange-Standardregel „Zulassen“ lautet, auch wenn sich der Benutzer in der Zielgruppe befindet.
- Überprüfen Sie die Existenz und den Zugriffsstatus des Geräts in Exchange:
  - Verwenden Sie dieses PowerShell-Cmdlet, um eine Liste aller mobilen Geräte für ein Postfach abzurufen: „Get-ActiveSyncDeviceStatistics -mailbox mbx“. Wenn das Gerät nicht aufgeführt ist, greift es nicht auf Exchange zu.
  - Wenn das Gerät aufgeführt ist, verwenden Sie das Cmdlet „Get-CASmailbox -identity:’upn’ | fl“, um ausführliche Informationen zum Zugriffsstatus zu erhalten und diese Informationen dem Microsoft-Support bereitzustellen.

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie weitere Hilfe benötigen, können Sie ebenfalls [Support für Microsoft Intune](get-support.md) anfordern.
