---
title: Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender
description: Opis wymagań licencjonowania dotyczących urządzeń dołączających do usługi
keywords: wymagania minimalne, licencjonowanie, tabela porównania
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 754537d11a4c183cd1057b94d583a31543d9e4a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467362"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Istnieją pewne minimalne wymagania dotyczące urządzeń dołączających do usługi. Dowiedz się więcej o licencjonowaniu, wymaganiach dotyczących sprzętu i oprogramowania oraz innych ustawieniach konfiguracji na urządzeniach podłączonych do usługi.

> [!TIP]
>
> - W tym artykule opisano minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2. Jeśli szukasz informacji na temat programu Defender dla punktu końcowego (plan 1), zobacz Wymagania dotyczące usługi [Defender dla punktu końcowego (plan 1](mde-p1-setup-configuration.md#review-the-requirements)).
> - Dowiedz się więcej o najnowszych ulepszeniach w programie Defender for Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Program Defender for Endpoint zademonstrował wiodące w branży kable i funkcje wykrywania w ostatnim czasie oceny miTRE. Przeczytaj: [Szczegółowe informacje z miTRE ATT&oceny na podstawie CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania
Aby uzyskać informacje o wymaganiach licencjonowania Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender informacje o licencjonowaniu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).


Aby uzyskać szczegółowe informacje o licencjonowaniu, zobacz witrynę [Warunki](https://www.microsoft.com/licensing/terms/) produktu i współpracy z zespołem klienta, aby dowiedzieć się więcej o warunkach i postanowieniach.

Aby uzyskać więcej informacji na temat tablicy funkcji dostępnych w Windows wersjach, zobacz [Porównanie Windows wersji](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Wymagania dotyczące przeglądarki

Dostęp do usługi Defender for Endpoint odbywa się za pośrednictwem przeglądarki, która obsługuje następujące przeglądarki:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Mimo że inne przeglądarki mogą działać, wymienione przeglądarki są obsługiwane.

## <a name="hardware-and-software-requirements"></a>Wymagania dotyczące sprzętu i oprogramowania

### <a name="supported-windows-versions"></a>Obsługiwane Windows wersji

- Windows 7 z dodatkiem SP1 Enterprise ([wymaga dodatku ESU do pomocy technicznej](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 7 z dodatkiem SP1 Pro ([wymaga dodatku ESU do pomocy technicznej](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- System Windows 11 dla firm
- System Windows 11 dla edukacji
- System Windows 11 Pro
- System Windows 11 Pro dla edukacji
- System Windows10 dla firm
- [Windows 10 Enterprise LTSC 2016 (lub nowszy)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >Mimo że program Windows 10 IoT Enterprise jest obsługiwanym systemem operacyjnym w programie Ochrona punktu końcowego w usłudze Microsoft Defender i umożliwia im rozpowszechnianie go w ramach produktu lub rozwiązania, klienci powinni postępować zgodnie ze wskazówkami OEM/ODM wokół zainstalowanego oprogramowania i możliwości obsługi technicznej na komputerze hosta.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows serwera
  - Windows Server 2008 R2 z dodatkiem SP1 ([wymaga programu ESU do pomocy technicznej](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - System Windows Server 2016
  - Windows Server w wersji 1803 lub nowszej
  - Windows Server 2019
  - Windows Server 2022
- Windows pulpit wirtualny

Na urządzeniach w Twojej sieci musi być uruchomiona jedna z tych wersji.

Wymagania sprzętowe usługi Defender dla punktu końcowego na urządzeniach są takie same w przypadku obsługiwanych wersji.

> Podstawy: 2 minimalne, 4 preferowane pamięci: co najmniej 1 GB, 4 preferowane

Aby uzyskać więcej informacji na temat obsługiwanych wersji Windows 10, zobacz (/windows/release-health/release-information).

> [!NOTE]
> Komputery z wersjami programu Windows (takimi jak Windows CE i Windows 10 Mobile) nie są obsługiwane.
>
> Virtual Machines uruchomione Windows 10 Enterprise 2016 LTSB mogą wystąpić problemy z wydajnością, jeśli są uruchomione na platformach innych niż Microsoft Virtualization.
>
> W przypadku środowisk wirtualnych zalecamy używanie programu Windows 10 Enterprise LTSC 2019 lub nowszego.

Gdy składniki są aktualne w systemach operacyjnych microsoft Windows, pomoc techniczna Ochrona punktu końcowego w usłudze Microsoft Defender cykl życia odpowiedniego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz Często [zadawane pytania dotyczące cyklu życia](/lifecycle/faq/general-lifecycle). Nowe funkcje lub funkcje są zwykle udostępniane tylko w systemach operacyjnych, które jeszcze nie zakończyły ich cyklu życia. Aktualizacje analizy zabezpieczeń (aktualizacje definicji i aparatu) oraz logika wykrywania będą nadal udostępniane do co najmniej:

- Data [zakończenia pomocy technicznej](/lifecycle/products/) (dla systemów operacyjnych, które nie mają programu rozszerzonej aktualizacji zabezpieczeń).
- Data [zakończenia ESU](/lifecycle/faq/extended-security-updates) (dla systemów operacyjnych, które mają program ESU).



### <a name="other-supported-operating-systems"></a>Inne obsługiwane systemy operacyjne

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Aby integracja działała, należy potwierdzić zgodność dystrybucji i wersji systemu Android, iOS i macOS z programem Defender for Endpoint.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Wymagania dotyczące sieci i magazynowania danych oraz konfiguracji

Przy pierwszym uruchomieniu kreatora dołączania musisz wybrać miejsce przechowywania informacji związanych z usługą Ochrona punktu końcowego w usłudze Microsoft Defender: w Unii Europejskiej, Wielkiej Brytanii lub w centrum Stany Zjednoczone danych.

> [!NOTE]
>
> - Po pierwszej konfiguracji nie można zmienić lokalizacji przechowywania danych.
> - Zapoznaj się [Ochrona punktu końcowego w usłudze Microsoft Defender przechowywaniem i prywatnością](data-storage-privacy.md) danych, aby uzyskać więcej informacji na temat miejsca i sposobu przechowywania danych przez firmę Microsoft.

### <a name="diagnostic-data-settings"></a>Ustawienia danych diagnostycznych

> [!NOTE]
> Ochrona punktu końcowego w usłudze Microsoft Defender nie wymaga żadnego określonego poziomu diagnostycznego, jeśli jest włączony.

Upewnij się, że usługa danych diagnostycznych jest włączona na wszystkich urządzeniach w organizacji.
Domyślnie ta usługa jest włączona. Warto sprawdzić, czy będziesz mieć pewność, że otrzymasz od nich dane czujnika.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Sprawdzanie typu uruchamiania usługi Windows wiersza polecenia

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień na urządzeniu:
   1. Przejdź do **przycisku Start** i wpisz **cmd**.
   2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

   ```console
   sc qc diagtrack
   ```

   Jeśli usługa jest włączona, wynik powinien wyglądać tak, jak na poniższym zrzucie ekranu:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Wynik polecenia zapytania sc w celu rozwiązania diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

Musisz skonfigurować usługę tak, aby uruchamiała się automatycznie, jeśli **START_TYPE nie jest** ustawiona **na AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Ustawianie automatycznego uruchamiania usługi danych Windows wiersza polecenia

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień w punkcie końcowym:
    1. Przejdź do **przycisku Start** i wpisz **cmd**.
    2. Kliknij prawym przyciskiem myszy **pozycję Wiersz polecenia i** wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie i naciśnij klawisz **Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. Zostanie wyświetlony komunikat o sukcesie. Sprawdź zmianę, wprowadzając następujące polecenie, a następnie naciśnij klawisz **Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>Łączność z Internetem

Łączność internetowa na urządzeniach jest wymagana bezpośrednio lub przez serwer proxy.

Czujnik defender dla punktu końcowego może korzystać ze średniej dziennej przepustowości 5 MB do komunikacji z usługą w chmurze Defender for Endpoint i zgłaszania danych cyberprzestępczości. Podczas tej średniej dziennej przepustowości nie są uwzględniane działania tego typu, takie jak przekazywanie plików i zbieranie pakietów badania.

Aby uzyskać więcej informacji na temat dodatkowych ustawień konfiguracji serwera proxy, zobacz [Konfigurowanie ustawień serwera proxy i łączności internetowej urządzenia](configure-proxy-internet.md).

Zanim urządzenia będą włączone, musi być włączona usługa danych diagnostycznych. Usługa jest domyślnie włączona w Windows 10 i Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Program antywirusowy Microsoft Defender konfiguracji

Agent programu Defender for Endpoint zależy od możliwości skanowania Program antywirusowy Microsoft Defender i podania informacji na ich temat.

Skonfiguruj aktualizacje analizy zabezpieczeń w programie Defender dla urządzeń końcowych, Program antywirusowy Microsoft Defender, czy jest aktywnym złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Jeśli Program antywirusowy Microsoft Defender nie jest aktywnym złośliwym oprogramowaniem w organizacji i korzystasz z usługi Defender for Endpoint, Program antywirusowy Microsoft Defender przechodzi w tryb pasywny.

Jeśli Twoja organizacja została wyłączona Program antywirusowy Microsoft Defender przy użyciu zasad grupy lub innych metod, urządzenia, które są włączone, muszą być wykluczone z tych zasad grupy.

Jeśli wnoszysz serwery i Program antywirusowy Microsoft Defender nie jest aktywnym złośliwym oprogramowaniem na tych serwerach, konieczne będzie skonfigurowanie Program antywirusowy Microsoft Defender do działania w trybie pasywnym lub odinstalowywania. Konfiguracja zależy od wersji serwera. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender zgodności](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> Twoje zwykłe zasady grupy nie dotyczą ochrony przed naruszeniami, a zmiany Program antywirusowy Microsoft Defender są ignorowane, gdy ochrona przed naruszeniami jest wł.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Program antywirusowy Microsoft Defender włączono sterownik ELAM (Early Launch Antimalware)

Jeśli używasz programu Program antywirusowy Microsoft Defender jako podstawowego produktu ochrony przed złośliwym kodem na swoich urządzeniach, agent programu Defender for Endpoint pomyślnie zostanie uruchomiony.

Jeśli korzystasz z rozwiązań mobilnych Zarządzanie urządzeniami lub Microsoft Endpoint Manager (bieżąca gałąź), musisz upewnić się, że sterownik Program antywirusowy Microsoft Defender ELAM jest włączony. Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender wyłączyć zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Tematy pokrewne

- [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sieci](production-deployment.md)
- [Dołączanie urządzeń](onboard-configure.md)
