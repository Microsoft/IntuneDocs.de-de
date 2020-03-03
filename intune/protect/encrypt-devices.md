---
title: Verschlüsseln von Geräten mit der von Plattformen unterstützten Verschlüsselungsmethode
titleSuffix: Microsoft Intune
description: Verschlüsseln Sie Geräte mithilfe von integrierten Verschlüsselungsmethoden wie BitLocker oder FileVault, und verwalten Sie die Wiederherstellungsschlüssel für diese verschlüsselten Geräte über das Intune-Portal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a5c844377dcd69b6caf5ef9f72fcb8dbb4ef8bd0
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609313"
---
# <a name="use-device-encryption-with-intune"></a>Verwenden der Geräteverschlüsselung mit Intune

Verwenden Sie Intune, um Geräte mit integrierter Laufwerk- oder Datenträgerverschlüsselung zu verwalten, damit die Daten auf Ihren Geräten geschützt werden.

Konfigurieren Sie die Datenträgerverschlüsselung als Teil eines Gerätekonfigurationsprofils für Endpoint Protection. Die folgenden Plattformen und Verschlüsselungstechnologien werden von Intune unterstützt:

- macOS: FileVault
- Windows 10 und höher: BitLocker

Intune beinhaltet auch einen integrierten [Verschlüsselungsbericht](encryption-monitor.md), in dem Details zum Verschlüsselungsstatus Ihrer verwalteten Geräte angezeigt werden.

## <a name="filevault-encryption-for-macos"></a>FileVault-Verschlüsselung für macOS

Verwenden Sie Intune, um die FileVault-Datenträgerverschlüsselung auf macOS-Geräten zu konfigurieren. Verwenden Sie anschließend den Intune-Verschlüsselungsbericht, um die Verschlüsselungsdetails für diese Geräte anzuzeigen und Wiederherstellungsschlüssel für mit FileVault verschlüsselte Geräte zu verwalten.

Damit FileVault auf dem Gerät funktioniert, ist eine vom Benutzer genehmigte Geräteregistrierung erforderlich. Der Benutzer muss das Verwaltungsprofil manuell anhand von Systemeinstellungen genehmigen, damit die Registrierung als vom Benutzer genehmigt angesehen wird.

FileVault ist ein Verschlüsselungsprogramm für ganze Datenträger, das im Lieferumfang von macOS enthalten ist. Verwenden Sie Intune, um FileVault auf Geräten zu konfigurieren, auf denen **macOS 10.13 oder höher** ausgeführt wird.

Erstellen Sie zum Konfigurieren von FileVault ein [Gerätekonfigurationsprofil](../configuration/device-profile-create.md) für Endpoint Protection unter macOS. Die FileVault-Einstellungen gehören zu den verfügbaren Einstellungskategorien in Endpoint Protection unter macOS.

Sobald Sie eine Richtlinie für die Geräteverschlüsselung mit FileVault erstellt haben, wird die Richtlinie in zwei Phasen auf die Geräte angewendet. Zuerst wird das Gerät vorbereitet, damit Intune den Wiederherstellungsschlüssel abrufen und sichern kann. Dies wird als Schlüsselhinterlegung bezeichnet. Sobald dieser Vorgang abgeschlossen ist, kann die Datenträgerverschlüsselung beginnen.

![FileVault-Einstellungen](./media/encrypt-devices/filevault-settings.png)

Ausführliche Informationen zur FileVault-Einstellung, die Sie mit Intune verwalten können, finden Sie unter [FileVault](endpoint-protection-macos.md#filevault) im Intune-Artikel für Endpoint Protection-Einstellungen unter macOS.

### <a name="permissions-to-manage-filevault"></a>Berechtigungen zum Verwalten von FileVault

Damit Sie FileVault in Intune verwalten können, muss Ihr Konto in Intune über die entsprechenden Berechtigungen für die [rollenbasierte Zugriffssteuerung](../fundamentals/role-based-access-control.md) (RBAC) verfügen.

Im Folgenden sind die FileVault-Berechtigungen aufgelistet, die zur Kategorie der **Remoteaufgaben** gehören, sowie die integrierten RBAC-Rollen für das Erteilen der jeweiligen Berechtigung:
 
- **Get FileVault key** (FileVault-Schlüssel erhalten):
  - Helpdesk-Operator
  - Endpoint security manager (Endpunktsicherheits-Manager)

- **Rotate FileVault key** (FileVault-Schlüssel rotieren)
  - Helpdesk-Operator

### <a name="how-to-configure-macos-filevault"></a>Konfigurieren von FileVault unter macOS

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Legen Sie die folgenden Optionen fest:

   - Plattform: macOS
   - Profiltyp: Endpoint Protection

4. Klicken Sie auf **Einstellungen** > **FileVault**.

5. Klicken Sie dann unter *FileVault* auf **Aktivieren**.

6. Als *Art des Wiederherstellungsschlüssels* wird nur **Persönlicher Schlüssel** unterstützt.

   Fügen Sie ggf. eine Meldung hinzu, um den Endbenutzern zu erläutern, wie sie den Wiederherstellungsschlüssel für ihr Gerät abrufen können. Diese Informationen können für Ihre Endbenutzer nützlich sein, wenn Sie die Einstellung für die Rotation persönlicher Wiederherstellungsschlüssel verwenden. Dadurch können regelmäßig automatisch neue Wiederherstellungsschlüssel für die Geräte generiert werden.

   Beispiel: Melden Sie sich auf einem beliebigen Gerät bei der Intune-Unternehmensportal-Website an, um verlorene oder kürzlich rotierte Wiederherstellungsschlüssel abrufen. Navigieren Sie im Portal zu *Geräte*, wählen Sie das Gerät aus, für das FileVault aktiviert ist, und klicken Sie dann auf *Wiederherstellungsschlüssel abrufen*. Dann wird der aktuelle Wiederherstellungsschlüssel angezeigt.

7. Konfigurieren Sie die restlichen [FileVault-Einstellungen](endpoint-protection-macos.md#filevault) entsprechend Ihren Geschäftsanforderungen, und wählen Sie anschließend **OK** aus.

  8. Schließen Sie die Konfiguration zusätzlicher Einstellungen ab, und speichern Sie anschließend das Profil.  

### <a name="manage-filevault"></a>Verwalten von FileVault

Sobald Intune ein macOS-Gerät mit FileVault verschlüsselt, können Sie die FileVault-Wiederherstellungsschlüssel anzeigen und verwalten, wenn Sie den Intune-[Verschlüsselungsbericht](encryption-monitor.md) anzeigen.

Nachdem Intune ein macOS-Gerät mit FileVault verschlüsselt hat, können Sie den persönlichen Wiederherstellungsschlüssel dieses Geräts im Webunternehmensportal auf einem beliebigen Gerät anzeigen. Wählen Sie im Webunternehmensportal das verschlüsselte macOS-Gerät aus, und wählen Sie anschließend „Wiederherstellungsschlüssel abrufen“ als Remotegeräteaktion aus.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>Abrufen eines persönlichen Wiederherstellungsschlüssels von MEM-verschlüsselten macOS-Geräten

Endbenutzer rufen ihren persönlichen Wiederherstellungsschlüssel (FileVault-Schlüssel) mithilfe der Unternehmensportal-App für iOS ab. Das Gerät mit dem persönlichen Wiederherstellungsschlüssel muss bei Intune registriert und über Intune mit FileVault verschlüsselt sein. Mithilfe der iOS-Unternehmensportal-App können die Endbenutzer eine Webseite öffnen, die den persönlichen FileVault-Wiederherstellungsschlüssel umfasst. Sie können den Wiederherstellungsschlüssel auch aus Intune abrufen, indem Sie **Geräte** > *das verschlüsselte und registrierte macOS-Gerät* > **Wiederherstellungsschlüssel abrufen** auswählen. 

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-Verschlüsselung für Windows 10

Verwenden Sie Intune, um die BitLocker-Laufwerkverschlüsselung auf Geräten unter Windows 10 zu konfigurieren. Rufen Sie dann im Intune-Verschlüsselungsbericht die Verschlüsselungsdetails zu diesen Geräten ab. Sie können über Ihre Geräte wie bei Azure Active Directory (Azure AD) auch auf wichtige Informationen zu BitLocker zugreifen.

BitLocker ist auf Geräten verfügbar, auf denen **Windows 10 oder höher** ausgeführt wird.

Erstellen Sie zum Konfigurieren von BitLocker ein [Gerätekonfigurationsprofil](../configuration/device-profile-create.md) für Endpoint Protection für Windows 10 oder höher. Die BitLocker-Einstellungen befinden sich bei Endpoint Protection unter Windows 10 unter „Windows-Verschlüsselungseinstellungen“.

![BitLocker-Einstellungen](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Konfigurieren von BitLocker unter Windows 10

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Legen Sie die folgenden Optionen fest:

   - Plattform: Windows 10 und höher
   - Profiltyp: Endpoint Protection

4. Klicken Sie auf **Einstellungen** > **Windows-Verschlüsselung**.

5. Konfigurieren Sie die Einstellungen für BitLocker entsprechend Ihren Geschäftsanforderungen, und klicken Sie dann auf **OK**.

6. Schließen Sie die Konfiguration zusätzlicher Einstellungen ab, und speichern Sie anschließend das Profil.

### <a name="manage-bitlocker"></a>Verwalten von BitLocker

Sobald Intune ein Windows 10-Gerät mit BitLocker verschlüsselt, können Sie die BitLocker-Wiederherstellungsschlüssel im Intune-[Verschlüsselungsbericht](encryption-monitor.md) einsehen und abrufen.

### <a name="rotate-bitlocker-recovery-keys"></a>Drehen von BitLocker-Wiederherstellungsschlüsseln

Sie können mithilfe einer Intune-Geräteaktion über eine Remoteverbindung den BitLocker-Wiederherstellungsschlüssel eines Geräts mit Windows 10, Version 1909 oder höher drehen.

#### <a name="prerequisites"></a>Voraussetzungen

Geräte müssen die folgenden Voraussetzungen erfüllen, damit der BitLocker-Wiederherstellungsschlüssel gedreht werden kann:

- Sie müssen Windows 10, Version 1909 oder höher ausführen.

- Auf in Azure AD und Hybrid eingebundenen Geräten muss die Schlüsselrotation unterstützt werden:

  - **Rotation von clientgesteuerten Wiederherstellungskennwörtern**

  Diese Einstellung finden Sie unter *Windows-Verschlüsselung* als Teil einer Gerätekonfigurationsrichtlinie für Windows 10 Endpoint Protection.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>So drehen Sie den BitLocker-Wiederherstellungsschlüssel

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Klicken Sie auf **Geräte** > **Alle Geräte**.

3. Wählen Sie in der Liste der von Ihnen verwalteten Geräte ein Gerät aus, und klicken Sie erst auf **Mehr** und anschließend auf die Remotegeräteaktion **BitLocker-Schlüsselrotation**.

## <a name="next-steps"></a>Nächste Schritte

Erstellen Sie eine [Gerätekonformitätsrichtlinie](compliance-policy-create-windows.md).

Verwenden Sie den Verschlüsselungsbericht, um Folgendes zu verwalten:

- [BitLocker-Wiederherstellungsschlüssel](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault-Wiederherstellungsschlüssel](encryption-monitor.md#filevault-recovery-keys)

Überprüfen Sie die Verschlüsselungseinstellungen, die Sie mit Intune für Folgendes konfigurieren können:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
