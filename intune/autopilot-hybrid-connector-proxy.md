---
title: Konfigurieren von Proxyeinstellungen für den Intune-Connector für Active Directory
description: In diesem Artikel wird beschrieben, wie Sie den Intune-Connector für Active Directory für die Verwendung vorhandener lokaler Proxyserver konfigurieren.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f91ec3124d8fab067ec32194a68508762c6cef33
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735261"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Verwenden vorhandener lokaler Proxyserver

In diesem Artikel wird erläutert, wie Sie den Intune-Connector für Active Directory für die Verwendung ausgehender Proxyserver konfigurieren. Er ist für Kunden gedacht, die über Netzwerkumgebungen mit vorhandenen Proxys verfügen.

Weitere Informationen zur Funktionsweise von Connectors finden Sie unter [Grundlegendes zu Azure AD-Anwendungsproxyconnectors](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Umgehen ausgehender Proxys

Connectors verfügen über zugrundeliegende Betriebssystemkomponenten, die ausgehende Anforderungen senden. Diese Komponenten versuchen automatisch, mit dem Web Proxy Auto-Discovery-Dienst (WPAD) einen Proxyserver im Netzwerk zu finden.

Die Betriebssystemkomponenten versuchen, einen Proxyserver zu finden, indem sie eine DNS-Suche nach „wpad.domainsuffix“ durchführen. Wenn die Suche im DNS aufgelöst wurde, erfolgt eine HTTP-Anforderung von „wpad.dat“ an die IP-Adresse. Diese Anforderung wird zum Proxykonfigurationsskript in Ihrer Umgebung. Der Connector verwendet dieses Skript, um einen ausgehenden Proxyserver auszuwählen. Möglicherweise kommt der Datenverkehr des Connectors jedoch trotzdem nicht durch, da auf dem Proxy zusätzliche Konfigurationseinstellungen erforderlich sind.

Sie können den Connector so konfigurieren, dass er Ihren lokalen Proxy umgeht, um sicherzustellen, dass er eine direkte Verbindung zu den Azure-Diensten verwendet. Dieser Ansatz wird empfohlen, solange Ihre Netzwerkrichtlinie dies zulässt, da Sie dadurch eine Konfiguration weniger verwalten müssen.

Bearbeiten Sie die Datei „:\Programme\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config“, um die Verwendung ausgehender Proxys für den Connector zu deaktivieren, und fügen Sie die Proxyadresse und den Proxyport in dem Abschnitt hinzu, der in diesem Codebeispiel gezeigt wird:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Nehmen Sie eine ähnliche Änderung an „C:\Programme\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config“ vor, um sicherzustellen, dass der Connector Updater-Dienst den Proxy ebenfalls umgeht.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Kopieren Sie davor unbedingt die Originaldateien, falls Sie die .config-Standarddateien wiederherstellen müssen.

Nach dem Ändern der Konfigurationsdateien müssen Sie den Intune-Connectordienst neu starten. 

1. Öffnen Sie **services.msc**.
2. Suchen Sie den **Intune ODJConnector-Dienst**, und wählen Sie diesen aus.
3. Klicken Sie auf **Neu starten**.

![Screenshot: Neustart des Diensts](media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Geräten](device-management.md)