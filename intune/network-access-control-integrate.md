---
title: Integrieren der Netzwerkzugriffssteuerung mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Lösungen für die Netzwerkzugriffssteuerung überprüfen die Registrierung und Konformität von Geräten mit Intune. Die Netzwerkzugriffssteuerung umfasst bestimmte Verhalten und arbeitet mit dem bedingten Zugriff zusammen. Weitere Informationen finden Sie in den Integrationsschritten und unter der Liste mit Partnerlösungen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48228d0baea204fd94175750075c04771116a74d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57399003"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integrieren der Netzwerkzugriffssteuerung (NAC) mit Intune

Intune arbeitet mit Partnern der Netzwerkzugriffssteuerung zusammen, um Organisationen beim Schützen von Unternehmensdaten zu helfen, wenn Geräte versuchen, auf lokale Ressourcen zuzugreifen.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Wie helfen Lösungen von Intune und NAC beim Schutz der Ressourcen Ihrer Organisation?

Lösungen für die Zugriffssteuerung überprüfen den Registrierungs- und Kompatibilitätsstatus des Geräts mit Intune, um Entscheidungen bezüglich der Zugriffssteuerung zu treffen. Wenn das Gerät nicht registriert ist oder registriert ist, aber nicht den Intune-Gerätekonformitätsrichtlinien entspricht, sollte es für die Registrierung oder eine Gerätekonformitätsprüfung an Intune umgeleitet werden.

### <a name="example"></a>Beispiel

Wenn das Gerät registriert und mit Intune kompatibel ist, sollte die NAC-Lösung dem Gerät den Zugriff auf Unternehmensressourcen erlauben. Benutzern kann beispielsweise der Zugriff auf das Unternehmens-WLAN oder VPN-Ressourcen gewährt oder verweigert werden.

## <a name="feature-behaviors"></a>Featureverhalten

Geräte, die aktiv mit Intune synchronisiert werden, können nicht vom Zustand **Konform** / **Nicht konform** in **Nicht synchronisiert** (oder **Unbekannt**) wechseln. Der Zustand **Unbekannt** ist für neu registrierte Geräte reserviert, die noch nicht im Hinblick auf ihre Konformität ausgewertet wurden.

Bei Geräten, die für den Zugriff auf Ressourcen blockiert sind, sollte der blockierende Dienst alle Benutzer auf das [Verwaltungsportal](https://portal.manage.microsoft.com) umleiten, um festzustellen, warum das Gerät blockiert ist.  Wenn die Benutzer diese Seite besuchen, werden ihre Geräte erneut synchron im Hinblick auf Konformität ausgewertet.

## <a name="nac-and-conditional-access"></a>NAC und bedingter Zugriff

NAC nutzt bei Entscheidungen bezüglich der Zugriffssteuerung den bedingten Zugriff. Weitere Informationen finden Sie unter [Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs in Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Funktionsweise der NAC-Integration

Im Folgenden erhalten Sie einen Überblick darüber, wie die Integration der Netzwerkzugriffssteuerung funktioniert, wenn sie in Intune integriert ist. In den ersten drei Schritten 1-3 wird der Onboardingprozess erklärt. Nachdem die Lösung für die Zugriffssteuerung in Intune integriert wurde, wird in den Schritten 4-9 der laufende Betrieb beschrieben.

![Darstellung der Funktionsweise der Netzwerkzugriffssteuerung mit Intune](./media/ca-intune-common-ways-2.png)

1. Registrieren Sie die Lösung des NAC-Partners mit Azure Active Directory (AAD), und gewähren Sie delegierte Berechtigungen an die Intune-NAC-API.
2. Konfigurieren Sie die Lösung des NAC-Partners mit den geeigneten Einstellungen, darunter die URL für die Intune-Ermittlung.
3. Konfigurieren Sie die Lösung des NAC-Partners für die Zertifikatauthentifizierung.
4. Der Benutzer stellt eine Verbindung zum WLAN-Zugriffspunkt her oder fordert eine VPN-Verbindung an.
5. Die Lösung des NAC-Partners leitet die Geräteinformationen an Intune weiter und fragt Intune nach dem Registrierungs- und Kompatibilitätsstatus des Geräts.
6. Wenn das Gerät nicht konform oder nicht registriert ist, weist die Lösung des NAC-Partners den Benutzer an, das Gerät zu registrieren oder die Konformitätsprobleme zu beheben.
7. Das Gerät versucht bei Bedarf, seinen Konformitäts- und Registrierungszustand erneut zu überprüfen.
8. Wenn das Gerät registriert wurde und kompatibel ist, erhält die Lösung des NAC-Partners von Intune eine Statusmeldung.
9. Die Verbindung konnte erfolgreich hergestellt werden, und das Gerät erhält Zugriff auf Unternehmensressourcen.

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>Verwenden der NAC für ein VPN auf iOS-Geräten  
Die NAC für Cisco Legacy AnyConnect, F5 Access Legacy und Citrix VPN wird unterstützt, ohne dass die NAC im VPN-Profil aktiviert werden muss.

Die NAC für Citrix SSO wird ebenfalls unterstützt. Um die NAC für Citrix SSO für iOS zu aktivieren, gehen Sie wie folgt vor:
- Verwenden Sie Citrix Gateway 12.0.59 oder höher.  
- Benutzer müssen Citrix SSO 1.1.6 oder höher installiert haben.
- [Integrieren Sie NetScaler in Intune für die NAC](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html), wie in der Citrix-Produktdokumentation beschrieben wird.
- Aktivieren Sie in der Basis-VPN-Einstellungskonfiguration für **Netzwerkzugriffssteuerung (NAC) aktivieren** das Kontrollkästchen **Ich stimme zu**.

Wenn Sie Citrix SSO für iOS verwenden, wird die VPN-Verbindung aus Sicherheitsgründen innerhalb von 24 Stunden getrennt. Die VPN-Verbindung kann sofort wiederhergestellt werden.


**Für die folgenden VPN-Clients wird die Netzwerkzugriffssteuerung unter iOS derzeit nicht unterstützt**:
-   Cisco AnyConnect
-   F5 Access

Microsoft und Partner arbeiten an einer NAC-Lösung für diese neueren Clients. Dieser Artikel erhält Updates mit weiteren Informationen, sobald neue Lösungen verfügbar sind. 


## <a name="next-steps"></a>Nächste Schritte

- [Integrieren von Cisco ISE mit Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Integrieren von Citrix NetScaler mit Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Integrieren von HPE Aruba ClearPass mit Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Integrate Squadra security Removable Media Manager (secRMM) with Intune (Integrieren des Squadra-Sicherheitsmanagers für entfernbare Wechselmedien mit Intune)](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
