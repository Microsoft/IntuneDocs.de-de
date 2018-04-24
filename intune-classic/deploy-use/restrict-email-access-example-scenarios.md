---
title: Schützen von E-Mail-Szenarien
description: Einige Beispielszenarien und wie sie mit bedingtem Zugriff implementiert werden könnten.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3116cfdb6b1ea153d914630a23e0db82a8c31d85
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="protect-access-to-email-with-microsoft-intune-example-scenarios"></a>Schützen des E-Mail-Zugriffs mit Microsoft Intune: Beispielszenarios

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>Szenario 1: Blockieren des Zugriffs auf Exchange Online durch Benutzer nicht kompatibler Geräte
### <a name="scenario-requirements"></a>Anforderungen für das Szenario
- Der Zugriff auf Exchange Online muss für alle Benutzer in der Azure Active Directory-Sicherheitsgruppe **Accounting** blockiert werden, wenn das verwendete Gerät einer von Ihnen bereitgestellten Kompatibilitätsrichtlinie nicht entspricht.
- Wenn in dieser Gruppe Benutzer vorhanden sind, deren Geräte von Intune nicht unterstützt werden, muss der Zugriff auf Exchange Online über diese Geräte blockiert werden.
- Benutzer in der Azure Active Directory-Sicherheitsgruppe **Finance** müssen von der Richtlinie ausgenommen werden, auch wenn sie sich ebenfalls in der Sicherheitsgruppe **Accounting** befinden.

Um dies zu erreichen, konfigurieren Sie eine Richtlinie für bedingten Zugriff für Exchange Online mit folgenden Einstellungen:

- Wählen Sie **Richtlinie für bedingten Zugriff aktivieren** aus.

- Wählen Sie die Plattformen aus, auf denen Sie Zugriff über Apps mit moderner Authentifizierung zulassen möchten.
- Wählen Sie für Exchange ActiveSync-Apps **Nicht kompatible Geräte auf Plattformen blockieren, die von Microsoft Intune unterstützt werden** und **Alle weiteren Geräte auf Plattformen blockieren, die nicht von Microsoft Intune unterstützt werden**.
-   Wählen Sie im Abschnitt **Zielgruppe** unter **Ausgewählte Sicherheitsgruppen** die Benutzergruppe **Accounting** aus.

-   Wählen Sie im Abschnitt **Ausgenommen Gruppe** unter **Ausgewählte Sicherheitsgruppen** die Benutzergruppe **Finance** aus.


Der folgende Ablauf wird im Szenario verwendet, um zu entscheiden, welche Geräte auf Exchange Online zugreifen können:

![Ablauf für Gerätezugriff](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>Szenario 2: Alle iOS-Geräte, die auf lokales Exchange zugreifen, müssen von Intune verwaltet werden
### <a name="scenario-requirements"></a>Anforderungen für das Szenario
- Nur Geräten, auf denen iOS ausgeführt wird, sollte Zugriff auf lokales Exchange gewährt werden.
- Die Geräte müssen auch bei Intune registriert sein und die Regeln der Konformitätsrichtlinie erfüllen, bevor sie für den Zugriff auf Exchange verwendet werden können.

Um dies zu erreichen, konfigurieren Sie die folgende Richtlinie für bedingten Zugriff für lokales Exchange mit folgenden Einstellungen:

- Wählen Sie die Option **Zugriff auf lokales Exchange von E-Mail-Apps blockieren, wenn das Gerät nicht kompatibel oder nicht bei Microsoft Intune registriert ist**. Wenn Sie diese Option auswählen, aktivieren Sie die Richtlinie für bedingten Zugriff, die erfordert, dass alle Geräte bei Microsoft Intune registriert sein und die Regeln der Kompatibilitätsrichtlinie erfüllen müssen, bevor sie auf Exchange zugreifen können.

- Erstellen Sie für die erweiterten Exchange ActiveSync-Einstellungen Folgendes:

  -   Eine Plattformausnahme, die Geräten mit iOS erlaubt, auf Exchange zuzugreifen.   

  -   Eine Standardregel, die festlegt, dass der Zugriff auf Exchange über ein Gerät, das nicht durch die Plattformausnahmeregel abgedeckt ist, blockiert werden soll. Diese Regel stellt sicher, dass der Zugriff auf Exchange über Geräte, auf denen iOS nicht ausgeführt wird, blockiert wird.

Sie verwenden den folgenden Ablauf, um zu entscheiden, welche Geräte auf Exchange zugreifen können:

![Ablauf für Gerätezugriff](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>Szenario 3: Kein Android-Gerät darf auf lokales Exchange zugreifen
### <a name="scenario-requirements"></a>Anforderungen für das Szenario
- Der Zugriff auf Exchange soll für alle Android-Geräte blockiert werden.
- Alle anderen unterstützten Geräte können auf Exchange zugreifen, solange sie von Intune verwaltet werden.

Um dies zu erreichen, konfigurieren Sie eine Richtlinie für bedingten Zugriff für lokales Exchange mit folgenden Einstellungen:

-   Wählen Sie die Option **Zugriff auf lokales Exchange von E-Mail-Apps blockieren, wenn das Gerät nicht kompatibel oder nicht bei Microsoft Intune registriert ist**. Durch Auswahl dieser Option legen Sie fest, dass alle Geräte bei Intune registriert sein und die Regeln der Kompatibilitätsrichtlinie erfüllen müssen.

- Erstellen Sie für die erweiterten Exchange ActiveSync-Einstellungen Folgendes:
  -   Eine Plattformausnahme, die verhindert, dass Geräte mit Android auf Exchange zugreifen. Diese Regel stellt sicher, dass Android-Geräte nicht für den Zugriff auf Exchange verwendet werden können.

  -   Eine Standardregel, die angibt, dass ein Gerät für den Zugriff auf Exchange zugelassen werden soll, wenn es nicht durch andere Regeln abgedeckt wird. Diese Standardregel stellt sicher, dass Geräte, auf denen andere Plattformen als Android ausgeführt werden, die aber von Microsoft Intune unterstützt werden, für den Zugriff auf Exchange verwendet werden können. Sie müssen jedoch bei Intune registriert sein und die Regeln der Kompatibilitätsrichtlinie erfüllen.

Sie verwenden den folgenden Ablauf, um zu entscheiden, welche Geräte auf Exchange zugreifen können:

![Ablauf für Gerätezugriff](./media/ConditionalAccess8-4.png)
