---
title: Konfigurieren von Zertifikatprofilen
description: Erfahren Sie, wie Sie ein Intune-Zertifikatprofil erstellen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6230fbc50ae79702cfd938f158d2961b5d720c9
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="configure-intune-certificate-profiles"></a>Konfigurieren von Intune-Zertifikatprofilen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Nachdem Sie Ihre Infrastruktur und Zertifikate konfiguriert haben (gemäß der Beschreibung in [Konfigurieren der Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) oder [Konfigurieren der Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)), können Sie Zertifikatprofile erstellen. Gehen Sie dazu folgendermaßen vor:

- **Aufgabe 1**: Exportieren des Zertifikats der vertrauenswürdigen Stamm-CA
- **Aufgabe 2**: Erstellen von vertrauenswürdigen Zertifikatprofilen
- **Aufgabe 3**: Erstellen eines von zwei Zertifikatprofiltypen:
  - SCEP-Zertifikatprofile
  - PFX-Zertifikatprofile

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**Aufgabe 1**: Exportieren des Zertifikats der vertrauenswürdigen Stamm-CA
Exportieren Sie das Zertifikat vertrauenswürdigen Stammzertifizierungsstelle als **CER**-Datei aus der ausstellenden Zertifizierungsstelle oder von einem beliebigen Gerät, das die ausstellende Zertifizierungsstelle als vertrauenswürdig erachtet. Exportieren Sie auf keinen Fall den privaten Schlüssel.

Sie importieren dieses Zertifikat, wenn Sie ein vertrauenswürdiges Zertifikatprofil einrichten.

## <a name="task-2-create-trusted-certificate-profiles"></a>**Aufgabe 2**: Erstellen von vertrauenswürdigen Zertifikatprofilen
Sie müssen ein vertrauenswürdiges Zertifikatprofil erstellen, bevor Sie ein Simple Certificate Enrollment Protocol- oder ein PKCS #12-Zertifikatprofil erstellen können (d.h. SCEP- oder PFX-Zertifikatprofile). Sie benötigen ein vertrauenswürdiges Zertifikatprofil und ein SCEP- oder PFS-Profil für jede Plattform für mobile Geräte.

### <a name="to-create-a-trusted-certificate-profile"></a>So erstellen Sie ein vertrauenswürdiges Zertifikatprofil

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) **Richtlinie** &gt; **Richtlinie hinzufügen** und anschließend eine Geräteplattform aus. Sie können ein vertrauenswürdiges Zertifikatprofil für diese Geräte erstellen:

-  Android 4 und höher

-  Android for Work

-  iOS 7.1 und höher

-  Mac OS X 10.9 und höher

-  Windows 8.1 und höher

-  Windows Phone 8.1 und höher

2.  Fügen Sie eine Richtlinie für ein **vertrauenswürdiges Zertifikatprofil** hinzu.

    Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Geben Sie die angeforderten Informationen ein, um die Profileinstellungen vertrauenswürdiger Zertifikate für Android, iOS, Mac OS X, Windows 8.1 oder Windows Phone 8.1 zu konfigurieren.
4.  Importieren Sie in der Einstellung **Zertifikatdatei** das Zertifikat der vertrauenswürdigen Stamm-CA (CER-Datei), das Sie aus der ausstellenden Zertifizierungsstelle exportiert haben. Die Einstellung **Zielspeicher** gilt nur für Geräte mit Windows 8.1 und höher und auch nur, wenn das Gerät über mehr als einen Zertifikatspeicher verfügt.

4.  Wählen Sie **Richtlinie speichern** aus.

Die neue Richtlinie wird im Arbeitsbereich **Richtlinie** angezeigt. Sie können sie nun bereitstellen.

> [!NOTE]
>
> Android- und Android for Work-Geräte zeigen eine Benachrichtigung an, dass ein Drittanbieter ein vertrauenswürdiges Zertifikat installiert hat.


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**Aufgabe 3**: Erstellen von SCEP- oder PFX-Zertifikatprofilen
Nachdem Sie ein Profil des vertrauenswürdigen Zertifizierungsstellenzertifikats erstellt haben, erstellen Sie SCEP- oder PFX-Zertifikatprofile für jede Plattform, die Sie verwenden möchten. Wenn Sie ein SCEP-Zertifikatprofil erstellen, müssen Sie ein vertrauenswürdiges Zertifikatprofil für dieselbe Plattform angeben. Auf diese Weise werden die beiden Zertifikatprofile verknüpft. Sie müssen jedes Profil trotzdem separat bereitstellen.

### <a name="to-create-an-scep-certificate-profile"></a>So erstellen Sie ein SCEP-Zertifikatprofil

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) **Richtlinie** &gt; **Richtlinie hinzufügen** und anschließend eine Geräteplattform aus.  Sie können ein SCEP-Zertifikatprofil für diese Geräte erstellen:

-  Android 4 und höher

-  Android for Work

-  iOS 7.1 und höher

-  Mac OS X 10.9 und höher

-  Windows 8.1 und höher

-  Windows Phone 8.1 und höher

2.  Fügen Sie eine Richtlinie für ein **SCEP-Zertifikatprofil** hinzu.

    Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Befolgen Sie die Anweisungen auf der Profilkonfigurationsseite, um die SCEP-Zertifikatprofileinstellungen zu konfigurieren.
    > [!NOTE]
    >
    > Wählen Sie unter **Format des Antragstellernamens** die Option **Benutzerdefiniert** aus, um ein benutzerdefiniertes Format für den Antragstellernamen einzugeben (nur in iOS-Profilen).
    >
    > Die beiden derzeit für das benutzerdefinierte Format unterstützten Variablen sind `Common Name (CN)` und `Email (E)`. Durch eine Kombination dieser Variablen mit statischen Zeichenfolgen können Sie ein benutzerdefiniertes Format wie dieses für den Antragstellernamen erstellen:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > In diesem Beispiel hat der Administrator ein Format für den Antragstellernamen erstellt, das zusätzlich zu den Variablen `CN` und `E` entsprechende Zeichenfolgen für Organisationseinheit (OU), Organisation (O), Ort (L), Bundesland/Kanton (ST) und Land (C) verwendet. Die [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)-Funktion listet unterstützte Zeichenfolgen auf.

4.  Wählen Sie **Richtlinie speichern** aus.

Die neue Richtlinie wird im Arbeitsbereich **Richtlinie** angezeigt. Sie können sie nun bereitstellen.

### <a name="to-create-a-pfx-certificate-profile"></a>So erstellen Sie ein PFX-Zertifikatprofil

1.  Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) **Richtlinie** &gt; **Richtlinie hinzufügen** und anschließend eine Geräteplattform aus. PFX-Zertifikate werden für folgende Betriebssysteme unterstützt:
  - Android 4 und höher
  - Android for Work
  - Windows 10 und höher
  - Windows Phone 10 und höher
  - iOS 8.0 und höher)    


2.  Fügen Sie eine Richtlinie für ein **PFX-Zertifikatprofil** hinzu.
      Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Geben Sie die Informationen ein, die auf dem Richtlinienformular angefordert werden.
4.  Wählen Sie **Richtlinie speichern** aus.

Die neue Richtlinie wird im Arbeitsbereich **Richtlinie** angezeigt. Sie können sie nun bereitstellen.

## <a name="deploy-certificate-profiles"></a>Bereitstellen von Zertifikatprofilen
Wenn Sie Zertifikatprofile bereitstellen, wird die Zertifikatdatei aus dem Profil des vertrauenswürdigen Zertifizierungsstellenzertifikats auf dem Gerät installiert. Das Gerät verwendet das SCEP- oder PFX-Zertifikatprofil, um eine Zertifikatanforderung zu erstellen.

Zertifikatprofile werden nur auf den Geräten installiert, auf denen die beim Erstellen des Profils verwendete Plattform ausgeführt wird.

-   Sie können Zertifikatprofile für Benutzer- oder Gerätesammlungen bereitstellen.

    > [!TIP]
    > Damit Zertifikate möglichst schnell nach deren Registrierung auf Geräten veröffentlicht werden können, stellen Sie das Zertifikatprofil lieber für eine Benutzergruppe bereit (und nicht für eine Gerätegruppe). Wenn Sie es für eine Gerätegruppe bereitstellen, muss eine vollständige Geräteregistrierung stattfinden, bevor das Gerät Richtlinien empfängt.

-   Obwohl Sie jedes Profil separat bereitstellen, müssen Sie auch die vertrauenswürdige Stamm-CA und die SCEP- oder PFX-Profile bereitstellen. Andernfalls schlägt die SCEP- oder PFX-Zertifikatrichtlinie fehl.

Stellen Sie Zertifikatprofile auf die gleiche Weise bereit wie andere Richtlinien für Intune:

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie anschließend **Bereitstellung verwalten** aus.
2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:
    -   **So stellen Sie die Richtlinie bereit**: Wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und wählen Sie anschließend **Hinzufügen** &gt; **OK** aus.
    -   **So schließen Sie das Dialogfeld, ohne die Richtlinie bereitzustellen**: Klicken Sie auf **Abbrechen**.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Richtlinienliste anzeigen.

### <a name="next-steps"></a>Nächste Schritte

Erfahren Sie nun, wie Sie mithilfe von Zertifikaten E-Mail-, WLAN- und VPN-Profile schützen können.

-  [Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [WLAN-Verbindungen in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [VPN-Verbindungen in Microsoft Intune](vpn-connections-in-microsoft-intune.md)
