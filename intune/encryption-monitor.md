---
title: Verschlüsselungsbericht für verschlüsselte Berichte in Microsoft Intune
titleSuffix: Microsoft Intune
description: Rufen Sie einen Bericht zum Verschlüsselungsstatus Ihres iOS- oder Windows-Geräts ab, und greifen Sie über das Microsoft Intune-Portal auf die FileVault- und BitLocker-Wiederherstellungsschlüssel zu.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 76a0df5933127641d299a2a2f5e01d848e4d5d18
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550120"
---
# <a name="monitor-device-encryption-with-intune"></a>Überwachen der Geräteverschlüsselung mit Intune   

Der Microsoft Intune-Verschlüsselungsbericht enthält Details zum Verschlüsselungsstatus Ihrer verwalteten Geräte sowie Optionen zum Verwalten von Wiederherstellungsschlüsseln für Geräte. Welche Wiederherstellungsschlüsseloptionen verfügbar sind, hängt vom Typ des Geräts ab, das aufgerufen wird.  

Den Bericht finden Sie, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) anmelden, zur **Gerätekonfiguration** navigieren und dann unter *Überwachung* die Option **Verschlüsselungsbericht** auswählen.  

## <a name="view-encryption-details"></a>Abrufen von Verschlüsselungsdetails  

Der Verschlüsselungsbericht enthält allgemeine Informationen zu allen unterstützten und von Ihnen verwalteten Geräten. In den folgenden Abschnitten finden Sie Details zu den Informationen, die im Intune-Bericht enthalten sind.  
 
### <a name="prerequisites"></a>Voraussetzungen:  

Der Verschlüsselungsbericht unterstützt die Berichterstellung auf Geräten, auf denen die folgenden Betriebssystemversionen ausgeführt werden:  
- macOS 10.13 oder höher  
- Windows, Version 1607 oder höher  

### <a name="report-details"></a>Berichtdetails  

Im Bereich „Verschlüsselungsbericht“ werden alle von Ihnen verwalteten Geräte einschließlich entsprechender allgemeiner Details aufgelistet. Sie können ein Gerät aus der Liste auswählen, um einen Drilldown auszuführen und weitere Details im Bereich [Geräteverschlüsselungsstatus](#device-encryption-status) anzuzeigen.  

- **Gerätename:** der Name des Geräts.  
- **Betriebssystem:** die Geräteplattform, z. B. Windows oder macOS.  
- **Betriebssystemversion:** die Version von Windows oder macOS auf dem Gerät.  
- **TPM-Version** *(gilt nur für Windows 10):* die Version des TPM-Chips (Trusted Platform Module) auf dem Windows 10 Gerät.  
- **Verschlüsselungsbereitschaft:** eine Auswertung der Bereitschaft der Geräte zur Unterstützung einer anwendbaren Verschlüsselungstechnologie wie der BitLocker-oder FileVault-Verschlüsselung. Die Geräte können die folgenden Status aufweisen:  
  - **Bereit:** Das Gerät kann mithilfe einer MDM-Richtlinie (Mobile Device Management) verschlüsselt werden. Dazu muss es die folgenden Anforderungen erfüllen:  
    
    **Für macOS-Geräte:**  
    - macOS, Version 10.13 oder höher  
    
    **Für Windows 10-Geräte:**  
    - Version 1703 oder höher von *Business*, *Enterprise* oder *Education* oder Version 1809 oder höher von *Pro*  
    - Das Gerät muss über einen TPM-Chip verfügen.  
    
    Weitere Informationen finden Sie in der Windows-Dokumentation unter [BitLocker configuration service provider (CSP) (BitLocker-Konfigurationsdienstanbieter (Configuration Service Provider, CSP))](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).  

  - **Nicht bereit:** Das Gerät kann nicht vollständig verschlüsselt werden, unterstützt jedoch die Verschlüsselung. Das Windows-Gerät könnte beispielsweise von einem Benutzer manuell verschlüsselt werden oder über eine Gruppenrichtlinie, die so festgelegt werden kann, dass die Verschlüsselung ohne ein TPM zulässig ist.
  - **Nicht zutreffend**: Es stehen nicht genügend Informationen zur Verfügung, um dieses Gerät zu klassifizieren.  

- **Verschlüsselungsstatus:** Gibt an, ob das Betriebssystemlaufwerk verschlüsselt ist  

- **Benutzerprinzipalname:** der primäre Benutzer des Geräts.  

### <a name="device-encryption-status"></a>Geräteverschlüsselungsstatus  

Wenn Sie im Verschlüsselungsbericht ein Gerät auswählen, zeigt Intune den Bereich **Geräteverschlüsselungsstatus** an. In diesem Bereich finden Sie die folgenden Details:  

- **Gerätename:** Der Name des Geräts, das Sie sich ansehen  

- **Verschlüsselungsbereitschaft:** eine Auswertung der Bereitschaft der Geräte zur Unterstützung der Verschlüsselung über eine MDM-Richtlinie.  
  
  Beispiel: Wenn ein Windows 10-Gerät als *Nicht bereit* eingestuft wird, kann es trotzdem sein, dass die Verschlüsselung unterstützt wird. Das Windows 10-Gerät kann nur als *Bereit* eingestuft werden, wenn es über einen TPM-Chip verfügt. Es nicht erforderlich, dass der TPM-Chip die Verschlüsselung unterstützt. (Weitere Informationen zur Verschlüsselungsbereitschaft finden Sie im vorherigen Abschnitt.)  

- **Verschlüsselungsstatus:** Gibt an, ob das Betriebssystemlaufwerk verschlüsselt ist Es kann bis zu 24 Stunden dauern, bis Intune den Verschlüsselungsstatus eines Geräts oder die Änderung dieses Status meldet.  

- **Profile:** eine Liste von *Gerätekonfigurationsprofilen*, die für dieses Gerät gelten und mit den folgenden Werten konfiguriert werden:  

  - macOS:
    - Profiltyp = *Endpoint Protection*  
    - „Einstellungen“ > „FileVault“ > „FileVault“ = *Aktivieren*

  - Windows 10:
    - Profiltyp = *Endpoint Protection*  
    - Einstellungen > Windows-Verschlüsselung > Geräte verschlüsseln = *Erforderlich*  

  Sie können die Profilliste verwenden, um einzelne Richtlinien für eine Überprüfung auszuwählen, sollte die *Profilstatuszusammenfassung* auf Probleme hindeuten.  

- **Profilstatuszusammenfassung:** Eine Zusammenfassung der Profile, die für das Gerät gelten Die Zusammenfassung stellt die am wenigsten vorteilhafte Bedingung aller anwendbaren Profile dar. Wenn beispielsweise ein Profil von mehreren anwendbaren Profilen einen Fehler auslöst, zeigt die *Profilstatuszusammenfassung* *Fehler* an.  

- **Statusdetails:** Erweiterte Details zum Verschlüsselungsstatus eines Geräts.  

  > [!IMPORTANT]  
  > Für Windows 10-Geräte zeigt Intune *Statusdetails* für Geräte an, die mindestens das *Windows 10-Update vom 10. April 2019* ausführen.  
  
  Dieses Feld zeigt Informationen zu jedem anwendbaren Fehler an, der erkannt werden kann. Mithilfe dieser Informationen verstehen Sie, warum ein Gerät möglicherweise nicht für die Verschlüsselung bereit ist.  

  Im Folgenden sehen Sie Beispiele für Statusdetails, die Intune melden kann:  
  
  **macOS**:
  - Der Wiederherstellungsschlüssel wurde noch nicht abgerufen und gespeichert. Höchstwahrscheinlich wurde das Gerät nicht entsperrt, oder es wurde nicht angemeldet.  
 
    *Zu berücksichtigen: Dieses Ergebnis stellt nicht notwendigerweise einen Fehlerzustand dar, sondern einen temporären Zustand, der durch die zeitliche Steuerung auf dem Gerät verursacht werden kann, wenn die Hinterlegung von Wiederherstellungsschlüsseln eingerichtet werden muss, bevor die Verschlüsselungsanforderung an das Gerät gesendet wird. Dieser Status kann auch darauf hindeuten, dass das Gerät weiterhin gesperrt ist oder in letzter Zeit nicht bei Intune angemeldet wurde. Außerdem ist es möglich, dass ein Benutzer einen Wiederherstellungsschlüssel für ein Gerät erhält, das noch nicht verschlüsselt ist, da die FileVault-Verschlüsselung erst gestartet wird, nachdem das Gerät zum Laden an den Strom angeschlossen wurde.*  

  - Der Benutzer verzögert die Verschlüsselung oder führt derzeit den Verschlüsselungsprozess aus.  
 
    *Zu berücksichtigen: Der Benutzer hat sich nach dem Empfang der Verschlüsselungsanforderung noch nicht abgemeldet. Dies ist erforderlich, damit das Gerät von FileVault verschlüsselt werden kann. Es kann aber auch sein, dass der Benutzer das Gerät manuell entschlüsselt hat. Intune kann nicht verhindern, dass ein Benutzer sein Gerät entschlüsselt.*  

  - Das Gerät ist bereits verschlüsselt. Der Gerätebenutzer muss das Gerät entschlüsseln, um weitere Schritte ausführen zu können.  
 
    *Zu berücksichtigen: Intune kann FileVault nicht auf einem Gerät einrichten, das bereits verschlüsselt ist. Stattdessen muss der Benutzer sein Gerät manuell entschlüsseln, bevor es über eine Gerätekonfigurationsrichtlinie und Intune verwaltet werden kann.* 
 
  - Für FileVault muss der Benutzer sein Verwaltungsprofil in macOS Catalina und höher genehmigen.  
 
    *Zu berücksichtigen: Ab macOS, Version 10.15 (Catalina) können durch den Benutzer genehmigte Registrierungseinstellungen dazu führen, dass der Benutzer die FileVault-Verschlüsselung manuell genehmigen muss. Weitere Informationen finden Sie unter [Durch den Benutzer genehmigte Registrierung](macos-enroll.md) in der Intune-Dokumentation.*  

  - Unbekannt  

    *Zu berücksichtigen: Eine mögliche Ursache für einen unbekannten Status ist, dass das Gerät gesperrt ist und Intune den Hinterlegungs-oder Verschlüsselungsvorgang nicht starten kann. Sobald das Gerät entsperrt wird, kann der Vorgang fortgesetzt werden.*  

  **Windows 10:**  
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
  
  - Für BitLocker steht kein TPM zur Verfügung – entweder, weil keines vorhanden ist, es in der Registrierung nicht mehr zur Verfügung steht, oder weil sich das Betriebssystem auf einem Laufwerk befindet, das entfernt werden kann.  
  
  - Das TMP ist nicht bereit für BitLocker.  
  
  - Das Netzwerk ist nicht verfügbar. Dies ist aber eine Voraussetzung zur Sicherung des Wiederherstellungsschlüssels.  

## <a name="export-report-details"></a>Exportieren von Berichtsdetails 
Wenn Sie den Bereich „Verschlüsselungsbericht“ anzeigen, können Sie auf **Exportieren** klicken, um die Berichtsdetails in einer *CSV*-Datei herunterzuladen.  Dieser Bericht enthält allgemeine Informationen zum Bereich *Verschlüsselungsbericht* und Details zum *Geräteverschlüsselungsstatus* der einzelnen Geräte, die Sie verwalten.   
 
  
![Exportieren von Details](./media/encryption-monitor/export.png) 
 
Dieser Bericht kann bei der Identifizierung von Problemen von Gerätegruppen verwendet werden. Beispielsweise können Sie den Bericht verwenden, um eine Liste der macOS-Geräte zu erstellen, für die *der Benutzer bereits FileVault aktiviert hat*. So können die Geräte ermittelt werden, die manuell entschlüsselt werden müssen, damit Intune deren FileVault-Einstellungen verwalten kann.  
 
## <a name="filevault-recovery-keys"></a>FileVault-Wiederherstellungsschlüssel   
Wenn Intune zum ersten Mal ein macOS-Gerät mithilfe von FileVault verschlüsselt, wird ein persönlicher Wiederherstellungsschlüssel erstellt. Bei der Verschlüsselung zeigt das Gerät dem Endbenutzer den persönlichen Schlüssel einmal an.  
 
Bei verwalteten Geräten kann Intune eine Kopie des persönlichen Wiederherstellungsschlüssels hinterlegen. Durch die Hinterlegung von Schlüsseln können Intune-Administratoren die Schlüssel zum Schutz von Geräten rotieren, und die Benutzer können verlorene oder rotierte persönliche Wiederherstellungsschlüssel wiederherstellen.  
 
Intune unterstützt mehrere Optionen für das Rotieren oder Wiederherstellen von persönlichen Wiederherstellungsschlüsseln. Beispielsweise werden Schlüssel rotiert, wenn der aktuelle persönliche Schlüssel verloren geht oder als gefährdet eingestuft wird.  
 
> [!IMPORTANT]  
>  Geräte, die von Benutzern anstelle von Intune verschlüsselt werden, können nicht von Intune verwaltet werden. Das bedeutet, dass Intune die persönlichen Wiederherstellungsschlüssel dieser Geräte nicht hinterlegen und die Rotation des Wiederherstellungsschlüssels nicht verwalten kann.  Bevor Intune FileVault und die Wiederherstellungsschlüssel für das Gerät verwalten kann, muss der Benutzer sein Gerät entschlüsseln und dann von Intune wieder verschlüsseln lassen.  

### <a name="rotate-recovery-keys"></a>Rotieren von Wiederherstellungsschlüsseln  

- **Automatische Rotation:** Als Administrator können Sie festlegen, dass durch die FileVault-Einstellung „Rotation für persönlichen Wiederherstellungsschlüssel“ in regelmäßigen Abständen automatisch neue Wiederherstellungsschlüssel erstellt werden.  Wenn ein neuer Schlüssel für ein Gerät generiert wird, wird dieser nicht dem Benutzer angezeigt. Stattdessen muss der Benutzer den Schlüssel entweder bei einem Administrator anfragen oder über die Unternehmensportal-App abrufen.  

- **Manuelle Rotation:** Als Administrator können Sie Informationen zu einem über FileVault verschlüsselten Gerät abrufen, das Sie mit Intune verwalten. Anschließend können Sie den Wiederherstellungsschlüssel für Unternehmensgeräte manuell rotieren. Wiederherstellungsschlüssel für persönliche Geräte können nicht rotiert werden.  

  So rotieren Sie einen Wiederherstellungsschlüssel: 
  1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, navigieren Sie zu  **Geräte** , und wählen Sie dann unter „Verwalten“ die Option  **Alle Geräte** aus.  
  2. Wählen Sie aus der Geräteliste das verschlüsselte Gerät aus, für das Sie den Schlüssel rotieren möchten. Klicken Sie dann unter „Überwachen“ auf  **Wiederherstellungsschlüssel**.  
  3. Klicken Sie im Bereich „Wiederherstellungsschlüssel“ auf die Option **FileVault-Wiederherstellungsschlüssel rotieren**.  
  
     Wenn das Gerät das nächste Mal bei Intune eincheckt, wird dann der persönliche Schlüssel rotiert. Falls erforderlich kann der neue Schlüssel vom Endbenutzer über das Unternehmensportal abgerufen werden. 


### <a name="recover-recovery-keys"></a>Wiederherstellen von Wiederherstellungsschlüsseln  
- **Administrator:** Administratoren können keine persönlichen Wiederherstellungsschlüssel für Geräte abrufen, die mit FileVault verschlüsselt sind.  

- **Endbenutzer:** Endbenutzer können ihre persönlichen Wiederherstellungsschlüssel für ihre verwalteten Geräte über die Unternehmensportal-Website abrufen. Über die Unternehmensportal-App ist dies nicht möglich.  

 
  So rufen Sie einen Wiederherstellungsschlüssel ab:  
  1. Melden Sie sich auf einem beliebigen Gerät bei der *Intune-Unternehmensportal*-Website an.  
  2. Navigieren Sie im Portal zu **Geräte**, und wählen Sie das macOS-Gerät aus, das über FileVault verschlüsselt ist.  
  3. Klicken Sie auf **Wiederherstellungsschlüssel abrufen**. Dann wird der aktuelle Wiederherstellungsschlüssel angezeigt.  
  
     Wenn Sie ein iPhone verwenden, müssen Sie auf die *drei* Punkte klicken, bevor die Option *Wiederherstellungsschlüssel abrufen* angezeigt wird.  

## <a name="bitlocker-recovery-keys"></a>BitLocker-Wiederherstellungsschlüssel  

Intune gewährt Zugriff auf das Azure AD-Blatt für BitLocker, sodass Sie sich über das Intune-Portal die BitLocker-Schlüssel-IDs und -Wiederherstellungsschlüssel für Ihre Windows 10-Geräte ansehen können.  Damit auf ein Gerät zugegriffen werden kann, müssen die dazugehörigen Schlüssel in Azure AD hinterlegt sein. 
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, navigieren Sie zu **Geräte**, und wählen Sie dann unter *Verwalten* die Option **Alle Geräte** aus.  

2. Wählen Sie ein Gerät aus der Liste aus, und wählen Sie dann unter *Überwachung* die Option **Recovery keys** (Wiederherstellungsschlüssel) aus.  
  
Wenn Schlüssel in Azure AD verfügbar sind, sind die folgenden Informationen verfügbar:
- BitLocker-Schlüssel-ID  
- BitLocker-Wiederherstellungsschlüssel  
- Festplattentyp  

Wenn keine Schlüssel in Azure AD verfügbar sind, zeigt Intune die Meldung *Für dieses Gerät wurde kein BitLocker-Schlüssel gefunden* an.  

Informationen zu BitLocker stehen über den [BitLocker-Konfigurationsdienstanbieter](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (Configuration Service Provider, CSP) zur Verfügung. Der BitLocker-CSP wird ab der Windows 10-Version 1703 unterstützt, und ab der Windows 10 Pro-Version 1809.  

## <a name="next-steps"></a>Nächste Schritte  

Erstellen Sie eine [Gerätekonformitätsrichtlinie](compliance-policy-create-windows.md).
