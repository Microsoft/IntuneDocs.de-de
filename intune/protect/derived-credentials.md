---
title: Verwenden abgeleiteter Anmeldeinformationen für mobile Geräte in Microsoft Intune | Microsoft-Dokumentation
description: Verwenden Sie abgeleitete Anmeldeinformationen auf mobilen Geräten als Authentifizierungsmethode für VPN, E-Mails, WLAN-Profile, Anwendungen, S/MIME und die Verschlüsselung in Intune. Abgeleitete Anmeldeinformationen sind eine Implementierung der NIST-Richtlinien für Special Publication 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91442d262adb1d85217cb73f2f415766b89267af
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510519"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Verwenden abgeleiteter Anmeldeinformationen in Microsoft Intune

*Dieser Artikel gilt für iOS-Geräte*

In einer Umgebung, in der Smartcards für die Authentifizierung oder Verschlüsselung und Signierung erforderlich sind, können Sie mit Intune jetzt mobile Geräte mit einem Zertifikat bereitstellen, das von der Smartcard eines Benutzers abgeleitet ist. Dieses Zertifikat wird als *abgeleitete Anmeldeinformation* bezeichnet. Intune [unterstützt mehrere Zertifikataussteller für abgeleitete Anmeldeinformationen](#supported-issuers). Sie können pro Mandant aber jeweils nur einen Zertifikataussteller verwenden.

Abgeleitete Anmeldeinformationen sind eine Implementierung der NIST-Richtlinien (National Institute of Standards and Technology) für PIV-Anmeldeinformationen (Personal Identity Verification) aus SP 800-157 (Special Publication).

**Ablauf der Intune-Implementierung:**

- Der Intune-Administrator konfiguriert seinen Mandanten so, dass dieser mit einem unterstützten Zertifikataussteller für abgeleitete Anmeldeinformationen arbeitet. Sie müssen keine Intune-spezifischen Einstellungen im System des Zertifikatausstellers für abgeleitete Anmeldeinformationen konfigurieren.

- Der Intune-Administrator gibt für die folgenden Objekte **Derived credentials** (Abgeleitete Anmeldeinformationen) als *Authentifizierungsmethode* an:

  - Allgemeine Profiltypen wie WLAN, VPN und E-Mail (einschließlich der nativen iOS/iPadOS-E-Mail-App)

  - App-Authentifizierung

  - S/MIME-Signatur und -Verschlüsselung

- Benutzer erhalten abgeleitete Anmeldeinformationen, indem sie ihre Smartcard auf einem Computer verwenden, um sich beim Zertifikataussteller der abgeleiteten Anmeldeinformationen zu authentifizieren. Der Zertifikataussteller gibt dann ein Zertifikat für das mobile Gerät zurück, das von der Smartcard abgeleitet ist.

- Nachdem das Gerät die abgeleitete Anmeldeinformation empfangen hat, wird diese für die Authentifizierung und für die S/MIME-Signatur und -Verschlüsselung verwendet, wenn Apps oder Ressourcenzugriffsprofile die abgeleitete Anmeldeinformation erfordern. 

## <a name="prerequisites"></a>Voraussetzungen

Lesen Sie die folgenden Informationen, bevor Sie Ihren Mandanten für die Verwendung abgeleiteter Anmeldeinformationen konfigurieren.

### <a name="supported-platforms"></a>Unterstützte Plattformen

Intune unterstützt abgeleitete Anmeldeinformationen auf den folgenden Betriebssystemplattformen:

- iOS/iPadOS

### <a name="supported-issuers"></a>Unterstützte Zertifikataussteller

Intune unterstützt pro Mandant einen einzelnen Zertifikataussteller für abgeleitete Anmeldeinformationen. Sie können Intune so konfigurieren, dass die folgenden Zertifikataussteller verwendet werden:

- **DISA Purebred**: https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercede**: https://www.intercede.com/

Wichtige Details zur Verwendung der verschiedenen Zertifikataussteller finden Sie in der jeweiligen Anleitung für diesen Zertifikataussteller<!-- , including the issuers end-user workflow-->. Weitere Informationen finden Sie in diesem Artikel im Abschnitt [Plan für abgeleitete Anmeldeinformationen](#plan-for-derived-credentials).

> [!IMPORTANT]  
> Wenn Sie einen Zertifikataussteller für abgeleitete Anmeldeinformationen aus Ihrem Mandanten löschen, funktionieren die über diesen Zertifikataussteller eingerichteten abgeleiteten Anmeldeinformationen nicht mehr.
>
> Näheres hierzu finden Sie später in diesem Artikel im Abschnitt [Ändern des Zertifikatausstellers für abgeleitete Anmeldeinformationen](#change-the-derived-credential-issuer).

### <a name="company-portal-app"></a>Unternehmensportal-App

Planen Sie die Bereitstellung der Intune-Unternehmensportal-App auf Geräten, die für abgeleitete Anmeldeinformationen registriert werden. Gerätebenutzer verwenden die Unternehmensportal-App, um den Registrierungsvorgang für Anmeldeinformationen zu starten.

Informationen zu iOS/iPadOS-Geräten finden Sie im Artikel [Hinzufügen von iOS Store-Apps zu Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planen abgeleiteter Anmeldeinformationen

Beachten Sie die folgenden Überlegungen, bevor Sie einen Zertifikataussteller für abgeleitete Anmeldeinformationen einrichten.

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) Überprüfen der Dokumentation zum ausgewählten Zertifikataussteller für abgeleitete Anmeldeinformationen  

Lesen Sie vor dem Konfigurieren des Zertifikatausstellers die jeweilige Dokumentation durch, um zu verstehen, wie das System abgeleitete Anmeldeinformationen an Geräte übermittelt.

Je nach ausgewähltem Aussteller müssen zum Zeitpunkt der Registrierung möglicherweise Mitarbeiter zur Verfügung stehen, um den Benutzern den Vorgang zu erleichtern. Außerdem sollten Sie Ihre aktuellen Intune-Konfigurationen überprüfen, um sicherzustellen, dass diese nicht den Zugriff blockieren, der für Geräte oder Benutzer zum Abschließen der Anforderung von Anmeldeinformationen erforderlich ist.

Sie können beispielsweise den bedingten Zugriff verwenden, um für nicht kompatible Geräte den E-Mail-Zugriff zu blockieren. Wenn Sie Benutzer mit E-Mail-Benachrichtigungen darüber informieren, dass der Registrierungsprozess für abgeleitete Anmeldeinformationen gestartet werden soll, erhalten Ihre Benutzer diese Anweisungen möglicherweise erst bei Konformität mit den Richtlinien.

Entsprechend erfordern einige Anforderungsworkflows für abgeleitete Anmeldeinformationen die Verwendung der Gerätekamera zum Scannen eines QR-Codes auf dem Bildschirm. Dieser Code leitet das Gerät zur Authentifizierungsanforderung für den Zertifikataussteller für abgeleitete Anmeldeinformationen. Wenn die Verwendung der Kamera durch Gerätekonfigurationsrichtlinien blockiert wird, kann der Benutzer die Registrierungsanforderung für abgeleitete Anmeldeinformationen nicht abschließen.

Allgemeine Informationen:

- Sie können pro Mandant nur einen einzelnen Zertifikataussteller konfigurieren, der dann allen Benutzern und unterstützten Geräten in Ihrem Mandanten zur Verfügung steht.

- Benutzer werden so lange nicht benachrichtigt, dass sie sich für die abgeleiteten Anmeldeinformationen registrieren müssen, bis Sie eine Richtlinie angeben, die abgeleitete Anmeldeinformationen erfordert.

- Die Benachrichtigung kann über eine App-Benachrichtigung für das Unternehmensportal, eine E-Mail oder beides erfolgen. Wenn Sie E-Mail-Benachrichtigungen und den bedingten Zugriff verwenden, erhalten Benutzer möglicherweise keine E-Mail-Benachrichtigung, wenn ihr Gerät nicht konform ist.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) Überprüfen des Endbenutzerworkflows für den ausgewählten Zertifikataussteller

Im Folgenden finden Sie wichtige Überlegungen zu jedem unterstützten Partner.  Machen Sie sich mit diesen Informationen vertraut, um sicherzustellen, dass Ihre Intune-Richtlinien und Konfigurationen keine Benutzer und Gerät blockieren und dadurch die Registrierung abgeleiteter Anmeldeinformationen von diesem Zertifikataussteller nicht erfolgreich abgeschlossen werden kann.

#### <a name="disa-purebred"></a>DISA Purebred

Überprüfen Sie den [Benutzerworkflow für DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Zu den wichtigsten Anforderungen für diesen Workflow gehören folgende:

- Benutzer benötigen Zugriff auf einen Computer oder KIOSK, auf dem Sie Ihre Smartcard zum Authentifizieren beim Zertifikataussteller verwenden können.

- Auf Geräten, die für abgeleitete Anmeldeinformationen registriert werden, muss die Intune-Unternehmensportal-App installiert werden.

- Verwenden Sie Intune zum [Bereitstellen der DISA Purebred-App](#deploy-the-disa-purebred-app) auf Geräten, die für abgeleitete Anmeldeinformationen registriert werden. Diese App muss über Intune bereitgestellt werden, damit sie verwaltet und mit der Intune-Unternehmensportal-App genutzt werden kann. Diese App wird von Gerätebenutzern zum Abschließen der Anforderung von abgeleiteten Anmeldeinformationen verwendet.

- Die DISA Purebred-App erfordert ein [App-bezogenes VPN](../configuration/vpn-settings-configure.md), um sicherzustellen, dass die App während der Registrierung für abgeleitete Anmeldeinformationen auf DISA Purebred zugreifen kann.

- Gerätebenutzer müssen während des Registrierungsprozesses mit einem Live-Agent zusammenarbeiten. Im Laufe des Registrierungsprozesses werden dem Benutzer zeitlich begrenzte und einmalige Passcodes bereitgestellt.

Informationen zum Abrufen und Konfigurieren der DISA Purebred-App finden Sie später in diesem Artikel im Abschnitt [Bereitstellen der DISA Purebred-App](#deploy-the-disa-purebred-app).

#### <a name="entrust-datacard"></a>Entrust Datacard

Überprüfen Sie den [Benutzerworkflow für Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard). Zu den wichtigsten Anforderungen für diesen Workflow gehören folgende:

- Benutzer benötigen Zugriff auf einen Computer oder KIOSK, auf dem Sie Ihre Smartcard zum Authentifizieren beim Zertifikataussteller verwenden können.

- Auf Geräten, die für abgeleitete Anmeldeinformationen registriert werden, muss die Intune-Unternehmensportal-App installiert werden.

- Es wird eine Gerätekamera zum Scannen eines QR-Codes verwendet, der die Authentifizierungsanforderung mit der Anforderung für abgeleitete Anmeldeinformationen vom mobilen Gerät verbindet.

#### <a name="intercede"></a>Intercede

Überprüfen Sie den [Benutzerworkflow für Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Zu den wichtigsten Anforderungen für diesen Workflow gehören folgende:

- Benutzer benötigen Zugriff auf einen Computer oder KIOSK, auf dem Sie Ihre Smartcard zum Authentifizieren beim Zertifikataussteller verwenden können.

- Auf Geräten, die für abgeleitete Anmeldeinformationen registriert werden, muss die Intune-Unternehmensportal-App installiert werden.

- Es wird eine Gerätekamera zum Scannen eines QR-Codes verwendet, der die Authentifizierungsanforderung mit der Anforderung für abgeleitete Anmeldeinformationen vom mobilen Gerät verbindet.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) Bereitstellen eines vertrauenswürdigen Stammzertifikats für Geräte

Ein vertrauenswürdiges Stammzertifikat wird zusammen mit abgeleiteten Anmeldeinformationen verwendet, um zu überprüfen, ob die Vertrauenskette der abgeleiteten Anmeldeinformationen gültig und vertrauenswürdig ist. Auch wenn nicht direkt auf die Richtlinie verwiesen wird, ist ein vertrauenswürdiges Stammzertifikat erforderlich. Informationen finden Sie im Artikel [Konfigurieren eines Zertifikatprofils für Ihre Geräte in Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) Bereitstellen von Endbenutzeranweisungen zum Abrufen von abgeleiteten Anmeldeinformationen

Erstellen Sie für Ihre Benutzer eine Anleitung mit Informationen zum Starten des Registrierungsprozesses für abgeleitete Anmeldeinformationen und für die Navigation durch den Registrierungsworkflow für abgeleitete Anmeldeinformationen des jeweiligen ausgewählten Zertifikatausstellers.

Es wird empfohlen, eine URL mit Ihrer Anleitung anzugeben. Sie geben diese URL beim Konfigurieren des Zertifikatausstellers für abgeleitete Anmeldeinformationen für Ihren Mandanten an. Sie wird dann in der Unternehmensportal-App zur Verfügung gestellt. Wenn Sie nicht Ihre eigene URL angeben, stellt Intune einen Link zu generischen Details bereit. Diese können allerdings nicht alle Szenarios abdecken und treffen möglicherweise nicht auf Ihre Umgebung zu.

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) Bereitstellen von Intune-Richtlinien für abgeleitete Anmeldeinformationen

Sie können neue Richtlinien erstellen oder vorhandene bearbeiten, um abgeleitete Anmeldeinformationen zu verwenden. Abgeleitete Anmeldeinformationen ersetzen andere Authentifizierungsmethoden für die App-Authentifizierung, WLAN, VPN, E-Mails sowie die S/MIME-Signatur und -Verschlüsselung.

Vermeiden Sie die Verwendung abgeleiteter Anmeldeinformationen für den Zugriff auf einen Prozess, den Sie als Teil des Abrufprozesses für abgeleitete Anmeldeinformationen verwenden, da so möglicherweise verhindert wird, dass Benutzer die Anforderung abschließen können.

## <a name="set-up-a-derived-credential-issuer"></a>Einrichten eines Zertifikatausstellers für abgeleitete Anmeldeinformationen

Richten Sie vor dem Erstellen von Richtlinien, die abgeleitete Anmeldeinformationen erfordern, in der Intune-Konsole einen Zertifikataussteller für Anmeldeinformationen ein. Bei einem Zertifikataussteller für abgeleitete Anmeldeinformationen handelt es sich um eine mandantenweite Einstellung. Mandanten unterstützen jeweils nur einen einzelnen Zertifikataussteller.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Abgeleitete Anmeldeinformationen** aus.

    > [!div class="mx-imgBorder"]
    > ![Konfigurieren abgeleiteter Anmeldeinformationen in der Konsole](./media/derived-credentials/configure-provider.png)

3. Geben Sie einen **Anzeigenamen** für die Zertifikatsausstellerrichtlinie für abgeleitete Anmeldeinformationen an.  Dieser Name wird den Gerätebenutzern nicht angezeigt.

4. Wählen Sie für **Derived credential issuer** (Zertifikataussteller für abgeleitete Anmeldeinformationen) den Zertifikataussteller für abgeleitete Anmeldeinformationen aus, den Sie für Ihren Mandanten ausgewählt haben:
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

5. Geben Sie eine **Hilfe-URL zu abgeleiteten Anmeldeinformationen** an, um einen Link mit benutzerdefinierten Anweisungen bereitzustellen, der Benutzern beim Abrufen abgeleiteter Anmeldeinformationen für Ihre Organisation hilft. Diese Anweisungen sollten sich auf Ihre Organisation und den Workflow beziehen, der für das Abrufen von Anmeldeinformationen vom ausgewählten Zertifikataussteller erforderlich ist. Der Link wird in der Unternehmensportal-App angezeigt und sollte vom Gerät aus zugänglich sein.

   Wenn Sie nicht Ihre eigene URL angeben, stellt Intune einen Link zu generischen Details bereit, die nicht alle Szenarios abdecken können. Diese generische Anleitung trifft möglicherweise nicht auf Ihre Umgebung zu.

6. Wählen Sie für **Notification type** (Benachrichtigungstyp) eine oder mehrere Optionen aus. Benachrichtigungstypen sind die Methoden, die Sie verwenden, um Benutzer über die folgenden Szenarios zu informieren:

   - Registrieren Sie ein Gerät bei einem Zertifikataussteller, um neue abgeleitete Anmeldeinformationen zu erhalten.
   - Rufen Sie neue abgeleitete Anmeldeinformationen ab, wenn die aktuellen Anmeldeinformationen demnächst ablaufen.
   - Verwenden Sie abgeleitete Anmeldeinformationen mit einer Richtlinie für die WLAN-, VPN-, E-Mail- oder App-Authentifizierung sowie die S/MIME-Signatur und -Verschlüsselung.

7. Klicken Sie auf **Speichern**, um die Konfiguration des Zertifikatausstellers für abgeleitete Anmeldeinformationen abzuschließen.

Nachdem Sie die Konfiguration gespeichert haben, können Sie mit Ausnahme des *Zertifikatausstellers für abgeleitete Anmeldeinformationen* Änderungen an allen Feldern vornehmen.  Nähere Informationen zum Ändern des Zertifikatausstellers finden Sie unter [Ändern des Zertifikatausstellers für abgeleitete Anmeldeinformationen](#change-the-derived-credential-issuer).

## <a name="deploy-the-disa-purebred-app"></a>Bereitstellen der DISA Purebred-App

*Dieser Abschnitt gilt nur dann, wenn Sie DISA Purebred verwenden.*

Wenn Sie **DISA Purebred** als Zertifikataussteller für abgeleitete Anmeldeinformationen für Intune verwenden möchten, müssen Sie zunächst die DISA Purebred-App herunterladen und Intune für die Bereitstellung der App auf Geräten verwenden. Gerätebenutzer verwenden die App auf ihrem Gerät, um die abgeleiteten Anmeldeinformationen von DISA Purebred anzufordern.

Zusätzlich zur Bereitstellung der App mit Intune müssen Sie ein App-bezogenes Intune-VPN für die DISA Purebred-Anwendung konfigurieren.

**Führen Sie die folgenden Aktionen aus:**
  
1. Laden Sie die [DISA Purebred-Anwendung](https://cyber.mil/pki-pke/purebred/) herunter.
2. Stellen Sie die DISA Purebred-App in Intune bereit.  Informationen finden Sie unter [Hinzufügen von branchenspezifischen iOS-Apps zu Microsoft Intune](../apps/lob-apps-ios.md).
3. [Erstellen Sie ein App-bezogenes VPN](../configuration/vpn-settings-configure.md) für die DISA Purebred-Anwendung.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Verwenden abgeleiteter Anmeldeinformationen für die Authentifizierung und die S/MIME-Signatur und -Verschlüsselung

Sie können **Derived credentials** (Abgeleitete Anmeldeinformationen) für die folgenden Profiltypen und Zwecke angeben:

- [Anwendungen](#use-derived-credentials-for-app-authentication)
- [E-Mail](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME-Signatur und -Verschlüsselung](certificates-s-mime-encryption-sign.md)
- [WLAN](../configuration/wi-fi-settings-ios.md)

  Für WLAN-Profile ist die *Authentifizierungsmethode* nur verfügbar, wenn der **EAP-Typ** auf einen der folgenden Werte festgelegt ist:
  - EAP-TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Verwenden abgeleiteter Anmeldeinformationen für die App-Authentifizierung

Verwenden Sie abgeleitete Anmeldeinformationen für die zertifikatbasierte Authentifizierung bei Websites und Anwendungen. So verwenden Sie abgeleitete Anmeldeinformationen zur App-Authentifizierung

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein guter Profilname ist beispielsweise **Abgeleitete Anmeldeinformationen für iOS/iPadOS-Geräteprofile**.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **Plattform**: Wählen Sie **iOS/iPadOS** aus.
    - **Profiltyp**: Wählen Sie **Abgeleitete Anmeldeinformationen** aus.

4. Klicken Sie auf **OK**, um die Änderungen zu speichern.
5. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Das Profil wird erstellt und in der Liste **Gerätekonfiguration > Konfigurationsprofile** angezeigt.
6. Wählen Sie Ihr neues Profil aus, und klicken Sie auf **Zuweisungen**. Wählen Sie die Gruppen aus, die die Richtlinie erhalten sollen.
 
Benutzer erhalten die App- oder E-Mail-Benachrichtigung abhängig von den Einstellungen, die Sie beim Einrichten des Zertifikatausstellers für abgeleitete Anmeldeinformationen angegeben haben. Die Benachrichtigung informiert den Benutzer darüber, dass das Unternehmensportal gestartet werden muss, damit die Richtlinien für abgeleitete Anmeldeinformationen verarbeitet werden können.

## <a name="renew-a-derived-credential"></a>Erneuern abgeleiteter Anmeldeinformationen

Abgeleitete Anmeldeinformationen können nicht erweitert oder erneuert werden. Stattdessen müssen Benutzer den Anforderungsworkflow für Anmeldeinformationen verwenden, um neue abgeleitete Anmeldeinformationen für ihr Gerät anzufordern.

Wenn Sie eine oder mehrere Methoden für **Benachrichtigungstyp** konfigurieren, werden Benutzer automatisch von Intune benachrichtigt, wenn die aktuellen abgeleiteten Anmeldeinformationen 80 % ihrer Lebensspanne erreicht haben. Die Benachrichtigung weist Benutzer an, den Anforderungsprozess für Anmeldeinformationen zu durchlaufen, um neue abgeleitete Anmeldeinformationen zu erhalten.

Nachdem ein Gerät neue abgeleitete Anmeldeinformationen erhalten hat, werden Richtlinien, die abgeleitete Anmeldeinformationen verwenden, erneut auf diesem Gerät bereitgestellt.


## <a name="change-the-derived-credential-issuer"></a>Ändern des Zertifikatausstellers für abgeleitete Anmeldeinformationen

Auf Mandantenebene können Sie den Zertifikataussteller für Anmeldeinformationen ändern, obwohl jeweils nur ein Zertifikataussteller für einen Mandanten unterstützt wird.

Nachdem Sie den Zertifikataussteller geändert haben, werden Benutzer aufgefordert, neue abgeleitete Anmeldeinformationen vom neuen Benutzer zu erhalten. Sie müssen dies tun, bevor sie abgeleitete Anmeldeinformationen für die Authentifizierung verwenden können.

### <a name="change-the-issuer-for-your-tenant"></a>Ändern des Zertifikatausstellers für Ihren Mandanten

> [!IMPORTANT]  
> Wenn Sie einen Zertifikataussteller löschen und denselben Zertifikataussteller sofort neu konfigurieren, müssen Sie weiterhin Profile und Geräte aktualisieren, damit die abgeleiteten Anmeldeinformationen von diesem Zertifikataussteller verwendet werden. Abgeleitete Anmeldeinformationen, die vor dem Löschen des Zertifikatausstellers abgerufen wurden, sind nicht mehr gültig.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Mandantenverwaltung** > **Connectors und Token** > **Abgeleitete Anmeldeinformationen** aus.
3. Klicken Sie auf **Löschen**, um den aktuellen Zertifikataussteller für abgeleitete Anmeldeinformationen zu löschen.
4. Konfigurieren Sie einen neuen Zertifikataussteller.

### <a name="update-profiles-that-use-derived-credentials"></a>Aktualisieren von Profilen, die abgeleitete Anmeldeinformationen verwenden

Nach dem Löschen eines alten und Hinzufügen eines neuen Zertifikatausstellers müssen Sie jedes Profil bearbeiten, das abgeleitete Anmeldeinformationen verwendet. Diese Regel gilt auch dann, wenn Sie den vorherigen Zertifikataussteller wiederherstellen. Jede Bearbeitung des Profils löst ein Update einschließlich einer einfachen Bearbeitung des Profils *Beschreibung* aus.

### <a name="update-derived-credentials-on-devices"></a>Aktualisieren abgeleiteter Anmeldeinformationen auf Geräten

Nach dem Löschen eines alten und Hinzufügen eines neuen Zertifikatausstellers müssen Gerätebenutzer neue abgeleitete Anmeldeinformationen anfordern. Diese Regel gilt auch dann, wenn Sie denselben Zertifikataussteller hinzufügen, den Sie entfernt haben. Der Prozess zum Anfordern der neuen abgeleiteten Anmeldeinformationen entspricht dem Verfahren zum Registrieren eines neuen Geräts oder Erneuern vorhandener Anmeldeinformationen.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen von Gerätekonfigurationsprofilen](../configuration/device-profile-create.md)
