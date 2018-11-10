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
ms.custom: intune-azure
ms.openlocfilehash: d4287322fd494c97cf24feb8cc16435a4405f2af
ms.sourcegitcommit: 7a649a5995600fb91817643e20a5565caedbb8f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50150102"
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
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird

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
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird 


## <a name="ios-devices"></a>iOS-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:

  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator das SCEP-Profil ändert oder aktualisiert

- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird

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
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird
  
- Das Stammzertifikat wird entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt

- PKCS-Zertifikate **verbleiben** auf dem Gerät (d.h., sie werden weder widerrufen noch entfernt), wenn:
  - ein Endbenutzer seine Intune-Lizenz verliert
  - der Administrator die Intune-Lizenz widerruft
  - der Administrator den Benutzer oder die Gruppe aus Azure AD entfernt
  - der Administrator das PKCS-Profil ändert oder aktualisiert

## <a name="android--android-enterprise-devices"></a>Android- und Android Enterprise-Geräte

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Zurücksetzen](devices-wipe.md#wipe) durchführt

- SCEP-Zertifikate werden widerrufen, wenn:
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird
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
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird 

## <a name="macos-certificates"></a>macOS-Zertifikate

#### <a name="scep-certificates"></a>SCEP-Zertifikate

- SCEP-Zertifikate werden widerrufen *und* entfernt, wenn:
  - die Registrierung eines Endbenutzers aufgehoben wird
  - der Administrator die Aktion [Außer Betrieb nehmen](devices-wipe.md#retire) durchführt
  - das Gerät aus der Azure Active Directory-Gruppe entfernt wird
  - die Konformitätsrichtlinie aus der Gruppenzuweisung entfernt wird
  - das Konfigurationsprofil aus der Gruppenzuweisung entfernt wird

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

