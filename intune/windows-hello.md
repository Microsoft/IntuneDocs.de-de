---
title: Integrieren von Windows Hello for Business in Microsoft Intune
titleSuffix: 
description: "Erfahren Sie, wie Sie eine Richtlinie zum Steuern der Verwendung von Windows Hello for Business auf verwalteten Geräten erstellen."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46bb82fd49fa58e87c22c8bf0abb57e1587b8b40
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Integrieren von Windows Hello for Business in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Sie können Windows Hello for Business (früher Microsoft Passport for Work) in Microsoft Intune integrieren.

 Hello for Business ist eine alternative Anmeldemethode, die Active Directory oder ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen. Damit können Sie anstelle eines Kennworts eine *Benutzergeste* zur Anmeldung verwenden. Eine Benutzeraktion kann eine einfache PIN, eine biometrische Authentifizierung wie Windows Hello oder ein externes Gerät sein, z. B. ein Fingerabdruckleser.

Intune integriert Hello for Business auf zwei Arten:

-   Sie können mithilfe einer Intune-Richtlinie steuern, welche Aktionen von Benutzern zum Anmelden verwendet werden können.

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Bei Desktop- und mobilen Versionen von Windows 10 vor dem Anniversary Update konnten Sie zwei unterschiedliche PINS für die Authentifizierung bei Ressourcen festlegen:
- Die **Geräte-PIN** konnte zum Entsperren des Geräts und zur Verbindung mit Cloudressourcen verwendet werden.
- Die **Arbeits-PIN** wurde für den Zugang zu Azure AD-Ressourcen auf persönlichen Geräten von Benutzern (BYOD) verwendet.

>Im Anniversary Update wurden diese beiden PINs in eine einzige Geräte-PIN zusammengeführt.
Dieser neue PIN-Wert wird jetzt sowohl von allen Intune-Konfigurationsrichtlinien, die Sie zum Steuern der Geräte-PIN festlegen, als auch von allen konfigurierten Windows Hello for Business-Richtlinien festgelegt.
Wenn Sie beide Richtlinientypen für die PIN-Steuerung eingerichtet haben, wird sowohl auf Desktop- als auch auf mobilen Geräten mit Windows 10 die Windows Hello for Business-Richtlinie angewendet.
Um sicherzustellen, dass Richtlinienkonflikte gelöst werden und dass die PIN-Richtlinie korrekt angewendet wird, aktualisieren Sie Ihre Windows Hello for Business-Richtlinie auf die Einstellungen in der Konfigurationsrichtlinie. Fordern Sie auch die Benutzer auf, ihre Geräte in der Unternehmensportal-App zu synchronisieren.



## <a name="create-a-windows-hello-for-business-policy"></a>Erstellen einer Windows Hello for Business-Richtlinie

1.  Wählen Sie im Azure-Portal **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.

2.  Wählen Sie auf der Seite „Intune“ die Option **Geräteregistrierung** aus, und klicken Sie anschließend auf **Windows-Registrierung** > **Windows Hello for Business**.

3.  Wählen Sie auf der daraufhin geöffneten Seite die **Standardeinstellungen** aus.

4.  Klicken Sie auf der Seite **Alle Benutzer** auf **Eigenschaften**, und geben Sie einen **Namen** und eine optionale **Beschreibung** für die Einstellungen für Windows Hello for Business ein.

5. Klicken Sie auf der Seite **Alle Benutzer** auf **Einstellungen**, und wählen Sie für **Windows Hello for Business konfigurieren** aus Folgendem aus:

    - **Deaktiviert**. Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Einstellung aus. In diesem Fall ist keine der anderen Einstellungen auf dem Bildschirm verfügbar.
    - **Aktiviert**. Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen konfigurieren möchten.
    - **Nicht konfiguriert**. Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen nicht mit Intune steuern möchten. Vorhandene Windows Hello for Business-Einstellungen auf Geräten mit Windows 10 werden nicht geändert. Alle anderen Einstellungen auf der Seite sind nicht verfügbar.

6.  Wenn Sie im letzten Schritt **Aktiviert** ausgewählt haben, konfigurieren Sie die erforderlichen Einstellungen, die auf alle registrierten Geräte mit Windows 10 und Windows 10 Mobile angewendet werden.

 - **Trusted Platform Module (TPM) verwenden**. Ein TPM-Chip bietet eine zusätzliche Sicherheitsebene für Daten.<br>Wählen Sie einen der folgenden Werte aus:

     - **Erforderlich** (Standard). Nur Geräte mit verfügbarem TPM können Windows Hello for Business bereitstellen.
     - **Bevorzugt**. Geräte versuchen zunächst, ein TPM zu verwenden. Wenn diese Option nicht verfügbar ist, können sie die Softwareverschlüsselung verwenden.

 - **Minimale PIN-Länge vorschreiben**/**Maximale PIN-Länge vorschreiben**. Konfiguriert Geräte für die Verwendung der von Ihnen angegebenen minimalen und maximalen PIN-Länge, um eine sichere Anmeldung zu gewährleisten. Die Standard-PIN-Länge beträgt 6 Zeichen, aber Sie können eine Mindestlänge von 4 Zeichen erzwingen. Die maximale PIN-Länge ist 127 Zeichen.

 - **Kleinbuchstaben in PIN vorschreiben**/**Großbuchstaben in PIN vorschreiben**/**Sonderzeichen in PIN vorschreiben**. Sie können eine stärkere PIN erzwingen, indem Sie die Nutzung von Großbuchstaben, Kleinbuchstaben und Sonderzeichen in der PIN vorschreiben. Es stehen die folgenden Optionen zur Auswahl:

     - **Zulässig**. Benutzer können den Zeichentyp in ihrer PIN verwenden, aber es ist nicht zwingend erforderlich.

     - **Erforderlich**. Benutzer müssen mindestens einen der Zeichentypen in ihrer PIN verwenden. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.

     - **Nicht zulässig** (Standard). Benutzer dürfen diese Zeichentypen in ihrer PIN nicht verwenden. (Dies trifft auch zu, wenn die Einstellung nicht konfiguriert ist.)<br>Gilt für diese Sonderzeichen: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

 - **PIN-Ablauf (Tage)**. Es wird empfohlen, ein Ablaufdatum für eine PIN anzugeben, nach dem sie vom Benutzer geändert werden muss. Die Standardeinstellung ist 41 Tage.

 - **PIN-Verlauf speichern**. Schränkt die Wiederverwendung zuvor verwendeter PINs ein. Standardmäßig können die letzten fünf PINs nicht erneut verwendet werden.

 - **Biometrische Authentifizierung zulassen**. Aktiviert die biometrische Authentifizierung, z. B. die Gesichtserkennung oder Fingerabdrücke, als Alternative zu einer PIN für Windows Hello for Business. Benutzer müssen für den Fall dennoch eine PIN konfigurieren, dass die biometrische Authentifizierung fehlschlägt. Es stehen die folgenden Optionen zur Auswahl:

     - **Ja**. Windows Hello for Business ermöglicht biometrische Authentifizierung.
     - **Nein**. Windows Hello for Business verhindert die biometrische Authentifizierung (für alle Arten von Konten).

 - **Erweitertes Antispoofing verwenden, falls verfügbar**. Konfiguriert, ob die Antispoofingfeatures von Windows Hello auf Geräten verwendet werden, die diese unterstützen (z. B. Erkennung eines Fotos von einem Gesicht anstelle eines echten Gesichts).<br>Wenn diese Option auf **Ja** festgelegt ist, erfordert Windows von allen Benutzern die Verwendung von Antispoofing für Gesichtsmerkmale, sofern dies unterstützt wird.

 - **Anmeldung per Telefon verwenden**. Wenn diese Option auf **Ja** festgelegt ist, können die Benutzer einen Remote-Passport als tragbares Begleitgerät für die Authentifizierung von Desktopcomputern verwenden. Der Desktopcomputer muss Azure Active Directory angehören, und das Begleitgerät muss mit einer Windows Hello for Business-PIN konfiguriert werden.

## <a name="windows-holographic-for-business-support"></a>Unterstützung durch Windows Holographic for Business

Windows Holographic for Business unterstützt die folgenden Windows Hello for Business-Einstellungen:

- Trusted Platform Module (TPM) verwenden
- Mindestlänge für PIN
- Höchstlänge für PIN
- Kleinbuchstaben in PIN
- Großbuchstaben in PIN
- Sonderzeichen in PIN
- PIN-Ablauf (Tage)
- PIN-Verlauf speichern

## <a name="further-information"></a>Weitere Informationen
Weitere Informationen zu Microsoft Passport finden Sie im [Leitfaden](https://technet.microsoft.com/library/mt589441.aspx) in der Dokumentation zu Windows 10.
