---
title: Konfigurieren von Identity Protection-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen eines Geräteprofils zum Festlegen der Windows Hello for Business-Einstellungen auf Windows 10-Geräten in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317914"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Konfigurieren von Identity Protection-Einstellungen in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Über Identity Protection-Profile wird gesteuert, wie Windows Hello for Business auf verwalteten Windows 10-Geräten bereitgestellt und konfiguriert wird. Erstellen Sie dieses Profil, um Folgendes zu konfigurieren:  
* Windows Hello for Business-Verfügbarkeit für Geräte und Benutzer
* Geräte-PIN-Anforderungen
* Für die Anmeldung bei ihren Geräten zulässige und unzulässige Benutzergesten  

 Sie können dieses Profil zur Auswahl von Benutzer- und Gerätegruppen oder allen Benutzern und allen Geräten zuweisen. Gruppen erhalten das Identity Protection-Profil, wenn sie bei Intune einchecken.    

Verwenden Sie die Informationen in diesem Artikel, um ein Identity Protection-Profil zu erstellen. [Weisen Sie dann Ihr Profil](device-profile-assign.md) Benutzer- und Gerätegruppen zu.

Dieses Feature gilt für das ausgeführte Gerät:  
- Windows 10 und höher
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Erstellen eines Geräteprofils mit Identity Protection-Einstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das Identity Protection-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Option **Windows 10 und höher** aus. Windows Hello for Business wird nur auf Geräten mit Windows 10 und höher unterstützt.
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Identity Protection** aus.
7. Wählen Sie im Bereich „Windows Hello for Business“ unter den folgenden Optionen für die Konfiguration von Windows Hello for Business aus:
    * Deaktiviert. Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Einstellung aus. In diesem Fall ist keine der anderen Einstellungen auf dem Bildschirm verfügbar.
    * Aktiviert Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen konfigurieren möchten.  

8. Wenn Sie im letzten Schritt **Aktiviert** ausgewählt haben, konfigurieren Sie die erforderlichen Einstellungen, die auf die registrierten Zielgeräte mit Windows 10 und Windows 10 Mobile sowie auf die Benutzer angewendet werden.

> [!NOTE]
> Wenn Sie Identity Protection-Profile nur für Benutzer zuweisen, wird der Gerätekontext standardmäßig auf **Nicht konfiguriert** gesetzt.  

   - **PIN-Mindestlänge**/**Maximale PIN-Länge**. Konfiguriert Geräte für die Verwendung der von Ihnen angegebenen minimalen und maximalen PIN-Länge, um eine sichere Anmeldung zu gewährleisten. Die Standard-PIN-Länge beträgt 6 Zeichen, aber Sie können eine Mindestlänge von 4 Zeichen erzwingen. Die maximale PIN-Länge ist 127 Zeichen.  

   - **Kleinbuchstaben in PIN**/**Großbuchstaben in PIN**/**Sonderzeichen in PIN**. Sie können eine stärkere PIN erzwingen, indem Sie die Nutzung von Großbuchstaben, Kleinbuchstaben und Sonderzeichen in der PIN vorschreiben. Es stehen die folgenden Optionen zur Auswahl:

     - **Zulässig**. Benutzer können den Zeichentyp in ihrer PIN verwenden, aber es ist nicht zwingend erforderlich.

     - **Erforderlich**. Benutzer müssen mindestens einen der Zeichentypen in ihrer PIN verwenden. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

     - **Nicht zulässig** (Standard). Benutzer dürfen diese Zeichentypen in ihrer PIN nicht verwenden. (Dieses Verhalten tritt auch auf, wenn die Einstellung nicht konfiguriert ist.)<br>Gilt für diese Sonderzeichen: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN-Ablauf (Tage)**. Es wird empfohlen, ein Ablaufdatum für eine PIN anzugeben, nach dem sie vom Benutzer geändert werden muss. Die Standardeinstellung ist 41 Tage.

   - **PIN-Verlauf speichern**. Schränkt die Wiederverwendung zuvor verwendeter PINs ein. Standardmäßig können die letzten fünf PINs nicht erneut verwendet werden.  
   - **PIN-Wiederherstellung aktivieren**: Ermöglicht es dem Benutzer, seine PIN mithilfe des PIN-Wiederherstellungsdiensts von Windows Hello for Business zu ändern. 
       - **Aktivieren**. Der Clouddienst verschlüsselt ein Geheimnis für die PIN-Wiederherstellung, das auf dem Gerät gespeichert wird. Der Benutzer kann seine PIN bei Bedarf ändern.  
       - **Nicht konfiguriert** (Standardeinstellung). Es wird kein Geheimnis für die PIN-Wiederherstellung erstellt oder gespeichert. Wenn der Benutzer seine PIN vergisst, gibt es nur eine Möglichkeit, eine neue PIN zu erhalten: Er muss die vorhandene PIN löschen und eine neue erstellen. Infolgedessen muss sich der Benutzer bei allen Diensten, auf die er mit der alten PIN zugreifen konnte, neu registrieren.  
   
   - **Trusted Platform Module (TPM) verwenden**. Ein TPM-Chip bietet eine zusätzliche Sicherheitsebene für Daten. Wählen Sie einen der folgenden Werte aus:  
     - **Aktivieren**. Nur Geräte mit verfügbarem TPM können Windows Hello for Business bereitstellen.
     - **Nicht konfiguriert**. Alle Geräte können Windows Hello for Business bereitstellen, selbst wenn kein verwendbares TPM vorhanden ist. Es wird zunächst versucht, ein TPM zu verwenden, sollte jedoch keins verfügbar sein, können Geräte auf die Softwareverschlüsselung zurückgreifen.  

   - **Biometrische Authentifizierung zulassen**. Aktiviert die biometrische Authentifizierung, z. B. die Gesichtserkennung oder Fingerabdrücke, als Alternative zu einer PIN für Windows Hello for Business. Benutzer müssen für den Fall dennoch eine PIN konfigurieren, dass die biometrische Authentifizierung fehlschlägt. Es stehen die folgenden Optionen zur Auswahl:

     - **Aktivieren**. Windows Hello for Business ermöglicht biometrische Authentifizierung.
     - **Nicht konfiguriert** (Standardeinstellung). Windows Hello for Business verhindert die biometrische Authentifizierung (für alle Arten von Konten).

   - **Erweitertes Antispoofing verwenden, falls verfügbar**. Konfiguriert, ob die Antispoofingfeatures von Windows Hello auf Geräten verwendet werden, die diese unterstützen (z. B. Erkennung eines Fotos von einem Gesicht anstelle eines echten Gesichts).
       - **Aktivieren**. Windows erfordert, dass alle Benutzer Antispoofing für Gesichtsmerkmale einsetzen, sofern dies unterstützt wird.  
       - **Nicht konfiguriert** (Standardeinstellung). Antispoofingkonfigurationen auf dem Gerät werden von Windows berücksichtigt.

   - **Zertifikat für lokale Ressourcen**. 
       - **Aktivieren**. Ermöglicht es Windows Hello for Business, Zertifikate zur Authentifizierung bei lokalen Ressourcen zu verwenden.
       - **Nicht konfiguriert** (Standardeinstellung). Verhindert, dass Windows Hello for Business Zertifikate zur Authentifizierung bei lokalen Ressourcen verwendet.  
9. Klicken Sie auf **OK**, um Ihr Profil zu speichern.  

Das Profil wird erstellt und in der Liste **Gerätekonfigurationsprofile** angezeigt. Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, finden Sie weitere Informationen unter [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
