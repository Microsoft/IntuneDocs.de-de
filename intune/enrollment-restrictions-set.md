---
title: "Festlegen von Registrierungseinschränkungen in Microsoft Intune"
titlesuffix: 
description: "Schränken Sie die Registrierung plattformbezogen ein, und legen Sie in Intune einen Grenzwert für die Geräteregistrierung fest."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 396c8881ba0dfae5cfad4eab9bf787b6a9f33d44
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="set-enrollment-restrictions"></a>Festlegen von Registrierungseinschränkungen

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie Registrierungseinschränkungen erstellen und verwalten. Diese Einschränkungen definieren die Anzahl und Arten von Geräten, die bei der Verwaltung mit Intune registriert werden können. Sie können mehrere Beschränkungen definieren und diese verschiedenen Benutzergruppen zuordnen. Für Ihre verschiedenen Beschränkungen können Sie eine [Prioritätsreihenfolge](#change-enrollment-restriction-priority) festlegen.

>[!NOTE]
>Registrierungseinschränkungen stellen keine Sicherheitsfunktionen dar. Gefährdete Geräte können falsche Angaben zu ihren Eigenschaften enthalten. Diese Einschränkungen sind eine bestmögliche Barriere für nicht böswillige Benutzer.

>[!NOTE]
>Die unten aufgeführten Einschränkungen von Gruppen zugewiesenen Registrierungen und Prioritätsfunktionen werden derzeit für den gesamten Intune-Kundenstamm bereitgestellt. Bis zur vollständigen Durchführung der Bereitstellung kann es sein, dass Sie noch keinen Zugriff auf Gruppen- und Prioritätsfeatures haben.

Sie können u.a. die folgenden spezifischen Registrierungsbeschränkungen festlegen:

- Maximale Anzahl registrierter Geräte
- Geräteplattformen, die registriert werden können:
  - Android
  - Android for Work
  - iOS
  - macOS
  - Windows
- Plattform-Betriebssystemversion für iOS, Android, Android for Work und Windows (es können nur Windows 10-Versionen verwendet werden. Lassen Sie diese Einstellung leer, wenn Windows 8.1 zulässig ist)
  - Mindestversion
  - Maximalversion
- Geräte in Privatbesitz einschränken (nur iOS, Android, Android for Work und macOS)

## <a name="default-restrictions"></a>Standardbeschränkungen

Auf den Gerätetyp und das Gerätelimit bezogene Registrierungsbeschränkungen werden standardmäßig vorgeschlagen. Sie können die Optionen für die Standardeinstellungen ändern. Standardbeschränkungen gelten für alle Benutzer- und benutzerlosen Registrierungen. Sie können diese Standardeinstellungen überschreiben, indem Sie neue Beschränkungen mit höheren Prioritäten definieren.

## <a name="create-a-restriction"></a>Definieren einer Beschränkung

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste**, suchen Sie nach **Intune**, und wählen Sie dann **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie **Beschränkung erstellen**.
5. Geben Sie für die Beschränkung einen Namen und eine Beschreibung ein.
6. Wählen Sie einen **Beschränkungstyp**, und klicken Sie dann auf **Erstellen**.
7. Um Beschränkungen für das Gerätelimit festzulegen, klicken Sie auf **Gerätelimit**, um die maximale Anzahl von Geräten festzulegen, die ein Benutzer registrieren kann.
8. Klicken Sie für Beschränkungen des Gerätetyps auf **Plattformen** und **Plattformkonfigurationen**, um verschiedene Plattformen und Versionen zuzulassen oder zu blockieren.
9. Klicken Sie auf **Zuweisungen** > **+ Gruppen auswählen**.
10. Wählen Sie unter **Gruppen** eine oder mehrere Gruppen aus, und klicken Sie dann auf **Auswählen**. Die Beschränkung gilt nur für Gruppen, denen sie zugewiesen ist. Wenn Sie nicht mindestens einer Gruppe eine Beschränkung zuweisen, hat sie keine Wirkung.
11. Klicken Sie auf **Speichern**.
12. Die neue Beschränkung wird mit einer Priorität knapp über dem Standardwert erstellt. Sie können [die Priorität ändern](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Festlegen von Gerätetypbeschränkungen

Sie können die Einstellungen für eine Gerätetypbeschränkung ändern, indem Sie diese Schritte ausführen:

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste**, suchen Sie nach **Intune**, und wählen Sie dann **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Gerätetypbeschränkungen** die Beschränkung, die Sie festlegen möchten.
5. Wählen Sie unter dem Namen der Beschränkung (**Alle Benutzer** für die Standardbeschränkung) die Option **Plattformen** aus. Wählen Sie für jede aufgeführte Plattform **Zulassen** oder **Blockieren** aus.
6. Klicken Sie auf **Speichern**.
7. Wählen Sie unter dem Namen der Beschränkung (**Alle Benutzer** für die Standardbeschränkung) **Plattformkonfigurationen** und dann die minimale und maximale **Version** für die aufgeführte Plattform aus. Die folgenden Versionen werden unterstützt:
  - Android und Android for Work unterstützen major.minor.rev.build.
  - iOS unterstützt major.minor.rev.
  - Windows unterstützt major.minor.rev.build nur für Windows 10.
  Die Betriebssystemversionen gelten nicht für Apple-Geräte, die mit dem Programm zur Geräteregistrierung, dem Apple School Manager oder der App Apple Configurator registriert werden.
8. Wählen Sie für jede aufgeführte Plattform **Zulassen** oder **Blockieren** für **Geräte in Privatbesitz** aus.

    ![Screenshot des Arbeitsbereichs „Geräteeinschränkungen“ mit der für Geräte in Privatbesitz konfigurierten Standardgeräteplattform](media/device-restrictions-platform-configurations.png)
9. Klicken Sie auf **Speichern**.

>[!NOTE]
>- Wenn Sie die Registrierung privater Android-Geräte blockieren, können private Android for Work-Geräte weiterhin registriert werden.
>- Standardmäßig ändern sich die Android for Work-Geräteeinstellungen gegenüber Ihren Android-Geräteeinstellungen nicht. Dies ändert sich allerdings, nachdem Sie ihre Android for Work-Einstellungen geändert haben.
>- Wenn Sie die private Android for Work-Registrierung blockieren, können sich nur unternehmenseigene Android-Geräte als Android for Work-Geräte registrieren.

## <a name="set-device-limit-restrictions"></a>Festlegen von Einschränkungen zum Gerätelimit

Sie können die Einstellungen für eine Gerätelimitbeschränkung ändern, indem Sie diese Schritte ausführen:

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste**, suchen Sie nach **Intune**, und wählen Sie dann **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Einschränkungen zum Gerätelimit** die Beschränkung, die Sie festlegen möchten.
5. Wählen Sie **Gerätelimit** und dann in der Dropdownliste die maximale Anzahl der Geräte aus, die ein Benutzer registrieren kann.
    ![Screenshot des Blatts „Einschränkungen zum Gerätelimit“](./media/device-restrictions-limit.png)
6. Klicken Sie auf **Speichern**.

Ihr Endbenutzer erhält eine Benachrichtigung darüber, wann sein Limit registrierter Geräte erreicht ist. Bei iOS würde dies wie folgt aussehen:

![Screenshot der iOS-Gerätelimitbenachrichtigung](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Ändern der Priorität der Registrierungsbeschränkung

Die Priorität wird verwendet, wenn ein Benutzer in mehreren Gruppen vorhanden ist, denen Beschränkungen zugewiesen sind. Benutzer unterliegen nur der Beschränkung mit der höchsten Priorität, die einer Gruppe zugewiesen wurde, zu der sie gehören. Beispiel: Johanna gehört zur Gruppe A, der Beschränkungen der Priorität 5 zugewiesen ist, und zur Gruppe B, der Beschränkungen der Priorität 2 zugeordnet sind. Johanna unterliegt also nur Einschränkungen der Priorität 2.

Wenn Sie eine Beschränkung definieren, wird sie der Liste direkt über dem Standardwert hinzugefügt.

Zur Geräteregistrierung gehören Standardbeschränkungen für den Gerätetyp und das Gerätelimit. Diese beiden Beschränkungen gelten für alle Benutzer, es sei denn, sie werden durch Beschränkungen höherer Priorität außer Kraft gesetzt.

Sie können die Priorität jeder nicht standardmäßigen Beschränkung ändern.

**So ändern Sie Priorität einer Beschränkung**

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste**, suchen Sie nach **Intune**, und wählen Sie dann **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Zeigen Sie in der Prioritätenliste auf die Beschränkung.
5. Ziehen Sie mithilfe der drei vertikalen Punkte die Priorität an die gewünschte Position in der Liste.
