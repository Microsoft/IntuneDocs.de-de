---
title: Fehler und Beschreibungen für Softwareupdates in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Liste der Fehlercodes für den Softwareupdate-Agent in Microsoft Intune – Fehlercodes, symbolische Namen und Fehlerbeschreibungen eingeschlossen.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c73ed7973fa15d796aee1e33efc37191777c222a
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74058055"
---
# <a name="software-update-agent-error-codes-and-descriptions-in-microsoft-intune"></a>Fehlercodes und -beschreibungen für den Softwareupdate-Agent in Microsoft Intune

In der nachfolgenden Tabelle werden Fehlercodes für den Intune-**Update-Agent** aufgelistet. Wenn Sie in dieser Tabelle einen bestimmten Fehlercode nicht finden, überprüfen Sie die [Fehlercodeliste für Windows Update](https://support.microsoft.com/help/938205/windows-update-error-code-list).

|Fehlercode|Symbolischer Name|Weitere Informationen|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|Der Agent wurde erfolgreich beendet.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|Der Vorgang wurde erfolgreich abgeschlossen, aber während der Anwendung der Updates sind Fehler aufgetreten.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Ein Rückruf wurde als "wird später getrennt" markiert, weil die Anforderung, den Vorgang zu trennen, aufgetreten ist, als der Rückruf ausgeführt wurde.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|Das System muss neu gestartet werden, um die Updateinstallation abzuschließen.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|Das Update, das installiert werden soll, ist bereits auf dem System installiert.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|Das Update, das entfernt werden soll, ist nicht auf dem System installiert.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|Das Update wird installiert.|
|**0x80cf0001**|OM_E_NO_SERVICE|Der Dienst kann vom Agent nicht bereitgestellt werden.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|Die maximale Kapazität des Diensts wurde überschritten.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|Eine ID kann nicht gefunden werden.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|Das Objekt konnte nicht initialisiert werden.|
|**0x80cf0007**|OM_E_INVALIDINDEX|Der Index für eine Auflistung ist ungültig.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|Der Schlüssel für das abgefragte Element konnte nicht gefunden werden.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Derzeit wird ein anderer Vorgang ausgeführt, der zu einem Konflikt führt. Einige Vorgänge, z. B. mehrere Installationen, können nicht gleichzeitig durchgeführt werden.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|Der Vorgang wurde abgebrochen.|
|**0x80cf000C**|OM_E_NOOP|Es war kein Vorgang erforderlich.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|Die erforderlichen Informationen konnten vom Agent nicht in den Update-XML-Daten gefunden werden.|
|**0x80cf000E**|OM_E_XML_INVALID|In den Update-XML-Daten wurden vom Agent ungültige Informationen gefunden.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Zirkelverweise zwischen Updates wurden in den Metadaten gefunden.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|Die Updatebeziehungen wurden zu tief verschachtelt, um ausgewertet werden zu können.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|Eine ungültige Updatebeziehung wurde gefunden.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|Ein ungültiger Registrierungswert wurde gelesen.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|Es wurde versucht, ein doppeltes Element zu einer Liste hinzuzufügen.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|Der Aufrufer kann keine Updates installieren, die für die Installation angefordert wurden.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|Es wurde versucht, eine Installation durchzuführen, während eine andere Installation durchgeführt wurde, oder es stand ein erforderlicher Systemneustart aus.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|Der Vorgang wurde nicht durchgeführt, weil keine anwendbaren Updates verfügbar sind.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|Fehler bei diesem Vorgang, weil ein erforderliches Benutzertoken fehlt.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|Ein exklusives Update kann nicht gleichzeitig mit anderen Updates installiert werden.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Es wurde kein Richtlinienwert festgelegt.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Ein Update enthält ungültige Metadaten.|
|**0x80cf001E**|OM_E_SERVICE_STOP|Der Vorgang konnte nicht abgeschlossen werden, da der Dienst oder das System heruntergefahren wurde.|
|**0x80cf001F**|OM_E_NO_CONNECTION|Der Vorgang konnte nicht abgeschlossen werden, da die Netzwerkverbindung nicht verfügbar war.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|Der Vorgang konnte nicht abgeschlossen werden, da kein interaktiver Benutzer angemeldet ist.|
|**0x80cf0021**|OM_E_TIME_OUT|Der Vorgang konnte aufgrund einer Zeitüberschreitung nicht abgeschlossen werden.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|Der Vorgang ist für alle Updates fehlgeschlagen.|
|**0x80cf0024**|OM_E_NO_UPDATE|Es gibt keine Updates.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|Durch Gruppenrichtlinieneinstellungen wurde der Zugriff auf Windows Update verhindert.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|Der Updatetyp ist ungültig.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|Das Update konnte nicht deinstalliert werden, da die Anforderung nicht von einem WSUS-Server stammt.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|Einige Updates fehlten möglicherweise in der Suche, oder eine nicht lizenzierte Anwendung ist auf dem System vorhanden.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Ein deltakomprimiertes Update konnte nicht installiert werden, da die Quelle benötigt wurde.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Ein vollständiges Dateiupdate konnte nicht installiert werden, da die Quelle benötigt wurde.|
|**0x80cf002E**|OM_E_WU_DISABLED|Der Zugriff auf einen nicht verwalteten Server ist nicht zulässig.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|Der Vorgang konnte nicht abgeschlossen werden, da die **DisableWindowsUpdateAccess**-Richtlinie festgelegt war.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|Das Format der Proxyliste ist ungültig.|
|**0x80cf0031**|OM_E_INVALID_FILE|Die Datei hat das falsche Format.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|Die Zeichenfolge der Suchkriterien ist ungültig.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|Das Update konnte nicht heruntergeladen werden.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|Das Update wurde nicht verarbeitet.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|Der Vorgang wurde wegen des aktuellen Objektzustands nicht zugelassen.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|Der Vorgang wird nicht unterstützt.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|Die heruntergeladene Datei weist einen unerwarteten Inhaltstyp auf.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|Der Agent wurde vom Server zu häufig aufgefordert, neu zu synchronisieren.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|Die WUA-Benutzeroberfläche wird nicht unterstützt.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Nur Administratoren können diesen Vorgang für computerspezifische Updates durchführen.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|Die Suchanfrage enthielt einen nicht unterstützten Bereich.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|Die URL verweist nicht auf eine Datei.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|Der angeforderte Vorgang wird nicht unterstützt.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Die Daten sind außerhalb des zulässigen Bereichs.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Die Daten enthalten eine ungültige Version.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|Der Suchaufruf wurde abgeschlossen, einige der Updates konnten jedoch nicht ermittelt werden.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|Der Downloadaufruf wurde abgeschlossen, einige der Updates konnten jedoch nicht heruntergeladen werden.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|Der Installationsaufruf wurde abgeschlossen, einige der Updates konnten jedoch nicht heruntergeladen werden.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Der Windows Update-Cache ist leer, da er nicht initialisiert wurde.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|Die kategoriespezifische Suche wird vom Server nicht unterstützt. Stattdessen muss eine vollständige Katalogsuche durchgeführt werden.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Bei der Autorisierung mit dem Dienst ist ein Problem aufgetreten.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|Es ist keine Route- oder Netzwerkverbindung zum Endpunkt vorhanden.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|Die empfangenen Daten erfüllen die Erwartungen des Datenvertrags nicht.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|Die URL ist ungültig.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|NWS-Laufzeit kann nicht geladen werden.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|Das Proxyauthentifizierungsschema wird nicht unterstützt.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|Die angeforderte Diensteigenschaft ist nicht verfügbar.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|Für das Endpunktanbieter-Plug-In ist eine Onlineaktualisierung erforderlich.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|Eine URL ist für den angeforderten Dienstendpunkt nicht verfügbar.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|Die Verbindung zum Dienstendpunkt wurde abgebrochen.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|Der Vorgang ist ungültig, da Protocol Talker sich in einem unzulässigen Zustand befindet.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|Fehler bei einem Vorgang aufgrund von Ursachen, die nicht in einem anderen Fehlercode behandelt werden.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Einige Updates wurden möglicherweise nicht gefunden, da die Windows Installer-Version älter als Version 3.1 ist.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Einige Updates wurden möglicherweise nicht gefunden, da Windows Installer nicht konfiguriert ist.|
|**0x80cf1003**|OM_E_MSP_DISABLED|Einige Updates wurden möglicherweise nicht gefunden, da in der Richtlinie Windows Installer-Patchen deaktiviert ist.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Ein Update konnte nicht angewendet werden, da die Anwendung für jeden Benutzer einzeln installiert wird.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Eine Anforderung an einen Remoteupdatehandler konnte nicht abgeschlossen werden, da kein Remoteprozess verfügbar ist.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Eine Anforderung an einen Remoteupdatehandler konnte nicht abgeschlossen werden, da der Handler nur lokal verfügbar ist.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Ein Remoteupdatehandler konnte nicht erstellt werden, da bereits einer vorhanden ist.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|Die Anforderung an einen Handler, ein Update zu installieren/deinstallieren, konnte nicht abgeschlossen werden, da vom Update keine Installation/Deinstallation unterstützt wird.|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Ein Vorgang konnte nicht abgeschlossen werden, da der falsche Handler angegeben wurde.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Ein Handlervorgang konnte nicht abgeschlossen werden, da das Update ungültige Metadaten enthält.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Ein Vorgang konnte nicht abgeschlossen werden, da das Zeitlimit vom Installer überschritten wurde. Überprüfen Sie, ob ein Update, das den Eingriff eines Benutzers erfordert, für die Bereitstellung genehmigt wurde. In diesem Fall müssen Sie die Updateinstallationsparameter überarbeiten, damit das Update im Hintergrund installiert werden kann.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Ein Vorgang, der vom Updatehandler durchgeführt wurde, wurde abgebrochen.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Ein Vorgang konnte nicht abgeschlossen werden, da die handlerspezifischen Metadaten ungültig sind.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|Mindestens ein Update konnte vom Installer nicht installiert/deinstalliert werden.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|Das Update konnte vom Updatehandler nicht installiert werden, da es erneut heruntergeladen werden muss.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|Die Benachrichtigung über den Status des Installations-/Deinstallationsvorgangs konnte vom Updatehandler nicht versendet werden.|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|Der Vorgang nach dem Neustart für das Update wird noch ausgeführt.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|Das Ergebnis des Vorgangs nach dem Neustart für das Update konnte nicht ermittelt werden.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|Der Status des Updates, nachdem der Vorgang nach dem Neustart abgeschlossen wurde, ist unerwartet.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|Der Betriebssystem-Dienstbereitstellungsstapel muss aktualisiert werden, bevor dieses Update heruntergeladen oder installiert wird.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Ein Rückruf-Installer hat sich mit einem Fehler zurückgemeldet.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|Die benutzerdefinierte Installersignatur entsprach nicht der Signatur, die vom Update gefordert wird.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|Die Installationskonfiguration wird nicht vom Installer unterstützt.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|Die Zielsitzung für die Installation ist ungültig.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Ein Updatehandlerfehler wird nicht in einem anderen OM_E_UH_&#42;-Code behandelt.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|Die Benutzeroberfläche kann im Nicht-Benutzeroberflächen-Modus nicht angezeigt werden. Windows Update-Clientbenutzeroberflächenmodule können eventuell nicht installiert werden.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Diese Version der exportierten Funktionen der WU-Clientbenutzeroberfläche wird nicht unterstützt.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Ein Fehler in der Benutzeroberfläche ist aufgetreten, der nicht in einem anderen OM_E_AUCLIENT_&#42;-Fehlercode behandelt wird.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Identisch mit **SOAPCLIENT_SOAPFAULT**. Fehler im SOAP-Client, da ein SOAP-Fehler des Fehlercodetyps **OM_E_PT_SOAP_&#42;** aufgetreten ist.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Identisch mit **SOAPCLIENT_PARSEFAULT_ERROR**.  Ein SOAP-Fehler konnte nicht vom SOAP-Client analysiert werden.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Identisch mit **SOAPCLIENT_PARSE_ERROR**.  Die Antwort des Servers konnte vom SOAP-Client nicht analysiert werden.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Identisch mit **SOAP_E_VERSION_MISMATCH**. Vom SOAP-Client wurde ein nicht erkennbarer Namespace für den SOAP-Umschlag gefunden.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Identisch mit **SOAP_E_MUST_UNDERSTAND**. Ein Header konnte vom SOAP-Client nicht interpretiert werden.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Identisch mit **SOAP_E_CLIENT**. Die Nachricht wurde vom SOAP-Client für falsch formatiert befunden. Korrigieren Sie dies, bevor Sie sie erneut versenden.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Identisch mit **SOAP_E_SERVER**. Die SOAP-Nachricht konnte aufgrund eines Serverfehlers nicht verarbeitet werden. Versenden Sie sie später erneut.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|Die Anzahl der Roundtrips an den Server hat den Höchstwert überschritten.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|Fehler bei der Initialisierung, da das Objekt bereits initialisiert wurde.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|Der Computername konnte nicht ermittelt werden.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|Durch die Antwort des Servers wird angezeigt, dass der Server geändert wurde oder dass das Cookie ungültig ist. Aktualisieren Sie den internen Cache, und wiederholen Sie den Vorgang.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Identisch mit **HTTP-Status 400**. Der Server konnte die Anforderung nicht verarbeiten, da die Syntax ungültig ist.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Identisch mit **HTTP-Status 401**. Für die angeforderte Ressource ist eine Benutzerauthentifizierung erforderlich.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Identisch mit **HTTP-Status 403**. Die Anforderung wurde vom Server verstanden, aber die Erfüllung wurde abgelehnt.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Identisch mit **HTTP-Status 404**. Der angeforderte URI (Uniform Resource Identifier) kann vom Server nicht gefunden werden.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Identisch mit **HTTP-Status 405**. Die HTTP-Methode ist nicht zulässig.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Identisch mit **HTTP-Status 407**. Eine Proxyauthentifizierung ist erforderlich.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Identisch mit **HTTP-Status 408**. Das Zeitlimit wurde beim Warten auf die Anforderung vom Server überschritten.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Identisch mit **HTTP-Status 409**. Die Anforderung konnte aufgrund eines Konflikts mit dem aktuellen Zustand der Ressource nicht abgeschlossen werden.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Identisch mit **HTTP-Status 410**. Die angeforderte Ressource ist nicht mehr auf dem Server verfügbar.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Identisch mit **HTTP-Status 500**. Durch einen internen Serverfehler wurde ein Erfüllen der Anforderung verhindert.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Identisch mit **HTTP-Status 500**. Die Funktion, die zum Erfüllen der Anforderung erforderlich ist, wird vom Server nicht unterstützt.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Identisch mit **HTTP-Status 502**. Vom Server wurde in seiner Funktion als Gateway oder Proxy eine ungültige Antwort vom Upstreamserver, auf den der Zugriff erfolgte, um die Anforderung zu erfüllen, empfangen.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Identisch mit **HTTP-Status 503**. Der Dienst ist zurzeit überlastet.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Identisch mit **HTTP-Status 503**. Bei der Anforderung ist eine Zeitüberschreitung aufgetreten, während auf ein Gateway gewartet wurde.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Identisch mit **HTTP-Status 505**. Die HTTP-Protokollversion, die für die Anforderung verwendet wurde, wird vom Server nicht unterstützt.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|Fehler bei diesem Vorgang aufgrund eines geänderten Dateispeicherorts. Aktualisieren Sie den internen Status, und senden Sie die Anforderung erneut.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|Vom Server wurde eine leere Authentifizierungsinformationsliste zurückgegeben.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|Vom Agent konnten keine gültigen Authentifizierungscookies erstellt werden.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Ein Wert einer Konfigurationseigenschaft war falsch.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Ein Wert einer Konfigurationseigenschaft fehlte.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|Die HTTP-Anforderung konnte nicht abgeschlossen werden. Der Grund entsprach keinem **OM_E_PT_HTTP_&#42;** -Fehlercode.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Identisch mit **ERROR_WINHTTP_NAME_NOT_RESOLVED**. Der Proxyserver- oder Zielservername kann nicht aufgelöst werden.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|Die externe CAB-Dateiverarbeitung wurde fehlerhaft abgeschlossen.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|Die externe CAB-Prozessorinitialisierung wurde nicht abgeschlossen.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|Das Format einer Metadatendatei ist ungültig.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|Vom externen CAB-Prozessor wurden ungültige Metadaten gefunden.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Der Dateidigest konnte nicht aus einer externen CAB-Datei extrahiert werden.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Eine externe CAB-Datei konnte nicht dekomprimiert werden.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|Vom externen CAB-Prozessor konnten die Dateispeicherorte nicht abgerufen werden.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Ein Kommunikationsfehler ist aufgetreten, der von keinem anderen **OM_E_PT_&#42;** -Fehlercode abgedeckt wird.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Ein Download-Manager-Vorgang konnte nicht abgeschlossen werden, da die angeforderte Datei keine URL aufweist.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Ein Download-Manager-Vorgang konnte nicht abgeschlossen werden, da der Dateidigest nicht erkannt wurde.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Ein Download-Manager-Vorgang konnte nicht abgeschlossen werden, da von den Dateimetadaten ein unbekannter Hashalgorithmus angefordert wurde.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Ein Download-Manager-Vorgang konnte nicht abgeschlossen werden, da die Netzwerkverbindung nicht verfügbar war.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|Das Update wurde nicht heruntergeladen.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|Ein Download-Manager-Vorgang konnte nicht abgeschlossen werden, da vom Download-Manager keine Verbindung zum Intelligenten Hintergrundübertragungsdienst (Background Intelligent Transfer Service, BITS) hergestellt werden konnte.|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|Fehler bei einem Download-Manager-Vorgang aufgrund eines unbestimmten Transferfehlers des Intelligenten Hintergrundübertragungsdiensts (Background Intelligent Transfer Service, BITS).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|Ein Download muss neu gestartet werden, da sich der Downloadquellspeicherort verändert hat.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|Ein Download muss neu gestartet werden, da der Updateinhalt in einer neuen Revision geändert wurde.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Ein Download-Manager-Fehler ist aufgetreten, der von keinem anderen **OM_E_DM_&#42;** -Fehlercode abgedeckt wird.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|Eine ungültige Ereignisnutzlast wurde angegeben.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|Die Größe, die von der Ereignisnutzlast übermittelt wurde, ist ungültig.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|Der Dienst ist nicht registriert.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|Fehler bei einem Vorgang, da der Agent heruntergefahren wird.|
|**0x80cf8001**|OM_E_DS_INUSE|Fehler bei einem Vorgang, da der Datenspeicher verwendet wurde.|
|**0x80cf8002**|OM_E_DS_INVALID|Die aktuellen und die erwarteten Zustände des Datenspeichers stimmen nicht überein.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|Eine Tabelle ist im Datenspeicher nicht vorhanden.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|Der Datenspeicher enthält eine Tabelle mit unerwarteten Spalten.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|Eine Tabelle konnte nicht geöffnet werden, da sie sich nicht im Datenspeicher befindet.|
|**0x80cf8006**|OM_E_DS_BADVERSION|Die aktuelle und die erwartete Version des Datenspeichers stimmen nicht überein.|
|**0x80cf8007**|OM_E_DS_NODATA|Die Informationen, die angefordert werden, befinden sich nicht im Datenspeicher.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|Im Datenspeicher fehlen benötigte Informationen, oder in einer Tabellenspalte, die einen anderen Wert als Null erfordert, steht eine Null.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|Im Datenspeicher fehlen benötigte Informationen, oder es ist ein Verweis zu fehlenden Lizenzbedingungen, Dateien, lokalisierten Eigenschaften oder verknüpften Zeilen enthalten.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|Das Update wurde nicht verarbeitet, da der Updatehandler nicht erkannt wurde.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|Das Update wurde nicht gelöscht, da es noch immer mit einem oder mehreren Diensten verknüpft ist.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|Der Datenspeicherabschnitt konnte nicht innerhalb der vorgesehenen Zeit gesperrt werden.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|Die Zeile wurde nicht hinzugefügt, da eine vorhandene Zeile denselben primären Schlüssel hat.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Der Datenspeicher konnte nicht initialisiert werden, da er von einem anderen Prozess gesperrt wurde.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|Der Datenspeicher darf im aktuellen Prozess nicht mit COM registriert werden.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Ein Datenspeicherobjekt konnte von einem Vorgang nicht in einem anderen Prozess erstellt werden.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|Vom Server wurde dasselbe Update mit zwei verschiedenen Revisions-IDs an einen Client gesendet.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Ein Vorgang konnte nicht abgeschlossen werden, da der Dienst nicht im Datenspeicher ist.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Ein Vorgang konnte nicht abgeschlossen werden, da die Registrierung des Diensts abgelaufen ist.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|Eine Anforderung, ein Update zu verstecken, wurde abgelehnt, da es sich um ein obligatorisches Update handelt oder da es mit einem Stichtag bereitgestellt wurde.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|Eine Tabelle wurde nicht geschlossen, da sie nicht der Sitzung zugeordnet ist.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|Eine Tabelle wurde nicht geschlossen, da sie nicht der Sitzung zugeordnet ist.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|Die Anforderung, den Dienst zu entfernen oder die Registrierung aufzuheben, wurde abgelehnt, da es sich um einen integrierten Dienst handelt, oder weil "Automatische Updates" nicht auf einen anderen Dienst zurückgreifen kann.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|Die Anfrage wurde abgelehnt, da der Vorgang nicht zulässig ist.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|Das Schema des aktuellen Datenspeichers und das Schema einer Tabelle in einem XML-Sicherungsdokument stimmen nicht überein.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|Vom Datenspeicher wird ein Zurücksetzen der Sitzung gefordert. Geben Sie die Sitzung frei, und wiederholen Sie den Vorgang mit einer neuen Sitzung.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|Ein Datenspeichervorgang konnte nicht abgeschlossen werden, da er mit einer imitierten Identität angefordert wurde.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Ein Datenspeicherfehler ist aufgetreten, der von keinem anderen **OM_E_DS_&#42;** -Code abgedeckt wird.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Eingehende Anforderungen konnten von "Automatische Updates" nicht bedient werden.|
|**0x80cfA004**|OM_E_AU_PAUSED|Eingehende Anforderungen konnten von "Automatische Updates" nicht verarbeitet werden, da "Automatische Updates" angehalten wurde.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Kein unverwalteter Dienst ist bei "Automatische Updates" registriert.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Der Standarddienst, der bei "Automatische Updates" registriert wurde, wurde während der Suche geändert.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Der Benutzer wird bereits von "Automatische Updates" zu einem Neustart aufgefordert.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|In "Automatische Updates" ist ein Fehler aufgetreten, der von keinem anderen **OM_E_AU &#42;** -Code abgedeckt wird.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da ein Ausdruck nicht erkannt wurde.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da ein Ausdruck ungültig war.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da in einem Ausdruck eine falsche Anzahl an Metadatenknoten enthalten war.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da die Version der serialisierten Ausdrucksdaten ungültig ist.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|Die Ausdrucksauswertung konnte nicht initialisiert werden.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da ein Attribut ungültig ist.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Ein Ausdrucksauswertungsvorgang konnte nicht abgeschlossen werden, da der Clusterstatus des Computers nicht bestimmt werden konnte.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Ein Ausdrucksauswertungsfehler ist aufgetreten, der von keinem anderen **OM_E_EE_&#42;** -Fehlercode abgedeckt wird.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|Die Ereigniscachedatei war fehlerhaft.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Die XML-Datei im Ereignis-Namespacedeskriptor konnte nicht analysiert werden.|
|**0x80cfF003**|OM_E_INVALID_EVENT|Die XML-Datei im Ereignis-Namespacedeskriptor ist ungültig.|
|**0x80cfF004**|OM_E_SERVER_BUSY|Vom Server wurde ein Ereignis zurückgewiesen, weil der Server ausgelastet war.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Ein Berichtsfehler ist aufgetreten, der durch keinen anderen Fehlercode abgedeckt ist.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|Bei der Installation ist ein Fehler aufgrund eines ausstehenden obligatorischen Neustarts aufgetreten.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|Das Herunterladen wurde abgebrochen.|