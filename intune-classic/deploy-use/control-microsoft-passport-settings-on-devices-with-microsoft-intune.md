---
title: Steuern der Einstellungen von Windows Hello for Business auf Geräten
description: Erfahren Sie, wie Intune Windows Hello for Business integriert wird. Dies ist eine alternative Anmeldemethode, die Active Directory oder ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 09/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b841bcf97ecb213f75575508362de0234bc8a2b9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="control-windows-hello-for-business-settings-on-devices-with-microsoft-intune"></a>Steuern der Einstellungen von Windows Hello for Business auf Geräten mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Erfahren Sie, wie Microsoft Intune in Windows Hello for Business (früher Microsoft Passport for Work) integriert wird. Dies ist eine alternative Anmeldemethode, die Active Directory oder ein Azure Active Directory-Konto verwendet, um ein Kennwort, eine Smartcard oder eine virtuelle Smartcard zu ersetzen.

Mit Hello for Business können Sie anstelle eines Kennworts eine *Benutzeraktion* zur Anmeldung verwenden. Eine Benutzeraktion kann eine einfache PIN, eine biometrische Authentifizierung wie Windows Hello oder ein externes Gerät sein, z. B. ein Fingerabdruckleser.

Intune integriert Hello for Business auf zwei Arten:

-   Sie können mithilfe einer Intune-Richtlinie steuern, welche Aktionen von Benutzern zum Anmelden verwendet werden können.

-   Sie können Authentifizierungszertifikate im Windows Hello for Business-Schlüsselspeicheranbieter (Key Storage Provider, KSP) speichern. Weitere Informationen finden Sie unter [Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).

> [!IMPORTANT]
> Bei Desktop- und mobilen Versionen von Windows 10 vor dem Anniversary Update konnten Sie zwei unterschiedliche PINS für die Authentifizierung bei Ressourcen festlegen:
> - Die **Geräte-PIN** konnte zum Entsperren des Geräts und zur Verbindung mit Cloudressourcen verwendet werden.
> - Die **Arbeits-PIN** wurde für den Zugang zu Azure AD-Ressourcen auf persönlichen Geräten von Benutzern (BYOD) verwendet.
> 
> Im Anniversary Update wurden diese beiden PINs in eine einzige Geräte-PIN zusammengeführt.
> Dieser neue PIN-Wert wird jetzt sowohl von allen Intune-Konfigurationsrichtlinien, die Sie zum Steuern der Geräte-PIN festlegen, als auch von allen konfigurierten Windows Hello for Business-Richtlinien festgelegt.
> Wenn Sie beide Richtlinientypen für die PIN-Steuerung eingerichtet haben, wird sowohl auf Desktop- als auch auf mobilen Geräten mit Windows 10 die Windows Hello for Business-Richtlinie angewendet.
> Um sicherzustellen, dass Richtlinienkonflikte gelöst werden und dass die PIN-Richtlinie korrekt angewendet wird, aktualisieren Sie Ihre Windows Hello for Business-Richtlinie auf die Einstellungen in der Konfigurationsrichtlinie. Fordern Sie auch die Benutzer auf, ihre Geräte in der Unternehmensportal-App zu synchronisieren.



## <a name="create-a-windows-hello-for-business-policy"></a>Erstellen einer Windows Hello for Business-Richtlinie

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **Windows** &gt; **Windows Hello for Business**, um die Seite „Windows Hello for Business“ zu öffnen.

    ![Windows Hello for Business-Seite](../media/passport.png)

2.  Wählen Sie eine der folgenden Einstellungen aus:
    - **Windows Hello for Business auf registrierten Geräten deaktivieren**. Wenn Sie Windows Hello for Business nicht verwenden möchten, wählen Sie diese Einstellung aus. In diesem Fall ist keine der anderen Einstellungen auf dem Bildschirm verfügbar.
    - **Windows Hello for Business auf registrierten Geräten aktivieren**. Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen konfigurieren möchten.
    - **Nicht konfiguriert**. Wählen Sie diese Einstellung aus, wenn Sie Windows Hello for Business-Einstellungen nicht mit Intune steuern möchten. Vorhandene Windows Hello for Business-Einstellungen auf Geräten mit Windows 10 werden nicht geändert. Keine der anderen Einstellungen auf dem Bildschirm ist verfügbar.
3.  Wenn Sie **Windows Hello for Business auf registrierten Geräten aktivieren** ausgewählt haben, konfigurieren Sie die erforderlichen Einstellungen, die auf alle registrierten Geräte mit Windows 10 und Windows 10 Mobile angewendet werden.
4.  Wählen Sie anschließend **Speichern** aus.


## <a name="settings-for-the-windows-hello-for-business-policy"></a>Einstellungen für die Windows Hello for Business-Richtlinie

- **Trusted Platform Module (TPM) verwenden**. Ein TPM-Chip bietet eine zusätzliche Sicherheitsebene für Daten.<br>Wählen Sie einen der folgenden Werte aus:
    - **Erforderlich** (Standard). Nur Geräte mit verfügbarem TPM können Windows Hello for Business bereitstellen.
    - **Bevorzugt**. Geräte versuchen zunächst, ein TPM zu verwenden. Wenn diese Option nicht verfügbar ist, können sie die Softwareverschlüsselung verwenden.
- **Minimale PIN-Länge vorschreiben**/**Maximale PIN-Länge vorschreiben**. Konfiguriert Geräte für die Verwendung der von Ihnen angegebenen minimalen und maximalen PIN-Länge, um eine sichere Anmeldung zu gewährleisten. Die Standard-PIN-Länge beträgt 6 Zeichen, aber Sie können eine Mindestlänge von 4 Zeichen erzwingen. Die maximale PIN-Länge ist 127 Zeichen.
- **Kleinbuchstaben in PIN vorschreiben**/**Großbuchstaben in PIN vorschreiben**/**Sonderzeichen in PIN vorschreiben**. Sie können eine stärkere PIN erzwingen, indem Sie die Nutzung von Großbuchstaben, Kleinbuchstaben und Sonderzeichen in der PIN vorschreiben. Es stehen die folgenden Optionen zur Auswahl:
    - **Zulässig**. Benutzer können den Zeichentyp in ihrer PIN verwenden, aber es ist nicht zwingend erforderlich.
    - **Erforderlich**. Benutzer müssen mindestens einen der Zeichentypen in ihrer PIN verwenden. Beispielsweise ist es üblich, die Verwendung mindestens eines Großbuchstabens und eines Sonderzeichens vorzuschreiben.
    - **Nicht zulässig** (Standard). Benutzer dürfen diese Zeichentypen in ihrer PIN nicht verwenden. (Dies trifft auch zu, wenn die Einstellung nicht konfiguriert ist.)<br>Sonderzeichen sind: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **PIN-Ablauf (Tage)**. Es wird empfohlen, ein Ablaufdatum für eine PIN anzugeben, nach dem sie vom Benutzer geändert werden muss. Die Standardeinstellung ist 41 Tage.
- **PIN-Verlauf speichern**. Schränkt die Wiederverwendung zuvor verwendeter PINs ein. Standardmäßig können die letzten fünf PINs nicht erneut verwendet werden.
- **Biometrische Authentifizierung zulassen**. Aktiviert die biometrische Authentifizierung, z. B. die Gesichtserkennung oder Fingerabdrücke, als Alternative zu einer PIN für Windows Hello for Business. Benutzer müssen für den Fall dennoch eine PIN konfigurieren, dass die biometrische Authentifizierung fehlschlägt. Es stehen die folgenden Optionen zur Auswahl:
    - **Ja**. Windows Hello for Business ermöglicht biometrische Authentifizierung.
    - **Nein**. Windows Hello for Business verhindert die biometrische Authentifizierung (für alle Arten von Konten).
- **Erweitertes Antispoofing verwenden, falls verfügbar**. Konfiguriert, ob die Antispoofingfeatures von Windows Hello auf Geräten verwendet werden, die diese unterstützen (z. B. Erkennung eines Fotos von einem Gesicht anstelle eines echten Gesichts).<br>Wenn diese Option auf **Ja** festgelegt ist, erfordert Windows von allen Benutzern die Verwendung von Antispoofing für Gesichtsmerkmale, sofern dies unterstützt wird.
- **Anmeldung per Telefon verwenden**. Wenn diese Option auf **Ja** festgelegt ist, können die Benutzer einen Remote-Passport als tragbares Begleitgerät für die Authentifizierung von Desktopcomputern verwenden. Der Desktopcomputer muss Azure Active Directory angehören, und das Begleitgerät muss mit einer Windows Hello for Business-PIN konfiguriert werden.

## <a name="further-information"></a>Weitere Informationen
Weitere Informationen zu Microsoft Passport finden Sie im [Leitfaden](https://technet.microsoft.com/library/mt589441.aspx) in der Dokumentation zu Windows 10.
