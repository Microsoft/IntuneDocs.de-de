---
title: Entfernen Ihres Windows-Geräts aus Intune
description: Beschreibt das Entfernen eines Windows-Geräts aus Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1dd64250c1996c6b13c62f80572282d639112ba6
ms.sourcegitcommit: 8ee543c864097dc195b6f440471dca713fc21ed2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>Entfernen Ihres Windows-Geräts aus der Intune-Verwaltung

Entfernen Sie ein registriertes, Windows-Gerät aus Intune, wenn Sie für folgende Zwecke nicht mehr wünschen oder benötigen:  
* Verwenden Ihres Geräts für geschäftliche oder schulische Aufgaben 
* Zugreifen auf geschäftliche oder schulische E-Mail, Apps oder andere Ressourcen

Nachdem es entfernt wurde, können Sie auf dem Gerät nicht mehr auf schulische oder geschäftliche Ressourcen zugreifen. Folgende Windows-Geräte können aus Intune entfernt werden:  
* Windows 10-Geräte 
* Windows 8.1-Computer
* Mobile Windows 8.1-Geräte
 
Weitere Informationen dazu, was beim Entfernen Ihres Geräts aus der Intune-Verwaltung geschieht, finden Sie unter [Was geschieht, wenn Sie Ihr Gerät aus Intune entfernen?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Entfernen Ihres Windows 10-Geräts
Führen Sie die folgenden Schritte zum Entfernen eines Windows 10-Geräts aus Intune aus.

### <a name="via-the-company-portal-app"></a>Über die Unternehmensportal-App

1. Öffnen Sie die Unternehmensportal-App.
2. Melden Sie sich mit Ihren Geschäfts-, Schul- oder Unianmeldeinformationen an.
3. Wählen Sie in **Meine Geräte** das Gerät aus, das Sie entfernen möchten.
4. Wählen Sie rechts oben in der App das Symbol **Mehr anzeigen** aus.
5. Wählen Sie **Entfernen** aus. 
6. Wählen Sie zum Bestätigen des Entfernens des Geräts **Gerät entfernen** aus.

### <a name="via-device-settings-app"></a>In der App „Einstellungen“ des Geräts
1. Öffnen Sie die App „Einstellungen“. 
2. Wechseln Sie zu **Konten** > **Auf Arbeits- oder Schulkonto zugreifen**.
3. Wählen Sie das verbundene Konto, das Sie entfernen möchten, und dann **Trennen** aus.
4. Wählen Sie zum Bestätigen des Entfernens des Geräts **Ja** aus.

## <a name="remove-your-windows-81-computer"></a>Entfernen Ihres Windows 8.1-Computers
Führen Sie die folgenden Schritte zum Entfernen eines Windows 8.1-Computers aus Intune aus.

1.  Navigieren Sie zu **PC-Einstellungen** > **Netzwerk** > **Arbeitsplatz**.
2.  Wählen Sie unter **Arbeitsplatzeinbindung** **Leave** (Verlassen) aus.
3.  Wählen Sie unter **Turn on device management** (Geräteverwaltung aktivieren) **Turn off** (Deaktivieren) aus.
4.  Wählen Sie im sich öffnenden Popupfenster **Turn off** (Deaktivieren) aus.

## <a name="remove-your-windows-81-mobile-device"></a>Entfernen Ihres mobilen Windows 8.1-Geräts
Führen Sie die folgenden Schritte zum Entfernen eines mobilen Geräts mit Windows 8.1 aus Intune aus.

1.  Wechseln Sie zu **Einstellungen** > **Arbeitsplatz**.
2.  Tippen Sie auf das Arbeitsplatzkonto, für das Sie die Registrierung aufheben möchten.
3.  Tippen Sie am unteren Bildschirmrand auf **Löschen**.
4.  Tippen Sie im Dialogfeld **Konto löschen** auf **Löschen**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Entfernen Ihrer persönlichen Informationen nach dem Entfernen des Unternehmensportals
Es gibt zwei Arten von Daten, die das Unternehmensportal auf Ihrem Windows-Gerät speichert:

-   **Diagnoseprotokolle:** Daten zu Standardaktivitäten von Apps, die Microsoft sammelt, werden automatisch gelöscht, wenn Sie das Gerät aus dem Unternehmensportal entfernen. App-Aktivitätsdaten enthalten z.B. Informationen dazu, wie lange die App geöffnet war oder sie abgestürzt ist.
-   **Anwendungscache:** Unterstützungsdateien, die erforderlich sind, damit die App funktioniert, z.B. Symbole und Einstellungen.

Sie müssen einige Schritte durchführen, um diese Informationen vollständig zu löschen.

1. Deinstallieren Sie das Unternehmensportal. Durch das [Deinstallieren einer Unternehmensportal-App](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) werden einige der App-Daten entfernt, die auf Ihrem Gerät gespeichert sind.  

2. Setzen Sie das Unternehmensportal zurück, um die gespeicherten App-Daten zurückzusetzen. Öffnen Sie die App **Einstellungen**, und wählen Sie **Apps** > **Unternehmensportal** > **Erweiterte Optionen** > **Zurücksetzen** aus. 

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).