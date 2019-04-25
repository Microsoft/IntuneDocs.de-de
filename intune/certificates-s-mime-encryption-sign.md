---
title: 'Signieren und Verschlüsseln der E-Mails mit S/MIME: Microsoft Intune – Azure | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie digitale E-Mail-Zertifikate in Microsoft Intune zum Signieren und Verschlüsseln von E-Mails auf Geräten verwenden können. Diese Zertifikate werden als „S/MIME“ bezeichnet und über Gerätekonfigurationsprofile konfiguriert. Signatur- und Verschlüsselungszertifikate verwenden PKCS oder private Zertifikate und verwenden einen Connector, um Zertifikate zu importieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e288cdf426f2fda2638e49350515182107d9bba
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508291"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>S/MIME-Übersicht zum Signieren und Verschlüsseln von E-Mails in Intune

E-Mail-Zertifikate, auch bekannt als S/MIME-Zertifikate, bieten zusätzliche Sicherheit für Ihre E-Mail-Kommunikation durch Ver- und Entschlüsselung. Microsoft Intune kann S/MIME-Zertifikate verwenden, um E-Mails auf mobilen Geräten mit den folgenden Plattformen zu signieren und zu verschlüsseln:

- Android
- iOS
- macOS
- Windows 10 und höher
- Windows Phone

Auf iOS-Geräten können Sie ein von Intune verwaltetes E-Mail-Profil erstellen, das S/MIME und Zertifikate zum Signieren und Verschlüsseln eingehender und ausgehender E-Mails verwendet. Für andere Plattformen wird S/MIME möglicherweise nicht unterstützt. Wenn S/MIME unterstützt wird, installieren Sie Zertifikate, welche die S/MIME-Signatur und -Verschlüsselung verwenden. Anschließend aktiviert ein Endbenutzer S/MIME in seiner E-Mail-Anwendung.

Weitere Informationen zur S/MIME-E-Mail-Signatur und -Verschlüsselung finden Sie unter [S/MIME for message signing and encryption (S/MIME für die Nachrichtensignatur und -verschlüsselung)](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

In diesem Artikel erhalten Sie eine Übersicht über die Verwendung von S/MIME-Zertifikaten zum Signieren und Verschlüsseln von E-Mails auf Ihren Geräten.

## <a name="signing-certificates"></a>Signaturzertifikate

Mithilfe von Signaturzertifikaten kann die E-Mail-App des Clients sicher mit dem E-Mail-Server kommunizieren.

Für die Verwendung von Signaturzertifikaten müssen Sie eine Vorlage in Ihrer Zertifizierungsstelle erstellen, deren Schwerpunkt auf dem Signieren liegt. In der Zertifizierungsstelle von Microsoft Active Directory werden unter [Konfigurieren der Zertifikatvorlage des Servers](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) die Schritte für die Erstellung der Zertifikatvorlagen aufgeführt.

Signaturzertifikate in Intune verwenden PKCS-Zertifikate. Unter [Konfigurieren und Verwenden von PKCS-Zertifikate](certficates-pfx-configure.md) wird beschrieben, wie PKCS-Zertifikate in Ihrer Intune-Umgebung bereitgestellt und verwendet werden. Diese Schritte umfassen:

- Das Herunterladen und Installieren von Microsoft Intune Certificate Connector zur Unterstützung von PKCS-Zertifikatanforderungen.
- Das Erstellen eines vertrauenswürdigen Stammzertifikatprofil für Ihre Geräte. Dieser Schritt beinhaltet die Verwendung von vertrauenswürdigen Stamm- und Zwischenzertifikaten für Ihre Zertifizierungsstelle und die Bereitstellung des Profils für Geräte.
- Erstellen Sie mit der von Ihnen erstellten Zertifikatvorlage ein PKCS-Zertifikatprofil. Dieses Profil stellt Signaturzertifikate für Geräte aus und stellt das PKCS-Zertifikatprofil für Geräte bereit.

Sie können ein Signaturzertifikat auch für einen bestimmten Benutzer importieren. Das Signaturzertifikat wird auf allen Geräten bereitgestellt, die von einem Benutzer registriert werden. Verwenden Sie zum Importieren von Zertifikaten in Intune die [PowerShell-Cmdlets in GitHub](https://github.com/Microsoft/Intune-Resource-Access). Wenn Sie ein PKCS-Zertifikat bereitstellen möchten, das in Intune für die E-Mail-Signierung importiert wurde, müssen Sie die Schritte unter [Konfigurieren und Verwenden von PKCS-Zertifikaten mit Intune](certficates-pfx-configure.md) ausführen. Diese Schritte umfassen:

- Das Herunterladen und Installieren von PFX Certificate Connector für Microsoft Intune. Dieser Connector stellt importierte PKCS-Zertifikate für Geräte bereit.
- Das Importieren von S/MIME-E-Mail-Signaturzertifikaten in Intune.
- Das Erstellen eines importierten PKCS-Zertifikatprofils. Dieses Profil stellt importierte PKCS-Zertifikate für die entsprechenden Geräte des Benutzers bereit.

## <a name="encryption-certificates"></a>Verschlüsselungszertifikate

Mit für die Verschlüsselung verwendeten Zertifikaten wird bestätigt, dass eine verschlüsselte E-Mail nur von dem beabsichtigten Empfänger entschlüsselt werden kann. Die S/MIME-Verschlüsselung stellt eine zusätzliche Sicherheitsstufe dar, die in der E-Mail-Kommunikation verwendet werden kann.

Beim Senden einer verschlüsselten E-Mail an einen anderen Benutzer wird der öffentliche Schlüssel des Verschlüsselungszertifikats dieses Benutzers abgerufen und die von Ihnen gesendete E-Mail verschlüsselt. Der Empfänger entschlüsselt die E-Mail mithilfe des privaten Schlüssels auf seinem Gerät. Benutzer können über einen Verlauf der Zertifikate verfügen, die zum Verschlüssen von E-Mails verwendet wurden. Jedes dieser Zertifikate muss für alle Geräte eines bestimmten Benutzers bereitgestellt werden, damit dessen E-Mails erfolgreich entschlüsselt werden können.

Es wird empfohlen, E-Mail-Verschlüsselungszertifikate nicht in Intune zu erstellen. Intune unterstützt die Ausstellung von PKCS-Zertifikaten, die Verschlüsselungen unterstützen, und erstellt ein eindeutiges Zertifikat pro Gerät. Bei einem S/MIME-Verschlüsselungsszenario, in dem das Verschlüsselungszertifikat von allen Geräten des Benutzers gemeinsam genutzt werden sollte, ist die Erstellung eines eindeutigen Zertifikats pro Gerät nicht ideal.

Zum Bereitstellen von S/MIME-Zertifikate mit Intune müssen Sie sämtliche Verschlüsselungszertifikate eines Benutzers in Intune importieren. Anschließend stellt Intune alle diese Zertifikate für die einzelnen Geräte bereit, die vom Benutzer registriert werden. Verwenden Sie zum Importieren von Zertifikaten in Intune die [PowerShell-Cmdlets in GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Wenn Sie ein PKCS-Zertifikat bereitstellen möchten, das in Intune für die E-Mail-Verschlüsselung importiert wurde, müssen Sie die Schritte unter [Konfigurieren und Verwenden von PKCS-Zertifikaten mit Intune](certficates-pfx-configure.md) ausführen. Diese Schritte umfassen:

- Das Herunterladen und Installieren von PFX Certificate Connector für Microsoft Intune. Dieser Connector stellt importierte PKCS-Zertifikate für Geräte bereit.
- Das Importieren von S/MIME-E-Mail-Verschlüsselungszertifikaten in Intune.
- Das Erstellen eines importierten PKCS-Zertifikatprofils. Dieses Profil stellt importierte PKCS-Zertifikate für die entsprechenden Geräte des Benutzers bereit.

 > [!NOTE]
 > Importierte S/MIME-Verschlüsselungszertifikate werden von Intune entfernt, wenn Unternehmensdaten entfernt werden oder wenn die Registrierung von Benutzern über die Verwaltung aufgehoben wird. Zertifikate werden jedoch nicht von der Zertifizierungsstelle gesperrt.

## <a name="smime-email-profiles"></a>S/MIME-E-Mail-Profile

Nachdem Sie S/MIME-Zertifikatprofile für die Signierung und Verschlüsselung erstellt haben, können Sie [S/MIME für native iOS-E-Mails aktivieren](email-settings-ios.md).

## <a name="next-steps"></a>Nächste Schritte

- [Konfigurieren und Verwenden von SCEP-Zertifikaten mit Intune](certificates-scep-configure.md)
- [Konfigurieren und Verwenden von PKCS-Zertifikaten mit Intune](certficates-pfx-configure.md)
- [Verwenden einer Partnerzertifizierungsstelle](certificate-authority-add-scep-overview.md)
- [Einrichten des Intune Certificate Connectors für den Symantec PKI-Manager-Webdienst](certificates-symantec-configure.md)
