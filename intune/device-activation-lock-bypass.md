---
title: Umgehung der iOS-Aktivierungssperre mit Intune
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie mithilfe von Intune die iOS-Aktivierungssperre umgehen, um auf gesperrte Geräte zuzugreifen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b37c210425fd5abf8fd0b0501966fef8196b451b
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312620"
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Umgehen der Aktivierungssperre auf überwachten iOS-Geräten mit Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune kann Sie bei der Verwaltung der iOS-Aktivierungssperre unterstützen, einer Funktion der Mein iPhone suchen-App für Geräte mit iOS 8.0 und höher. Die Aktivierungssperre wird automatisch aktiviert, wenn ein Benutzer die App „Mein iPhone suchen“ auf einem Gerät öffnet. Nach der Aktivierung müssen die Apple-ID und das Kennwort des Benutzers eingegeben werden, bevor folgende Vorgänge möglich sind:

- Deaktivieren von „Mein iPhone suchen“
- Löschen des Geräts
- Reaktivieren des Geräts

## <a name="how-activation-lock-affects-you"></a>Auswirkungen der Aktivierungssperre

Obwohl die Aktivierungssperre zum Schutz von iOS-Geräten beiträgt und die Chancen einer Wiederherstellung bei Verlust oder Diebstahl des Geräts erhöht, kann diese Funktion Sie als IT-Administrator vor eine Reihe von Herausforderungen stellen. Beispiel:

- Ein Benutzer richtet die Aktivierungssperre auf einem Gerät ein. Anschließend verlässt der Benutzer das Unternehmen und gibt das Gerät zurück. Ohne die Apple-ID und das Kennwort des Benutzers gibt es keine Möglichkeit, das Gerät zu reaktivieren.
- Sie benötigen einen Bericht über alle Geräte, bei denen die Aktivierungssperre aktiviert ist.
- Während einer Geräteaktualisierung in Ihrem Unternehmen möchten Sie einige Geräte einer anderen Abteilung zuweisen. Es können nur Geräte neu zugewiesen werden, bei denen die Aktivierungssperre nicht aktiviert ist.

Apple hat zur Behebung dieser Probleme eine Umgehung der Aktivierungssperre in iOS 7.1 eingeführt. Mit der Umgehung der Aktivierungssperre können Sie die Aktivierungssperre von überwachten Geräten ohne Apple-ID und Kennwort des Benutzers entfernen. Überwachte Geräte können einen gerätespezifischen Umgehungscode für die Aktivierungssperre generieren, der auf dem Aktivierungsserver von Apple gespeichert wird.

>[!TIP]
>Im überwachten Modus für iOS-Geräte können Sie mit dem Apple Configurator ein Gerät sperren, um die Funktionen auf bestimmte geschäftliche Zwecke zu beschränken. Der überwachte Modus ist in der Regel nur für firmeneigene Geräte vorgesehen.

Auf der [Website von Apple](https://support.apple.com/HT201365) erfahren Sie mehr über die Aktivierungssperre.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Unterstützung von Intune beim Verwalten der Aktivierungssperre
Intune kann den Status der Aktivierungssperre von überwachten Geräten anfordern, die iOS 8.0 und höher ausführen. Ausschließlich für überwachte Geräte kann Intune den Umgehungscode der Aktivierungssperre abrufen und ihn direkt auf das Gerät anwenden. Wenn das Gerät zurückgesetzt wurde, können Sie direkt auf das Gerät zugreifen, indem Sie einen leeren Benutzernamen und den Code als Kennwort verwenden.

**Die Unternehmensvorteile der Verwaltung der Aktivierungssperre mit Intune sind Folgende:**

- Der Benutzer erhält die Sicherheitsvorteile der App „Mein iPhone suchen“.
- Sie können es den Benutzern ermöglichen, ihre Arbeit zu erledigen, in dem Wissen, dass Sie das Gerät außer Kraft setzen oder entsperren können, wenn es einem neuen Zweck zugewiesen werden soll.

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie die Aktivierungssperre auf Geräten umgehen können, müssen Sie sie aktivieren, indem Sie dieser Anleitung folgen:

1. Konfigurieren Sie ein Intune-Profil für die Einschränkung von Geräten für iOS. Verwenden Sie dafür die Informationen unter [So konfigurieren Sie Einstellungen für Geräteeinschränkungen](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Aktivieren Sie in den [Einstellungen für Geräteeinschränkungen für iOS](device-restrictions-ios.md) unter **Allgemein** die Option **Aktivierungssperre**.
3. Speichern Sie das Profil, und [weisen Sie es den Geräten zu](device-profile-assign.md), auf denen Sie die Umgehung der Aktivierungssperre verwalten möchten.


## <a name="how-to-use-activation-lock-bypass"></a>Verwenden der Umgehung der Aktivierungssperre

>[!IMPORTANT]
>Nachdem die Aktivierungssperre auf einem Gerät umgangen wurde, wird automatisch eine neue Aktivierungssperre angewendet, wenn die App „Mein iPhone suchen“ gestartet wird. Aus diesem Grund **muss das Gerät physisch verfügbar sein, bevor Sie dieses Verfahren ausführen**.

Die Intune-Remotegeräteaktion **Aktivierungssperre umgehen** entfernt die Aktivierungssperre von einem iOS-Gerät, ohne dass die Apple-ID und das Kennwort des Benutzers angegeben werden müssen. Nachdem Sie die Aktivierungssperre umgangen haben, aktiviert das Gerät die Aktivierungssperre erneut, wenn die App „Mein iPhone suchen“ gestartet wird. Umgehen Sie die Aktivierungssperre nur, wenn Sie direkten Zugriff auf das Gerät haben.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräte** aus.
4. Wählen Sie auf dem Blatt **Geräte** die Option **Alle Geräte** aus.
5. Wählen Sie sie aus der Liste mit von Ihnen verwalteten Geräten die Remotegeräteaktion **Aktivierungssperre umgehen** aus.
6. Navigieren Sie zum Abschnitt „Hardware“, und kopieren Sie den Wert **Code zum Umgehen der Aktivierungssperre** unter **Bedingter Zugriff**.

    >[!NOTE]
    >Kopieren Sie den Umgehungscode, bevor Sie das Gerät zurücksetzen. Wenn Sie die Geräteeinstellungen zurücksetzen, bevor Sie den Code kopieren, wird dieser aus Azure entfernt.

7.  Navigieren Sie zum Blatt **Übersicht** des Geräts, und klicken Sie dann auf **Zurücksetzen**.
8.  Nachdem das Gerät zurückgesetzt wurde, werden Sie aufgefordert, die *Apple-ID* und das *Kennwort* einzugeben. Lassen Sie das Feld *ID* leer, und geben Sie den **Umgehungscode** für das *Kennwort* ein. Dadurch wird das Konto von dem Gerät entfernt. 


## <a name="next-steps"></a>Nächste Schritte

Sie können den Status der Entsperranforderung in der Workload **Geräte verwalten** auf der Detailseite für das Gerät überprüfen.
