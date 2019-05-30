---
title: Verschlüsselungsbericht und BitLocker-Schlüssel in Microsoft Intune
titleSuffix: Microsoft Intune
description: Sehen Sie sich einen Bericht zum Verschlüsselungsstatus Ihres Geräts an, und greifen Sie über das Microsoft Intune-Portal auf BitLocker-Wiederherstellungsschlüssel zu.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 52b92483ddafadf460911caaa472825a0bc0a20f
ms.sourcegitcommit: b4483c8476a209de83102e8993d8074dbb323493
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527216"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Überwachen von BitLocker und Geräteverschlüsselung  
Intune stellt einen zentralen Ort zur Verfügung, an dem der Verschlüsselungsstatus Ihrer Windows 10-Geräte bestimmt werden kann, und unterstützt Sie dabei, über Ihre Geräte auf wichtige Informationen für BitLocker zuzugreifen, z. B. Informationen in Active Directory (Azure AD).  

- Der [Verschlüsselungsbericht (in der öffentlichen Vorschauversion)](#encryption-report) stellt Details zum Verschlüsselungsstatus eines Geräts und zu dessen Bereitschaft zur Verfügung. Mithilfe der Informationen aus dem Bericht können Sie Probleme erkennen, die die erfolgreiche Verschlüsselung von Geräten behindern, die Sie schützen möchten.  
- [Sehen Sie sich über das Intune-Portal BitLocker-Details (in der öffentlichen Vorschauversion) an](#bitlocker-recovery-keys), z. B. die Schlüssel-ID und Wiederherstellungsschlüssel für Ihre Geräte.  

## <a name="encryption-report"></a>Verschlüsselungsbericht
Verwenden Sie den Verschlüsselungsbericht (in der öffentlichen Vorschauversion), um sich Details zum Verschlüsselungsstatus Ihrer Windows 10-Geräte anzusehen.  

Den Bericht finden Sie, indem Sie sich bei [Intune](https://aka.ms/intuneportal) anmelden, zur **Gerätekonfiguration** navigieren, und dann unter *Überwachung* die Option **Verschlüsselungsbericht (Vorschau)** auswählen.  

### <a name="prerequisites"></a>Voraussetzungen:
Damit ein Gerät im Verschlüsselungsbericht aufgeführt wird, muss mindestens die Windows-Version 1607 ausgeführt werden.  

### <a name="report-details"></a>Berichtdetails
Der Bericht zeigt den **Gerätenamen** sowie umfangreiche Details für Ihre Windows 10-Geräte an, z. B.:  
- **Betriebssystemversion:** Die Windows-Version  
- **TPM-Version:** Die Version des TPM-Chips (Trusted Platform Module) auf dem Gerät  
- **Verschlüsselungsbereitschaft:** Eine Auswertung der Bereitschaft der Geräte, die BitLocker-Verschlüsselung zu unterstützen Geräte können erkannt werden als:
  - **Bereit:** Das Gerät kann mithilfe einer MDM-Richtlinie (Mobile Device Management) verschlüsselt werden. Dazu muss das Gerät über ein TPM (Trusted Platform Module) verfügen und die folgenden Anforderungen an die Version von Windows 10 und SKU-Voraussetzungen erfüllen:
    - Mindestens Version 1703, Business, Enterprise oder Education
    - Mindestens Version 1809, Pro  
  
    Weitere Informationen finden Sie in der Windows-Dokumentation unter [BitLocker configuration service provider (CSP) (BitLocker-Konfigurationsdienstanbieter (Configuration Service Provider, CSP))](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).  

  - **Nicht bereit:** Das Gerät kann nicht vollständig verschlüsselt werden, unterstützt jedoch die Verschlüsselung. Das Gerät könnte beispielsweise von einem Benutzer manuell verschlüsselt werden oder über eine Gruppenrichtlinie, die so festgelegt werden kann, dass die Verschlüsselung ohne ein TPM zulässig ist.
  - **Nicht zutreffend**: Es stehen nicht genügend Informationen zur Verfügung, um dieses Gerät zu klassifizieren.  

- **Verschlüsselungsstatus:** Gibt an, ob das Betriebssystemlaufwerk verschlüsselt ist  


### <a name="device-encryption-status"></a>Geräteverschlüsselungsstatus
Wenn Sie ein Gerät auswählen, zeigt Intune den Bereich **Geräteverschlüsselungsstatus** an.

In diesem Bereich finden Sie die folgenden Details:  
- **Gerätename:** Der Name des Geräts, das Sie sich ansehen  
- **Verschlüsselungsbereitschaft:** Eine Auswertung der Bereitschaft der Geräte, die BitLocker-Verschlüsselung zu unterstützen Es wäre nicht möglich, dass ein Gerät den Verschlüsselungsstatus *Verschlüsselt* aufweist, obwohl seine Verschlüsselungsbereitschaft *Nicht bereit* ist, da ein TPM fehlt. (Weitere Informationen zur Verschlüsselungsbereitschaft finden Sie im vorherigen Abschnitt.)
- **Verschlüsselungsstatus:** Gibt an, ob das Betriebssystemlaufwerk verschlüsselt ist  
- **Profile:** Eine Liste von *Gerätekonfigurationsprofilen*, die auf das Gerät zutreffen, und die folgenden Profiltypen und -einstellungen beinhalten:  
  - Profiltyp = *Endpoint Protection*  
  - Einstellungen > Windows-Verschlüsselung > Geräte verschlüsseln = *Erforderlich*  

  Diese Liste ist hilfreich, wenn einzelne Richtlinien für eine Überprüfung gesucht werden, sollte die Profilstatuszusammenfassung auf Probleme hindeuten.  

- **Profilstatuszusammenfassung:** Eine Zusammenfassung der Profile, die für das Gerät gelten Die Zusammenfassung stellt die am wenigsten vorteilhafte Bedingung aller anwendbaren Profile dar. Wenn ein Profil beispielsweise zu einem Fehler führt, zeigt die Profilstatuszusammenfassung *Fehler* an.  
- **Statusdetails:** Erweiterte Details zum Verschlüsselungsstatus eines Geräts. 
  > [!NOTE]  
  > Intune zeigt nur *Statusdetails* für Geräte an, die mindestens das *Windows 10-Update vom 10. April 2019* ausführen.
  
  Dieses Feld zeigt Informationen zu jedem anwendbaren Fehler an, der erkannt werden kann. Mithilfe dieser Informationen verstehen Sie, warum ein Gerät möglicherweise nicht für die Verschlüsselung bereit ist.  

  Im Folgenden sehen Sie Beispiele für Statusdetails, die Intune melden kann:  

   - Die BitLocker-Richtlinie erfordert eine Benutzereinwilligung, damit der BitLocker-Laufwerkverschlüsselungsassistent gestartet werden kann, um mit der Verschlüsselung des Betriebssystemvolumes zu beginnen. Der Benutzer hat jedoch nicht eingewilligt.  
   - Die Verschlüsselungsmethode des Betriebssystemvolume stimmt nicht mit der BitLocker-Richtlinie überein.  
   - Die BitLocker-Richtlinie erfordert eine TPM-Schutzvorrichtung, damit das Betriebssystemvolume geschützt wird; es wird jedoch kein TPM verwendet.  
   - Die BitLocker-Richtlinie erfordert eine reine TPM-Schutzvorrichtung für das Betriebssystemvolume, aber es wird kein TPM-Schutz verwendet.  
   - Die BitLocker-Richtlinie erfordert einen TPM+PIN-Schutz für das Betriebssystemvolume, aber es wird keine TPM+PIN-Schutzvorrichtung verwendet.  
   - Die BitLocker-Richtlinie erfordert einen TPM+Systemstartschlüssel-Schutz für das Betriebssystemvolume, aber es wird keine TPM+Systemstartschlüssel-Schutzvorrichtung verwendet.  
   - Die BitLocker-Richtlinie erfordert einen TPM+PIN+Systemstartschlüssel-Schutz für das Betriebssystemvolume, aber es wird keine TPM+PIN+Systemstartschlüssel-Schutzvorrichtung verwendet.  
   - Das Betriebssystemvolume ist nicht geschützt.  
   - Die Sicherung des Wiederherstellungsschlüssel ist fehlgeschlagen.  
   - Ein Festplattenlaufwerk ist nicht geschützt.  
   - Die Verschlüsselungsmethode des Festplattenlaufwerks stimmt nicht mit der BitLocker-Richtlinie überein.  
   - Wenn Laufwerke verschlüsselt werden sollen, erfordert die BitLocker-Richtlinie entweder eine Anmeldung des Benutzers als Administrator, oder die Richtlinie „AllowStandardUserEncryption“ muss auf 1 festgelegt werden, wenn das Gerät mit Azure AD verknüpft ist.  
   - Die Windows-Wiederherstellungsumgebung (Windows Recovery Environment, WinRE) ist nicht konfiguriert.  
   - Für BitLocker steht kein TPM zur Verfügung, entweder, weil keines vorhanden ist, es in der Registrierung nicht mehr zur Verfügung steht, oder weil sich das Betriebssystem auf einem Laufwerk befindet, das entfernt werden kann.  
   - Das TMP ist nicht bereit für BitLocker.  
   - Das Netzwerk ist nicht verfügbar. Dies ist aber eine Voraussetzung zur Sicherung des Wiederherstellungsschlüssels.  

## <a name="bitlocker-recovery-keys"></a>BitLocker-Wiederherstellungsschlüssel
Intune gewährt im Rahmen einer öffentlichen Vorschauversion Zugriff auf das Azure AD-Blatt für BitLocker, sodass Sie sich über das Intune-Portal die BitLocker-Schlüssel-IDs und -Wiederherstellungsschlüssel für Ihre Windows 10-Geräte ansehen können.  Damit auf ein Gerät zugegriffen werden kann, müssen die dazugehörigen Schlüssel in Azure AD hinterlegt sein. 
1. Melden Sie sich bei [Intune](https://aka.ms/intuneportal) an, navigieren Sie zu **Geräte**, und wählen Sie dann unter *Verwalten* die Option **Alle Geräte** aus.
2. Wählen Sie aus der Liste ein Gerät aus, und wählen Sie dann unter *Überwachung* die Option **Recovery keys – Preview** (Wiederherstellungsschlüssel – Vorschau) aus.  
  
Wenn Schlüssel in Azure AD verfügbar sind, sind die folgenden Informationen verfügbar:
- BitLocker-Schlüssel-ID
- BitLocker-Wiederherstellungsschlüssel
- Laufwerkstyp  

Wenn keine Schlüssel in Azure AD verfügbar sind, zeigt Intune die Meldung *Für dieses Gerät wurde kein BitLocker-Schlüssel gefunden* an.  

Informationen zu BitLocker stehen über den [BitLocker-Konfigurationsdienstanbieter](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (Configuration Service Provider, CSP) zur Verfügung. Der BitLocker-CSP wird ab der Windows 10-Version 1703 unterstützt, und ab der Windows 10 Pro-Version 1809. 

## <a name="next-steps"></a>Nächste Schritte
Erstellen Sie eine [Gerätekonformitätsrichtlinie](compliance-policy-create-windows.md) für Windows 10-Geräte, um BitLocker und eine Verschlüsselung zu konfigurieren.
