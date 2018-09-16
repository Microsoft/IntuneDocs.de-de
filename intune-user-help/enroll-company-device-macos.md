---
title: Registrieren Ihres vom Unternehmen zur Verfügung gestellten macOS-Geräts für die Verwaltung | Microsoft-Dokumentation
description: Informationen zum Registrieren eines macOS-Geräts bei Intune, das von Ihrer Organisation erworben und bereitgestellt wurde.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: a5808a0ac80390b76058827d2ca0870249b043b9
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241829"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Registrieren eines von Ihrer Organisation bereitgestellten macOS-Geräts für die Verwaltung

Erfahren Sie, wie Sie Ihr neues macOS-Gerät in Intune verwalten können.  

Geräte, die Ihnen von der Arbeit, der Schule oder der Universität zur Verfügung gestellt werden, sind häufig vorkonfiguriert, bevor Sie sie erhalten. Ihre Organisation sendet diese vorkonfigurierten Einstellungen an das Gerät, nachdem Sie es eingeschaltet und sich zum ersten Mal angemeldet haben. Wenn Ihr Gerät das Setup abgeschlossen hat, erhalten Sie Zugriff auf Ihre Unternehmens- bzw. Schul- oder Universitätsressourcen. 

Wenn Sie mit dem Setup der Verwaltung beginnen möchten, schalten Sie Ihr Gerät ein, und melden Sie sich mit den betreffenden Anmeldeinformationen an. Im folgenden Artikel werden die Schritte und Bildschirme erläutert, die für das Setup mit dem Setup-Assistenten von Bedeutung sind.   

## <a name="what-is-apple-dep"></a>Was ist das Apple-Programm zur Geräteregistrierung?
Möglicherweise hat Ihre Organisation ihre Geräte über ein sogenanntes *Apple-Programm zur Geräteregistrierung* erworben. Über das Apple-Programm zur Geräteregistrierung haben Organisationen die Möglichkeit, große Mengen von iOS- oder macOS-Geräten zu erwerben. Dann können sie diese Geräte über einen beliebigen Dienst (z.B. Intune), der die Verwaltung mobiler Geräte anbietet, konfigurieren und verwalten. Wenn Sie über Administratorberechtigungen verfügen und sich für das Apple-Programm zur Geräteregistrierung interessieren, erhalten Sie weitere Informationen unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="set-up-your-macos-device"></a>Einrichten Ihres macOS-Geräts  
Führen Sie die folgenden Schritte aus, um Ihr macOS-Gerät für die Verwaltung zu registrieren. Wenn Sie Ihr eigenes Gerät anstelle eines organisationseigenen Geräts verwenden, führen Sie die Schritte für [persönliche Geräte oder Bring Your Own Device](enroll-your-device-in-intune-macos-cp.md) aus.  

1. Schalten Sie Ihr macOS-Gerät ein. 
2. Wählen Sie Ihre **Sprache** aus, und klicken Sie auf **Weiter**.  

   ![Screenshot des Begrüßungsbildschirms des Setup-Assistenten für macOS-Geräte, auf dem eine Liste mit den auswählbaren Sprachen angezeigt wird.](./media/macos-dep-welcome-1808.png)   
3. Wählen Sie ein Tastaturlayout aus. Die Liste besteht basierend auf der von Ihnen ausgewählten Sprache aus mindestens einer Option. Wenn Sie unabhängig von der ausgewählten Sprache alle Layoutoptionen abrufen möchten, klicken Sie auf **Alle anzeigen**. Klicken Sie dann auf **Weiter**.  

   ![Screenshot des Bildschirms zum Auswählen des Tastaturlayouts im Setup-Assistenten für macOS-Geräte, auf dem eine Liste mit auswählbaren Tastatursprachen, die Option „Alle anzeigen“ (deaktiviert) und die Schaltflächen „Zurück“ und „Weiter“ angezeigt werden.](./media/macos-dep-keyboard-1808.png)  
4. Wählen Sie Ihr WLAN-Netzwerk aus. Sie müssen mit dem Internet verbunden sein, um mit dem Setup fortzufahren. Wenn Ihr Netzwerk nicht angezeigt wird oder Sie über ein Kabelnetzwerk eine Verbindung herstellen müssen, klicken Sie auf **Other Network Options** (Weitere Netzwerkoptionen). Klicken Sie dann auf **Weiter**.  

   ![Screenshot des Bildschirms zum Auswählen des WLAN-Netzwerks im Setup-Assistenten für macOS-Geräte, auf dem eine Liste der verfügbaren Netzwerke abgebildet ist. Außerdem werden die Schaltflächen „Other Network Options“ (Andere Netzwerkoptionen), „Zurück“ und „Weiter“ angezeigt.](./media/macos-dep-wifi-1808.png)  
5. Wenn Sie eine WLAN-Verbindung hergestellt haben, wird der Bildschirm **Remoteverwaltung** angezeigt. Über die Remoteverwaltung kann der Administrator der Organisation Ihr Gerät über eine Remoteverbindung mit Konten, Einstellungen, Apps und Netzwerken konfigurieren, die das Unternehmen erfordert. Lesen Sie die Dokumentation, bevor Sie fortfahren, um besser nachvollziehen zu können, wie Ihr Gerät verwaltet wird. Klicken Sie dann auf **Weiter**.  

   ![Screenshot des Bildschirms zur Remoteverwaltung im Setup-Assistenten für macOS-Geräte, auf dem eine Erläuterung zur Remoteverwaltung und ein Link zur Dokumentation angezeigt wird. Außerdem werden die Schaltflächen „Zurück“ und „Weiter“ angezeigt.](./media/macos-dep-remote-management-1-1808.png)  
6. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an, wenn Sie dazu aufgefordert werden. Nach der Authentifizierung installiert Ihr Gerät ein Verwaltungsprofil. Über dieses Profil wird Ihr Zugriff auf die Ressourcen der Organisation konfiguriert und aktiviert.  
7. Informieren Sie sich über das Apple-Symbol „Data & Privacy“ (Daten und Datenschutz), damit Sie später wissen, wann personenbezogene Daten erfasst werden. Klicken Sie dann auf **Weiter**.  

   ![Screenshot des Bildschirms „Data & Privacy“ (Daten und Datenschutz) im Setup-Assistenten für macOS-Geräte, auf dem eine Zeichnung von zwei Personen dargestellt ist, die sich die Hände schütteln, und erläutert wird, wie Apple personenbezogene Daten verwendet. Außerdem werden die Schaltflächen „Zurück“ und „Weiter“ angezeigt.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Nach der Registrierung Ihres Geräts müssen Sie ggf. zusätzliche Schritte ausführen. Welche Schritte Ihnen angezeigt werden ist davon abhängig, wie Ihre Organisation das Setup aufgesetzt hat. Sie werden möglicherweise aufgefordert, einen der folgenden Schritte auszuführen:
    * Melden Sie sich bei einem Apple-Konto an.
    * Stimmen Sie den Nutzungsbedingungen zu.
    * Erstellen Sie ein Computerkonto.
    * Führen Sie ein Express-Setup durch.
    * Richten Sie Ihren Mac ein.  
## <a name="get-the-company-portal-app"></a>Herunterladen der Unternehmensportal-App      
Navigieren Sie zum App Store, um die Intune-Unternehmensportal-App auf Ihrem Gerät herunterzuladen. Mithilfe dieser App können Sie Ihr Gerät für die Verwaltung überwachen und synchronisieren bzw. zu dieser hinzufügen und Apps installieren.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).