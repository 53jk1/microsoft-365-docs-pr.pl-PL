---
title: Planowanie zarządzania ryzykiem w niejawnym programie testów
description: Dowiedz się, jak zaplanować korzystanie z zasad zarządzania ryzykiem w niejawnym programie testów w organizacji.
keywords: Microsoft 365, ryzyko niejawnego programu testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 824a31780a377fc91d834db6d37068a425428ec8
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010402"
---
# <a name="plan-for-insider-risk-management"></a>Planowanie zarządzania ryzykiem w niejawnym programie testów

Przed rozpoczęciem pracy z [zarządzaniem ryzykiem](insider-risk-management.md) w ramach niejawnego programu testów w organizacji należy uwzględnić ważne działania i zagadnienia związane z planowaniem, które powinny być przeglądane przez Twoje zespoły ds. technologii informatycznych i zarządzania zgodnością. Dokładne zrozumienie i planowanie wdrożenia w następujących obszarach pomoże zapewnić płynne wdrożenie i korzystanie z funkcji zarządzania ryzykiem w niejawnym programie testów oraz ich zgodność z najlepszymi rozwiązaniami.

Obejrzyj poniższy klip wideo, aby dowiedzieć się, jak przepływ pracy zarządzanie ryzykiem w niejawnym programie testów może ułatwić Twojej organizacji zapobieganie, wykrywanie i zawieranie czynników ryzyka podczas ustalania priorytetów wartości, kultury i środowiska użytkownika organizacji:
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Praca z uczestnikami projektu w organizacji

Zidentyfikuj odpowiednie osoby biorące udział w projektu w organizacji w celu współpracy nad podejmowaniem działań dotyczących alertów i spraw dotyczących zarządzania ryzykiem w ramach niejawnego programu testów. Niektórzy polecani uczestnicy projektu, którzy mogą rozważyć ich uwzględnienie w planowaniu wstępnym i w end-to-end insider [risk management workflow](insider-risk-management.md#workflow) , to osoby z następujących obszarów organizacji:

- Technologia informacyjna
- Zgodność
- Prywatność
- Bezpieczeństwo
- Zasoby ludzkie
- Legal

## <a name="determine-any-regional-compliance-requirements"></a>Określanie wszelkich regionalnych wymagań dotyczących zgodności

W różnych obszarach geograficznych i organizacyjnych mogą być spełnione wymagania dotyczące zgodności i prywatności, które różnią się od innych obszarów organizacji. We współpracy z uczestnikami projektu w tych obszarach należy się upewnić, że rozumie on mechanizmy kontroli zgodności i prywatności w zarządzaniu ryzykiem w ramach niejawnego programu testów i ich stosowanie w różnych obszarach organizacji. W niektórych scenariuszach wymagania dotyczące zgodności z przepisami i prywatności mogą wymagać zasad wyznaczania lub ograniczania części uczestników projektu w związku z badaniami i sprawami w zależności od sytuacji, w przypadku których użytkownik lub wymagania prawne dotyczące tego obszaru są wymagane.

Jeśli istnieje wymaganie angażowania określonych uczestników projektu w badaniach przypadku, w których są zaangażowani użytkownicy w określonych regionach, rolach lub wydziałach, można zaimplementować oddzielne (nawet jeśli [identyczne) zasady](insider-risk-management-policies.md) zarządzania ryzykiem w niejawnym programie testów dotyczące poszczególnych regionów i populacji. Taka konfiguracja ułatwi odpowiednim uczestnikom projektu przechowanie spraw istotnych dla ich ról i regionów oraz zarządzanie nimi. Ponadto możesz rozważyć utworzenie procesów i zasad dla regionów, w których uczestnicy i recenzentzy mówią ten sam język co użytkownicy, aby usprawnić proces eskalacji w przypadku alertów i spraw zarządzania ryzykiem w niejawnym programie testów.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planowanie przepływu pracy recenzji i badania

Wybierz dedykowanych uczestników projektu, aby monitorować i przeglądać alerty i sprawy w regularny sposób [w Centrum zgodności platformy Microsoft 365.](https://compliance.microsoft.com) Upewnij się, że przypiszesz różnych uczestników projektu do różnych grup ról dostępnych w zarządzaniu ryzykiem w niejawnym programie testów.

> [!IMPORTANT]
> Po skonfigurowaniu grup ról może upłynąć do 30 minut, aby uprawnienia grupy ról dotyczyły przypisanych użytkowników w organizacji.

Do konfigurowania początkowych uprawnień w celu zarządzania funkcjami zarządzania ryzykiem w niejawnym programie testów jest używanych sześć grup ról. Aby **udostępnić** zarządzanie ryzykiem w niejawnym programie testów jako opcję menu w programie Centrum zgodności platformy Microsoft 365 i kontynuować te kroki konfiguracji, musisz mieć przypisaną jedną z następujących ról lub grup ról:

- Azure Active Directory [*administrator globalny*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*administratora*](/azure/active-directory/roles/permissions-reference#compliance-administrator) zgodności
- Centrum zgodności platformy Microsoft 365 [*ról Zarządzanie*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organizacją
- Centrum zgodności platformy Microsoft 365 [*ról Administrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) zgodności
- *Grupa ról Zarządzanie ryzykiem w niejawnym* programie testów
- *Grupa ról Administrator zarządzania ryzykiem w niejawnym programie* testów

Członkowie następujących ról mają te same uprawnienia rozwiązania, które są zawarte *w grupie ról* Administrator zarządzania ryzykiem w niejawnym programie testów:

- Azure Active Directory *administrator globalny*
- Azure Active Directory *administratora zgodności*
- Centrum zgodności platformy Microsoft 365 *zarządzanie organizacją*
- Centrum zgodności platformy Microsoft 365 *zgodności*

> [!IMPORTANT]
> Upewnij się, że w grupach ról Zarządzanie ryzykiem niejawnego programu testów  lub Administrator zarządzania ryzykiem w niejawnym programie testów (w zależności od wybranej opcji) zawsze jest co najmniej jeden użytkownik, aby konfiguracja zarządzania ryzykiem w niejawnym programie testów nie była dostępna w przypadku opuszczenia organizacji przez określonych użytkowników.

W zależności od tego, jak chcesz zarządzać zasadami i alertami zarządzania ryzykiem w niejawnym programie testów, konieczne będzie przypisanie użytkowników do określonych grup ról w celu zarządzania różnymi zestawami funkcji zarządzania ryzykiem w niejawnym programie testów. Możesz przypisać użytkownikom różne obowiązki dotyczące zgodności z przepisami do określonych grup ról w celu zarządzania różnymi obszarami funkcji zarządzania ryzykiem w niejawnym programie testów. Możesz także przypisać wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, osób oglądających i osoby przeglądowe do grupy ról *Zarządzanie* ryzykiem w niejawnym programie testów. Korzystaj z jednej lub wielu grup ról, aby jak najlepiej dopasować się do wymagań zarządzania zgodnością.

Podczas konfigurowania zarządzania ryzykiem w niejawnym programie testów i zarządzania nimi wybierz jedną z tych opcji grupy ról rozwiązania:

| **Grupa ról** | **Uprawnienia roli** |
| :------------- | :------------------- |
| **Zarządzanie ryzykiem w niejawnym programie testów** | Ta grupa ról pozwala zarządzać zarządzaniem ryzykiem niejawnego programu testów w organizacji w jednej grupie. Dodając wszystkie konta użytkowników przeznaczone dla wyznaczonych administratorów, analityków, audytorów i audytorów, możesz skonfigurować uprawnienia do zarządzania ryzykiem w ramach poziomu niejawnego programu testów w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień do zarządzania ryzykiem w niejawnym programie testów i skojarzone uprawnienia. Jest to najprostszy sposób na szybkie rozpoczynanie pracy z zarządzaniem ryzykiem w niejawnym programie testów i jest dobrym rozwiązaniem dla organizacji, które nie potrzebują osobnych uprawnień zdefiniowanych dla osobnych grup użytkowników. Podczas korzystania z tej konfiguracji należy zawsze mieć przypisanego co najmniej jednego użytkownika do tej grupy ról, aby upewnić się, że zasady działają zgodnie z oczekiwaniami, a użytkownik może tworzyć i edytować zasady **_,_** konfigurować ustawienia rozwiązania i przeglądać ostrzeżenia dotyczące kondycji zasad.|
| **Administrator zarządzania ryzykiem w niejawnym programie testów** | Ta grupa ról umożliwia wstępne skonfigurowanie zarządzania ryzykiem w niejawnym programie testów, a później oddziel administratorów ryzyka niejawnego programu testów do zdefiniowanej grupy. Użytkownicy w tej grupie ról mogą włączać i wyświetlać szczegółowe informacje z analiz, a także tworzyć, odczytywać, aktualizować i usuwać zasady zarządzania ryzykiem niejawnego programu testów, ustawienia globalne i przypisania ról do grup ról. Podczas korzystania z tej konfiguracji należy zawsze mieć przypisanego co najmniej jednego użytkownika do tej grupy ról, aby upewnić się, że zasady działają zgodnie z oczekiwaniami, a użytkownik może tworzyć i edytować zasady **_,_** konfigurować ustawienia rozwiązania i przeglądać ostrzeżenia dotyczące kondycji zasad. |
| **Analitycy zarządzania ryzykiem wewnętrznym** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jako analitycy ds. ryzyka w niejawnym programie testów. Użytkownicy w tej grupie ról mogą wyświetlać i wyświetlać wszystkie szablony alertów zarządzania ryzykiem w ramach niejawnego programu testów, spraw, szczegółowych informacji analitycznych i powiadomień. Nie mogą oni uzyskać dostępu do Eksploratora zawartości z ryzykiem w niejawnym programie testów. |
| **Badacze zarządzania ryzykiem wewnętrznym** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak osoby chłonące dane ryzyka w niejawnym programie testów. Użytkownicy w tej grupie ról mają dostęp do wszystkich alertów zarządzania ryzykiem w niejawnym programie testów, spraw, szablonów powiadomień i Eksploratora zawartości we wszystkich przypadkach. |
| **Audytorzy zarządzania ryzykiem w niejawnym programie testów** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą insektować działania związane z zarządzaniem ryzykiem w niejawnym programie testów. Użytkownicy w tej grupie ról mają dostęp do dziennika inspekcji ryzyka niejawnego programu testów. |

## <a name="understand-requirements-and-dependencies"></a>Opis wymagań i zależności

W zależności od tego, jak planujesz wdrożyć zasady zarządzania ryzykiem w niejawnym programie testów, musisz mieć odpowiednie Microsoft 365 subskrypcji licencjonowania oraz zrozumieć i zaplanować niektóre wymagania wstępne dotyczące rozwiązania.

**Licencjonowanie:** Zarządzanie ryzykiem niejawnego programu testów jest dostępne w ramach szerokiego wyboru Microsoft 365 subskrypcji licencjonowania zbiorowego. Aby uzyskać szczegółowe informacje, zobacz [Artykuł Wprowadzenie do zarządzania ryzykiem w niejawnym programie](insider-risk-management-configure.md#subscriptions-and-licensing) testów.

> [!IMPORTANT]
> Zarządzanie ryzykiem w ramach niejawnego programu testów jest obecnie dostępne w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi Azure. Aby sprawdzić, czy zarządzanie ryzykiem niejawnego programu testów jest obsługiwane w Twojej organizacji, zobacz Dostępność platformy [Azure zależności według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz jeszcze planu Microsoft 365 Enterprise E5 i chcesz wypróbować zarządzanie ryzykiem w ramach niejawnego programu testów, możesz dodać usługę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub utworzyć konto w [](https://www.microsoft.com/microsoft-365/enterprise) celu wypróbowania usługi Microsoft 365 Enterprise E5.

**Wymagania dotyczące szablonu zasad:** W zależności od wybranego szablonu zasad należy zrozumieć i zaplanować wymagania przed skonfigurowaniem zarządzania ryzykiem w niejawnym programie testów w organizacji:

- W **przypadku korzystania z** szablonu Kradzież danych przez odchodzącego użytkownika należy skonfigurować łącznik kadr usługi Microsoft 365, aby okresowo importować informacje o datach ponownego przypisania i zakończenia dla użytkowników w organizacji. Zobacz artykuł [Importowanie danych za pomocą łącznika](import-hr-data.md) kadr, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji.
- Podczas korzystania **z szablonów wycieków** danych musisz skonfigurować co najmniej jedną politykę ochrony przed utratą danych (DLP, Data Loss Prevention), aby definiować poufne informacje w organizacji i otrzymywać alerty o wysokim poziomie ryzyka w związku z alertami o zasadach DLP o wysokim poziomie ważności. Zobacz artykuł [Tworzenie, testowanie](create-test-tune-dlp-policy.md) i dostosowywanie zasad DLP, aby uzyskać szczegółowe instrukcje dotyczące konfigurowania zasad DLP dla organizacji.
- Podczas korzystania **z szablonów naruszenia zasad** zabezpieczeń należy włączyć usługę Microsoft Defender for Endpoint w celu integracji zarządzania ryzykiem w niejawnym programie testów w Centrum zabezpieczeń Defender, aby importować alerty o naruszeniach zabezpieczeń. Aby uzyskać szczegółowe instrukcje dotyczące włączania integracji usługi Defender for Endpoint z zarządzaniem ryzykiem w niejawnym programie testów, zobacz Konfigurowanie zaawansowanych funkcji w [programie Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- W przypadku **korzystania z szablonów** użytkowników niezasydane należy skonfigurować łącznik kadr usługi Microsoft 365, aby okresowo importował informacje o wydajności lub statusie ruchu dla użytkowników w organizacji. Zobacz artykuł [Importowanie danych za pomocą łącznika](import-hr-data.md) kadr, aby uzyskać szczegółowe wskazówki dotyczące konfigurowania łącznika Microsoft 365 kadr dla organizacji.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Testowanie z małą grupą użytkowników w środowisku produkcyjnym

Przed włączeniem rozwiązania w szerszym zakresie w środowisku produkcyjnym możesz rozważyć przetestowanie zasad u niewielkiego zestawu użytkowników produkcyjnych podczas przeprowadzania niezbędnych działań w zakresie zgodności z przepisami, prywatności i przeglądów prawnych w organizacji. Ocena zarządzania ryzykiem niejawnego programu testowego w środowisku testowym wymagałaby wygenerowania symulowanych akcji użytkownika i innych sygnałów w celu utworzenia alertów w przypadku triage i przypadków przetwarzania. Ta metoda jest niepraktyczna w przypadku większości organizacji, więc zalecane jest testowanie zarządzania ryzykiem w niejawnym programie testów z małą grupą użytkowników w środowisku produkcyjnym.

Zachowaj funkcję anonimizacji w ustawieniach zasad włączoną anonimizowanie nazw wyświetlanych użytkowników w konsoli zarządzania ryzykiem niejawnego programu testów podczas tych testów, aby zachować prywatność w obrębie narzędzia. To ustawienie pomaga chronić prywatność użytkowników, którzy mają dopasowania do zasad, i może ułatwić promowanie obiektowości w analizie danych i przeglądach analiz alertów o ryzyku w niejawnym programie testów.

Jeśli nie widzisz żadnych alertów natychmiast po skonfigurowaniu zasad zarządzania ryzykiem w niejawnym programie testów, może to oznaczać, że nie został jeszcze spełniony minimalny próg ryzyka. Dobrym sposobem sprawdzenia, czy zasady są wyzwalane i działają zgodnie z oczekiwaniami, jest sprawdzenie, czy użytkownik znajduje się w zasięgu zasad na **stronie Użytkownicy** .

## <a name="resources-for-stakeholders"></a>Zasoby dla uczestników projektu

Udostępnij dokumentację zarządzania ryzykiem w niejawnym programie testów uczestnikom projektu w organizacji, którzy są dostępni w przepływie pracy zarządzania i rozwiązywania problemów:

- [Tworzenie zasad ryzyka w niejawnym programie testów i zarządzanie nimi](insider-risk-management-policies.md)
- [Badanie działań ryzyka niejawnego programu testów](insider-risk-management-activities.md)
- [Działania w przypadku niejawnego programu testów](insider-risk-management-cases.md)
- [Przeglądanie danych dotyczących sprawy za pomocą Eksploratora zawartości związanego z ryzykiem w niejawnym programie testów](insider-risk-management-content-explorer.md)
- [Tworzenie szablonów informacji o ryzyku niejawnego programu testów](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Wszystko gotowe do rozpoczęcia?

Wszystko gotowe do skonfigurowania zarządzania ryzykiem w niejawnym programie testów dla organizacji? Przejrzyj następujące artykuły:

- [Wprowadzenie do ustawień zarządzania ryzykiem w niejawnym programie testów w celu](insider-risk-management-settings.md) skonfigurowania ustawień zasad globalnych.
- [Wprowadzenie do zarządzania ryzykiem w niejawnym programie testów](insider-risk-management-configure.md) w celu skonfigurowania wymagań wstępnych, utworzenia zasad i otrzymywania alertów.