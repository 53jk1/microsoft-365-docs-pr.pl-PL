---
title: Sprawdzanie stanu kondycji czujnika w programie Microsoft Defender dla punktu końcowego
description: Sprawdź kondycję czujnika na urządzeniach, aby sprawdzić, które z nich są nieprawidłowo skonfigurowane, nieaktywne lub nie zgłaszają danych czujnika.
keywords: czujnik, kondycja czujnika, nieprawidłowo skonfigurowane, nieaktywne, bez danych czujnika, dane czujnika, zakłócona komunikacja, komunikacja
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 926e23da7e439aa6035574a13bab2752004dd189
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996766"
---
# <a name="check-sensor-health-state-in-microsoft-defender-for-endpoint"></a>Sprawdzanie stanu kondycji czujnika w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

**Kafelek Urządzenia z problemami z** czujnikiem znajduje się na pulpicie nawigacyjnym Operacje zabezpieczeń. Ten kafelek zawiera informacje o możliwościach poszczególnych urządzeń w celu przekazywania danych czujnika i komunikowania się z usługą Defender for Endpoint. Raportuje ono, ile urządzeń wymaga uwagi i ułatwia zidentyfikowanie urządzeń sprawiających problem oraz podejmie działania w celu poprawienia znanych problemów.

Na kafelku są dwa wskaźniki stanu, które dostarczają informacji o liczbie urządzeń, które nie zgłaszają poprawnie usługi:

- **Nieprawidłowo skonfigurowane —** te urządzenia mogą częściowo zgłaszać dane czujnika do usługi Defender for Endpoint i mogą mieć błędy konfiguracji, które należy poprawić.
- **Nieaktywne** — urządzenia, które w ciągu ostatniego miesiąca przestały zgłaszać się do usługi Defender for Endpoint przez ponad siedem dni.

Kliknięcie dowolnej grupy pokieruje Cię do **listy** Urządzenia przefiltrowane według wybranej opcji.

![Zrzut ekranu przedstawiający kafelek Urządzenia z czujnikami.](images/atp-devices-with-sensor-issues-tile.png)

Na **liście Urządzenia** można filtrować listę stanu kondycji według następującego stanu:

- **Aktywne** — urządzenia, które aktywnie zgłaszają się do usługi Defender for Endpoint.
- **Nieprawidłowo skonfigurowane —** te urządzenia mogą częściowo zgłaszać dane czujnika do usługi Defender for Endpoint, ale mają błędy konfiguracji, które trzeba poprawić. Błędnie skonfigurowane urządzenia mogą mieć jeden lub połączenie następujących problemów:
  - **Brak danych czujnika** — urządzenia przestały wysyłać dane czujnika. Z urządzenia można wyzwolić ograniczone alerty.
  - **Ograniczona komunikacja** — możliwość komunikowania się z urządzeniem jest ograniczona. Wysyłanie plików do dogłębnej analizy, blokowanie plików, odizolowanie urządzenia od sieci i inne akcje, które wymagają komunikacji z urządzeniem, mogą nie działać.
- **Nieaktywne** — urządzenia, które przestały zgłaszać się do usługi Defender for Endpoint.

Możesz również pobrać całą listę w formacie CSV przy użyciu **funkcji Eksportowanie** . Aby uzyskać więcej informacji na temat filtrów, [zobacz Wyświetlanie i organizowanie listy Urządzenia](machines-view-overview.md).

> [!NOTE]
> Wyeksportuj listę w formacie CSV, aby wyświetlić niefiltrowane dane. Plik CSV będzie zawierać wszystkie urządzenia w organizacji, niezależnie od filtrowania zastosowanego w samym widoku i w zależności od tego, jak duża jest Twoja organizacja, może zająć dużo czasu.

![Zrzut ekranu przedstawiający stronę listy Urządzenia.](images/atp-devices-list-page.png)

Po kliknięciu nieprawidłowo skonfigurowanego lub nieaktywnego urządzenia możesz wyświetlić szczegóły urządzenia.

## <a name="see-also"></a>Zobacz też

- [Naprawianie czujników o złej kondycji w programie Defender dla punktu końcowego](fix-unhealthy-sensors.md)
- [Omówienie analizatora klientów](overview-client-analyzer.md)
- [Pobieranie i uruchamianie analizatora klienta](download-client-analyzer.md)
- [Uruchamianie analizatora klienta na Windows](run-analyzer-windows.md)
- [Uruchamianie analizatora klienta w systemie macOS lub Linux](run-analyzer-macos-linux.md)
- [Zbieranie danych na potrzeby zaawansowanego rozwiązywania problemów na Windows](data-collection-analyzer.md)