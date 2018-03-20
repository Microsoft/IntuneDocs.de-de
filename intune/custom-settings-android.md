---
title: "Hinzufügen von benutzerdefinierten Einstellungen für Android-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation"
description: "Hinzufügen oder Erstellen eines benutzerdefinierten Profils für Android-Geräte zum Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel, Erstellen eines Profils für Pro-App-VPN, oder Erlauben bzw. Blockieren von Apps für Samsung KNOX Standard-Geräte in Microsoft Intune"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa105cc96cd0fa7d8c6beb32cdb80b7782d9828c
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="custom-settings-for-android-devices---intune"></a>Benutzerdefinierte Einstellungen für Android-Geräte in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Benutzerdefinierte Profile verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Konfigurieren verschiedener Features auf Android-Geräten. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features auf dem Gerät zu steuern.

Mithilfe eines benutzerdefinierten Profils können Sie folgende Android-Einstellungen konfigurieren. Diese Einstellungen werden nicht in den Intune-Richtlinien enthalten:

- [Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel](/intune/wi-fi-profile-shared-key)
- [Erstellen eines Pro-App-VPN-Profils](/intune/android-pulse-secure-per-app-vpn)
- [Zulassen und Blockieren von Apps für Samsung KNOX Standard-Geräte](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Nur die aufgeführten Einstellungen können von diesem Profiltyp konfiguriert werden. Android-Geräte stellen keine vollständige Liste der OMA-URI-Einstellungen zur Verfügung, die Sie konfigurieren können. Wenn Sie weitere Einstellungen hinzufügen möchten, stimmen Sie auf der [Intune Uservoice-Website](https://microsoftintune.uservoice.com/forums/291681-ideas) für mehr Einstellungen.

## <a name="custom-profile-settings-for-android-devices"></a>Benutzerdefinierte Profileinstellungen für Android-Geräte

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. 
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**.
3. Erstellen Sie ein benutzerdefiniertes Profil mithilfe der Android-Plattform. Eine exemplarische Vorgehensweise finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
4. Klicken Sie unter **Custom OMA-URI Settings** (Benutzerdefinierte OMA-URI-Einstellungen) auf **Hinzufügen** und dann auf **Zeile hinzufügen**.
5. Geben Sie die folgenden Eigenschaften ein:

  - **Name**: Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie diese leicht finden können.
  - **Beschreibung**: Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
  - **Datentyp**: Geben Sie den Datentyp ein, den Sie für diese OMA-URI-Einstellung verwenden möchten. Wählen Sie aus **Zeichenfolge**, **Zeichenfolge (XML)**, **Datum und Uhrzeit**, **ganze Zahl**, **Gleitkomma** oder **Boolesch** aus.
  - **OMA-URI**: Geben Sie den gewünschten OMA-URI ein.
  - **Wert:** Geben Sie den gewünschten Wert an, der dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll.

6. Klicken Sie auf **OK**, um die Änderungen zu speichern. Fügen Sie nach Bedarf weitere Einstellungen hinzu.

## <a name="next-steps"></a>Nächste Schritte

Das Profil wird erstellt und wird in der Liste angezeigt, wenn Sie die Einstellungen abschließen. Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).
