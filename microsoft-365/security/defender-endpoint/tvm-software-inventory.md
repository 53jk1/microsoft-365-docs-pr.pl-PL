---
title: Spis oprogramowania w Zarządzanie zagrożeniami i lukami
description: Strona spisu oprogramowania dla Ochrona punktu końcowego w usłudze Microsoft Defender firmy Zarządzanie zagrożeniami i lukami pokazuje, ile luk i błędów zostało wykrytych w oprogramowaniu.
keywords: Zarządzanie zagrożeniami i lukami, Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender spisu oprogramowania, Ochrona punktu końcowego w usłudze Microsoft Defender zagrożenia & zarządzanie lukami w zabezpieczeniach, Ochrona punktu końcowego w usłudze Microsoft Defender zagrożenia & zarządzanie lukami w zabezpieczeniach spis oprogramowania, Ochrona punktu końcowego w usłudze Microsoft Defender spis oprogramowania telewizyjnego, spis oprogramowania telewizyjnego
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cbd4634e779fe2bf853aaf014b59b1e7e1c1928f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470048"
---
# <a name="software-inventory---threat-and-vulnerability-management"></a>Spis oprogramowania — Zarządzanie zagrożeniami i lukami


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Spis oprogramowania w Zarządzanie zagrożeniami i lukami zawiera listę znanego oprogramowania w organizacji. Filtr domyślny na stronie spisu oprogramowania wyświetla całe oprogramowanie z oficjalnymi wyliczeniami wspólnej platformy [(CPE).](https://nvd.nist.gov/products/cpe) Widok zawiera takie szczegóły, jak imię i nazwisko dostawcy, liczba chłonięć, zagrożenia i liczba ujawnionych urządzeń.

Możesz usunąć filtr **DOSTĘPNY WWK** , aby uzyskać dalszą widoczność i zwiększyć zakres wyszukiwania we wszystkich zainstalowanych oprogramowaniu w organizacji. Oznacza to, że wszystkie oprogramowanie, łącznie z oprogramowaniem bez cpe, będzie teraz wyświetlane na liście zasobów oprogramowania.

> [!NOTE]
> Ze względu na to, że firmy zarządzanie lukami w zabezpieczeniach są używane do identyfikowania oprogramowania i ewentualnej luki w zabezpieczeniach, nawet jeśli produkty oprogramowania bez niego będą wyświetlane na stronie spisu oprogramowania, nie będą one obsługiwane przez firmę Zarządzanie zagrożeniami i lukami  oraz informacje, takie jak luki, liczba dostępnych urządzeń i słabe urządzenia, nie będą dla nich dostępne.

## <a name="how-it-works"></a>Jak to działa

W obszarze odnajdowania używamy tego samego zestawu sygnałów, które są odpowiedzialne za wykrywanie i ocenę luk w zabezpieczeniach podczas wykrywania i Ochrona punktu końcowego w usłudze Microsoft Defender [wykrywania i reagowania](overview-endpoint-detection-response.md).

Ponieważ jest to czas rzeczywisty, w ciągu kilku minut podczas ich odkrywania będą luki w zabezpieczeniach. Aparat automatycznie pobiera informacje z wielu kanałów informacyjnych zabezpieczeń. W rzeczywistości zobaczysz, czy dane oprogramowanie jest połączone z kampanią zagrożenia na żywo. Udostępnia również link do raportu analizy zagrożeń, gdy tylko będzie dostępny.

## <a name="navigate-to-the-software-inventory-page"></a>Przechodzenie do strony spisu oprogramowania

Aby uzyskać dostęp do strony spisu **oprogramowania, wybierz** pozycję Spis oprogramowania Zarządzanie zagrożeniami i lukami menu nawigacji w portalu Microsoft 365 Defender [sieci Web](portal-overview.md).

Wyświetlaj oprogramowanie na poszczególnych urządzeniach na poszczególnych stronach z [listy urządzeń](machines-view-overview.md).

> [!NOTE]
> Jeśli wyszukuje oprogramowanie za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender wyszukiwanie globalne, pamiętaj o włoceniu podkreślenia zamiast spacji. Aby na przykład uzyskać najlepsze wyniki wyszukiwania, wpisz "windows_10" lub "windows_11" zamiast "Windows 10" lub "Windows 11".

## <a name="software-inventory-overview"></a>Omówienie spisu oprogramowania

**Zostanie otwarta** strona Spis oprogramowania z listą oprogramowania zainstalowanego w Twojej sieci, łącznie z nazwą dostawcy, odnalezionymi wadami, zagrożeniami z nimi skojarzonymi, ujawnionymi urządzeniami, wpływem na ocenę ekspozycji i tagami.

Domyślnie widok jest filtrowany według **kodu produktu (CPE): Dostępny**. Widok listy można również filtrować na podstawie wad oprogramowania, zagrożeń z nimi związanych oraz znaczników, takich jak informacje o tym, czy oprogramowanie zakończyło wsparcie techniczne.

:::image type="content" source="images/tvm-software-inventory.png" alt-text="Strona startowa spisu oprogramowania" lightbox="images/tvm-software-inventory.png":::

Wybierz oprogramowanie, które chcesz zbadać. Zostanie otwarty panel wysuwu z bardziej zwartym widokiem informacji na stronie. Możesz przejść do bardziej dogłębnego badania i wybrać pozycję **Otwórz** stronę oprogramowania lub oflagować wszelkie niespójności techniczne, wybierając pozycję Zgłoś nieścisłości.

### <a name="software-that-isnt-supported"></a>Oprogramowanie, które nie jest obsługiwane

Oprogramowanie, które nie jest obecnie obsługiwane przez zagrożenia & zarządzanie lukami w zabezpieczeniach, może się znaleźć na stronie spisu oprogramowania. Ponieważ nie jest to obsługiwane, dostępne będą tylko ograniczone dane. Filtruj według nieobsługiwanego oprogramowania za pomocą opcji "Niedostępne" w sekcji "Brak"

:::image type="content" source="images/tvm-unsupported-software-filter.png" alt-text="Filtr Nieobsługiwane oprogramowanie" lightbox="images/tvm-unsupported-software-filter.png":::

Poniższe informacje oznaczają, że oprogramowanie nie jest obsługiwane:

- Pole Brak wskazuje na "Niedostępne"
- W polu Dostępne urządzenia jest pokazana kreska
- Tekst informacyjny dodany na panelu bocznym i na stronie oprogramowania
- Strona oprogramowania nie będzie mieć zaleceń dotyczących zabezpieczeń, wykrytych luk ani sekcji osi czasu zdarzeń

## <a name="software-inventory-on-devices"></a>Spis oprogramowania na urządzeniach

Z Microsoft 365 Defender nawigacji portalu przejdź do **[spisu urządzeń](machines-view-overview.md)**. Wybierz nazwę urządzenia, aby otworzyć stronę urządzenia (na przykład Komputer1), a następnie wybierz kartę  Spis oprogramowania, aby wyświetlić listę wszystkich znanych oprogramowania na urządzeniu. Wybierz konkretną pozycję oprogramowania, aby otworzyć wysuwne okno wysuwu z konkretną informacją.

Oprogramowanie może być widoczne na poziomie urządzenia, nawet jeśli nie jest obecnie obsługiwane przez Zarządzanie zagrożeniami i lukami. Jednak dostępne będą tylko ograniczone dane. Dowiesz się, czy oprogramowanie nie jest obsługiwane, ponieważ w kolumnie "Brak" będzie on zawierał "Niedostępne".

Oprogramowanie bez cpe może być również wyświetlane w tym spisie oprogramowania dla określonych urządzeń.

### <a name="software-evidence"></a>Dowód oprogramowania

Zapoznaj się z dowodami wykrycia określonego oprogramowania na urządzeniu z rejestru, dysku lub obu tych danych. Można ją znaleźć na dowolnym urządzeniu w spisie oprogramowania urządzenia.

Wybierz nazwę oprogramowania, aby otworzyć wysuwne informacje, a następnie odszukaj sekcję "Dowód oprogramowania".

:::image type="content" source="images/tvm-software-evidence.png" alt-text="Lista Windows 10 z listy urządzeń" lightbox="images/tvm-software-evidence.png":::

## <a name="software-pages"></a>Strony oprogramowania

Strony oprogramowania można wyświetlać na kilka sposobów:

- Strona spisu oprogramowania > Wybieranie nazwy oprogramowania > Wybieranie **strony Otwórz oprogramowanie w** wysuwanych listach
- [Strona Zalecenia dotyczące](tvm-security-recommendation.md) zabezpieczeń > wybierz zalecenie > Wybierz **pozycję Otwórz stronę oprogramowania w** wysuwanych oknach
- Strona osi [czasu zdarzenia >](threat-and-vuln-mgt-event-timeline.md) Wybierz zdarzenie > Zaznacz nazwę oprogramowania z hiperlinkiem (na przykład Visual Studio 2017) w sekcji "Składnik pokrewny" w wysuwanych elementach

 Zostanie wyświetlone pełnej strony ze wszystkimi szczegółami określonego oprogramowania i następującymi informacjami:

- Panel boczny z informacjami o dostawcach, części oprogramowania w organizacji (w tym liczba urządzeń, na których jest zainstalowany, i ujawnione urządzenia, które nie są poprawiane), informacje o tym, czy są dostępne i wykorzystujące, oraz wpływ na ocenę ekspozycji.
- Wizualizacje danych przedstawiające liczbę i ważność luk i błędnej konfiguracji. Ponadto wykresy z liczbą ujawnionych urządzeń.
- Karty z informacjami, takimi jak:
  - Odpowiednie zalecenia dotyczące bezpieczeństwa w przypadku wskazanych luk i luk.
  - Nazwane życiorysy wykrytych luk.
  - Urządzenia, na których jest zainstalowane oprogramowanie (wraz z nazwą urządzenia, domeną, systemem operacyjnym i innymi).
  - Lista wersji oprogramowania (w tym liczba urządzeń, na których jest zainstalowana wersja, liczba wykrytych luk i nazwy zainstalowanych urządzeń).

    :::image type="content" source="images/tvm-software-page-example.png" alt-text="The Visual Studio 2017 with the software details,  jego słabe, exposed devices, and more" lightbox="images/tvm-software-page-example.png":::

## <a name="report-inaccuracy"></a>Nieścisłości raportu

Zgłoś nieścisłości, gdy zostaną podane nieprawidłowe informacje o lukach w zabezpieczeniach i wyniki testów.

1. Otwórz wysuwne okno wysuwu oprogramowania na stronie Spis oprogramowania.
2. Wybierz **pozycję Nieścisłości raportu**.
3. W wysuwanych okienkach wybierz problem, który chcesz zgłosić:

    - Szczegóły oprogramowania są nieprawidłowe
    - oprogramowanie nie jest zainstalowane na żadnym urządzeniu w mojej organizacji
    - liczba zainstalowanych lub ujawnionych urządzeń jest nieprawidłowa

4. Wypełnij wymagane szczegóły dotyczące nieścisłości. Zależy to od tego, który problem jest zgłaszany.

![Nieścisłości raportu](images/report-inaccuracy-software.png)

5. Wybierz **pozycję Prześlij**. Twoja opinia zostanie natychmiast przesłana do Zarządzanie zagrożeniami i lukami ekspertów.

## <a name="related-articles"></a>Artykuły pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md)
- [Oś czasu zdarzenia](threat-and-vuln-mgt-event-timeline.md)
- [Wyświetlanie i organizowanie listy Ochrona punktu końcowego w usłudze Microsoft Defender Urządzenia](machines-view-overview.md)
