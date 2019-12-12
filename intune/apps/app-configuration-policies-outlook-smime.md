---
title: Konfigurieren von S/MIME mit Outlook für iOS in Microsoft Intune
description: Grundlegendes zu S/MIME mit Outlook für iOS in Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9572f4accb1be232d4667d99b98beff90d81379
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000413"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Konfigurieren von S/MIME mit Outlook für iOS

S/MIME (Secure/Multipurpose Internet Mail Extensions) bietet eine zusätzliche Sicherheitsebene für E-Mails, die an ein bzw. von einem EAS-Konto (Exchange Active Sync) gesendet werden. [Microsoft Outlook](https://aka.ms/omsmime) kann S/MIME verwenden, damit Benutzer sowohl ausgehende Nachrichten als auch Anhänge verschlüsseln können. Dadurch wird sichergestellt, dass nur der vorgesehene Empfänger bei Verwendung von Office 365-Konten die Nachrichteninhalte lesen und darauf zugreifen kann. Benutzer können Nachrichten auch digital signieren, wodurch die Empfänger die Identität des Absenders überprüfen und sicherstellen können, dass die Nachricht nicht manipuliert wurde. Diese Funktion wird durch die Verwendung von Zertifikaten möglich. Weitere Informationen finden Sie unter [Grundlegendes zu S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> Diese Funktion hat sich verzögert, wird aber bald veröffentlicht.

> [!NOTE]
> In diesem Thema wird beschrieben, wie vertrauenswürdige Stammzertifikate über [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) bereitgestellt werden können. Bei Microsoft Endpoint Manager handelt es sich um eine einzelne, integrierte Endpunktverwaltungsplattform zum Verwalten aller Endpunkte. Im Microsoft Endpoint Manager Admin Center sind ConfigMgr und Microsoft Intune integriert.

## <a name="about-message-encryption"></a>Informationen zur Nachrichtenverschlüsselung
Benutzer können verschlüsselte Nachrichten an Personen in ihrer Organisation und außerhalb ihrer Organisation senden, wenn sie über den öffentlichen Teil der Verschlüsselungszertifikate verfügen. Private Schlüssel, die den Verschlüsselungszertifikaten zugeordnet sind, sollten immer durch den Empfänger der verschlüsselten Nachricht geschützt und gesichert werden. Der private Schlüssel des Verschlüsselungszertifikat wird verwendet, um die Nachricht vom Empfänger zu entschlüsseln.

Verschlüsselte Nachrichten können nur von Empfängern gelesen werden, die deren Zertifikat dem Zertifikat entspricht, das die Nachricht verschlüsselt hat. Wenn Sie versuchen, eine Nachricht an Empfänger zu senden, deren Verschlüsselungszertifikat nicht verfügbar ist, werden Sie von der App aufgefordert, diese Empfänger vor dem Senden der E-Mail zu entfernen.

## <a name="about-digital-signatures"></a>Informationen zu digitalen Signaturen
Eine digital signierte Nachricht bestätigt dem Empfänger, dass die Nachricht nicht manipuliert wurde und die Identität des Absenders authentisch ist. Empfänger können die digitale Signatur nur überprüfen, wenn sie einen E-Mail-Client verwenden, der S/MIME unterstützt.

## <a name="prerequisites"></a>Voraussetzungen
- Outlook für iOS unterstützt nur S/MIME für Office 365-Konten.
- S/MIME muss für Office 365 konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von S/MIME in Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Sie müssen über eine Zertifizierungsstelle verfügen, die Zertifikate ausstellen kann, die zum Signieren und Verschlüsseln verwendet werden können.
- Stellen Sie über Endpoint Manager vertrauenswürdige Stammzertifikate bereit. Weitere Informationen finden Sie unter [Erstellen vertrauenswürdiger Zertifikatprofile](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Verschlüsselungszertifikate müssen in Endpoint Manager importiert werden. Weitere Informationen finden Sie unter [Konfigurieren und Verwenden importierter PKCS-Zertifikate mit Intune](~/protect/certificates-imported-pfx-configure.md).
- Installieren und konfigurieren Sie den PFX-Connector für Microsoft Intune. Weitere Informationen finden Sie unter [Herunterladen, Installieren und Konfigurieren des PFX-Zertifikatconnectors für Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Die Geräte müssen für die Verwaltung mobiler Geräte (MDM) registriert sein, damit sie automatisch vertrauenswürdige Stamm- und S/MIME-Zertifikate von Endpoint Manager empfangen können.

> [!IMPORTANT]
> Sie müssen den PFX-Connector (Version 6.1911.11.0 oder höher) für Microsoft Intune herunterladen und installieren, um S/MIME-Verschlüsselungszertifikate mit Outlook für iOS verwenden zu können.

## <a name="smime-support-in-outlook-for-ios"></a>S/MIME in Outlook für iOS
Outlook für iOS unterstützt das Signieren und Verschlüsseln von Nachrichten mit S/MIME-Zertifikaten. Viele Kunden verfügen anstelle eines einzelnen Zertifikats, das sowohl das Signieren als auch das Verschlüsseln unterstützt, über separate Zertifikate für die jeweilige Aktion. Signaturzertifikate sind auf den registrierten Geräten eines Benutzers in der Regel eindeutig, während Verschlüsselungszertifikate von den registrierten Geräten eines Benutzers gemeinsam genutzt werden. Häufig verwenden Benutzer S/MIME für mehrere Jahre und haben im Laufe der Zeit andere Verschlüsselungszertifikate verwendet, wenn Zertifikate erneuert werden. Der Verlauf der Verschlüsselungszertifikate einschließlich privater Schlüssel muss auf dem Gerät des Benutzers vorhanden sein, damit E-Mails, die möglicherweise mit einem dieser Zertifikate in der Vergangenheit verschlüsselt wurden, gelesen werden können. Es ist auch möglich, ein einzelnes Zertifikat zu nutzen, das das Signieren und das Verschlüsseln unterstützt.

Outlook für iOS unterstützt zwei Möglichkeiten zum Übermitteln von Zertifikaten an Geräte, damit diese für S/MIME verwendet werden können:

- **Benutzer** können S/MIME-Zertifikate per Mail an sich selbst senden und über die Anlagen in Outlook für iOS auf ihren mobilen Geräten installieren.
- **Administratoren** können den Verlauf der Verschlüsselungszertifikate von jeder Zertifizierungsstelle in Endpoint Manager importieren. Diese Zertifikate werden dann automatisch von Endpoint Manager an alle Geräte übertragen, die vom Benutzer registriert werden. Im Allgemeinen wird SCEP (Simple Certificate Enrollment-Protokoll) zum Signieren von Zertifikaten verwendet. Mit SCEP wird der private Schlüssel generiert und auf dem registrierten Gerät gespeichert, und es wird ein eindeutiges Zertifikat an jedes Gerät übermittelt, das von einem Benutzer registriert wird und für die Nichtabstreitbarkeit verwendet werden kann. Administratoren importieren für Benutzer den Verlauf von Verschlüsselungszertifikaten in Endpoint Manager, sodass alle Verschlüsselungszertifikate des Benutzers an die Geräte übermittelt werden, die registriert werden. Schließlich unterstützt Endpoint Manager abgeleitete Anmeldeinformationen für Kunden, die Unterstützung für den NIST 800-157-Standard benötigen. Unter iOS wird das Unternehmensportal zum Abrufen von Signatur- und Verschlüsselungszertifikaten aus Intune verwendet.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Konfigurieren von Outlook für iOS S/MIME in Endpoint Manager
Führen Sie die folgenden Schritte aus, um Outlook für iOS S/MIME in Endpoint Manager einschließlich der automatischen Bereitstellung von S/MIME-Zertifikaten zu konfigurieren, die von Outlook für iOS verwendet werden können:

### <a name="add-the-microsoft-outlook-app"></a>Hinzufügen der Microsoft Outlook-App
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Fügen Sie die Microsoft Outlook für iOS-App aus dem App Store zu Endpoint Manager hinzu, oder synchronisieren Sie Outlook für iOS aus dem Apple Volume Purchase Program. Weitere Informationen finden Sie unter [Hinzufügen von iOS Store-Apps zu Microsoft Intune](~/apps/store-apps-ios.md) und [Verwalten von iOS- und macOS-Apps, die über das Apple Volume Purchase Program mit Microsoft Intune erworben wurden](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Erstellen der S/MIME-Konfigurationsrichtlinie für Outlook für iOS

In den folgenden Schritten wird erläutert, wie Sie die S/MIME-Richtlinie für Outlook für iOS in Endpoint Manager erstellen und konfigurieren. Diese Einstellungen ermöglichen die automatisierte Übermittlung der Signatur- und Verschlüsselungszertifikate.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und wählen Sie **Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** aus.<br>
Der Bereich **Add configuration policy** (Konfigurationsrichtlinie hinzufügen) wird angezeigt.
2. Geben Sie den **Namen** und die **Beschreibung** der Konfigurationsrichtlinie ein.
3. Wählen Sie **Managed devices** (Verwaltete Geräte) als **Device enrollment type** (Geräteregistrierungstyp) aus.
4. Wählen Sie für **Plattform** **iOS/iPadOS** aus.
5. Klicken Sie auf **Select the required app** (Erforderliche App auswählen), um die zuvor hinzugefügte Microsoft Outlook für iOS-App zu suchen und zuzuordnen. 
6. Klicken Sie auf **Konfigurationseinstellungen**, um Konfigurationseinstellungen hinzuzufügen. 
    - Klicken Sie neben **Configuration settings format** (Format der Konfigurationseinstellungen) auf **Use configuration designer** (Konfigurations-Designer verwenden), und übernehmen Sie die Standardeinstellungen. Weitere Informationen finden Sie unter [Microsoft Outlook-Konfigurationseinstellungen](~/apps/app-configuration-policies-outlook.md).
7. Klicken Sie auf **S/MIME**, um die **Outlook S/MIME settings** (Outlook-S/MIME-Einstellungen) anzuzeigen.
8. Legen Sie **Enable S/MIME** (S/MIME aktivieren) auf **Ja** fest.
9. Legen Sie **Deploy S/MIME certificates from Intune** (S/MIME-Zertifikate aus Intune bereitstellen) auf **Ja** fest.
10. Wählen Sie unter **Signing certificates** (Signaturzertifikate) neben der Option **Certificate profile type** (Zertifikatprofiltyp) eine der folgenden Optionen aus:
    - **SCEP:** Dieses Protokoll erstellt ein Zertifikat, das für das Gerät und den Benutzer eindeutig ist und von Microsoft Outlook zum Signieren verwendet werden kann. Weitere Informationen finden Sie unter [Konfigurieren der Infrastruktur zur Unterstützung von SCEP mit Intune](~/protect/certificates-scep-configure.md) und [Erstellen eines SCEP-Zertifikatprofils](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **PKCS imported certificates (Importierte PKCS-Zertifikate):** Bei dieser Option wird ein Zertifikat verwendet, das für den Benutzer eindeutig ist, aber möglicherweise von allen Geräten gemeinsam genutzt wird und vom Administrator im Auftrag des Benutzers in Endpoint Manager importiert wurde. Das Zertifikat wird an alle Geräte übermittelt, die von einem Benutzer registriert werden. Endpoint Manager wählt automatisch das importierte Zertifikat aus, das das Signieren unterstützt und auf dem Gerät des registrierten Benutzers bereitgestellt werden soll.
    - **Derived credentials (Abgeleitete Anmeldeinformationen):** Hier wird ein Zertifikat verwendet, das sich bereits auf dem Gerät befindet, das zum Signieren verwendet werden kann. Das Zertifikat muss mithilfe der abgeleiteten Anmeldeinformationsflows in Intune auf dem Gerät abgerufen werden.
11. Wählen Sie unter **Encryption certificates** (Verschlüsselungszertifikate) neben der Option **Certificate profile type** (Zertifikatprofiltyp) eine der folgenden Optionen aus:
    - **PKCS imported certificates (Importierte PKCS-Zertifikate):** Bei dieser Option werden alle Verschlüsselungszertifikate, die vom Administrator in Endpoint Manager importiert wurden, an alle vom Benutzer registrierten Geräte übermittelt. Endpoint Manager wählt automatisch das importierte Zertifikat bzw. die Zertifikate aus, die die Verschlüsselung unterstützen und auf dem Gerät des registrierten Benutzers bereitgestellt werden sollen.
    - **Derived credentials (Abgeleitete Anmeldeinformationen):** Hier wird ein Zertifikat verwendet, das sich bereits auf dem Gerät befindet, das zum Signieren verwendet werden kann. Das Zertifikat muss mithilfe der abgeleiteten Anmeldeinformationsflows in Intune auf dem Gerät abgerufen werden.
12. Wählen Sie neben **End-user notifications** (Benutzerbenachrichtigungen) die Option zum Benachrichtigen von Endbenutzern aus, indem Sie auf **Unternehmensportal** oder **E-Mail** klicken, um S/MIME-Zertifikate für Outlook für iOS abzurufen.

    Unter iOS müssen Benutzer die Unternehmensportal-App verwenden, um S/MIME-Zertifikate abzurufen. Endpoint Manager informiert den Benutzer darüber, dass er die Unternehmensportal-App starten muss, um über den Abschnitt „Benachrichtigungen“ des Unternehmensportals, eine Pushbenachrichtigung und/oder eine E-Mail S/MIME-Zertifikate abzurufen. Wenn Benutzer auf eine der Benachrichtigungen klicken, wird eine Angebotsseite angezeigt, die über den Fortschritt zum Abrufen des Zertifikats informiert. Nachdem die Zertifikate abgerufen wurden, kann der Benutzer S/MIME innerhalb von Microsoft Outlook für iOS verwenden, um E-Mails zu signieren und zu verschlüsseln.
    
    Die Benutzerbenachrichtigungen enthalten die folgenden Optionen:
       - **Unternehmensportal:** Wenn diese Option ausgewählt wird, erhalten Benutzer eine Pushbenachrichtigung auf ihrem Gerät, sodass sie auf die Angebotsseite im Unternehmensportal gelangen, auf die S/MIME-Zertifikate abgerufen werden.
        - **E-Mail:** Hier wird eine E-Mail an den Endbenutzer gesendet, in der er darüber informiert wird, dass er die Unternehmensportal-App starten muss, um S/MIME-Zertifikate abzurufen. Wenn sich der Benutzer beim Klicken auf den Link in der Mail auf dem registrierten iOS-Gerät befindet, wird er ins Unternehmensportal umgeleitet, um die Zertifikate abzurufen.
    
13. Klicken Sie auf **Zuweisungen**, um den Azure AD-Gruppen die App-Konfigurationsrichtlinie zuzuweisen. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen finden Sie unter [App-Konfigurationsrichtlinien für Microsoft Intune](app-configuration-policies-overview.md).
