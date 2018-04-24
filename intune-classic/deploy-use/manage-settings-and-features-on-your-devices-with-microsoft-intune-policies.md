---
title: Verwalten von Geräteeinstellungen mit Richtlinien
description: Verwenden Sie Intune, um Richtlinien zu erstellen und bereitzustellen, die Einstellungen und Features auf registrierten, von Ihnen verwalteten Geräten steuern.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6e639dda2509ab51bfcf6d0976be517e220800e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="manage-settings-and-features-on-your-devices-with-microsoft-intune-policies"></a>Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune-*Richtlinien* sind Gruppen von Einstellungen zur Steuerung der Features auf mobilen Geräten und Computern. Sie erstellen Richtlinien mithilfe von Vorlagen, in denen empfohlene oder benutzerdefinierte Einstellungen enthalten sind, und stellen diese dann für Geräte- oder Benutzergruppen bereit.

## <a name="types-of-policies"></a>Richtlinientypen

Intune-Richtlinien lassen sich in die folgenden Kategorien einteilen: Die von Ihnen verwendete Kategorie bestimmt, wie Sie die Richtlinie erstellen und bereitstellen können.


- **Konfigurationsrichtlinien**: Diese werden häufig zum Verwalten von Sicherheitseinstellungen und -features auf Ihren Geräten verwendet. Verwenden Sie die Informationen in diesem Thema, um mehr über das Erstellen und Bereitstellen dieser Richtlinien und die verfügbaren Einstellungen zu erfahren.
- **Gerätekompatibilitätsrichtlinien**: Diese definieren die Regeln und Einstellungen, die ein Gerät erfüllen muss, damit es als kompatibel mit Richtlinien für bedingten Zugriff eingestuft wird. Kompatibilitätsrichtlinien ermöglichen Ihnen auch, die Kompatibilität von Geräten unabhängig von bedingten Zugriffsrechten zu überwachen und zu beheben.
Weitere Informationen finden Sie unter [Gerätekonformitätsrichtlinien in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Richtlinien für bedingten Zugriff**: Mit diesen Richtlinien können Sie E-Mail- und andere Dienste basierend auf Bedingungen schützen, die Sie festlegen.
Weitere Informationen finden Sie unter [Beschränken des Zugriffs auf E-Mail- und Office 365-Dienste mit Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Richtlinien zum Registrieren unternehmenseigener Geräte**: Informationen über Richtlinien zum Registrieren unternehmenseigener Geräte finden Sie unter [Einrichten der iOS- und Mac-Verwaltung mit Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Ressourcenzugriffsrichtlinien:** Diese Richtlinien ermöglichen Benutzern den Zugriff auf die Dateien und Ressourcen, die sie für ihre Arbeit benötigen, und zwar unabhängig davon, wo sie sich befinden.
Weitere Informationen finden Sie unter [Aktivieren des Zugriffs auf Unternehmensressourcen mit Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Eine vollständige Liste der Intune-Richtlinien finden Sie unter [Referenz zu Microsoft Intune-Richtlinien](microsoft-intune-policy-reference.md).

## <a name="create-a-configuration-policy"></a>Erstellen einer Konfigurationsrichtlinie

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Optionen **Richtlinie** &gt; **Konfigurationsrichtlinien** &gt; **Hinzufügen**.

2.  Wählen Sie die gewünschte Richtlinie aus, und entscheiden Sie, ob Sie die empfohlenen Einstellungen für die Richtlinie verwenden (sofern verfügbar, Sie können diese Einstellungen später ändern) oder eine benutzerdefinierte Richtlinie mit Ihren eigenen Einstellungen erstellen möchten.

    > [!TIP]
    > Hilfe zur Auswahl der richtigen Richtlinie finden Sie in der [Referenz zu Microsoft Intune-Richtlinien](microsoft-intune-policy-reference.md).

3.  Wenn Sie bereit sind, wählen Sie **Richtlinie erstellen**.

4.  Geben Sie auf der Seite **Richtlinie erstellen** einen Namen und optional eine Beschreibung für die Richtlinie ein.

5.  Konfigurieren Sie die erforderlichen Richtlinieneinstellungen, und wählen Sie dann **Richtlinie speichern**.

    Wenn Sie Hilfe zu Richtlinieneinstellungen benötigen, wählen Sie Ihren Richtlinientyp aus der folgenden Liste aus:

    - [Einstellungen für iOS-Geräte](ios-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Android-Geräte](android-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Android for Work-Geräte](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Geräte mit Windows 8 und Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Geräte mit Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Desktop- und mobile Geräte mit Windows 10](windows-10-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Windows Team-Geräte](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Upgradeeinstellungen für die Windows-Edition](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Mac OS X-Geräte](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Einstellungen für Nutzungsbedingungsrichtlinien](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Allgemeine Einstellungen für mobile Geräte (Legacy)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Wählen Sie im Bestätigungsdialogfeld **Ja**, um die Richtlinie jetzt bereitzustellen, oder **Nein**, um die Richtlinie zu erstellen, ohne sie bereitzustellen.

Sie können die neue Richtlinie anzeigen und bearbeiten, indem Sie im Arbeitsbereich **Richtlinie** durch die Abschnitte für die einzelnen Richtlinientypen navigieren.

Wenn sie eine Richtlinie erstellen, bei der die empfohlenen Einstellungen verwendet werden, setzt sich der Name der neuen Richtlinie aus dem Vorlagennamen, dem Datum und der Uhrzeit zusammen. Wenn Sie die Richtlinie bearbeiten, wird der Name mit dem Datum und der Uhrzeit der Bearbeitung aktualisiert.

Nachdem Sie eine Richtlinie erstellt haben, werden Sie sie in der Regel für eine oder mehrere Gruppen von Benutzern oder Geräten bereitstellen.

> [!TIP]
> Sie stellen nicht alle Richtlinientypen bereit. Beispielsweise wird die Richtlinie für die Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) nicht bereitgestellt. Diese Richtlinie wird stattdessen einer App zugeordnet, die Sie dann bereitstellen.

## <a name="deploy-a-configuration-policy"></a>Bereitstellen einer Konfigurationsrichtlinie

1.  Wählen Sie im Arbeitsbereich **Richtlinie** die Richtlinie aus, die Sie bereitstellen möchten, und wählen Sie dann **Bereitstellung verwalten** aus.

2.  Führen Sie im Dialogfeld **Bereitstellung verwalten** folgende Schritte aus:

    -   Um die Richtlinie bereitzustellen, wählen Sie mindestens eine Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und klicken Sie auf **Hinzufügen** &gt; **OK**.

    -   Um das Dialogfeld zu schließen, ohne die Richtlinie bereitzustellen, klicken Sie auf **Abbrechen**.

Wenn Sie eine bereitgestellte Richtlinie auswählen, können Sie weitere Informationen zur Bereitstellung im unteren Teil der Richtlinienliste anzeigen.

## <a name="manage-policies"></a>Verwalten von Richtlinien

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Richtlinie**, navigieren Sie zu der Richtlinie, die Sie verwalten möchten, und wählen Sie sie aus.

2.  Wählen Sie eine der folgenden Aktionen aus:

- **Bearbeiten**: Öffnen Sie die Eigenschaften für die ausgewählte Richtlinie, um Änderungen daran vorzunehmen.
- **Löschen**: Löschen Sie die ausgewählte Richtlinie.<br>Wenn Sie eine Richtlinie löschen, wird sie aus allen Gruppen entfernt, für die sie bereitgestellt worden war.
- **Bereitstellung verwalten**: Wählen Sie die Gruppe aus, für die Sie die Richtlinie bereitstellen möchten, und wählen Sie dann **Hinzufügen**.


## <a name="frequently-asked-questions-about-intune-policies"></a>Häufig gestellte Fragen zu Intune-Richtlinien

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-deployed"></a>Wie lange dauert es, bis mobile Geräte Richtlinien oder Apps nach ihrer Bereitstellung abrufen können?
Wenn eine Richtlinie oder App bereitgestellt wird, beginnt Intune sofort mit dem Versuch, das Gerät zu benachrichtigen und zum Einchecken beim Intune-Dienst zu veranlassen. Dies dauert normalerweise weniger als fünf Minuten.

Wenn ein Gerät sich nach der ersten Benachrichtigung nicht zum Abrufen der Richtlinie eincheckt, unternimmt Intune drei weitere Versuche.  Wenn das Gerät offline ist (z. B. ausgeschaltet oder nicht mit einem Netzwerk verbunden), erhält es die Benachrichtigungen möglicherweise nicht. In diesem Fall erhält das Gerät die Richtlinie beim nächsten geplanten Einchecken beim Intune-Dienst wie folgt:

- iOS und Mac OS X: alle sechs Stunden.
- Android: alle acht Stunden.
- Windows Phone: alle acht Stunden.
- Als Geräte registrierte PCs unter Windows 8.1 und Windows 10: alle acht Stunden.

Wenn das Gerät gerade registriert wurde, ist die Eincheckfrequenz höher:

- iOS und Mac OS X: sechs Stunden lang alle 15 Minuten, danach alle sechs Stunden.
- Android: 15 Minuten lang alle drei Minuten, danach zwei Stunden lang alle 15 Minuten, anschließend alle acht Stunden.
- Windows Phone: 15 Minuten lang alle fünf Minuten, danach zwei Stunden lang alle 15 Minuten, anschließend alle acht Stunden.
- Als Geräte registrierte Windows-PCs: 30 Minuten lang alle drei Minuten, danach alle acht Stunden.

Benutzer können auch jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort auf Richtlinien zu prüfen.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Bei welchen Aktionen sendet Intune sofort eine Benachrichtigung an ein Gerät?
Geräte checken bei Intune entweder beim Erhalt einer Benachrichtigung ein, die sie dazu auffordert, oder während ihres regelmäßigen geplanten Eincheckvorgangs.  Wenn Sie für ein Gerät oder einen Benutzer ausdrücklich eine Aktion durchführen, wie z. B. Zurücksetzen, Sperren, Zurücksetzen der Kennung, App-Bereitstellung, Profilbereitstellung (WLAN, VPN, E-Mail usw.) oder Bereitstellung der Richtlinie, beginnt Intune sofort mit dem Versuch, das Gerät zu benachrichtigen, dass es sich zum Erhalten dieser Updates beim Intune-Dienst einchecken soll.

Andere Änderungen, wie z. B. die Überarbeitung der Kontaktinformationen im Unternehmensportal, führen nicht zu einer sofortigen Benachrichtigung von Geräten.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Wie finde ich heraus, welche Einstellungen angewendet werden, wenn für denselben Benutzer oder dasselbe Gerät mehrere Richtlinien bereitgestellt werden?
Bei Bereitstellung mehrerer Richtlinien für denselben Benutzer oder dasselbe Gerät erfolgt die Auswertung, welche Einstellung angewendet werden soll, auf der Ebene der einzelnen Einstellungen:

-   Kompatibilitätsrichtlinieneinstellungen haben immer Vorrang vor Konfigurationsrichtlinieneinstellungen.

-   Die restriktivste Kompatibilitätsrichtlinie wird angewendet, wenn sie anhand derselben Einstellung in einer anderen Kompatibilitätsrichtlinie ausgewertet wird.

-   Falls eine Konfigurationsrichtlinieneinstellung im Konflikt mit einer Einstellung in einer anderen Konfigurationsrichtlinie steht, wird dieser Konflikt in der Intune-Konsole angezeigt. Konflikte dieser Art müssen Sie manuell auflösen.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>Was geschieht, wenn Richtlinien für die Verwaltung mobiler Anwendungen miteinander in Konflikt stehen? Welche wird auf die App angewendet?
Konfliktwerte sind die restriktivsten Einstellungen, die in einer MAM-Richtlinie zur Verfügung stehen, außer für die Zahleneingabefelder (z. B. PIN-Versuche vor dem Zurücksetzen).  Die Zahleneingabefelder werden auf dieselben Werte gesetzt, die auch verwendet werden, wenn Sie in der Konsole eine MAM-Richtlinie erstellen und die empfohlenen Einstellungen verwenden.

Konflikte treten auf, wenn zwei Richtlinieneinstellungen identisch sind.  Beispielsweise haben Sie zwei MAM-Richtlinien konfiguriert, die mit Ausnahme der Einstellung für Kopieren/Einfügen identisch sind.  In diesem Szenario wird die Einstellung für Kopieren und Einfügen auf den restriktivsten Wert festgelegt, die übrigen Einstellungen werden jedoch wie konfiguriert angewendet.

Wenn eine Richtlinie für die App bereitgestellt wird und in Kraft tritt und anschließend eine weitere bereitgestellt wird, erhält die zuerst bereitgestellte Richtlinie Vorrang und bleibt wirksam, während die zweite als in Konflikt stehend angezeigt wird. Wenn beide Richtlinien gleichzeitig angewendet werden, also keine vorherige Richtlinie vorhanden ist, stehen beide in Konflikt. Alle in Konflikt stehenden Einstellungen werden auf die restriktivsten Werte festgelegt.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Was geschieht, wenn Sie benutzerdefinierte iOS-Richtlinien in Konflikt stehen?
Intune bewertet nicht die Nutzlast von Apple-Konfigurationsdateien oder einer benutzerdefinierten OMA-URI-Richtlinie (Open Mobile Alliance Uniform Resource Identifier). Es dient lediglich als Übermittlungsmechanismus.

Wenn Sie eine benutzerdefinierte Richtlinie bereitstellen, stellen Sie sicher, dass die konfigurierten Einstellungen nicht mit Kompatibilitäts-, Konfigurations- oder anderen benutzerdefinierten Richtlinien in Konflikt stehen. Bei einer benutzerdefinierten Richtlinie mit Einstellungskonflikten werden die Einstellungen in zufälliger Reihenfolge angewendet.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Was geschieht, wenn eine Richtlinie gelöscht wird oder nicht mehr gilt?
Wenn Sie eine Richtlinie löschen oder ein Gerät aus einer Gruppe entfernen, für die eine Richtlinie bereitgestellt wurde, werden die Richtlinie und die Einstellungen gemäß den folgenden Listen von dem Gerät entfernt.

#### <a name="enrolled-devices"></a>Angemeldete Geräte

- WLAN-, VPN-, Zertifikat- und E-Mail-Profile: Diese Profile werden von allen unterstützten registrierten Geräten entfernt.
- Alle anderen Richtlinientypen:
    - **Windows- und Android-Geräte**: Einstellungen werden nicht vom Gerät entfernt.
    - **Windows Phone 8.1-Geräte**: Die folgenden Einstellungen werden entfernt:
        - Anfordern eines Kennworts zum Entsperren mobiler Geräte
        - Einfache Kennwörter zulassen
        - Minimale Kennwortlänge
        - Erforderlicher Kennworttyp
        - Kennwortablauf (Tage)
        - Kennwortverlauf speichern
        - Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird
        - Minuten der Inaktivität, bevor ein Kennwort erforderlich ist
        - Erforderlicher Kennworttyp – Mindestanzahl von Zeichensätzen
        - Kamera zulassen
        - Verschlüsselung auf mobilem Gerät anfordern
        - Wechselspeichermedien zulassen
        - Webbrowser zulassen
        - App Store zulassen
        - Bildschirmaufnahme zulassen
        - Geolocation zulassen
        - Microsoft-Konto erlauben
        - Kopieren und Einfügen zulassen
        - WLAN-Tethering zulassen
        - Automatische Verbindung mit unverschlüsselten WLAN-Hotspots zulassen
        - Berichterstellung für WLAN-Hotspots zulassen
        - Zurücksetzen auf Werkseinstellungen zulassen
        - Bluetooth zulassen
        - NFC zulassen
        - WLAN zulassen

    - **iOS**: Alle Einstellungen werden entfernt, außer:
        - Sprachroaming zulassen
        - Datenroaming zulassen
        - Automatische Synchronisierung beim Roaming zulassen

#### <a name="windows-pcs-running-the-intune-client-software"></a>Windows-PCs, auf denen die Intune-Clientsoftware ausgeführt wird

- **Endpoint Protection-Einstellungen**: Die Einstellungen werden auf die empfohlenen Werte zurückgesetzt. Die einzige Ausnahme ist die Einstellung **Microsoft Active Protection Service beitreten**, deren Standardwert **Nein** lautet. Weitere Informationen finden Sie unter [Schützen von Windows-PCs mit Endpoint Protection für Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Einstellungen für Softwareupdates**: Die Einstellungen werden auf die Standardwerte des Betriebssystems zurückgesetzt. Weitere Informationen finden Sie unter [Aktualisieren Ihrer Windows-PCs mit Softwareupdates in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Microsoft Intune Center-Einstellungen**: Alle Informationen zur Kontaktaufnahme mit dem Support, die durch die Richtlinie definiert waren, werden von den Computern gelöscht.
- **Einstellungen für die Windows-Firewall**: Die Einstellungen werden auf die Standardwerte des Computerbetriebssystems zurückgesetzt. Weitere Informationen finden Sie unter [Schützen von Windows-PCs mit Endpoint Protection für Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### <a name="how-can-i-refresh-the-policies-on-a-device-to-ensure-that-they-are-current-applies-to-windows-pcs-running-the-intune-client-software-only"></a>Wie kann ich die Richtlinien auf einem Gerät aktualisieren und so sicherstellen, dass sie aktuell sind (gilt nur für Windows-PCs, auf denen die Intune-Clientsoftware ausgeführt wird)?

1.  Wählen Sie in einer beliebigen Gerätegruppe die Geräte aus, auf denen die Richtlinien aktualisiert werden sollen, und wählen Sie dann **Remoteaufgaben** &gt; **Richtlinien aktualisieren**.
2.  Wählen Sie in der Intune-Verwaltungskonsole unten rechts die Option **Remoteaufgaben**, um den Aufgabenstatus zu überprüfen.

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Wo finde ich Hilfe zur Problembehandlung bei Richtlinien?

Siehe [Behandlung von Problemen mit Richtlinien in Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-policies-in-microsoft-intune).
