---
title: 'Android-Kioskeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Konfigurieren Sie Android Enterprise-Kioskgeräte.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c4db49b6727a430696d6ade3bc8eb8f4600ebe3e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190284"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Android Enterprise-Kioskeinstellungen in Intune

Android-Kioskprofile unterstützen die folgenden Konfigurationseinstellungen. Beim Erstellen eines Profils werden diese Einstellungen angezeigt, wenn Sie auf **Profiltyp** > **Nur Gerätebesitzer** > **Geräteeinschränkungen** klicken. Klicken Sie in einem Android Enterprise-Geräteeinschränkungsprofil auf **Eigenschaften** und dann auf **Konfigurieren**, um diese Einstellungen anzuzeigen.

## <a name="general-settings"></a>Allgemeine Einstellungen

- **Bildschirmaufnahme:** Wenn Sie **Blockieren** festlegen, wird verhindert, das Benutzer den Bildschirm des Geräts aufnehmen können.
- **Kamera:** Wenn Sie **Blockieren** festlegen, wird die Kamera des Geräts deaktiviert.
- **Standardberechtigungsrichtlinie:** Diese Einstellung definiert die Standardberechtigungsrichtlinie für Anforderungen für Laufzeitberechtigungen. Folgende Werte sind zulässig:
    - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
    - **Eingabeaufforderung:** Der Benutzer wird dazu aufgefordert, die Berechtigung zu genehmigen.
    - **Automatisch zulassen:** Berechtigungen werden automatisch gewährt.
    - **Automatisch ablehnen:** Berechtigungen werden automatisch verweigert.
- **Änderung der Lautstärke:** Wenn Sie **Blockieren** festlegen, können Benutzer die Lautstärke des Geräts nicht ändern.
- **Zurücksetzen:** Wenn Sie **Blockieren** festlegen, wird verhindert, dass Benutzer das Gerät zurücksetzen können.
- **Abgesicherter Start:** Wenn Sie **Blockieren** festlegen, können Benutzer das Gerät nicht im abgesicherten Modus neustarten.
- **Statusleiste:** Wenn Sie **Blockieren** festlegen, erhalten Benutzer keinen Zugriff auf die Statusleiste, einschließlich Benachrichtigungen und Schnelleinstellungen.
- **Änderung der WLAN-Einstellungen:** Wenn Sie **Blockieren** festlegen, können Benutzer die vom Eigentümer des Geräts eingestellten Konfigurationen nicht ändern. Benutzer können ihre eigenen WLAN-Konfigurationen erstellen.
- **Konfiguration des WLAN-Zugriffspunkts:** Wenn Sie **Blockieren** festlegen, können Benutzer keine WLAN-Konfigurationen erstellen oder bearbeiten.
- **Debugging features** (Debugfeatures): Wenn Sie **Zulassen** festlegen, können Benutzer Features zum Debuggen verwenden.
- **Mikrofonanpassung:** Wenn Sie **Blockieren** festlegen, können Benutzer weder die Lautstärke des Mikrofons anpassen noch das Mikrofon stummschalten.
- **E-Mail-Adressen für Schutz vor Zurücksetzung auf Werkseinstellungen:** Wenn Sie **E-Mail-Adressen für Google-Konto** festlegen, können Sie (durch Semikolons getrennte) E-Mail-Adressen definieren, die ein Gerät nach dem Zurücksetzen auf die Werkseinstellungen entsperren können. Wenn keine E-Mail-Adresse festgelegt ist, kann jeder das Gerät nach der Zurücksetzung entsperren.
- **Notausstieg für Netzwerk**: Wenn Sie diese Option **aktivieren**, wird das Feature „Notausstieg für Netzwerk“ aktiviert. Wenn beim Start keine Netzwerkverbindung hergestellt werden kann, wird der Benutzer über das Feature „Notausstieg für Netzwerk“ aufgefordert, sich vorübergehend mit einem Netzwerk zu verbinden, um die Geräterichtlinie zu aktualisieren. Nach dem Anwenden der Richtlinie wird das temporäre Netzwerk ignoriert, und das Gerät setzt den Start fort. So wird verhindert, dass keine Verbindung mit einem Netzwerk hergestellt werden kann, wenn in der letzten Richtlinie kein geeignetes Netzwerk vorhanden ist und das Gerät im Aufgabensperrmodus einer App gestartet wird oder der Benutzer anderweitig nicht in der Lage ist, die Geräteeinstellungen zu erreichen.
- **Installation über unbekannte Quellen zulassen:** Wenn Sie **Zulassen** festlegen, können Benutzer Installationen über unbekannte Quellen ausführen.
- **Systemupdate:** Hier können Sie eine Option auswählen, um zu definieren, wie das Geräte Over-the-Air-Updates verarbeitet:
    - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
    - **Automatisch:** Updates werden ohne Interaktion des Benutzers automatisch installiert. Durch das Festlegen dieser Richtlinie werden sofort alle ausstehenden Updates installiert.
    - **Zurückgestellt:** Updates werden für 30 Tage zurückgestellt. Nach Ablauf der 30 Tage wird der Benutzer von Android zur Installation des Updates aufgefordert. Gerätehersteller oder Mobilfunkanbieter können verhindern (ausschließen), dass wichtige Sicherheitsupdates zurückgestellt werden. Bei einem ausgeschlossenen Update wird dem Benutzer eine Systembenachrichtigung auf dem Gerät angezeigt. 
    - **Wartungsfenster:** Updates werden automatisch in einem täglichen Wartungsfenster installiert, das Sie in Intune festlegen. Die Installation wird 30 Tage lang täglich versucht und kann aufgrund von zu geringem Speicherplatz oder Akkustand fehlschlagen. Nach 30 Tagen wird der Benutzer von Android zur Installation aufgefordert. Dieses Fenster wird auch verwendet, um Updates für Google Play-Apps zu installieren. Diese Option wird für dedizierte Geräte wie Kioskgeräte empfohlen, da Apps, die im Vordergrund auf einem Gerät ausgeführt werden, auf dem der Kioskmodus für die Ausführung einer einzelnen App aktiviert ist, aktualisiert werden können. 

## <a name="kiosk-settings"></a>Kioskeinstellungen

- **Kioskmodus:** Definiert, ob das Gerät eine einzelne oder mehrere Apps ausführen kann. Weitere Informationen finden Sie unter [Kiosk settings for Android devices (Kioskeinstellungen für Android-Geräte in Intune)](android-kiosk-settings.md).
    - **Kiosk mit einzelner App:** Benutzer können nur auf eine einzelne App zugreifen.
    - **Multi-App-Kiosk:** Benutzer können nur auf eine begrenzte Anzahl von Apps zugreifen.

## <a name="device-password-settings"></a>Gerätekennworteinstellungen

- **Keyguard:** Wenn Sie **Deaktivieren** festlegen, können Benutzer Keyguard nicht auf dem Gerät verwenden.
- **Erforderlicher Kennworttyp:** Hiermit wird der Typ des erforderlichen Kennworts für das Gerät definiert.
- **Minimale Kennwortlänge:** Hiermit wird die erforderliche Mindestlänge des Kennworts für das Gerät definiert.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird:** Hiermit wird die Anzahl von Anmeldefehlern definiert, bevor das Gerät zurückgesetzt wird.

## <a name="power-settings"></a>Energieeinstellungen

- **Zeit bis Bildschirmsperre:** Hiermit wird die Leerlaufzeit festgelegt, nach der das Gerät gesperrt wird.
- **Bildschirm aktiviert, wenn Gerät angeschlossen ist:** Hiermit kann ausgewählt werden, bei welchen Stromquellen der Bildschirm des Geräts aktiviert bleibt, wenn es angeschlossen ist.

## <a name="users-and-accounts-settings"></a>Einstellungen für Benutzer und Konten

- **Neue Benutzer hinzufügen:** Wenn Sie **Blockieren** festlegen, können Benutzer keine neuen Benutzer hinzufügen.
- **Entfernen von Benutzern:** Wenn Sie **Blockieren** festlegen, können Benutzer keine Benutzer entfernen.
- **Kontoänderungen:** Wenn Sie **Blockieren** festlegen, können Benutzer Konten nicht bearbeiten.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)



