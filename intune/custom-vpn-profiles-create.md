---
title: Erstellen von benutzerdefinierten VPN-Profilen mit Microsoft Intune
titleSuffix: ''
description: Verwenden Sie benutzerdefinierte Konfigurationen, um VPN-Profile in Intune zu erstellen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 28ed8902a11500b195fff839d59b90c16af6e743
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>Erstellen von benutzerdefinierten VPN-Profilen in Microsoft Intune

Sie können benutzerdefinierte Intune-Konfigurationsrichtlinien verwenden, um VPN-Profile für die folgenden Plattformen zu erstellen:

* Android 4 und höher
* Registrierte Geräte unter Windows 8.1 und höher
* Windows Phone 8.1 und höher
* Registrierte Geräte unter Windows 10 Desktop 
* Windows 10 Mobile

Dieser Richtlinientyp kann hilfreich sein, wenn die standardmäßigen Intune-VPN-Richtlinien nicht die Einstellungen enthalten, die Sie verwenden möchten.

## <a name="to-create-a-custom-configuration-policy"></a>So erstellen Sie eine benutzerdefinierte Konfigurationsrichtlinie:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonfiguration**.
2. Klicken Sie im Bereich **Gerätekonfiguration** im Abschnitt **Verwalten** auf **Profile**.
5. Klicken Sie im Bereich „Profile“ auf **Profil erstellen**.
6. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine **Beschreibung** für das VPN-Profil ein.
7. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie VPN-Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die benutzerdefinierte Geräteeinstellungen auswählen:
    - **Android**
    - **Android for Work**
    - **iOS** (konfiguriert mit einer Datei, die Sie aus Apple Configurator exportiert haben)
    - **macOS** (konfiguriert mit einer Datei, die Sie aus Apple Configurator exportiert haben)
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Benutzerdefiniert** aus.
7. Klicken Sie im Bereich **Custom OMA-URI Settings** (Benutzerdefinierte OMA-URI-Einstellungen) für jede URI-Einstellung, die Sie angeben möchten, auf **Hinzufügen**, geben Sie die geforderten Informationen ein, und klicken Sie dann auf **OK**. Beispiel:

   ![Dialogfeld „Benutzerdefinierte VPN-Profilkonfiguration“](./media/Intune_Add_VPN_URI.png)

4.  Nachdem Sie alle erforderlichen URI-Einstellungen eingegeben haben, klicken Sie auf **OK** und dann im Bereich **Profil erstellen** auf **Erstellen**.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.
Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.




