---
title: Graph-APIs zum Konfigurieren von Geräten in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Eine Liste aller Entitäten, die Graph-API mit dem entsprechenden Windows-CSP und Offset URI auf Windows 10-Geräte und höher verwendet werden soll, beim Konfigurieren von Geräten in Microsoft Intune. Finden Sie im entsprechenden API- und CSP shared-PCs, endpointprotection, Windows Defender advanced Threat Protection, Identity Protection, Windows 10-Teams, Kioskmodus und Windows Update for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e18ed81cc1e61f81323b3c06fd6af9dfe4f4f360
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57400533"
---
# <a name="graph-apis-and-matching-windows-10-csps-used-in-intune"></a>Graph-APIs und zum Abgleich von Windows 10-CSPs, die in Intune verwendet

Microsoft Intune verwendet die [Graph-API-Entitäten](https://docs.microsoft.com/graph/api/resources/intune-graph-overview) (öffnet eine andere Dokumentationswebsite) zum Konfigurieren von Geräten (**Intune** > **Gerätekonfiguration**) unter Windows 10 und höher. Der Graph-API verwendet Konfigurationsdienstanbieter (CSP) zu lesen, festzulegen, ändern, und/oder Konfigurationseinstellungen auf Geräten zu löschen.

Diese Liste gilt für:

- Windows 10 und höher

Dieser Artikel beschreibt die Graph-Entitäten und deren entsprechende Windows 10-CSPs und URIs.

Diese Informationen sind nützlich für eine Vielzahl von Szenarien. Beispielsweise sehen Sie, was von Intune verwendet wird, finden Sie unter Einstellungen für benutzerdefinierte OMA-URI-Konfigurationen, und so weiter. 

## <a name="windows-10-csps"></a>Windows 10 CSPs

Weitere Informationen zu den Konfigurationsdienstanbieter für Windows 10, finden Sie unter den [Konfigurationsdienstanbieter-Referenz](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (öffnet eine andere Docs-Website).

## <a name="graph-api-properties-to-csp-mapping"></a>Graph-API-Eigenschaften für die CSP-Zuordnung

Die folgende Liste enthält die Mehrzahl der Graph-API-Entitäten, die von Microsoft Intune für Windows 10-Gerätekonfiguration verwendet. Darüber hinaus wird gezeigt, die entsprechenden Windows 10-CSP und URI.

Um Windows 10-Versionen anzuzeigen, die folgenden APIs gelten, verwenden Sie das Windows 10- [Konfigurationsdienstanbieter-Referenz](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (öffnet eine andere Docs-Website).

#### <a name="editionupgradeconfigurationlicense"></a>EditionUpgradeConfiguration.License 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**Offset URI**: /UpgradeEditionWithLicense

#### <a name="editionupgradeconfigurationlicensetype"></a>EditionUpgradeConfiguration.LicenseType 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**Offset URI**: /LicenseKeyType

#### <a name="editionupgradeconfigurationproductkey"></a>EditionUpgradeConfiguration.ProductKey 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**Offset URI**: /UpgradeEditionWithProductKey

#### <a name="editionupgradeconfigurationwindowssmode"></a>EditionUpgradeConfiguration.WindowsSMode 
**CSP**: ./Device/Vendor/MSFT/WindowsLicensing  
**Offset URI**: / SMode/SwitchingPolicy

#### <a name="sharedpcconfigurationaccountmanagerpolicy"></a>SharedPCConfiguration.AccountManagerPolicy 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /DeletionPolicy, /DiskLevelCaching, /InactiveThreshold, /DiskLevelDeletion

#### <a name="sharedpcconfigurationaccountmanagerpolicy-windows-holographic-for-business-edition-targeted-devices"></a>SharedPCConfiguration.AccountManagerPolicy (Windows Holographic for Business-Edition, die Ziel-Geräte) 
**CSP**: ./Vendor/MSFT/AccountManagement  
**Offset URI**: /DeletionPolicy, /StorageCapacityStartDeletion, /StorageCapacityStopDeletion, /ProfileInactivityThreshold

#### <a name="sharedpcconfigurationallowedaccounts"></a>SharedPCConfiguration.AllowedAccounts 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /AccountModel

#### <a name="sharedpcconfigurationallowlocalstorage"></a>SharedPCConfiguration.AllowLocalStorage 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /RestrictLocalStorage

#### <a name="sharedpcconfigurationdisableaccountmanager"></a>SharedPCConfiguration.DisableAccountManager 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /EnableAccountManager

#### <a name="sharedpcconfigurationdisableedupolicies"></a>SharedPCConfiguration.DisableEduPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SetEduPolicies

#### <a name="sharedpcconfigurationdisablepowerpolicies"></a>SharedPCConfiguration.DisablePowerPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SetPowerPolicies

#### <a name="sharedpcconfigurationdisablesigninonresume"></a>SharedPCConfiguration.DisableSignInOnResume 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SignInOnResume

#### <a name="sharedpcconfigurationenabled"></a>SharedPCConfiguration.Enabled 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /EnableSharedPCMode

#### <a name="sharedpcconfigurationidletimebeforesleepinseconds"></a>SharedPCConfiguration.IdleTimeBeforeSleepInSeconds 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /InactiveThreshold

#### <a name="sharedpcconfigurationkioskappdisplayname"></a>SharedPCConfiguration.KioskAppDisplayName 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /KioskModeUserTileDisplayText

#### <a name="sharedpcconfigurationkioskappusermodelid"></a>SharedPCConfiguration.KioskAppUserModelId 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /KioskModeAUMID

#### <a name="sharedpcconfigurationlocalstorage"></a>SharedPCConfiguration.LocalStorage 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /RestrictLocalStorage

#### <a name="sharedpcconfigurationmaintenancestarttime"></a>SharedPCConfiguration.MaintenanceStartTime 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /MaintenanceStartTime

#### <a name="sharedpcconfigurationsetaccountmanager"></a>SharedPCConfiguration.SetAccountManager
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /EnableAccountManager

#### <a name="sharedpcconfigurationsetedupolicies"></a>SharedPCConfiguration.SetEduPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SetEduPolicies

#### <a name="sharedpcconfigurationsetpowerpolicies"></a>SharedPCConfiguration.SetPowerPolicies 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SetPowerPolicies

#### <a name="sharedpcconfigurationsigninonresume"></a>SharedPCConfiguration.SignInOnResume 
**CSP**: ./Vendor/MSFT/SharedPC  
**Offset URI**: /SignInOnResume

#### <a name="windows10endpointconfigurationsmartscreenblockoverrideforfiles"></a>Windows10endpointconfiguration.smartScreenBlockOverrideForFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/SmartScreen/PreventOverrideForFilesInShell

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowfilesaveonhost"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowFileSaveOnHost 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: /Settings/SaveFilesToHost

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowpersistence"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPersistence 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/AllowPersistence

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttolocalprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToLocalPrinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttonetworkprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToNetworkPrinters 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttopdf"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToPDF 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttoxps"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToXPS 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowvirtualgpu"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowVirtualGPU 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: /Settings/AllowVirtualGPU

#### <a name="windows10endpointprotectionconfigurationapplicationguardblockclipboardsharing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockClipboardSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Settings/ClipboardSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardblockfiletransfer"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockFileTransfer 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: /Settings/ClipboardFileType

#### <a name="windows10endpointprotectionconfigurationapplicationguardblocknonenterprisecontent"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockNonEnterpriseContent 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: /Settings/BlockNonEnterpriseContent

#### <a name="windows10endpointprotectionconfigurationapplicationguardenabled"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardEnabled 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: /Settings/AllowWindowsDefenderApplicationGuard

#### <a name="windows10endpointprotectionconfigurationapplicationguardforceauditing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardForceAuditing 
**CSP**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Offset URI**: / Audit/AuditApplicationGuard

#### <a name="windows10endpointprotectionconfigurationbitlockerallowstandarduserencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerAllowStandardUserEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /AllowStandardUserEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerdisablewarningforotherdiskencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerDisableWarningForOtherDiskEncryption 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /AllowWarningForOtherDiskEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerenablestoragecardencryptiononmobile"></a>Windows10EndpointProtectionConfiguration.BitLockerEnableStorageCardEncryptionOnMobile 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /RequireStorageCardEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerencryptdevice"></a>Windows10EndpointProtectionConfiguration.BitLockerEncryptDevice 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /RequireDeviceEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerfixeddrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerFixedDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /EncryptionMethodByDriveType, /FixedDrivesRequireEncryption, /FixedDrivesRecoveryOptions

#### <a name="windows10endpointprotectionconfigurationbitlockerremovabledrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerRemovableDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /EncryptionMethodByDriveType, /RemovableDrivesRequireEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockersystemdrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerSystemDrivePolicy 
**CSP**: ./Device/Vendor/MSFT/BitLocker  
**Offset URI**: /EncryptionMethodByDriveType, /SystemDrivesRequireStartupAuthentication, /SystemDrivesMinimumPINLength, /SystemDrivesRecoveryMessage, /SystemDrivesRecoveryOptions

#### <a name="windows10endpointprotectionconfigurationclientconnectionencryptionlevel"></a>windows10endpointprotectionconfiguration.clientConnectionEncryptionLevel 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

#### <a name="windows10endpointprotectionconfigurationconfiguresmbv1clientdriver"></a>windows10endpointprotectionconfiguration.configureSMBV1ClientDriver 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

#### <a name="windows10endpointprotectionconfigurationconnectivitydownloadingofprintdriversoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityDownloadingOfPrintDriversOverHttp 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/DisableDownloadingOfPrintDriversOverHTTP

#### <a name="windows10endpointprotectionconfigurationconnectivityhardeneduncpaths"></a>Windows10EndpointProtectionConfiguration.ConnectivityHardenedUncPaths 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/HardenedUNCPaths

#### <a name="windows10endpointprotectionconfigurationconnectivityinternetdownloadforwebpublishingandonlineorderingwizards"></a>Windows10EndpointProtectionConfiguration.ConnectivityInternetDownloadForWebPublishingAndOnlineOrderingWizards 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/DisableInternetDownloadForWebPublishingAndOnlineOrderingWizards

#### <a name="windows10endpointprotectionconfigurationconnectivityprintingoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityPrintingOverHttp 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/DiablePrintingOverHTTP

#### <a name="windows10endpointprotectionconfigurationcredentialsuienumerateadministrators"></a>Windows10EndpointProtectionConfiguration.CredentialsUIEnumerateAdministrators 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/CredentialsUI/EnumerateAdministrators

#### <a name="windows10endpointprotectionconfigurationdefenderadditionalguardedfolders"></a>Windows10EndpointProtectionConfiguration.DefenderAdditionalGuardedFolders 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/Defender/ControlledFolderAccessProtectedFolders

#### <a name="windows10endpointprotectionconfigurationdefenderadvancedransomewareprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderAdvancedRansomewareProtectionType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderattacksurfacereductionexcludedpaths"></a>Windows10EndpointProtectionConfiguration.DefenderAttackSurfaceReductionExcludedPaths 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionOnlyExclusions

#### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecution"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecution 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowEmailScanning

#### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecutionType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxml"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXml 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/ExploitGuard/ExploitProtectionSettings

#### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxmlfilename"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXmlFileName 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/ExploitGuard/ExploitProtectionSettings

#### <a name="windows10endpointprotectionconfigurationdefenderguardedfoldersallowedapppaths"></a>Windows10EndpointProtectionConfiguration.DefenderGuardedFoldersAllowedAppPaths 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/Defender/ControlledFolderAccessAllowedApplications

#### <a name="windows10endpointprotectionconfigurationdefenderguardmyfolderstype"></a>Windows10EndpointProtectionConfiguration.DefenderGuardMyFoldersType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/EnableControlledFolderAccess

#### <a name="windows10endpointprotectionconfigurationdefendernetworkprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderNetworkProtectionType 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/Defender/EnableNetworkProtection

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunch"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunch 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunchtype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunchType
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocess"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcessType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjection"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjectionType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType 

#### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32imports"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32Imports 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32importstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32ImportsType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderpreventcredentialstealingtype"></a>Windows10EndpointProtectionConfiguration.DefenderPreventCredentialStealingType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderprocesscreation"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderprocesscreationtype"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreationType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderprotectagainstpotentiallyunwantedapplications"></a>Windows10EndpointProtectionConfiguration.DefenderProtectAgainstPotentiallyUnwantedApplications 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/TurnOnWindowsDefenderProtectionAgainstPotentiallyUnwantedApplications

#### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecution"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecution 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecutionType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocode"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocodetype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCodeType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterblockexploitprotectionoverride"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterBlockExploitProtectionOverride 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableaccountui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAccountUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableAccountProtectionUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableappbrowserui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAppBrowserUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableAppBrowserUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablefamilyui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableFamilyUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableFamilyUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablehealthui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableHealthUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableHealthUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablenetworkui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableNetworkUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableNetworkUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablesecurebootui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableSecureBootUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/HideSecureBoot

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisabletroubleshootingui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableTroubleshootingUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/HideTPMTroubleshooting

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablevirusui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableVirusUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/DisableVirusUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpemail"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpEmail 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/Email

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpphone"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpPhone 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/Phone

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpurl"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpURL 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/URL

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenteritcontactdisplay"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterITContactDisplay 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /WindowsDefenderSecurityCenter/EnableCustomizedToasts, /WindowsDefenderSecurityCenter/EnableInAppCustomization

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenternotificationsfromapp"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterNotificationsFromApp 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/HideWindowsSecurityNotificationAreaControl

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterorganizationdisplayname"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterOrganizationDisplayName 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsDefenderSecurityCenter/CompanyName

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutable"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutable 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutabletype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutableType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocess"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcessType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AttackSurfaceReductionRules (CSP/Konfiguration erfordert Graph-Eigenschaften: windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdeviceguardenablesecurebootwithdma"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableSecureBootWithDMA 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceGuard/RequirePlatformSecurityFeatures

#### <a name="windows10endpointprotectionconfigurationdeviceguardenablevirtualizationbasedsecurity"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableVirtualizationBasedSecurity 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/DeviceGuard/EnableVirtualizationBasedSecurity

#### <a name="windows10endpointprotectionconfigurationdeviceguardlaunchsystemguard"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLaunchSystemGuard 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceGuard/ConfigureSystemGuardLaunch

#### <a name="windows10endpointprotectionconfigurationdeviceguardlocalsystemauthoritycredentialguardsettings"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLocalSystemAuthorityCredentialGuardSettings 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceGuard/LsaCfgFlags

#### <a name="windows10endpointprotectionconfigurationdmaguarddeviceenumerationpolicy"></a>Windows10EndpointProtectionConfiguration.DmaGuardDeviceEnumerationPolicy 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DmaGuard/DeviceEnumerationPolicy

#### <a name="windows10endpointprotectionconfigurationeventlogserviceapplicationlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceApplicationLogMaximumFileSizeInKb 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/EventLogService/SpecifyMaximumFileSizeApplicationLog

#### <a name="windows10endpointprotectionconfigurationeventlogservicesecuritylogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSecurityLogMaximumFileSizeInKb 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/EventLogService/SpecifyMaximumFileSizeSecurityLog

#### <a name="windows10endpointprotectionconfigurationeventlogservicesystemlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSystemLogMaximumFileSizeInKb 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/EventLogService/SpecifyMaximumFileSizeSystemLog

#### <a name="windows10endpointprotectionconfigurationexplorerdataexecutionprevention"></a>Windows10EndpointProtectionConfiguration.ExplorerDataExecutionPrevention 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/FileExplorer/TurnOffDataExecutionPreventionForExplorer

#### <a name="windows10endpointprotectionconfigurationexplorerheapterminationoncorruption"></a>Windows10EndpointProtectionConfiguration.ExplorerHeapTerminationOnCorruption 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/FileExplorer/TurnOffHeapTerminationOnCorruption

#### <a name="windows10endpointprotectionconfigurationfirewallblockstatefulftp"></a>Windows10EndpointProtectionConfiguration.FirewallBlockStatefulFTP 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/DisableStatefulFtp

#### <a name="windows10endpointprotectionconfigurationfirewallcertificaterevocationlistcheckmethod"></a>Windows10EndpointProtectionConfiguration.FirewallCertificateRevocationListCheckMethod 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/CRLcheck

#### <a name="windows10endpointprotectionconfigurationfirewallidletimeoutforsecurityassociationinseconds"></a>Windows10EndpointProtectionConfiguration.FirewallIdleTimeoutForSecurityAssociationInSeconds 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/SaIdleTime

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowdhcp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowDHCP 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowicmp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowICMP 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowneighbordiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowNeighborDiscovery 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowrouterdiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowRouterDiscovery 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallmergekeyingmodulesettings"></a>Windows10EndpointProtectionConfiguration.FirewallMergeKeyingModuleSettings 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/OpportunisticallyMatchAuthSetPerKM

#### <a name="windows10endpointprotectionconfigurationfirewallpacketqueueingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPacketQueueingMethod 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/EnablePacketQueue

#### <a name="windows10endpointprotectionconfigurationfirewallpresharedkeyencodingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPreSharedKeyEncodingMethod 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/Global/PresharedKeyEncoding

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomain"></a>Windows10EndpointProtectionConfiguration.FirewallProfileDomain 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /EnableFirewall, /DisableStealthMode, / geschützte, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/DomainProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/DomainProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/DomainProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomainoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.outboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/DomainProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivate"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePrivate 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /EnableFirewall, /DisableStealthMode, / geschützte, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivatefirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.firewallEnabled 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PrivateProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PrivateProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundNotificationsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PrivateProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.outboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PrivateProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublic"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePublic 
**CSP**: ./Vendor/MSFT/Firewall  
**Offset URI**: /EnableFirewall, /DisableStealthMode, / geschützte, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicconnectionsecurityrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.connectionSecurityRulesFromGroupPolicyMerged 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicfirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.firewallEnabled 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundNotificationsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.outboundConnectionsBlocked 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicpolicyrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.policyRulesFromGroupPolicyMerged 
**CSP**: ./Device/Vendor/MSFT/Firewall  
**Offset URI**: /MdmStore/PublicProfile/AllowLocalPolicyMerge

#### <a name="windows10endpointprotectionconfigurationlanmanagerauthenticationlevel"></a>Windows10EndpointProtectionConfiguration.LanManagerAuthenticationLevel 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_LANManagerAuthenticationLevel

#### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationdisableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationDisableInsecureGuestLogons 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LanmanWorkstation/EnableInsecureGuestLogons

#### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationenableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationEnableInsecureGuestLogons 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LanmanWorkstation/EnableInsecureGuestLogons

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratoraccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorAccountName 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_RenameAdministratorAccount

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratorelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorElevationPromptBehavior
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForAdministrators

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowanonymousenumerationofsamaccountsandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowpku2uauthenticationrequests"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowPKU2UAuthenticationRequests 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_AllowPKU2UAuthenticationRequests

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanager"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanagerhelperbool"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowsystemtobeshutdownwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Shutdown\_AllowSystemToBeShutDownWithoutHavingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationElevation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_AllowUIAccessApplicationsToPromptForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationsforsecurelocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationsForSecureLocations 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowundockwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUndockWithoutHavingToLogon 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Devices\_AllowUndockWithoutHavingToLogon

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockmicrosoftaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockMicrosoftAccounts 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_BlockMicrosoftAccounts

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremotelogonwithblankpassword"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteLogonWithBlankPassword 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremoteopticaldriveaccess"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteOpticalDriveAccess 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Devices\_RestrictCDROMAccessToLocallyLoggedOnUserOnly

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockusersinstallingprinterdrivers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockUsersInstallingPrinterDrivers 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Devices\_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclearvirtualmemorypagefile"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClearVirtualMemoryPageFile 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Shutdown\_ClearVirtualMemoryPageFile

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientDigitallySignCommunicationsAlways 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsAlways

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientsendunencryptedpasswordtothirdpartysmbservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_SendUnencryptedPasswordToThirdPartySMBServers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdetectapplicationinstallationsandpromptforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_DetectApplicationInstallationsAndPromptForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableAdministratorAccount 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableclientdigitallysigncommunicationsifserveragrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsIfServerAgrees

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableGuestAccount 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsAlways

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsifclientagrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsIfClientAgrees

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotallowanonymousenumerationofsamaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSAMAccounts

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotrequirectrlaltdel"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotRequireCtrlAltDel 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotRequireCTRLALTDEL

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotstorelanmanagerhashvalueonnextpasswordchange"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_DoNotStoreLANManagerHashValueOnNextPasswordChange

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableAdministratorAccount 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableGuestAccount 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsformatandejectofremovablemediaalloweduser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Devices\_AllowedToFormatAndEjectRemovableMedia

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsguestaccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsGuestAccountName 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_RenameGuestAccount

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshidelastsignedinuser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideLastSignedInUser 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayLastSignedIn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshideusernameatsignin"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideUsernameAtSignIn 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayUsernameAtSignIn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationdisplayedonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationDisplayedOnLockScreen 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationshownonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationShownOnLockScreen 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetext"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageText 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTextForUsersAttemptingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetitle"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageTitle 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTitleForUsersAttemptingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimit"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimit 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimitinminutes"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimitInMinutes 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedclients"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedClients

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedServers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsonlyelevatesignedexecutables"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsOnlyElevateSignedExecutables 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateExecutableFilesThatAreSignedAndValidated

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsrestrictanonymousaccesstonamedpipesandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictAnonymousAccessToNamedPipesAndShares

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionssmartcardremovalbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSmartCardRemovalBehavior 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_SmartCardRemovalBehavior

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsstandarduserelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsStandardUserElevationPromptBehavior 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForStandardUsers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsswitchtosecuredesktopwhenpromptingforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_SwitchToTheSecureDesktopWhenPromptingForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmode"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_UseAdminApprovalMode

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmodeforadministrators"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalModeForAdministrators 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_RunAllAdministratorsInAdminApprovalMode

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsvirtualizefileandregistrywritefailurestoperuserlocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations

#### <a name="windows10endpointprotectionconfigurationnetworkicmpredirectsoverrideospfgeneratedroutes"></a>Windows10EndpointProtectionConfiguration.NetworkIcmpRedirectsOverrideOspfGeneratedRoutes 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSLegacy/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes

#### <a name="windows10endpointprotectionconfigurationnetworkignorenetbiosnamereleaserequestsexceptfromwinsservers"></a>Windows10EndpointProtectionConfiguration.NetworkIgnoreNetBiosNameReleaseRequestsExceptFromWinsServers 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSLegacy/AllowTheComputerToIgnoreNetBIOSNameReleaseRequestsExceptFromWINSServers

#### <a name="windows10endpointprotectionconfigurationnetworkipsourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpSourceRoutingProtectionLevel 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSLegacy/IPSourceRoutingProtectionLevel

#### <a name="windows10endpointprotectionconfigurationnetworkipv6sourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpV6SourceRoutingProtectionLevel 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSLegacy/IPv6SourceRoutingProtectionLevel

#### <a name="windows10endpointprotectionconfigurationpasswordpinlogon"></a>Windows10EndpointProtectionConfiguration.PasswordPinLogOn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/CredentialProviders/AllowPINLogon

#### <a name="windows10endpointprotectionconfigurationpowershellshellscriptblocklogging"></a>Windows10EndpointProtectionConfiguration.PowerShellShellScriptBlockLogging 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsPowerShell/TurnOnPowerShellScriptBlockLogging

#### <a name="windows10endpointprotectionconfigurationremoteassistancesolicitedsetting"></a>Windows10EndpointProtectionConfiguration.RemoteAssistanceSolicitedSetting 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/HardenedUNCPaths

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicesclientconnectionencryptionlevel"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesClientConnectionEncryptionLevel 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicesdriveredirection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesDriveRedirection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/DoNotAllowDriveRedirection

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicespasswordsaving"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPasswordSaving 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/DoNotAllowPasswordSaving

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicespromptforpassworduponconnection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPromptForPasswordUponConnection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/PromptForPasswordUponConnection

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicessecurerpccommunication"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesSecureRpcCommunication 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteDesktopServices/RequireSecureRPCCommunication

#### <a name="windows10endpointprotectionconfigurationremotehostdelegationofnonexportablecredentials"></a>Windows10EndpointProtectionConfiguration.RemoteHostDelegationOfNonExportableCredentials 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/CredentialsDelegation/RemoteHostAllowsDelegationOfNonExportableCredentials

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientbasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientBasicAuthentication 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/AllowBasicAuthentication\_Client

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientdigestauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientDigestAuthentication 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/DisallowDigestAuthentication

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientUnencryptedTraffic 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/AllowUnencryptedTraffic\_Client

#### <a name="windows10endpointprotectionconfigurationremotemanagementservicebasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceBasicAuthentication 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/AllowBasicAuthentication\_Service

#### <a name="windows10endpointprotectionconfigurationremotemanagementservicestoringrunascredentials"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceStoringRunAsCredentials 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/DisallowStoringOfRunAsCredentials

#### <a name="windows10endpointprotectionconfigurationremotemanagementserviceunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceUnencryptedTraffic 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteManagement/AllowUnencryptedTraffic\_Service

#### <a name="windows10endpointprotectionconfigurationrpcunauthenticatedclientoptions"></a>Windows10EndpointProtectionConfiguration.RpcUnauthenticatedClientOptions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteProcedureCall/RestrictUnauthenticatedRPCClients

#### <a name="windows10endpointprotectionconfigurationsecurityguideapplyuacrestrictionstolocalaccountsonnetworklogon"></a>Windows10EndpointProtectionConfiguration.SecurityGuideApplyUacRestrictionsToLocalAccountsOnNetworkLogon 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/ApplyUACRestrictionsToLocalAccountsOnNetworkLogon

#### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1clientdriverstartconfiguration"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1ClientDriverStartConfiguration 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

#### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1server"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1Server 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/ConfigureSMBV1Server

#### <a name="windows10endpointprotectionconfigurationsecurityguidestructuredexceptionhandlingoverwriteprotection"></a>Windows10EndpointProtectionConfiguration.SecurityGuideStructuredExceptionHandlingOverwriteProtection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/EnableStructuredExceptionHandlingOverwriteProtection

#### <a name="windows10endpointprotectionconfigurationsecurityguidewdigestauthentication"></a>Windows10EndpointProtectionConfiguration.SecurityGuideWDigestAuthentication 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/MSSecurityGuide/WDigestAuthentication

#### <a name="windows10endpointprotectionconfigurationsmartscreenblockoverrideforfiles"></a>Windows10EndpointProtectionConfiguration.SmartScreenBlockOverrideForFiles 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/DeviceGuard/RequirePlatformSecurityFeatures

#### <a name="windows10endpointprotectionconfigurationsmartscreenenableinshell"></a>Windows10EndpointProtectionConfiguration.SmartScreenEnableInShell 
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/SmartScreen/EnableSmartScreenInShell

#### <a name="windows10endpointprotectionconfigurationsolicitedremoteassistance"></a>windows10endpointprotectionconfiguration.solicitedRemoteAssistance 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/RemoteAssistance/SolicitedRemoteAssistance

#### <a name="windows10endpointprotectionconfigurationuserrightsaccesscredentialmanagerastrustedcaller"></a>Windows10EndpointProtectionConfiguration.UserRightsAccessCredentialManagerAsTrustedCaller 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/AccessCredentialManagerAsTrustedCaller

#### <a name="windows10endpointprotectionconfigurationuserrightsaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsAccessFromNetwork 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/AccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsactaspartoftheoperatingsystem"></a>Windows10EndpointProtectionConfiguration.userRightsActAsPartOfTheOperatingSystem 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ActAsPartOfTheOperatingSystem

#### <a name="windows10endpointprotectionconfigurationuserrightsallowaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsAllowAccessFromNetwork 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/AccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsbackupdata"></a>Windows10EndpointProtectionConfiguration.UserRightsBackupData 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/BackupFilesAndDirectories

#### <a name="windows10endpointprotectionconfigurationuserrightsblockaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsBlockAccessFromNetwork 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/DenyAccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightschangesystemtime"></a>Windows10EndpointProtectionConfiguration.UserRightsChangeSystemTime 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ChangeSystemTime

#### <a name="windows10endpointprotectionconfigurationuserrightscreateglobalobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateGlobalObjects 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/CreateGlobalObjects

#### <a name="windows10endpointprotectionconfigurationuserrightscreatepagefile"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePageFile 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/CreatePageFile

#### <a name="windows10endpointprotectionconfigurationuserrightscreatepermanentsharedobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePermanentSharedObjects 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/CreatePermanentSharedObjects

#### <a name="windows10endpointprotectionconfigurationuserrightscreatesymboliclinks"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateSymbolicLinks 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/CreateSymbolicLinks

#### <a name="windows10endpointprotectionconfigurationuserrightscreatetoken"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateToken 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/CreateToken

#### <a name="windows10endpointprotectionconfigurationuserrightsdebugprograms"></a>Windows10EndpointProtectionConfiguration.UserRightsDebugPrograms 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/DebugPrograms

#### <a name="windows10endpointprotectionconfigurationuserrightsdelegation"></a>Windows10EndpointProtectionConfiguration.UserRightsDelegation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/EnableDelegation

#### <a name="windows10endpointprotectionconfigurationuserrightsdenyaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsDenyAccessFromNetwork 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/DenyAccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsgeneratesecurityaudits"></a>Windows10EndpointProtectionConfiguration.UserRightsGenerateSecurityAudits 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/GenerateSecurityAudits

#### <a name="windows10endpointprotectionconfigurationuserrightsimpersonateclient"></a>Windows10EndpointProtectionConfiguration.UserRightsImpersonateClient 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ImpersonateClient

#### <a name="windows10endpointprotectionconfigurationuserrightsincreaseschedulingpriority"></a>Windows10EndpointProtectionConfiguration.UserRightsIncreaseSchedulingPriority 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/IncreaseSchedulingPriority

#### <a name="windows10endpointprotectionconfigurationuserrightsloadunloaddrivers"></a>Windows10EndpointProtectionConfiguration.UserRightsLoadUnloadDrivers 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/LoadUnloadDeviceDrivers

#### <a name="windows10endpointprotectionconfigurationuserrightslocallogon"></a>Windows10EndpointProtectionConfiguration.UserRightsLocalLogOn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/AllowLocalLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightslockmemory"></a>Windows10EndpointProtectionConfiguration.UserRightsLockMemory 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/LockMemory

#### <a name="windows10endpointprotectionconfigurationuserrightsmanageauditingandsecuritylogs"></a>Windows10EndpointProtectionConfiguration.UserRightsManageAuditingAndSecurityLogs 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ManageAuditingAndSecurityLog

#### <a name="windows10endpointprotectionconfigurationuserrightsmanagevolumes"></a>Windows10EndpointProtectionConfiguration.UserRightsManageVolumes 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ManageVolume

#### <a name="windows10endpointprotectionconfigurationuserrightsmodifyfirmwareenvironment"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyFirmwareEnvironment 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ModifyFirmwareEnvironment

#### <a name="windows10endpointprotectionconfigurationuserrightsmodifyobjectlabels"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyObjectLabels 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ModifyObjectLabel

#### <a name="windows10endpointprotectionconfigurationuserrightsprofilesingleprocess"></a>Windows10EndpointProtectionConfiguration.UserRightsProfileSingleProcess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/ProfileSingleProcess

#### <a name="windows10endpointprotectionconfigurationuserrightsregisterprocessasservice"></a>Windows10EndpointProtectionConfiguration.UserRightsRegisterProcessAsService 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/DenyLocalLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightsremotedesktopserviceslogon"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteDesktopServicesLogOn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/DenyRemoteDesktopServicesLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightsremoteshutdown"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteShutdown 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/RemoteShutdown

#### <a name="windows10endpointprotectionconfigurationuserrightsrestoredata"></a>Windows10EndpointProtectionConfiguration.UserRightsRestoreData 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/RestoreFilesAndDirectories

#### <a name="windows10endpointprotectionconfigurationuserrightstakeownership"></a>Windows10EndpointProtectionConfiguration.UserRightsTakeOwnership 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/UserRights/TakeOwnership

#### <a name="windows10endpointprotectionconfigurationwindowsconnectionmanagerconnectiontonondomainnetworks"></a>Windows10EndpointProtectionConfiguration.WindowsConnectionManagerConnectionToNonDomainNetworks 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsConnectionManager/ProhitConnectionToNonDomainNetworksWhenConnectedToDomainAuthenticatedNetwork

#### <a name="windows10endpointprotectionconfigurationwindowslogonsigninlastinteractiveuseraftersysteminitiatedrestart"></a>Windows10EndpointProtectionConfiguration.WindowsLogOnSignInLastInteractiveUserAfterSystemInitiatedRestart 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsLogon/SignInLastInteractiveUserAutomaticallyAfterASystemInitiatedRestart

#### <a name="windows10endpointprotectionconfigurationxboxservicesaccessorymanagementservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesAccessoryManagementServiceStartupMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxservicesenablexboxgamesavetask"></a>Windows10EndpointProtectionConfiguration.XboxServicesEnableXboxGameSaveTask 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/TaskScheduler/EnableXboxGameSaveTask

#### <a name="windows10endpointprotectionconfigurationxboxservicesliveauthmanagerservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveAuthManagerServiceStartupMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxserviceslivegamesaveservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveGameSaveServiceStartupMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/SystemServices/XboxServicesLiveGameSaveServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxserviceslivenetworkingservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveNetworkingServiceStartupMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode

#### <a name="windows10enterprisemodernappmanagementconfigurationuninstallbuiltinapps"></a>Windows10EnterpriseModernAppManagementConfiguration.UninstallBuiltInApps
**CSP**: N/v-Graph-API-Aufruf nur **Offset URI**: Nur n/v-Graph-API-Aufruf

#### <a name="windows10generalconfigurationaccountsblockaddingnonmicrosoftaccountemail"></a>Windows10GeneralConfiguration.AccountsBlockAddingNonMicrosoftAccountEmail 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Accounts/AllowAddingNonMicrosoftAccountsManually

#### <a name="windows10generalconfigurationantitheftmodeblocked"></a>Windows10GeneralConfiguration.AntiTheftModeBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/AntiTheftMode

#### <a name="windows10generalconfigurationappmanagementmsiallowusercontroloverinstall"></a>Windows10GeneralConfiguration.AppManagementMSIAllowUserControlOverInstall 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/MSIAllowUserControlOverInstall

#### <a name="windows10generalconfigurationappmanagementmsialwaysinstallwithelevatedprivileges"></a>Windows10GeneralConfiguration.AppManagementMSIAlwaysInstallWithElevatedPrivileges 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges

#### <a name="windows10generalconfigurationappsallowtrustedappssideloading"></a>Windows10GeneralConfiguration.AppsAllowTrustedAppsSideloading 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowAllTrustedApps

#### <a name="windows10generalconfigurationappsblockwindowsstoreoriginatedapps"></a>Windows10GeneralConfiguration.AppsBlockWindowsStoreOriginatedApps 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/DisableStoreOriginatedApps

#### <a name="windows10generalconfigurationappsmicrosoftaccountsoptional"></a>Windows10GeneralConfiguration.AppsMicrosoftAccountsOptional 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/AppRuntime/AllowMicrosoftAccountsToBeOptional

#### <a name="windows10generalconfigurationassignedaccessmultimodeprofiles"></a>Windows10GeneralConfiguration.AssignedAccessMultiModeProfiles 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**Offset URI**: / Configuration

#### <a name="windows10generalconfigurationassignedaccesssinglemodeappusermodelid"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeAppUserModelId 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**Offset URI**: / Configuration

#### <a name="windows10generalconfigurationassignedaccesssinglemodeusername"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeUserName 
**CSP**: ./Device/Vendor/MSFT/AssignedAccess  
**Offset URI**: / Configuration

#### <a name="windows10generalconfigurationauthenticationallowfidodevice"></a>Windows10GeneralConfiguration.AuthenticationAllowFIDODevice 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Authentication/AllowFidoDeviceSignon

#### <a name="windows10generalconfigurationauthenticationallowsecondarydevice"></a>Windows10GeneralConfiguration.AuthenticationAllowSecondaryDevice 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Authentication/AllowSecondaryAuthenticationDevice

#### <a name="windows10generalconfigurationauthenticationpreferredazureadtenantdomainname"></a>Windows10GeneralConfiguration.AuthenticationPreferredAzureADTenantDomainName 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Authentication/PreferredAadTenantDomainName

#### <a name="windows10generalconfigurationauthenticationwebsignin"></a>Windows10GeneralConfiguration.AuthenticationWebSignIn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Authentication/EnableWebSignIn

#### <a name="windows10generalconfigurationautoplaydefaultautorunbehavior"></a>Windows10GeneralConfiguration.AutoPlayDefaultAutoRunBehavior 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Autoplay/SetDefaultAutoRunBehavior

#### <a name="windows10generalconfigurationautoplayfornonvolumedevices"></a>Windows10GeneralConfiguration.AutoPlayForNonVolumeDevices 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Autoplay/DisallowAutoplayForNonVolumeDevices

#### <a name="windows10generalconfigurationautoplaymode"></a>Windows10GeneralConfiguration.AutoPlayMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Autoplay/TurnOffAutoPlay

#### <a name="windows10generalconfigurationbluetoothallowedservices"></a>Windows10GeneralConfiguration.BluetoothAllowedServices 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/ServicesAllowedList

#### <a name="windows10generalconfigurationbluetoothblockadvertising"></a>Windows10GeneralConfiguration.BluetoothBlockAdvertising 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/AllowAdvertising

#### <a name="windows10generalconfigurationbluetoothblockdiscoverablemode"></a>Windows10GeneralConfiguration.BluetoothBlockDiscoverableMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/AllowDiscoverableMode

#### <a name="windows10generalconfigurationbluetoothblocked"></a>Windows10GeneralConfiguration.BluetoothBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowBluetooth

#### <a name="windows10generalconfigurationbluetoothblockprepairing"></a>Windows10GeneralConfiguration.BluetoothBlockPrePairing 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/AllowPrepairing

#### <a name="windows10generalconfigurationbluetoothblockpromptedproximalconnections"></a>Windows10GeneralConfiguration.BluetoothBlockPromptedProximalConnections 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/AllowPromptedProximalConnections

#### <a name="windows10generalconfigurationbluetoothdevicename"></a>Windows10GeneralConfiguration.BluetoothDeviceName 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Bluetooth/LocalDeviceName

#### <a name="windows10generalconfigurationbootstartdriverinitialization"></a>windows10generalconfiguration.bootStartDriverInitialization 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/System/BootStartDriverInitialization

#### <a name="windows10generalconfigurationcamerablocked"></a>Windows10GeneralConfiguration.CameraBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Camera/AllowCamera

#### <a name="windows10generalconfigurationcellularblockdatawhenroaming"></a>Windows10GeneralConfiguration.CellularBlockDataWhenRoaming 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowCellularDataRoaming

#### <a name="windows10generalconfigurationcellularblockvpn"></a>Windows10GeneralConfiguration.CellularBlockVpn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowVPNOverCellular

#### <a name="windows10generalconfigurationcellularblockvpnwhenroaming"></a>Windows10GeneralConfiguration.CellularBlockVpnWhenRoaming 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowVPNRoamingOverCellular

#### <a name="windows10generalconfigurationcellulardata"></a>Windows10GeneralConfiguration.CellularData 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowCellularData

#### <a name="windows10generalconfigurationcertificatesblockmanualrootcertificateinstallation"></a>Windows10GeneralConfiguration.CertificatesBlockManualRootCertificateInstallation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/AllowManualRootCertificateInstallation

#### <a name="windows10generalconfigurationconnecteddevicesserviceblocked"></a>Windows10GeneralConfiguration.ConnectedDevicesServiceBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowConnectedDevices

#### <a name="windows10generalconfigurationcopypasteblocked"></a>Windows10GeneralConfiguration.CopyPasteBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowCopyPaste

#### <a name="windows10generalconfigurationcortanablocked"></a>Windows10GeneralConfiguration.CortanaBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/AboveLock/AllowCortanaAboveLock

#### <a name="windows10generalconfigurationcryptographyallowfipsalgorithmpolicy"></a>Windows10GeneralConfiguration.CryptographyAllowFipsAlgorithmPolicy 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Cryptography/AllowFipsAlgorithmPolicy

#### <a name="windows10generalconfigurationdataprotectionblockdirectmemoryaccess"></a>Windows10GeneralConfiguration.DataProtectionBlockDirectMemoryAccess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DataProtection/AllowDirectMemoryAccess

#### <a name="windows10generalconfigurationdefenderblockenduseraccess"></a>Windows10GeneralConfiguration.DefenderBlockEndUserAccess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowUserUIAccess

#### <a name="windows10generalconfigurationdefenderblockonaccessprotection"></a>Windows10GeneralConfiguration.DefenderBlockOnAccessProtection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowOnAccessProtection

#### <a name="windows10generalconfigurationdefendercloudblocklevel"></a>Windows10GeneralConfiguration.DefenderCloudBlockLevel 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/CloudBlockLevel

#### <a name="windows10generalconfigurationdefendercloudextendedtimeout"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeout 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/CloudExtendedTimeout

#### <a name="windows10generalconfigurationdefendercloudextendedtimeoutinseconds"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeoutInSeconds 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/CloudExtendedTimeout

#### <a name="windows10generalconfigurationdefenderdaysbeforedeletingquarantinedmalware"></a>Windows10GeneralConfiguration.DefenderDaysBeforeDeletingQuarantinedMalware 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/DaysToRetainCleanedMalware

#### <a name="windows10generalconfigurationdefenderdetectedmalwareactions"></a>Windows10GeneralConfiguration.DefenderDetectedMalwareActions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ThreatSeverityDefaultAction

#### <a name="windows10generalconfigurationdefenderfileextensionstoexclude"></a>Windows10GeneralConfiguration.DefenderFileExtensionsToExclude 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ExcludedExtensions

#### <a name="windows10generalconfigurationdefenderfilesandfolderstoexclude"></a>Windows10GeneralConfiguration.DefenderFilesAndFoldersToExclude 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ExcludedPaths

#### <a name="windows10generalconfigurationdefendermonitorfileactivity"></a>Windows10GeneralConfiguration.DefenderMonitorFileActivity 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowRealtimeMonitoring

#### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappaction"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppAction 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/PUAProtection

#### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappactionsetting"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppActionSetting 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/PUAProtection

#### <a name="windows10generalconfigurationdefenderprocessestoexclude"></a>Windows10GeneralConfiguration.DefenderProcessesToExclude 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ExcludedProcesses

#### <a name="windows10generalconfigurationdefenderpromptforsamplesubmission"></a>Windows10GeneralConfiguration.DefenderPromptForSampleSubmission 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/SubmitSamplesConsent

#### <a name="windows10generalconfigurationdefenderrequirebehaviormonitoring"></a>Windows10GeneralConfiguration.DefenderRequireBehaviorMonitoring 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowBehaviorMonitoring

#### <a name="windows10generalconfigurationdefenderrequirecloudprotection"></a>Windows10GeneralConfiguration.DefenderRequireCloudProtection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowCloudProtection

#### <a name="windows10generalconfigurationdefenderrequirenetworkinspectionsystem"></a>Windows10GeneralConfiguration.DefenderRequireNetworkInspectionSystem 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowIntrusionPreventionSystem

#### <a name="windows10generalconfigurationdefenderrequirerealtimemonitoring"></a>Windows10GeneralConfiguration.DefenderRequireRealTimeMonitoring 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowRealtimeMonitoring

#### <a name="windows10generalconfigurationdefenderscanarchivefiles"></a>Windows10GeneralConfiguration.DefenderScanArchiveFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowArchiveScanning

#### <a name="windows10generalconfigurationdefenderscandownloads"></a>Windows10GeneralConfiguration.DefenderScanDownloads 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowIOAVProtection

#### <a name="windows10generalconfigurationdefenderscanincomingmail"></a>Windows10GeneralConfiguration.DefenderScanIncomingMail 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowScanningNetworkFiles

#### <a name="windows10generalconfigurationdefenderscanmappednetworkdrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanMappedNetworkDrivesDuringFullScan 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowFullScanOnMappedNetworkDrives

#### <a name="windows10generalconfigurationdefenderscanmaxcpu"></a>Windows10GeneralConfiguration.DefenderScanMaxCpu 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AvgCPULoadFactor

#### <a name="windows10generalconfigurationdefenderscannetworkfiles"></a>Windows10GeneralConfiguration.DefenderScanNetworkFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowScanningNetworkFiles

#### <a name="windows10generalconfigurationdefenderscanremovabledrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanRemovableDrivesDuringFullScan 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowFullScanRemovableDriveScanning

#### <a name="windows10generalconfigurationdefenderscanscriptsloadedininternetexplorer"></a>Windows10GeneralConfiguration.DefenderScanScriptsLoadedInInternetExplorer 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/AllowScriptScanning

#### <a name="windows10generalconfigurationdefenderscantype"></a>Windows10GeneralConfiguration.DefenderScanType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ScanParameter

#### <a name="windows10generalconfigurationdefenderscheduledquickscantime"></a>Windows10GeneralConfiguration.DefenderScheduledQuickScanTime 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ScheduleQuickScanTime

#### <a name="windows10generalconfigurationdefenderscheduledscantime"></a>Windows10GeneralConfiguration.DefenderScheduledScanTime 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ScheduleScanTime

#### <a name="windows10generalconfigurationdefenderschedulescanday"></a>Windows10GeneralConfiguration.DefenderScheduleScanDay 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ScheduleScanDay

#### <a name="windows10generalconfigurationdefendersignatureupdateintervalinhours"></a>Windows10GeneralConfiguration.DefenderSignatureUpdateIntervalInHours 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/SignatureUpdateInterval

#### <a name="windows10generalconfigurationdefendersubmitsamplesconsenttype"></a>Windows10GeneralConfiguration.DefenderSubmitSamplesConsentType 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/SubmitSamplesConsent

#### <a name="windows10generalconfigurationdefendersystemscanschedule"></a>Windows10GeneralConfiguration.DefenderSystemScanSchedule 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Defender/ScheduleScanDay

#### <a name="windows10generalconfigurationdeveloperunlocksetting"></a>Windows10GeneralConfiguration.DeveloperUnlockSetting 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowDeveloperUnlock

#### <a name="windows10generalconfigurationdevicemanagementblockfactoryresetonmobile"></a>Windows10GeneralConfiguration.DeviceManagementBlockFactoryResetOnMobile 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/System/AllowUserToResetPhone

#### <a name="windows10generalconfigurationdevicemanagementblockmanualunenroll"></a>Windows10GeneralConfiguration.DeviceManagementBlockManualUnenroll 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowManualMDMUnenrollment

#### <a name="windows10generalconfigurationdiagnosticsdatasubmissionmode"></a>Windows10GeneralConfiguration.DiagnosticsDataSubmissionMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/AllowTelemetry

#### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedoff"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOff 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Display/TurnOffGdiDPIScalingForApps

#### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedon"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Display/TurnOnGdiDPIScalingForApps

#### <a name="windows10generalconfigurationedgeallowstartpagesmodification"></a>Windows10GeneralConfiguration.EdgeAllowStartPagesModification 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/HomePages

#### <a name="windows10generalconfigurationedgeblockaccesstoaboutflags"></a>Windows10GeneralConfiguration.EdgeBlockAccessToAboutFlags 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventAccessToAboutFlagsInMicrosoftEdge

#### <a name="windows10generalconfigurationedgeblockaddressbardropdown"></a>Windows10GeneralConfiguration.EdgeBlockAddressBarDropdown 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowAddressBarDropdown

#### <a name="windows10generalconfigurationedgeblockautofill"></a>Windows10GeneralConfiguration.EdgeBlockAutofill 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowAutofill

#### <a name="windows10generalconfigurationedgeblockcompatibilitylist"></a>Windows10GeneralConfiguration.EdgeBlockCompatibilityList 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowMicrosoftCompatibilityList

#### <a name="windows10generalconfigurationedgeblockdevelopertools"></a>Windows10GeneralConfiguration.EdgeBlockDeveloperTools 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowDeveloperTools

#### <a name="windows10generalconfigurationedgeblocked"></a>Windows10GeneralConfiguration.EdgeBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowBrowser

#### <a name="windows10generalconfigurationedgeblockeditfavorites"></a>Windows10GeneralConfiguration.EdgeBlockEditFavorites 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/LockdownFavorites

#### <a name="windows10generalconfigurationedgeblockextensions"></a>Windows10GeneralConfiguration.EdgeBlockExtensions 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowExtensions

#### <a name="windows10generalconfigurationedgeblockfullscreenmode"></a>Windows10GeneralConfiguration.EdgeBlockFullScreenMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowFullScreenMode

#### <a name="windows10generalconfigurationedgeblockinprivatebrowsing"></a>Windows10GeneralConfiguration.EdgeBlockInPrivateBrowsing 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowInPrivate

#### <a name="windows10generalconfigurationedgeblocklivetiledatacollection"></a>Windows10GeneralConfiguration.EdgeBlockLiveTileDataCollection 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventLiveTileDataCollection

#### <a name="windows10generalconfigurationedgeblockpasswordmanager"></a>Windows10GeneralConfiguration.EdgeBlockPasswordManager 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowPasswordManager

#### <a name="windows10generalconfigurationedgeblockpopups"></a>Windows10GeneralConfiguration.EdgeBlockPopups 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowPopups

#### <a name="windows10generalconfigurationedgeblockprelaunch"></a>Windows10GeneralConfiguration.EdgeBlockPrelaunch 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowPrelaunch

#### <a name="windows10generalconfigurationedgeblockprinting"></a>Windows10GeneralConfiguration.EdgeBlockPrinting 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowPrinting

#### <a name="windows10generalconfigurationedgeblocksavinghistory"></a>Windows10GeneralConfiguration.EdgeBlockSavingHistory 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowSavingHistory

#### <a name="windows10generalconfigurationedgeblocksearchsuggestions"></a>Windows10GeneralConfiguration.EdgeBlockSearchSuggestions 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowSearchSuggestionsinAddressBar

#### <a name="windows10generalconfigurationedgeblocksendingdonottrackheader"></a>Windows10GeneralConfiguration.EdgeBlockSendingDoNotTrackHeader 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowDoNotTrack

#### <a name="windows10generalconfigurationedgeblocksendingintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeBlockSendingIntranetTrafficToInternetExplorer 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SendIntranetTraffictoInternetExplorer

#### <a name="windows10generalconfigurationedgeblocksideloadingextensions"></a>Windows10GeneralConfiguration.EdgeBlockSideloadingExtensions 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowSideloadingOfExtensions

#### <a name="windows10generalconfigurationedgeblocktabpreloading"></a>Windows10GeneralConfiguration.EdgeBlockTabPreloading 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowTabPreloading

#### <a name="windows10generalconfigurationedgeblockwebcontentonnewtabpage"></a>Windows10GeneralConfiguration.EdgeBlockWebContentOnNewTabPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowWebContentOnNewTabPage

#### <a name="windows10generalconfigurationedgeclearbrowsingdataonexit"></a>Windows10GeneralConfiguration.EdgeClearBrowsingDataOnExit 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ClearBrowsingDataOnExit

#### <a name="windows10generalconfigurationedgecookiepolicy"></a>Windows10GeneralConfiguration.EdgeCookiePolicy 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowCookies

#### <a name="windows10generalconfigurationedgedisablefirstrunpage"></a>Windows10GeneralConfiguration.EdgeDisableFirstRunPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventFirstRunPage

#### <a name="windows10generalconfigurationedgeenterprisemodesitelistlocation"></a>Windows10GeneralConfiguration.EdgeEnterpriseModeSiteListLocation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/EnterpriseSiteListServiceUrl

#### <a name="windows10generalconfigurationedgefavoritesbarvisibility"></a>Windows10GeneralConfiguration.EdgeFavoritesBarVisibility 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureFavoritesBar

#### <a name="windows10generalconfigurationedgefavoriteslistlocation"></a>Windows10GeneralConfiguration.EdgeFavoritesListLocation 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ProvisionFavorites

#### <a name="windows10generalconfigurationedgefirstrunurl"></a>Windows10GeneralConfiguration.EdgeFirstRunUrl 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/FirstRunURL

#### <a name="windows10generalconfigurationedgehomebuttonconfiguration"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfiguration 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SetHomeButtonURL

#### <a name="windows10generalconfigurationedgehomebuttonconfigurationenabled"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfigurationEnabled 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureHomeButton

#### <a name="windows10generalconfigurationedgehomepageurls"></a>Windows10GeneralConfiguration.EdgeHomepageUrls 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SetHomeButtonURL

#### <a name="windows10generalconfigurationedgenewtabpageurl"></a>Windows10GeneralConfiguration.EdgeNewTabPageURL 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SetNewTabPageURL

#### <a name="windows10generalconfigurationedgeopenswith"></a>Windows10GeneralConfiguration.EdgeOpensWith 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureOpenMicrosoftEdgeWith

#### <a name="windows10generalconfigurationedgepreventcertificateerroroverride"></a>Windows10GeneralConfiguration.EdgePreventCertificateErrorOverride 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventCertErrorOverrides

#### <a name="windows10generalconfigurationedgerequiresmartscreen"></a>Windows10GeneralConfiguration.EdgeRequireSmartScreen 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/AllowSmartScreen

#### <a name="windows10generalconfigurationedgesearchengine"></a>Windows10GeneralConfiguration.EdgeSearchEngine 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SetDefaultSearchEngine

#### <a name="windows10generalconfigurationedgesendintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeSendIntranetTrafficToInternetExplorer 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SendIntranetTraffictoInternetExplorer

#### <a name="windows10generalconfigurationedgeshowmessagewhenopeninginternetexplorersites"></a>Windows10GeneralConfiguration.EdgeShowMessageWhenOpeningInternetExplorerSites 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ShowMessageWhenOpeningSitesInInternetExplorer

#### <a name="windows10generalconfigurationedgesyncfavoriteswithinternetexplorer"></a>Windows10GeneralConfiguration.EdgeSyncFavoritesWithInternetExplorer 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/SyncFavoritesBetweenIEAndMicrosoftEdge

#### <a name="windows10generalconfigurationedgetelemetryformicrosoft365analytics"></a>Windows10GeneralConfiguration.EdgeTelemetryForMicrosoft365Analytics 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureTelemetryForMicrosoft365Analytics

#### <a name="windows10generalconfigurationenableautomaticredeployment"></a>Windows10GeneralConfiguration.EnableAutomaticRedeployment 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/CredentialProviders/DisableAutomaticReDeploymentCredentials

#### <a name="windows10generalconfigurationenterprisecloudprintdiscoveryendpoint"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryEndPoint 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint

#### <a name="windows10generalconfigurationenterprisecloudprintdiscoverymaxlimit"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryMaxLimit 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit

#### <a name="windows10generalconfigurationenterprisecloudprintmopriadiscoveryresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId

#### <a name="windows10generalconfigurationenterprisecloudprintoauthauthority"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthAuthority 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

#### <a name="windows10generalconfigurationenterprisecloudprintoauthclientidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthClientIdentifier 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

#### <a name="windows10generalconfigurationenterprisecloudprintresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintResourceIdentifier 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/EnterpriseCloudPrint/CloudPrintResourceId

#### <a name="windows10generalconfigurationexperienceblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.ExperienceBlockConsumerSpecificFeatures 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsConsumerFeatures

#### <a name="windows10generalconfigurationexperienceblockdevicediscovery"></a>Windows10GeneralConfiguration.ExperienceBlockDeviceDiscovery 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowDeviceDiscovery

#### <a name="windows10generalconfigurationexperienceblockerrordialogwhennosim"></a>Windows10GeneralConfiguration.ExperienceBlockErrorDialogWhenNoSIM 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowSIMErrorDialogPromptWhenNoSIM

#### <a name="windows10generalconfigurationexperienceblocktaskswitcher"></a>Windows10GeneralConfiguration.ExperienceBlockTaskSwitcher 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowTaskSwitcher

#### <a name="windows10generalconfigurationexperienceblockwindowsspotlight"></a>Windows10GeneralConfiguration.ExperienceBlockWindowsSpotlight 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsSpotlight

#### <a name="windows10generalconfigurationexperiencedonotsyncbrowsersettings"></a>Windows10GeneralConfiguration.ExperienceDoNotSyncBrowserSettings 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/DoNotSyncBrowserSettings

#### <a name="windows10generalconfigurationgamedvrblocked"></a>Windows10GeneralConfiguration.GameDvrBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowGameDVR

#### <a name="windows10generalconfigurationhardwaredeviceinstallationbydeviceidentifiers"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationByDeviceIdentifiers 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

#### <a name="windows10generalconfigurationhardwaredeviceinstallationbysetupclasses"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationBySetupClasses 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

#### <a name="windows10generalconfigurationinkworkspaceaccess"></a>Windows10GeneralConfiguration.InkWorkspaceAccess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

#### <a name="windows10generalconfigurationinkworkspaceaccessstate"></a>Windows10GeneralConfiguration.InkWorkspaceAccessState 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

#### <a name="windows10generalconfigurationinkworkspaceblocksuggestedapps"></a>Windows10GeneralConfiguration.InkWorkspaceBlockSuggestedApps 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace

#### <a name="windows10generalconfigurationinternetexploreractivexcontrolsinprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerActiveXControlsInProtectedMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DoNotAllowActiveXControlsInProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerautocomplete"></a>Windows10GeneralConfiguration.InternetExplorerAutoComplete 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/AllowAutoComplete

#### <a name="windows10generalconfigurationinternetexplorerblockoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerBlockOutdatedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DoNotBlockOutdatedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarnings"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarnings 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableBypassOfSmartScreenWarnings

#### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarningsaboutuncommonfiles"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarningsAboutUncommonFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableBypassOfSmartScreenWarningsAboutUncommonFiles

#### <a name="windows10generalconfigurationinternetexplorercertificateaddressmismatchwarning"></a>Windows10GeneralConfiguration.InternetExplorerCertificateAddressMismatchWarning 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/AllowCertificateAddressMismatchWarning

#### <a name="windows10generalconfigurationinternetexplorercheckservercertificaterevocation"></a>Windows10GeneralConfiguration.InternetExplorerCheckServerCertificateRevocation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/CheckServerCertificateRevocation

#### <a name="windows10generalconfigurationinternetexplorerchecksignaturesondownloadedprograms"></a>Windows10GeneralConfiguration.InternetExplorerCheckSignaturesOnDownloadedPrograms 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/CheckSignaturesOnDownloadedPrograms

#### <a name="windows10generalconfigurationinternetexplorercrashdetection"></a>Windows10GeneralConfiguration.InternetExplorerCrashDetection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableCrashDetection

#### <a name="windows10generalconfigurationinternetexplorerdisableprocessesinenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerDisableProcessesInEnhancedProtectedMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableProcessesInEnhancedProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerdownloadenclosures"></a>Windows10GeneralConfiguration.InternetExplorerDownloadEnclosures 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableEnclosureDownloading

#### <a name="windows10generalconfigurationinternetexplorerencryptionsupport"></a>Windows10GeneralConfiguration.InternetExplorerEncryptionSupport 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableEncryptionSupport

#### <a name="windows10generalconfigurationinternetexplorerenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerEnhancedProtectedMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/AllowEnhancedProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerfallbacktossl3"></a>Windows10GeneralConfiguration.InternetExplorerFallbackToSsl3 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/AllowFallbackToSSL3

#### <a name="windows10generalconfigurationinternetexplorerignorecertificateerrors"></a>Windows10GeneralConfiguration.InternetExplorerIgnoreCertificateErrors 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableIgnoringCertificateErrors

#### <a name="windows10generalconfigurationinternetexplorerincludeallnetworkpaths"></a>Windows10GeneralConfiguration.InternetExplorerIncludeAllNetworkPaths 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/IncludeAllNetworkPaths

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAccessToDataSources 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowAccessToDataSources

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowVBScriptToRun 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowVBScriptToRunInInternetExplorer

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAutomaticPromptForFileDownloads 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowAutomaticPromptingForFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerinternetzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCopyAndPasteViaScript 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowCopyPasteViaScript

#### <a name="windows10generalconfigurationinternetexplorerinternetzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCrossSiteScriptingFilter 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneEnableCrossSiteScriptingFilter

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDotNetFrameworkReliantComponents 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowNETFrameworkReliantComponents

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadSignedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneDownloadSignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadUnsignedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneDownloadUnsignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragAndDropOrCopyAndPasteFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowDragAndDropCopyAndPasteFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneIncludeLocalPathWhenUploadingFilesToServer

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneJavaPermissions


#### <a name="windows10generalconfigurationinternetexplorerinternetzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneLaunchingApplicationsAndFilesInIFRAME

#### <a name="windows10generalconfigurationinternetexplorerinternetzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLessPrivilegedSites 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowLessPrivilegedSites

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLoadingOfXamlFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowLoadingOfXAMLFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLogonOptions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneLogonOptions

#### <a name="windows10generalconfigurationinternetexplorerinternetzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneNavigateWindowsAndFrames

#### <a name="windows10generalconfigurationinternetexplorerinternetzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerInternetZonePopupBlocker 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneUsePopupBlocker

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneProtectedMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneEnableProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerinternetzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptingOfWebBrowserControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowScriptingOfInternetExplorerWebBrowserControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptInitiatedWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowScriptInitiatedWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptlets 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowScriptlets

#### <a name="windows10generalconfigurationinternetexplorerinternetzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneShowSecurityWarningForPotentiallyUnsafeFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSmartScreen 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUpdatesToStatusBarViaScript 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowUpdatesToStatusBarViaScript

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUserDataPersistence 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/InternetZoneAllowUserDataPersistence

#### <a name="windows10generalconfigurationinternetexplorerintranetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/IntranetZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerintranetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/IntranetZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/IntranetZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LocalMachineZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddowninternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownInternetZoneSmartScreen 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownInternetZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerlockeddownintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownIntranetZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownIntranetJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownLocalMachineZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownLocalMachineZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownRestrictedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneSmartScreen 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownRestrictedSitesZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerlockeddowntrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownTrustedZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/LockedDownTrustedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerpreventmanagingsmartscreenfilter"></a>Windows10GeneralConfiguration.InternetExplorerPreventManagingSmartScreenFilter 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/PreventManagingSmartScreenFilter

#### <a name="windows10generalconfigurationinternetexplorerpreventperuserinstallationofactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerPreventPerUserInstallationOfActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/PreventPerUserInstallationOfActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerprocessesconsistentmimehandling"></a>Windows10GeneralConfiguration.InternetExplorerProcessesConsistentMimeHandling 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/ConsistentMimeHandlingInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesmimesniffingsafetyfeature"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMimeSniffingSafetyFeature 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/MimeSniffingSafetyFeatureInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesmkprotocolsecurityrestriction"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMKProtocolSecurityRestriction 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/MKProtocolSecurityRestrictionInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesnotificationbar"></a>Windows10GeneralConfiguration.InternetExplorerProcessesNotificationBar 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/NotificationBarInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesprotectionfromzoneelevation"></a>Windows10GeneralConfiguration.InternetExplorerProcessesProtectionFromZoneElevation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/ProtectionFromZoneElevationInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictactivexinstall"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictActiveXInstall 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictActiveXInstallInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictfiledownload"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictFileDownload 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictFileDownloadInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesscriptedwindowsecurityrestrictions"></a>Windows10GeneralConfiguration.InternetExplorerProcessesScriptedWindowSecurityRestrictions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/ScriptedWindowSecurityRestrictionsInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerremoverunthistimebuttonforoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRemoveRunThisTimeButtonForOutdatedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RemoveRunThisTimeButtonForOutdatedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAccessToDataSources 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowAccessToDataSources

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneactivescripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneActiveScripting 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowActiveScripting

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowVBScriptToRun 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowVBScriptToRunInInternetExplorer

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAutomaticPromptForFileDownloads 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowAutomaticPromptingForFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonebinaryandscriptbehaviors"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneBinaryAndScriptBehaviors 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowBinaryAndScriptBehaviors

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCopyAndPasteViaScript 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowCopyPasteViaScript

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCrossSiteScriptingFilter 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableCrossSiteScriptingFilter

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDotNetFrameworkReliantComponents 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowNETFrameworkReliantComponents

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadSignedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneDownloadSignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadUnsignedActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneDownloadUnsignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragAndDropOrCopyAndPasteFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowDragAndDropCopyAndPasteFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsAcrossWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsWithinWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonefiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneFileDownloads 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneIncludeLocalPathWhenUploadingFilesToServer 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneIncludeLocalPathWhenUploadingFilesToServer

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLaunchApplicationsAndFilesInAnIFrame 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneLaunchingApplicationsAndFilesInIFRAME

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLessPrivilegedSites 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowLessPrivilegedSites

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLoadingOfXamlFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowLoadingOfXAMLFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLogonOptions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneLogonOptions

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonemetarefresh"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneMetaRefresh 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowMETAREFRESH

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneNavigateWindowsAndFrames

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZonePopupBlocker 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneUsePopupBlocker

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneProtectedMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneTurnOnProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerunactivexcontrolsandplugins"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunActiveXControlsAndPlugins 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneRunActiveXControlsAndPlugins

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptactivexcontrolsmarkedsafeforscripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptActiveXControlsMarkedSafeForScripting 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneScriptActiveXControlsMarkedSafeForScripting

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofjavaapplets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfJavaApplets 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneScriptingOfJavaApplets

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfWebBrowserControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptingOfInternetExplorerWebBrowserControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptInitiatedWindows 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptInitiatedWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptlets 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptlets

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSecurityWarningForPotentiallyUnsafeFiles 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneShowSecurityWarningForPotentiallyUnsafeFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSmartScreen 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUpdatesToStatusBarViaScript 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowUpdatesToStatusBarViaScript

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUserDataPersistence 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowUserDataPersistence

#### <a name="windows10generalconfigurationinternetexplorersecuritysettingscheck"></a>Windows10GeneralConfiguration.InternetExplorerSecuritySettingsCheck 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DisableSecuritySettingsCheck

#### <a name="windows10generalconfigurationinternetexplorersecurityzonesuseonlymachinesettings"></a>Windows10GeneralConfiguration.InternetExplorerSecurityZonesUseOnlyMachineSettings 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/SecurityZonesUseOnlyMachineSettings

#### <a name="windows10generalconfigurationinternetexplorersoftwarewhensignatureisinvalid"></a>Windows10GeneralConfiguration.InternetExplorerSoftwareWhenSignatureIsInvalid 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/AllowSoftwareWhenSignatureIsInvalid

#### <a name="windows10generalconfigurationinternetexplorertrustedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneDoNotRunAntimalwareAgainstActiveXControls 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/TrustedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorertrustedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/TrustedSitesZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorertrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneJavaPermissions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/TrustedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexploreruseactivexinstallerservice"></a>Windows10GeneralConfiguration.InternetExplorerUseActiveXInstallerService 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/SpecifyUseOfActiveXInstallerService

#### <a name="windows10generalconfigurationinternetexplorerusersaddingsites"></a>Windows10GeneralConfiguration.InternetExplorerUsersAddingSites 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DoNotAllowUsersToAddSites

#### <a name="windows10generalconfigurationinternetexploreruserschangingpolicies"></a>Windows10GeneralConfiguration.InternetExplorerUsersChangingPolicies 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/InternetExplorer/DoNotAllowUsersToChangePolicies

#### <a name="windows10generalconfigurationinternetsharingblocked"></a>Windows10GeneralConfiguration.InternetSharingBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WiFi/AllowInternetSharing

#### <a name="windows10generalconfigurationlocationservicesblocked"></a>Windows10GeneralConfiguration.LocationServicesBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/AllowLocation

#### <a name="windows10generalconfigurationlockscreenallowtimeoutconfiguration"></a>Windows10GeneralConfiguration.LockScreenAllowTimeoutConfiguration 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/AllowScreenTimeoutWhileLockedUser/Config

#### <a name="windows10generalconfigurationlockscreenblockactioncenternotifications"></a>Windows10GeneralConfiguration.LockScreenBlockActionCenterNotifications 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/AboveLock/AllowActionCenterNotifications

#### <a name="windows10generalconfigurationlockscreenblockcortana"></a>Windows10GeneralConfiguration.LockScreenBlockCortana 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/AboveLock/AllowCortanaAboveLock

#### <a name="windows10generalconfigurationlockscreenblocktoastnotifications"></a>Windows10GeneralConfiguration.LockScreenBlockToastNotifications 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/AboveLock/AllowToasts

#### <a name="windows10generalconfigurationlockscreencamera"></a>Windows10GeneralConfiguration.LockScreenCamera 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/PreventEnablingLockScreenCamera

#### <a name="windows10generalconfigurationlockscreenhidenetworkselectionui"></a>Windows10GeneralConfiguration.LockScreenHideNetworkSelectionUI 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsLogon/DontDisplayNetworkSelectionUI

#### <a name="windows10generalconfigurationlockscreenslideshow"></a>Windows10GeneralConfiguration.LockScreenSlideShow 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/PreventLockScreenSlideShow

#### <a name="windows10generalconfigurationlockscreentimeoutinseconds"></a>Windows10GeneralConfiguration.LockScreenTimeoutInSeconds 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/ScreenTimeoutWhileLocked

#### <a name="windows10generalconfigurationlogonblockfastuserswitching"></a>Windows10GeneralConfiguration.LogonBlockFastUserSwitching 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsLogon/HideFastUserSwitching

#### <a name="windows10generalconfigurationmessagingblockmms"></a>Windows10GeneralConfiguration.MessagingBlockMMS 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Messaging/AllowMMS

#### <a name="windows10generalconfigurationmessagingblockrichcommunicationservices"></a>Windows10GeneralConfiguration.MessagingBlockRichCommunicationServices 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Messaging/AllowRCS

#### <a name="windows10generalconfigurationmessagingblocksync"></a>Windows10GeneralConfiguration.MessagingBlockSync 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Messaging/AllowMessageSync

#### <a name="windows10generalconfigurationmicrosoftaccountblocked"></a>Windows10GeneralConfiguration.MicrosoftAccountBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Accounts/AllowMicrosoftAccountConnection

#### <a name="windows10generalconfigurationmicrosoftaccountblocksettingssync"></a>Windows10GeneralConfiguration.MicrosoftAccountBlockSettingsSync 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowSyncMySettings

#### <a name="windows10generalconfigurationmicrosoftaccountsigninassistantsettings"></a>Windows10GeneralConfiguration.MicrosoftAccountSignInAssistantSettings 
**CSP**: ./Device/Vendor/MSFT/Accounts  
**Offset URI**: /AllowMicrosoftAccountSignInAssistant

#### <a name="windows10generalconfigurationnetworkproxyapplysettingsdevicewide"></a>Windows10GeneralConfiguration.NetworkProxyApplySettingsDeviceWide 
**CSP**: ./Device/Vendor/MSFT/NetworkProxy  
**Offset URI**: /ProxySettingsPerUser

#### <a name="windows10generalconfigurationnetworkproxyautomaticconfigurationurl"></a>Windows10GeneralConfiguration.NetworkProxyAutomaticConfigurationUrl 
**CSP**: ./Device/Vendor/MSFT/NetworkProxy  
**Offset URI**: /SetupScriptUrl

#### <a name="windows10generalconfigurationnetworkproxydisableautodetect"></a>Windows10GeneralConfiguration.NetworkProxyDisableAutoDetect 
**CSP**: ./Device/Vendor/MSFT/NetworkProxy  
**Offset URI**: /AutoDetect

#### <a name="windows10generalconfigurationnetworkproxyserver"></a>Windows10GeneralConfiguration.NetworkProxyServer 
**CSP**: ./Vendor/MSFT/NetworkProxy  
**Offset URI**: / ProxyAddress, /Exceptions und /UseProxyForLocalAddresses

#### <a name="windows10generalconfigurationnfcblocked"></a>Windows10GeneralConfiguration.NfcBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowNFC

#### <a name="windows10generalconfigurationonedrivedisablefilesync"></a>Windows10GeneralConfiguration.OneDriveDisableFileSync 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/DisableOneDriveFileSync

#### <a name="windows10generalconfigurationpasswordblocksimple"></a>Windows10GeneralConfiguration.PasswordBlockSimple 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/AllowSimpleDevicePassword

#### <a name="windows10generalconfigurationpasswordexpirationdays"></a>Windows10GeneralConfiguration.PasswordExpirationDays 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/DevicePasswordExpiration

#### <a name="windows10generalconfigurationpasswordminimumageindays"></a>Windows10GeneralConfiguration.PasswordMinimumAgeInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/MinimumPasswordAge

#### <a name="windows10generalconfigurationpasswordminimumcharactersetcount"></a>Windows10GeneralConfiguration.PasswordMinimumCharacterSetCount 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/MinDevicePasswordComplexCharacters

#### <a name="windows10generalconfigurationpasswordminimumlength"></a>Windows10GeneralConfiguration.PasswordMinimumLength 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/MinDevicePasswordLength

#### <a name="windows10generalconfigurationpasswordminutesofinactivitybeforescreentimeout"></a>Windows10GeneralConfiguration.PasswordMinutesOfInactivityBeforeScreenTimeout 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/MaxInactivityTimeDeviceLock

#### <a name="windows10generalconfigurationpasswordpreviouspasswordblockcount"></a>Windows10GeneralConfiguration.PasswordPreviousPasswordBlockCount 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/DevicePasswordHistory

#### <a name="windows10generalconfigurationpasswordrequired"></a>Windows10GeneralConfiguration.PasswordRequired 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/DevicePasswordEnabled

#### <a name="windows10generalconfigurationpasswordrequiredtype"></a>Windows10GeneralConfiguration.PasswordRequiredType 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/AlphanumericDevicePasswordRequired

#### <a name="windows10generalconfigurationpasswordrequirewhenresumefromidlestate"></a>Windows10GeneralConfiguration.PasswordRequireWhenResumeFromIdleState 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/AllowIdleReturnWithoutPassword

#### <a name="windows10generalconfigurationpasswordsigninfailurecountbeforefactoryreset"></a>Windows10GeneralConfiguration.PasswordSignInFailureCountBeforeFactoryReset 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceLock/MaxDevicePasswordFailedAttempts

#### <a name="windows10generalconfigurationpersonalizationdesktopimageurl"></a>Windows10GeneralConfiguration.PersonalizationDesktopImageUrl 
**CSP**: ./Device/Vendor/MSFT/Personalization  
**Offset URI**: /DesktopImageUrl

#### <a name="windows10generalconfigurationpersonalizationlockscreenimageurl"></a>Windows10GeneralConfiguration.PersonalizationLockScreenImageUrl 
**CSP**: ./Device/Vendor/MSFT/Personalization  
**Offset URI**: /LockScreenImageUrl

#### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhileonbattery"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhileOnBattery 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Power/RequirePasswordWhenComputerWakesOnBattery

#### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhilepluggedin"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhilePluggedIn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Power/RequirePasswordWhenComputerWakesPluggedIn

#### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhileonbattery"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhileOnBattery 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Power/AllowStandbyStatesWhenSleepingOnBattery

#### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhilepluggedin"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhilePluggedIn 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Power/AllowStandbyWhenSleepingPluggedIn

#### <a name="windows10generalconfigurationpreventinstallationofmatchingdeviceids"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceIDs 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

#### <a name="windows10generalconfigurationpreventinstallationofmatchingdevicesetupclasses"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceSetupClasses 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

#### <a name="windows10generalconfigurationprinterblockaddition"></a>Windows10GeneralConfiguration.PrinterBlockAddition 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Education/PreventAddingNewPrinters

#### <a name="windows10generalconfigurationprinterdefaultname"></a>Windows10GeneralConfiguration.PrinterDefaultName 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Education/DefaultPrinterName

#### <a name="windows10generalconfigurationprinternames"></a>Windows10GeneralConfiguration.PrinterNames 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Education/PrinterNames

#### <a name="windows10generalconfigurationprivacyadvertisingid"></a>Windows10GeneralConfiguration.PrivacyAdvertisingId 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Privacy/DisableAdvertisingID

#### <a name="windows10generalconfigurationprivacyautoacceptpairingandconsentprompts"></a>Windows10GeneralConfiguration.PrivacyAutoAcceptPairingAndConsentPrompts 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Privacy/AllowAutoAcceptPairingAndPrivacyConsentPrompts

#### <a name="windows10generalconfigurationprivacyblockactivityfeed"></a>Windows10GeneralConfiguration.PrivacyBlockActivityFeed 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Privacy/EnableActivityFeed

#### <a name="windows10generalconfigurationprivacyblockinputpersonalization"></a>Windows10GeneralConfiguration.PrivacyBlockInputPersonalization 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Privacy/AllowInputPersonalization

#### <a name="windows10generalconfigurationprivacyblockpublishuseractivities"></a>Windows10GeneralConfiguration.PrivacyBlockPublishUserActivities 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Privacy/PublishUserActivities

#### <a name="windows10generalconfigurationsafesearchfilter"></a>Windows10GeneralConfiguration.SafeSearchFilter 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/SafeSearchPermissions

#### <a name="windows10generalconfigurationscreencaptureblocked"></a>Windows10GeneralConfiguration.ScreenCaptureBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowScreenCapture

#### <a name="windows10generalconfigurationsearchblockdiacritics"></a>Windows10GeneralConfiguration.SearchBlockDiacritics 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/AllowUsingDiacritics

#### <a name="windows10generalconfigurationsearchblockwebresults"></a>Windows10GeneralConfiguration.SearchBlockWebResults 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/DoNotUseWebResults

#### <a name="windows10generalconfigurationsearchdisableautolanguagedetection"></a>Windows10GeneralConfiguration.SearchDisableAutoLanguageDetection 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/AlwaysUseAutoLangDetection

#### <a name="windows10generalconfigurationsearchdisableindexerbackoff"></a>Windows10GeneralConfiguration.SearchDisableIndexerBackoff 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/DisableBackoff

#### <a name="windows10generalconfigurationsearchdisableindexingencrypteditems"></a>Windows10GeneralConfiguration.SearchDisableIndexingEncryptedItems 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/AllowIndexingEncryptedStoresOrItems

#### <a name="windows10generalconfigurationsearchdisableindexingremovabledrive"></a>Windows10GeneralConfiguration.SearchDisableIndexingRemovableDrive 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/DisableRemovableDriveIndexing

#### <a name="windows10generalconfigurationsearchdisablelocation"></a>Windows10GeneralConfiguration.SearchDisableLocation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/AllowSearchToUseLocation

#### <a name="windows10generalconfigurationsearchdisableuselocation"></a>Windows10GeneralConfiguration.SearchDisableUseLocation 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/AllowSearchToUseLocation

#### <a name="windows10generalconfigurationsearchenableautomaticindexsizemanangement"></a>Windows10GeneralConfiguration.SearchEnableAutomaticIndexSizeManangement 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/PreventIndexingLowDiskSpaceMB

#### <a name="windows10generalconfigurationsearchenableremotequeries"></a>Windows10GeneralConfiguration.SearchEnableRemoteQueries 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Search/PreventRemoteQueries

#### <a name="windows10generalconfigurationsecurityblockazureadjoineddevicesautoencryption"></a>Windows10GeneralConfiguration.SecurityBlockAzureADJoinedDevicesAutoEncryption 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices

#### <a name="windows10generalconfigurationsettingsblockaccountspage"></a>Windows10GeneralConfiguration.SettingsBlockAccountsPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockaddprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockAddProvisioningPackage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/AllowAddProvisioningPackage

#### <a name="windows10generalconfigurationsettingsblockappspage"></a>Windows10GeneralConfiguration.SettingsBlockAppsPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockchangelanguage"></a>Windows10GeneralConfiguration.SettingsBlockChangeLanguage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/AllowLanguage

#### <a name="windows10generalconfigurationsettingsblockchangepowersleep"></a>Windows10GeneralConfiguration.SettingsBlockChangePowerSleep 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/AllowPowerSleep

#### <a name="windows10generalconfigurationsettingsblockchangeregion"></a>Windows10GeneralConfiguration.SettingsBlockChangeRegion 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/AllowRegion

#### <a name="windows10generalconfigurationsettingsblockchangesystemtime"></a>Windows10GeneralConfiguration.SettingsBlockChangeSystemTime 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/AllowDateTime

#### <a name="windows10generalconfigurationsettingsblockdevicespage"></a>Windows10GeneralConfiguration.SettingsBlockDevicesPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockeaseofaccesspage"></a>Windows10GeneralConfiguration.SettingsBlockEaseOfAccessPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockeditdevicename"></a>Windows10GeneralConfiguration.SettingsBlockEditDeviceName 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/AllowEditDeviceName

#### <a name="windows10generalconfigurationsettingsblockgamingpage"></a>Windows10GeneralConfiguration.SettingsBlockGamingPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblocknetworkinternetpage"></a>Windows10GeneralConfiguration.SettingsBlockNetworkInternetPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockpersonalizationpage"></a>Windows10GeneralConfiguration.SettingsBlockPersonalizationPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockprivacypage"></a>Windows10GeneralConfiguration.SettingsBlockPrivacyPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockremoveprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockRemoveProvisioningPackage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/AllowRemoveProvisioningPackage

#### <a name="windows10generalconfigurationsettingsblocksystempage"></a>Windows10GeneralConfiguration.SettingsBlockSystemPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblocktimelanguagepage"></a>Windows10GeneralConfiguration.SettingsBlockTimeLanguagePage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockupdatesecuritypage"></a>Windows10GeneralConfiguration.SettingsBlockUpdateSecurityPage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationshareduserappdataallowed"></a>Windows10GeneralConfiguration.SharedUserAppDataAllowed 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowSharedUserAppData

#### <a name="windows10generalconfigurationsmartscreenblockpromptoverride"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverride 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventSmartScreenPromptOverride

#### <a name="windows10generalconfigurationsmartscreenblockpromptoverrideforfiles"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverrideForFiles 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventSmartScreenPromptOverrideForFiles

#### <a name="windows10generalconfigurationsmartscreenenableappinstallcontrol"></a>Windows10GeneralConfiguration.SmartScreenEnableAppInstallControl 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/SmartScreen/EnableAppInstallControl

#### <a name="windows10generalconfigurationstartblockunpinningappsfromtaskbar"></a>Windows10GeneralConfiguration.StartBlockUnpinningAppsFromTaskbar 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/NoPinningToTaskbar

#### <a name="windows10generalconfigurationstartmenuapplistvisibility"></a>Windows10GeneralConfiguration.StartMenuAppListVisibility 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideAppList

#### <a name="windows10generalconfigurationstartmenuhidechangeaccountsettings"></a>Windows10GeneralConfiguration.StartMenuHideChangeAccountSettings 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideChangeAccountSettings

#### <a name="windows10generalconfigurationstartmenuhidefrequentlyusedapps"></a>Windows10GeneralConfiguration.StartMenuHideFrequentlyUsedApps 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideFrequentlyUsedApps

#### <a name="windows10generalconfigurationstartmenuhidehibernate"></a>Windows10GeneralConfiguration.StartMenuHideHibernate 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideHibernate

#### <a name="windows10generalconfigurationstartmenuhidelock"></a>Windows10GeneralConfiguration.StartMenuHideLock 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideLock

#### <a name="windows10generalconfigurationstartmenuhidepowerbutton"></a>Windows10GeneralConfiguration.StartMenuHidePowerButton 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HidePowerButton

#### <a name="windows10generalconfigurationstartmenuhiderecentjumplists"></a>Windows10GeneralConfiguration.StartMenuHideRecentJumpLists 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideRecentJumplists

#### <a name="windows10generalconfigurationstartmenuhiderecentlyaddedapps"></a>Windows10GeneralConfiguration.StartMenuHideRecentlyAddedApps 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideRecentlyAddedApps

#### <a name="windows10generalconfigurationstartmenuhiderestartoptions"></a>Windows10GeneralConfiguration.StartMenuHideRestartOptions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideRestart

#### <a name="windows10generalconfigurationstartmenuhideshutdown"></a>Windows10GeneralConfiguration.StartMenuHideShutDown 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideShutDown

#### <a name="windows10generalconfigurationstartmenuhidesignout"></a>Windows10GeneralConfiguration.StartMenuHideSignOut 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideSignOut

#### <a name="windows10generalconfigurationstartmenuhidesleep"></a>Windows10GeneralConfiguration.StartMenuHideSleep 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideSleep

#### <a name="windows10generalconfigurationstartmenuhideswitchaccount"></a>Windows10GeneralConfiguration.StartMenuHideSwitchAccount 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideSwitchAccount

#### <a name="windows10generalconfigurationstartmenuhideusertile"></a>Windows10GeneralConfiguration.StartMenuHideUserTile 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/HideUserTile

#### <a name="windows10generalconfigurationstartmenulayoutedgeassetsxml"></a>Windows10GeneralConfiguration.StartMenuLayoutEdgeAssetsXml 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/ImportEdgeAssets

#### <a name="windows10generalconfigurationstartmenulayoutxml"></a>Windows10GeneralConfiguration.StartMenuLayoutXml 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/StartLayout

#### <a name="windows10generalconfigurationstartmenumode"></a>Windows10GeneralConfiguration.StartMenuMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/ForceStartSize

#### <a name="windows10generalconfigurationstartmenupinnedfolderdocuments"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDocuments 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderDocuments

#### <a name="windows10generalconfigurationstartmenupinnedfolderdownloads"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDownloads 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderDownloads

#### <a name="windows10generalconfigurationstartmenupinnedfolderfileexplorer"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderFileExplorer 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderFileExplorer

#### <a name="windows10generalconfigurationstartmenupinnedfolderhomegroup"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderHomeGroup 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderHomeGroup

#### <a name="windows10generalconfigurationstartmenupinnedfoldermusic"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderMusic 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderMusic

#### <a name="windows10generalconfigurationstartmenupinnedfoldernetwork"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderNetwork 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderNetwork

#### <a name="windows10generalconfigurationstartmenupinnedfolderpersonalfolder"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPersonalFolder 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderPersonalFolder

#### <a name="windows10generalconfigurationstartmenupinnedfolderpictures"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPictures 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderPictures

#### <a name="windows10generalconfigurationstartmenupinnedfoldersettings"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderSettings 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderSettings

#### <a name="windows10generalconfigurationstartmenupinnedfoldervideos"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderVideos 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Start/AllowPinnedFolderVideos

#### <a name="windows10generalconfigurationstorageblockremovablestorage"></a>Windows10GeneralConfiguration.StorageBlockRemovableStorage 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/AllowStorageCard

#### <a name="windows10generalconfigurationstoragerequiremobiledeviceencryption"></a>Windows10GeneralConfiguration.StorageRequireMobileDeviceEncryption 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Security/RequireDeviceEncryption

#### <a name="windows10generalconfigurationstoragerestrictappdatatosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppDataToSystemVolume 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/RestrictAppDataToSystemVolume

#### <a name="windows10generalconfigurationstoragerestrictappinstalltosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppInstallToSystemVolume 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/RestrictAppToSystemVolume

#### <a name="windows10generalconfigurationsystembootstartdriverinitialization"></a>Windows10GeneralConfiguration.SystemBootStartDriverInitialization 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/System/BootStartDriverInitialization

#### <a name="windows10generalconfigurationsystemtelemetryproxyserver"></a>Windows10GeneralConfiguration.SystemTelemetryProxyServer 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/System/TelemetryProxy

#### <a name="windows10generalconfigurationtaskmanagerblockendtask"></a>Windows10GeneralConfiguration.TaskManagerBlockEndTask 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/TaskManager/AllowEndTask

#### <a name="windows10generalconfigurationtenantlockdownrequirenetworkduringoutofboxexperience"></a>Windows10GeneralConfiguration.TenantLockdownRequireNetworkDuringOutOfBoxExperience 
**CSP**: ./Vendor/MSFT/TenantLockdown  
**Offset URI**: /RequireNetworkInOOBE

#### <a name="windows10generalconfigurationusbblocked"></a>Windows10GeneralConfiguration.UsbBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Connectivity/AllowUSBConnection

#### <a name="windows10generalconfigurationvoicerecordingblocked"></a>Windows10GeneralConfiguration.VoiceRecordingBlocked 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowVoiceRecording

#### <a name="windows10generalconfigurationwebrtcblocklocalhostipaddress"></a>Windows10GeneralConfiguration.WebRtcBlockLocalhostIpAddress 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/PreventUsingLocalHostIPAddressForWebRTC

#### <a name="windows10generalconfigurationwifiblockautomaticconnecthotspots"></a>Windows10GeneralConfiguration.WiFiBlockAutomaticConnectHotspots 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WiFi/AllowAutoConnectToWiFiSenseHotspots

#### <a name="windows10generalconfigurationwifiblocked"></a>Windows10GeneralConfiguration.WiFiBlocked 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Wifi/AllowWiFi

#### <a name="windows10generalconfigurationwifiblockmanualconfiguration"></a>Windows10GeneralConfiguration.WiFiBlockManualConfiguration 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WiFi/AllowManualWiFi/Configuration

#### <a name="windows10generalconfigurationwifiscaninterval"></a>Windows10GeneralConfiguration.WiFiScanInterval 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WiFi/WLANScanMode

#### <a name="windows10generalconfigurationwindowslogonlocalusersondomainjoinedcomputers"></a>Windows10GeneralConfiguration.WindowsLogOnLocalUsersOnDomainJoinedComputers 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/WindowsLogon/EnumerateLocalUsersOnDomainJoinedComputers

#### <a name="windows10generalconfigurationwindowsspotlightblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockConsumerSpecificFeatures 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsConsumerFeatures

#### <a name="windows10generalconfigurationwindowsspotlightblocked"></a>Windows10GeneralConfiguration.WindowsSpotlightBlocked 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsSpotlight

#### <a name="windows10generalconfigurationwindowsspotlightblockonactioncenter"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockOnActionCenter 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsSpotlightOnActionCenter

#### <a name="windows10generalconfigurationwindowsspotlightblocktailoredexperiences"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockTailoredExperiences 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowTailoredExperiencesWithDiagnosticData

#### <a name="windows10generalconfigurationwindowsspotlightblockthirdpartynotifications"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockThirdPartyNotifications 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowThirdPartySuggestionsInWindowsSpotlight

#### <a name="windows10generalconfigurationwindowsspotlightblockwelcomeexperience"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWelcomeExperience 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsSpotlightWindowsWelcomeExperience

#### <a name="windows10generalconfigurationwindowsspotlightblockwindowstips"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWindowsTips 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/AllowWindowsTips

#### <a name="windows10generalconfigurationwindowsspotlightconfigureonlockscreen"></a>Windows10GeneralConfiguration.WindowsSpotlightConfigureOnLockScreen 
**CSP**: ./User/Vendor/MSFT/Policy  
**Offset URI**: /Config/Experience/ConfigureWindowsSpotlightOnLockScreen

#### <a name="windows10generalconfigurationwindowsstoreblockautoupdate"></a>Windows10GeneralConfiguration.WindowsStoreBlockAutoUpdate 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowAppStoreAutoUpdate

#### <a name="windows10generalconfigurationwindowsstoreblocked"></a>Windows10GeneralConfiguration.WindowsStoreBlocked 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/AllowStore

#### <a name="windows10generalconfigurationwindowsstoreenableprivatestoreonly"></a>Windows10GeneralConfiguration.WindowsStoreEnablePrivateStoreOnly 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/ApplicationManagement/RequirePrivateStoreOnly

#### <a name="windows10generalconfigurationwirelessdisplayblockprojectiontothisdevice"></a>Windows10GeneralConfiguration.WirelessDisplayBlockProjectionToThisDevice 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WirelessDisplay/AllowProjectionToPC

#### <a name="windows10generalconfigurationwirelessdisplayblockuserinputfromreceiver"></a>Windows10GeneralConfiguration.WirelessDisplayBlockUserInputFromReceiver 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WirelessDisplay/AllowUserInputFromWirelessDisplayReceiver

#### <a name="windows10generalconfigurationwirelessdisplayrequirepinforpairing"></a>Windows10GeneralConfiguration.WirelessDisplayRequirePinForPairing 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/WirelessDisplay/RequirePINForPairing

#### <a name="windows10networkboundaryconfigurationwindowsnetworkisolationpolicy"></a>Windows10NetworkBoundaryConfiguration.WindowsNetworkIsolationPolicy 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/NetworkIsolation/EnterpriseCloudResources, /Config/NetworkIsolation/EnterpriseIPRange, /Config/NetworkIsolation/EnterpriseIPRangesAreAuthoritative, / config/NetworkIsolation / EnterpriseInternalProxyServers, /Config/NetworkIsolation/EnterpriseNetworkDomainNames, /Config/NetworkIsolation/EnterpriseProxyServers, /Config/NetworkIsolation/EnterpriseProxyServersAreAuthoritative, / config/NetworkIsolation / NeutralResources

#### <a name="windows10policyoverrideconfigurationprefermdmovergrouppolicy"></a>Windows10PolicyOverrideConfiguration.PreferMdmOverGroupPolicy 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/ControlPolicyConflict/MDMWinsOverGP

#### <a name="windows10secureassessmentconfigurationallowprinting"></a>Windows10SecureAssessmentConfiguration.AllowPrinting 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /RequirePrinting

#### <a name="windows10secureassessmentconfigurationallowscreencapture"></a>Windows10SecureAssessmentConfiguration.AllowScreenCapture 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /AllowScreenMonitoring

#### <a name="windows10secureassessmentconfigurationallowtextsuggestion"></a>Windows10SecureAssessmentConfiguration.AllowTextSuggestion 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /AllowTextSuggestions

#### <a name="windows10secureassessmentconfigurationconfigurationaccount"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccount 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /TesterAccount

#### <a name="windows10secureassessmentconfigurationconfigurationaccounttype"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccountType 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /TesterAccount

#### <a name="windows10secureassessmentconfigurationlaunchuri"></a>Windows10SecureAssessmentConfiguration.LaunchUri 
**CSP**: ./Vendor/MSFT/SecureAssessment  
**Offset URI**: /LaunchURI

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsblocktelemetry"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsBlockTelemetry 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / MOMAgent/WorkspaceID und WorkspaceKey/MOMAgent /

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspaceid"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceId 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /MOMAgent/WorkspaceID

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspacekey"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceKey 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / MOMAgent/WorkspaceKey

#### <a name="windows10teamgeneralconfigurationconnectappblockautolaunch"></a>Windows10TeamGeneralConfiguration.ConnectAppBlockAutoLaunch 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/Connect/AutoLaunch

#### <a name="windows10teamgeneralconfigurationdeviceaccountblockexchangeservices"></a>Windows10TeamGeneralConfiguration.DeviceAccountBlockExchangeServices 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / DeviceAccount/E-Mail

#### <a name="windows10teamgeneralconfigurationdeviceaccountemailaddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountEmailAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / DeviceAccount/E-Mail

#### <a name="windows10teamgeneralconfigurationdeviceaccountexchangeserveraddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountExchangeServerAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / DeviceAccount/ExchangeServer

#### <a name="windows10teamgeneralconfigurationdeviceaccountrequirepasswordrotation"></a>Windows10TeamGeneralConfiguration.DeviceAccountRequirePasswordRotation 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /DeviceAccount/PasswordRotationEnabled

#### <a name="windows10teamgeneralconfigurationdeviceaccountsessioninitiationprotocoladdress"></a>Windows10TeamGeneralConfiguration.DeviceAccountSessionInitiationProtocolAddress 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /DeviceAccount/SipAddress

#### <a name="windows10teamgeneralconfigurationmaintenancewindowblocked"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowBlocked 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /MaintenanceHoursSimple/Hours/Duration und /MaintenanceHoursSimple/Hours/StartTime

#### <a name="windows10teamgeneralconfigurationmaintenancewindowdurationinhours"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowDurationInHours 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /MaintenanceHoursSimple/Hours/Duration

#### <a name="windows10teamgeneralconfigurationmaintenancewindowstarttime"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowStartTime 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /MaintenanceHoursSimple/Hours/StartTime

#### <a name="windows10teamgeneralconfigurationmiracastblocked"></a>Windows10TeamGeneralConfiguration.MiracastBlocked 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/WirelessProjection/Enabled

#### <a name="windows10teamgeneralconfigurationmiracastchannel"></a>Windows10TeamGeneralConfiguration.MiracastChannel 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/WirelessProjection/Channel

#### <a name="windows10teamgeneralconfigurationmiracastrequirepin"></a>Windows10TeamGeneralConfiguration.MiracastRequirePin 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/WirelessProjection/PINRequired

#### <a name="windows10teamgeneralconfigurationsettingsblockmymeetingsandfiles"></a>Windows10TeamGeneralConfiguration.SettingsBlockMyMeetingsAndFiles 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /Properties/DoNotShowMyMeetingsAndFiles

#### <a name="windows10teamgeneralconfigurationsettingsblocksessionresume"></a>Windows10TeamGeneralConfiguration.SettingsBlockSessionResume 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /Properties/AllowSessionResume

#### <a name="windows10teamgeneralconfigurationsettingsblocksigninsuggestions"></a>Windows10TeamGeneralConfiguration.SettingsBlockSigninSuggestions 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / Eigenschaften/DisableSigninSuggestions

#### <a name="windows10teamgeneralconfigurationsettingsdefaultvolume"></a>Windows10TeamGeneralConfiguration.SettingsDefaultVolume 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / Eigenschaften/DefaultVolume

#### <a name="windows10teamgeneralconfigurationsettingsscreentimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsScreenTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / Eigenschaften/ScreenTimeout

#### <a name="windows10teamgeneralconfigurationsettingssessiontimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSessionTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / Eigenschaften/SessionTimeout

#### <a name="windows10teamgeneralconfigurationsettingssleeptimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSleepTimeoutInMinutes 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: / Eigenschaften/SleepTimeout

#### <a name="windows10teamgeneralconfigurationwelcomescreenbackgroundimageurl"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBackgroundImageUrl 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/Welcome/CurrentBackgroundPath

#### <a name="windows10teamgeneralconfigurationwelcomescreenblockautomaticwakeup"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBlockAutomaticWakeUp 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/Welcome/AutoWakeScreen

#### <a name="windows10teamgeneralconfigurationwelcomescreenmeetinginformation"></a>Windows10TeamGeneralConfiguration.WelcomeScreenMeetingInformation 
**CSP**: ./Vendor/MSFT/SurfaceHub  
**Offset URI**: /InBoxApps/Welcome/MeetingInfoOption

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: /Offboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingFilename
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: /Offboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingBlob 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: /Onboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingFilename 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: /Onboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationallowsamplesharing"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AllowSampleSharing 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: / Configuration/SampleSharing

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationenableexpeditedtelemetryreporting"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.EnableExpeditedTelemetryReporting 
**CSP**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Offset URI**: /Configuration/TelemetryReportingFrequency

#### <a name="windowsdeliveryoptimizationconfigurationdeliveryoptimizationmode"></a>WindowsDeliveryOptimizationConfiguration.DeliveryOptimizationMode 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/DeliveryOptimization/DODownloadMode

#### <a name="windowsidentityprotectionconfigurationenhancedantispoofingforfacialfeaturesenabled"></a>WindowsIdentityProtectionConfiguration.EnhancedAntiSpoofingForFacialFeaturesEnabled 
**CSP**: ./Device/Vendor/MSFT/PassportForWork  
**Offset URI**: /Biometrics/FacialFeaturesUseEnhancedAntiSpoofing

#### <a name="windowsidentityprotectionconfigurationpinexpirationindays"></a>WindowsIdentityProtectionConfiguration.PinExpirationInDays 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/Ablauf

#### <a name="windowsidentityprotectionconfigurationpinlowercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinLowercaseCharactersUsage 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/LowercaseLetters

#### <a name="windowsidentityprotectionconfigurationpinmaximumlength"></a>WindowsIdentityProtectionConfiguration.PinMaximumLength 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/MaximumPINLength

#### <a name="windowsidentityprotectionconfigurationpinminimumlength"></a>WindowsIdentityProtectionConfiguration.PinMinimumLength 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: /{AADTenantId}/Policies/PINComplexity/MinimumPINLength

#### <a name="windowsidentityprotectionconfigurationpinpreviousblockcount"></a>WindowsIdentityProtectionConfiguration.PinPreviousBlockCount 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/den Verlauf

#### <a name="windowsidentityprotectionconfigurationpinrecoveryenabled"></a>WindowsIdentityProtectionConfiguration.PinRecoveryEnabled 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: /{AADTenantId}/Policies/EnablePinRecovery

#### <a name="windowsidentityprotectionconfigurationpinspecialcharactersusage"></a>WindowsIdentityProtectionConfiguration.PinSpecialCharactersUsage 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/SpecialCharacters

#### <a name="windowsidentityprotectionconfigurationpinuppercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinUppercaseCharactersUsage
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: / {AADTenantId} / Richtlinien/PINComplexity/UppercaseLetters

#### <a name="windowsidentityprotectionconfigurationsecuritydevicerequired"></a>WindowsIdentityProtectionConfiguration.SecurityDeviceRequired 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: /{AADTenantId}/Policies/RequireSecurityDevice

#### <a name="windowsidentityprotectionconfigurationunlockwithbiometricsenabled"></a>WindowsIdentityProtectionConfiguration.UnlockWithBiometricsEnabled 
**CSP**: ./Device/Vendor/MSFT/PassportForWork  
**Offset URI**: /Biometrics/UseBiometrics

#### <a name="windowsidentityprotectionconfigurationusecertificatesforonpremisesauthenabled"></a>WindowsIdentityProtectionConfiguration.UseCertificatesForOnPremisesAuthEnabled 
**CSP**: ./Device/Vendor/MSFT/PassportForWork  
**Offset URI**: /{AADTenantId}/Policies/UseCertificateForOnPremAuth

#### <a name="windowsidentityprotectionconfigurationwindowshelloforbusinessblocked"></a>WindowsIdentityProtectionConfiguration.WindowsHelloForBusinessBlocked 
**CSP**: ./Vendor/MSFT/PassportForWork  
**Offset URI**: /{AADTenantId}/Policies/UsePassportForWork

#### <a name="windowskioskconfigurationedgekioskenablepublicbrowsing"></a>WindowsKioskConfiguration.EdgeKioskEnablePublicBrowsing 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureKioskMode

#### <a name="windowskioskconfigurationedgekioskresetafteridletimeinminutes"></a>WindowsKioskConfiguration.EdgeKioskResetAfterIdleTimeInMinutes 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Browser/ConfigureKioskResetAfterIdleTimeout

#### <a name="windowskioskconfigurationkioskbrowserblockedurlexceptions"></a>WindowsKioskConfiguration.KioskBrowserBlockedUrlExceptions 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/BlockedUrlExceptions

#### <a name="windowskioskconfigurationkioskbrowserblockedurls"></a>WindowsKioskConfiguration.KioskBrowserBlockedURLs 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/BlockedUrls

#### <a name="windowskioskconfigurationkioskbrowserdefaulturl"></a>WindowsKioskConfiguration.KioskBrowserDefaultUrl 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/DefaultUrl

#### <a name="windowskioskconfigurationkioskbrowserenableendsessionbutton"></a>WindowsKioskConfiguration.KioskBrowserEnableEndSessionButton 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/EnableEndSessionButton

#### <a name="windowskioskconfigurationkioskbrowserenablehomebutton"></a>WindowsKioskConfiguration.KioskBrowserEnableHomeButton 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/EnableHomeButton

#### <a name="windowskioskconfigurationkioskbrowserenablenavigationbuttons"></a>WindowsKioskConfiguration.KioskBrowserEnableNavigationButtons 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/EnableNavigationButtons

#### <a name="windowskioskconfigurationkioskbrowserrestartonidletimeinminutes"></a>WindowsKioskConfiguration.KioskBrowserRestartOnIdleTimeInMinutes 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/KioskBrowser/KioskBrowserRestartOnIdleTimeInMinutes

#### <a name="windowsupdateforbusinessconfigurationautomaticupdatemode"></a>WindowsUpdateForBusinessConfiguration.AutomaticUpdateMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/AllowAutoUpdate

#### <a name="windowsupdateforbusinessconfigurationautorestartnotificationdismissal"></a>WindowsUpdateForBusinessConfiguration.AutoRestartNotificationDismissal 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/AutoRestartRequiredNotificationDismissal

#### <a name="windowsupdateforbusinessconfigurationbusinessreadyupdatesonly"></a>WindowsUpdateForBusinessConfiguration.BusinessReadyUpdatesOnly 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/BranchReadinessLevel

#### <a name="windowsupdateforbusinessconfigurationdeliveryoptimizationmode"></a>WindowsUpdateForBusinessConfiguration.DeliveryOptimizationMode 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/DeliveryOptimization/DODownloadMode

#### <a name="windowsupdateforbusinessconfigurationdriversexcluded"></a>WindowsUpdateForBusinessConfiguration.DriversExcluded 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/ExcludeWUDriversInQualityUpdate

#### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineForFeatureUpdatesInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartDeadlineForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartDeadline

#### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleForFeatureUpdatesInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartSnoozeScheduleForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartSnoozeSchedule

#### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleForFeatureUpdatesInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartTransitionScheduleForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/EngagedRestartTransitionSchedule

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesDeferralPeriodInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/DeferFeatureUpdatesPeriodInDays

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatespaused"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPaused 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/PauseFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPauseStartDateTime 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/PauseFeatureUpdatesStartTime

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackStartDateTime
**CSP**: N/v - Graph-API nur **Offset URI**: N/v – nur Graph-API

#### <a name="windowsupdateforbusinessconfigurationfeatureupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesWillBeRolledBack 
**CSP**: N/v - Graph-API nur **Offset URI**: N/v – nur Graph-API

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackwindowindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackWindowInDays
**CSP**: N/v - Graph-API nur **Offset URI**: N/v – nur Graph-API

#### <a name="windowsupdateforbusinessconfigurationinstallationschedule"></a>WindowsUpdateForBusinessConfiguration.InstallationSchedule
**CSP**: ./Device/Vendor/MSFT/Policy **Offset URI**: /Config/Update/ActiveHoursStart, /Config/Update/ActiveHoursEnd, /Config/Update/ScheduledInstallDay, /Config/Update/ScheduledInstallTime

#### <a name="windowsupdateforbusinessconfigurationmicrosoftupdateserviceallowed"></a>WindowsUpdateForBusinessConfiguration.MicrosoftUpdateServiceAllowed 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/AllowMUUpdateService

#### <a name="windowsupdateforbusinessconfigurationpreviewbuildsetting"></a>WindowsUpdateForBusinessConfiguration.PreviewBuildSetting 
**CSP**: ./Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/ManagePreviewBuilds

#### <a name="windowsupdateforbusinessconfigurationqualityupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesDeferralPeriodInDays 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/DeferQualityUpdatesPeriodInDays

#### <a name="windowsupdateforbusinessconfigurationqualityupdatespaused"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPaused 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/PauseQualityUpdates

#### <a name="windowsupdateforbusinessconfigurationqualityupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPauseStartDateTime 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/PauseQualityUpdatesStartTime

#### <a name="windowsupdateforbusinessconfigurationqualityupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesRollbackStartDateTime
**CSP**: N/v - Graph-API nur **Offset URI**: N/v – nur Graph-API

#### <a name="windowsupdateforbusinessconfigurationqualityupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesWillBeRolledBack 
**CSP**: N/v - Graph-API nur **Offset URI**: N/v – nur Graph-API

#### <a name="windowsupdateforbusinessconfigurationscheduleimminentrestartwarninginminutes"></a>WindowsUpdateForBusinessConfiguration.ScheduleImminentRestartWarningInMinutes 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/ScheduleImminentRestartWarning

#### <a name="windowsupdateforbusinessconfigurationschedulerestartwarninginhours"></a>WindowsUpdateForBusinessConfiguration.ScheduleRestartWarningInHours 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/ScheduleRestartWarning

#### <a name="windowsupdateforbusinessconfigurationskipchecksbeforerestart"></a>WindowsUpdateForBusinessConfiguration.SkipChecksBeforeRestart 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/SetEDURestart

#### <a name="windowsupdateforbusinessconfigurationupdateweeks"></a>WindowsUpdateForBusinessConfiguration.UpdateWeeks 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/ScheduledInstallEveryWeek, /Config/Update/ScheduledInstallFirstWeek, /Config/Update/ScheduledInstallFourthWeek, /Config/Update/ScheduledInstallSecondWeek, / config/Update / ScheduledInstallThirdWeek

#### <a name="windowsupdateforbusinessconfigurationuserpauseaccess"></a>WindowsUpdateForBusinessConfiguration.UserPauseAccess 
**CSP**: ./Device/Vendor/MSFT/Policy  
**Offset URI**: /Config/Update/SetDisablePauseUXAccess


## <a name="next-steps"></a>Nächste Schritte

- [Übersicht über die Geräte-Konfiguration](device-profiles.md)
- [Konfigurationsdienstanbieter-Referenz](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (öffnet eine andere Dokumentationswebsite)
