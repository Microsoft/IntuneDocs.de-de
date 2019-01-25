---
title: Verknüpfen Ihres Intune-Mandantenkontos mit Ihrem Android Enterprise-Konto
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto verknüpfen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 698bc4e7e2d2cf8ece1b1c17b091a91c76a7d178
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386891"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Verknüpfen Ihres Intune-Mandantenkontos mit Ihrem Android Enterprise-Konto

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie müssen Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto verknüpfen, um [Android-Arbeitsprofilgeräte](android-work-profile-enroll.md), [vollständig verwaltete Android-Geräte](android-fully-managed-enroll.md) und [dedizierte Android-Geräte](android-kiosk-enroll.md) zu unterstützen.  

> [!NOTE]
> Aufgrund der Interaktion zwischen Google- und Microsoft-Domänen müssen Sie möglicherweise Ihre Browsereinstellungen anpassen, um diesen Schritt durchzuführen.  Stellen Sie sicher, dass „portal.azure.com“ und „play.google.com“ sich in der gleichen Sicherheitszone Ihres Browsers befinden.

1. Wenn nicht bereits geschehen, bereiten Sie die Verwaltung mobiler Geräte durch [Festlegen der Autorität für die Verwaltung mobiler Geräte](mdm-authority-set.md) auf **Microsoft Intune** vor.
2. Melden Sie sich im [Azure-Portal in Intune](https://aka.ms/intuneportal) an, wählen Sie **Geräteregistrierung** > **Android-Registrierung** > **Managed Google Play** aus.  Wenn Sie eine benutzerdefinierte Administratorrolle für Intune verwenden, benötigen Sie für den Zugriff die Berechtigungen „Organisation“ und „Update“.
   
   ![Registrierungsseite von Android Enterprise](./media/android-work-bind.png)

3. Wählen Sie **Ich stimme zu** aus, um Microsoft die Berechtigung zu erteilen, [Benutzer- und Geräteinformationen an Google zu senden](data-intune-sends-to-google.md). 
   
4. Wählen Sie **Launch Google to connect now** (Jetzt Google für die Verknüpfung starten), um die Google Play-Website zu öffnen. Die Website wird auf einer neuen Registerkarte im Browser geöffnet.
  
5. Geben Sie auf der Anmeldeseite von Google das Google-Konto an, das allen Android Enterprise-Verwaltungsaufgaben für diesen Mandanten zugeordnet sein wird. Dies ist das Google-Konto, das von den IT-Administratoren Ihres Unternehmens gemeinsam zum Verwalten und Veröffentlichen von Apps in der Google Play-Konsole verwendet wird. Sie können ein vorhandenes Google-Konto verwenden oder ein neues Konto erstellen. Das von Ihnen ausgewählte Konto sollte einer G-Suite-Domäne zugeordnet sein.
    
    > [!Note]
    > Wenn Sie Microsoft Edge als Browser verwenden, klicken Sie in der oberen rechten Ecke auf **Anmelden**, um sich bei Ihrem Google-Konto anzumelden.

6. Geben Sie den Namen Ihres Unternehmens als **Organisationsnamen** ein. Für den **Enterprise Mobility Verwaltungsanbieter (EMM)** sollte **Microsoft Intune** angezeigt werden.

7. Stimmen Sie der Android-Vereinbarung zu, und klicken Sie dann auf **Bestätigen**. Ihre Anforderung wird verarbeitet.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Aufheben der Verknüpfung Ihres Android Enterprise-Verwaltungskontos

Sie können die Registrierung und die Verwaltung von Android deaktivieren. Dafür müssen Sie zunächst registrierte Android-Geräte mit Arbeitsprofilen außer Betrieb nehmen. Wenn Sie in der Intune-Administratorkonsole auf **Trennen** klicken, werden alle Android-Arbeitsprofilgeräte und -Kioskgeräte aus der Registrierung entfernt. Dadurch wird außerdem die Beziehung zwischen dem Android Enterprise-Konto und Intune entfernt.

1. Wählen Sie als Intune-Administrator im [Azure-Portal](https://portal.azure.com) die Optionen **Alle Dienste** > **Überwachung + Verwaltung** > **Intune** aus.
2. Klicken Sie auf **Geräteregistrierung** > **Android-Registrierung** > **Managed Google Play** > **Trennen**.
3. Wählen Sie **Ja**, um die Verknüpfung und die Registrierung aller Android Enterprise-Geräte in Intune aufzuheben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine Verknüpfung mit dem Android Enterprise-Konto hergestellt haben, können Sie [Android-Arbeitsprofilgeräte](android-work-profile-enroll.md) und [Android-Kioskgeräte einrichten](android-kiosk-enroll.md).
