---
title: 'S/MIME für die Signierung und Verschlüsselung von E-Mails: Azure | Microsoft-Dokumentation'
description: Verwenden oder Aktivieren Sie S/MIME zum Signieren und Verschlüsseln von E-Mails in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0eac3c1d6739ca70e485b0327e3257ba8d32d2b
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321654"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>S/MIME für die Signierung und Verschlüsselung von E-Mails in Intune

S/MIME-bietet durch Ver- und Entschlüsselungen eine zusätzliche Sicherheitsstufe für Ihre E-Mail-Kommunikation. Microsoft Intune kann mit S/MIME E-Mails an mobile Geräte signieren und verschlüsseln, die unter iOS, Windows, Windows Phone, Android und macOS ausgeführt werden.

Auf iOS-Geräten können Sie ein von Intune verwaltetes E-Mail-Profil erstellen, das S/MIME und Zertifikate zum Signieren und Verschlüsseln eingehender und ausgehender E-Mails verwendet. Für andere Plattformen wird S/MIME möglicherweise nicht unterstützt. Wenn S/MIME unterstützt wird, können Sie Zertifikate installieren, welche die S/MIME-Signierung und -Verschlüsselung verwenden. Anschließend kann ein Benutzer S/MIME in seiner E-Mail-Anwendung aktivieren.

Weitere Informationen zu S/MIME für die Signierung und Verschlüsselung von E-Mails finden Sie unter [S/MIME für die Nachrichtensignierung und -verschlüsselung](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

## <a name="signing-certificates"></a>Signaturzertifikate

Mithilfe von Signaturzertifikaten kann die E-Mail-App des Clients sicher mit dem E-Mail-Server kommunizieren.

Für die Verwendung von Signaturzertifikaten müssen Sie eine Vorlage in Ihrer Zertifizierungsstelle erstellen, deren Schwerpunkt auf der Signierung liegt. In der Zertifizierungsstelle von Microsoft Active Directory werden unter [Konfigurieren der Zertifikatvorlage des Servers](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) die Schritte für die Erstellung der Zertifikatvorlagen aufgeführt.

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