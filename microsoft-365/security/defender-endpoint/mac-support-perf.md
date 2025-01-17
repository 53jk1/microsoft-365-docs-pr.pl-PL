---
title: Rozwiązywanie problemów z wydajnością aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS
description: Rozwiązywanie problemów z wydajnością w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, wydajność
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e83400e444d4c8c733bea5552a31954bb019e358
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474052"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Rozwiązywanie problemów z wydajnością aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie przedstawiono kilka ogólnych kroków, które można wykorzystać do zawężenia problemów z wydajnością związanych z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS.

Ochrona w czasie rzeczywistym (RTP) to funkcja, która Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS, która nieustannie monitoruje i chroni Twoje urządzenie przed zagrożeniami. Obejmuje on monitorowanie plików i procesów oraz inne heuristics.

W zależności od uruchomionej aplikacji i charakterystyki urządzenia wydajność może być suboptimalna, gdy Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS. W szczególności aplikacje lub procesy systemowe, które w krótkim czasie uzyskają dostęp do wielu zasobów, mogą powodować problemy z wydajnością w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS.

Aby rozwiązać te problemy i zminimalizować te problemy, można wykonać następujące czynności:

1. Wyłącz ochronę w czasie rzeczywistym przy użyciu jednej z następujących metod i sprawdź, czy wydajność nie poprawia się. Ta metoda pozwala zawęzić zakres Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS.

      Jeśli Twoje urządzenie nie jest zarządzane przez Twoją organizację, ochronę w czasie rzeczywistym można wyłączyć przy użyciu jednej z następujących opcji:

    - Z interfejsu użytkownika. Otwórz Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS i przejdź do **okna Zarządzanie ustawieniami**.

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" Strona Zarządzanie ochroną w czasie rzeczywistym" lightbox="images/mdatp-36-rtp.png":::
      

    - Z terminalu. Ze względów bezpieczeństwa ta operacja wymaga podwyższenia.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      Jeśli Twoje urządzenie jest zarządzane przez Twoją organizację, administrator może wyłączyć ochronę w czasie rzeczywistym, korzystając z instrukcji w te sposób: Ustawianie preferencji dla aplikacji dla systemu [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md).

      Jeśli problem z wydajnością będzie nadal występował, gdy ochrona w czasie rzeczywistym jest wyłączona, źródłem problemu może być wykrywanie i reagowanie w punktach końcowych składnikiem. W takim przypadku skontaktuj się z działem obsługi klienta, aby uzyskać dalsze instrukcje i środki zaradcze.

2. Otwórz program Finder i przejdź do **aplikacji Narzędzia** \> **.** Otwórz **Monitor aktywności** i analizuj, które aplikacje korzystające z zasobów w systemie. Typowymi przykładami są programy aktualizujące oprogramowanie i programy programowe.

3. Aby znaleźć aplikacje wyzwalające najwięcej skanów, możesz użyć statystyk czasu rzeczywistego zebranych z programu Defender dla punktu końcowego na komputerze Mac.

      > [!NOTE]
      > Ta funkcja jest dostępna w wersji 100.90.70 lub nowszej.
      Ta funkcja jest domyślnie włączona w **kanałach Dogfast** i **InsiderFast** . Jeśli korzystasz z innego kanału aktualizacji, tę funkcję można włączyć z wiersza polecenia:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      Ta funkcja wymaga włączonej ochrony w czasie rzeczywistym. Aby sprawdzić stan ochrony w czasie rzeczywistym, uruchom następujące polecenie:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    Sprawdź, czy **real_time_protection_enabled** jest prawdziwy. W przeciwnym razie uruchom następujące polecenie, aby je włączyć:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      Aby zbierać bieżące statystyki, uruchom:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > Użycie **formatu --output** (należy zwrócić uwagę na podwójną kreskę) gwarantuje, że format wyjściowy jest gotowy do analizy.
      Wynik tego polecenia spowoduje pokazanie wszystkich procesów i ich skojarzonej aktywności skanowania.

4. W systemie Mac pobierz przykładowy parser w języku Python high_cpu_parser.py przy użyciu tego polecenia:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    Wyniki tego polecenia powinny przypominać następujące:

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.
    mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in
    0s
    ```

5. Następnie wpisz następujące polecenia:

      ```bash
        chmod +x high_cpu_parser.py
      ```

      ```bash
        cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
      ```

      Powyższe dane wyjściowe to lista osób, które są najbardziej współautorami problemów z wydajnością. Pierwsza kolumna zawiera identyfikator procesu (PID), druga — nazwę procesu, a ostatnia — liczbę zeskanowanych plików posortowanych według wpływu.

      Wynik polecenia będzie na przykład podobny do poniższego:

      ```output
        ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
        27432 None 76703
        73467 actool     1249
        73914 xcodebuild 1081
        73873 bash 1050
        27475 None 836
        1    launchd    407
        73468 ibtool     344
        549  telemetryd_v1   325
        4764 None 228
        125  CrashPlanService 164
      ```

      Aby poprawić wydajność programu Defender for Endpoint na komputerze Mac, odszukaj program o największej liczbie w wierszu Łączna liczba zeskanowanych plików i dodaj dla niego wykluczenie. Aby uzyskać więcej informacji, zobacz Konfigurowanie i weryfikowanie wykluczeń dla [programu Defender dla punktu końcowego w systemie Linux](linux-exclusions.md).

      > [!NOTE]
      > Aplikacja przechowuje statystyki w pamięci i śledzi tylko aktywność plików od jej rozpoczęcia i została włączona ochrona w czasie rzeczywistym. Nie są liczone procesy uruchomione przed lub podczas okresów, w których ochrona w czasie rzeczywistym była wyłączona. Ponadto zliczane są tylko zdarzenia, które wyzwoliły skany.
      >
6. Skonfiguruj Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS z wykluczeniami dla procesów lub lokalizacji dyskowych, które sprzyjają problemom z wydajnością, i ponownie włącz ochronę w czasie rzeczywistym.

     Aby uzyskać szczegółowe informacje, zobacz Konfigurowanie i weryfikowanie wykluczeń Ochrona punktu końcowego w usłudze Microsoft Defender [w systemie macOS](mac-exclusions.md).
