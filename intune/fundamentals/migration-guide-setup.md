---
title: Grundlegende Einrichtung von Microsoft Intune
description: Dieser Artikel enthält die notwendigen Schritte zum Einrichten von Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ca0983b7b637b7e85bef97cd77e6c870c4e43eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510013"
---
# <a name="basic-setup"></a>Grundlegende Einrichtung

Nachdem Sie Ihre Umgebung analysiert haben, können Sie mit dem Einrichten von Microsoft Intune beginnen.

## <a name="external-dependencies-for-an-intune-deployment"></a>Externe Abhängigkeiten für eine Bereitstellung mit Intune

### <a name="identity"></a>Identität

Intune erfordert Azure Active Directory (AAD) als Identitäts- und Benutzergruppierungsanbieter. Weitere Informationen:

- [Identitätsanforderungen](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [Anforderungen für die Verzeichnissynchronisierung](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [So funktioniert's: Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [Planen von Benutzer- und Gerätegruppen](users-add.md)

- [Erstellen von Benutzer- und Gerätegruppen](groups-get-started.md)

Wenn in Ihrer Organisation bereits Office 365 verwendet wird, muss Intune dieselbe Azure Active Directory-Umgebung verwenden.

### <a name="pki-optional"></a>PKI (optional)

Wenn Sie Zertifikat-basierte Authentifizierung für VPN-, WLAN- oder E-Mail-Profile von Intune zu verwenden möchten, müssen Sie sicherstellen, dass eine unterstützte [PKI-Infrastruktur vorhanden ist](../protect/certificates-configure.md), in der Zertifikatprofile erstellt und bereitgestellt werden können. Weitere Informationen zum Konfigurieren von Zertifikaten in Intune:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP](/intune/certificates-scep-configure)

- [Konfigurieren der Zertifikatinfrastruktur für PFX](/intune/certficates-pfx-configure)


## <a name="task-list-for-an-intune-setup"></a>Aufgabenliste für die Einrichtung von Intune

### <a name="task-1-intune-subscription"></a>Aufgabe 1: Intune-Abonnement

Bevor Sie zu Intune migrieren können, brauchen Sie ein Intune-Abonnement.

- Suchen Sie [diese Seite](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) auf, um Informationen zu den folgenden Vorgängen zu erhalten:

  - Erstellen eines neuen Intune-Abonnements, das mit einem neuen AAD-Mandanten verknüpft ist

  - Verknüpfen eines Intune-Abonnements, indem Sie sich als bereits vorhandener AAD-Mandant anmelden

### <a name="task-2-assign-intune-user-licenses"></a>Aufgabe 2: Zuweisen von Intune-Benutzerlizenzen

- Erfahren Sie, wie Sie [Intune-Benutzerlizenzen zuweisen](licenses-assign.md) können.

- Wenn Sie bereits einen neuen AAD-Mandanten erstellt haben, erfahren Sie, wie Sie [neue Benutzer erstellen oder Benutzer aus Ihrem lokalen Active Directory (AD) synchronisieren](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) können.

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Aufgabe 3: Umstellen Ihrer MDM-Autorität auf Intune

Intune kann über das Azure-Portal oder über die Konsole von Configuration Manager Current Branch verwaltet werden. Wenn Sie Intune nicht in eine Bereitstellung mit Configuration Manager Current Branch integrieren müssen, wird empfohlen, Intune über das [Azure-Portal](https://portal.azure.com) zu verwalten.

Legen Sie Ihre MDM-Autorität auf **Intune** fest, um das Azure-Portal für Intune zu aktivieren. Wenn Sie eine andere MDM-Autorität verwenden, ist es Intune möglich, die MDM-Verwaltung auf andere Verwaltungskonsolen von Microsoft zu übertragen. Das geschieht jedoch selten.

> [!IMPORTANT]
> Wenn Sie Ihr MDM zum ersten Mal an Intune übertragen, sollten Sie die MDM-Autorität auf Intune festlegen.

Erfahren Sie, wie Sie die [Autorität für die Verwaltung mobiler Geräte einrichten](mdm-authority-set.md) können.

## <a name="next-step"></a>Nächster Schritt

Konfigurieren Sie [Richtlinien für die Verwaltung von Apps und Geräten](../migration-guide-configure-policies.md).
