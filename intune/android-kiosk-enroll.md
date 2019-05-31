---
title: Einrichten der Intune-Registrierung für dedizierte Android Enterprise-Geräte
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie dedizierte Android Enterprise-Geräte bei Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e980049797ffc3c727d89c197037c019b94326a
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567347"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Einrichten der Intune-Registrierung für dedizierte Android Enterprise-Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Enterprise unterstützt unternehmenseigene kioskartige Geräte zur einmaligen Verwendung mit Lösungen für dedizierte Geräte. Solche Geräte werden für einen einzigen Zweck verwendet, dazu gehören z.B. die digitale Beschilderung, das Drucken von Tickets oder die Bestandsverwaltung. Administratoren beschränken die Verwendung eines Geräts auf eine begrenzte Anzahl von Apps und Weblinks. Außerdem wird verhindert, dass Benutzer andere Apps hinzufügen oder andere Aktionen auf dem Gerät ausführen können.

Intune unterstützt Sie beim Bereitstellen von Apps und Einstellungen für dedizierte Android Enterprise-Geräte. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Geräte, die Sie auf diese Weise verwalten, werden ohne Benutzerkonto in Intune registriert und keinem Endbenutzer zugeordnet. Sie sind nicht für den persönlichen Gebrauch von Anwendungen oder Apps vorgesehen, die ausführliche Voraussetzung für benutzerspezifische Kontodaten umfassen, z.B. Outlook oder Gmail.

## <a name="device-requirements"></a>Geräteanforderungen

Geräte müssen diese Anforderungen erfüllen, um als dediziertes Android Enterprise-Gerät verwaltet zu werden:

- Android-Betriebssystemversion 5.1 und höher.
- Geräte müssen eine Android-Verteilung ausführen, die über GMS-Konnektivität (Google Mobile Services) verfügt. Geräte müssen über GMS verfügen und dazu in der Lage sein, eine Verbindung mit GMS herzustellen.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Einrichten der Verwaltung von dedizierten Android Enterprise-Geräten

Führen Sie die folgenden Schritte aus, um die Verwaltung für dedizierte Android Enterprise-Geräte einzurichten:

1. Sie müssen [**Microsoft Intune** als MDM-Autorität (mobile Geräteverwaltung) festlegen](mdm-authority-set.md), um die Verwaltung von mobilen Geräten vorzubereiten. Sie legen dieses Element nur einmal fest, wenn Sie die Ersteinrichtung von Intune für die Verwaltung mobiler Geräte durchführen.
2. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem verwalteten Google Play-Konto](connect-intune-android-enterprise.md).
3. [Erstellen Sie ein Registrierungsprofil](#create-an-enrollment-profile).
4. [Erstellen Sie eine Gerätegruppe](#create-a-device-group).
5. [Registrieren Sie die dedizierten Geräte](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Erstellen eines Anmeldungsprofils

Sie müssen ein Registrierungsprofil erstellen, damit Sie Ihre dedizierten Geräte registrieren können. Wenn das Profil erstellt wird, wird ein Registrierungstoken (zufällige Zeichenfolge) und ein QR-Code bereitgestellt. Je nach Android-Betriebssystem und Version des Geräts können Sie entweder das Token oder den QR-Code zum [Registrieren des dedizierten Geräts](#enroll-the-dedicated-devices) verwenden.

1. Rufen Sie das [Intune-Portal](https://portal.azure.com) auf, und klicken Sie auf **Device enrollment** (Geräteregistrierung) > **Android enrollment** (Android-Registrierung) > **Corporate-owned dedicated devices**(Unternehmenseigene, dedizierte Geräte).
2. Klicken Sie auf **Erstellen**, und füllen Sie die erforderlichen Felder aus.
    - **Name**: Geben Sie einen Namen ein, den Sie zum Zuweisen des Profils zu einer dynamischen Gerätegruppe verwenden.
    - **Datum für Tokenablauf**: Der Ablaufzeitpunkt des Tokens. Google erzwingt maximal 90 Tage.
3. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

### <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe

Sie können Apps und Richtlinien auf zugewiesene oder dynamische Gerätegruppen ausrichten. Sie können dynamische AAD-Gerätegruppen konfigurieren, um Geräte dynamisch aufzufüllen, die mit einem bestimmten Registrierungsprofil registriert werden, indem Sie die folgenden Schritte ausführen:

1. Navigieren Sie zum [Intune-Portal](https://portal.azure.com), und klicken Sie auf **Gruppen** > **Alle Gruppen** > **Neue Gruppe**.
2. Füllen Sie auf dem Blatt **Gruppe** die erforderlichen Felder wie folgt aus:
    - **Gruppentyp**: Sicherheit
    - **Gruppenname**: Geben Sie einen aussagekräftigen Namen ein (z.B. Factory 1-Geräte)
    - **Mitgliedschaftstyp**: Dynamisches Gerät
3. Klicken Sie auf **Dynamische Abfrage hinzufügen**.
4. Füllen Sie die Felder auf dem Blatt **Dynamische Mitgliedschaftsregeln** wie folgt aus:
    - **Regel für dynamische Mitgliedschaft hinzufügen**: Einfache Regel
    - **Geräte hinzufügen, wobei:** enrollmentProfileName
    - Klicken Sie im mittleren Feld auf **Übereinstimmung**.
    - Geben Sie im letzten Feld den Namen des Registrierungsprofils ein, das Sie zuvor erstellt haben.
    Weitere Informationen über Regeln für die dynamische Mitgliedschaft finden Sie unter [Regeln für eine dynamische Mitgliedschaft für Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Klicken Sie auf **Abfrage hinzufügen** > **Erstellen**.

### <a name="replace-or-remove-tokens"></a>Ersetzen oder Entfernen von Token

Sie können Token und QR-Codes ersetzen oder entfernen.

- **Token ersetzen**: Sie können ein neues Token bzw. einen neuen QR-Code generieren, wenn das Ablaufdatum sich nähert, indem Sie „Token ersetzen“ verwenden.
- **Token widerrufen**: Sie können das Token bzw. den QR-Code sofort für ungültig erklären. Von diesem Zeitpunkt an kann das Token bzw. der QR-Code nicht mehr verwendet werden. Sie können diese Option verwenden, wenn Sie:
    - das Token bzw. den QR-Code versehentlich mit nicht autorisierten Personen geteilt haben
    - alle Registrierungen abgeschlossen haben und das Token bzw. den QR-Code nicht mehr benötigen

Das Ersetzen oder Widerrufen eines Tokens bzw. QR-Codes hat keine Auswirkungen auf Geräte, die bereits registriert sind.

1. Rufen Sie das [Intune-Portal](https://portal.azure.com) auf, und klicken Sie auf **Device enrollment** (Geräteregistrierung) > **Android enrollment** (Android-Registrierung) > **Corporate-owned dedicated devices**(Unternehmenseigene, dedizierte Geräte).
2. Wählen Sie das Profil aus, mit dem Sie arbeiten möchten.
3. Klicken Sie auf **Token**.
4. Klicken Sie auf **Token ersetzen**, um das Token zu ersetzen.
5. Klicken Sie auf **Token widerrufen**, um das Token zu widerrufen.

## <a name="enroll-the-dedicated-devices"></a>Registrieren der dedizierten Geräte

Sie können jetzt [Ihre dedizierten Geräte registrieren](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Verwalten von Apps auf dedizierten Android Enterprise-Geräten

Nur Apps, deren Zuweisungstyp [auf Erforderlich festgelegt](apps-deploy.md#assign-an-app) ist, können auf dedizierten Android Enterprise-Geräten installiert werden. Apps werden über den verwalteten Google Play Store auf die gleiche Weise installiert wie bei Android Enterprise-Arbeitsprofilgeräten.

Apps werden auf verwalteten Geräten automatisch aktualisiert, wenn der App-Entwickler ein Update auf Google Play veröffentlicht.

Sie können eine der folgenden Aktionen durchführen, um eine App von dedizierten Android Enterprise-Geräten zu entfernen:
-   Löschen Sie die erforderliche App-Bereitstellung.
-   Erstellen Sie eine Deinstallationsdatei für die App.

## <a name="next-steps"></a>Nächste Schritte
- [Bereitstellen von Android-Apps](apps-deploy.md)
- [Hinzufügen von Android-Konfigurationsrichtlinien](device-profiles.md)
