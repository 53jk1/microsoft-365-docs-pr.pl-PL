---
title: Ocenianie wpisu w zabezpieczeniach za pomocą programu Microsoft Secure Score
description: W tym artykule opisano, jak podjąć działania w celu poprawienia wyniku bezpiecznego wyniku firmy Microsoft w Microsoft 365 Defender sieci Microsoft 365 Defender sieci.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal, improvement actions
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: ee2aadd844eebf6da436c1d6d02b6244f093bfd6
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013666"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>Ocenianie postawy dotyczącej zabezpieczeń za pomocą programu Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score to miara stanu zabezpieczeń organizacji. Wyższa liczba oznacza więcej działań usprawnień. Można go znaleźć w https://security.microsoft.com/securescore portalu [Microsoft 365 Defender.](microsoft-365-defender.md)

Aby szybciej znaleźć potrzebne informacje, działania udoskonalania firmy Microsoft są zorganizowane w grupy:

- Tożsamość (Azure Active Directory kont & ról)
- Device (Microsoft Defender for Endpoint, known as [Microsoft Secure Score for Devices](/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices))
- Aplikacje (poczta e-mail i aplikacje w chmurze, w tym Office 365 i Microsoft Defender dla aplikacji w chmurze)

>[!NOTE]
>W ostatniej wersji programu Microsoft Secure Score opublikowano ulepszony model oceniania, który tymczasowo niezgodne z bezpiecznym wynikiem tożsamości i interfejsem API Graph. [Wyświetl szczegóły](microsoft-secure-score-whats-new.md)

Na stronie przeglądu wyników bezpiecznego programu Microsoft możesz sprawdzić, jak punkty są podzielone między te grupy i jakie punkty są dostępne. Możesz również uzyskać widok całościowy wyniku, historycznego trendu bezpiecznego wyniku za pomocą porównań wzorcowych i priorytetowych działań udoskonalania, które można podjąć w celu poprawienia wyniku.

![Strona główna Secure Score.](../../media/secure-score/secure-score-home-page.png)

## <a name="check-your-current-score"></a>Sprawdzanie bieżącego wyniku

Aby sprawdzić bieżący wynik, przejdź do strony przeglądu Microsoft Secure Score i poszukaj kafelka z **tytułem Twój bezpieczny wynik**. Uzyskany wynik będzie wyświetlany jako wartość procentowa wraz z liczbą punktów, które udało Ci się zdobyć w łącznej liczbie możliwych punktów.

Ponadto, jeśli wybierzesz **przycisk Dołącz obok** wyniku, możesz wybrać różne widoki wyniku. Te różne widoki wyników będą wyświetlane na wykresie na kafelku wyników i na wykresie podziału punktów.

Poniżej przedstawiono wyniki, które można dodać do widoku ogólnego wyniku, aby uzyskać pełniejszą ilustrację ogólnego wyniku:

- **Planowany wynik**: Pokaż wynik prognozowany, gdy planowane akcje są ukończone
- **Bieżący wynik licencji**: Pokaż wynik, który można uzyskać przy użyciu bieżącej licencji firmy Microsoft
- **Osiągalny** wynik: pokaż wynik, który można uzyskać przy użyciu licencji firmy Microsoft i bieżącej akceptacji ryzyka

Widok ten będzie wyglądał tak, jeśli uwzględniono wszystkie możliwe widoki wyników:

![Bezpieczny wynik, w tym planowany wynik, bieżący wynik licencji i wynik, który można uzyskać.](../../media/secure-score/secure-score-achievable.png)

## <a name="take-action-to-improve-your-score"></a>Działanie w celu poprawienia wyniku

Na **karcie Akcje udoskonalania** są wyszczególnione zalecenia dotyczące zabezpieczeń dotyczące możliwych powierzchni ataków. Zawiera także ich status (do rozwiązania, zaplanowano, zaakceptowano ryzyko, rozwiązano za pośrednictwem innej firmy, rozwiązano w ramach alternatywnego wpływu i ukończono). Możesz wyszukiwać, filtrować i grupować wszystkie akcje udoskonalania.  

### <a name="ranking"></a>Klasyfikacja

Klasyfikacja opiera się na liczbie punktów, które pozostało do osiągnięcia, trudności z implementacją, wpływu użytkownika i złożoności. W przypadku akcji udoskonalania, które zostały sklasyfikowane jako pierwsze, pozostało wiele punktów z niskim poziomem trudności, wpływem użytkownika i złożonością.

### <a name="view-improvement-action-details"></a>Wyświetlanie szczegółów akcji udoskonalania

Po wybraniu określonej akcji udoskonalania zostanie wyświetlone wysuwanie pełnej strony.  

![Przykład wysuwu akcji udoskonalania.](../../media/secure-score/secure-score-improvement-action-details.png)

Aby ukończyć akcję, masz kilka możliwości:

- Wybierz **pozycję Zarządzaj** , aby przejść do ekranu konfiguracji i wprowadzić zmianę. Uzyskasz w ten sposób punkty, które są wartościowe, widoczne na wysuwanych akcjęch. Aktualizacja punktów trwa zwykle około 24 godzin.

- Wybierz **pozycję** Udostępnij, aby skopiować bezpośredni link do akcji udoskonalania. Możesz także wybrać platformę udostępniania linku, taką jak poczta e-mail, Microsoft Teams lub Microsoft Planner.

Dodaj **notatki** , aby śledzić postęp lub cokolwiek innego, co chcesz skomentować. Jeśli do akcji udoskonalania **dodasz** własne tagi, możesz filtrować je według tych tagów.

### <a name="choose-an-improvement-action-status"></a>Wybieranie stanu akcji udoskonalania

Wybierz dowolne statusy i zanotuj uwagi dotyczące działania udoskonalania.

- **Adres —** wiesz, że jest konieczne działanie ulepszeń i zaplanuj działanie w przyszłości. Ten stan dotyczy również akcji wykrytych jako częściowo, ale nie w pełni ukończone.
- **Planowane** — istnieją konkretne plany, aby ukończyć działanie ulepszeń.
- **Zaakceptowane ryzyko** — zabezpieczenia zawsze powinny być zrównoważone pod względami użyteczności i nie wszystkie zalecenia będą działać w Twoim środowisku. W takim przypadku możesz zaakceptować czynnik ryzyka lub pozostałe ryzyko, a nie chwalić działanie udoskonalania. Nie będziesz mieć żadnych punktów, ale akcja nie będzie już widoczna na liście działań udoskonalania. W dowolnym momencie możesz przejrzeć tę akcję w historii lub ją cofnąć.
- **Rozwiązane przez inną firmę** i Rozwiązane w ramach alternatywnego ograniczenia — działanie udoskonalania zostało już rozwiązane przez aplikację lub oprogramowanie innej firmy lub wewnętrzne narzędzie. Zyskasz punkty, na które warto akcję zwrócić uwagę, więc wynik lepiej odzwierciedla ogólną wartość zabezpieczeń. Jeśli narzędzie innej firmy lub wewnętrzne nie przykrywa już tej kontroli, możesz wybrać inny stan. Pamiętaj, że firma Microsoft nie będzie mieć wglądu w kompletność wdrożenia, jeśli działanie udoskonalania zostanie oznaczone jako jeden z tych stanów.

#### <a name="threat--vulnerability-management-improvement-actions"></a>Działania & zarządzanie lukami w zabezpieczeniach zagrożenia

W przypadku działań udoskonalania w kategorii "Urządzenie" nie można wybierać statusów. Zamiast tego otrzymasz skojarzoną z Zarządzanie zagrożeniami i lukami [zabezpieczeń](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) w [Centrum zabezpieczeń usługi Microsoft Defender działania.](/windows/security/threat-protection/microsoft-defender-atp/use) Wybór wyjątku i uzasadnienia będzie specyficzny dla danego portalu. Nie będzie ona obecna w portalu Microsoft Secure Score.

#### <a name="completed-improvement-actions"></a>Ukończone działania udoskonalania

Działania udoskonalania mają stan "ukończony", gdy wszystkie możliwe punkty za działania udoskonalania zostały osiągnięte. Wykonane działania udoskonalania są potwierdzone za pomocą danych firmy Microsoft i nie można zmienić stanu.

### <a name="assess-information-and-review-user-impact"></a>Ocenianie informacji i przeglądanie wpływu na użytkowników

Sekcja O **nazwie Na pierwszy rzut oka** zawiera informacje o kategorii, atakach, przed których może chronić, oraz o produkcie.

**Wpływ na** użytkowników jest odczuwany przez użytkowników, jeśli działania udoskonalania zostaną zrównane, a użytkownicy, których dotyczy problem, będą dotyczyć tych osób.

### <a name="implement-the-improvement-action"></a>Wdrożenie działania udoskonalania

Sekcja **Implementacja** zawiera wszystkie wymagania wstępne, kolejne kroki, krok po kroku, aby ukończyć działanie udoskonalania, bieżący stan implementacji działania udoskonalania, a także linki więcej informacji.

Wymagania wstępne obejmują wszystkie wymagane licencje lub akcje do ukończenia przed podjęciem działania udoskonalania. Upewnij się, że licencja jest wystarczająca do wykonania działań udoskonalania i że te licencje są stosowane do niezbędnych użytkowników.  

## <a name="we-want-to-hear-from-you"></a>Chcemy usłyszeć Od Ciebie

Jeśli masz problemy, po daj nam o tym znać, publikując wpis w społeczności dotyczącej zabezpieczeń [, prywatności & zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Monitorujemy społeczność i udzielamy pomocy.

## <a name="related-resources"></a>Zasoby pokrewne

- [Omówienie bezpiecznego wyniku firmy Microsoft](microsoft-secure-score.md)
- [Śledzenie historii bezpiecznego wyniku firmy Microsoft i spełnienie celów](microsoft-secure-score-history-metrics-trends.md)
- [Co będzie wkrótce](microsoft-secure-score-whats-coming.md)
- [Co nowego](microsoft-secure-score-whats-new.md)