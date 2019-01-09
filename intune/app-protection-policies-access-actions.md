---
title: Löschen von Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien in Microsoft Intune selektiv löschen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 3f53ce0b2afd214dec98082c23f7187b4e69317b
ms.sourcegitcommit: f114eeba1909c7d4e157003b1a9e2232dd1c99e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53734237"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Selektives Löschen von Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien in Intune

Mithilfe von App-Schutzrichtlinien von Intune können Sie Einstellungen konfigurieren, um Endbenutzern den Zugriff auf eine Unternehmens-App oder ein Unternehmenskonto zu verwehren. Diese Einstellungen sind für die Anforderungen für die Datenverschiebung und den Zugriff, die von Ihrem Unternehmen festgelegt werden, z.B. für Geräte mit Jailbreak und Mindestversionen für das Betriebssystem.
 
Sie können diese Einstellungen verwenden, um die Unternehmensdaten bei Nichtkonformität explizit vom Benutzergerät zu löschen. Für einige Einstellungen können Sie mehrere Aktionen konfigurieren, z.B. das Blockieren des Zugriffs und das Löschen von Daten basierend auf verschiedenen festgelegten Werten.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Erstellen einer App-Schutzrichtlinie mithilfe von Zugriffsaktionen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf **Client-Apps** > **App-Schutzrichtlinien**.
4. Klicken Sie auf **Richtlinie hinzufügen** (Alternativ können Sie eine vorhandene Richtlinie bearbeiten). 
5. Klicken Sie auf **Erforderliche Einstellungen konfigurieren**, um die Liste der verfügbaren Einstellungen anzuzeigen, die für die Richtlinie konfiguriert werden können. 
6. Wenn Sie im Bereich „Einstellungen“ nach unten scrollen, finden Sie einen Abschnitt namens **Zugriffsaktionen** mit einer bearbeitbaren Tabelle.

    ![Screenshot der Zugriffsaktionen für den Intune-App-Schutz](./media/apps-selective-wipe-access-actions01.png)

7. Wählen Sie eine **Einstellung** aus, und geben Sie den **Wert** an, den Benutzer erfüllen müssen, um sich bei Ihrer Unternehmens-App anzumelden. 
8. Wählen Sie die **Aktion** aus, die Benutzer ausführen sollen, wenn Sie Ihre Anforderungen nicht erfüllen. In einigen Fällen können mehrere Aktionen für eine einzelne Einstellung konfiguriert werden. Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

>[!NOTE]
> Geben Sie eine durch Semikolons getrennte Liste der Modellbezeichner ein, um die Einstellung **Device model(s) or Device manufacturer(s)** (Gerätemodelle oder Gerätehersteller) zu verwenden. Vermeiden Sie Leerzeichen in Listen mit mehreren Werten. Bei den Werten wird nicht zwischen Groß- und Kleinschreibung unterschieden. 

## <a name="policy-settings"></a>Richtlinieneinstellungen 

Die Tabelle für die Einstellungen der App-Schutzrichtlinien enthält Spalten für **Einstellungen**, **Werte** und **Aktionen**.

### <a name="ios-policy-settings"></a>iOS-Richtlinieneinstellungen
Für iOS können Sie mithilfe der Dropdownliste **Einstellung** Aktionen für die folgenden Einstellungen konfigurieren:
-  Maximal zulässige PIN-Versuche
-  Offline-Toleranzperiode
-  Geräte mit Jailbreak/entfernten Nutzungsbeschränkungen
-  Mindestversion für Betriebssystem
-  Mindestversion für App
-  Mindestversion für SDK
-  Gerätemodelle

Geben Sie eine durch Semikolons getrennte Liste der iOS-Modellbezeichner ein, um die **Gerätemodelle**-Einstellung zu verwenden. Sie finden iOS-Modellbezeichner in der Spalte „Device Type“ (Gerätetyp) in der [Dokumentation für HockeyApp Support](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types).<br>
Beispieleingabe: *iPhone5,2;iPhone5,3*

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen der Gerätemodelle aus, die in Intune für Anwendungsschutzrichtlinien angegeben sind. Die Übereinstimmung hängt ausschließlich davon ab, was das Gerät meldet. Sie (der IT-Administrator) können sicherstellen, dass das gewünschte Verhalten eintritt, indem Sie diese Einstellung basierend auf mehrerer Geräteherstellern und -modellen und für eine kleine Benutzergruppe testen. Der Standardwert lautet **Nicht konfiguriert**.<br>
Legen Sie eine der folgenden Aktionen fest: 
- Angegebene zulassen (nicht Angegebene blockieren)
- Angegebene zulassen (nicht Angegebene löschen)

**Was geschieht, wenn der IT-Administrator eine andere Liste von iOS-Modellbezeichnern zwischen den Richtlinien einfügt, die für die gleichen Apps für den gleichen Intune-Benutzer vorgesehen sind?**<br>
Wenn ein Konflikt zwischen zwei App-Schutzrichtlinien für konfigurierte Werte entsteht, verwendet Intune in der Regel den restriktivsten Ansatz. Daher wäre die resultierende Richtlinie, die an die Ziel-App gesendet wird, die von dem entsprechenden Intune-Benutzer geöffnet wird, eine Schnittmenge des/der aufgelisteten iOS-Modellbezeichner/s in *Richtlinie A* und *Richtlinie B*, die für die gleiche App- bzw. Benutzerkombination gilt. Zum Beispiel gibt *Richtlinie A* „iPhone5,2;iPhone5,3“ an, während *Richtlinie B* „iPhone5,3“ angibt. Die resultierende Richtlinie, unter die der Intune-Benutzer durch *Richtlinie A* und *Richtlinie B* fällt, wäre demnach „iPhone5,3“. 

### <a name="android-policy-settings"></a>Android-Richtlinieneinstellungen

Für Android können Sie mithilfe der Dropdownliste **Einstellung** Aktionen für die folgenden Einstellungen konfigurieren:
-  Maximal zulässige PIN-Versuche
-  Offline-Toleranzperiode
-  Geräte mit Jailbreak/entfernten Nutzungsbeschränkungen
-  Mindestversion für Betriebssystem
-  Mindestversion für App
-  Mindestversion für den Patch
-  Gerätehersteller

Geben Sie eine durch Semikolons getrennte Liste der Android-Hersteller ein, um die Einstellung **Gerätehersteller** zu verwenden. Den Android-Gerätehersteller finden Sie in den Geräteeinstellungen.<br>
Beispieleingabe: *Hersteller A;Hersteller B* 

>[!NOTE]
> Dies sind einige gängige Hersteller, die von Geräten mit Intune-Verwendung gemeldet werden, sie können als Eingabe verwendet werden: Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen der Gerätemodelle aus, die in Intune für Anwendungsschutzrichtlinien angegeben sind. Die Übereinstimmung hängt ausschließlich davon ab, was das Gerät meldet. Sie (der IT-Administrator) können sicherstellen, dass das gewünschte Verhalten eintritt, indem Sie diese Einstellung basierend auf mehreren Geräteherstellern und -modellen und für eine kleine Benutzergruppe testen. Der Standardwert lautet **Nicht konfiguriert**.<br>
Legen Sie eine der folgenden Aktionen fest: 
- Angegebene zulassen (nicht Angegebene blockieren)
- Angegebene zulassen (nicht Angegebene löschen)

**Was geschieht, wenn der IT-Administrator eine andere Liste von Android-Herstellern zwischen den Richtlinien einfügt, die für die gleichen Apps für den gleichen Intune-Benutzer vorgesehen sind?**<br>
Wenn ein Konflikt zwischen zwei App-Schutzrichtlinien für konfigurierte Werte entsteht, verwendet Intune in der Regel den restriktivsten Ansatz. Daher wäre die resultierende Richtlinie, die an die Ziel-App gesendet wird, die von dem entsprechenden Intune-Benutzer geöffnet wird, eine Schnittmenge der aufgelisteten Android-Hersteller in *Richtlinie A* und *Richtlinie B*, die für die gleiche App- bzw. Benutzerkombination gilt. Zum Beispiel gibt *Richtlinie A* „Google;Samsung“ an, während *Richtlinie B* „Google“ angibt. Die resultierende Richtlinie, unter die der Intune-Benutzer durch *Richtlinie A* und *Richtlinie B* fällt, wäre demnach „Google“. 

### <a name="additional-settings-and-actions"></a>Zusätzliche Einstellungen und Aktionen 

Die Tabelle enthält standardmäßig gefüllte Zeilen als Einstellungen, die für **Offline-Toleranzperiode** und **Maximal zulässige PIN-Versuche** konfiguriert sind, wenn die Einstellung **PIN für Zugriff anfordern** auf **Ja** festgelegt ist.
 
Wählen Sie eine Einstellung aus der Dropdownliste unter der Spalte **Einstellung** aus, um diese zu konfigurieren. Sobald eine Einstellung ausgewählt ist, wird das bearbeitbare Textfeld unter der Spalte **Wert** in der gleichen Zeile aktiviert, wenn ein Wert festgelegt werden muss. Außerdem wird die Dropdownliste unter der Spalte **Aktion** aktiviert, die eine Reihe von bedingten Startaktionen enthält, die für die Einstellung anwendbar sind. 

Die folgende Liste enthält häufig verwendete Aktionen:
-  **Zugriff blockieren:** Blockiert den Zugriff auf die Unternehmens-App für den Endbenutzer.
-  **Daten löschen:** Löschen der Daten vom Gerät des Endbenutzers.
-  **Warnung:** Angeben eines Dialogfelds mit einer Warnmeldung für den Endbenutzer.

In einigen Fällen, z.B. bei der Einstellung **Mindestversion für Betriebssystem**, können Sie die Einstellung konfigurieren, um alle anwendbaren Aktionen basierend auf verschiedenen Versionsnummern auszuführen. 

![Screenshot der Zugriffsaktionen für den App-Schutz: Mindestversion für Betriebssystem](./media/apps-selective-wipe-access-actions05.png)

Sobald eine Einstellung vollständig konfiguriert wurde, wird die Zeile in einer schreibgeschützten Ansicht angezeigt und kann jederzeit bearbeitet werden. Darüber hinaus wird eine Zeile angezeigt, die eine Dropdownliste zur Auswahl in der Spalte **Einstellung** enthält. Einstellungen, die bereits konfiguriert wurden und mehrere Aktionen nicht zulassen, sind in der Dropdownliste nicht verfügbar.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den App-Schutzrichtlinien von Intune finden Sie unter:
- [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md)
- [Einstellungen für App-Schutzrichtlinien für iOS](app-protection-policy-settings-ios.md)
- [Einstellungen für App-Schutzrichtlinien in Microsoft Intune](app-protection-policy-settings-android.md) 
