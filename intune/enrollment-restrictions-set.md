---
title: Festlegen von Registrierungseinschränkungen in Microsoft Intune
titlesuffix: ''
description: Schränken Sie die Registrierung plattformbezogen ein, und legen Sie in Intune einen Grenzwert für die Geräteregistrierung fest.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 76c0b96a1759caad4a1052a7233c7dcc8cecfa3b
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313716"
---
# <a name="set-enrollment-restrictions"></a>Festlegen von Registrierungseinschränkungen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie Registrierungsbeschränkungen erstellen und verwalten, die die Anzahl und Typen von Geräten festlegen, die sich für die Verwaltung mit Intune registrieren können. Sie können mehrere Beschränkungen definieren und diese verschiedenen Benutzergruppen zuordnen. Für Ihre verschiedenen Beschränkungen können Sie eine [Prioritätsreihenfolge](#change-enrollment-restriction-priority) festlegen.

>[!NOTE]
>Registrierungseinschränkungen stellen keine Sicherheitsfunktionen dar. Gefährdete Geräte können falsche Angaben zu ihren Eigenschaften enthalten. Diese Einschränkungen sind eine bestmögliche Barriere für nicht böswillige Benutzer.

Sie können u.a. die folgenden spezifischen Registrierungsbeschränkungen festlegen:

- Maximale Anzahl registrierter Geräte
- Geräteplattformen, die registriert werden können:
  - Android
  - Android-Arbeitsprofil
  - iOS
  - macOS
  - Windows
- Plattformbetriebssystemversion für iOS, Android, Android-Arbeitsprofil und Windows. (Es können nur Windows 10-Versionen verwendet werden. Dieses Feld bleibt leer, wenn Windows 8.1 zulässig ist.)
  - Mindestens erforderliche Version
  - Maximal zulässige Version
- Private Geräte einschränken (nur iOS, Android, Android-Arbeitsprofil, macOS und Windows)

## <a name="default-restrictions"></a>Standardbeschränkungen

Auf den Gerätetyp und das Gerätelimit bezogene Registrierungsbeschränkungen werden standardmäßig vorgeschlagen. Sie können die Optionen für die Standardeinstellungen ändern. Standardbeschränkungen gelten für alle Benutzer- und benutzerlosen Registrierungen. Sie können diese Standardeinstellungen überschreiben, indem Sie neue Beschränkungen mit höheren Prioritäten definieren.

## <a name="create-a-restriction"></a>Definieren einer Beschränkung

1. Melden Sie sich im Azure-Portal an.
2. Klicken Sie auf **Weitere Dienste**, suchen Sie nach **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Klicken Sie auf **Beschränkung erstellen**.
5. Geben Sie für die Beschränkung einen Namen und eine Beschreibung ein.
6. Wählen Sie einen **Beschränkungstyp**, und klicken Sie dann auf **Erstellen**.
7. Um Beschränkungen für das Gerätelimit festzulegen, klicken Sie auf **Gerätelimit**, um die maximale Anzahl von Geräten festzulegen, die ein Benutzer registrieren kann.
8. Klicken Sie für Beschränkungen des Gerätetyps auf **Plattformen** und **Plattformkonfigurationen**, um verschiedene Plattformen und Versionen zuzulassen oder zu blockieren.
9. Klicken Sie auf **Zuweisungen** > **Gruppen auswählen**.
10. Wählen Sie unter **Gruppen auswählen** mindestens eine Gruppen aus, und klicken Sie dann auf **Auswählen**. Die Beschränkung gilt nur für Gruppen, denen sie zugewiesen ist. Wenn Sie nicht mindestens einer Gruppe eine Beschränkung zuweisen, hat sie keine Wirkung.
11. Wählen Sie **Speichern** aus.
12. Die neue Beschränkung wird mit einer Priorität knapp über dem Standardwert erstellt. Sie können [die Priorität ändern](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Festlegen von Gerätetypbeschränkungen

Sie können die Einstellungen für eine Gerätetypbeschränkung ändern, indem Sie die folgenden Schritte ausführen. Diese Beschränkungen haben keine Auswirkungen auf Geräte, die bereits registriert wurden. Geräte, die mit dem [Intune-PC-Agent](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune.md) registriert sind, können nicht über dieses Feature blockiert werden.

1. Melden Sie sich im Azure-Portal an.
2. Klicken Sie auf **Weitere Dienste**, suchen Sie nach **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Gerätetypbeschränkungen** die Beschränkung aus, die Sie festlegen möchten. Dann wählen Sie **Eigenschaften** > **Plattformen auswählen** aus. Wählen Sie für jede aufgeführte Plattform **Zulassen** oder **Blockieren** aus.
    ![Screenshot: Zulassen oder Blockieren einer Plattform](media/enrollment-restrictions-set/platform-allow-block.png)
5. Wählen Sie **OK** aus.
6. Wählen Sie **Plattformen konfigurieren** aus.
    ![Screenshot: Konfigurieren von Plattformen](media/enrollment-restrictions-set/configure-platforms.png)
7. Wählen Sie die mindestens erforderliche und die maximal zulässige **Version** für die aufgelisteten Plattformen aus. Folgende Versionsformate werden unterstützt:
    - Android-Arbeitsprofile unterstützen major.minor.rev.build.
    - iOS unterstützt major.minor.rev. Die Betriebssystemversionen gelten nicht für Apple-Geräte, die mit dem Programm zur Geräteregistrierung, dem Apple School Manager oder der App Apple Configurator registriert werden.
    - Windows unterstützt major.minor.rev.build nur für Windows 10.
8. Wählen Sie für jede aufgeführte Plattform **Zulassen** oder **Blockieren** für **Persönliches Eigentum** aus.
9. Wählen Sie **OK** aus.

### <a name="android-device-type-restrictions"></a>Beschränkungen für Android-Gerätetypen
- Wenn Sie die Registrierung privater Android-Geräte blockieren, können private Android-Arbeitsprofilgeräte weiterhin registriert werden.
- Standardmäßig ändern sich die Android-Arbeitsprofilgeräteeinstellungen gegenüber Ihren Android-Geräteeinstellungen nicht. Dies ändert sich allerdings, nachdem Sie ihre Android-Arbeitsprofileinstellungen geändert haben.
- Wenn Sie die private Android-Arbeitsprofilregistrierung blockieren, können sich nur unternehmenseigene Android-Geräte als Android-Arbeitsprofilgeräte registrieren.

### <a name="windows-device-type-restrictions"></a>Beschränkungen für Windows-Gerätetypen
Nachdem die Beschränkung des Gerätetyps der Windows-Plattform auf **Blockieren** gesetzt wurde, überprüft Intune, ob jede neue Windows-Registrierungsanforderung als Unternehmensregistrierung autorisiert wurde. Nicht autorisierte Registrierungen werden blockiert.

Die folgenden Methoden sind als Windows-Unternehmensregistrierung autorisiert:
 - Der Benutzer, der sich registriert, verwendet ein [Konto für den Geräteregistrierungs-Manager]( device-enrollment-manager-enroll.md).
- Das Gerät wird über [Windows AutoPilot](enrollment-autopilot.md) registriert.
- Die IME-Nummer des Geräts ist unter **Geräteregistrierung** > **[Bezeichner von Unternehmensgeräten](corporate-identifiers-add.md)** aufgeführt. (für Windows Phone 8.1 nicht unterstützt)
- Das Gerät wird über ein [Massenbereitstellungspaket](windows-bulk-enroll.md) registriert.
- Das Gerät wird über eine [automatische Registrierung von SCCM für die Co-Verwaltung](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md) registriert.
 
Die folgenden Registrierungen werden von Intune als unternehmenseigen markiert. Da diese jedoch nicht die gerätespezifische Steuerung über den Intune-Administrator bieten, werden sie blockiert:
 - [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung während der Windows-Einrichtung](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung aus den Windows-Einstellungen](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup.md).
 
Die folgenden persönlichen Registrierungsmethoden werden ebenso blockiert:
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) durch [Hinzufügen eines Geschäftskontos über die Windows-Einstellungen](https://docs.microsoft.com/azure/active-directory/device-management-azuread-registered-devices-windows10-setup.md).
- Die Option [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Nur MDM-Registrierung) in den Windows-Einstellungen.


## <a name="set-device-limit-restrictions"></a>Festlegen von Einschränkungen zum Gerätelimit

Sie können die Einstellungen für eine Gerätelimitbeschränkung ändern, indem Sie diese Schritte ausführen:

1. Melden Sie sich im Azure-Portal an.
2. Klicken Sie auf **Weitere Dienste**, suchen Sie nach **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Einschränkungen zum Gerätelimit** die Beschränkung, die Sie festlegen möchten.
5. Klicken Sie auf **Gerätelimit**, und legen Sie dann in der Dropdownliste die maximale Anzahl der Geräte fest, die ein Benutzer registrieren kann.
    ![Blatt „Einschränkungen zum Gerätelimit“ mit den Einschränkungen zur Gerätebeschränkung](./media/device-restrictions-limit.png)
6. Wählen Sie **Speichern** aus.


Benutzer erhalten eine Benachrichtigung darüber, wann das Limit registrierter Geräte erreicht ist. Bei iOS sieht dies wie folgt aus:

![iOS-Gerätelimitbenachrichtigung](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Ändern der Priorität der Registrierungsbeschränkung

Die Priorität wird verwendet, wenn ein Benutzer in mehreren Gruppen vorhanden ist, denen Beschränkungen zugewiesen sind. Benutzer unterliegen nur der Beschränkung mit der höchsten Priorität, die einer Gruppe zugewiesen wurde, zu der sie gehören. Beispiel: Joe gehört zu Gruppe A, der Beschränkungen der Priorität 5 zugewiesen sind, und zu Gruppe B, der Beschränkungen der Priorität 2 zugeordnet sind. Joe unterliegt also nur Einschränkungen der Priorität 2.

Wenn Sie eine Beschränkung definieren, wird sie der Liste direkt über dem Standardwert hinzugefügt.

Zur Geräteregistrierung gehören Standardbeschränkungen für den Gerätetyp und das Gerätelimit. Diese beiden Beschränkungen gelten für alle Benutzer, es sei denn, sie werden durch Beschränkungen höherer Priorität außer Kraft gesetzt.

Sie können die Priorität jeder nicht standardmäßigen Beschränkung ändern.

1. Melden Sie sich im Azure-Portal an.
2. Klicken Sie auf **Weitere Dienste**, suchen Sie nach **Intune**, und klicken Sie dann auf **Intune**.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Zeigen Sie in der Prioritätenliste auf die Beschränkung.
5. Ziehen Sie mithilfe der drei vertikalen Punkte die Priorität an die gewünschte Position in der Liste.
