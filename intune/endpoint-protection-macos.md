---
title: Hinzufügen von Endpoint Protection unter macOS in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie auf macOS-Geräten den Gatekeeper, um zu bestimmen, wo Apps, einschließlich der Mac App Store, installiert werden können. Aktivieren oder Konfigurieren Sie ebenfalls eine Firewall, um bestimmte Apps zuzulassen, zu blockieren, den geschützten Modus zu verwenden oder bestimmte Arten von eingehenden Verbindungen mithilfe von Microsoft Intune zu blockieren.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80b904893f118bac1f4d0d79da0cd10498b9f2ed
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71162866"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Endpoint Protection-Einstellungen in Intune unter MacOS  

In diesem Artikel werden die Endpoint Protection-Einstellungen beschrieben, die Sie für Ihre macOS-Geräte konfigurieren können. Sie konfigurieren diese Einstellungen mithilfe eines macOS-Geräte Konfigurations Profils für [Endpoint Protection](endpoint-protection-configure.md) in InTune.  

## <a name="gatekeeper"></a>Gatekeeper  

- **Von diesen Standorten heruntergeladene apps zulassen**  
  Begrenzen Sie die apps, die ein Gerät starten kann, je nachdem, wo die apps heruntergeladen wurden. Dadurch sollen Geräte vor Schadsoftware geschützt werden, außerdem werden nur Apps von vertrauenswürdigen Quellen zugelassen.  

  - **Nicht konfiguriert**  
  - **Mac App Store**  
  - **Mac App Store und verifizierte Entwickler**  
  - **Anywhere** (Beliebig)  

  **Standardeinstellung:** Nicht konfiguriert  

- **Benutzer kann Gatekeeper außer Kraft setzen.**  
  Hindert Benutzer am Außerkraftsetzen der Gatekeeper-Einstellungen und vom Installieren von Apps durch STRG+Klick. Wenn diese Einstellung aktiviert ist, kann der Benutzer eine beliebige App mithilfe von STRG+Klick installieren.  
 
  - **Nicht konfiguriert** : Benutzer können mit der Maustaste klicken, um apps zu installieren.  
  - **Blockieren** : verhindert, dass Benutzer mit dem Steuerelement per Mausklick apps installieren.  

  **Standardeinstellung:** Nicht konfiguriert  

## <a name="firewall"></a>Firewall  

Verwenden Sie die Firewall, um Verbindungen pro Anwendung statt pro Port zu steuern. Wenn Sie die Einstellung „Pro Anwendung“ verwenden, können Sie die Vorteile des Schutzes durch die Firewall besser nutzen. Dadurch wird ebenfalls verhindert, dass unerwünschte Apps die Netzwerkports steuern, die für zulässige Apps geöffnet sind.  

**Allgemein**
- **Firewall**  
  Aktivieren Sie die Firewall, um zu konfigurieren, wie eingehende Verbindung in Ihrer Umgebung behandelt werden.  
  - **Nicht konfiguriert**  
  - **Aktivieren**  

  **Standardeinstellung:** Nicht konfiguriert  

- **Eingehende Verbindungen**  
  Blockiert alle eingehenden Verbindungen außer denen, die für grundlegende Internetdienste erforderlich sind, z.B. DHCP, Bonjour und IPSec. Durch dieses Feature werden alle Freigabedienste blockiert, z.B. die Dateifreigabe und die Bildschirmfreigabe. Wenn Sie Freigabedienste verwenden, behalten Sie *Nicht konfiguriert* für diese Einstellung bei.  
  - **Nicht konfiguriert**  
  - **Blockieren**  

  **Standardeinstellung:** Nicht konfiguriert  

**Zulassen oder Blockieren eingehender Verbindungen für bestimmte Apps.**  

  - **Zulässige apps**  
    Wählen Sie die Apps aus, die explizit für eingehende Verbindungen zugelassen sind.  

  - **Blockierte apps**  
    Wählen Sie die Apps aus, für die eingehende Verbindungen blockiert werden sollen.  

  - **Geschützter Modus**  
    Hindern Sie den Computer daran, auf Suchanforderungen zu antworten, indem Sie den geschützten Modus aktivieren. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.  
    - **Nicht konfiguriert**  
    - **Aktivieren**  

    **Standardeinstellung:** Nicht konfiguriert  

## <a name="filevault"></a>FileVault  
Weitere Informationen zu den Einstellungen von Apple-flevault finden Sie unter [fdefilevault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) in den Inhalten von Apple Developer. 

> [!IMPORTANT]  
> Ab macOS 10,15 muss die MDM-Registrierung vom Benutzer genehmigt werden. 

- **FileVault**  
  Sie können die vollständige Datenträger Verschlüsselung mithilfe von XTS-AES 128 mit "flevault" auf Geräten *aktivieren* , auf denen macOS 10,13 und höher ausgeführt wird.  
  - **Nicht konfiguriert**  
  - **Aktivieren**  

  **Standardeinstellung:** Nicht konfiguriert  

  - **Wiederherstellungs Schlüsseltyp**  
    Für Geräte werden *Schlüssel Wiederherstellungs* Schlüssel erstellt. Konfigurieren Sie die folgenden Einstellungen für den persönlichen Schlüssel.  

    - **Speicherort des persönlichen Wiederherstellungs Schlüssels** : Geben Sie eine kurze Nachricht an den Benutzer an, die erläutert, wie und wo Sie Ihren persönlichen Wiederherstellungs Schlüssel abrufen können. Dieser Text wird in die Meldung eingefügt, die dem Benutzer auf dem Anmeldebildschirm angezeigt wird, wenn er zur Eingabe des persönlichen Wiederherstellungs Schlüssels aufgefordert wird, wenn ein Kennwort vergessen wird.  
      
    - **Rotation persönlicher Wiederherstellungs Schlüssel** : Geben Sie an, wie häufig der persönliche Wiederherstellungs Schlüssel für ein Gerät rotiert werden soll. Sie können den Standardwert **nicht konfiguriert**oder einen Wert von **1** bis **12** Monaten auswählen.  

  - **Eingabeaufforderung beim Abmelden deaktivieren**  
    Verhindern Sie, dass die Aufforderung an den Benutzer die Aktivierung von "flevault" beim Abmelden anfordert.  Wenn diese Option deaktiviert ist, wird die Eingabeaufforderung bei der Abmeldung deaktiviert, und der Benutzer wird stattdessen aufgefordert, wenn er sich anmeldet.  
    - **Nicht konfiguriert**  
    - **Deaktivieren** : Deaktivieren Sie die Eingabeaufforderung bei der Abmeldung.

    **Standardeinstellung:** Nicht konfiguriert  

  - **Gibt an, wie oft umgangen werden darf.**  
  Legen Sie fest, wie oft ein Benutzer Aufforderungen zum Aktivieren von "flevault" ignorieren kann, bevor "flevault" für die Anmeldung durch den Benutzer erforderlich ist.  

    - **Nicht konfiguriert** : die Verschlüsselung auf dem Gerät ist erforderlich, bevor die nächste Anmeldung zulässig ist.  
    - **1** bis **10** : erlauben Sie einem Benutzer, die Eingabeaufforderung von 1 bis 10 Mal zu ignorieren, bevor die Verschlüsselung auf dem Gerät erforderlich ist.  
    - **Keine Beschränkung, immer auffordern** : der Benutzer wird aufgefordert, die Aktivierung von "flevault" durchzusetzen, die Verschlüsselung ist jedoch nie erforderlich.  
 
    **Standardeinstellung:** Nicht konfiguriert  

Weitere Informationen zu "flevault" mit InTune finden Sie unter " [flevault Recovery Keys](encryption-monitor.md#filevault-recovery-keys)".

