---
title: Verwalten firmeneigener Geräte
description: Registrieren Sie unternehmenseigene Geräte auf verschiedene Weise, je nach Gerätetyp, Art des Kaufs und den Anforderungen der Organisation.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 23ae8afbf6c200f983ebee8a94fff42f65ec2486
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="enroll-corporate-owned-devices-by-using-intune"></a>Registrieren unternehmenseigener Geräte über Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Sie können organisations- bzw. unternehmenseigene Geräte auf verschiedene Weise für die Verwaltung durch Intune registrieren, je nachdem, um welches Gerät es sich handelt, wie es erworben wurde und welche Anforderungen der Organisation bestehen. Sie können auch die Unternehmensportal-App installieren, um unternehmenseigene Geräte zu registrieren und zu verwalten, ähnlich wie in einem BYOD-Szenario („Bring Your Own Device“).

Standardmäßig dürfen Geräte für alle Plattformen in Intune registriert werden. Um Geräte für die Registrierung zu blockieren, melden Sie sich mit Ihren Administratoranmeldeinformationen im [Microsoft Intune-Verwaltungsportal](https://manage.microsoft.com) an. Wählen Sie **Admin**(Administrator) > **Verwaltung mobiler Geräte** > **Registrierungsregeln**, und deaktivieren Sie die entsprechenden Kontrollkästchen, die Sie blockieren möchten.

## <a name="enroll-corporate-owned-ios-devices"></a>Registrieren firmeneigener iOS-Geräte

Die Registrierungsmethoden für unternehmenseigene Geräte eignen sich gut für CYOD-Szenarien („Choose Your Own Device“). In einer CYOD-Umgebung bezahlt die Organisation das Gerät, das der Benutzer sich aussucht, und die Organisation verwaltet das Gerät auch.

Wenn Sie iOS-Geräte zur Auswahl anbieten, können Sie die Registrierung vorkonfigurieren, sodass das Gerät direkt ab dem ersten Einschalten durch den Benutzer über Intune verwaltet wird. Intune unterstützt die Registrierung mithilfe des [Apple-Programms zur Geräteregistrierung (Device Enrollment Program, DEP)](ios-device-enrollment-program-in-microsoft-intune.md) oder des Tools Apple Configurator, das auf einem Mac-Computer für die [direkte](ios-direct-enrollment-in-microsoft-intune.md) Registrierung oder die Registrierung mit dem [Setup-Assistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md) ausgeführt wird.

Erfahren Sie, wie Sie [unternehmenseigene iOS-Geräte registrieren](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Erstellen eines Kontos für Geräteregistrierungs-Manager

Sie können ein DEM-Konto (Device Enrollment Manager) für einen Einzelbenutzer in Intune erstellen, um eine Vielzahl von mobilen Geräten für Ihre Organisation zu verwalten. Nachdem Sie das DEM-Konto erstellt haben, kann ein festgelegter Konto-Manager mehr als die fünfzehn Geräte registrieren, die ein Standardbenutzer registrieren darf.

Sie können ein DEM-Konto verwenden, um nur Geräte zu registrieren, die nicht von einem bestimmten Benutzer verwendet werden. Diese Gerätetypen eignen sich z.B. für POS- oder -Hilfsprogramm-Apps, nicht aber für Benutzer, die Zugriff auf E-Mails oder Unternehmensressourcen benötigen.

Erfahren Sie, wie Sie [unternehmenseigene Geräte mithilfe eines DEM-Kontos registrieren](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>Registrieren von unternehmenseigenen Windows 10 Enterprise-Geräten

Wenn Sie in Ihrer Organisation Azure Active Directory oder die Microsoft Enterprise Mobility Suite verwenden, können Sie [Windows 10 Enterprise-Geräte registrieren](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Wenn ein Benutzer auf einem Gerät ein Geschäfts-, Schul- oder Unikonto hinzufügt, wird das Gerät automatisch als „unternehmenseigen“ markiert.

## <a name="import-imei-numbers"></a>Importieren von IMEI-Nummern

Viele Hersteller von mobilen Geräten verwenden für jedes Gerät eine eindeutige Nummer, eine so genannte IMEI-Nummer (International Mobile Equipment Identity). Sie können IMEI-Nummern für Geräte importieren, die sich im Besitz Ihrer Organisation befinden. Wenn ein Gerät von Intune verwaltet wird, wird es als unternehmenseigenes Gerät markiert.

Erfahren Sie, wie Sie [unternehmenseigene Geräte mithilfe von IMEI-Nummern markieren](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporate-owned"></a>Identifizieren von Geräten als unternehmenseigen

Ein Gerät wird von Intune als unternehmenseigenes Gerät erkannt, wenn eine der folgenden Bedingungen zutrifft:

 - Das Gerät wurde [mithilfe eines DEM-Kontos registriert](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (alle Plattformen).
 - Das Gerät wurde mithilfe von [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) oder [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) registriert (nur iOS).
 - Der Gerätehersteller [hat das Gerät mithilfe von IMEI-Nummern vorab deklariert](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (alle Plattformen mit IMEI-Nummern).
 - Jedes Gerät ist in [Azure Active Directory oder der Enterprise Mobility Suite als Windows 10 Enterprise-Gerät](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) registriert (nur Windows 10).

Wenn ein Gerät als Unternehmensgerät markiert wurde, wird im Gerätedatensatz in der Administratorkonsole in der Spalte **Eigentum** der Eintrag **Unternehmen** angezeigt. 
