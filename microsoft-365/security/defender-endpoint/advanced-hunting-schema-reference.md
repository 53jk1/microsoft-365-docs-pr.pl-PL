---
title: Zaawansowane informacje o schemacie łęgowania
description: Informacje na temat tabel w zaawansowanym schemacie chłoniania, aby zrozumieć dane, na których możesz uruchamiać zapytania wyszukiwania zagrożeń.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, mdatp, microsoft defender atp, microsoft defender for endpoint, wyszukiwanie wdatp, zapytanie, telemetria, informacje o schemacie, kusto, tabela, dane
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 2e45a4ae78d0beb9bc57b72a59b9cf1376ac7da7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468352"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Opis zaawansowanego schematu wyszukiwania w programie Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Zaawansowany [schemat wyszukiwania](advanced-hunting-overview.md) składa się z wielu tabel, które dostarczają informacji o wydarzeniach lub o urządzeniach i innych jednostkach. Aby skutecznie tworzyć zapytania obejmujące wiele tabel, musisz zrozumieć tabele i kolumny w zaawansowanym schemacie wyszukiwania.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>Informacje o schemacie w Defender dla Chmury

Podczas konstruowania zapytań użyj wbudowanego odwołania do schematu, aby szybko uzyskać następujące informacje o każdej tabeli w schemacie:

- **Opis tabel**: typ danych zawartych w tabeli i źródło tych danych.
- **Kolumny**: Wszystkie kolumny w tabeli.
- **Typy akcji**: Możliwe wartości w kolumnie `ActionType` reprezentujące typy zdarzeń obsługiwane przez tabelę. Te wartości są udostępniane tylko w przypadku tabel zawierających informacje o zdarzeniach.
- **Przykładowe zapytanie**: Przykładowe zapytania, które oferują możliwości korzystania z tabeli.

### <a name="access-the-schema-reference"></a>Uzyskiwanie dostępu do informacji o schemacie

Aby szybko uzyskać dostęp do odwołania do schematu, wybierz akcję **Wyświetl** odwołanie obok nazwy tabeli w reprezentacji schematu. Możesz również wybrać pozycję **Odwołanie do schematu** , aby wyszukać tabelę.

:::image type="content" source="images/ah-reference.png" alt-text="Strona zaawansowanego wyszukiwania" lightbox="images/ah-reference.png":::

## <a name="learn-the-schema-tables"></a>Informacje o tabelach schematów

W poniższej tabeli wymieniono wszystkie tabele w zaawansowanym schemacie szukania. Każda nazwa tabeli zawiera linki do stron z opisami nazw kolumn dla tej tabeli.

Nazwy tabel i kolumn są również wymienione w portalu Microsoft 365 Defender, w reprezentacjach schematu na zaawansowanym ekranie wyszukiwania.

<br>

****

|Nazwa tabeli|Opis|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Alerty dotyczące Microsoft 365 Defender |
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|Informacje o urządzeniu, w tym informacje o systemem operacyjnym|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|Właściwości sieciowe urządzeń, w tym karty, adresy IP i MAC, a także połączone sieci i domeny|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|Tworzenie procesów i powiązane zdarzenia|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|Połączenie sieciowe i powiązane zdarzenia|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|Tworzenie plików, modyfikacje i inne zdarzenia systemowe plików|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|Tworzenie i modyfikowanie wpisów rejestru|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|Logowania i inne zdarzenia uwierzytelniania|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|Zdarzenia ładowania biblioteki DLL|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|Wiele typów zdarzeń, w tym zdarzenia wyzwalane przez mechanizmy kontroli zabezpieczeń, takie jak Program antywirusowy Microsoft Defender i exploit protection|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|Informacje o certyfikatach podpisanych plików uzyskanych ze zdarzeń weryfikacji certyfikatu w punktach końcowych|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|Spis oprogramowania zainstalowanego na urządzeniach, w tym informacje o ich wersji i stanie zakończenia pomocy technicznej|
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Luki w zabezpieczeniach oprogramowania na urządzeniach oraz lista dostępnych aktualizacji zabezpieczeń, które mają na celu ochronę przed każdą luką|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Baza wiedzy na temat luk w zabezpieczeniach dostępnych publicznie, w tym tego, czy kod wykorzystujący lukę jest publicznie dostępny|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Zagrożenia & zdarzeń oceny luk w zabezpieczeniach, które wskazują stan różnych konfiguracji zabezpieczeń na urządzeniach|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Baza wiedzy na temat różnych konfiguracji zabezpieczeń używanych przez funkcje zarządzania & zagrożeniami i lukami w zabezpieczeniach do oceny urządzeń; obejmuje mapowania na różne standardy i punkty odniesienia|
|

> [!TIP]
> Użyj [zaawansowanego wyszukiwania w Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview), aby poszukać zagrożeń za pomocą danych z usługi Defender dla punktów końcowych, Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Cloud Apps i Microsoft Defender for Identity. [Włącz Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

Aby dowiedzieć się więcej na temat przenoszenia zaawansowanych przepływów pracy łowiectwo z Ochrona punktu końcowego w usłudze Microsoft Defender do Microsoft 365 Defender zobacz Migrowanie zaawansowanych zapytań [łowiec z Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
- [Wykrywanie niestandardowe — omówienie](overview-custom-detections.md)
- [Zaawansowane zmiany schematu łęgowania](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
