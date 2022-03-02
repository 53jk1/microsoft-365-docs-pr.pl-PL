---
title: Office 365 omówienie zabezpieczeń, program Microsoft Defender dla Office 365, EOP, MSDO
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Zabezpieczenia w Office 365, od usługi EOP do usługi Defender Office 365 planów 1 i 2, wersji Standardowe i Ścisłe konfiguracje zabezpieczeń i nie tylko. Dowiedz się, co masz, i dowiedz się, jak zabezpieczyć swoje właściwości.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cbcdf83423b8a6d4e40f34a96282059b44c9df3e
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "62970543"
---
# <a name="office-365-security"></a>Office 365 zabezpieczeń


**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)


Ten artykuł zawiera wprowadzenie do nowych właściwości zabezpieczeń w chmurze. Niezależnie od tego, czy jesteś częścią Centrum operacji zabezpieczeń, jesteś administratorem zabezpieczeń w tym miejscu, czy chcesz odświeżyć swoją pracę.

> [!CAUTION]
> Jeśli korzystasz z usługi **Outlook.com**, **Microsoft 365 Family** lub **Microsoft 365 Personal** i potrzebujesz linków programu *Sejf* lub załączników programu *Sejf*, kliknij ***ten link***: Zaawansowane zabezpieczenia usługi [Outlook.com dla Microsoft 365 subskrybenci](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="office-365-security-spelled-out"></a>Office 365 o zabezpieczeniach

Każda Office 365 ma funkcje zabezpieczeń. Cele i działania, jakie możesz podjąć, zależą od fokusu tych różnych subskrypcji. W Office 365 zabezpieczeń istnieją trzy główne usługi zabezpieczeń (lub produkty) powiązane z typem subskrypcji:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

> [!NOTE]
> Jeśli zakupiono subskrypcję i chcesz teraz w tej chwili w programie zapewnić funkcje *zabezpieczeń, przejdź* do procedury opisanej w artykule Ochrona [przed zagrożeniami](protect-against-threats.md) . Jeśli dopiero zaczynasz korzystać z subskrypcji i chcesz poznać swoją licencję przed rozpoczęciem, przejrzyj strony Rozliczenia > Produkty w [centrum administracyjne platformy Microsoft 365.](https://admin.microsoft.com/AdminPortal/#/homepage)

Office 365 zabezpieczeń na podstawie podstawowych zabezpieczeń oferowanych przez usługę EOP. Usługa EOP jest obecna w dowolnej subskrypcji, Exchange Online można znaleźć skrzynki pocztowe (pamiętaj, że wszystkie produkty zabezpieczające omówione tutaj są oparte na chmurze).

Być może wiesz, że te trzy składniki zostały omówione w ten sposób:

|EOP|Microsoft Defender dla Office 365 P1|Microsoft Defender dla Office 365 P2|
|---|---|---|
|Zapobiega szerokiemu, znanemu atakowi opartemu na woluminie.|Chroni pocztę e-mail i współpracę przed złośliwym oprogramowaniem, wyłudami i firmowymi zabezpieczeniami poczty e-mail.|Dodaje badania po naruszeniu, łowiectwo i reakcję, a także automatyzację i symulacyjne (na szkoleniach).|
|

Pod względem architektury zacznijmy jednak od pojęcia każdej z nich jako skumulowanych warstw zabezpieczeń z wyróżnieniem zabezpieczeń. Bardziej przypomina to:

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic.":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="Usługi EOP i Microsoft Defender dla Office 365 oraz ich relacje między sobą z wyróżnieniem usługi, w tym notatką do uwierzytelniania poczty e-mail.":::

Mimo że każda z tych usług ma na celu ochrona, wykrywanie, badanie i odpowiadanie, ***wszystkie** _ usługi mogą wykonywać _ *_dowolne_** cele ochrony, wykrywania, badania i odpowiadania.

Podstawową zasadą Office 365 jest ochrona eOP. Program Microsoft Defender for Office 365 P1 zawiera usługę EOP. Defender for Office 365 P2 contains P1 and EOP. Struktura jest skumulowana. Dlatego podczas konfigurowania tego produktu należy zacząć od usługi EOP i pracować z usługą Defender dla Office 365.

Konfiguracja uwierzytelniania wiadomości e-mail odbywa się w publicznym systemie DNS, jednak warto skonfigurować tę funkcję, aby ułatwić obronę przed fałszercą. *Jeśli masz usługę EOP,* ***musisz skonfigurować [uwierzytelnianie poczty e-mail](email-validation-and-authentication.md)***.

Jeśli masz konto usługi Office 365 E3 lub poniżej, masz usługę EOP, ale z opcją zakupu autonomicznego programu Defender dla systemu Office 365 P1 przez uaktualnienie. Jeśli masz już Office 365 E5, masz już defender dla Office 365 P2.

> [!TIP]
> Jeśli Twoja subskrypcja nie jest Office 365 E3 ani E5, możesz sprawdzić, czy masz możliwość uaktualnienia do programu Microsoft Defender dla systemu Office 365 P1. Jeśli chcesz, ta strona sieci [](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) Web zawiera listę subskrypcji, które uprawniają do uaktualnienia programu Microsoft Defender dla systemu Office 365 P1 (sprawdź na końcu strony, aby uzyskać drobny wydruk).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Zabezpieczenia Office 365 usługi EOP do programu Microsoft Defender dla Office 365

![Usługi EOP i Microsoft Defender Office 365 oraz ich wyróżnienia w zakresie bezpieczeństwa, przechodząc z chroń i wykryj, aby zbadać i odpowiedzieć. Konfiguracja uwierzytelniania poczty e-mail (co najmniej DKIM i DMARC) powinna zostać skonfigurowania dla usługi EOP i konfiguracji.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> Zapoznaj się ze szczegółami na tych stronach: [Exchange Online Protection](exchange-online-protection-overview.md) i [Defender for Office 365](defender-for-office-365.md).

Co sprawia, że dodanie programu Microsoft Defender dla programu Office 365 może być trudne do odsłoniania korzyści z zarządzania zagrożeniami wyłącznie za pomocą usługi EOP. Aby ułatwić sortowanie, czy ścieżka uaktualnienia jest właściwa dla Twojej organizacji, przyjrzyjmy się możliwościom poszczególnych produktów, jeśli chodzi o:

- zapobieganie i wykrywanie zagrożeń
- badanie
- odpowiadanie

zaczynając od **Exchange Online Protection**:
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Do technologii należą:<ul><li>spam</li><li>phish</li><li>złośliwe oprogramowanie</li><li>poczta masowa</li><li>fałszywa inteligencja</li><li>wykrywanie personifikacji</li><li>Kwarantanna administratora</li><li>Przesyłanie przez administratora i użytkownika wyników wyników fałszywie dodatnich i wyników fałszywie ujemnych</li><li>Zezwalaj na/blokuj dla adresów URL i plików</li><li>Raporty</li></ul>|<li>Przeszukiwanie dziennika inspekcji</li><li>Śledzenie wiadomości</li>|<li>Automatyczne czyszczenie zerowej godziny (ZAP)</li><li>Uściślij i testuj listy zezwalania i blokowania</li>|
|

Jeśli chcesz przejść do programu EOP, przejdź **[do tego artykułu](exchange-online-protection-overview.md)**.

Ponieważ te produkty są skumulowane, jeśli oceniasz usługę Microsoft Defender dla programu Office 365 P1 i zdecydujesz się ją subskrybować, dodasz te możliwości.

Zyski z **defenderem dla Office 365, plan 1** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w UOP oraz:<ul><li>Sejf załączników</li><li>Sejf linków<li>Program Microsoft Defender Office 365 ochrony obciążeń (np. SharePoint online, Teams, OneDrive dla Firm)</li><li>Ochrona poczty e-mail, poczty e-mail i Office klientach i innych Teams</li><li>ochrona przed wyłudzaniem informacji w programie Defender dla Office 365</li><li>Ochrona użytkownika i personifikacji domeny</li><li>Alerty i interfejs API integracji interfejsu SIEM dla alertów</li>|<li>Interfejs API integracji SIEM do wykrywania</li><li>**Narzędzie do wykrywania w czasie rzeczywistym**</li><li>Śledzenie adresu URL</li>|<li>Takie same</li></ul>

Dlatego program Microsoft Defender dla Office 365 P1 rozszerza się po stronie ***prevention** _ domu i dodaje dodatkowe formy _*_detection_**.

Usługa Microsoft Defender dla Office 365 P1 dodaje również **wykrywanie** w czasie rzeczywistym na badaniach. Nazwa tego narzędzia do ochrony przed zagrożeniami jest pogrubiona, ponieważ jej wyraźnym sposobem jest wiedza o tym, że masz program Defender dla Office 365 P1. Nie jest ona wyświetlana w programie Defender Office 365 P2.

Zyski z **defenderem dla Office 365, plan 2** (do tej pory):
<p>

|Zapobieganie/wykrywanie|Badanie|Odpowiadanie|
|---|---|---|
|Technologie obejmują wszystko w usługach EOP i Microsoft Defender for Office 365 P1 oraz:<ul><li>Takie same</li>|<li>**Eksplorator zagrożeń**</li><li>Śledzenie zagrożeń</li><li>Widoki kampanii</li>|<li>Zautomatyzowane badania i odpowiedzi (AIR)</li><li>AIR z Eksploratora zagrożeń</li><li>AIR w przypadku naruszonych użytkowników</li><li>Interfejs API integracji usług SIEM dla zautomatyzowanych badań</li>

Dlatego usługa Microsoft Defender dla Office 365 P2 rozszerza się po stronie badania i  odpowiedzi domu i dodaje nową siłę łętwną. Automatyzacja.

W programie Microsoft Defender Office 365 P2 główne narzędzie do wyszukiwania jest nazywane Eksploratorem **zagrożeń, a** nie wykrywaniem w czasie rzeczywistym. Jeśli po nawigacji do usługi Defender dla chmury jest wyświetlony Eksplorator zagrożeń, to w usłudze Microsoft Defender Office 365 P2.

Aby uzyskać szczegółowe informacje na temat programu Microsoft Defender dla komputerów Office 365 P1 i P2, przejdź **[do tego artykułu](defender-for-office-365.md)**.

> [!TIP]
> Usługi EOP i Microsoft Defender Office 365 również różnią się w przypadku użytkowników końcowych. W usługach EOP i Defender dla Office 365 P1 celem jest *informacja,* Outlook więc te dwie usługi dołączają dodatek Report message Outlook (Zgłoś wiadomość), który umożliwia użytkownikom zgłaszanie wiadomości *e-mail*, które u nich są podejrzane, w celu dalszej analizy. <p> W programie Defender dla systemu Office 365 P2 (który zawiera wszystko w usługach EOP i P1) fokus przesunie się na dalsze szkolenia dla użytkowników końcowych, dzięki czemu Centrum operacji zabezpieczeń będzie mieć dostęp  do zaawansowanego narzędzia Zagrożeń, które udostępnia ono użytkownikom końcowych.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender dla Office 365 Plan 1 a Plan 2 ściągawka

Ten podręczny przewodnik pomoże Ci zrozumieć, jakie możliwości posiada każda usługa Microsoft Defender dla Office 365 subskrypcji. W połączeniu z Twoją wiedzą na temat funkcji usługi EOP może ona pomóc podejmowania decyzji biznesowych w określeniu, która usługa Microsoft Defender for Office 365 najlepiej jest dla nich.

|Defender for Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Funkcje konfiguracji, ochrony i wykrywania: <ul><li>[Sejf załączników](safe-attachments.md)</li><li>[Bezpieczne linki](safe-links.md)</li><li>[Sejf załączników do SharePoint, OneDrive i Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Ochrona przed wyłudzaniem informacji w programie Defender dla Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Wykrywanie w czasie rzeczywistym](threat-explorer.md)</li></ul>|Funkcje usługi Defender Office 365 Plan 1 <p> --- plus --- <p> Funkcje automatyzacji, badań, rozwiązywania problemów i edukacji: <ul><li>[Śledzenie zagrożeń](threat-trackers.md)</li><li>[Eksplorator zagrożeń](threat-explorer.md)</li><li>[Zautomatyzowane badanie i odpowiedź](office-365-air.md)</li><li>[Atak zbędny](attack-simulator.md)</li></ul>|
|

- Program Microsoft Defender dla Office 365 Plan 2 jest Office 365 E5, Office 365 A5 i Microsoft 365 E5.

- Program Microsoft Defender for Office 365 Plan 1 jest dołączony do Microsoft 365 Business Premium.

- Program Microsoft Defender dla Office 365 Plan 1 i Defender dla Office 365 Plan 2 są dostępne jako dodatek dla niektórych subskrypcji. Aby dowiedzieć się więcej, oto kolejny link Dostępność funkcji w programie [Microsoft Defender dla Office 365 planów](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funkcja [Sejf dokumenty](safe-docs.md) programu Sejf jest dostępna tylko dla użytkowników Microsoft 365 E5 licencji usługi Zabezpieczenia platformy Microsoft 365 E5 (nieujętą do programu Microsoft Defender dla Office 365 planów).

- Jeśli Twoja bieżąca subskrypcja nie zawiera programu Microsoft Defender dla usługi Office 365 i [chcesz, skontaktuj](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) się ze sprzedażą, aby rozpocząć okres próbny i dowiedz się, jak usługa Microsoft Defender dla usługi Office 365 może działać w Twojej organizacji.

> [!TIP]
> ***Porada niejawnego programu** testów. Za pomocą spisu docs.microsoft.com można dowiedzieć się więcej o usługach EOP i Microsoft Defender for Office 365. Wróć do tej strony, [Office 365 omówienie](index.yml) zabezpieczeń, a na pasku bocznym widać, że organizacja spisu treści. Proces ten rozpoczyna się od wdrożenia (w tym migracji), a następnie jest w dalszym ciągu zapobieganie, wykrywanie, badanie i reagowanie. <p> Ta struktura jest podzielona, tak aby po tematach _ *Security Administration** były **poruszane tematy dotyczące operacji zabezpieczeń** . Jeśli jesteś nowym członkiem zespołu na stanowisku, skorzystaj z linku zawartego w tej poradce i swojej wiedzy na temat spisu treści, aby dowiedzieć się więcej na ten temat. Pamiętaj, aby na *czas korzystać z linków opinii* i *oceniać* artykuły. Opinie pomagają nam ulepszać to, co oferujemy.

## <a name="where-to-go-next"></a>Gdzie przejść dalej

Jeśli jesteś administratorem zabezpieczeń, może być konieczne skonfigurowanie DKIM lub DMARC dla poczty. Możesz chcieć, aby dla użytkowników priorytetowych było publikowane "Ścisłe" ustawienia wstępne zabezpieczeń, lub poszukać nowych nowości w tym produkcie. Jeśli natomiast korzystasz z usługi Security Ops, możesz chcieć korzystać z wykrywania w czasie rzeczywistym lub Eksploratora zagrożeń w celu zbadania i reakcji albo przeprowadzić wykrywanie użytkowników końcowych za pomocą ataku i odpowiedzi. Tak czy inaczej, poniżej poszło kilka dodatkowych zaleceń, które należy sprawdzić w następnych krokach.

[Uwierzytelnianie poczty e-mail, w tym SPF, DKIM i DMARC (z linkami do konfiguracji wszystkich trzech)](email-validation-and-authentication.md)

[Zapoznaj się z zalecanymi "złotymi" konfiguracjami](recommended-settings-for-eop-and-office365.md) i użyj ich zalecanych ustawień wstępnych, [aby szybko skonfigurować zasady zabezpieczeń](preset-security-policies.md)

Nadrabiaj [zaległości w nowościach w programie Microsoft Defender dla Office 365 (w tym nad rozwojem usługi EOP)](whats-new-in-defender-for-office-365.md)

[Korzystanie z wykrywania w Eksploratorze zagrożeń lub w czasie rzeczywistym](threat-explorer.md)

Używanie [funkcji ataków dla usługi Microsoft Defender dla Office 365](attack-simulator.md)