---
title: 'Schnellstart: Erstellen und Zuweisen von App-Schutzrichtlinien'
titlesuffix: Microsoft Intune
description: In diesem Schnellstart erfahren Sie, wie Sie Microsoft Intune zum Erstellen und Zuweisen von App-Schutzrichtlinien verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2ae378550a75f756390053e44eb4fbd04f665612
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179074"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>Schnellstart: Erstellen und Zuweisen von App-Schutzrichtlinien

In diesem Schnellstart erfahren Sie, wie Sie mithilfe von Intune eine App-Schutzrichtlinie erstellen und einer Client-App auf dem Gerät eines Endbenutzers zuweisen. Intune verwendet App-Schutzrichtlinien, um zu überprüfen, ob bestimmte Apps die Datenschutzanforderungen des jeweiligen Unternehmens erfüllen.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen

- Sie müssen für diesen Schnellstart [einen Benutzer](quickstart-create-user.md) und [eine Gruppe erstellen](quickstart-create-group.md), [ein Gerät registrieren](quickstart-setup-auto-enrollment.md) und [eine App hinzufügen und zuweisen](quickstart-add-assign-app.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators). Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-an-app-protection-policy"></a>Erstellen einer App-Schutzrichtlinie

Führen Sie die folgenden Schritte aus, um eine App-Schutzrichtlinie zu erstellen:

1. Klicken Sie unter [Intune](https://aka.ms/intuneportal) auf **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie erstellen**. 
2. Geben Sie die folgenden Informationen an: 

    - **Name:** *Inhaltsschutz für Windows 10*
    - **Beschreibung:** *Benutzer, denen die Richtlinie zugewiesen ist, können in zugewiesenen Apps und anderen nicht verwalteten Apps auf dem Gerät keine Inhalte ausschneiden, kopieren oder einfügen.*
    - **Plattform**: *Windows 10*
    - **Registrierungsstatus:** *Mit Registrierung*

3. Klicken Sie auf **Protected apps** (Geschützte Apps), um die Apps auszuwählen, für die diese Richtlinie gelten soll.
4. Klicken Sie auf **Apps hinzufügen**.
5. Klicken Sie unter **Empfohlene Apps** auf **Word Mobile**.
5. Klicken Sie auf **OK** > **OK**. 
6. Klicken Sie auf **Erforderliche Einstellungen**, um die App zu konfigurieren.
7. Klicken Sie auf **Außerkraftsetzungen zulassen**, um den Windows Information Protection-Modus festzulegen. Wenn Sie diese Option auswählen, wird verhindert, dass Unternehmensdaten die geschützte App verlassen.
8. Klicken Sie auf **OK** > **Erstellen**.

Dann sollte die App-Schutzrichtlinie in Intune angezeigt werden.

### <a name="assign-the-app-protection-policy"></a>Zuweisen von App-Schutzrichtlinien

Wenn Sie eine App-Schutzrichtlinie in Intune erstellt haben, können Sie diese Gruppen zuweisen. 

Führen Sie die folgenden Schritte aus, um eine App-Schutzrichtlinie zu zuzuweisen:

1.  Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Intune** > **Client-Apps** > **App-Schutzrichtlinien**. 
2.  Wählen Sie die App-Schutzrichtlinie aus, die Sie zuvor erstellt haben. In diesem Schnellstart heißt die Richtlinie **Inhaltsschutz für Windows 10**.
3.  Wählen Sie **Zuweisungen** aus.
4.  Klicken Sie auf der Registerkarte **Einschließen** auf **Select groups to include** (Einzuschließende Gruppen auswählen).
5.  Wählen Sie **Contoso Testers** als einzuschließende Gruppe aus.
6.  Klicken Sie auf **Auswählen**. 

Somit ist die App-Schutzrichtlinie zugewiesen.

> [!NOTE]
> App-Schutzrichtlinien können nur auf Gruppen angewendet werden, denen Benutzer angehören. Gruppen, denen Geräte angehören, sind davon ausgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart wurde erläutert, wie Sie App-Schutzrichtlinien erstellen und zuweisen können. Benutzer, denen die Richtlinie zugewiesen ist, können in zugewiesenen Apps und anderen nicht verwalteten Apps auf dem Gerät keine Inhalte ausschneiden, kopieren oder einfügen. Dadurch werden die Daten Ihrer Organisation geschützt. Weitere Informationen zu App-Schutzrichtlinien in Intune finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen und Zuweisen einer benutzerdefinierten Rolle](quickstart-create-custom-role.md)