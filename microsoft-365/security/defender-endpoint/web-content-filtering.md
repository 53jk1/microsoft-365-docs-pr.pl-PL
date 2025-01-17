---
title: Filtrowanie zawartości sieci Web
description: Używanie filtrowania zawartości internetowej w Ochrona punktu końcowego w usłudze Microsoft Defender do śledzenia i regulowania dostępu do witryn internetowych na podstawie ich kategorii zawartości.
keywords: ochrona sieci Web, ochrona przed zagrożeniami w Internecie, przeglądanie internetu, monitorowanie, raporty, karty, lista domen, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, luki w zabezpieczeniach, witryny internetowe, ochrona sieci, Przeglądarka Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 01000e08153e96042e6873dc45fcb0627ea82e47
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782990"
---
# <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Filtrowanie zawartości internetowej jest częścią funkcji [ochrony sieci Web](web-protection-overview.md) w Ochrona punktu końcowego w usłudze Microsoft Defender. Umożliwia organizacji śledzenie i regulowanie dostępu do witryn internetowych na podstawie ich kategorii zawartości. Wiele z tych witryn internetowych, choć nie jest złośliwych, może być problematycznych z powodu przepisów dotyczących zgodności, użycia przepustowości lub innych problemów.

Skonfiguruj zasady w grupach urządzeń, aby blokować niektóre kategorie. Zablokowanie kategorii uniemożliwia użytkownikom w określonych grupach urządzeń dostęp do adresów URL skojarzonych z kategorią. W przypadku każdej kategorii, która nie jest zablokowana, adresy URL są automatycznie poddawane inspekcji. Użytkownicy mogą uzyskiwać dostęp do adresów URL bez zakłóceń, a ty zbierzesz statystyki dostępu, aby ułatwić tworzenie bardziej niestandardowych decyzji dotyczących zasad. Użytkownicy zobaczą powiadomienie o blokadzie, jeśli element na wyświetlonej stronie wykonuje wywołania zablokowanego zasobu.

Filtrowanie zawartości internetowej jest dostępne w głównych przeglądarkach internetowych z blokami wykonywanymi przez Windows Defender SmartScreen (Microsoft Edge) i Network Protection (Chrome, Firefox, Brave i Opera). Aby uzyskać więcej informacji na temat obsługi przeglądarki, zobacz sekcję wymagania wstępne.

## <a name="benefits-of-web-content-filtering"></a>Zalety filtrowania zawartości internetowej

- Użytkownicy nie mogą uzyskiwać dostępu do witryn internetowych w zablokowanych kategoriach, niezależnie od tego, czy przeglądają w środowisku lokalnym, czy poza siecią.

- Twój zespół ds. zabezpieczeń może wygodnie wdrażać zasady w grupach użytkowników przy użyciu grup urządzeń zdefiniowanych w [Ochrona punktu końcowego w usłudze Microsoft Defender ustawień kontroli dostępu na podstawie ról](/microsoft-365/security/defender-endpoint/rbac).

- Twój zespół ds. zabezpieczeń może uzyskiwać dostęp do raportów internetowych w tej samej centralnej lokalizacji z widocznością rzeczywistych bloków i użycia sieci Web.

## <a name="prerequisites"></a>Wymagania wstępne

Przed wypróbowaniem tej funkcji upewnij się, że spełniasz następujące wymagania:

- Twoja subskrypcja obejmuje jedną z następujących opcji: Windows 10 Enterprise E5, Microsoft 365 E5, Zabezpieczenia platformy Microsoft 365 E5, Microsoft 365 E3 lub Ochrona punktu końcowego w usłudze Microsoft Defender licencji autonomicznej. 

- Masz dostęp do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

- Urządzenia organizacji są uruchomione Windows 10 rocznicowej aktualizacji (wersja 1607) lub nowszej lub Windows 11 z [najnowszymi aktualizacjami oprogramowania antywirusowego/ochrony przed złośliwym kodem](manage-updates-baselines-microsoft-defender-antivirus.md).

- Windows Defender Filtr SmartScreen i ochrona sieci są włączone na urządzeniach organizacji.

## <a name="data-handling"></a>Obsługa danych

Dane są przechowywane w regionie wybranym w ramach [ustawień obsługi danych Ochrona punktu końcowego w usłudze Microsoft Defender](data-storage-privacy.md). Dane nie opuszczą centrum danych w tym regionie. Ponadto dane użytkownika nie będą udostępniane żadnym osobom trzecim, w tym naszym dostawcom danych.

## <a name="turn-on-web-content-filtering"></a>Włączanie filtrowania zawartości internetowej

W obszarze nawigacji po lewej stronie w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> wybierz pozycję **Ustawienia** \> **Punkty końcowe** \> **Ogólne** \> **funkcje zaawansowane**. Przewiń w dół, aż zobaczysz wpis **filtrowania zawartości sieci Web**. Przełącz przełącznik do pozycji **Włączone** i **Zapisz preferencje**.

### <a name="configure-web-content-filtering-policies"></a>Konfigurowanie zasad filtrowania zawartości internetowej

Zasady filtrowania zawartości sieci Web określają, które kategorie witryn są blokowane dla grup urządzeń. Aby zarządzać zasadami, przejdź do **obszaru Ustawienia** \> **Filtrowanie zawartości sieci Web** **punktów końcowych** (w obszarze **Reguły**\>).

Zasady można wdrożyć, aby zablokować dowolną z następujących kategorii nadrzędnych lub podrzędnych:

<details>
<summary>Zawartość dla dorosłych</summary>

**Kulty**: Strony związane z grupami lub ruchami, których członkowie demonstrują pasję do systemu przekonań, który różni się od tych, które są akceptowane społecznie. 

**Hazard**: Hazard online i witryny, które promują umiejętności i praktyki związane z hazardem.

**Nagość**: witryny, które zapewniają pełne frontalne i półnagie obrazy lub filmy wideo, zazwyczaj w formie artystycznej, i mogą zezwalać na pobieranie lub sprzedaż takich materiałów.

**Pornografia / Treści o charakterze seksualnym**: witryny zawierające treści o charakterze jednoznacznie seksualnym w formie obrazowej lub tekstowej. Każda forma materiałów zorientowanych seksualnie jest również wymieniona tutaj.

**Edukacja seksualna**: Strony, które dyskutują o seksie i seksualności w sposób informacyjny i nie voyeuristic, w tym witryny, które zapewniają edukację na temat reprodukcji ludzi i antykoncepcji, strony, które oferują porady na temat zapobiegania zakażeniom chorób seksualnych, i strony, które oferują porady w sprawach zdrowia seksualnego.

**Tasteless**: Strony zorientowane na treści nieodpowiednie dla dzieci w wieku szkolnym do oglądania lub że pracodawca byłby niewygodny z dostępem swoich pracowników, ale niekoniecznie przemocy lub pornografii.

**Przemoc**: witryny, które wyświetlają lub promują treści związane z przemocą wobec ludzi lub zwierząt.

</details>

<details>
<summary>Wysoka przepustowość</summary>

**Pobieranie witryn**: witryny, których podstawową funkcją jest umożliwienie użytkownikom pobierania zawartości multimedialnej lub programów, takich jak programy komputerowe.

**Udostępnianie obrazów**: witryny używane głównie do wyszukiwania lub udostępniania zdjęć, w tym tych, które mają aspekty społeczne.

**Komunikacja równorzędna**: witryny, które hostują oprogramowanie typu peer-to-peer (P2P) lub ułatwiają udostępnianie plików przy użyciu oprogramowania P2P.

**Pliki do pobrania multimediów strumieniowych &**: witryny, których podstawową funkcją jest dystrybucja multimediów strumieniowych lub witryn, które umożliwiają użytkownikom wyszukiwanie, oglądanie lub słuchanie multimediów przesyłanych strumieniowo.
  
</details>

<details>
<summary>Odpowiedzialność prawna</summary>

**Obrazy wykorzystywania dzieci**: witryny, które zawierają obrazy wykorzystywania dzieci lub pornografię. 

**Działalność przestępcza**: Strony, które udzielają instrukcji, doradzają lub promocję nielegalnej działalności.

**Hacking**: Strony, które zapewniają zasoby do nielegalnego lub wątpliwego korzystania z oprogramowania komputerowego lub sprzętu, w tym witryn, które rozpowszechniają materiały chronione prawami autorskimi, które zostały pęknięte.

**Nietolerancja & nienawiści**: Strony promujące agresywne, poniżające lub obraźliwe opinie na temat dowolnej części populacji, które mogą być identyfikowane przez rasę, religię, płeć, wiek, narodowość, niepełnosprawność fizyczną, sytuację ekonomiczną, preferencje seksualne lub jakikolwiek inny wybór stylu życia.

**Nielegalny lek**: Witryny, które sprzedają nielegalne/kontrolowane substancje, promują nadużywanie substancji lub sprzedają powiązane akcesoria.

**Nielegalne oprogramowanie**: witryny zawierające lub promujące używanie złośliwego oprogramowania, programów szpiegujących, botnetów, oszustw phishingowych lub piractwa & kradzieży praw autorskich.

**Oszustwo szkolne**: Witryny związane z plagiatem lub oszustwem szkolnym. 

**Samookaleczenie**: witryny promujące samookaleczenie, w tym witryny cyberprzemocy, które zawierają obraźliwe i/lub groźne wiadomości wobec użytkowników.

**Broń**: Każda strona, która sprzedaje broń lub opowiada się za użyciem broni, w tym między innymi broni, noży i amunicji.

</details>

<details>
<summary>Wypoczynek</summary>

**Czat**: witryny, które są głównie pokojami czatów opartymi na sieci Web.

**Gry**: Witryny związane z grami wideo lub komputerowymi, w tym witryny, które promują gry poprzez hostowanie Usługi online lub informacji związanych z grami.

**Wiadomości błyskawiczne**: witryny, których można użyć do pobierania oprogramowania do obsługi wiadomości błyskawicznych lub wiadomości błyskawicznych opartych na kliencie.

**sieć Professional**: lokacje, które zapewniają profesjonalne usługi sieciowe.

**Sieci społecznościowe**: witryny, które zapewniają usługi sieci społecznościowych.

**Poczta e-mail oparta na sieci Web**: witryny oferujące internetowe usługi pocztowe.
  
</details>

<details>
<summary>Uncategorized</summary>

**Nowo zarejestrowane domeny**: witryny, które zostały nowo zarejestrowane w ciągu ostatnich 30 dni i nie zostały jeszcze przeniesione do innej kategorii.

**Zaparkowane domeny**: witryny, które nie mają zawartości lub są zaparkowane do późniejszego użycia.
  
**UWAGA**: Bez kategorii zawiera tylko nowo zarejestrowane domeny i zaparkowane domeny i nie obejmuje wszystkich innych witryn spoza tych kategorii.
  
</details>

### <a name="create-a-policy"></a>Tworzenie zasad

Aby dodać nowe zasady, wykonaj następujące kroki:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> wybierz pozycję **Ustawienia** >  **Filtrowanie** >  zawartości sieci Web **+ Dodaj zasady**.

2. Określ nazwę.

3. Wybierz kategorie do zablokowania. Użyj ikony rozwijania, aby w pełni rozwinąć każdą kategorię nadrzędną i wybrać określone kategorie zawartości internetowej.

4. Określ zakres zasad. Wybierz grupy urządzeń, aby określić miejsce zastosowania zasad. Tylko urządzenia w wybranych grupach urządzeń nie będą mogły uzyskiwać dostępu do witryn internetowych w wybranych kategoriach.

5. Przejrzyj podsumowanie i zapisz zasady. Odświeżanie zasad może potrwać do 2 godzin w przypadku wybranych urządzeń.

> [!NOTE]
>
> - Zasady można wdrożyć bez wybierania dowolnej kategorii w grupie urządzeń. Ta akcja spowoduje utworzenie zasad inspekcji tylko w celu ułatwienia zrozumienia zachowania użytkownika przed utworzeniem zasad blokowych.
> - Jeśli jednocześnie usuwasz zasady lub zmieniasz grupy urządzeń, może to spowodować opóźnienie wdrażania zasad.
> - Zablokowanie kategorii "Uncategorized" może prowadzić do nieoczekiwanych i niepożądanych wyników.

## <a name="end-user-experience"></a>Środowisko użytkownika końcowego

Środowisko blokowania obsługiwanych przeglądarek innych firm jest udostępniane przez usługę Network Protection, która udostępnia komunikat na poziomie systemu powiadamiający użytkownika o zablokowanym połączeniu. Aby uzyskać bardziej przyjazne dla użytkownika środowisko w przeglądarce, rozważ użycie Microsoft Edge.

### <a name="allow-specific-websites"></a>Zezwalaj na określone witryny sieci Web

Istnieje możliwość zastąpienia zablokowanej kategorii w filtrowaniu zawartości internetowej, aby zezwolić na pojedynczą witrynę, tworząc niestandardowe zasady wskaźników. Niestandardowe zasady wskaźników zastąpią zasady filtrowania zawartości internetowej, gdy zostaną zastosowane do danej grupy urządzeń.

Aby zdefiniować wskaźnik niestandardowy, wykonaj następujące kroki:

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> przejdź do **pozycji Ustawienia** \> **Adres URL** **wskaźników** \> **punktów końcowych**\>/**Dodaj**\> element domeny.

2. Wprowadź domenę witryny.

3. Ustaw akcję zasad na **wartość Zezwalaj**.

### <a name="dispute-categories"></a>Kategorie sporów

Jeśli napotkasz domenę, która została niepoprawnie skategoryzowana, możesz zakwestionować tę kategorię bezpośrednio z portalu.

Aby zakwestionować kategorię domeny, przejdź do obszaru Domeny **szczegółów**\> **filtrowania zawartości sieci Web** **usługi Reports** \> **Web Protection**\>. Na karcie domeny raportów filtrowania zawartości sieci Web obok każdej domeny zostanie wyświetlony wielokropek. Umieść kursor nad tym wielokropem i wybierz pozycję **Kategoria sporów**.

Zostanie otwarty panel, w którym można wybrać priorytet i dodać więcej szczegółów, takich jak sugerowana kategoria ponownej kategorii. Po wypełnieniu formularza wybierz pozycję **Prześlij**. Nasz zespół przejrzy żądanie w ciągu jednego dnia roboczego. W celu natychmiastowego odblokowania utwórz [niestandardowy wskaźnik zezwalania](indicator-ip-domain.md).

## <a name="web-content-filtering-cards-and-details"></a>Karty i szczegóły filtrowania zawartości sieci Web

Wybierz pozycję **Raporty** \> **Ochrona w Internecie** , aby wyświetlić karty z informacjami o filtrowaniu zawartości internetowej i ochronie przed zagrożeniami w Internecie. Poniższe karty zawierają podsumowanie informacji na temat filtrowania zawartości internetowej.

### <a name="web-activity-by-category"></a>Działanie sieci Web według kategorii

Ta karta zawiera listę nadrzędnych kategorii zawartości internetowej z największym wzrostem lub spadkiem liczby prób dostępu. Omówienie drastycznych zmian wzorców działań internetowych w organizacji z ostatnich 30 dni, 3 miesięcy lub 6 miesięcy. Wybierz nazwę kategorii, aby wyświetlić więcej informacji.

W ciągu pierwszych 30 dni od użycia tej funkcji organizacja może nie mieć wystarczającej ilości danych, aby wyświetlić te informacje.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Działanie internetowe według karty kategorii" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Karta podsumowania filtrowania zawartości sieci Web

Ta karta wyświetla rozkład zablokowanych prób dostępu w różnych nadrzędnych kategoriach zawartości internetowej. Wybierz jeden z kolorowych pasków, aby wyświetlić więcej informacji o określonej nadrzędnej kategorii sieci Web.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Karta podsumowania filtrowania zawartości internetowej" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Karta podsumowania aktywności sieci Web

Ta karta wyświetla łączną liczbę żądań dotyczących zawartości internetowej we wszystkich adresach URL.

:::image type="content" source="images/web-activity-summary.png" alt-text="Karta podsumowania aktywności internetowej" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Wyświetlanie szczegółów karty

Aby uzyskać dostęp do **szczegółów raportu** dla każdej karty, wybierz wiersz tabeli lub kolorowy pasek na wykresie na karcie. Strona szczegółów raportu dla każdej karty zawiera obszerne dane statystyczne dotyczące kategorii zawartości internetowej, domen witryn internetowych i grup urządzeń.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Szczegóły raportu ochrony sieci Web" lightbox="images/web-protection-report-details.png":::

- **Kategorie sieci Web**: wyświetla listę kategorii zawartości internetowej, które miały próby dostępu w organizacji. Wybierz określoną kategorię, aby otworzyć wysuwane podsumowanie.

- **Domeny**: wyświetla listę domen internetowych, do których uzyskano dostęp lub które zostały zablokowane w organizacji. Wybierz określoną domenę, aby wyświetlić szczegółowe informacje o tej domenie.

- **Grupy urządzeń**: wyświetla listę wszystkich grup urządzeń, które wygenerowały działanie internetowe w organizacji

Użyj filtru zakresu czasu w lewym górnym rogu strony, aby wybrać okres. Możesz również filtrować informacje lub dostosowywać kolumny. Wybierz wiersz, aby otworzyć okienko wysuwane z jeszcze większą ilością informacji o wybranym elemencie.

### <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

Tylko Microsoft Edge jest obsługiwane, jeśli konfiguracja systemu operacyjnego urządzenia to Serwer (**konfiguracja systemu operacyjnego cmd** \> **Systeminfo** \> **).** Ochrona sieci jest obsługiwana tylko w trybie inspekcji na urządzeniach serwera, który jest odpowiedzialny za zabezpieczanie ruchu w obsługiwanych przeglądarkach innych firm.

Obsługiwane są tylko Microsoft Edge, a ochrona sieci nie jest obsługiwana na Windows 10 hostach z wieloma sesjami usługi Azure Virtual Desktop.

Usługa Network Protection nie obsługuje obecnie inspekcji protokołu SSL, co może spowodować, że niektóre witryny będą dozwolone przez filtrowanie zawartości sieci Web, które normalnie byłyby blokowane. Witryny będą dozwolone z powodu braku wglądu w zaszyfrowany ruch po uzgadnianiu protokołu TLS i niemożności przeanalizowania niektórych przekierowań.  Obejmuje to przekierowania ze stron logowania poczty internetowej do strony skrzynki pocztowej. Jako zaakceptowane obejście możesz utworzyć niestandardowy wskaźnik bloku dla strony logowania, aby upewnić się, że żaden użytkownik nie będzie mógł uzyskać dostępu do witryny. Należy pamiętać, że może to zablokować dostęp do innych usług skojarzonych z tą samą witryną internetową. 

## <a name="see-also"></a>Zobacz też

- [Omówienie ochrony sieci Web](web-protection-overview.md)
- [Ochrona przed zagrożeniami sieci Web](web-threat-protection.md)
- [Monitoruj bezpieczeństwo sieci Web](web-protection-monitoring.md)
- [Odpowiadaj na zagrożenia sieci Web](web-protection-response.md)
- [Wymagania dotyczące ochrony sieci](web-content-filtering.md)
