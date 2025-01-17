---
title: Microsoft 365 optymalizacji wydajności dzierżawy globalnej dla użytkowników w Chinach
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Ten artykuł zawiera wskazówki dotyczące optymalizowania wydajności sieci dla użytkowników globalnych usług Microsoft 365 w Chinach.
ms.openlocfilehash: 6c99245d523048d30124fc8f8b0c01d7c2004327
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326933"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 optymalizacji wydajności dzierżawy globalnej dla użytkowników w Chinach

> [!IMPORTANT]
> Wskazówki te są specyficzne dla scenariuszy użycia, w których użytkownicy Microsoft 365 **w** Chinach łączą się z globalną **dzierżawą usługi Microsoft 365 dzierżawy**. Te wskazówki nie **mają zastosowania** do dzierżaw w Office 365 obsługiwanej przez firmę 21Vianet.

>[!NOTE]
>Ten artykuł jest częścią zestawu artykułów dotyczących optymalizacji Microsoft 365 zdalnych.

>- Aby uzyskać omówienie korzystania z rozdzielania dzielonego sieci VPN w celu zoptymalizowania Microsoft 365 dla użytkowników zdalnych, zobacz Omówienie: rozdzielanie sieci VPN dla sieci [Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Aby uzyskać szczegółowe wskazówki dotyczące implementowania rozdzielania sieci VPN, zobacz [Implementowanie](microsoft-365-vpn-implement-split-tunnel.md) rozdzielania sieci VPN na Microsoft 365.
>- Aby uzyskać szczegółową listę scenariuszy rozdzielania rozdzielania sieci VPN, zobacz Typowe scenariusze rozdzielania sieci [VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Aby uzyskać wskazówki dotyczące zabezpieczania Teams ruchu multimedialnego w środowiskach rozdzielanych sieci VPN, zobacz Zabezpieczanie sieci Teams sieci multimedialnej na Teams [sieci VPN](microsoft-365-vpn-securing-teams.md).
>- Aby uzyskać informacje na temat konfigurowania usługi Stream i zdarzeń na żywo w środowiskach VPN, zobacz Szczególne zagadnienia dotyczące przesyłania strumieniowego i wydarzeń na żywo w [środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md).

W przypadku przedsiębiorstw z globalną dzierżawą usługi Microsoft 365 i obecnością firmy w Chinach wydajność klienta usługi Microsoft 365 użytkowników w Chinach może być skomplikowana ze względu na czynniki unikatowe dla architektury internetowej firmy China Telco.

W Chinach są uregulowane połączenia z globalną publiczną Internetem, które przecinają urządzenia obwodowe, które są podatne na wysokie poziomy przeciążenia sieci. To przeciążenie powoduje utratę pakietów i opóźnienie dla całego ruchu internetowego przychodzącego do Chin i z tego kraju.

![Microsoft 365 ruchu — bez sieci.](../media/O365-networking/China-O365-unoptimized.png)

Utrata pakietów i opóźnienia mogą zaszkodzić wydajności usług sieciowych, zwłaszcza tych, które wymagają dużych wymiany danych (takich jak duże transfery plików) lub wymagają niemal wydajności w czasie rzeczywistym (aplikacji audio i wideo).

Celem tego tematu jest podanie najlepszych praktyk w zakresie ograniczania wpływu na ograniczenie granicznych połączeń między sieciami w Chinach na Microsoft 365 sieci. Ten temat nie dotyczy innych typowych problemów z wydajnością ostatniej mili, takich jak problemy z dużymi opóźnieniami pakietów ze względu na złożony routing w obrębie operatorów w Chinach.

## <a name="corporate-network-best-practices"></a>Najlepsze rozwiązania dotyczące sieci firmowej

Wiele przedsiębiorstw z globalną Microsoft 365 dzierżawami i użytkownikami w Chinach zaimplementowało sieci prywatne, które przenoszą ruch sieciowy firmowy między lokalizacjami biur w Chinach a lokalizacjami biurowymi na całym świecie. Te przedsiębiorstwa mogą wykorzystać tę infrastrukturę sieciową w celu uniknięcia przeciążenia sieci przy granicach i zoptymalizowania Microsoft 365 w Chinach.

> [!IMPORTANT]
> Tak jak w przypadku wszystkich prywatnych implementacji sieci WAN, należy zawsze skonsultować się z wymaganiami prawnymi dla swojego kraju i/lub regionu, aby zapewnić zgodność z konfiguracją sieci.

Pierwszym krokiem jest wykonanie wskazówek dotyczących sieci wzorcowej w te sposób: Planowanie sieci i dostosowywanie wydajności [pod](./network-planning-and-performance.md) Microsoft 365. Podstawowym celem powinno być uniknięcie, jeśli to możliwe, uzyskiwania dostępu Microsoft 365 usług internetowych z Internetu w Chinach.

- Wykorzystaj istniejącą sieć prywatną do przenoszenia Microsoft 365 sieciowego między sieciami biurowymi w Chinach i lokalizacjami, które wychodzą z publicznego Internetu poza Chiny. Niemal każde położenie poza Chinami zapewni jasne korzyści. Administratorzy sieci mogą dodatkowo optymalizować ruch wychodzący w obszarach o małych opóźnieniach, które są połączone z [globalną siecią firmy Microsoft](/azure/networking/microsoft-global-network). Przykładem są Hongkong, Singapur, Japonia i Korea Południowa.
- Skonfiguruj na urządzeniach użytkowników dostęp do sieci firmowej za pośrednictwem połączenia VPN, aby umożliwić Microsoft 365 sieci firmowej przez prywatne łącze sieci firmowej. Upewnij się, że klienci sieci VPN nie są skonfigurowani do korzystania z rozdzielania rozdzielania lub że urządzenia użytkownika zostały skonfigurowane tak, aby ignorować podział na Microsoft 365 sieci. Aby uzyskać dodatkowe informacje na temat optymalizowania łączności VPN Teams ruchu multimedialnego w czasie rzeczywistym, zobacz [tę sekcję](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Skonfiguruj sieć tak, aby cała sieć Microsoft 365 twojego prywatnego łącza sieciowego. Jeśli musisz zminimalizować ilość ruchu na linku prywatnym, możesz wybrać, czy w kategorii Optymalizowanie mają być kierowane tylko punkty  końcowe, czy zezwolić na przekierowywowanie żądań do punktów końcowych Zezwalaj i Domyślne do przesyłania Internetu.  Spowoduje to zwiększenie wydajności i zminimalizowanie zużycia przepustowości przez ograniczenie zoptymalizowanego ruchu do krytycznych usług, które są najbardziej poufne na duże opóźnienia i utratę pakietów.
- Jeśli to możliwe, użyj protokołu UDP zamiast protokołu TCP w przypadku ruchu strumieniowego przesyłania na żywo, na przykład dla połączeń Teams. Protokół UDP oferuje lepszą wydajność przesyłania strumieniowego na żywo niż tcp.

Aby uzyskać informacje na temat selektywnego rozsyłania Microsoft 365, zobacz [Zarządzanie Office 365 końcowymi](managing-office-365-endpoints.md). Aby uzyskać listę wszystkich adresów URL Office 365 i IP, zobacz Adresy URL Office 365 [i zakresy adresów IP](urls-and-ip-address-ranges.md).

![Microsoft 365 ruchu — zoptymalizowany.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Najlepsze rozwiązania dla użytkowników

Użytkownicy w Chinach, którzy łączą się z globalną dzierżawcą usługi Microsoft 365 z lokalizacji zdalnych, takich jak dom, kawiarnie, hotele i oddziały firmy bez połączenia z sieciami przedsiębiorstwa, mogą odczuwać niską wydajność sieci, ponieważ ruch między ich urządzeniami Microsoft 365 musi być przenoszony przez zatłoczone, krzyżowe obwody sieciowe w Chinach.

Jeśli nie wchodzi w grę między sieciami prywatnymi i/lub dostępem VPN do sieci firmowej, nadal można zminimalizować problemy z wydajnością  per użytkowników, szkolenie użytkowników w Chinach w celu śledzenia tych najlepszych rozwiązań.

- Korzystaj z rozbudowanych Office klienckich do buforowania (takich jak Outlook, Teams, OneDrive itp.) i unikaj klientów internetowych. Office buforowania klientów i dostępu w trybie offline mogą znacznie zmniejszyć wpływ przeciążenia i opóźnień sieci.
- Jeśli dzierżawa Microsoft 365 została skonfigurowana za pomocą funkcji konferencje _głosowe_, użytkownicy Teams mogą dołączać do spotkań za pośrednictwem publicznej sieci telefonicznej. Aby uzyskać więcej informacji, zobacz [Konferencje głosowe w programie Office 365](/microsoftteams/audio-conferencing-in-office-365).
- W przypadku problemów z wydajnością sieci użytkownicy powinni zgłaszać swojemu działowi IT w celu rozwiązania problemów i w przypadku problemów z usługami firmy Microsoft eskalować ich eskalację do pomocy technicznej firmy Microsoft 365 Microsoft. Nie wszystkie problemy są powodowane przez wydajność sieci krzyżowej.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optymalizowanie Microsoft Teams sieci spotkań dla użytkowników w Chinach

W przypadku organizacji z globalną dzierżawą Microsoft 365 i obecnością w Chinach wydajność Microsoft 365 klientów w Chinach może być skomplikowana ze względu na czynniki unikatowe dla architektury internetowej w Chinach. Wiele firm i szkół zgłosiło dobre wyniki, korzystając z poniższych wskazówek. Zakres ten jest jednak ograniczony do lokalizacji sieciowych użytkowników, które kontrolują konfigurację sieci IT, takich jak lokalizacje biura lub punkty końcowe domu/urządzenia przenośne z łącznością VPN. Microsoft Teams połączenia i spotkania są często używane z lokalizacji zewnętrznych, takich jak biury domowe, komórkowe, w podróży i kawiarnie. Połączenia i spotkania korzystają z ruchu multimedialnego w czasie rzeczywistym, dlatego Teams są szczególnie wrażliwe na przeciążenie sieci.

W efekcie firma Microsoft współpracuje z dostawcami usług telekomunikacyjnych w celu przenoszenia ruchu multimedialnego w czasie rzeczywistym usług Teams i Skype dla firm Online przy użyciu wyższej jakości ścieżki sieciowej między połączeniami krajowych i publicznego Internetu w Chinach a usługami Teams i Skype w globalnej chmurze firmy Microsoft 365. Ta funkcja wywęsła ponad 10-dniowy wzrost utraty pakietów i inne kluczowe metryki wpływające na środowisko użytkownika.

>[!IMPORTANT]
>Obecnie te ulepszenia nie obejmują uczestnictwa w spotkaniach na żywo w programie Microsoft Live Events, takich jak duże spotkania w stylu emisji lub "miejskim" za pomocą programu Teams lub usługi Microsoft Stream. Aby wyświetlić spotkanie w zdarzeniach na żywo, użytkownicy w Chinach muszą korzystać z sieci prywatnej lub rozwiązania SDWAN/VPN. Ulepszenia sieci będą jednak korzystne dla użytkowników, którzy prezentują lub zakładają spotkanie na żywo, ponieważ to środowisko pełni rolę zwykłego spotkania Teams dla producenta lub osoby presenterowej.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Najlepsze rozwiązania dotyczące spotkań w sieci Teams organizacji

Należy rozważyć sposób wykorzystania tych ulepszeń sieci, mając na uwagę, że poprzednie wskazówki dotyczące rozważania rozszerzenia sieci prywatnej w celu uniknięcia przeciążenia sieci przez granice. Istnieją dwie ogólne opcje sieci biurowych organizacji:

1. Nie robisz nic nowego. Należy postępować zgodnie z wcześniejszymi wskazówkami na temat obejścia sieci prywatnej, aby uniknąć przeciążenia sieci przez granice. Teams w czasie rzeczywistym ruch multimedialny będzie wykorzystywać konfigurację, tak jak wcześniej.
2. Wdrożenie wzorca podziału/wdrożenia hybrydowego.
   - Użyj poprzednich wskazówek dotyczących całego ruchu oflagowanych w celu optymalizacji Teams spotkania i wywoływania ruchu multimedialnego w czasie rzeczywistym.
   - Przekieruj Teams spotkania i połączenia z ruchem multimedialnym w czasie rzeczywistym za pośrednictwem publicznego Internetu. Zapoznaj się z poniższymi informacjami, aby uzyskać szczegółowe informacje na temat identyfikowania ruchu w sieci multimedialnej w czasie rzeczywistym.

Wysyłanie Teams audio i wideo w czasie rzeczywistym za pośrednictwem publicznego Internetu, który korzysta z wysokiej jakości łączności, może kosztować znacznie więcej, ponieważ wysyłanie tego ruchu przez sieć prywatną jest bezpłatne w porównaniu z płatnością. Podobnych dodatkowych korzyści mogą mieć użytkownicy, którzy również korzystali z klientów SDWAN lub VPN. Niektóre organizacje preferują również ogólne przechodzenie do większej części danych w publicznych połączeniach internetowych.

Te same opcje mogą być stosowane do konfiguracji SDWAN lub VPN. Na przykład użytkownik używa sieci SDWAN lub VPN do trasowania ruchu Microsoft 365 do sieci firmowej, Microsoft 365 następnie korzysta z prywatnego rozszerzenia tej sieci w celu uniknięcia przeciążenia na linii krzyżowej. W sieci SDWAN lub VPN użytkownika można teraz skonfigurować tak, aby wykluczyć Teams i dzwonić do ruchu w czasie rzeczywistym z routingu VPN. Ta konfiguracja sieci VPN jest określana mianem rozdzielania rozdzielania. Aby [uzyskać więcej informacji, zobacz Rozdzielanie sieci VPN Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) sieci.

Możesz również nadal używać swojego urządzenia SDWAN lub VPN do wszystkich Microsoft 365 ruchu, w tym do Microsoft Teams ruchu w czasie rzeczywistym. Firma Microsoft nie ma żadnych zaleceń dotyczących używania rozwiązań SDWAN i VPN.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Najlepsze rozwiązania dotyczące sieci dla użytkowników domowych, urządzeń przenośnych i użytkowników w Teams spotkaniach

Użytkownicy w Chinach mogą skorzystać z tych ulepszeń, łącząc się z publiczną usługą internetową w Chinach za pomocą telefonu stacjonarnego lub komórkowego. Teams w czasie rzeczywistym ruchu audio i wideo w publicznym Internecie bezpośrednio korzysta z lepszej łączności i jakości.

Jednak dane z innych usług Microsoft 365 — ani innego ruchu w sieci Teams, takich jak pliki lub czaty — nie będą od razu korzystać z tych ulepszeń. Użytkownicy spoza sieci organizacji mogą w dalszym ciągu odczuwać niską wydajność sieci dla tego ruchu. Jak omówiono w tym artykule, możesz zmniejszyć te efekty przy użyciu sieci VPN lub SDWAN. Użytkownicy mogą również używać rozbudowanych klientów komputerowych za pośrednictwem klientów sieci Web, którzy obsługują buforowanie w aplikacji w celu ograniczenia problemów z siecią.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identyfikowanie Teams ruchu w sieci medialnej w czasie rzeczywistym

W przypadku konfigurowania urządzenia sieciowego lub konfiguracji VPN/SDWAN musisz wykluczyć tylko Teams ruchu audio i wideo w czasie rzeczywistym. Szczegóły ruchu można znaleźć dla identyfikatora 11 na oficjalnej liście adresów URL Office 365 [i zakresów adresów IP](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Wszystkie pozostałe konfiguracje sieci powinny pozostać niezmienione.

Firma Microsoft nieustannie pracuje nad ulepszaniem Microsoft 365 użytkowników i wydajności klientów w zakresie najszerszego zakresu architektur i cech sieciowych. Odwiedź [witrynę Office 365 sieci Community](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking), aby rozpocząć konwersację lub dołączyć do niej, znaleźć zasoby oraz przesłać sugestie i sugestie dotyczące funkcji

## <a name="related-articles"></a>Artykuły pokrewne

[Omówienie: rozdzielanie sieci VPN na Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementowanie rozdzielania sieci VPN na Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Typowe scenariusze rozdzielania sieci VPN dla sieci Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Zabezpieczanie Teams multimediów na przykład przez rozdzielanie sieci VPN](microsoft-365-vpn-securing-teams.md)

[Szczególne zagadnienia dotyczące przesyłania strumienia i wydarzeń na żywo w środowiskach VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 dotyczące łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Ocenianie Microsoft 365 sieciowej](assessing-network-connectivity.md)

[Microsoft 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Nowoczesne mechanizmy kontroli zabezpieczeń można zapewnić specjalistom zabezpieczeń i informatykom w alternatywnych, obecnie unikatowych scenariuszach pracy zdalnej (blog zespołu zabezpieczeń firmy Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Zwiększanie wydajności sieci VPN w firmie Microsoft: Windows 10 profilów SIECI VPN w celu umożliwienia automatycznego na połączenia](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Vpn: jak firma Microsoft łączy się ze swoimi pracownikami zdalnymi](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Sieć globalna firmy Microsoft](/azure/networking/microsoft-global-network)
