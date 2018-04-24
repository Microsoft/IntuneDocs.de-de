---
title: Registrieren mit dem Geräteregistrierungs-Manager
description: Das Geräteregistrierungs-Manager-Konto (Device Enrollment Manager, DEM) kann eine große Anzahl gemeinsam genutzter, firmeneigener mobiler Geräte mit einem einzigen Benutzerkonto verwalten.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4973e896109589a91891545bbf6db6ca6df45aad
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Registrieren von firmeneigenen Geräten mit dem Geräteregistrierungs-Manager in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Intune können Organisationen eine Vielzahl mobiler Geräte mit einem einzelnen Benutzerkonto verwalten. Das Konto *Geräteregistrierungsmanager* (DEM) ist ein spezielles Benutzerkonto, das bis zu 1.000 Geräte registrieren kann. Fügen Sie dem DEM-Konto vorhandene Benutzer hinzu, damit diese bestimmte DEM-Funktionen erhalten. Jedes registrierte Gerät verwendet eine Einzellizenz. Wir empfehlen, dass Sie Geräte verwenden, die mithilfe dieses Kontos als freigegebene Geräte registriert wurden (also ohne Benutzeraffinität) und nicht als persönliche Geräte (BYOD).  

Es müssen Benutzer im Azure-Portal vorhanden sein, damit sie als Geräteregistrierungs-Manager hinzugefügt werden können. Für die optimale Sicherheit darf der DEM-Benutzer nicht zusätzlich Intune-Administrator sein.

>[!NOTE]
>Die Registrierung mithilfe des DEM-Kontos kann nicht zusammen mit der Registrierung mit dem [Setup-Assistenten von Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md), der [direkten Registrierung](ios-direct-enrollment-in-microsoft-intune.md), der macOS-Registrierung oder der [Registrierung über das Programm zur Geräteregistrierung (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) verwendet werden.

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Beispiel für ein Geräteregistrierungs-Manager-Szenario:

Ein Restaurant möchte 50 Point-of-Sale-Tablets für sein Bedienpersonal bereitstellen sowie Bestellmonitore für seine Küchenmitarbeiter. Die Mitarbeiter müssen niemals auf Unternehmensdaten zugreifen und sich nie als Benutzer anmelden. Der Intune-Administrator erstellt ein Geräteregistrierungs-Manager-Konto und fügt einen Vorgesetzten des Restaurants zum DEM-Konto hinzu, dieser erhält also DEM-Fähigkeiten. Der Vorgesetzte kann nun die 50 Tablets registrieren, indem er die DEM-Anmeldeinformationen verwendet.

Nur Benutzer in der Intune-Konsole können Geräteregistrierungs-Manager sein. Der Geräteregistrierungs-Manager kann kein Intune-Administrator sein.

Der DEM-Benutzer kann Folgendes tun:

-   Registrieren von bis zu 1000 Geräten in Intune
-   Verwenden Sie die Unternehmensportal-App, um Unternehmens-Apps abzurufen
-   Konfigurieren des Zugriffs auf Unternehmensdaten durch Bereitstellen von rollenspezifischen Apps auf den Tablets

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Einschränkungen der Geräte, die mit dem DEM Konto angemeldet sind

Für Geräte, die mit einem Geräteregistrierungs-Manager-Konto registriert wurden, gelten folgende Einschränkungen:

  - Es gibt keinen speziellen „Gerätebenutzer“. Das heißt, es ist kein E-Mail-Zugriff und kein Zugriff auf Unternehmensdaten möglich. Allerdings können z.B. die Geräte-Apps noch immer dazu verwendet werden, um über VPN auf Daten zuzugreifen.

  - Kein bedingter Zugriff, da dies benutzerspezifische Szenarien voraussetzen würde.

  - Der DEM-Benutzer kann die Registrierung von DEM-Geräten auf dem Gerät mit dem Unternehmensportal nicht aufheben. Der Intune-Administrator hat diese Fähigkeit, der DEM-Benutzer jedoch nicht.

  - Nur das lokale Gerät erscheint in der Unternehmensportal-App oder -Website.

  - Benutzer können Apps aus dem Apple Volume Purchase Program (VPP) nicht verwenden, weil für die Verwaltung dieser Apps benutzerspezifische Apple-IDs erforderlich sind.

  - (Nur iOS) Wenn Sie DEM zur Registrierung von iOS-Geräten verwenden, können Sie Apple Configurator oder das Apple-Programm zur Geräteregistrierung nicht zum Registrieren von Geräten verwenden.

> [!NOTE]
> Um Unternehmens-Apps auf Geräten bereitzustellen, die mit dem Geräteregistrierungs-Manager verwaltet werden, stellen Sie die Unternehmensportal-App als **erforderliche Installation** für das Benutzerkonto des Geräteregistrierungs-Managers bereit.
> Zur Verbesserung der Leistung werden beim Anzeigen der Unternehmensportal-App auf einem mit dem Geräteregistrierungs-Manager verwalteten Gerät nur das lokale Gerät angezeigt. Für die Remoteverwaltung anderer vom Geräteregistrierungs-Manager verwalteter Geräte muss die Intune-Verwaltungskonsole verwendet werden.


## <a name="add-a-device-enrollment-manager"></a>Hinzufügen eines Geräteregistrierungs-Managers

1. Stellen Sie sicher, dass der Benutzer, den Sie bereits auf dem DEM-Konto hinzufügen möchten, vorhanden ist. Wenn Sie den Benutzer hinzufügen möchten, melden Sie sich beim [Office 365-Portal](https://go.microsoft.com/fwlink/p/?LinkId=698854) an, und führen Sie die Schritte auf der Seite [Hinzufügen von einzelnen Benutzern oder Massenhinzufügen von Benutzern zu Office 365 – Administratorhilfe](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec) aus.

2. Melden Sie sich bei der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) mit Ihren Administratoranmeldedaten an.

3. Wählen Sie im Navigationsbereich **Admin** aus, gehen Sie zur **Administratorverwaltung**, und wählen Sie **Geräteregistrierungs-Manager** aus. Die Seite **Geräteregistrierungs-Manager** wird geöffnet.

4. Wählen Sie **Hinzufügen…** aus. Das Dialogfeld **Geräteregistrierungs-Manager hinzufügen** wird geöffnet.

5. Geben Sie die **Benutzer-ID** des Intune-Kontos ein, und klicken Sie anschließend auf **OK**.

   Der DEM-Benutzer kann nun Mobilgeräte über dasselbe Verfahren registrieren, das ein Endbenutzer für ein BYOD-Szenario im Unternehmensportal verwendet. Der Manager-Endbenutzer kann die Unternehmensportal-App installieren und das Gerät unter Verwendung seiner DEM-Anmeldeinformationen auf bis zu 1000 Geräten registrieren. Die Schritte zur Registrierung für jede Plattform für den Endbenutzer finden Sie unter folgenden Links:

   - [Registrieren Ihres iOS-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)
   - [Registrieren Ihres Mac OS-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos)
   - [Registrieren Ihres Android-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)
   - [Registrieren Ihres Windows-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Löschen eines Geräteregistrierungs-Managers aus Intune

1.  Melden Sie sich beim [Microsoft Intune-Verwaltungsportal](https://manage.microsoft.com) mit Ihren Administratoranmeldedaten an.

2.  Wählen Sie im Navigationsbereich **Admin** aus, gehen Sie zur **Administratorverwaltung**, und wählen Sie **Geräteregistrierungs-Manager** aus. Die Seite **Geräteregistrierungs-Manager** wird geöffnet.

3.  Wählen Sie den **Geräteregistrierungs-Managerbenutzer** aus, den Sie löschen möchten, und wählen Sie anschließend **Löschen** aus. Dieser Benutzer wird nicht aus Intune gelöscht, und die Geräte, die diese Benutzer verwaltet, bleiben in Intune angemeldet. Durch das Löschen eines Geräteregistrierungs-Manager wird verhindert, dass der Benutzer mehr Geräte in Intune registrieren kann.

4.  Wählen Sie **Ja** aus, um das Löschen des Geräteregistrierungs-Managers zu bestätigen.

Wenn Sie einen Geräteregistrierungs-Manager löschen, wirkt sich dies nicht auf registrierte Geräte aus. Wenn ein Geräteregistrierungs-Manager gelöscht wird:

-   sind keine registrierten Geräte betroffen

-   werden registrierte Geräte weiterhin vollständig verwaltet

-   bleiben die gelöschten Kontoanmeldedaten für den Geräteregistrierungs-Manager für die Anmeldung beim Unternehmensportal zum Zugriff auf Apps gültig

-   können über die Kontoanmeldedaten für den Geräteregistrierungs-Manager weiterhin keine Geräte zurückgesetzt oder deaktiviert werden

-   bleibt die Beziehung des gelöschten Geräteregistrierungs-Manager-Kontos zu registrierten Geräten bestehen, es können jedoch keine zusätzlichen Geräte registriert werden
