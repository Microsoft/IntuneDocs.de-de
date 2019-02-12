---
title: Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Administratoren können mithilfe der Aktionen „Zurücksetzen“ oder „Außer Betrieb nehmen“ Zertifikate aus Microsoft Intune entfernen. In einigen Szenarios werden Zertifikate automatisch entfernt, wenn z.B. die Registrierung eines Geräts aufgehoben oder eine Konformitätsrichtlinie entfernt wird. In einigen Zertifikaten bleiben Zertifikate automatisch auf dem Gerät erhalten, wenn z.B. die Intune-Lizenz verloren geht oder entfernt wird. Informieren Sie sich über die verschiedenen Möglichkeiten für Android-, Android Enterprise-, iOS-, macOS- und Windows-Geräte.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82d0bf8abdaf572e28cfcf1547f6fadca7d1e6b0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834788"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune

In Microsoft Intune können Sie Simple Certificate Enrollment Protocol-Zertifikate (SCEP) und Public Key Cryptography Standards-Zertifikate (PKCS) zu Geräten hinzufügen. Diese Zertifikate können anschließend auch wieder entfernt werden, wenn Sie das Gerät [zurücksetzen](devices-wipe.md#wipe) oder [außer Betrieb nehmen](devices-wipe.md#retire). 

In einigen anderen Szenarios werden Zertifikate automatisch entfernt bzw. sie verbleiben auf dem Gerät. In diesem Artikel werden einige häufig auftretende Szenarios aufgelistet, und es wird beschrieben, welche Auswirkungen diese auf PKCS- und SCEP-Zertifikate haben.

> [!NOTE]
> Führen Sie die nachfolgenden Schritte in der richtigen Reihenfolge aus, um sicherzustellen, dass Zertifikate für einen Benutzer entfernt bzw. widerrufen werden, der aus einer lokalen Active Directory-Instanz bzw. Azure Active Directory (Azure AD) entfernt wird:
>
> 1. Setzen Sie das Gerät des Benutzers zurück, oder nehmen Sie es außer Betrieb.
> 2. Entfernen Sie den Benutzer aus der lokalen Active Directory-Instanz bzw. aus Azure AD.

## <a name="windows-devices"></a>Windows-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:

- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.
- das Gerät aus einer Azure AD-Gruppe entfernt wird.
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.

SCEP-Zertifikate werden widerrufen, wenn:
- ein Administrator das SCEP-Profil ändert oder aktualisiert.

Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

SCEP-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

PKCS-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.
- ein Administrator das PKCS-Profil ändert oder aktualisiert
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.


## <a name="ios-devices"></a>iOS-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:

- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.
- das Gerät aus der Azure AD-Gruppe entfernt wird.
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.

SCEP-Zertifikate werden widerrufen, wenn:
- ein Administrator das SCEP-Profil ändert oder aktualisiert.

Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

SCEP-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

Das PKCS-Zertifikat wird entfernt, wenn:
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.
  
Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

PKCS-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.
- ein Administrator das PKCS-Profil ändert oder aktualisiert

## <a name="android-knox-devices"></a>Android KNOX-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.

SCEP-Zertifikate werden widerrufen, wenn:
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.
- das Gerät aus einer Azure AD-Gruppe entfernt wird.
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.
- ein Administrator das SCEP-Profil ändert oder aktualisiert.

Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

SCEP-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

Das Stammzertifikat wird entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) ausführt.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.

PKCS-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.
- ein Administrator das PKCS-Profil ändert oder aktualisiert
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.
  
  
> [!NOTE]
> Android for Work-Geräte sind für die zuvor genannten Szenarios nicht freigegeben. Android-Legacygeräte (jedes Profilgerät, das kein Samsung- oder Work-Gerät ist) sind nicht für die Entfernung von Zertifikaten freigegeben. 

## <a name="macos-certificates"></a>macOS-Zertifikate

#### <a name="scep-certificates"></a>SCEP-Zertifikate

SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
- die Registrierung eines Benutzers aufgehoben wird.
- ein Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) ausführt.
- das Gerät aus einer Azure AD-Gruppe entfernt wird.
- ein Zertifikatprofil aus der Gruppenzuweisung entfernt wird.

SCEP-Zertifikate werden widerrufen, wenn:
- ein Administrator das SCEP-Profil ändert oder aktualisiert.

SCEP-Zertifikate *verbleiben* auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
- ein Benutzer seine Intune-Lizenz verliert.
- ein Administrator die Intune-Lizenz widerruft.
- ein Administrator den Benutzer oder die Gruppe aus Azure AD entfernt.

> [!NOTE]
> Die Aktion [Zurücksetzen](devices-wipe.md#wipe) zum Zurücksetzen von macOS-Geräten auf die Werkseinstellungen wird nicht unterstützt.

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

PKCS-Zertifikate werden nicht unterstützt.

