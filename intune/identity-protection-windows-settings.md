---
title: Windows Hello for Business-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Liste aller PIN-, biometrischen und Antispoofing-Einstellungen in einem Identity Protection-Profil zum Verwenden und Konfigurieren von Windows Hello for Business-Geräten auf Windows 10 in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 158840a73784516d13defa04785ca5990a9874cf
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041824"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Einstellungen für Windows 10-Geräte zum Aktivieren von Windows Hello for Business in Intune

In diesem Artikel werden die Windows Hello for Business-Einstellungen aufgeführt und beschrieben, die Sie für Windows 10-Geräte in Intune steuern können. Als Intune-Administrator können Sie diese Einstellungen konfigurieren und Windows 10-Geräten als Teil Ihrer Lösung für die mobile Geräteverwaltung (MDM) zuweisen. 

Weitere Informationen zu diesen Einstellungen finden Sie in der Windows Hello-Dokumentation unter [Configure Windows Hello for Business Policy settings](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings) (Konfigurieren der Richtlinieneinstellungen für Windows Hello for Business).


Weitere Informationen zu Windows Hello for Business-Profilen in Intune finden Sie unter [Konfigurieren von Identity Protection-Einstellungen in Microsoft Intune](identity-protection-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello for Business

- **Configure Windows Hello for Business** (Konfigurieren von Windows Hello for Business): Wählen Sie **Aktivieren** aus, um dieses Feature zu verwenden und dessen Einstellungen zu konfigurieren.
- **Minimale PIN-Länge**: Geben Sie die minimale PIN-Länge ein, die Sie auf den Geräten zulassen möchten. Die Standard-PIN-Länge ist sechs Zeichen. Die minimale PIN-Länge ist vier (4) Zeichen.
- **Maximale PIN-Länge**: Geben Sie die maximale PIN-Länge ein, die Sie auf den Geräten zulassen möchten. Die Standard-PIN-Länge ist sechs (6) Zeichen. Die maximale PIN-Länge ist 127 Zeichen.  
- **Kleinbuchstaben in PIN**: Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Kleinbuchstaben einzubeziehen. Folgende Optionen sind verfügbar:

  - **Nicht zulässig** (Standard): Hiermit wird die Verwendung von Kleinbuchstaben in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
  - **Zulässig**: Benutzer können Kleinbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
  - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Kleinbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

- **Großbuchstaben in PIN**: Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Großbuchstaben einzubeziehen. Folgende Optionen sind verfügbar:

  - **Nicht zulässig** (Standard): Hiermit wird die Verwendung von Großbuchstaben in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
  - **Zulässig**: Benutzer können Großbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
  - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Großbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

- **Sonderzeichen in PIN**: Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Sonderzeichen einzubeziehen. Folgende Optionen sind verfügbar:

  - **Nicht zulässig** (Standard): Hiermit wird die Verwendung von Sonderzeichen in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
    Gilt für diese Sonderzeichen: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Zulässig**: Benutzer können Großbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
  - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Großbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

- **PIN-Ablauf (Tage)** : Es wird empfohlen, ein Ablaufdatum für eine PIN anzugeben, nach dem sie vom Benutzer geändert werden muss. Die Standardeinstellung ist 41 Tage.

- **Remember PIN history** (PIN-Verlauf speichern): Schränkt die Wiederverwendung zuvor verwendeter PINs ein. Standardmäßig können die letzten fünf PINs nicht erneut verwendet werden.  
- **PIN-Wiederherstellung aktivieren**: Ermöglicht es dem Benutzer, seine PIN mithilfe des PIN-Wiederherstellungsdiensts von Windows Hello for Business zu ändern.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Trusted Platform Module (TPM) verwenden**: Ein TPM-Chip bietet eine zusätzliche Sicherheitsebene für Daten. Wählen Sie einen der folgenden Werte aus:  
  - **Aktivieren**: Nur Geräte mit verfügbarem TPM können Windows Hello for Business bereitstellen.
  - **Nicht konfiguriert**: Alle Geräte können Windows Hello for Business bereitstellen, selbst wenn kein verwendbares TPM vorhanden ist. Es wird zunächst versucht, ein TPM zu verwenden, sollte jedoch keins verfügbar sein, können Geräte auf die Softwareverschlüsselung zurückgreifen.  

- **Biometrische Authentifizierung zulassen**: Aktiviert die biometrische Authentifizierung, z. B. die Gesichtserkennung oder Fingerabdrücke, als Alternative zu einer PIN für Windows Hello for Business. Benutzer müssen für den Fall dennoch eine PIN konfigurieren, dass die biometrische Authentifizierung fehlschlägt. Es stehen die folgenden Optionen zur Auswahl:

  - **Aktivieren**: Windows Hello for Business ermöglicht biometrische Authentifizierung.
  - **Nicht konfiguriert** (Standard): Windows Hello for Business verhindert die biometrische Authentifizierung (für alle Kontotypen).

- **Use enhanced anti-spoofing, when available** (Erweitertes Antispoofing verwenden, falls verfügbar): Wählen Sie diese Option, wenn Antispoofing-Features von Windows Hello auf Geräten verwendet werden, die dies unterstützen. Beispiel: Erkennen eines Fotos eines Gesichts anstelle eines echten Gesichts.

  - **Aktivieren**: Windows verlangt, dass alle Benutzer Antispoofing für Gesichtsmerkmale einsetzen, sofern dies unterstützt wird.  
  - **Nicht konfiguriert** (Standard): Antispoofingkonfigurationen auf dem Gerät werden von Windows berücksichtigt.

- **Zertifikat für lokale Ressourcen**: 

  - **Aktivieren**: Ermöglicht es Windows Hello for Business, Zertifikate zur Authentifizierung bei lokalen Ressourcen zu verwenden.
  - **Nicht konfiguriert** (Standard): Verhindert, dass Windows Hello for Business Zertifikate zur Authentifizierung bei lokalen Ressourcen verwendet. Stattdessen verwenden Geräte das Standardverhalten der *lokalen schlüsselbasierten Authentifizierung*. Weitere Informationen finden Sie unter [User certificate for on-premises authentication (Benutzerzertifikat für lokale Authentifizierung)](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) in der Windows Hello-Dokumentation.  
## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
