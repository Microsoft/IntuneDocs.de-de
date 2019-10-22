---
title: Exchange Connector-Problembehandlung
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Problemen mit dem lokalen Intune Exchange Connector behandeln.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508838"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Problembehandlung für den Intune Exchange Connector

In diesem Artikel wird beschrieben, wie Sie Probleme im Intune Exchange Connector behandeln.

## <a name="before-you-start"></a>Vorbereitung

Bevor Sie mit der Problembehandlung für ein Exchange Connector-Problem in InTune beginnen, erfassen Sie grundlegende Informationen, damit Sie an einer soliden Grundlage arbeiten. Diese Vorgehensweise kann Ihnen helfen, die Art des Problems besser zu verstehen und schneller zu beheben.

- Vergewissern Sie sich, dass Ihr Prozess die Installationsanforderungen erfüllt. Informationen finden Sie unter [Einrichten des lokalen Intune Exchange-Connectors](exchange-connector-install.md).
- Stellen Sie sicher, dass Ihr Konto sowohl über Exchange-als auch InTune-Administrator Berechtigungen verfügt
- Notieren Sie sich den vollständigen und genauen Fehler Meldungs Text, Details und den Ort, an dem die Meldung angezeigt wird.
- Bestimmen, wann das Problem gestartet wurde: 
  - Richten Sie den Connector zum ersten Mal ein? 
  - Funktioniert der Connector ordnungsgemäß und schlägt fehl?
  - Welche Änderungen wurden in der InTune-Umgebung, in der Exchange-Umgebung oder auf dem Computer, auf dem die Connector-Software ausgeführt wird, ausgeführt?
- Was ist die MDM-Autorität? Wenn es System Center Configuration Manager ist, welche Version von Configuration Manager verwenden Sie?
- Welche Version von Exchange verwenden Sie?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Verwenden Sie PowerShell, um weitere Daten zu Exchange Connector-Problemen zu erhalten.

- Um eine Liste aller mobilen Geräte für ein Postfach abzurufen, verwenden Sie `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Um eine Liste der SMTP-Adressen für ein Postfach abzurufen, verwenden Sie `Get-Mailbox -Identity user | select emailaddresses | fl`
- Verwenden Sie `Get-CASMailbox <upn> | fl`, um ausführliche Informationen zum Zugriffsstatus eines Geräts abzurufen.

## <a name="review-the-connector-configuration"></a>Überprüfen der Connector-Konfiguration

Überprüfen Sie die [Anforderungen für den lokalen Exchange-Connector](exchange-connector-install.md#intune-exchange-connector-requirements) , um sicherzustellen, dass Ihre Umgebung und der Connector ordnungsgemäß konfiguriert sind. 

### <a name="general-considerations-for-the-connector"></a>Allgemeine Überlegungen zum Connector

- Stellen Sie sicher, dass Ihre Firewall-und Proxy Server die Kommunikation zwischen dem Server zulassen, auf dem InTune Exchange Connector und der InTune-Dienst gehostet werden.

- Der Computer, der den InTune Exchange Connector und den Exchange-Client Zugriffs Server (CAS) hostet, sollte in eine Domäne eingebundenen und auf demselben LAN sein. Stellen Sie sicher, dass die erforderlichen Berechtigungen für das Konto hinzugefügt werden, das vom InTune Exchange Connector verwendet wird.

- Das Benachrichtigungs Konto dient zum Abrufen der Einstellungen für die *Automatische* Ermittlung. Weitere Informationen zu autodisover in Exchange finden Sie unter [autodiscover-Dienst in Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- Der InTune Exchange Connector sendet eine Anforderung an die EWS-URL mithilfe der Anmelde Informationen für das Benachrichtigungs Konto, um e-Mail-Benachrichtigungs Meldungen zusammen mit dem Link " *Get Started* " (für die Registrierung bei InTune) zu senden. Die Verwendung des Links " *Get Started* " zur Registrierung ist eine Voraussetzung für Android-nicht-Knox-Geräte. Andernfalls werden diese Geräte durch den bedingten Zugriff blockiert.

### <a name="common-issues-for-connector-configurations"></a>Häufige Probleme bei Connector-Konfigurationen

- **Kontoberechtigung**: Stellen Sie im Dialogfeld „Microsoft Intune Exchange Connector“ sicher, dass Sie ein Benutzerkonto angeben, das die richtigen Berechtigungen besitzt, um die [erforderlichen Windows PowerShell-Exchange-Cmdlets](exchange-connector-install.md#exchange-cmdlet-requirements) auszuführen.
- **Benachrichtigungs-e-Mail**: Benachrichtigungen aktivieren und ein Benachrichtigungs Konto angeben.
- **Client Access-Server Synchronisierung**: Geben Sie beim Konfigurieren von Exchange Connector einen Zertifizierungsstellen-CAS mit der niedrigsten Netzwerk Latenz für den Server an, auf dem der Exchange-Connector gehostet wird. Die Latenz bei der Kommunikation zwischen dem Clientzugriffsserver und dem Exchange Connector kann zu Verzögerungen bei der Geräteerkennung führen, insbesondere bei der dedizierten Verwendung von Exchange Online.
- **Synchronisierungszeitplan**: Bei einem Benutzer mit einem neu registrierten Gerät kann es beim Zugriff zu Verzögerungen kommen, bis der Exchange Connector mit dem Exchange-Clientzugriffsserver synchronisiert wurde. Eine vollständige Synchronisierung erfolgt einmal täglich, während eine schnelle Synchronisierung (Delta) mehrmals täglich durchgeführt wird. Sie können eine [schnelle oder vollständige Synchronisierung manuell erzwingen](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync), um Verzögerungen zu minimieren.

## <a name="next-steps"></a>Nächste Schritte
Die folgenden Artikel helfen Ihnen, häufige Probleme und spezifische Fehler zu beheben:

- [Beheben Sie häufige Probleme für den InTune Exchange Connector](troubleshoot-exchange-connector-common-problems.md).
- [Beheben Sie häufige Fehler für den InTune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Unterstützung durch Support oder InTune-Community:

- Weitere Informationen finden Sie [unter Support](../fundamentals/get-support.md) zur Verwendung der InTune-Konsole, um das Problem zu beheben, oder um eine Support Anfrage bei Microsoft zu eröffnen. 
- Veröffentlichen Sie Ihr Problem in den [Microsoft InTune-Foren](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
