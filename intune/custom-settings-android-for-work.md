---
title: 'Hinzufügen benutzerdefinierter Einstellungen zu Android Enterprise-Geräten in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Hinzufügen oder Erstellen eines benutzerdefinierten Profils für Android Enterprise-Geräte zum Erstellen in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a622264ed7cc091849bacbd02f8ae7bdb33603fe
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983141"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Verwenden benutzerdefinierter Einstellungen für Android Enterprise-Geräte in Microsoft Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für Android Enterprise-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Benutzerdefinierte Android Enterprise-Profile verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Festlegen verschiedener Features auf Android Enterprise-Geräten. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features festzulegen.

Intune unterstützt zurzeit eine begrenzte Anzahl von benutzerdefinierten Android Enterprise-Profilen.

In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Profil für Android Enterprise-Geräte erstellen. Außerdem wird im Artikel ein Beispiel für ein benutzerdefiniertes Profil aufgezeigt, das Kopier- und Einfügevorgänge blockiert.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `android enterprise custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform:** Wählen Sie **Android Enterprise** aus.
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
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Das Profil wird erstellt und in der Liste **Gerätekonfiguration > Profile** angezeigt.

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen Sie ein benutzerdefiniertes Profil, das Kopier- und Einfügevorgänge zwischen geschäftlichen und persönlichen Apps auf Android Enterprise-Geräten einschränkt.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `android ent block copy paste custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform:** Wählen Sie **Android Enterprise** aus.
    - **Profiltyp:** Wählen Sie **Benutzerdefiniert** aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie zum Beispiel `Block copy and paste` ein.
    - **Beschreibung:** Geben Sie zum Beispiel `Blocks copy/paste between work and personal apps` ein.
    - **OMA-URI:** Geben Sie `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste` ein.
    - **Datentyp:** Wählen Sie **Boolean** (Boolescher Wert) aus, damit der Wert für den OMA-URI **TRUE** oder **FALSE** ist.
    - **Wert:** Wählen Sie **TRUE** aus.

5. Nachdem Sie die Einstellungen festgelegt haben, sollte Ihre Umgebung in etwa wie folgt aussehen:

    ![Kopieren und Einfügen für das Android Enterprise-Profil blockieren](./media/custom-policy-afw-copy-paste.png)

Wenn Sie dieses Profil einem von Ihnen verwalteten Android Enterprise-Gerät zuweisen, werden Kopier- und Einfügevorgänge zwischen Apps im Arbeitsprofil und im persönlichen Profil blockiert.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen finden Sie im [Artikel zum Erstellen eines Profils auf einem Android-Gerät](custom-settings-android.md).