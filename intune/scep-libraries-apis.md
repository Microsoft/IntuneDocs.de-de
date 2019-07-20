---
title: APIs zum Onboarding von Zertifizierungsstellen von Drittanbietern
titleSuffix: Microsoft Intune
description: Fügen Sie die SCEP-GitHub-Lösung für Drittanbieter-Zertifizierungsstellen (Certificate Authorities, CA) hinzu oder integrieren Sie diese, um SCEP-Zertifikate für Geräte in Microsoft Intune auszustellen. Diese Lösung umfasst Java- und C#-APIs, die Benachrichtigungen über die erfolgreiche und fehlgeschlagene Ausführung überprüfen, an Intune senden und über eine SSL-Socket-Factory mit Intune kommunizieren. Darüber hinaus können Sie einen Überblick über die Schritte anzeigen, um Ihre SCEP-Konfiguration für Zertifizierungsstellen zu testen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7baa95d6719dfa3161ae6644bbc9351d3f3d9f0
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882379"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Verwenden von APIs zum Hinzufügen von Drittanbieter-Zertifizierungsstellen für SCEP in Intune

Sie können in Microsoft Intune Drittanbieter-Zertifizierungsstellen (Certificate Authorities, CA) hinzufügen und diese Zertifizierungsstellen Zertifikate über das SCEP (Simple Certificate Enrollment-Protokoll) ausstellen und überprüfen lassen. [Hinzufügen der Drittanbieter-Zertifizierungsstelle](certificate-authority-add-scep-overview.md) bietet einen Überblick über diese Funktion und beschreibt die Aufgaben des Administrators in Intune.

Es gibt auch einige Aufgaben für Entwickler, die eine von Microsoft unter GitHub.com veröffentlichte Open-Source-Bibliothek verwenden. Die Bibliothek enthält eine API, die:

- das von Intune dynamisch generierte SCEP-Kennwort überprüft
- Intune über die erstellten Zertifikate auf Geräten benachrichtigt, die SCEP-Anforderungen übermitteln

Bei Verwendung dieser API wird der SCEP-Server Ihres Drittanbieters in die SCEP-Verwaltungslösung von Intune für MDM-Geräte integriert. Die Bibliothek abstrahiert Aspekte wie z.B. Authentifizierung, Dienstidentifizierung und die ODATA Intune-Dienst-API von den zugehörigen Benutzern.

## <a name="scep-management-solution"></a>SCEP-Verwaltungslösung

![Integration von Drittanbieter-Zertifizierungsstellen mittels SCEP in Microsoft Intune](./media/scep-certificate-vendor-integration.png)

Administratoren erstellen mit Intune SCEP-Profile und weisen diese Profile anschließend MDM-Geräten zu. Die SCEP-Profile enthalten Parameter wie die folgenden:

- Die URL des SCEP-Servers
- Das vertrauenswürdige Stammzertifikat der Zertifizierungsstelle
- Zertifikatattribute und Vieles mehr

Geräte, die bei Intune einchecken, werden dem SCEP-Profil zugewiesen und mit diesen Parametern konfiguriert. Intune erstellt ein dynamisch generiertes SCEP-Abfragekennwort, das dem Gerät anschließend zugewiesen wird.

Diese Abfrage enthält Folgendes:

- Das dynamisch generierte Abfragekennwort
- Die Details zu den Parametern, die in der Zertifikatsignieranforderung (Certificate Signing Request, CSR) erwartet werden, die das Gerät für den SCEP-Server ausführt.
- Die Ablaufzeit der Abfrage

Intune verschlüsselt diese Informationen, signiert das verschlüsselte Blob und packt diese Details anschließend in das SCEP-Abfragekennwort.

Geräte, die zur Anforderung eines Zertifikats eine Verbindung mit dem SCEP-Server herstellen, geben anschließend dieses SCEP-Abfragekennwort an. Der SCEP-Server sendet die Zertifikatsignieranforderung und das verschlüsselte SCEP-Abfragekennwort zur Überprüfung an Intune.  Dieses Abfragekennwort und die Zertifikatsignieranforderung müssen die Überprüfung bestehen, damit der SCEP-Server ein Zertifikat für das Gerät ausstellt. Bei der Überprüfung eines SCEP-Abfragekennworts geschieht Folgendes:


- Die Signatur des verschlüsselten Blobs wird überprüft
- Es wird überprüft, ob die Herausforderung abgelaufen ist
- Es wird überprüft, ob das Profil weiterhin für das Gerät vorgesehen ist
- Es wird überprüft, ob die bei der Zertifikatsignieranforderung vom Gerät angeforderten Zertifikateigenschaften den erwarteten Werten entsprechen

Die SCEP-Verwaltungslösung beinhaltet auch die Berichterstellung. Ein Administrator kann Informationen zu dem Bereitstellungsstatus des SCEP-Profils und zu den für die Geräte ausgestellten Zertifikaten abrufen.

## <a name="integrate-with-intune"></a>Integration in Intune

Der Code für die Integration der Bibliothek im Intune-SCEP kann im [GitHub-Repository Microsoft/Intune-Resource-Access](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) heruntergeladen werden.

Für die Integration der Bibliothek in Ihre Produkte müssen die folgenden Schritte ausgeführt werden. Für diese Schritte sind Kenntnisse in der Arbeit mit GitHub-Repositorys und der Erstellung von Projektmappen und Projekten in Visual Studio erforderlich.

1. Registrieren Sie sich, um Benachrichtigungen vom Repository zu erhalten
2. Klonen Sie das Repository oder laden Sie es herunter
3. Wechseln Sie zur erforderlichen Bibliotheksimplementierung im Ordner `\src\CsrValidation` (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) )
4. Erstellen Sie die Bibliothek mithilfe der Anweisungen in der README-Datei
5. Schließen Sie die Bibliothek in das Projekt ein, in dem Ihr SCEP-Server erstellt wird
6. Führen Sie auf dem SCEP-Server die folgenden Schritte aus:

    - Ermöglichen Sie dem Administrator, [den Azure-Anwendungsbezeichner, den Azure-Anwendungsschlüssel und die Mandanten-ID](#onboard-scep-server-in-azure) (in diesem Artikel) zu konfigurieren, welche die Bibliothek für die Authentifizierung verwendet. Administratoren sollten den Azure-Anwendungsschlüssel aktualisieren können.
    - Identifizieren Sie SCEP-Anforderungen, die ein in Intune generiertes SCEP-Kennwort enthalten
    - Überprüfen Sie mithilfe der Bibliothek **Anforderungs-API überprüfen** die in Intune generierten SCEP-Kennwörter
    - Informieren Sie Intune über die Benachrichtigungs-APIs der Bibliothek über Zertifikate, die für SCEP-Anforderungen ausgestellt wurden und über von Intune generierte SCEP-Kennwörter verfügen. Darüber hinaus sollten Sie Intune auch über Fehler benachrichtigen, die bei der Verarbeitung dieser SCEP-Anforderungen auftreten.
    - Vergewissern Sie sich, dass der Server genügend Informationen protokolliert, um Administratoren bei der Behebung von Problemen unterstützen zu können

7. Führen Sie die [Integrationstests](#integration-testing) (in diesem Artikel) aus, und beheben Sie sämtliche Probleme
8. Stellen Sie eine schriftliche Anleitung für den Kunden bereit, in dem Folgendes erläutert wird:

    - Vorgehensweise beim Integrieren des SCEP-Servers in das Azure-Portal
    - Vorgehensweise beim Abrufen des Azure-Anwendungsbezeichners und des Azure-Anwendungsschlüssels, die für die Konfiguration der Bibliothek erforderlich sind

### <a name="onboard-scep-server-in-azure"></a>Integrieren des SCEP-Servers in Azure

Für die Authentifizierung bei Intune benötigt der SCEP-Server einen Azure-Anwendungsbezeichner, einen Azure-Anwendungsschlüssel und eine Mandanten-ID. Darüber hinaus benötigt der SCEP-Server eine Autorisierung für den Zugriff auf die Intune-API.

Zum Abrufen dieser Daten meldet sich der Administrator des SCEP-Servers beim Azure-Portal an, registriert die Anwendung, erteilt der Anwendung die Berechtigung für die **Microsoft Intune-API\Überprüfung der SCEP-Herausforderung**, erstellt einen Schlüssel für die Anwendung und lädt anschließend den Anwendungsbezeichner, den zugehörigen Schlüssel und die Mandanten-ID herunter.

Eine Anleitung zur Registrierung einer Anwendung sowie zum Abrufen der Bezeichner und Schlüssel finden Sie unter [Verwenden des Portals zum Erstellen einer AAD-Anwendung und eines Dienstprinzipals für den Zugriff auf Ressourcen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>API der Java-Bibliothek

Die Java-Bibliothek wird als Maven-Projekt implementiert, welche die zugehörigen Abhängigkeiten während der Erstellung abruft. Die API wird unter dem Namespace `com.microsoft.intune.scepvalidation` von der Klasse `IntuneScepServiceClient` implementiert.

#### <a name="intunescepserviceclient-class"></a>IntuneScepServiceClient-Klasse

Die `IntuneScepServiceClient`-Klasse enthält die Methoden, die der SCEP-Dienst zur Überprüfung von SCEP-Kennwörtern, um Intune über erstellte Zertifikate zu benachrichtigen, sowie zur Auflistung sämtlicher Fehler verwendet.

##### <a name="intunescepserviceclient-constructor"></a>IntuneScepServiceClient-Konstruktor

Signatur:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Beschreibung:

Instanziiert und konfiguriert ein `IntuneScepServiceClient`-Objekt.

Parameter:

    - configProperties: Das Eigenschaftenobjekt mit Informationen zur Clientkonfiguration

Die Konfiguration muss folgende Eigenschaften enthalten:

    - AAD_APP_ID = „Der während des Integrationsprozesses abgerufene Azure-Anwendungsbezeichner“
    - AAD_APP_KEY = „Der während des Integrationsprozesses abgerufene Azure-Anwendungsschlüssel“
    - TENANT = „Die während des Integrationsprozesses abgerufene Mandanten-ID“
    - PROVIDER_NAME_AND_VERSION = „Informationen zum Identifizieren Ihres Produkts und der zugehörigen Version“
    
Wenn Ihre Lösung eher einen Proxy mit oder ohne Authentifizierung erfordert, können Sie die folgenden Eigenschaften hinzufügen:

    - PROXY_HOST="The host the proxy is hosted on." (Der Host, auf dem der Proxy gehostet wird)
    - PROXY_PORT="The port the proxy is listening on." (Der Port, auf den der Proxy hört)
    - PROXY_USER="The username to use if proxy uses basic authentication." (Der zu verwendende Benutzername, wenn der Proxy Standardauthentifizierung verwendet)
    - PROXY_PASS="The password to use if proxy uses basic authentication." (Das zu verwendende Kennwort, wenn der Proxy Standardauthentifizierung verwendet)

Löst aus:

    - IllegalArgumentException: Wird ausgelöst, wenn der Konstruktor ohne ordnungsgemäßes Eigenschaftenobjekt ausgeführt wird.

> [!IMPORTANT]
> Es wird empfohlen, eine Instanz dieser Klasse zu instanziieren und diese für die Verarbeitung mehrerer SCEP-Anforderungen zu verwenden. Auf diese Weise wird der Mehraufwand reduziert, da Authentifizierungstoken und Informationen zur Dienstidentifizierung zwischengespeichert werden.

**Sicherheitshinweise**  
Der Implementer des SCEP-Servers muss die Daten, die in die Konfigurationseigenschaften eingegeben wurden und im Speicher erhalten bleiben, vor Verfälschungen und Veröffentlichungen schützen. Es wird empfohlen, zum Schutz der Informationen ordnungsgemäße ACLs und eine ordnungsgemäße Verschlüsselung zu verwenden.

##### <a name="validaterequest-method"></a>ValidateRequest-Methode

Signatur:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Beschreibung:

Überprüft eine SCEP-Zertifikatanforderung.

Parameter:

    - transactionId: Die Transaktions-ID des SCEP
    - certificateRequest: DER-codierte PKCS #10-Zertifikatanforderung mit Base64-Codierung als Zeichenfolge

Löst aus:

    - IllegalArgumentException: Dieser Parameter wird ausgelöst, wenn er mit einem ungültigen Parameter aufgerufen wird
    - IntuneScepServiceException: Wird ausgelöst, wenn festgestellt wird, dass die Zertifikatanforderung ungültig ist
    - Exception: Wird ausgelöst, wenn ein unerwarteter Fehler auftritt

> [!IMPORTANT]
> Von dieser Methode ausgelöste Ausnahmen sollten vom Server protokolliert werden. Beachten Sie, dass die `IntuneScepServiceException`-Eigenschaften detaillierte Informationen darüber aufweisen, weshalb die Überprüfung der Zertifikatanforderung fehlgeschlagen ist.

**Sicherheitshinweise**  

- Wenn diese Methode eine Ausnahme auslöst, darf der SCEP-Server **kein** Zertifikat für den Client ausstellen.
- Fehler bei der Überprüfung der SCEP-Zertifikatanforderung weisen möglicherweise auf ein Problem in der Intune-Infrastruktur hin. Alternativ könnten sie auch darauf hinweisen, dass ein Angreifer versucht, ein Zertifikat abzurufen.

##### <a name="sendsuccessnotification-method"></a>SendSuccessNotification-Methode

Signatur:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Beschreibung:

Benachrichtigt Intune darüber, dass ein Zertifikat als Teil der Verarbeitung einer SCEP-Anforderung erstellt wurde.

Parameter:

    - transactionId: Die Transaktions-ID des SCEP
    - certificateRequest: DER-codierte PKCS #10-Zertifikatanforderung mit Base64-Codierung als Zeichenfolge
    - certThumprint: Ein Fingerabdruck des bereitgestellten Zertifikats
    - CertSerialNumber: Die Seriennummer des bereitgestellten Zertifikats
    - CertExpirationDate: Das Ablaufdatum des bereitgestellten Zertifikats. Die DateTime-Zeichenfolge sollte als UTC-Webzeit (YYYY-MM-DDThh:mm:ss.sssTZD) formatiert werden (ISO 8601).
    - certIssuingAuthority: Der Name der Stelle, die das Zertifikat ausgestellt hat

Löst aus:

    - IllegalArgumentException: Dieser Parameter wird ausgelöst, wenn er mit einem ungültigen Parameter aufgerufen wird
    - IntuneScepServiceException: Wird ausgelöst, wenn festgestellt wird, dass die Zertifikatanforderung ungültig ist
    - Exception: Wird ausgelöst, wenn ein unerwarteter Fehler auftritt

> [!IMPORTANT]
> Von dieser Methode ausgelöste Ausnahmen sollten vom Server protokolliert werden. Beachten Sie, dass die `IntuneScepServiceException`-Eigenschaften detaillierte Informationen darüber aufweisen, weshalb die Überprüfung der Zertifikatanforderung fehlgeschlagen ist.

**Sicherheitshinweise**

- Wenn diese Methode eine Ausnahme auslöst, darf der SCEP-Server **kein** Zertifikat für den Client ausstellen.
- Fehler bei der Überprüfung der SCEP-Zertifikatanforderung weisen möglicherweise auf ein Problem in der Intune-Infrastruktur hin. Alternativ könnten sie auch darauf hinweisen, dass ein Angreifer versucht, ein Zertifikat abzurufen.

##### <a name="sendfailurenotification-method"></a>SendFailureNotification-Methode

Signatur:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Beschreibung:

Benachrichtigt Intune darüber, dass bei der Verarbeitung einer SCEP-Anforderung ein Fehler aufgetreten ist. Diese Methode sollte nicht bei Ausnahmen aufgerufen werden, die von den Methoden dieser Klasse ausgelöst werden.

Parameter:

    - transactionId: Die Transaktions-ID des SCEP
    - certificateRequest: DER-codierte PKCS #10-Zertifikatanforderung mit Base64-Codierung als Zeichenfolge
    - hResult: Ein Win32-Fehlercode, der den aufgetretenen Fehler am besten beschreibt. Siehe [Win32-Fehlercodes](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription: Eine Beschreibung des aufgetretenen Fehlers

Löst aus:

    - IllegalArgumentException: Dieser Parameter wird ausgelöst, wenn er mit einem ungültigen Parameter aufgerufen wird
    - IntuneScepServiceException: Wird ausgelöst, wenn festgestellt wird, dass die Zertifikatanforderung ungültig ist
    - Exception: Wird ausgelöst, wenn ein unerwarteter Fehler auftritt

> [!IMPORTANT]
> Von dieser Methode ausgelöste Ausnahmen sollten vom Server protokolliert werden. Beachten Sie, dass die `IntuneScepServiceException`-Eigenschaften detaillierte Informationen darüber aufweisen, weshalb die Überprüfung der Zertifikatanforderung fehlgeschlagen ist.

**Sicherheitshinweise**

- Wenn diese Methode eine Ausnahme auslöst, darf der SCEP-Server **kein** Zertifikat für den Client ausstellen.
- Fehler bei der Überprüfung der SCEP-Zertifikatanforderung weisen möglicherweise auf ein Problem in der Intune-Infrastruktur hin. Alternativ könnten sie auch darauf hinweisen, dass ein Angreifer versucht, ein Zertifikat abzurufen.

##### <a name="setsslsocketfactory-method"></a>SetSslSocketFactory-Methode

Signatur:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Beschreibung:

Mit dieser Methode können Sie den Client darüber informieren, dass dieser bei der Kommunikation mit Intune die angegebene SSL-Socket-Factory verwenden muss (anstelle des Standardwerts).

Parameter:

    - factory: Die SSL-Socket-Factory, die der Client für HTTPS-Anforderungen verwenden sollte

Löst aus:

    - IllegalArgumentException: Dieser Parameter wird ausgelöst, wenn er mit einem ungültigen Parameter aufgerufen wird

> [!NOTE]
> Die SSL-Socket-Factory muss ggf. festgelegt werden, bevor die anderen Methoden dieser Klasse ausgeführt werden.

## <a name="integration-testing"></a>Testen der Integration

Das Überprüfen und Testen, ob Ihre Lösung ordnungsgemäß in Intune integriert wurde, ist ein Muss. Im Folgenden wird eine Übersicht über die Schritte aufgeführt:

1. Richten Sie ein [Intune-Testkonto](account-sign-up.md) ein.
2. Integrieren Sie den [SCEP-Server in das Azure-Portal](#onboard-scep-server-in-azure) (in diesem Artikel).
3. [Konfigurieren Sie den SCEP-Server](certificates-scep-configure.md) mit den IDs und dem Schlüssel, die bei der Integration Ihres SCEP-Servers erstellt wurden.
4. [Registrieren Sie Geräte](device-enrollment.md), um die Szenarios in der [Matrix zum Testen von Szenarios](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv) zu testen.
5. [Erstellen Sie ein vertrauenswürdiges Stammzertifikatprofil](certificates-scep-configure.md) für Ihre Zertifizierungsstelle.
6. Erstellen Sie SCEP-Profile, um die in der [Matrix zum Testen von Szenarios](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv) aufgeführten Szenarios zu testen.
7. [Weisen Sie die Profile](device-profile-assign.md) Benutzern zu, die ihre Geräte registriert haben.
8. Warten Sie, bis die Geräte mit Intune synchronisiert wurden. Alternativ können Sie die Geräte auch [manuell synchronisieren](device-sync.md).
9. Vergewissern Sie sich, dass das vertrauenswürdige Stammzertifikat und [SCEP-Profile auf den Geräten bereitgestellt wurden](device-profile-monitor.md).
10. Vergewissern Sie sich, dass das vertrauenswürdige Stammzertifikat auf allen Geräten installiert wurde.
11. Vergewissern Sie sich, dass die SCEP-Zertifikate für die zugewiesenen Profile auf allen Geräten installiert wurden.
12. Vergewissern Sie sich, dass die Eigenschaften der installierten Zertifikate mit den im SCEP-Profil festgelegten Eigenschaften übereinstimmen.
13. Vergewissern Sie sich, dass die ausgestellten Zertifikate in der Intune-Konsole ordnungsgemäß aufgeführt werden

## <a name="see-also"></a>Siehe auch

- [Übersicht: Hinzufügen von Drittanbieter-Zertifizierungsstellen](certificate-authority-add-scep-overview.md)
- [Einrichten von Intune](setup-steps.md)
- [Geräteregistrierung](device-enrollment.md)
- [Konfigurieren von SCEP-Zertifikatprofilen](certificates-scep-configure.md#create-a-scep-certificate-profile) (für dieses Szenario wird die Einrichtung von Microsoft NDES Server\Connector nicht verwendet)
