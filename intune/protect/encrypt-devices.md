---
title: Verschlüsseln von Geräten mit der von Plattformen unterstützten Verschlüsselungsmethode
titleSuffix: Microsoft Intune
description: Verschlüsseln Sie Geräte mithilfe von integrierten Verschlüsselungsmethoden wie BitLocker oder FileVault, und verwalten Sie die Wiederherstellungsschlüssel für diese verschlüsselten Geräte über das Intune-Portal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f885cbddf8ecb984dc6e98db38c9adbc6a07119a
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306856"
---
# <a name="use-device-encryption-with-intune"></a>Verwenden der Geräteverschlüsselung mit Intune  

Verwenden Sie Intune, um Geräte mit integrierter Laufwerk- oder Datenträgerverschlüsselung zu verwalten, damit die Daten auf Ihren Geräten geschützt werden.  

Konfigurieren Sie die Datenträgerverschlüsselung als Teil eines Gerätekonfigurationsprofils für Endpoint Protection. Die folgenden Plattformen und Verschlüsselungstechnologien werden von Intune unterstützt:  
- macOS: FileVault   
- Windows 10 und höher: BitLocker  

Intune beinhaltet auch einen integrierten [Verschlüsselungsbericht](encryption-monitor.md), in dem Details zum Verschlüsselungsstatus Ihrer verwalteten Geräte angezeigt werden.  

## <a name="filevault-encryption-for-macos"></a>FileVault-Verschlüsselung für macOS  

Verwenden Sie Intune, um die FileVault-Datenträgerverschlüsselung auf macOS-Geräten zu konfigurieren. Verwenden Sie anschließend den Intune-Verschlüsselungsbericht, um die Verschlüsselungsdetails für diese Geräte anzuzeigen und Wiederherstellungsschlüssel für mit FileVault verschlüsselte Geräte zu verwalten.  

FileVault ist ein Verschlüsselungsprogramm für ganze Datenträger, das im Lieferumfang von macOS enthalten ist. Verwenden Sie Intune, um FileVault auf Geräten zu konfigurieren, auf denen **macOS 10.13 oder höher** ausgeführt wird.  

Erstellen Sie zum Konfigurieren von FileVault ein [Gerätekonfigurationsprofil](../configuration/device-profile-create.md) für Endpoint Protection unter macOS. Die FileVault-Einstellungen gehören zu den verfügbaren Einstellungskategorien in Endpoint Protection unter macOS.  

Sobald Sie eine Richtlinie für die Geräteverschlüsselung mit FileVault erstellt haben, wird die Richtlinie in zwei Phasen auf die Geräte angewendet. Zuerst wird das Gerät vorbereitet, damit Intune den Wiederherstellungsschlüssel abrufen und sichern kann. Dies wird als Schlüsselhinterlegung bezeichnet. Sobald dieser Vorgang abgeschlossen ist, kann die Datenträgerverschlüsselung beginnen.

![FileVault-Einstellungen](./media/encrypt-devices/filevault-settings.png)

Ausführliche Informationen zur FileVault-Einstellung, die Sie mit Intune verwalten können, finden Sie unter [FileVault](endpoint-protection-macos.md#filevault) im Intune-Artikel für Endpoint Protection-Einstellungen unter macOS.  

### <a name="how-to-configure-macos-filevault"></a>Konfigurieren von FileVault unter macOS 

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und navigieren Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**.  

2. Legen Sie die folgenden Optionen fest:  

   - Plattform: macOS  
   - Profiltyp: Endpoint Protection  

3. Klicken Sie auf **Einstellungen** > **FileVault**.  

4. Klicken Sie dann unter *FileVault* auf **Aktivieren**.  

5. Als *Art des Wiederherstellungsschlüssels* wird nur **Persönlicher Schlüssel** unterstützt.  

   Fügen Sie ggf. eine Meldung hinzu, um den Endbenutzern zu erläutern, wie sie den Wiederherstellungsschlüssel für ihr Gerät abrufen können. Diese Informationen können für Ihre Endbenutzer nützlich sein, wenn Sie die Einstellung für die Rotation persönlicher Wiederherstellungsschlüssel verwenden. Dadurch können regelmäßig automatisch neue Wiederherstellungsschlüssel für die Geräte generiert werden.  

   Beispiel: Melden Sie sich auf einem beliebigen Gerät bei der Intune-Unternehmensportal-Website an, um verlorene oder kürzlich rotierte Wiederherstellungsschlüssel abrufen. Navigieren Sie im Portal zu *Geräte*, wählen Sie das Gerät aus, für das FileVault aktiviert ist, und klicken Sie dann auf *Wiederherstellungsschlüssel abrufen*. Dann wird der aktuelle Wiederherstellungsschlüssel angezeigt.  

6. Konfigurieren Sie die restlichen [FileVault-Einstellungen](endpoint-protection-macos.md#filevault) entsprechend Ihren Geschäftsanforderungen, und wählen Sie anschließend **OK** aus.  

   > [!IMPORTANT]  
   > Es ist ein bekanntes Problem aufgetreten, wenn die Einstellung **Aufforderung bei Abmeldung deaktivieren** auf *Aktivieren* gesetzt ist. Wenn Sie *Aktivieren* festlegen, muss die Einstellung für **Zulässige Anzahl von Umgehungen** auf einen Wert und nicht auf *Nicht konfiguriert* festgelegt werden. Wenn *Nicht konfiguriert* ausgewählt ist, tritt mit dem Profil auf dem Gerät ein Fehler auf. In diesem Szenario meldet das Gerät seine **Profilstatuszusammenfassung** als **Fehler** ohne weitere Details.
   > 
   > Wenn die für **Aufforderung bei Abmeldung deaktivieren** *Nicht konfiguriert* ausgewählt ist, kann für **Zulässige Anzahl von Umgehungen** *Nicht konfiguriert* oder ein Wert festgelegt werden.  
   > 
   > Dieses Problem wird in einem zukünftigen Update behoben. 

7. Schließen Sie die Konfiguration zusätzlicher Einstellungen ab, und speichern Sie anschließend das Profil.  

### <a name="manage-filevault"></a>Verwalten von FileVault  

Sobald Intune ein macOS-Gerät mit FileVault verschlüsselt, können Sie die FileVault-Wiederherstellungsschlüssel anzeigen und verwalten, wenn Sie den Intune-[Verschlüsselungsbericht](encryption-monitor.md) anzeigen.  

Nachdem Intune ein macOS-Gerät mit FileVault verschlüsselt hat, können Sie den persönlichen Wiederherstellungsschlüssel dieses Geräts im Webunternehmensportal auf einem beliebigen Gerät anzeigen. Wählen Sie im Webunternehmensportal das verschlüsselte macOS-Gerät aus, und wählen Sie anschließend „Wiederherstellungsschlüssel abrufen“ als Remotegeräteaktion aus. 

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-Verschlüsselung für Windows 10  

Verwenden Sie Intune, um die BitLocker-Laufwerkverschlüsselung auf Geräten unter Windows 10 zu konfigurieren. Rufen Sie dann im Intune-Verschlüsselungsbericht die Verschlüsselungsdetails zu diesen Geräten ab. Sie können über Ihre Geräte wie bei Azure Active Directory (Azure AD) auch auf wichtige Informationen zu BitLocker zugreifen.  

BitLocker ist auf Geräten verfügbar, auf denen **Windows 10 oder höher** ausgeführt wird.  

Erstellen Sie zum Konfigurieren von BitLocker ein [Gerätekonfigurationsprofil](../configuration/device-profile-create.md) für Endpoint Protection für Windows 10 oder höher. Die BitLocker-Einstellungen befinden sich bei Endpoint Protection unter Windows 10 unter „Windows-Verschlüsselungseinstellungen“.    

![BitLocker-Einstellungen](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Konfigurieren von BitLocker unter Windows 10  

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und navigieren Sie zu „Gerätekonfiguration“ > „Profile“ > „Profil erstellen“.  

2. Legen Sie die folgenden Optionen fest:  
   - Plattform: Windows 10 und höher  
   - Profiltyp: Endpoint Protection  

3. Klicken Sie auf **Einstellungen** > **Windows-Verschlüsselung**.

4. Konfigurieren Sie die Einstellungen für BitLocker entsprechend Ihren Geschäftsanforderungen, und klicken Sie dann auf **OK**.  

5. Schließen Sie die Konfiguration zusätzlicher Einstellungen ab, und speichern Sie anschließend das Profil.  

### <a name="manage-bitlocker"></a>Verwalten von BitLocker  

Sobald Intune ein Windows 10-Gerät mit BitLocker verschlüsselt, können Sie die BitLocker-Wiederherstellungsschlüssel im Intune-[Verschlüsselungsbericht](encryption-monitor.md) einsehen und abrufen.  

## <a name="next-steps"></a>Nächste Schritte  

Erstellen einer [Gerätekonformitätsrichtlinie](compliance-policy-create-windows.md)  

Verwenden Sie den Verschlüsselungsbericht, um Folgendes zu verwalten:  
- [BitLocker-Wiederherstellungsschlüssel](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault-Wiederherstellungsschlüssel](encryption-monitor.md#filevault-recovery-keys)

Überprüfen Sie die Verschlüsselungseinstellungen, die Sie mit Intune für Folgendes konfigurieren können:  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
