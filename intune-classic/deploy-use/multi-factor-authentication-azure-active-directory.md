---
title: Mehrstufige Authentifizierung für Intune-Geräteregistrierungen
description: Anfordern der mehrstufigen Authentifizierung in Azure AD für die Geräteregistrierung.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 62568a307b5e28c9543a8bb73271da2f55c44ae4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31014128"
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Multi-Factor Authentication für Intune-Geräteregistrierungen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune integriert die mehrstufige Authentifizierung (MFA) von Azure AD, damit Sie Ihre Unternehmensressourcen über die Geräteregistrierung sichern können.

MFA funktioniert, da zwei oder mehr der folgenden Überprüfungsmethoden erforderlich sind: 

- Etwas, das Sie kennen (normalerweise ein Kennwort oder eine PIN)
- Etwas, das Sie besitzen (ein vertrauenswürdiges Gerät, das nicht auf einfache Weise dupliziert werden kann, z.B. ein Telefon)
- Etwas, das einzigartig für Sie ist (Biometrie)

MFA wird für Geräte unter iOS, Android, Windows 8.1 oder höher und Windows Phone 8.1 oder höher unterstützt.

> [!NOTE]
> In älteren Versionen von Configuration Manager (vor Release 1610) wird in der Configuration Manager-Verwaltungskonsole noch immer die MFA-Einstellung angezeigt. MFA kann nicht über die Configuration Manager-Verwaltungskonsole konfiguriert werden. Konfigurieren Sie MFA wie in diesem Thema beschrieben.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Konfigurieren von Intune für das Anfordern der mehrstufigen Authentifizierung bei der Geräteregistrierung
Befolgen Sie die folgenden Schritte, um MFA anzufordern, wenn ein Gerät registriert wird:

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen beim [Microsoft Azure-Portal](https://manage.windowsazure.com) an.
2. Wählen Sie Ihren Mandanten.
2. Wählen Sie die Registerkarte **Anwendungen**. Sie sehen eine Liste der Dienste, für die Sie Azure AD-Sicherheitsfeatures konfigurieren können.
3. Wählen Sie **Microsoft Intune-Registrierung**.
4. Wählen Sie **Konfigurieren** aus. 
5. Unter **Mehrstufige Authentifizierung und standortbasierte Zugriffsregeln** haben Sie folgende Möglichkeiten:
    
    -  Aktivieren der Zugriffsregeln
    -  Auswählen, ob die Regeln für alle Benutzer oder für bestimmte Azure AD-Sicherheitsgruppen gelten sollen
    -  Anfordern der mehrstufigen Authentifizierung für die Registrierung aller Geräte
    -  Anfordern der mehrstufigen Authentifizierung für die Registrierung, wenn sich das Gerät nicht am Arbeitsplatz befindet
    -  Wählen Sie **Zugriff auf Unternehmensressourcen blockieren**, um die Registrierung eines Geräts zu verhindern, wenn es nicht mit dem Unternehmensnetzwerk verbunden ist. 
4. Sie können auch auf den Link klicken, um **Ihre Firmennetzwerkadresse zu definieren oder zu bearbeiten** und die Anforderungen der Geräteregistrierung an die Netzwerkkonnektivität zu konfigurieren.

> [!IMPORTANT]
> 
> Konfigurieren Sie keine **gerätebasierten Zugriffsregeln** für die Microsoft Intune-Registrierung.
