---
title: Windows Hello for Business-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Liste aller PIN-, biometrischen und Antispoofing-Einstellungen in einem Identity Protection-Profil zum Verwenden und Konfigurieren von Windows Hello for Business-Geräten auf Windows 10 in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: f49ea9e1e59fadcb90a773e362ec3ef41e25ab63
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502231"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Einstellungen für Windows 10-Geräte zum Aktivieren von Windows Hello for Business in Intune

In diesem Artikel werden die Windows Hello for Business-Einstellungen aufgeführt und beschrieben, die Sie für Windows 10-Geräte in Intune steuern können. Als Intune-Administrator können Sie diese Einstellungen konfigurieren und Windows 10-Geräten als Teil Ihrer Lösung für die mobile Geräteverwaltung (MDM) zuweisen. 

Weitere Informationen zu diesen Einstellungen finden Sie in der Windows Hello-Dokumentation unter [Configure Windows Hello for Business Policy settings](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings) (Konfigurieren der Richtlinieneinstellungen für Windows Hello for Business).


Weitere Informationen zu Windows Hello for Business-Profilen in Intune finden Sie unter [Konfigurieren von Identity Protection-Einstellungen in Microsoft Intune](identity-protection-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello for Business
- **Konfigurieren Sie Windows Hello for Business**:
  - **Nicht konfiguriert** – Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen nicht mit Intune steuern möchten. Vorhandene Windows Hello for Business-Einstellungen auf Geräten mit Windows 10 werden nicht geändert. Alle anderen Einstellungen in dem Bereich sind nicht verfügbar.

  - **Deaktiviert** – Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Einstellung aus. In diesem Fall ist keine der anderen Einstellungen auf dem Bildschirm verfügbar.
  - **Aktiviert** – Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen konfigurieren möchten.  
  
  **Standardeinstellung:** Nicht konfiguriert

  Wenn diese *Option auf aktiviert*festgelegt ist, sind die folgenden Einstellungen verfügbar:

  - **PIN-Mindestlänge**  
    Geben Sie eine minimale PIN-Länge für Geräte an, um die Anmeldung zu unterstützen. Windows-Geräte Standardwerte sind sechs Zeichen, diese Einstellung kann jedoch mindestens vier bis 127 Zeichen erzwingen. 

    **Standardeinstellung:** *Nicht konfiguriert*

  - **Höchstlänge für PIN**  
  Geben Sie eine maximale PIN-Länge für Geräte an, um die Anmeldung zu unterstützen. Windows-Geräte Standardwerte sind sechs Zeichen, diese Einstellung kann jedoch mindestens vier bis 127 Zeichen erzwingen.  

    **Standardeinstellung:** *Nicht konfiguriert*  

  - **Kleinbuchstaben in PIN**  
    Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Kleinbuchstaben einzubeziehen. Folgende Optionen sind verfügbar:

    - **Nicht zulässig** : Hiermit wird die Verwendung von Kleinbuchstaben in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
    - **Zulässig**: Benutzer können Kleinbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
    - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Kleinbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

  - **Großbuchstaben in PIN**  
    Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Großbuchstaben einzubeziehen. Folgende Optionen sind verfügbar:

    - **Nicht zulässig**: Hiermit wird die Verwendung von Großbuchstaben in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
    - **Zulässig**: Benutzer können Großbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
    - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Großbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

  - **Sonderzeichen in PIN**  
    Sie können eine stärkere PIN erzwingen, indem Sie von Endbenutzern fordern, Sonderzeichen einzubeziehen. Gilt für diese Sonderzeichen: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  

    Folgende Optionen sind verfügbar:
    - **Nicht zulässig** : Hiermit wird die Verwendung von Sonderzeichen in der PIN von Benutzern blockiert. Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.
    - **Zulässig**: Benutzer können Großbuchstaben in der PIN verwenden, aber es ist nicht erforderlich.
    - **Erforderlich**: Benutzer müssen in ihre PIN mindestens einen Großbuchstaben einbeziehen. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

    **Standard**: nicht zulässig

  - **PIN-Ablauf (Tage)**  
    Es wird empfohlen, ein Ablaufdatum für eine PIN anzugeben, nach dem sie vom Benutzer geändert werden muss. Windows-Geräte Standardwerte sind 41 Tage.

    **Standard**: Nicht konfiguriert

  - **PIN-Verlauf speichern**  
    Schränkt die Wiederverwendung zuvor verwendeter PINs ein. Windows-Geräte verhindern standardmäßig die Wiederverwendung der letzten fünf Pins.  

    **Standard**: Nicht konfiguriert  

  - **PIN-Wiederherstellung aktivieren**   
    Ermöglicht es Benutzern, den Windows Hello for Business-Pin-Wiederherstellungs Dienst zu verwenden. 
    
    - **Aktiviert** : der geheime Schlüssel für die Pin-Wiederherstellung wird auf dem Gerät gespeichert, und der Benutzer kann bei Bedarf die PIN ändern.  
    - **Deaktiviert** : das Wiederherstellungs Geheimnis wird nicht erstellt oder gespeichert.

    **Standardeinstellung:** Nicht konfiguriert

  - **Trusted Platform Module (TPM) verwenden**   
    Ein TPM-Chip bietet eine zusätzliche Sicherheitsebene für Daten.  

    - **Aktiviert**: Nur Geräte mit verfügbarem TPM können Windows Hello for Business bereitstellen.
    - **Nicht konfiguriert**: Geräte versuchen zunächst, ein TPM zu verwenden. Wenn diese Option nicht verfügbar ist, können sie die Softwareverschlüsselung verwenden.
    
    **Standardeinstellung:** Nicht konfiguriert

  - **Biometrische Authentifizierung zulassen**  
     Aktiviert die biometrische Authentifizierung, z. B. die Gesichtserkennung oder Fingerabdrücke, als Alternative zu einer PIN für Windows Hello for Business. Benutzer müssen für den Fall dennoch eine PIN konfigurieren, dass die biometrische Authentifizierung fehlschlägt. Es stehen die folgenden Optionen zur Auswahl:

    - **Aktivieren**: Windows Hello for Business ermöglicht biometrische Authentifizierung.
    - **Nicht konfiguriert**: Windows Hello for Business verhindert die biometrische Authentifizierung (für alle Kontotypen).

    **Standardeinstellung:** Nicht konfiguriert

  - **Erweitertes Antispoofing verwenden, falls verfügbar**  
    Konfiguriert, ob die Antispoofingfeatures von Windows Hello auf Geräten verwendet werden, die diese unterstützen (z. B. Erkennung eines Fotos von einem Gesicht anstelle eines echten Gesichts).  
    - **Aktivieren**: Windows verlangt, dass alle Benutzer Antispoofing für Gesichtsmerkmale einsetzen, sofern dies unterstützt wird.
    - **Nicht konfiguriert**: Antispoofingkonfigurationen auf dem Gerät werden von Windows berücksichtigt.

    **Standardeinstellung:** Nicht konfiguriert

  - **Zertifikat für lokale Ressourcen**  

    - **Aktivieren**: Ermöglicht es Windows Hello for Business, Zertifikate zur Authentifizierung bei lokalen Ressourcen zu verwenden.
    - **Nicht konfiguriert**: Verhindert, dass Windows Hello for Business Zertifikate zur Authentifizierung bei lokalen Ressourcen verwendet. Stattdessen verwenden Geräte das Standardverhalten der *lokalen schlüsselbasierten Authentifizierung*. Weitere Informationen finden Sie unter [User certificate for on-premises authentication (Benutzerzertifikat für lokale Authentifizierung)](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) in der Windows Hello-Dokumentation.  

  **Standardeinstellung:** Nicht konfiguriert

- **Verwenden von Sicherheitsschlüsseln zur Anmeldung**  
  Diese Einstellung ist für Geräte mit Windows 10, Version 1903 oder höher, verfügbar. Verwenden Sie es, um die Unterstützung für die Verwendung von Windows Hello-Sicherheits Schlüsseln für die Anmeldung zu verwalten.  

  - **Aktiviert** : Benutzer können einen Windows Hello-Sicherheitsschlüssel als Anmelde Informationen für PCs verwenden, die diese Richtlinie als Ziel verwenden. 
  - **Deaktiviert** : Sicherheitsschlüssel sind deaktiviert und können von Benutzern nicht zum Anmelden bei PCs verwendet werden.   

  **Standardeinstellung:** Nicht konfiguriert

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../configuration/device-profile-assign.md) und [Überwachen von Profilen](../configuration/device-profile-monitor.md)
