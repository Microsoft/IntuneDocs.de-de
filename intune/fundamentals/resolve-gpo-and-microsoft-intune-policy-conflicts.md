---
title: Lösen von Konflikten mit Gruppenrichtlinienobjekten und Intune-Richtlinien
titleSuffix: Microsoft Intune
description: Informationen zum Lösen von Konflikten zwischen Gruppenrichtlinie und Intune-Konfigurationsrichtlinien.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 745534f2c65bc9585ab4639f9d5a6d101638c5f9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509849"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Lösen von Konflikten mit Gruppenrichtlinienobjekten und Microsoft Intune-Richtlinien

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> Die Informationen in diesem Thema gelten nur für Windows-Desktops, die Sie als PCs mithilfe des Intune-Softwareclients verwalten.

In Intune können Sie Richtlinien zum Verwalten der Einstellungen auf Windows-PCs verwenden. Beispielsweise können Sie eine Richtlinie verwenden, um Einstellungen für die Windows-Firewall auf PCs zu steuern. Viele Intune-Einstellungen sind mit Einstellungen vergleichbar, die Sie mit Windows-Gruppenrichtlinien konfigurieren können. Es ist allerdings manchmal möglich, dass die beiden Methoden miteinander in Konflikt stehen.

Wenn Konflikte auftreten, hat die Gruppenrichtlinie auf Domänenebene Vorrang vor der Intune-Richtlinie, sofern die Anmeldung des PCs bei der Domäne möglich ist. In diesem Fall wird die Intune-Richtlinie auf den Client-PC angewendet.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Vorgehensweise bei Verwendung von Gruppenrichtlinien
Stellen Sie sicher, dass Richtlinien, die Sie anwenden, nicht von Gruppenrichtlinien verwaltet werden. Zum Vermeiden von Konflikten können Sie eine oder mehrere der folgenden Methoden verwenden:

- Verschieben Sie Ihre PCs in eine Active Directory-Organisationseinheit (OU), auf die keine Gruppenrichtlinieneinstellungen angewendet werden, bevor Sie den Intune-Client installieren. Sie können bei OUs mit PCs, die in Intune registriert sind und auf die Sie die Gruppenrichtlinieneinstellungen nicht anwenden möchten, auch die Vererbung der Gruppenrichtlinie deaktivieren.

- Verwenden Sie einen Sicherheitsgruppenfilter, um Gruppenrichtlinienobjekte auf PCs zu beschränken, die nicht mit Intune verwaltet werden.

- Deaktivieren oder entfernen Sie Gruppenrichtlinienobjekte, die mit den Intune-Richtlinien in Konflikt stehen.

Weitere Informationen zu Active Directory und Windows-Gruppenrichtlinien finden Sie in Ihrer Windows Server-Dokumentation.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Filtern vorhandener Gruppenrichtlinienobjekte, um Konflikte mit Intune-Richtlinien zu vermeiden
Wenn Sie Gruppenrichtlinienobjekte ermittelt haben, deren Einstellungen in Konflikt mit Intune-Richtlinien stehen, können Sie Sicherheitsgruppenfilter verwenden, um diese Gruppenrichtlinienobjekte auf PCs zu beschränken, die nicht mit Intune verwaltet werden.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1. Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2. Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3. Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    - For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    - For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4. Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    - For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    - For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Sie können GPOs auf nur die Sicherheitsgruppen anwenden, die im Bereich **Sicherheitsfilterung** der Gruppenrichtlinien-Verwaltungskonsole für ein ausgewähltes GPO festgelegt sind. Standardmäßig gelten Gruppenrichtlinienobjekte für *Authentifizierte Benutzer*.

- Erstellen Sie im Snap-In **Active Directory-Benutzer und -Computer** eine neue Sicherheitsgruppe, die Computer und Benutzerkonten enthält, die nicht über Intune verwaltet werden sollen. Nennen Sie die Gruppe z. B. *Nicht in Microsoft Intune*.

- Klicken Sie auf der Registerkarte **Delegierung** in der Gruppenrichtlinien-Verwaltungskonsole mit der rechten Maustaste auf die neue Sicherheitsgruppe, um den Benutzern und Computern in der Sicherheitsgruppe die geeigneten Berechtigungen **Lesen** und **Gruppenrichtlinie übernehmen** zu delegieren. (Die Berechtigungen**Gruppenrichtlinie übernehmen** befinden sich im Dialogfeld **Erweitert** .)

- Wenden Sie dann den neuen Sicherheits-Gruppenfilter auf ein ausgewähltes Gruppenrichtlinienobjekt an, und entfernen Sie den Standardfilter **Authentifizierte Benutzer** .

Die neue Sicherheitsgruppe muss in den Intune-Dienständerungen als Registrierung verwaltet werden.

## <a name="see-also"></a>Siehe auch
[Verwalten von Windows-PCs mit Microsoft Intune](../manage-windows-pcs-with-microsoft-intune.md)
