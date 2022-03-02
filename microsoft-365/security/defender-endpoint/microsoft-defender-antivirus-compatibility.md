---
title: Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi
description: Dowiedz się Program antywirusowy Microsoft Defender o innych produktach zabezpieczających i systemach operacyjnych.
keywords: windows defender, defender for endpoint, next-generation, antivirus, compatibility, passive mode
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.date: 02/11/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 67debb23e701b1c31edbc8084aa39ed7bb58385c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011919"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>Program antywirusowy Microsoft Defender zgodności z innymi produktami zabezpieczającymi

**Dotyczy:**

- Program antywirusowy Microsoft Defender
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

Program antywirusowy Microsoft Defender jest automatycznie instalowana w punktach końcowych z następującymi wersjami programu Windows:

- Windows 10 lub nowsze
- Windows Server 2022
- Windows Server 2019
- Windows Server, wersja 1803 lub nowsza
- System Windows Server 2016

Co się dzieje, gdy jest używane inne rozwiązanie antywirusowe/ochrony przed złośliwym oprogramowaniem firmy Microsoft? Czy można używać Program antywirusowy Microsoft Defender razem z innym produktem antywirusowym? Odpowiedzi zależą od kilku czynników, takich jak system operacyjny, oraz od tego, czy korzystasz z programu [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Defender for Endpoint) razem z ochroną antywirusową.

W tym artykule opisano, co się Program antywirusowy Microsoft Defender z programem Program antywirusowy Microsoft Defender i rozwiązaniem antywirusowym/złośliwym firmy Microsoft, z programem Defender for Endpoint lub bez niego.

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender jest dostępna tylko na urządzeniach z systemami Windows 10 i Windows Server 2022, Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 i Windows Server 2012 R2.
>
> W Windows 8.1 ochrony antywirusowej na poziomie przedsiębiorstwa jest oferowana [jako System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), która jest zarządzana za pośrednictwem Microsoft Endpoint Configuration Manager.
>
> Windows Defender jest również oferowana [dla klientów](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) Windows 8.1 urządzeń przenośnych, Windows Defender jednak zarządzanie na poziomie przedsiębiorstwa nie jest dostępne.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>Ochrona antywirusowa bez programu Defender dla punktu końcowego

W tej sekcji opisano, co się dzieje z Program antywirusowy Microsoft Defender i produktami antywirusowymi/złośliwymi produktami innych niż firmy Microsoft w przypadku punktów końcowych, które nie są w nim zainstalowane w programie Defender for Endpoint. W poniższej tabeli podsumowano, czego można oczekiwać:

<br/><br/>

|Windows wersji|Podstawowe rozwiązanie antywirusowe/ochrony przed złośliwym oprogramowaniem|Program antywirusowy Microsoft Defender stan|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|Program antywirusowy Microsoft Defender|Tryb aktywny|
|Windows 10 <br/> Windows 11|Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft|Tryb wyłączony (dzieje się automatycznie)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server, wersja 1803 lub nowsza <br/> System Windows Server 2016 |Program antywirusowy Microsoft Defender|Tryb aktywny|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server, wersja 1803 lub nowsza <br/> System Windows Server 2016  |Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft|Wyłączone (ustawione ręcznie) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) Na serwerze Windows, jeśli korzystasz z produktu antywirusowego innego niż firmy Microsoft, możesz wyłączyć program Program antywirusowy Microsoft Defender przy użyciu programu zasady grupy w celu wyłączenia programu Program antywirusowy Microsoft Defender lub przy użyciu klucza rejestru [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware). Aby użyć klucza rejestru, przejdź do pozycji `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`, a następnie ustaw lub utwórz wpis DWORD o nazwie `DisableAntiSpyware`. Ustaw wartość tego klucza `1` na (co oznacza wartość klucza rejestru na *prawda), a* następnie jako podstawę wybierz pozycję **Szesnastkowa** .

> [!TIP]
> Na Windows Server 2016 może *być Program antywirusowy Windows Defender zamiast* *Program antywirusowy Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>Program antywirusowy Microsoft Defender i rozwiązania antywirusowe/przeciwszybowe firmy Microsoft

W poniższej tabeli podsumowano, co się dzieje z programem Program antywirusowy Microsoft Defender, gdy razem z rozwiązaniami antywirusowymi lub złośliwymi firmami firmy Microsoft są używane razem lub bez programu Microsoft Defender for Endpoint. <br/><br/>

| Windows wersji   | Rozwiązanie antywirusowe/ochrony przed złośliwym oprogramowaniem  | Wnoszone do <br/> Czy program Defender dla punktu końcowego? | Program antywirusowy Microsoft Defender stan     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| Program antywirusowy Microsoft Defender | Tak  | Tryb aktywny | 
| Windows 10 <br/> Windows 11 | Program antywirusowy Microsoft Defender | Nie   | Tryb aktywny |
| Windows 10 <br/> Windows 11  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Tak  | Tryb pasywny (automatycznie) |
| Windows 10 <br/> Windows 11  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Nie   | Tryb wyłączony (automatycznie)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server w wersji 1803 lub nowszej  | Program antywirusowy Microsoft Defender  | Tak |         Tryb aktywny  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server w wersji 1803 lub nowszej   | Program antywirusowy Microsoft Defender | Nie  | Tryb aktywny |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server w wersji 1803 lub nowszej  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Tak  | Program antywirusowy Microsoft Defender musi być ustawiony na tryb pasywny (ręcznie) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server w wersji 1803 lub nowszej  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Nie  | Program antywirusowy Microsoft Defender wyłączyć (ręcznie) <sup>[[3](#fn3)]<sup></sup>  |
| System Windows Server 2016 <br/> Windows Server 2012 R2   | Program antywirusowy Microsoft Defender | Tak | Tryb aktywny |
|System Windows Server 2016 <br/> Windows Server 2012 R2  | Program antywirusowy Microsoft Defender | Nie | Tryb aktywny |
| System Windows Server 2016 <br/> Windows Server 2012 R2  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Tak | Program antywirusowy Microsoft Defender musi być ustawiony na tryb pasywny (ręcznie) <sup>[[2](#fn2)]<sup> |
|System Windows Server 2016 <br/> Windows Server 2012 R2  | Rozwiązanie niebędące oprogramowaniem antywirusowym/złośliwym firmy Microsoft | Nie | Program antywirusowy Microsoft Defender wyłączyć (ręcznie) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) Na Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 lub Windows Server 2012 R2 Program antywirusowy Microsoft Defender  nie włącza automatycznie trybu pasywnego podczas instalowania produktu antywirusowego firmy microsoft. W takich przypadkach ustaw tryb Program antywirusowy Microsoft Defender pasywny, aby zapobiec problemom wywołanym przez posiadanie wielu produktów antywirusowych zainstalowanych na serwerze. Możesz ustawić tryb Program antywirusowy Microsoft Defender pasywnego przy użyciu programu PowerShell, zasady grupy lub klucza rejestru. 

  Można ustawić tryb Program antywirusowy Microsoft Defender pasywnego, ustawiając następujący klucz rejestru:
- Ścieżka: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Nazwa: `ForceDefenderPassiveMode`
- Typ: `REG_DWORD`
- Wartość: `1`

 > [!NOTE]
 > Aby tryb pasywny działał na punktach końcowych z systemem Windows Server 2016 i Windows Server 2012 R2, te punkty końcowe muszą być połączone z nowoczesnym, ujednoliconym rozwiązaniem opisanym w te Windows [onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) Jeśli na komputerze Windows Server 2016 lub Windows Server 2012 R2 używasz produktu antywirusowego innego niż firma Microsoft, a ten punkt końcowy nie jest dołączany do programu Microsoft Defender for Endpoint, wyłącz/odinstaluj usługę Program antywirusowy Microsoft Defender  ręcznie, aby zapobiec problemom spowodowanym przez zainstalowanie na serwerze wielu produktów antywirusowych.

> [!TIP]
> Na Windows Server 2016 może *być Program antywirusowy Windows Defender zamiast* *Program antywirusowy Microsoft Defender*.

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender jest dostępna tylko na urządzeniach z systemami Windows 10 i Windows Server 2022, Windows Server 2019, Windows Server, wersja 1803 lub nowsza, Windows Server 2016 i Windows Server 2012 R2.
>
> W Windows 8.1 ochrony antywirusowej na poziomie przedsiębiorstwa jest oferowana [jako System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)), która jest zarządzana za pośrednictwem Microsoft Endpoint Configuration Manager.
>
> Windows Defender jest również oferowana [dla klientów](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) Windows 8.1 urządzeń przenośnych, Windows Defender jednak zarządzanie na poziomie przedsiębiorstwa nie jest dostępne.

Program Defender for Endpoint zawiera funkcje, które dodatkowo rozszerzają ochronę antywirusową zainstalowaną w Twoim punkcie końcowym. Możesz korzystać z uruchamiania Program antywirusowy Microsoft Defender razem z innym rozwiązaniem antywirusowym.

Na przykład wykrywanie punktu końcowego i odpowiedź [(EDR)](edr-in-block-mode.md) w trybie blokowania zapewnia dodatkową ochronę przed złośliwymi artefaktami, nawet jeśli Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym. Takie możliwości wymagają Program antywirusowy Microsoft Defender instalacji i działania w trybie pasywnym lub aktywnym.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>Wymagania dotyczące Program antywirusowy Microsoft Defender w trybie pasywnym

Aby tryb Program antywirusowy Microsoft Defender pasywny, punkty końcowe muszą spełniać następujące wymagania:

- System operacyjny: Windows 10 lub nowsza; Windows Server 2022, Windows Server 2019 lub Windows Server, wersja 1803 lub nowsza
- Program antywirusowy Microsoft Defender musi być zainstalowany
- Inny produkt antywirusowy/ochrony przed złośliwym oprogramowaniem firmy Microsoft musi być zainstalowany i używany jako podstawowe rozwiązanie antywirusowe
- Punkty końcowe muszą zostać dołoowane do usługi Defender for Endpoint

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>Jak Program antywirusowy Microsoft Defender na funkcję usługi Defender for Endpoint

Program Defender for Endpoint wpływa na możliwość Program antywirusowy Microsoft Defender w trybie pasywnym. Program antywirusowy Microsoft Defender może również mieć wpływ na niektóre funkcje w programie Defender for Endpoint. Na przykład ochrona w czasie rzeczywistym działa, gdy Program antywirusowy Microsoft Defender w trybie aktywnym lub pasywnym, ale nie w Program antywirusowy Microsoft Defender jest wyłączona lub odinstalowana.

W tabeli w tej sekcji podsumowano funkcje i możliwości, które aktywnie działają lub nie, w zależności od tego, Program antywirusowy Microsoft Defender tryb aktywny, tryb pasywny czy wyłączony/odinstalowany.

> [!IMPORTANT]
> Następująca tabela ma wyłącznie informacyjne informacje. Nie wyłączaj **funkcji, takich** jak ochrona w czasie rzeczywistym, ochrona w chmurze lub ograniczone skanowanie okresowe, jeśli używasz programu Program antywirusowy Microsoft Defender w trybie pasywnym lub jeśli używasz programu [EDR](edr-in-block-mode.md) w trybie blokowania, który działa w tle w celu wykrywania i korygowania złośliwych artefaktów, które zostały wykryte po naruszeniu zabezpieczeń.

<br/><br/>

 | Ochrona | Program antywirusowy Microsoft Defender <br/>(*Tryb aktywny*) | Program antywirusowy Microsoft Defender <br/>(*Tryb pasywny*) | Program antywirusowy Microsoft Defender <br/>(*Wyłączone lub odinstalowane*) | [EDR w trybie blokowania](edr-in-block-mode.md) | 
 |:---|:---|:---|:---|:---| 
 | [Ochrona w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) | Tak | Zobacz <sup>notatkę [[4](#fn4)]</sup> | Nie | Nie | 
 | [Ochrona w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md) | Tak | Nie  | Nie | Nie | 
 | [Ochrona sieci](network-protection.md)  | Tak | Nie | Nie | Nie | 
 | [Reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md)  | Tak | Nie | Nie  | Nie | 
 | [Ograniczona dostępność skanowania okresowego](limited-periodic-scanning-microsoft-defender-antivirus.md) | Nie | Nie | Tak | Nie | 
 | [Informacje dotyczące skanowania i wykrywania plików](review-scan-results-microsoft-defender-antivirus.md) | Tak | Tak | Nie | Tak | 
 | [Działania naprawcze w przypadku zagrożeń](configure-remediation-microsoft-defender-antivirus.md) | Tak | Zobacz <sup>notatkę [[5](#fn5)]</sup> | Nie | Tak | 
 | [Aktualizacje analizy zabezpieczeń](manage-updates-baselines-microsoft-defender-antivirus.md) | Tak | Tak | Nie | Tak | 

(<a id="fn4">4</a>) Na ogół w sytuacji, Program antywirusowy Microsoft Defender jest w trybie pasywnym, ochrona w czasie rzeczywistym nie blokuje ani nie wymusza, nawet jeśli jest włączona i pasywna.

(<a id="fn5">5</a>) Gdy Program antywirusowy Microsoft Defender tryb pasywny, funkcje rozwiązywania problemów z zagrożeniami są aktywne tylko podczas zaplanowanych skanowania lub skanowania na żądanie.

> [!NOTE]
> [Microsoft 365 punktu końcowego](/microsoft-365/compliance/endpoint-dlp-learn-about) ochrona przed utratą danych nadal normalnie działa, gdy Program antywirusowy Microsoft Defender jest aktywny lub pasywny.

## <a name="important-notes"></a>Ważne uwagi

- Nie wyłączaj, zatrzymywać ani nie modyfikuj żadnych skojarzonych usług używanych przez usługę Program antywirusowy Microsoft Defender, usługę Defender for Endpoint ani aplikację Zabezpieczenia Windows sieci Web. Zalecenie obejmuje procesy *i usługi wscsvc*, *SecurityHealthService*, *MsSense*, *Sense*, *WinDefend* lub *MsMpEng* . Ręczne modyfikowanie tych usług może spowodować poważne niestabilność na urządzeniach i narażona na zagrożenia sieci. Wyłączenie, zatrzymanie lub zmodyfikowanie tych usług może również powodować problemy podczas korzystania z rozwiązań antywirusowych innych niż firmy Microsoft oraz sposób wyświetlania ich informacji w [Zabezpieczenia Windows firm.](microsoft-defender-security-center-antivirus.md)

- W programie Defender for Endpoint włącz EDR tryb blokowania, nawet jeśli Program antywirusowy Microsoft Defender nie jest podstawowym rozwiązaniem antywirusowym. EDR trybie blokowania wykrywa i reakcyjne złośliwe elementy odnalezione na urządzeniu (po naruszeniu zabezpieczeń). Aby dowiedzieć się więcej, zobacz [EDR w trybie blokowania](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>Jak potwierdzić stan Program antywirusowy Microsoft Defender

Aby potwierdzić stan Program antywirusowy Microsoft Defender, można użyć jednej z kilku metod, zgodnie z opisem w poniższej tabeli:

<br/><br/>

 | Metoda | Procedura | 
 |:---|:---| 
 | Zabezpieczenia Windows aplikacji |  1. Na Windows otwórz aplikację Zabezpieczenia Windows urządzenia.<br/>2. Wybierz **pozycję Ochrona przed & zagrożeniami**.<br/>3. **W KtoTo chroni mnie? wybierz** pozycję **Zarządzaj dostawcami**.<br/>4. Na stronie **Dostawcy zabezpieczeń** w obszarze **Oprogramowanie antywirusowe** powinien być Program antywirusowy Microsoft Defender **włączony**. | 
 | Menedżer zadań |  1. Na Windows otwórz aplikację Menedżer zadań.<br/>2. Wybierz **kartę** Szczegóły.<br/>3. Poszukaj **MsMpEng.exe** na liście. | 
 | Windows PowerShell <br/> (Aby potwierdzić Program antywirusowy Microsoft Defender jest uruchomiona) |  1. Na Windows otwórz Windows PowerShell. <br/>2. Uruchom następujące polecenie cmdlet programu PowerShell: `Get-Process`.<br/>3. Przejrzyj wyniki. Powinien zostać wyświetlony **MsMpEng.exe**, Program antywirusowy Microsoft Defender jest włączony. | 
 | Windows PowerShell <br/>(Aby potwierdzić, że ochrona antywirusowa jest w miejscu) |  Możesz użyć polecenia [cmdlet Get-MpComputerStatus programu PowerShell](/powershell/module/defender/get-mpcomputerstatus).<br/>1. Na Windows otwórz Windows PowerShell.<br/>2. Uruchom następujące polecenie cmdlet programu PowerShell:<br/> \|Get-MpComputerStatus pozycję AMRunningMode <br/>3. Przejrzyj wyniki. Jeśli w punkcie **końcowym włączono** Program antywirusowy Microsoft Defender, powinien być wyświetlony stan Normalny lub Pasywny.  | 
 | Wiersz polecenia |  1. Na urządzeniu Windows otwórz wiersz polecenia.<br/>2. Wpisz `sc query windefend`, a następnie naciśnij klawisz Enter.<br/>3. Przejrzyj wyniki, aby sprawdzić, czy Program antywirusowy Microsoft Defender działa w trybie pasywnym.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>Więcej szczegółowych informacji o Program antywirusowy Microsoft Defender stanach

W tabeli w tej sekcji opisano różne stany, które mogą być Program antywirusowy Microsoft Defender.

<br/><br/>

 |  Stan  |  Co się dzieje  | 
 |:---|:---| 
 |  Tryb aktywny  |  W trybie aktywnym Program antywirusowy Microsoft Defender jako aplikacja antywirusowa na komputerze. Ustawienia skonfigurowane przy użyciu Menedżer konfiguracji, zasady grupy, Microsoft Intune lub innych produktów do zarządzania będą stosowane. Pliki są skanowane, są naprawiane zagrożenia, a informacje o wykrywaniu są raportowane w narzędziu konfiguracji (takim jak Menedżer konfiguracji lub aplikacja Program antywirusowy Microsoft Defender na samym punkcie końcowym).  | 
 |  Tryb pasywny  |  W trybie pasywnym Program antywirusowy Microsoft Defender nie jest używana jako aplikacja antywirusowa, a zagrożenia nie są  korygowane przez Program antywirusowy Microsoft Defender. Natomiast wykrywanie i reagowanie punktu końcowego [(EDR)](edr-in-block-mode.md) w trybie blokowania może pomóc w eliminowaniu zagrożeń. <br/><br/> Pliki są skanowane przez EDR, a także są udostępniane raporty dotyczące wykrywania zagrożeń udostępnianych w usłudze Defender for Endpoint. W usłudze [Defender](/defender-cloud-apps) dla chmury mogą być wyświetlane alerty pokazujące, Program antywirusowy Microsoft Defender źródło, nawet jeśli Program antywirusowy Microsoft Defender jest w trybie pasywnym. <br/><br/> Gdy Program antywirusowy Microsoft Defender jest pasywny, nadal można zarządzać aktualizacjami dla aplikacji [Program antywirusowy Microsoft Defender, ale](manage-updates-baselines-microsoft-defender-antivirus.md) nie można przenosić nowych Program antywirusowy Microsoft Defender  w tryb aktywny, jeśli Twoje urządzenia mają produkt antywirusowy firmy Microsoft, który zapewnia ochronę w czasie rzeczywistym przed złośliwym oprogramowaniem. <br/><br/> W celu zapewnienia optymalnej ochrony i wykrywania w warstwie zabezpieczeń pamiętaj o tym, aby pobrać aktualizacje oprogramowania antywirusowego i ochrony przed złośliwym oprogramowaniem, nawet Program antywirusowy Microsoft Defender działa w trybie pasywnym. Zobacz [Zarządzanie Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> **UWAGA**: Tryb pasywny nie jest obsługiwany w Windows Server 2016.  | 
 |  Wyłączone <br/><br/> lub <br/><br/> Odinstalowane  |  Po wyłączeniu lub odinstalowaniu Program antywirusowy Microsoft Defender nie jest używana jako aplikacja antywirusowa. Pliki nie są skanowane, a działania zagrożeń nie są korygowane. <br/><br/> Wyłączanie lub odinstalowywanie Program antywirusowy Microsoft Defender nie jest zalecane. Jeśli to możliwe, zachowaj pasywne Program antywirusowy Microsoft Defender w trybie pasywnym, jeśli używasz rozwiązania innego niż firmy Microsoft w celu ochrony przed złośliwym oprogramowaniem/oprogramowaniem antywirusowym. <br/><br/> W przypadkach Program antywirusowy Microsoft Defender gdy program Program antywirusowy Microsoft Defender jest wyłączony automatycznie, można go ponownie włączyć automatycznie, jeśli produkt inny niż firmy Microsoft antywirusowy/chroniący przed złośliwym kodem wygaśnie lub w inny sposób przestanie zapewniać ochronę w czasie rzeczywistym przed wirusami, złośliwym oprogramowaniem lub innymi zagrożeniami. Automatyczne ponowne włączenie programu Program antywirusowy Microsoft Defender pozwala zapewnić zachowanie ochrony antywirusowej dla punktów końcowych. <br/><br/> Możesz również okresowo przeprowadzać ograniczone [skanowanie, które](limited-periodic-scanning-microsoft-defender-antivirus.md) działa z aparatem Program antywirusowy Microsoft Defender, w celu okresowego sprawdzania zagrożeń, jeśli korzystasz z aplikacji antywirusowej innych niż firmy Microsoft.  | 


## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [EDR w trybie blokowania](edr-in-block-mode.md)
- [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w punktach końcowych](/microsoft-365/compliance/endpoint-dlp-learn-about)