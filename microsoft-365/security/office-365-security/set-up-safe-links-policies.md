---
title: Konfigurowanie zasad linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać zasady linków Sejf i globalne ustawienia linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 867d055c44ba0d0ae0b7b763bc556a06f16e5cd8
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847107"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Konfigurowanie zasad linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym, który szuka informacji o safelinkach w Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Linki w [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) udostępnia skanowanie adresów URL przychodzących wiadomości e-mail w przepływie poczty oraz czas weryfikacji kliknięć adresów URL i linków w wiadomościach e-mail i innych lokalizacjach. Aby uzyskać więcej informacji, zobacz [linki Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](safe-links.md).

Mimo że nie ma domyślnych zasad Sejf Łącza, wstępnie ustawione zasady zabezpieczeń **wbudowanej ochrony** zapewniają ochronę Sejf Łącza wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Łącza). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)).

Procedury przedstawione w tym artykule umożliwiają również tworzenie zasad linków Sejf, które mają zastosowanie do określonych użytkowników, grup lub domen.

> [!NOTE]
>
> Ustawienia globalne ochrony linków Sejf **poza** zasadami linków Sejf. Aby uzyskać instrukcje, zobacz [Konfigurowanie ustawień globalnych dla linków Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-global-settings-for-safe-links.md).
>
> Administratorzy powinni wziąć pod uwagę różne ustawienia konfiguracji linków Sejf. Jedną z dostępnych opcji jest uwzględnienie informacji możliwych do zidentyfikowania przez użytkownika w Sejf Linkach. Ta funkcja umożliwia zespołom operacji zabezpieczeń (SecOps) badanie potencjalnego naruszenia bezpieczeństwa użytkownika, podjęcie działań naprawczych i ograniczenie kosztownych naruszeń.

Zasady linków Sejf można skonfigurować w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla kwalifikujących się organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe, ale z Ochrona usługi Office 365 w usłudze Microsoft Defender subskrypcjami dodatków).

Podstawowe elementy zasad linków Sejf to:

- **Zasady bezpiecznych łączy**: włącz ochronę Sejf Łącza, włącz skanowanie adresów URL w czasie rzeczywistym, określ, czy czekać na ukończenie skanowania w czasie rzeczywistym przed dostarczeniem komunikatu, włącz skanowanie w poszukiwaniu komunikatów wewnętrznych, określ, czy chcesz śledzić kliknięcia adresów URL użytkowników, i określ, czy zezwolić użytkownikom na kliknięcie koryta do oryginalnego adresu URL.
- **Reguła bezpiecznych łączy**: określa filtry priorytetu i adresata (do kogo mają zastosowanie zasady).

Różnica między tymi dwoma elementami nie jest oczywista podczas zarządzania zasadami Sejf Links w portalu Microsoft 365 Defender:

- Podczas tworzenia zasad Sejf Links tworzysz regułę bezpiecznych łączy i skojarzone zasady bezpiecznych łączy w tym samym czasie, używając tej samej nazwy dla obu.
- Podczas modyfikowania zasad Sejf Łącza ustawienia związane z nazwą, priorytetem, włączoną lub wyłączoną, a filtry adresatów modyfikują regułę bezpiecznych łączy. Wszystkie inne ustawienia modyfikują skojarzone zasady bezpiecznych łączy.
- Po usunięciu zasad Sejf Łącza zostanie usunięta reguła bezpiecznych łączy i skojarzone zasady bezpiecznych łączy.

W programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP zasady i reguła są zarządzane oddzielnie. Aby uzyskać więcej informacji, zobacz sekcję [Use Exchange Online PowerShell or standalone EOP PowerShell to configure Sejf Links policies (Konfigurowanie zasad łączy Sejf)](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) w dalszej części tego artykułu.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **łącza Sejf**, użyj polecenia <https://security.microsoft.com/safelinksv2>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia:
  - Aby tworzyć, modyfikować i usuwać zasady linków Sejf, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** w portalu Microsoft 365 Defender **i** członkiem grupy ról **Zarządzanie organizacją** w Exchange Online.
  - Aby uzyskać dostęp tylko do odczytu do zasad łączy Sejf, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń**.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md) i [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  . — Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z naszymi zalecanymi ustawieniami zasad Sejf Łącza, zobacz [ustawienia zasad Sejf Linki](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Zaczekaj do 6 godzin na zastosowanie nowych lub zaktualizowanych zasad.

- [Nowe funkcje są stale dodawane do Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Po dodaniu nowych funkcji może być konieczne wprowadzenie zmian w istniejących zasadach linków Sejf.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Tworzenie zasad linków Sejf przy użyciu portalu Microsoft 365 Defender

Utworzenie niestandardowych zasad łączy Sejf w portalu Microsoft 365 Defender tworzy regułę bezpiecznych łączy i skojarzone zasady bezpiecznych łączy w tym samym czasie przy użyciu tej samej nazwy dla obu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady reguł** \> **zagrożeń** \> **Sejf Linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **łącza Sejf**, użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **łącza Sejf** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie otwarty kreator **zasad Nowe linki Sejf**. Na stronie **Nazwa zasad** skonfiguruj następujące ustawienia:

   - **Nazwa**: wprowadź unikatową, opisową nazwę zasad.
   - **Opis**: wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na wyświetlonej stronie **Użytkownicy i domeny** zidentyfikuj wewnętrznych adresatów, których dotyczą zasady (warunki adresatów):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty e-mail.
   - **Grupy**:
     - Członkowie określonych grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty.
     - Określona Grupy Microsoft 365.
   - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników, grupy i domeny**: aby dodać wyjątki dla wewnętrznych adresatów, których dotyczą zasady (wyjątki adresatów), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na wyświetlonej stronie **Ustawienia ochrony** skonfiguruj następujące ustawienia:
   - **Wybierz akcję dla nieznanych potencjalnie złośliwych adresów URL w wiadomościach**: wybierz pozycję **Włączone**, aby włączyć ochronę Sejf Łącza dla linków w wiadomościach e-mail. Jeśli to ustawienie zostanie włączone, dostępne są następujące ustawienia:
     - **Zastosuj skanowanie adresów URL w czasie rzeczywistym w poszukiwaniu podejrzanych linków i linków wskazujących pliki**: wybierz tę opcję, aby włączyć skanowanie łączy w czasie rzeczywistym w wiadomościach e-mail. Jeśli to ustawienie zostanie włączone, dostępne jest następujące ustawienie:
       - **Poczekaj na ukończenie skanowania adresu URL przed dostarczeniem komunikatu**: wybierz tę opcję, aby poczekać na ukończenie skanowania adresu URL w czasie rzeczywistym przed dostarczeniem komunikatu.
     - **Zastosuj Sejf Łącza do wiadomości e-mail wysyłanych w organizacji**: wybierz tę opcję, aby zastosować zasady linków Sejf do komunikatów między nadawcami wewnętrznymi i odbiorcami wewnętrznymi.
   - **Wybierz akcję dla nieznanych lub potencjalnie złośliwych adresów URL w Microsoft Teams**: wybierz pozycję **Włączone**, aby włączyć ochronę linków Sejf dla linków w Teams. Należy pamiętać, że zastosowanie tego ustawienia może potrwać do 24 godzin.
   - **Śledzenie kliknięć użytkownika**: pozostaw wybraną opcję, aby włączyć śledzenie kliknięć adresów URL w wiadomościach e-mail.
   - **Zezwalaj użytkownikom na klikanie oryginalnego adresu URL**: wyczyść tę opcję, aby uniemożliwić użytkownikom klikanie oryginalnego adresu URL [na stronach ostrzegawczych](safe-links.md#warning-pages-from-safe-links).
   - **Nie należy ponownie pisać następujących adresów URL**: zezwala na dostęp do określonych adresów URL, które w przeciwnym razie byłyby blokowane przez Sejf Łącza.

     W polu wpisz żądany adres URL lub wartość, a następnie kliknij przycisk **Dodaj**. Powtórz ten krok tyle razy, ile jest to konieczne.

     Aby usunąć istniejący wpis, kliknij przycisk ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wpisu.

     Aby uzyskać składnię wpisu, zobacz [Składnia wpisu dla listy "Nie przepisuj ponownie następujących adresów URL"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Aby uzyskać szczegółowe informacje na temat tych ustawień, zobacz [Sejf Ustawienia linków dla wiadomości e-mail](safe-links.md#safe-links-settings-for-email-messages) i [ustawień linków Sejf dla Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Aby uzyskać więcej zalecanych wartości dla standardowych i ścisłych ustawień zasad, zobacz [ustawienia zasad Sejf Łącza](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na wyświetlonej stronie **Powiadomienie** wybierz jedną z następujących wartości dla pozycji **Jak chcesz powiadomić użytkowników?**:
   - **Użyj domyślnego tekstu powiadomienia**
   - **Użyj niestandardowego tekstu powiadomienia**: Jeśli wybierzesz tę wartość (długość nie może przekraczać 200 znaków), zostaną wyświetlone następujące ustawienia:
     - **Używanie Microsoft Translator do automatycznej lokalizacji**
     - **Niestandardowy tekst powiadomienia**: wprowadź tekst powiadomienia niestandardowego w tym polu.

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na wyświetlonej stronie **Przegląd** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

8. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Wyświetlanie zasad linków Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady reguł** \> **zagrożeń** \> **Sejf Linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **łącza Sejf**, użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **łącza Sejf** następujące właściwości są wyświetlane na liście zasad linków Sejf:
   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**

3. Po wybraniu zasad przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Modyfikowanie zasad łączy Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender przejdź  do sekcji \> **Zasady & reguły zagrożeń** \> **zasady** \> **Sejf linki**.

2. Na stronie **Sejf Linki** wybierz zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwu szczegółów zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat ustawień, zobacz poprzednią sekcję [Używanie portalu Microsoft 365 Defender do tworzenia zasad linków Sejf](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) w tym artykule.

Aby włączyć lub wyłączyć zasady lub ustawić kolejność priorytetów zasad, zobacz następujące sekcje.

### <a name="enable-or-disable-safe-links-policies"></a>Włączanie lub wyłączanie zasad linków Sejf

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady reguł** \> **zagrożeń** \> **Sejf Linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **łącza Sejf**, użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **Sejf Linki** wybierz zasady z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz jedną z następujących wartości:
   - **Zasady wyłączone**: aby włączyć zasady, kliknij pozycję ![Włącz ikonę.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz pozycję** .
   - **Zasady włączone**: aby wyłączyć zasady, kliknij pozycję Wyłącz ikonę ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij pozycję **Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanym oknie szczegółów zasad.

Po powrocie na stronę zasad głównych wartość **Stan** zasad będzie **włączona** lub **wyłączona**.

### <a name="set-the-priority-of-safe-links-policies"></a>Ustawianie priorytetu zasad łączy Sejf

Domyślnie Sejf Linki mają priorytet oparty na kolejności, w jakiej zostały utworzone (nowsze zasady mają niższy priorytet niż starsze zasady). Niższy numer priorytetu wskazuje wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

Aby zmienić priorytet zasad, kliknij pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** we właściwościach zasad (nie możesz bezpośrednio zmodyfikować numeru **Priorytet** w portalu Microsoft 365 Defender). Zmiana priorytetu zasad ma sens tylko wtedy, gdy masz wiele zasad.

**Uwaga**:

- W portalu Microsoft 365 Defender można zmienić priorytet zasad Sejf Łącza tylko po jego utworzeniu. W programie PowerShell można zastąpić priorytet domyślny podczas tworzenia reguły bezpiecznych łączy (co może mieć wpływ na priorytet istniejących reguł).
- Sejf Zasady linków są przetwarzane w kolejności ich wyświetlania (pierwsza zasada ma wartość **Priorytet** 0). Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady reguł** \> **zagrożeń** \> **Sejf Linki** w sekcji Zasady. Aby przejść bezpośrednio do strony **łącza Sejf**, użyj polecenia <https://security.microsoft.com/safelinksv2>.

2. Na stronie **Sejf Linki** wybierz zasady z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** na podstawie bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady z **wartością Priorytet** **0** mają dostępną tylko opcję **Zmniejsz priorytet** .
   - Zasady z najniższą **wartością priorytetu** (na przykład **3**) mają dostępną tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, zasady między wartościami o najwyższym i najniższym priorytecie mają dostępne opcje **Zwiększanie priorytetu** i **Zmniejszanie priorytetu** .

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Zwiększ priorytet** lub ![Zmniejsz priorytet **ikona**](../../media/m365-cc-sc-decrease-icon.png) Zmniejsz priorytet, aby zmienić wartość **Priorytet**.

4. Po zakończeniu kliknij przycisk **Zamknij** w wysuwanym oknie szczegółów zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Usuwanie zasad linków Sejf przy użyciu portalu Microsoft 365 Defender

1. W  portalu Microsoft 365 Defender przejdź do pozycji Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące zagrożeń** \>  \> **Sejf Linki** w sekcji Zasady.

2. Na stronie **Sejf Linki** wybierz zasady z listy, klikając nazwę. W górnej części wyświetlonego menu wysuwanego szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Usuń ikonę](../../media/m365-cc-sc-delete-icon.png) zasad **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Konfigurowanie zasad linków Sejf przy użyciu Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP

Zgodnie z wcześniejszym opisem zasady Sejf Links składają się z zasad bezpiecznych łączy i reguły bezpiecznych łączy.

W programie PowerShell widoczna jest różnica między zasadami bezpiecznych łączy a regułami bezpiecznych łączy. Zasady bezpiecznych łączy można zarządzać przy użyciu **\*poleceń cmdlet -SafeLinksPolicy** i zarządzać regułami bezpiecznych łączy przy użyciu **\*poleceń cmdlet -SafeLinksRule** .

- W programie PowerShell najpierw tworzysz zasady bezpiecznych łączy, a następnie tworzysz regułę bezpiecznych łączy, która identyfikuje zasady, do których ma zastosowanie reguła.
- W programie PowerShell ustawienia zasad bezpiecznych łączy i reguły bezpiecznych łączy są modyfikowane oddzielnie.
- Po usunięciu zasad bezpiecznych łączy z programu PowerShell odpowiednia reguła bezpiecznych łączy nie zostanie automatycznie usunięta i na odwrót.

### <a name="use-powershell-to-create-safe-links-policies"></a>Tworzenie zasad linków Sejf przy użyciu programu PowerShell

Tworzenie zasad linków Sejf w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady bezpiecznych łączy.
2. Utwórz regułę bezpiecznych łączy określającą zasady bezpiecznych łączy, do których ma zastosowanie reguła.

> [!NOTE]
>
> - Możesz utworzyć nową regułę bezpiecznych łączy i przypisać do niej istniejące, nieskojarzone zasady bezpiecznych łączy. Reguły bezpiecznych łączy nie można skojarzyć z więcej niż jedną zasadą bezpiecznych łączy.
>
> - W programie PowerShell można skonfigurować następujące ustawienia dla nowych zasad bezpiecznych linków, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie zostaną utworzone zasady:
>   - Utwórz nowe zasady jako wyłączone (_włączone_ `$false` w poleceniu cmdlet **New-SafeLinksRule** ).
>   - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) w poleceniu cmdlet **New-SafeLinksRule**).
>
> - Nowe zasady bezpiecznych łączy utworzone w programie PowerShell nie są widoczne w portalu Microsoft 365 Defender, dopóki zasady nie zostaną przypisane do reguły bezpiecznych łączy.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Krok 1. Tworzenie zasad bezpiecznych łączy przy użyciu programu PowerShell

Aby utworzyć zasady bezpiecznych łączy, użyj tej składni:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Aby uzyskać szczegółowe informacje o składni wpisu do użycia dla parametru _DoNotRewriteUrls_ , zobacz [Składnia wpisu dla listy "Nie przepisuj ponownie następujących adresów URL"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).
>
> - Aby uzyskać dodatkową składnię, która może być używana dla parametru _DoNotRewriteUrls_ podczas modyfikowania istniejących zasad bezpiecznych łączy przy użyciu polecenia cmdlet **Set-SafeLinksPolicy** , zobacz sekcję [Używanie programu PowerShell do modyfikowania zasad bezpiecznych łączy](#use-powershell-to-modify-safe-links-policies) w dalszej części tego artykułu.

W tym przykładzie tworzone są zasady bezpiecznych łączy o nazwie Contoso All z następującymi wartościami:

- Włącz skanowanie i ponowne zapisywanie adresów URL w wiadomościach e-mail.
- Włącz skanowanie adresów URL w Teams.
- Włącz skanowanie w czasie rzeczywistym klikniętych adresów URL, w tym klikniętych linków wskazujących pliki.
- Przed dostarczeniem komunikatu poczekaj na ukończenie skanowania adresu URL.
- Włącz skanowanie i ponowne zapisywanie adresów URL dla komunikatów wewnętrznych.
- Śledzenie kliknięć użytkowników związanych z ochroną linków Sejf (nie używamy _parametru TrackUserClicks_, a wartość domyślna to $true).
- Nie zezwalaj użytkownikom na klikanie oryginalnego adresu URL.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Krok 2. Tworzenie reguły bezpiecznych łączy przy użyciu programu PowerShell

Aby utworzyć regułę bezpiecznych łączy, użyj tej składni:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

W tym przykładzie zostanie utworzona reguła bezpiecznych łączy o nazwie Contoso All z następującymi warunkami:

- Reguła jest skojarzona z zasadami bezpiecznych łączy o nazwie Contoso All.
- Reguła ma zastosowanie do wszystkich adresatów w domenie contoso.com.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.
- Reguła jest włączona (nie używamy parametru _Enabled_ , a wartość domyślna to `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Używanie programu PowerShell do wyświetlania zasad bezpiecznych łączy

Aby wyświetlić istniejące zasady bezpiecznych łączy, użyj następującej składni:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich zasad bezpiecznych łączy.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

Ten przykład zwraca szczegółowe informacje dotyczące zasad bezpiecznych łączy o nazwie Kierownictwo firmy Contoso.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Wyświetlanie reguł bezpiecznych łączy przy użyciu programu PowerShell

Aby wyświetlić istniejące reguły bezpiecznych łączy, użyj następującej składni:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich reguł bezpiecznych łączy.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Aby filtrować listę według reguł włączonych lub wyłączonych, uruchom następujące polecenia:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

Ten przykład zwraca szczegółowe informacje dotyczące reguły bezpiecznych łączy o nazwie Kierownictwo firmy Contoso.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Modyfikowanie zasad bezpiecznych łączy przy użyciu programu PowerShell

Nie można zmienić nazwy zasad bezpiecznych łączy w programie PowerShell (polecenie cmdlet **Set-SafeLinksPolicy** nie ma parametru _Name_ ). Po zmianie nazwy zasad Sejf Links w portalu Microsoft 365 Defender zmieniasz tylko nazwę _reguły_ bezpiecznych łączy.

Jedyną dodatkową kwestią dotyczącą modyfikowania zasad bezpiecznych linków w programie PowerShell jest dostępna składnia parametru _DoNotRewriteUrls_ ( [lista "Nie przepisuj ponownie następujących adresów URL](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)"):

- Aby dodać wartości, które zastąpią wszystkie istniejące wpisy, użyj następującej składni: `"Entry1","Entry2,..."EntryN"`.
- Aby dodać lub usunąć wartości bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

W przeciwnym razie te same ustawienia są dostępne podczas tworzenia zasad bezpiecznych łączy zgodnie z opisem w sekcji [Krok 1: Tworzenie zasad bezpiecznych łączy za pomocą programu PowerShell we wcześniejszej](#step-1-use-powershell-to-create-a-safe-links-policy) części tego artykułu.

Aby zmodyfikować zasady bezpiecznych łączy, użyj tej składni:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Modyfikowanie reguł bezpiecznych łączy przy użyciu programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły bezpiecznych łączy w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły bezpiecznych łączy, zobacz następną sekcję.

W przeciwnym razie te same ustawienia są dostępne podczas tworzenia reguły zgodnie z opisem w sekcji [Krok 2: Tworzenie reguły bezpiecznych łączy za pomocą programu PowerShell we wcześniejszej](#step-2-use-powershell-to-create-a-safe-links-rule) części tego artykułu.

Aby zmodyfikować regułę bezpiecznych łączy, użyj tej składni:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Włączanie lub wyłączanie reguł bezpiecznych łączy przy użyciu programu PowerShell

Włączenie lub wyłączenie reguły bezpiecznych łączy w programie PowerShell włącza lub wyłącza całe zasady Sejf Łącza (reguła bezpiecznych łączy i przypisane zasady bezpiecznych łączy).

Aby włączyć lub wyłączyć regułę bezpiecznych łączy w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

Ten przykład wyłącza regułę bezpiecznych łączy o nazwie Dział marketingu.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

W tym przykładzie włączono tę samą regułę.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) i [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Ustawianie priorytetu reguł bezpiecznych łączy przy użyciu programu PowerShell

Wartość o najwyższym priorytecie, którą można ustawić dla reguły, to 0. Najniższa wartość, którą można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć kaskadowy wpływ na inne reguły. Jeśli na przykład masz pięć reguł niestandardowych (priorytety od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły bezpiecznych łączy w programie PowerShell, użyj następującej składni:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie ustawiono priorytet reguły o nazwie Dział marketingu na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich priorytety są zwiększane o 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj parametru _Priority_ w poleceniu cmdlet **New-SafeLinksRule** .

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Usuwanie zasad bezpiecznych łączy przy użyciu programu PowerShell

W przypadku korzystania z programu PowerShell w celu usunięcia zasad bezpiecznych łączy odpowiednia reguła bezpiecznych łączy nie zostanie usunięta.

Aby usunąć zasady bezpiecznych łączy w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

W tym przykładzie usunięto zasady bezpiecznych łączy o nazwie Dział marketingu.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Usuwanie reguł bezpiecznych łączy przy użyciu programu PowerShell

Jeśli używasz programu PowerShell do usunięcia reguły bezpiecznych łączy, odpowiednie zasady bezpiecznych łączy nie zostaną usunięte.

Aby usunąć regułę bezpiecznych łączy w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

W tym przykładzie usunięto regułę bezpiecznych łączy o nazwie Dział marketingu.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Aby sprawdzić, czy Sejf Links skanuje komunikaty, sprawdź dostępne Ochrona usługi Office 365 w usłudze Microsoft Defender raporty. Aby uzyskać więcej informacji, zobacz [Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md) i [Korzystanie z Eksploratora w portalu Microsoft 365 Defender](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy pomyślnie utworzono, zmodyfikowano lub usunięto zasady linków Sejf, wykonaj dowolne z następujących czynności:

- Na stronie **linki Sejf** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/safelinksv2>sprawdź listę zasad, ich wartości **stanu** i wartości **Priorytet**. Aby wyświetlić więcej szczegółów, wybierz zasady z listy i wyświetl szczegóły w wysuwanej oknie.

- W Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell zastąp \<Name\> ciąg nazwą zasad lub reguły, uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
