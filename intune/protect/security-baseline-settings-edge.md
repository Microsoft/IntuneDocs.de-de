---
title: InTune-Einstellungen für Sicherheitsbaselines für Microsoft Edge
titleSuffix: Microsoft Intune
description: Von InTune unterstützte Sicherheitsbaseline-Einstellungen für die Verwaltung des Microsoft Edge-Browsers
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415645"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Microsoft Edge-Baseline-Einstellungen für InTune

Anzeigen der baselineeinstellungen des Microsoft Edge-Webbrowsers, die von Microsoft InTune unterstützt werden. Die Standardwerte der Microsoft Edge-Baseline stellen die empfohlene Konfiguration für Microsoft Edge-Browser dar und stimmen möglicherweise nicht mit den Standardwerten für andere Sicherheitsbaselines identisch.

> [!NOTE]
> Die Microsoft Edge-Baseline befindet sich in Public Preview. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Umgehung von Microsoft Defender SmartScreen-Eingabe Aufforderungen für Websites verhindern**  
  **Standard**: Aktiviert  
  Microsoft Edge CSP: [Browser/preventsmartscreenpromptopverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Mit dieser Richtlinien Einstellung können Sie entscheiden, ob Benutzer die Microsoft Defender SmartScreen-Warnungen zu potenziell schädlichen Websites außer Kraft setzen können. 
  - Wenn Sie diese Einstellung aktivieren, können Benutzer keine Microsoft Defender SmartScreen-Warnungen ignorieren, und Sie sind nicht mehr in der Lage, mit der Website fortzufahren. 
  - Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, können Benutzer Microsoft Defender SmartScreen-Warnungen ignorieren und die Website fortsetzen.

- **Minimale SSL-Version aktiviert**  
  **Standard**: Aktiviert  

  Legen Sie eine unterstützte Mindestversion von SSL fest. Wenn Sie diese Richtlinie auf " *nicht konfiguriert*" festlegen, verwendet Microsoft Edge eine Standard-Mindestversion von *TLS 1,0*. Wenn diese *Option auf aktiviert*festgelegt ist, können Sie eine minimale Version aus den folgenden Werten auswählen:

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **Minimale SSL-Version aktiviert**  
    **Standard**: TLS 1,2

- **Verhindern der Umgehung von Microsoft Defender SmartScreen-Warnungen zu Downloads**  
  **Standard**: Aktiviert  
  Microsoft Edge CSP: [Browser/preventsmartscreenprompdeverrideforfiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Mit dieser Richtlinie können Sie feststellen, ob Benutzer Microsoft Defender SmartScreen-Warnungen zu nicht überprüften Downloads überschreiben können.
  - Wenn Sie diese Richtlinie aktivieren, können Benutzer in Ihrer Organisation keine Microsoft Defender SmartScreen-Warnungen ignorieren, und Sie werden daran gehindert, die nicht überprüften Downloads abzuschließen.
  - Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können Benutzer Microsoft Defender SmartScreen-Warnungen ignorieren und nicht überprüfte Downloads durchführen.

- **Benutzern das Fortfahren von der SSL-Warnungs Seite gestatten**  
  **Standard**: Deaktiviert  
  Microsoft Edge CSP: [Browser/preventcerterroroverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge zeigt eine Warnseite an, wenn Benutzer Websites mit SSL-Fehlern besuchen. Wenn Sie diese Richtlinie auf " *aktiviert* " oder " *nicht konfiguriert*" festlegen, können Benutzer auf diese Warnungs Seiten klicken. Wenn diese Richtlinie *deaktiviert*ist, können Benutzer nicht mehr auf eine Warn Seite klicken. 

- **Standardeinstellung für Adobe Flash**  
  **Standard**: Aktiviert  
  Microsoft Edge CSP: [Browser/allowflash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)und [Browser/allowflashclicktor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Bestimmt, ob Websites, die nicht von "pluginsallowedforurls" oder "pluginsblockedforurls" abgedeckt werden, das Adobe Flash-Plug-in automatisch ausführen können. 

  - "Blockplugins" auswählen, um Adobe Flash an allen Standorten zu blockieren
  - Wählen Sie "clicktoplay" aus, um Adobe Flash auszuführen, aber der Benutzer muss auf den Platzhalter klicken, um ihn zu starten.
  
   In jedem Fall haben die Richtlinien "pluginsallowedforurls" und "pluginsblockedforurls" Vorrang vor "defaultpluginssetting". Die automatische Wiedergabe ist nur für Domänen zulässig, die in der Richtlinie "pluginsallowedforurls" explizit aufgeführt sind. 
   Wenn Sie die automatische Wiedergabe für alle Websites aktivieren möchten, können Sie dieser Liste http://* und https://* hinzufügen. 
   
   - Wenn Sie diese Richtlinie auf *nicht konfiguriert*festlegen, kann der Benutzer diese Einstellung manuell ändern. * 2 = Adobe Flash-Plug-in blockieren * 3 = Klicken Sie hier, um die frühere Option "1" für "allow-all" wiederzugeben. diese Funktion wird jedoch jetzt nur von der Richtlinie "pluginsallowedforurls" behandelt. Vorhandene Richtlinien, die ' 1 ' verwenden, werden im Click-to-Play-Modus ausgeführt.  
 
  - **Standardeinstellung für Adobe Flash**  
    **Standard**: blockieren Sie das Adobe Flash-Plug-in.

- **Site Isolation für jeden Standort aktivieren**  
  **Standard**: Aktiviert  

  Die Richtlinie "siteperprocess" kann verwendet werden, um zu verhindern, dass Benutzer das Standardverhalten der Isolierung aller Standorte ablehnen. Sie können auch die isolateorigins-Richtlinie verwenden, um zusätzliche, differenziertere Ursprünge zu isolieren.

  - Wenn diese Richtlinie auf *aktiviert*festgelegt ist, können Benutzer das Standardverhalten nicht ablehnen, wenn jede Site in einem eigenen Prozess ausgeführt wird. 
  - Wenn Sie " *deaktiviert* " oder " *nicht konfiguriert*" verwenden, kann der Benutzer die Site Isolation deaktivieren. (Z. b. mit dem Eintrag "Site Isolation deaktivieren" in Edge://Flags.) Wenn Sie die Richtlinie deaktivieren oder die Richtlinie nicht konfigurieren, wird die Standort Isolation nicht deaktiviert.

- **Unterstützte Authentifizierungs Schemas**  
  **Standard**: Aktiviert  

  Gibt an, welche http-Authentifizierungsschemata unterstützt werden. Sie können die Richtlinie mithilfe der folgenden Werte konfigurieren: "Basic", "Digest", "NTLM" und "aushandeln". Trennen Sie mehrere Werte durch Kommas. Wenn Sie diese Richtlinie nicht konfigurieren, werden alle vier Schemas verwendet.
 
  - **Unterstützte Authentifizierungs Schemas**  
    Wählen Sie eine der folgenden Optionen aus: 
    - Einfach
    - Digest
    - Integrierte Windows-Authentifizierung (NTLM) *(Standardeinstellung)*
    - Aushandeln *(standardmäßig ausgewählt)*

- **Speichern von Kenn Wörtern für den Kennwort-Manager aktivieren**  
  **Standard**: Deaktiviert  
  Microsoft Edge CSP: [Browser/allowpasswordmanager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Aktivieren Sie Microsoft Edge, um Benutzer Kennwörter zu speichern. 
  - Wenn Sie diese Richtlinie aktivieren, können Benutzer ihre Kenn Wörter in Microsoft Edge speichern. Wenn Sie die Website das nächste Mal besuchen, wird das Kennwort von Microsoft Edge automatisch eingegeben. 
  - Wenn Sie diese Richtlinie deaktivieren, können Benutzer keine neuen Kenn Wörter speichern, Sie können jedoch weiterhin zuvor gespeicherte Kenn Wörter verwenden. 
  
  Wenn Sie diese Richtlinie auf " *aktiviert* " oder " *deaktiviert*" festlegen, können Benutzer diese Richtlinie in Microsoft Edge nicht ändern oder außer Kraft setzen. 
  
  Wenn Sie diese Einstellung auf *nicht konfiguriert*festlegen, können Benutzer Kenn Wörter speichern und diese Funktion deaktivieren.

- **Steuern, welche Erweiterungen nicht installiert werden können**  
  **Standard**: Aktiviert  

  Listet die spezifischen Erweiterungen auf, die Benutzer in Microsoft Edge nicht installieren können. Wenn Sie diese Richtlinie bereitstellen, werden alle zuvor installierten Erweiterungen in dieser Liste deaktiviert, und der Benutzer ist nicht in der Lage, Sie zu aktivieren. Wenn Sie ein Element aus der Liste der blockierten Erweiterungen entfernen, wird diese Erweiterung automatisch erneut aktiviert, wenn Sie zuvor installiert wurde.
  
  Verwenden Sie **\*** , um alle Erweiterungen zu blockieren, die nicht explizit in der Zulassungsliste aufgeführt sind. Wenn diese Richtlinie auf *nicht konfiguriert*festgelegt ist, können Benutzer jede Erweiterung in Microsoft Edge installieren. 
  
  Beispiel Wert: extension_id1 extension_id2.  
  <br>
  - **Erweiterungs-IDs, bei denen der Benutzer die Installation verhindern soll (oder * für alle)**  
    Wählen Sie **Hinzufügen** , und geben Sie zusätzliche Erweiterungen an. **\*** ist standardmäßig ausgewählt.

- **Microsoft Defender SmartScreen konfigurieren**  
  **Standard**: Aktiviert  
  Microsoft Edge CSP: [Browser/allowsmartscreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Mit dieser Richtlinien Einstellung können Sie konfigurieren, ob Microsoft Defender SmartScreen aktiviert werden soll. Microsoft Defender SmartScreen bietet Warnmeldungen zum Schutz Ihrer Benutzer vor potenziell phishingscams und Schadsoftware. 
  
  - Microsoft Defender SmartScreen ist standardmäßig aktiviert. Wenn Sie diese Einstellung aktivieren, ist Microsoft Defender SmartScreen eingeschaltet, und die Benutzer können Sie nicht deaktivieren.
  - Wenn Sie diese Einstellung deaktivieren, ist Microsoft Defender SmartScreen ausgeschaltet, und die Benutzer können Sie nicht einschalten. 
  - Wenn diese Option auf *nicht konfiguriert*festgelegt ist, können Benutzer auswählen, ob Microsoft Defender SmartScreen verwendet werden soll. 
  
  Diese Richtlinie ist nur auf Windows-Instanzen verfügbar, die mit einer Microsoft Active Directory-Domäne verknüpft sind, oder auf Windows 10 pro-oder Enterprise-Instanzen, die für die Geräteverwaltung registriert sind.

- **Native Messaging Hosts auf Benutzerebene zulassen (installiert ohne Administrator Berechtigungen)**  
  **Standard**: Deaktiviert  

  Aktiviert die Installation nativer Messaging Hosts auf Benutzerebene. 
  - Wenn Sie diese Richtlinie deaktivieren, werden von Microsoft Edge nur native Messaging-Hosts verwendet, die auf der Systemebene installiert sind. Wenn Sie diese Richtlinie nicht konfigurieren, wird von Microsoft Edge standardmäßig die Verwendung von nativen Messaging Hosts auf Benutzerebene zugelassen.

## <a name="next-steps"></a>Nächste Schritte

[Verwenden von Sicherheitsbaselines in InTune](security-baselines.md)
