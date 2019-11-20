---
title: Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie eine Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto herstellen können.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a89b94f098292bf44122d6d2d144c7f35967cd32
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709453"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie müssen eine Verbindung zwischen Ihrem Intune-Mandantenkonto und Ihrem verwalteten Google Play-Konto herstellen, um [Android Enterprise-Arbeitsprofilgeräte](android-work-profile-enroll.md), [vollständig verwaltete Android Enterprise-Geräte](android-fully-managed-enroll.md) und [dedizierte Android Enterprise-Geräte](android-kiosk-enroll.md) zu unterstützen.  

Intune fügt bei der Verbindung mit Google Play automatisch vier gängige Android Enterprise-bezogene Apps zur Intune-Administratorkonsole hinzu, um Ihnen die Konfiguration und Nutzung der Android Enterprise-Verwaltung zu erleichtern. Die vier Android Enterprise-Apps sind wie folgt:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : für vollständig verwaltete Android Enterprise-Szenarien.
- **[Microsoft Authenticator:](https://play.google.com/store/apps/details?id=com.azure.authenticator)** Hilft bei der Anmeldung bei Ihren Konten, wenn Sie die zweistufige Überprüfung verwenden.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : wird für App Protection Policies (APP) und Szenarien mit Android Enterprise-Arbeitsprofilen genutzt.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : wird für dedizierte/Kioskszenarien mit Android Enterprise verwendet.

> [!NOTE]
> Aufgrund der Interaktion zwischen Google- und Microsoft-Domänen müssen Sie möglicherweise Ihre Browsereinstellungen anpassen, um diesen Schritt durchzuführen.  Stellen Sie sicher, dass „portal.azure.com“ und „play.google.com“ sich in der gleichen Sicherheitszone Ihres Browsers befinden.

1. Wenn nicht bereits geschehen, bereiten Sie die Verwaltung mobiler Geräte durch [Festlegen der Autorität für die Verwaltung mobiler Geräte](../fundamentals/mdm-authority-set.md) auf **Microsoft Intune** vor.
2. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, wählen Sie die Option **Geräteregistrierung** > **Android-Registrierung** > **Verwaltetes Google Play** aus.  Wenn Sie eine benutzerdefinierte Administratorrolle für Intune verwenden, benötigen Sie für den Zugriff die Berechtigungen „Organisation“ und „Update“.
   
   ![Registrierungsseite von Android Enterprise](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Wählen Sie **Ich stimme zu** aus, um Microsoft die Berechtigung zu erteilen, [Benutzer- und Geräteinformationen an Google zu senden](../protect/data-intune-sends-to-google.md). 
   
4. Wählen Sie **Launch Google to connect now** (Jetzt Google für die Verknüpfung starten), um die Google Play-Website zu öffnen. Die Website wird auf einer neuen Registerkarte im Browser geöffnet.
  
5. Geben Sie auf der Anmeldeseite von Google das Google-Konto an, das allen Android Enterprise-Verwaltungsaufgaben für diesen Mandanten zugeordnet sein wird. Dies ist das Google-Konto, das von den IT-Administratoren Ihres Unternehmens gemeinsam zum Verwalten und Veröffentlichen von Apps in der Google Play-Konsole verwendet wird. Sie können ein vorhandenes Google-Konto verwenden oder ein neues Konto erstellen. Das von Ihnen ausgewählte Konto sollte einer G-Suite-Domäne zugeordnet sein.
    
    > [!Note]
    > Wenn Sie Microsoft Edge als Browser verwenden, klicken Sie in der oberen rechten Ecke auf **Anmelden**, um sich bei Ihrem Google-Konto anzumelden.

6. Geben Sie den Namen Ihres Unternehmens als **Organisationsnamen** ein. Für den **Enterprise Mobility Verwaltungsanbieter (EMM)** sollte **Microsoft Intune** angezeigt werden.

7. Stimmen Sie der Android-Vereinbarung zu, und klicken Sie dann auf **Bestätigen**. Ihre Anforderung wird verarbeitet.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Trennen der Verbindung Ihres Android Enterprise-Verwaltungskontos

Sie können die Registrierung und die Verwaltung von Android Enterprise deaktivieren. Dazu müssen Sie zunächst alle registrierten Android Enterprise-Geräte außer Betrieb nehmen, einschließlich Arbeitsprofilgeräte, dedizierte Geräte und vollständig verwaltete Geräte. Wenn Sie anschließend in der Intune-Administratorkonsole auf **Trennen** klicken, werden alle Android Enterprise-Arbeitsprofilgeräte und alle dedizierten Android Enterprise-Geräte aus der Registrierung entfernt. Dadurch wird außerdem die Beziehung zwischen dem verwalteten Google Play-Konto und Intune entfernt.

1. Melden Sie sich als Intune-Administrator beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräteregistrierung** > **Android-Registrierung** > **Managed Google Play** > **Trennen**.
3. Wählen Sie **Ja**, um die Verknüpfung und die Registrierung aller Android Enterprise-Geräte in Intune aufzuheben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine Verbindung mit dem verwalteten Google Play-Konto hergestellt haben, können Sie [Android Enterprise-Arbeitsprofilgeräte einrichten](android-work-profile-enroll.md), [dedizierte Android Enterprise-Geräte einrichten](android-kiosk-enroll.md), und [vollständig verwaltete Android Enterprise-Geräte einrichten](android-kiosk-enroll.md).
