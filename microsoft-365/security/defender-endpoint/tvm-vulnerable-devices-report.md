---
title: Raport Urządzenia narażone na nie — Zarządzanie zagrożeniami i lukami
description: Raport przedstawiający podatny na trendy urządzeń i bieżące statystyki. Celem jest zrozumienie odchyłego i zakresu ekspozycji urządzenia.
keywords: Program Microsoft Defender for Endpoint-tvm narażona na urządzenia, Program Microsoft Defender for Endpoint, tvm, zmniejszanie zagrożenia & luki w zabezpieczeniach, zmniejszanie zagrożeń i luki w zabezpieczeniach, monitorowanie konfiguracji zabezpieczeń
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1f096433534abb91b9cb14b8db2737dacf566624
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997292"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>Raport Urządzenia narażone na nie — Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Raport przedstawia wykresy i wykresy słupkowe ze podatnymi na trendy urządzeń i bieżącymi statystykami. Celem jest zrozumienie odchyłego i zakresu ekspozycji urządzenia.

Uzyskaj dostęp do raportu w portalu Microsoft 365 Defender, przechodząc do **tematu Raporty > na urządzeniach, które są narażone na zagrożenia**

Istnieją dwie kolumny:

- Trendy (w czasie). Może pokazywać ostatnie 30 dni, 3 miesiące, 6 miesięcy lub niestandardowy zakres dat.
- Stan (bieżące informacje)

**Filtr**: Dane można filtrować według poziomów luk w zabezpieczeniach, wykorzystania możliwości, wieku luki w zabezpieczeniach, platformy systemu operacyjnego, platformy systemu Windows 10 lub Windows 11 lub grupy urządzeń.

**Przechodzenie do** szczegółów: Jeśli chcesz uzyskać szczegółowe informacje, wybierz odpowiedni wykres słupkowy, aby wyświetlić przefiltrowane listę urządzeń na stronie Spis urządzeń. W tym miejscu możesz wyeksportować listę.

## <a name="severity-level-graphs"></a>Wykresy poziomu ważności

Każde urządzenie jest liczone tylko raz w zależności od najpowszechniejszej luki w zabezpieczeniach, która została znaleziona na tym urządzeniu.

:::image type="content" alt-text="Jeden wykres przedstawiający bieżące poziomy luk w zabezpieczeniach urządzeń, a jeden wykres przedstawiający poziomy w czasie." source="images/tvm-report-severity.png" lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>Exploit availability graphs

Każde urządzenie jest liczone tylko raz na podstawie najwyższego poziomu znanego wykorzystania.

:::image type="content" alt-text="Jeden wykres przedstawiający bieżącą dostępność urządzeń, a jeden wykres przedstawiający dostępność w czasie." source="images/tvm-report-exploit-availability.png" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>Wykresy wiekowe luk w zabezpieczeniach

Każde urządzenie jest liczone tylko raz pod najstarszą datą publikacji bez luk. Starsze luki w zabezpieczeniach są większe w przypadku wykorzystania.

:::image type="content" alt-text="Jeden wykres przedstawiający bieżący wiek luk w zabezpieczeniach urządzenia, a jeden wykres przedstawiający wiek z czasem." source="images/tvm-report-age.png" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>Najbędsze urządzenia są narażone na wykresy platform systemu operacyjnego

Liczba urządzeń w poszczególnych systemach operacyjnych, które są udostępniane z powodu luk w oprogramowaniu.

:::image type="content" alt-text="Jeden wykres przedstawiający bieżące urządzenia, na które jest atna platforma systemu operacyjnego, a jeden wykres przedstawiający urządzenia, na których są narażone platformy systemu operacyjnego, w czasie." source="images/tvm-report-os.png" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>Najbędsze urządzenia Windows wykresy wersji

Liczba urządzeń na poszczególnych urządzeniach Windows 10 lub Windows 11, które są widoczne ze względu na narażenie aplikacji lub systemu operacyjnego.

![Jeden wykres przedstawiający obecnie narażone urządzenia według Windows 10 wersji, a jeden wykres przedstawiający narażone urządzenia według Windows 10 wersji w czasie.](images/tvm-report-version.png)lightbox="images/tvm-report-version.png":::

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)