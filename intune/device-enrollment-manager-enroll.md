---
title: Registrieren von Geräten mithilfe eines Geräteregistrierungs-Manager-Kontos
titlesuffix: Microsoft Intune
description: Verwenden Sie das Konto „Geräteregistrierungs-Manager“, um Geräte in Intune zu registrieren. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a32eb1d65710bf09d61c0846a8d949d5cd99ed2
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Registrieren von Geräten mithilfe eines Geräteregistrierungs-Manager-Kontos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit Intune können Organisationen eine Vielzahl mobiler Geräte mit einem einzelnen Benutzerkonto verwalten. Das Konto *Geräteregistrierungsmanager* (DEM) ist ein spezielles Benutzerkonto, das bis zu 1.000 Geräte registrieren kann. Fügen Sie dem DEM-Konto vorhandene Benutzer hinzu, damit diese bestimmte DEM-Funktionen erhalten. Jedes registrierte Gerät verwendet eine Einzellizenz. Es empfiehlt sich, Geräte zu verwenden, die mithilfe dieses Kontos als freigegebene Geräte registriert wurden, statt persönlicher („BYOD“) Geräte.  

Es müssen Benutzer im [Azure-Portal](https://portal.azure.com) vorhanden sein, damit sie als Geräteregistrierungs-Manager hinzugefügt werden können. Für die optimale Sicherheit darf der DEM-Benutzer nicht zusätzlich Intune-Administrator sein.

>[!NOTE]
>Die Registrierungsmethode mit dem Geräteregistrierungs-Manager (Device Enrollment Manager, DEM) kann nicht zusammen mit den folgenden anderen Registrierungsmethoden verwendet werden: [Apple Configurator mit Setup-Assistent](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator mit direkter Registrierung](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md) oder [Programm zur Geräteregistrierung (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Beispiel für ein Geräteregistrierungs-Manager-Szenario:

Ein Restaurant möchte 50 Point-of-Sale-Tablets für sein Bedienpersonal bereitstellen sowie Bestellmonitore für seine Küchenmitarbeiter. Die Mitarbeiter müssen niemals auf Unternehmensdaten zugreifen und sich nie als Benutzer anmelden. Der Intune-Administrator erstellt ein Geräteregistrierungs-Manager-Konto und fügt einen Vorgesetzten des Restaurants zum DEM-Konto hinzu. Der Vorgesetzte verfügt jetzt über DEM-Fähigkeiten. Der Vorgesetzte kann nun die 50 Tablets registrieren, indem er die DEM-Anmeldeinformationen verwendet.

Nur Benutzer im [Azure-Portal](https://portal.azure.com) können Geräteregistrierungs-Manager sein. Der Geräteregistrierungs-Manager kann kein Intune-Administrator sein.

Der DEM-Benutzer kann Folgendes tun:

-   Registrieren von bis zu 1000 Geräten in Intune
-   Anmelden beim Unternehmensportal, um Unternehmens-Apps abzurufen
-   Konfigurieren des Zugriffs auf Unternehmensdaten durch Bereitstellen von rollenspezifischen Apps auf den Tablets

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Einschränkungen der Geräte, die mit dem DEM Konto angemeldet sind

Für Geräte, die mit einem Geräteregistrierungs-Manager-Konto registriert wurden, gelten folgende Einschränkungen:

  - Kein Zugriff auf Benutzerebene. Da Geräten kein Benutzer zugewiesen ist, hat das Gerät keinen Zugriff auf E-Mails oder Unternehmensdaten. VPN-Konfigurationen beispielsweise können noch immer dazu verwendet werden, um Geräte-Apps Zugriff auf Daten zu gestatten.
  - Der DEM-Benutzer kann die Registrierung von DEM-Geräten auf dem Gerät mit dem Unternehmensportal nicht aufheben. Der Intune-Administrator kann Registrierungen aufheben.
  - Nur das lokale Gerät erscheint in der Unternehmensportal-App oder -Website.
  - Benutzer können Apps mit Benutzerlizenzen aus dem Apple Volume Purchase Program (VPP) nicht verwenden, weil für die Verwaltung dieser Apps benutzerspezifische Apple-IDs erforderlich sind.
  - (Nur iOS) Wenn Sie DEM zur Registrierung von iOS-Geräten verwenden, können Sie zum Registrieren von Geräten nicht Apple Configurator, das Apple-Programm zur Geräteregistrierung (DEP) oder Apple School Manager (ASM) verwenden.
  - (Nur Android) Die Anzahl der Android for Work-Geräte, die mit einem einzelnen DEM-Konto registriert werden können, ist begrenzt. Pro DEM-Konto können maximal zehn Android-Geräte mit Arbeitsprofil registriert werden. Diese Einschränkung gilt nicht für die Android-Legacy-Registrierung.
  - Geräte können VPP-Apps installieren, wenn sie über Gerätelizenzen verfügen.
  - Jedes Gerät benötigt eine Gerätelizenz. In diesem Artikel erfahren Sie mehr über [Benutzer- und Gerätelizenzen](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Sie können Unternehmens-Apps für Geräte bereitstellen, die über den Geräteregistrierungs-Manager verwaltet werden. Stellen Sie die Unternehmensportal-App im Benutzerkonto des Geräteregistrierungs-Managers als **Erforderliche Installation** bereit.
> Zur Verbesserung der Leistung werden beim Anzeigen der Unternehmensportal-App auf einem mit dem Geräteregistrierungs-Manager verwalteten Gerät nur das lokale Gerät angezeigt. Für die Remoteverwaltung anderer vom Geräteregistrierungs-Manager verwalteter Geräte muss die Intune-Verwaltungskonsole verwendet werden.


## <a name="add-a-device-enrollment-manager"></a>Hinzufügen eines Geräteregistrierungs-Managers

1.  Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Geräteregistrierung** > **Geräteregistrierungs-Manager** aus.

2.  Wählen Sie **Hinzufügen** aus.

3.  Geben Sie auf dem Blatt **Benutzer hinzufügen** einen Benutzerprinzipalnamen für den Geräteregistrierungs-Manager-Benutzer ein, und wählen Sie **Hinzufügen** aus. Der Geräteregistrierungs-Manager-Benutzer wird der Liste der Geräteregistrierungs-Manager-Benutzer hinzugefügt.

## <a name="permissions-for-dem"></a>Berechtigungen für DEM

Um Aufgaben zur DEM-Registrierung im Administratorportal durchzuführen, sind globale Azure AD-Rollen oder Azure AD-Rollen für Intune-Dienstadministratoren erforderlich. Diese Rollen sind auch erforderlich, um alle DEM-Benutzer trotz RBAC-Berechtigungen anzuzeigen und werden unter der benutzerdefinierten Benutzerrolle angezeigt. Ein Benutzer, dem keine globale Administratorrolle oder Intune-Dienstadministratorrolle zugewiesen ist, der jedoch über Leseberechtigungen für die Rolle „Geräteregistrierungs-Manager“ verfügt, kann nur die von ihm erstellten DEM-Benutzer sehen. Die Unterstützung von RBAC-Rollen für diese Features werden in der Zukunft bekannt gegeben.

Wenn einem Benutzer keine globale Administratorrolle oder Intune-Dienstadministratorrolle zugewiesen ist, für den Benutzer aber Leseberechtigungen für die Rolle „Geräteregistrierungs-Manager“ aktiviert sind, kann dieser nur die von ihm erstellten DEM-Benutzer sehen.

## <a name="remove-a-device-enrollment-manager"></a>Entfernen eines Geräteregistrierungs-Managers

Wenn Sie einen Geräteregistrierungs-Manager entfernen, wirkt sich dies nicht auf registrierte Geräte aus. Wenn ein Geräteregistrierungs-Manager entfernt wird:

-   Registrierte Geräte sind nicht betroffen und werden weiterhin vollständig verwaltet.
-   Die Anmeldedaten für das entfernte Geräteregistrierungs-Manager-Konto bleiben gültig.
-   Der entfernte Geräteregistrierungs-Manager kann weiterhin keine Geräte zurücksetzen oder deaktivieren.
-   Der entfernte Geräteregistrierungs-Manager kann nur eine Anzahl von Geräten mit dem Limit pro Benutzer registrieren, die vom Intune-Administrator konfiguriert wurde.

**So entfernen Sie einen Geräteregistrierungs-Manager**

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) zuerst **Geräteregistrierung** und dann **Geräteregistrierungs-Manager** aus.
2. Wählen Sie auf dem Blatt **Geräteregistrierungs-Manager** den DEM-Benutzer aus, und klicken Sie auf **Löschen**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Anzeigen der Eigenschaften des Geräteregistrierungs-Managers

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) zuerst **Geräteregistrierung** und dann **Geräteregistrierungs-Manager** aus.
2. Klicken Sie auf dem Blatt **Geräteregistrierungs-Manager** mit der rechten Maustaste auf den DEM-Benutzer, und wählen Sie **Eigenschaften** aus.
