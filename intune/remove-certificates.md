---
title: Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Administratoren können mithilfe der Aktionen „Zurücksetzen“ oder „Außer Betrieb nehmen“ Zertifikate aus Microsoft Intune entfernen. In einigen Szenarios werden Zertifikate automatisch entfernt, wenn z.B. die Registrierung eines Geräts aufgehoben oder eine Konformitätsrichtlinie entfernt wird. In einigen Zertifikaten bleiben Zertifikate automatisch auf dem Gerät erhalten, wenn z.B. die Intune-Lizenz verloren geht oder entfernt wird. Informieren Sie sich über die verschiedenen Möglichkeiten für Android-, Android Enterprise-, iOS-, macOS- und Windows-Geräte.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 06b568ee7cc2dc55a8d44cf04b96078b47d8c4b3
ms.sourcegitcommit: 77a1047f5d93c1924e5c9ea243454532881be031
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52579165"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune

Sie können in Microsoft Intune SCEP- und PKCS-Zertifikate zu Geräten hinzufügen. Diese Zertifikate können anschließend auch wieder entfernt werden, wenn Sie das Gerät [zurücksetzen](devices-wipe.md#wipe) oder [außer Betrieb nehmen](devices-wipe.md#retire). In einigen anderen Szenarios werden Zertifikate automatisch entfernt bzw. sie verbleiben auf dem Gerät.

In diesem Artikel werden einige häufig auftretende Szenarios aufgelistet, und es wird beschrieben, welche Auswirkungen diese auf PKCS- und SCEP-Zertifikate haben.

> [!NOTE]
> Führen Sie die nachfolgenden Schritte in der richtigen Reihenfolge aus, um sicherzustellen, dass Zertifikate für einen Benutzer entfernt bzw. widerrufen werden, der aus Active Directory (AD) oder Azure AD entfernt wird:
>
>    1. Setzen Sie das Gerät des Benutzers zurück, oder nehmen Sie es außer Betrieb.
>    2. Entfernen Sie den Benutzer aus AD oder Azure AD.

## <a name="windows-devices"></a>Windows-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- SCEP-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

- PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- PKCS-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt
  - der Administrator das PKCS-Profil ändert oder aktualisiert
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt


## <a name="ios-devices"></a>iOS-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- SCEP-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

- PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- Das PKCS-Zertifikat wird entfernt, wenn:
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt
  
- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- PKCS-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt
  - der Administrator das PKCS-Profil ändert oder aktualisiert

## <a name="android-knox-devices"></a>Android KNOX-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt
  - der Administrator den Benutzer oder die Gruppe aus Azure Active Directory (AD) entfernt
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- SCEP-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

- PKCS-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- PKCS-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt
  - der Administrator das PKCS-Profil ändert oder aktualisiert
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt
  
  
> [!NOTE]
> Android for Work-Geräte sind für die zuvor genannten Szenarios nicht freigegeben. Android-Legacygeräte (jedes Profilgerät, das kein Samsung- oder Work-Gerät ist) sind nicht für die Entfernung von Zertifikaten freigegeben. 

## <a name="macos-certificates"></a>macOS-Zertifikate

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - Zertifikatprofil wird aus der Gruppenzuweisung entfernt

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- SCEP-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt

> [!NOTE]
> Die Aktion [Zurücksetzen](devices-wipe.md#wipe) zum Zurücksetzen von macOS-Geräten auf die Werkseinstellungen wird nicht unterstützt.

#### <a name="pkcs-certificates"></a>PKCS-Zertifikate

PKCS-Zertifikate werden nicht unterstützt.

