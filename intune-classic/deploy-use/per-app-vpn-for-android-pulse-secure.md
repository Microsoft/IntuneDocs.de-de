---
title: App-bezogenes VPN für Android mithilfe von Pulse Secure
description: Sie können ein App-bezogenes VPN-Profil für Android-Geräte erstellen, die von Intune verwaltet werden.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fb4b6ad21b83d6ed2844238091f2e24e0d15cea5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="use-a-custom-policy-to-create-a-per-app-vpn-profile-for-android-devices"></a>Verwenden einer benutzerdefinierten Richtlinie zum Erstellen eines Profils für ein App-bezogenes VPN für Android-Geräte

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können ein App-bezogenes VPN-Profil für Android 5.0-Geräte oder höher erstellen, die von Intune verwaltet werden. Erstellen Sie zunächst ein VPN-Profil, das den Pulse Secure- oder Citrix-Verbindungstyp verwendet. Erstellen Sie anschließend eine benutzerdefinierte Konfigurationsrichtlinie, die das VPN-Profil angegebenen Apps zuordnet. 

Nachdem Sie die Richtlinie auf Ihrem Android-Gerät oder für Ihre Benutzergruppe bereitstellen, sollten Benutzer den Pulse Secure- oder Citrix-VPN starten. Pulse Secure erlaubt es dann nur den angegebenen Apps, die offene VPN-Verbindung zu nutzen.

> [!NOTE]
>
> Es werden nur die Verbindungstypen „Pulse Secure“ und „Citrix“ für dieses Profil unterstützt.


### <a name="step-1-create-a-vpn-profile"></a>Schritt 1: Erstellen eines VPN-Profils

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** > **Richtlinie hinzufügen**.
2. Wählen Sie eine Vorlage für die neue Richtlinie aus, indem Sie **Android** erweitern und anschließend **VPN-Profil (Android 4 und höher)** auswählen.
3. Wählen Sie in der Vorlage für **Verbindungstyp** die Option **Pulse Secure** oder **Citrix** aus.
4. Stellen Sie das VPN-Profil fertig, und speichern Sie es. Weitere Informationen zu VPN-Profilen finden Sie unter [VPN-Verbindungen](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Notieren Sie den Wert für **VPN-Verbindungsname (wird Benutzern angezeigt)**, den Sie beim Erstellen des VPN-Profils angegeben haben. Dieser wird im nächsten Schritt benötigt. Beispiel: **MeineApp-VPN-Profil**.

### <a name="step-2-create-a-custom-configuration-policy"></a>Schritt 2: Erstellen einer benutzerdefinierten Konfigurationsrichtlinie

   1. Wählen Sie in der Intune-Verwaltungskonsole **Richtlinie** > **Richtlinie hinzufügen** > **Android** > **Benutzerdefinierte Konfiguration** > **Richtlinie erstellen** aus.
   2. Geben Sie einen Namen für die Richtlinie ein.
   3. Wählen Sie unter **OMA-URI-Einstellungen** **Hinzufügen** aus.
   4. Geben Sie einen Einstellungsnamen ein.
   5. Geben Sie für **Datentyp** **Zeichenfolge** an.
   6. Geben Sie für **OMA-URI** diese Zeichenfolge an: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**. *Name* ist der Name des VPN-Profils, den Sie in Schritt 1 notiert haben. Bei unserem Beispiel lautet die Zeichenfolge **./Vendor/MSFT/VPN/Profile/MeineApp-VPN-Profil/PackageList**.
   7.   Erstellen Sie für **Wert** eine durch Semikolons getrennte Liste der Pakete, die dem Profil zugeordnet werden sollen. Wenn z.B. Excel und der Google-Browser Chrome die VPN-Verbindung verwenden sollen, geben Sie Folgendes ein: **com.microsoft.office.excel;com.android.chrome**.

![Beispiel einer benutzerdefinierten Richtlinie für ein App-bezogenes VPN für Android](./media/android_per_app_vpn_oma_uri.png)

#### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Festlegen, ob Ihre App-Liste eine Positivliste (Whitelist) oder eine Negativliste (Blacklist) sein soll (optional)
  Sie können eine Liste von Apps angeben, die die VPN-Verbindung *nicht* verwenden können, indem Sie den Wert **BLACKLIST** verwenden. Alle anderen Apps stellen über das VPN eine Verbindung her.
Alternativ können Sie den Wert **WHITELIST** verwenden, um eine Liste von Apps anzugeben, die die VPN-Verbindung verwenden *können*. Apps, die sich nicht auf der Liste befinden, werden keine Verbindung über das VPN herstellen.
  1.    Wählen Sie unter **OMA-URI-Einstellungen** **Hinzufügen** aus.
  2.    Geben Sie einen Einstellungsnamen ein.
  3.    Geben Sie für **Datentyp** **Zeichenfolge** an.
  4.    Verwenden Sie für **OMA-URI** diese Zeichenfolge: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**. *Name* ist der Name des VPN-Profils, den Sie in Schritt 1 notiert haben. Bei unserem Beispiel lautet die Zeichenfolge **./Vendor/MSFT/VPN/Profile/MeineApp-VPN-Profil/Mode**.
  5.    Geben Sie für **Wert** entweder **BLACKLIST** oder **WHITELIST** ein.



### <a name="step-3-deploy-both-policies"></a>Schritt 3: Bereitstellen beider Richtlinien

Sie müssen *beide* Richtlinien für die *gleichen* Intune-Gruppen bereitstellen.

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie dann **Bereitstellung verwalten** aus.
2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:
    -   **So stellen Sie die Richtlinie bereit**: Wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und wählen Sie anschließend **Hinzufügen** > **OK** aus.
    -   **So schließen Sie das Dialogfeld, ohne die Richtlinie bereitzustellen**: Wählen Sie **Abbrechen** aus.

Eine Statuszusammenfassung und Warnungen auf der Seite **Übersicht** des Arbeitsbereichs **Richtlinie** identifiziert Probleme mit der Richtlinie, die Ihre Aufmerksamkeit erfordern. Eine Statuszusammenfassung wird im Arbeitsbereich **Dashboard** angezeigt.
