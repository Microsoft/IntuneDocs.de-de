---
title: 'Hinzufügen von benutzerdefinierten Einstellungen zu Android-Geräten in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Hinzufügen oder Erstellen eines benutzerdefinierten Profils für Android-Geräte zum Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel, Erstellen eines Profils für Pro-App-VPN, oder Erlauben bzw. Blockieren von Apps für Samsung KNOX Standard-Geräte in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
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
ms.openlocfilehash: 8137a806598facd540781702b1c2c359e89d6bda
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206787"
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

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein guter Profilname ist beispielsweise **Android Custom profile**.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Android** aus.
    - **Profiltyp**: Wählen Sie **Benutzer**definiert aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie diese leicht finden können.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **OMA-URI**: Geben Sie den OMA-URI ein, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, den Sie für diese OMA-URI-Einstellung verwenden möchten. Folgende Optionen sind verfügbar:

      - Zeichenfolge
      - Zeichenfolge (XML-Datei)
      - Datum und Uhrzeit
      - Ganze Zahl
      - Gleitkomma
      - Boolesch
      - Base64 (Datei)

    - **Wert**: Geben Sie den gewünschten Datenwert an, der dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll. Der Wert hängt vom ausgewählten Datentyp ab. Beim Datentyp **Datum und Uhrzeit** wählen Sie den Wert beispielsweise aus einer Datumsauswahl aus.

    Wenn Sie einige Einstellungen hinzugefügt haben, können Sie auf **Exportieren** klicken. Wenn Sie auf **Exportieren** klicken, wird eine Liste aller hinzugefügten Werte in einer Datei mit durch Trennzeichen getrennten Werten (CSV) erstellt.

5. Klicken Sie auf **OK**, um die Änderungen zu speichern. Fügen Sie nach Bedarf weitere Einstellungen hinzu.
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Das Profil wird erstellt und in der Liste **Gerätekonfiguration > Konfigurationsprofile** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Erstellen Sie ein [benutzerdefiniertes Profil auf Android-Unternehmens Geräten](custom-settings-android-for-work.md).
