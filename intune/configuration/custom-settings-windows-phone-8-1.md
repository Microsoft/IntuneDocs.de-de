---
title: 'Hinzufügen von benutzerdefinierten Einstellungen für Windows Phone 8.1-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie ein benutzerdefinierten Profils zur Verwendung der OMA-URI-Einstellungen für Windows Phone 8.1-Geräte in Microsoft Intune hinzu, oder erstellen Sie ein solches Profil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6807caad60eb492324f37e0c406b44a4052589e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735011"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Verwenden von benutzerdefinierten Einstellungen für Windows Phone 8.1-Geräte in Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für Windows Phone 8.1-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Benutzerdefinierte Windows Phone 8.1-Profile verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Konfigurieren verschiedener Features. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features auf dem Gerät zu steuern. In [Windows Phone 8,1 MDM-protokolldokumentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) sind die Einstellungen aufgeführt.

In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Profil für Windows Phone 8.1-Geräte erstellen. 

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `windows phone custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform:** Wählen Sie **Windows Phone 8.1** aus.
    - **Profiltyp:** Wählen Sie **Benutzerdefiniert** aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen einfacher identifizieren können.
    - **Beschreibung:** Geben Sie eine Beschreibung, die eine Übersicht über die Einstellung bietet, und andere relevante Informationen ein, die Ihnen die Suche nach dem Profil erleichtern.
    - **OMA-URI** (Groß-/Kleinschreibung beachten): Geben Sie den OMA-URI an, den Sie als Einstellung verwenden möchten.
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

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden Windows 8.1 Phone-Geräte daran gehindert, Mobilfunknetze zu ändern, wenn Sie außerhalb des Fracht Bereichs des Fracht Bereichs unterwegs sind.

- **Name**: Mobilfunk-Datenroaming zulassen
- **Beschreibung**: zulassen oder ablehnen von Mobil funkdatenroaming
- **OMA-URI** (case sensitive): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Datentyp**: Ganzzahl
- **Wert**: 0

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen zum Erstellen eines benutzerdefinierten Profils finden Sie unter [Windows 10-Geräte](../custom-settings-windows-10.md).
