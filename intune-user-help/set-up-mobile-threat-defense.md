---
title: Installieren von Mobile Threat Defense auf Ihrem mobilen Gerät
description: Erfahren Sie, wie Sie Mobile Threat Defense auf Ihrem mobilen Gerät installieren.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 6b75712cf05626999c09e8d74fd28252666313c4
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857873"
---
# <a name="install-mobile-threat-defense"></a>Installieren von Mobile Threat Defense   

Im Rahmen der Sicherheitsanforderungen Ihres Unternehmens müssen Sie möglicherweise eine Anbieter-App für Mobile Threat Defense (MTD) installieren. Diese Art von App erkennt und warnt Sie auf Bedrohungen auf Ihrem Gerät, wie z. b. verdächtige apps, Netzwerke oder Betriebssystem-Sicherheitsrisiken.  

Wenn Sie nicht über die erforderliche MTD-App verfügen, werden Sie daran gehindert, sich mit Ihrem Geschäfts-, Schul-oder unikonto bei geschützten apps anzumelden. In diesem Artikel erfahren Sie, [wie Sie eine MTD-App installieren](set-up-mobile-threat-defense.md#install-app) , um die Blockierung aufzuheben.  

Es gibt eine Vielzahl von mtd-Anbieter-apps, die für die Installation verfügbar sind. Ihre Organisation informiert Sie über die zu verwendende. 


## <a name="information-your-organization-can-see"></a>Informationen, die Ihre Organisation sehen kann   

In Ihrer Organisation können keine Daten, z. b. Texte, e-Mails und Bilder, in Ihren persönlichen apps angezeigt werden. Die MTD-App meldet Informationen zu ihren apps, z. b. Name und Version, an Ihre Organisation. Die tatsächlich gemeldeten Informationen richten sich nach dem von Ihrem Unternehmen verwendeten MTD-Anbieter. In Ihrer Organisation kann Folgendes angezeigt werden:   

* App-Name  
* App-ID: der eindeutige Name, der die App in Google Play identifiziert.  
* App-Version und kurze Versionsnummer: Die spezifischen Releasenummern für eine App.  
* App Bundle und dynamische Größe: Die Menge Speicherplatz, die eine App auf Ihrem Gerät verwendet 


## <a name="install-app"></a>Installieren der App    
Wenn Sie sich bei einer geschützten App anmelden, werden Sie automatisch aufgefordert, eine MTD-APP zu installieren. Befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen. Verwenden Sie die Schritte in diesem Abschnitt, um weitere Informationen zu finden.  
 
Möglicherweise werden Sie auch aufgefordert, Ihr Gerät zu registrieren. Die Registrierung ist erforderlich, um Ihre Identität zu bestätigen und Ihr Schul-oder Geschäftskonto mit Ihrem Gerät zu verbinden. Wenn Sie nicht registriert sind, werden Sie automatisch durch das Setup geführt, bevor Sie die MTD-App installieren. Wenn Sie zum Bildschirm **Zugriff abrufen** gelangen, können Sie die Installationsschritte starten.  

Weitere Informationen zur Geräteregistrierung finden Sie unter [Registrieren Ihres persönlichen Geräts im Netzwerk Ihrer Organisation](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network).  

### <a name="ios-setup"></a>IOS-Setup  

1. Befolgen Sie auf dem Bildschirm **Zugriff abrufen** die Anweisungen zum Installieren der MTD-APP, die für Ihre Organisation erforderlich ist.   
2. Wechseln Sie zurück zum Bildschirm **Zugriff abrufen** , und wählen Sie **Öffnen**aus.  
3. Die MTD-App fordert die Berechtigung zum Öffnen von Microsoft Authenticator an. Wählen Sie **Öffnen** aus. 
4. Wählen Sie Ihr Geschäftskonto aus, um sich anzumelden. 
5. Warten Sie, während die MTD-App Ihr Gerät auf Sicherheitsbedrohungen scannt. 
6. Kehren Sie zur Schul-oder Arbeits-app zurück, auf die Sie ursprünglich zugreifen wollten. An diesem Punkt werden Sie möglicherweise von Ihrer Organisation aufgefordert, andere APP-Sicherheitsanforderungen zu konfigurieren, z. b. das Erstellen einer PIN.   
7. Sie sollten nun Zugriff auf die APP haben. Wenn Sie immer noch blockiert sind:  
    * **Wählen Sie**auf dem Bildschirm **Zugriff abrufen** die Option erneut aus.  
    * Wechseln Sie zur MTD-APP, und prüfen Sie, ob vorhandene Bedrohungen vorhanden sind. Führen Sie die empfohlenen Schritte aus, um die Bedrohung zu beheben und den Zugriff wiederherzustellen.    

### <a name="android-setup"></a>Android-Setup 

1. Befolgen Sie auf dem Bildschirm **Zugriff abrufen** die Anweisungen zum Installieren der MTD-APP, die für Ihre Organisation erforderlich ist.  
2. Wechseln Sie zurück zum Bildschirm **Zugriff abrufen** , und wählen Sie **Öffnen**aus.  
3. Die MTD-App fordert Sie auf, die Berechtigung für den Zugriff auf bestimmte Bereiche Ihres Geräts zu erhalten, wenn dies erforderlich ist. Damit diese APP ordnungsgemäß funktioniert, müssen Sie den Zugriff auf Kontakte **erlauben** . Die angeforderten Berechtigungen unterscheiden sich von mtd-Anbietern.  
4. Wählen Sie Ihr Geschäftskonto aus, um sich anzumelden.  
5. Warten Sie, während die MTD-App Ihr Gerät auf Sicherheitsbedrohungen scannt.  
6. Kehren Sie zur Schul-oder Arbeits-app zurück, auf die Sie ursprünglich zugreifen wollten. An diesem Punkt werden Sie möglicherweise von Ihrer Organisation aufgefordert, andere APP-Sicherheitsanforderungen zu konfigurieren, z. b. das Erstellen einer PIN.  
7. Sie sollten nun Zugriff auf die APP haben. Wenn Sie immer noch blockiert sind:  
    * **Wählen Sie**auf dem Bildschirm **Zugriff abrufen** die Option erneut aus.  
    * Wechseln Sie zur MTD-APP, und prüfen Sie, ob vorhandene Bedrohungen vorhanden sind. Führen Sie die empfohlenen Schritte aus, um die Bedrohung zu beheben und den Zugriff wiederherzustellen.  

### <a name="installation-failed"></a>Fehler bei der Installation.  

Wenn die Installation fehlschlägt, wenden Sie sich an Ihren IT-Support. Besuchen Sie die [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), um die Kontaktinformationen für Ihre Organisation zu erhalten.  

Sie können Ihre APP-Protokolle auch an Ihren IT-Supportmitarbeiter senden, um Ihnen mehr Kontext zur Installation bereitzustellen.  
* Android-Benutzer: [hochladen und senden Sie Ihre Protokolle](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android) aus Unternehmensportal.   

* IOS-Gerätebenutzer: Rufen Sie Ihre Protokolle von Microsoft Edge für IOS ab, [und senden Sie Sie](https://docs.microsoft.com/intune/apps/manage-microsoft-edge#use-microsoft-edge-on-ios-to-access-managed-app-logs) .  

## <a name="resolve-a-threat"></a>Beheben einer Bedrohung  
Wenn eine Bedrohung die definierte Bedrohungsstufe Ihres Unternehmens überschreitet, führt Ihre Organisation eine der folgenden Aktionen aus:  
   
* Zugriff blockieren: blockiert die Verwendung der geschützten Apps ihrer Organisation, während Sie bei Ihrem Geschäfts-, Schul-oder unikonto angemeldet sind.  
* Daten löschen: löscht Ihre Geschäfts-, Schul-oder unidaten aus einer oder mehreren geschützten Apps ihrer Organisation.  

Öffnen Sie die MTD-App auf Ihrem Gerät, um eine Bedrohung zu beheben und den Zugriff wiederherzustellen. Lesen Sie die Informationen in den bereitgestellten Informationen, um zu erfahren, wie sich die Bedrohung auf Ihr Gerät auswirken könnte Nachdem Sie die Schritte zum Beheben der Bedrohung befolgt haben, wechseln Sie zurück zur MTD-APP, und initiieren Sie eine neue Überprüfung. Es kann einige Minuten dauern, bis Sie wieder auf Ihre Organisation zugreifen können.  

## <a name="next-steps"></a>Nächste Schritte  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).

