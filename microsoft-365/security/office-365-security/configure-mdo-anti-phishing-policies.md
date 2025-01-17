---
title: Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak tworzyć, modyfikować i usuwać zaawansowane zasady ochrony przed wyłudzaniem informacji, które są dostępne w organizacjach z Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: fa7b1519120e349ca2ca99f8bd2df1b21408404d
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847430"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Zasady ochrony przed wyłudzaniem informacji w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) mogą pomóc chronić organizację przed złośliwymi atakami wyłudzania informacji opartymi na personifikacji i innymi typami ataków phishingowych. Aby uzyskać więcej informacji na temat różnic między zasadami ochrony przed wyłudzaniem informacji w Exchange Online Protection (EOP) i zasadami ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender, zobacz [Ochrona przed wyłudzaniem informacji](anti-phishing-protection.md).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślne zasady ochrony przed wyłudzaniem informacji. Aby uzyskać większy stopień szczegółowości, możesz również utworzyć niestandardowe zasady ochrony przed wyłudzaniem informacji, które mają zastosowanie do określonych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają pierwszeństwo przed zasadami domyślnymi, ale można zmienić priorytet (kolejność uruchamiania) zasad niestandardowych.

Zasady ochrony przed wyłudzaniem informacji można skonfigurować w Ochrona usługi Office 365 w usłudze Defender w portalu Microsoft 365 Defender lub w programie Exchange Online PowerShell.

Aby uzyskać informacje na temat konfigurowania bardziej ograniczonych zasad ochrony przed wyłudzaniem informacji, które są dostępne w Exchange Online Protection (tj. organizacji bez Ochrona usługi Office 365 w usłudze Defender), zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md).

Podstawowe elementy zasad ochrony przed wyłudzaniem informacji to:

- **Zasady anty-phish**: określa ochronę przed wyłudzaniem informacji, aby włączyć lub wyłączyć, a akcje do zastosowania opcji.
- **Reguła anty-phish**: określa priorytet i filtry adresatów (do kogo mają zastosowanie zasady) dla zasad anty-phish.

Różnica między tymi dwoma elementami nie jest oczywista podczas zarządzania zasadami ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender:

- Podczas tworzenia zasad tworzysz regułę anty-phish i skojarzone zasady anty-phish w tym samym czasie przy użyciu tej samej nazwy dla obu.
- Podczas modyfikowania zasad ustawienia związane z nazwą, priorytetem, włączonym lub wyłączonym, a filtry adresatów modyfikują regułę anty-phish. Wszystkie inne ustawienia modyfikują skojarzone zasady anty-phish.
- Po usunięciu zasad zostanie usunięta reguła anty-phish i skojarzone zasady anty-phish.

W programie Exchange Online programu PowerShell zasady i reguła są zarządzane oddzielnie. Aby uzyskać więcej informacji, zobacz sekcję [Use Exchange Online PowerShell to configure anti-phishing policies (Używanie Exchange Online programu PowerShell do konfigurowania zasad ochrony przed wyłudzaniem informacji](#use-exchange-online-powershell-to-configure-anti-phishing-policies)) w dalszej części tego artykułu.

Każda organizacja Ochrona usługi Office 365 w usłudze Defender ma wbudowane zasady ochrony przed wyłudzaniem informacji o nazwie Office 365 AntiPhish Default, które mają następujące właściwości:

- Zasady są stosowane do wszystkich adresatów w organizacji, mimo że z zasadami nie są skojarzone żadne reguły antyfizowe (filtry adresatów).
- Zasady mają niestandardową wartość priorytetu **Najniższa** , którą nie można zmodyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie utworzone zasady niestandardowe mają zawsze wyższy priorytet.
- Zasady to zasady domyślne (właściwość **IsDefault** ma wartość `True`) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender, można utworzyć niestandardowe zasady ochrony przed wyłudzaniem informacji z bardziej rygorystycznymi ustawieniami stosowanymi do określonych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby dodawać, modyfikować i usuwać zasady ochrony przed wyłudzaniem informacji, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do zasad ochrony przed wyłudzaniem informacji, musisz być członkiem grup <sup>\*</sup> ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z zalecanymi ustawieniami zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender, zobacz [Zasady ochrony przed wyłudzaniem informacji w ustawieniach Ochrona usługi Office 365 w usłudze Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

- Zaczekaj do 30 minut na zastosowanie nowych lub zaktualizowanych zasad.

- Aby uzyskać informacje o tym, gdzie zasady ochrony przed wyłudzaniem informacji są stosowane w potoku filtrowania, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Tworzenie zasad ochrony przed wyłudzaniem informacji za pomocą portalu Microsoft 365 Defender

Utworzenie niestandardowych zasad ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender tworzy regułę anty-phish i skojarzone zasady anty-phish w tym samym czasie przy użyciu tej samej nazwy dla obu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& zasady ochrony** \> **przed wyłudzaniem**  \> informacji w sekcji Zasady. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie otwarty kreator zasad. Na stronie **Nazwa zasad** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową, opisową nazwę zasad.
   - **Opis**: wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na wyświetlonej stronie **Użytkownicy, grupy i domeny** zidentyfikuj wewnętrznych adresatów, których dotyczą zasady (warunki adresatów):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty e-mail.
   - **Grupy**:
     - Członkowie określonych grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty.
     - Określona Grupy Microsoft 365.
   - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników, grupy i domeny**: aby dodać wyjątki dla adresatów wewnętrznych, których dotyczą zasady (wyjątki recpient), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na wyświetlonej stronie **Progu wyłudzania informacji & ochrony** skonfiguruj następujące ustawienia:

   - **Próg wiadomości e-mail wyłudzającej** informacje: użyj suwaka, aby wybrać jedną z następujących wartości:
     - **1 — Standardowa** (jest to wartość domyślna).
     - **2 — Agresywne**
     - **3 — Bardziej agresywne**
     - **4 - Najbardziej agresywne**

     Aby uzyskać więcej informacji, zobacz [Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Personifikacja**: te ustawienia są warunkiem dla zasad, które identyfikują określonych nadawców do wyszukania (indywidualnie lub według domeny) w adresie od komunikatów przychodzących. Aby uzyskać więcej informacji, zobacz [Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

     > [!NOTE]
     >
     > - W poszczególnych zasadach ochrony przed wyłudzaniem informacji można określić maksymalnie 350 chronionych użytkowników (adresy e-mail nadawcy). Nie można określić tego samego chronionego użytkownika w wielu zasadach.
     > - Ochrona przed personifikacją użytkownika nie działa, jeśli nadawca i adresat wcześniej komunikowali się za pośrednictwem poczty e-mail. Jeśli nadawca i adresat nigdy nie komunikowali się za pośrednictwem poczty e-mail, wiadomość zostanie zidentyfikowana jako próba personifikacji.

     - **Włącz ochronę użytkowników**: wartość domyślna jest wyłączona (nie jest zaznaczona). Aby ją włączyć, zaznacz pole wyboru, a następnie kliknij wyświetlony link **Zarządzaj nadawcami (nn** ).

       W wyświetlonym wysuwu **Zarządzanie nadawcami w celu ochrony przed personifikacją** wykonaj następujące kroki:

       - **Nadawcy wewnętrzni**: kliknij pozycję Dodaj ikonę ![wewnętrzną.](../../media/m365-cc-sc-add-internal-icon.png) **Wybierz pozycję wewnętrzna**. W wyświetlonym wysuwu **Dodaj wewnętrznych nadawców** kliknij w polu i wybierz użytkownika wewnętrznego z listy. Listę można filtrować, wpisując użytkownika, a następnie wybierając użytkownika z wyników. Możesz użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana.

         Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

         Po zakończeniu kliknij pozycję **Dodaj**

       - **Zewnętrzni nadawcy**: kliknij pozycję Dodaj ikonę ![zewnętrzną.](../../media/m365-cc-sc-create-icon.png) **Wybierz pozycję zewnętrzne**. W wyświetlonym wysuwu **Dodaj zewnętrznych nadawców** wprowadź nazwę **wyświetlaną w polu Dodaj nazwę** i adres e-mail w polu **Dodaj vaild email** , a następnie kliknij przycisk **Dodaj**.

         Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

         Po zakończeniu kliknij pozycję **Dodaj**

       Po powrocie do menu wysuwanego **Zarządzanie nadawcami w celu personifikacji** możesz usunąć wpisy, wybierając jeden lub więcej wpisów z listy. Wpisy można wyszukiwać przy użyciu ikony ![Wyszukaj.](../../media/m365-cc-sc-create-icon.png) Pole **wyszukiwania**.

       Po wybraniu co najmniej jednego wpisu ikona ![Usuń wybranych użytkowników.](../../media/m365-cc-sc-remove-selected-users-icon.png) **Zostanie wyświetlona ikona Usuń wybranych użytkowników** , której można użyć do usunięcia wybranych wpisów.

       Po zakończeniu kliknij pozycję **Gotowe**.

     - **Włącz ochronę domen**: wartość domyślna jest wyłączona (nie jest zaznaczona). Aby ją włączyć, zaznacz pole wyboru, a następnie skonfiguruj jedno lub oba z następujących wyświetlanych ustawień:
       - **Dołącz domeny, których jestem właścicielem**: aby włączyć to ustawienie, zaznacz pole wyboru. Aby wyświetlić domeny, których jesteś właścicielem, kliknij pozycję **Wyświetl moje domeny**.
       - **Dołącz domeny niestandardowe**: aby włączyć to ustawienie, zaznacz pole wyboru, a następnie kliknij wyświetlony link **Zarządzaj domenami niestandardowymi (nn** ). W wyświetlonym menu wysuwowym **Zarządzanie domenami niestandardowymi na potrzeby ochrony przed personifikacją** kliknij ikonę ![Dodaj domeny.](../../media/m365-cc-sc-create-icon.png) **Dodaj domeny**.

         W wyświetlonym menu wysuwnym **Dodawanie domen niestandardowych** kliknij pole **Domena** , wprowadź wartość, a następnie naciśnij klawisz Enter lub wybierz wartość wyświetlaną poniżej pola. Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

         Po zakończeniu kliknij pozycję **Dodaj domeny**

         > [!NOTE]
         > We wszystkich zasadach ochrony przed wyłudzaniem informacji możesz mieć maksymalnie 50 domen.

       Po powrocie do menu wysuwanego **Zarządzanie domenami niestandardowymi w celu personifikacji** można usunąć wpisy, wybierając jeden lub więcej wpisów z listy. Wpisy można wyszukiwać przy użyciu ikony ![Wyszukaj.](../../media/m365-cc-sc-create-icon.png) Pole **wyszukiwania**.

       Po wybraniu co najmniej jednego wpisu ikona ![Usuń domeny.](../../media/m365-cc-sc-delete-icon.png) **Zostanie** wyświetlona ikona Usuwania, której można użyć do usunięcia wybranych wpisów.

   - **Dodaj zaufanych nadawców i domeny**: określ wyjątki ochrony personifikacji dla zasad, klikając pozycję **Zarządzaj (nn) zaufanymi nadawcami i domenami**. W wyświetlonym wysuwu **Manage custom domains for impersonation protection (Zarządzanie domenami niestandardowymi na potrzeby ochrony przed personifikacją** ) skonfiguruj następujące ustawienia:
      - **Nadawcy**: sprawdź, czy wybrano kartę **Nadawca**, a następnie kliknij ikonę ![Dodaj nadawców.](../../media/m365-cc-sc-create-icon.png) W wyświetlonym wysuwu **Dodaj zaufanych nadawców** wprowadź adres e-mail w polu, a następnie kliknij przycisk **Dodaj**. Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejący wpis, kliknij ikonę ![](../../media/m365-cc-sc-close-icon.png) Usuń dla wpisu.

        Po zakończeniu kliknij przycisk **Dodaj**.

      - **Domeny**: wybierz kartę **Domena** i kliknij ikonę ![Dodaj domeny.](../../media/m365-cc-sc-create-icon.png)

        W wyświetlonym menu wysuwnym **Dodawanie zaufanych domen** kliknij pole **Domena** , wprowadź wartość, a następnie naciśnij klawisz Enter lub wybierz wartość wyświetlaną poniżej pola. Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

        Po zakończeniu kliknij przycisk **Dodaj**.

     Po powrocie do menu wysuwanego **Zarządzanie domenami niestandardowymi pod kątem personifikacji** możesz usunąć wpisy z kart **Nadawca** i **Domena** , wybierając jeden lub więcej wpisów z listy. Wpisy można wyszukiwać przy użyciu ikony ![Wyszukaj.](../../media/m365-cc-sc-create-icon.png) Pole **wyszukiwania**.

     Po wybraniu co najmniej jednego wpisu zostanie wyświetlona ikona **Usuń** , której można użyć do usunięcia wybranych wpisów.

     Po zakończeniu kliknij pozycję **Gotowe**.

     > [!NOTE]
     > Maksymalna liczba wpisów nadawcy i domeny to 1024.

   - **Włącz analizę skrzynki pocztowej**: wartość domyślna jest włączona (wybrana) i zalecamy pozostawienie jej na. Aby go wyłączyć, wyczyść pole wyboru.

     - **Włącz ochronę personifikacji opartą na analizie**: to ustawienie jest dostępne tylko wtedy, gdy opcja **Włącz analizę skrzynek pocztowych** jest włączona (wybrana). To ustawienie umożliwia analizie skrzynek pocztowych podjęcie akcji w przypadku wiadomości zidentyfikowanych jako próby personifikacji. Możesz określić akcję do wykonania w ustawieniu **Jeśli analiza skrzynki pocztowej wykryje personifikowanego użytkownika** na następnej stronie.

       Zalecamy włączenie tego ustawienia, zaznaczając pole wyboru. Aby wyłączyć to ustawienie, wyczyść pole wyboru.

   - **Fałszowanie**: w tej sekcji użyj pola wyboru **Włącz analizę fałszowania** , aby włączyć lub wyłączyć analizę fałszowania. Wartość domyślna jest włączona (wybrana) i zalecamy pozostawienie jej w pozycji . Możesz określić akcję do wykonania w przypadku komunikatów od zablokowanych sfałszowanych nadawców w ustawieniu **Jeśli wiadomość zostanie wykryta jako sfałszowana** na następnej stronie.

     Aby wyłączyć analizę fałszowania, wyczyść pole wyboru.

     > [!NOTE]
     > Nie musisz wyłączać ochrony przed fałszowaniem, jeśli rekord MX nie wskazuje na Microsoft 365. Zamiast tego włączysz filtrowanie rozszerzone dla łączników. Aby uzyskać instrukcje, zobacz [Rozszerzone filtrowanie łączników w Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na wyświetlonej stronie **Akcje** skonfiguruj następujące ustawienia:

   - **Akcje komunikatów**: skonfiguruj następujące akcje w tej sekcji:
     - **Jeśli komunikat zostanie wykryty jako personifikowany użytkownik**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz użytkownikom ochronę** na poprzedniej stronie. Wybierz jedną z następujących akcji na liście rozwijanej dla komunikatów, w których nadawca jest jednym z chronionych użytkowników określonych na poprzedniej stronie:
       - **Nie stosuj żadnej akcji**
       - **Przekierowywanie wiadomości na inne adresy e-mail**
       - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
       - **Kwarantanna komunikatu: Po wybraniu** tej akcji zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz zasady kwarantanny, które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed personifikacją użytkownika. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

         Pusta wartość **zasad kwarantanny Zastosuj** oznacza, że są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy na potrzeby wykrywania personifikacji użytkowników). Po późniejszej edycji zasad ochrony przed wyłudzaniem informacji lub wyświetleniu ustawień zostanie wyświetlona domyślna nazwa zasad kwarantanny.
  
       - **Dostarczanie komunikatu i dodawanie innych adresów do wiersza Bcc**
       - **Usuń wiadomość przed jej dostarczeniem**

     - **Jeśli komunikat zostanie wykryty jako domena personifikowana**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz domeny do ochrony** na poprzedniej stronie. Wybierz jedną z następujących akcji na liście rozwijanej dla wiadomości, w których adres e-mail nadawcy znajduje się w jednej z chronionych domen określonych na poprzedniej stronie:
       - **Nie stosuj żadnej akcji**
       - **Przekierowywanie wiadomości na inne adresy e-mail**
       - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
       - **Kwarantanna komunikatu**: Jeśli wybierzesz tę akcję, zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz zasady kwarantanny, które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed personifikacją domeny.

         Pusta wartość **zasad kwarantanny Zastosuj** oznacza, że są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy w przypadku wykrywania personifikacji domeny). Po późniejszej edycji zasad ochrony przed wyłudzaniem informacji lub wyświetleniu ustawień zostanie wyświetlona domyślna nazwa zasad kwarantanny.

       - **Dostarczanie komunikatu i dodawanie innych adresów do wiersza Bcc**
       - **Usuń wiadomość przed jej dostarczeniem**

     - **Jeśli analiza skrzynki pocztowej wykryje personifikowanego użytkownika**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz analizę na potrzeby ochrony przed personifikacją** na poprzedniej stronie. Wybierz jedną z następujących akcji na liście rozwijanej dla wiadomości, które zostały zidentyfikowane jako próby personifikacji przez analizę skrzynki pocztowej:
       - **Nie stosuj żadnej akcji**
       - **Przekierowywanie wiadomości na inne adresy e-mail**
       - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
       - **Kwarantanna komunikatu**: Jeśli wybierzesz tę akcję, zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz zasady kwarantanny, które mają zastosowanie do wiadomości, które zostały poddane kwarantannie przez ochronę przed analizą skrzynki pocztowej. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

         Pusta wartość **zasad kwarantanny Zastosuj** oznacza, że są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy w przypadku wykrywania analizy skrzynki pocztowej). Po późniejszej edycji zasad ochrony przed wyłudzaniem informacji lub wyświetleniu ustawień zostanie wyświetlona domyślna nazwa zasad kwarantanny.

       - **Dostarczanie komunikatu i dodawanie innych adresów do wiersza Bcc**
       - **Usuń wiadomość przed jej dostarczeniem**

     - **Jeśli komunikat zostanie wykryty jako sfałszowany**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz analizę fałszowania** na poprzedniej stronie. Wybierz jedną z następujących akcji na liście rozwijanej dla komunikatów od zablokowanych sfałszowanych nadawców:
       - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
       - **Kwarantanna komunikatu: Po wybraniu** tej akcji zostanie **wyświetlone pole Zastosuj zasady kwarantanny** , w którym wybierzesz zasady kwarantanny, które mają zastosowanie do komunikatów poddawanych kwarantannie przez ochronę przed fałszowaniem danych wywiadowczych. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

         Pusta wartość **zasad kwarantanny Zastosuj** oznacza, że są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy na potrzeby wykrywania fałszywych informacji wywiadowczych). Po późniejszej edycji zasad ochrony przed wyłudzaniem informacji lub wyświetleniu ustawień zostanie wyświetlona domyślna nazwa zasad kwarantanny.

   - **Wskazówki dotyczące bezpieczeństwa & wskaźniki**: Skonfiguruj następujące ustawienia:
     - **Pokaż porada dotycząca bezpieczeństwa pierwszego kontaktu**: Aby uzyskać więcej informacji, zobacz [First contact porada dotycząca bezpieczeństwa ( Pierwszy kontakt porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip)).
     - **Pokaż porada dotycząca bezpieczeństwa personifikacji użytkownika**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz ochronę użytkowników** na poprzedniej stronie.
     - **Pokaż porada dotycząca bezpieczeństwa personifikacji domeny**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz domeny do ochrony** na poprzedniej stronie.
     - **Pokaż nietypowe znaki personifikacji użytkownika porada dotycząca bezpieczeństwa** To ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz użytkowników do ochrony** lub **włącz ochronę domen** na poprzedniej stronie.
     - **Pokaż (?) dla nieuwierzytelnionych nadawców pod kątem fałszowania**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz analizę fałszowania** na poprzedniej stronie. Dodaje znak zapytania (?) do zdjęcia nadawcy w polu Od w Outlook, jeśli komunikat nie przechodzi testów SPF lub DKIM **, a** komunikat nie przekazuje [uwierzytelniania DMARC lub uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication).
     - **Pokaż tag "via"**: to ustawienie jest dostępne tylko wtedy, gdy **wybrano opcję Włącz analizę fałszowania** na poprzedniej stronie. Dodaje tag via (chris@contoso.com za pośrednictwem fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub **adresIE MAIL FROM** . Wartość domyślna jest włączona (wybrana). Aby go wyłączyć, wyczyść pole wyboru.

     Aby włączyć ustawienie, zaznacz pole wyboru. Aby go wyłączyć, wyczyść pole wyboru.

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na wyświetlonej stronie **Przegląd** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

8. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Wyświetlanie zasad ochrony przed wyłudzaniem informacji za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady  współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** **— zasady ochrony przed wyłudzaniem** \> informacji w sekcji Zasady.

2. Na stronie **Ochrona przed wyłudzaniem informacji** na liście zasad ochrony przed wyłudzaniem informacji są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Ostatnia modyfikacja**

3. Po wybraniu zasad przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Modyfikowanie zasad ochrony przed wyłudzaniem informacji za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& zasady ochrony** \> **przed wyłudzaniem**  \> informacji w sekcji Zasady. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** wybierz zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwu szczegółów zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat ustawień, zobacz [sekcję Używanie portalu Microsoft 365 Defender do tworzenia zasad ochrony przed wyłudzaniem informacji](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) we wcześniejszej części tego artykułu.

   W przypadku domyślnych zasad ochrony przed wyłudzaniem informacji sekcja **Użytkownicy, grupy i domeny** nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić nazwy zasad.

Aby włączyć lub wyłączyć zasady lub ustawić kolejność priorytetów zasad, zobacz następujące sekcje.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Włączanie lub wyłączanie niestandardowych zasad ochrony przed wyłudzaniem informacji

Nie można wyłączyć domyślnych zasad ochrony przed wyłudzaniem informacji.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& zasady ochrony** \> **przed wyłudzaniem**  \> informacji w sekcji Zasady. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** wybierz z listy zasady niestandardowe, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz jedną z następujących wartości:
   - **Zasady wyłączone**: aby włączyć zasady, kliknij pozycję ![Włącz ikonę.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz pozycję** .
   - **Zasady włączone**: aby wyłączyć zasady, kliknij pozycję Wyłącz ikonę ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij pozycję **Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanym oknie szczegółów zasad.

Po powrocie na stronę zasad głównych wartość **Stan** zasad będzie **włączona** lub **wyłączona**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Ustawianie priorytetu niestandardowych zasad ochrony przed wyłudzaniem informacji

Domyślnie zasady ochrony przed wyłudzaniem informacji mają priorytet oparty na kolejności, w jakiej zostały utworzone (nowsze zasady mają niższy priorytet niż starsze zasady). Niższy numer priorytetu wskazuje wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

Aby zmienić priorytet zasad, kliknij pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** we właściwościach zasad (nie możesz bezpośrednio zmodyfikować numeru **Priorytet** w portalu Microsoft 365 Defender). Zmiana priorytetu zasad ma sens tylko wtedy, gdy masz wiele zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender można zmienić priorytet zasad ochrony przed wyłudzaniem informacji dopiero po jego utworzeniu. W programie PowerShell można zastąpić priorytet domyślny podczas tworzenia reguły anty-phish (co może mieć wpływ na priorytet istniejących reguł).
- Zasady ochrony przed wyłudzaniem informacji są przetwarzane w kolejności ich wyświetlania (pierwsze zasady mają wartość **Priorytet** 0). Domyślne zasady ochrony przed wyłudzaniem informacji mają wartość priorytetu **Najniższa** i nie można jej zmienić.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& zasady ochrony** \> **przed wyłudzaniem**  \> informacji w sekcji Zasady. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** wybierz z listy zasady niestandardowe, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** na podstawie bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady z **wartością Priorytet** **0** mają dostępną tylko opcję **Zmniejsz priorytet** .
   - Zasady z najniższą **wartością priorytetu** (na przykład **3**) mają dostępną tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, zasady między wartościami o najwyższym i najniższym priorytecie mają dostępne opcje **Zwiększanie priorytetu** i **Zmniejszanie priorytetu** .

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Zwiększ priorytet** lub ![Zmniejsz priorytet **ikona**](../../media/m365-cc-sc-decrease-icon.png) Zmniejsz priorytet, aby zmienić wartość **Priorytet**.

4. Po zakończeniu kliknij przycisk **Zamknij** w wysuwanym oknie szczegółów zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Usuwanie niestandardowych zasad ochrony przed wyłudzaniem informacji za pomocą portalu Microsoft 365 Defender

W przypadku korzystania z portalu Microsoft 365 Defender w celu usunięcia niestandardowych zasad ochrony przed wyłudzaniem informacji zarówno reguła anty-phish, jak i odpowiednie zasady anty-phish zostaną usunięte. Nie można usunąć domyślnych zasad ochrony przed wyłudzaniem informacji.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& zasady ochrony** \> **przed wyłudzaniem**  \> informacji w sekcji Zasady. Aby przejść bezpośrednio do strony **ochrony przed wyłudzaniem informacji** , użyj polecenia <https://security.microsoft.com/antiphishing>.

2. Na stronie **Ochrona przed wyłudzaniem informacji** wybierz z listy zasady niestandardowe, klikając nazwę zasad.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Usuń ikonę](../../media/m365-cc-sc-delete-icon.png) zasad **Usuń zasady**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Konfigurowanie zasad ochrony przed wyłudzaniem informacji przy użyciu programu Exchange Online PowerShell

Jak opisano wcześniej, zasady antyspamowe składają się z zasad anty-phish i reguły anty-phish.

W Exchange Online programu PowerShell widoczna jest różnica między zasadami anty-phish i regułami anty-phish. Zasady antyfiszowe można zarządzać przy użyciu **\*poleceń cmdlet -AntiPhishPolicy** i zarządzać regułami antyfizowymi przy użyciu **\*poleceń cmdlet -AntiPhishRule** .

- W programie PowerShell najpierw utworzysz zasady anty-phish, a następnie utworzysz regułę anty-phish, która identyfikuje zasady, do których ma zastosowanie reguła.
- W programie PowerShell można oddzielnie modyfikować ustawienia zasad anty-phish i reguły anty-phish.
- Po usunięciu zasad anty-phish z programu PowerShell odpowiednia reguła anty-phish nie zostanie automatycznie usunięta i na odwrót.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Tworzenie zasad ochrony przed wyłudzaniem informacji przy użyciu programu PowerShell

Tworzenie zasad ochrony przed wyłudzaniem informacji w programie PowerShell to proces dwuetapowy:

1. Utwórz zasady anty-phish.
2. Utwórz regułę anty-phish określającą zasady anty-phish, do których ma zastosowanie reguła.

 **Uwagi**:

- Możesz utworzyć nową regułę anty-phish i przypisać do niej istniejące, nieskojarzone zasady anty-phish. Reguła anty-phish nie może być skojarzona z więcej niż jedną zasadą anty-phish.
- W programie PowerShell można skonfigurować następujące ustawienia dla nowych zasad anty-phish, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie zostaną utworzone zasady:
  - Utwórz nowe zasady jako wyłączone (_włączone_ `$false` w poleceniu cmdlet **New-AntiPhishRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) w poleceniu cmdlet **New-AntiPhishRule**).
- Nowe zasady anty-phish utworzone w programie PowerShell nie są widoczne w portalu Microsoft 365 Defender, dopóki zasady nie zostaną przypisane do reguły anty-phish.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Krok 1. Tworzenie zasad anty-phish przy użyciu programu PowerShell

Aby utworzyć zasady anty-phish, użyj tej składni:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

W tym przykładzie utworzono zasady anty-phish o nazwie Kwarantanna badań z następującymi ustawieniami:

- Zasady są włączone (nie używamy parametru _Włączone_ , a wartość domyślna to `$true`).
- Opis: Zasady działu badań.
- Zmienia domyślną akcję wykrywania fałszowania na Kwarantanna i używa domyślnych [zasad kwarantanny](quarantine-policies.md) dla komunikatów poddanych kwarantannie (nie używamy parametru _SpoofQuarantineTag_ ).
- Umożliwia ochronę domen organizacji dla wszystkich zaakceptowanych domen i ochronę domen docelowych dla fabrikam.com.
- Określa kwarantannę jako akcję wykrywania personifikacji domeny i używa domyślnych [zasad kwarantanny](quarantine-policies.md) dla komunikatów poddanych kwarantannie (nie używamy parametru _TargetedDomainQuarantineTag_ ).
- Określa mai Fujito (mfujito@fabrikam.com) jako użytkownika do ochrony przed personifikacją.
- Określa kwarantannę jako akcję wykrywania personifikacji użytkownika i używa domyślnych [zasad kwarantanny](quarantine-policies.md) dla komunikatów poddanych kwarantannie (nie używamy _parametru TargetedUserQuarantineTag_ ).
- Włącza analizę skrzynek pocztowych (_EnableMailboxIntelligence_), umożliwia ochronę inteligencji skrzynek pocztowych w celu podjęcia akcji na komunikatach (_EnableMailboxIntelligenceProtection_), określa kwarantannę jako akcję dla wykrytych wiadomości i używa domyślnych [zasad kwarantanny](quarantine-policies.md) dla komunikatów poddanych kwarantannie (nie używamy parametru _MailboxIntelligenceQuarantineTag_ ).
- Włącza wszystkie wskazówki dotyczące bezpieczeństwa.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach anty-phish, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Krok 2. Tworzenie reguły anty-phish przy użyciu programu PowerShell

Aby utworzyć regułę anty-phish, użyj tej składni:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie utworzono regułę anty-phish o nazwie Dział badań z następującymi warunkami:

- Reguła jest skojarzona z zasadami anty-phish o nazwie Kwarantanna badań.
- Reguła ma zastosowanie do członków grupy o nazwie Dział badań.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Używanie programu PowerShell do wyświetlania zasad anty-phish

Aby wyświetlić istniejące zasady anty-phish, użyj następującej składni:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich zasad anty-phish wraz z określonymi właściwościami.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Ten przykład zwraca wszystkie wartości właściwości dla zasad anty-phish o nazwie Kierownictwo.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Wyświetlanie reguł anty-phish za pomocą programu PowerShell

Aby wyświetlić istniejące reguły anty-phish, użyj następującej składni:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich reguł anty-phish wraz z określonymi właściwościami.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Aby filtrować listę według reguł włączonych lub wyłączonych, uruchom następujące polecenia:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Ten przykład zwraca wszystkie wartości właściwości dla reguły anty-phish o nazwie Contoso Executives.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Modyfikowanie zasad anty-phish przy użyciu programu PowerShell

Inne niż następujące elementy te same ustawienia są dostępne podczas modyfikowania zasad anty-phish w programie PowerShell, jak podczas tworzenia zasad zgodnie z opisem w [kroku 1: Użyj programu PowerShell, aby utworzyć zasady anty-phish](#step-1-use-powershell-to-create-an-anti-phish-policy) sekcji wcześniej w tym artykule.

- Przełącznik _MakeDefault_ , który zamienia określone zasady w zasady domyślne (stosowane do wszystkich użytkowników, zawsze **najniższy** priorytet i nie można go usunąć) jest dostępny tylko po zmodyfikowaniu zasad anty-phish w programie PowerShell.

- Nie można zmienić nazwy zasad anty-phish (polecenie cmdlet **Set-AntiPhishPolicy** nie ma parametru _Name_ ). Po zmianie nazwy zasad ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender zmieniasz tylko nazwę _reguły_ anty-phish.

Aby zmodyfikować zasady anty-phish, użyj tej składni:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach anty-phish, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Modyfikowanie reguł anty-phish przy użyciu programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły anty-phish w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły anty-phish, zobacz następną sekcję.

W przeciwnym razie podczas modyfikowania reguły anty-phish w programie PowerShell nie są dostępne żadne dodatkowe ustawienia. Te same ustawienia są dostępne podczas tworzenia reguły zgodnie z opisem w sekcji [Krok 2: Używanie programu PowerShell do utworzenia reguły anty-phish we wcześniejszej](#step-2-use-powershell-to-create-an-anti-phish-rule) części tego artykułu.

Aby zmodyfikować regułę anty-phish, użyj tej składni:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Używanie programu PowerShell do włączania lub wyłączania reguł anty-phish

Włączenie lub wyłączenie reguły anty-phish w programie PowerShell włącza lub wyłącza całe zasady ochrony przed wyłudzaniem informacji (reguła anty-phish i przypisane zasady anty-phish). Nie można włączyć ani wyłączyć domyślnych zasad ochrony przed wyłudzaniem informacji (są zawsze stosowane do wszystkich adresatów).

Aby włączyć lub wyłączyć regułę anty-phish w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Ten przykład wyłącza regułę anty-phish o nazwie Dział marketingu.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

W tym przykładzie włączono tę samą regułę.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) i [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Ustawianie priorytetu reguł anty-phish przy użyciu programu PowerShell

Wartość o najwyższym priorytecie, którą można ustawić dla reguły, to 0. Najniższa wartość, którą można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć kaskadowy wpływ na inne reguły. Jeśli na przykład masz pięć reguł niestandardowych (priorytety od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły anty-phish w programie PowerShell, użyj następującej składni:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie ustawiono priorytet reguły o nazwie Dział marketingu na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich priorytety są zwiększane o 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj parametru _Priority_ w poleceniu cmdlet **New-AntiPhishRule** .

- Domyślne zasady anty-phish nie ma odpowiedniej reguły anty-phish i zawsze ma niemodyfikowalną wartość priorytetu **Najniższa**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Usuwanie zasad anty-phish przy użyciu programu PowerShell

W przypadku korzystania z programu PowerShell w celu usunięcia zasad anty-phish odpowiednia reguła anty-phish nie zostanie usunięta.

Aby usunąć zasady anty-phish w programie PowerShell, użyj tej składni:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

W tym przykładzie usuwa zasady anty-phish o nazwie Dział marketingu.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Usuwanie reguł anty-phish przy użyciu programu PowerShell

Jeśli używasz programu PowerShell do usunięcia reguły anty-phish, odpowiednie zasady anty-phish nie zostaną usunięte.

Aby usunąć regułę anty-phish w programie PowerShell, użyj tej składni:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

W tym przykładzie usunięto regułę anty-phish o nazwie Dział marketingu.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy zasady ochrony przed wyłudzaniem informacji zostały pomyślnie skonfigurowane w Ochrona usługi Office 365 w usłudze Defender, wykonaj dowolne z następujących czynności:

- Na stronie **Ochrona przed wyłudzaniem informacji** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/antiphishing>sprawdź listę zasad, ich wartości **stanu** i wartości **Priorytet**. Aby wyświetlić więcej szczegółów, wybierz zasady z listy, klikając nazwę i wyświetlając szczegóły w wyświetlonym wysuwie.

- W Exchange Online programu PowerShell zastąp \<Name\> ciąg nazwą zasad lub reguły, a następnie uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
