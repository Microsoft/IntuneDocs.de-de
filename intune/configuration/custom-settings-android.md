---
title: 'Hinzufügen von benutzerdefinierten Einstellungen zu Android-Geräten in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Hinzufügen oder Erstellen eines benutzerdefinierten Profils für Android-Geräte zum Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel, Erstellen eines Profils für Pro-App-VPN, oder Erlauben bzw. Blockieren von Apps für Samsung KNOX Standard-Geräte in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17f0b30d0a8c706a7fdff1c7da722eeccdf097eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495789"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Verwenden benutzerdefinierter Einstellungen für Android-Geräte in Microsoft Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für Android-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Benutzerdefinierte Android-Profile verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Konfigurieren verschiedener Features auf Android-Geräten. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features festzulegen.

Mithilfe eines benutzerdefinierten Profils können Sie folgende Android-Einstellungen konfigurieren. Die folgenden Einstellungen sind nicht in Intune integriert:

- [Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel](/intune/wi-fi-profile-shared-key)
- [Erstellen eines Pro-App-VPN-Profils](/intune/android-pulse-secure-per-app-vpn)
- [Zulassen und Blockieren von Apps für Samsung KNOX Standard-Geräte](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Nur die aufgeführten Einstellungen können in einem benutzerdefinierten Profil konfiguriert werden. Android-Geräte stellen keine vollständige Liste der OMA-URI-Einstellungen zur Verfügung, die Sie konfigurieren können. Wenn Sie weitere Einstellungen hinzufügen möchten, stimmen Sie auf der [Intune Uservoice-Website](https://microsoftintune.uservoice.com/forums/291681-ideas) für mehr Einstellungen.

In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Profil für Android-Geräte erstellen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `android custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform:** Wählen Sie **Android**.
    - **Profiltyp:** Wählen Sie **Benutzerdefiniert** aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie diese leicht finden können.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **OMA-URI:** Geben Sie den OMA-URI ein, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, den Sie für diese OMA-URI-Einstellung verwenden möchten. Folgende Optionen sind verfügbar:

      - Zeichenfolge
      - Zeichenfolge (XML-Datei)
      - Datum und Uhrzeit
      - Ganze Zahl
      - Gleitkomma
      - Boolesch
      - Base64 (Datei)

    - **Wert:** Geben Sie den gewünschten Datenwert an, der dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll. Der Wert hängt vom ausgewählten Datentyp ab. Beim Datentyp **Datum und Uhrzeit** wählen Sie den Wert beispielsweise aus einer Datumsauswahl aus.

    Wenn Sie einige Einstellungen hinzugefügt haben, können Sie auf **Exportieren** klicken. Wenn Sie auf **Exportieren** klicken, wird eine Liste aller hinzugefügten Werte in einer Datei mit durch Trennzeichen getrennten Werten (CSV) erstellt.

5. Klicken Sie auf **OK**, um die Änderungen zu speichern. Fügen Sie nach Bedarf weitere Einstellungen hinzu. 
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Dann wird das Profil erstellt und in der Liste **Gerätekonfiguration > Profile** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen finden Sie im [Artikel zum Erstellen eines Profils auf einem Android Enterprise-Gerät](custom-settings-android-for-work.md).
