---
title: 'Hinzufügen von benutzerdefinierten Einstellungen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Fügen Sie ein benutzerdefiniertes Profil zur Verwendung der OMA-URI-Einstellungen für Windows 10 in Microsoft Intune hinzu, oder erstellen Sie ein solches Profil. Verwenden Sie ein benutzerdefiniertes Profil, um benutzerdefinierte Einstellung hinzuzufügen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86c822ba197851fe7e05d91ff8aa703fb9fe3811
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842780"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Verwenden von benutzerdefinierten Einstellungen für Windows 10-Geräte in Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für Windows 10-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Benutzerdefinierte Windows 10-Profile verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Konfigurieren verschiedener Features auf Android-Geräten. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features auf dem Gerät zu steuern. 

Windows 10 stellt viele CSP-Einstellungen zur Verfügung, z.B. den [Richtlinienkonfigurationsdienst-Anbieter (Policy Configuration Service Provider, Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows 10](device-restrictions-windows-10.md) viele integrierte Einstellungen enthält. Sie müssen also möglicherweise keine benutzerdefinierten Werte eingeben.

In diesem Artikel:

- erfahren Sie, wie Sie ein benutzerdefiniertes Profil für Windows 10-Geräte erstellen
- erhalten Sie eine Liste mit empfohlenen OMA-URI-Einstellungen
- wird ein Beispiel eines benutzerdefinierten Profils bereitgestellt, das eine VPN-Verbindung öffnet

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name**: Geben Sie einen Profilnamen ein, z.B. `windows 10 custom profile`.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
    - **Profiltyp**: Wählen Sie **Benutzerdefiniert** aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name**: Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können.
    - **Beschreibung**: Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **OMA-URI** (Groß-/Kleinschreibung beachten): Geben Sie den OMA-URI ein, für den Sie eine Einstellung bereitstellen möchten.
    - **Datentyp**: Wählen Sie den Datentyp aus, den Sie für diese OMA-URI-Einstellung verwenden möchten. Folgende Optionen sind verfügbar:

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
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Dann wird das Profil erstellt und in der Liste **Gerätekonfiguration > Profile** angezeigt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Einstellung **Konnektivität > VPN über Mobilfunknetz zulassen** aktiviert. Mit dieser Einstellung kann ein Windows 10-Gerät eine VPN-Verbindung über ein Mobilfunknetz herstellen.

![Beispiel für eine benutzerdefinierte Richtlinie mit VPN-Einstellungen](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Eine vollständige Liste aller Konfigurationsdienstanbieter (CSP), die von Windows 10 unterstützt werden, finden Sie in der [Referenz zum Konfigurationsdienstanbieter](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Nicht alle Einstellungen sind mit allen Windows 10-Versionen kompatibel. Über die [Konfigurationsdienstanbieter-Referenz](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) erfahren Sie, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Außerdem unterstützt Intune nicht alle Einstellungen, die in der [Referenz zum Konfigurationsdienstanbieter](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) aufgeführt sind. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Auf jeder Einstellungsseite wird angezeigt, welcher Vorgang jeweils unterstützt wird. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).
