---
title: Uprawnienia — Centrum & zgodności
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.AdminRoleGroups
ms.localizationpriority: medium
ms.collection: Strat_O365_IP
search.appverid:
- MOE150
- MET150
description: Administratorzy mogą dowiedzieć się więcej o uprawnieniach dostępnych w Centrum zabezpieczeń & zgodności w programie Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8670f28ab8a7d0af2c51628c3d8df764977a43cb
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2022
ms.locfileid: "63009671"
---
# <a name="permissions-in-the-security--compliance-center"></a>Uprawnienia w Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Centrum zabezpieczeń & zgodności umożliwia udzielanie uprawnień osobom, które wykonują zadania związane ze zgodnością, takie jak zarządzanie urządzeniami, ochrona przed utratą danych, zbierania elektronicznych materiałów dowodowych, przechowywanie itp. Te osoby mogą wykonywać tylko zadania, do których jawnie przyznajesz im dostęp. Aby uzyskać dostęp do Centrum & zgodności zabezpieczeń, użytkownicy muszą być administratorami globalnymi lub członkami jednej lub kilku grup ról Centrum zabezpieczeń & zgodności.

Uprawnienia w Centrum & zabezpieczeń są oparte na modelu uprawnień RBAC (Role-based Access Control). RBAC to ten sam model uprawnień, który jest używany przez program Exchange, więc jeśli znasz program Exchange, udzielanie uprawnień w Centrum zgodności usługi & zabezpieczeń będzie bardzo podobne. Należy jednak pamiętać, że grupy ról Exchange i grupy ról Centrum & zgodności nie mają jednak współużytego członkostwa ani uprawnień. Obie grupy ról Zarządzanie organizacją nie są jednakowe. Uprawnienia, które przyznają, i członkowie grup ról, są różne. Poniżej znajduje się lista grup ról centrum & zabezpieczeń i zgodności.

![Stronie Uprawnienia w Centrum & zgodności.](../../media/992c20ca-e82e-497c-9c8d-6fab212deb80.png)

## <a name="relationship-of-members-roles-and-role-groups"></a>Relacja między członkami, rolami i grupami ról

Rola **udziela** uprawnień do wykonywania zestawu zadań. Na przykład rola Zarządzanie sprawami umożliwia użytkownikom pracę ze sprawami zbierania elektronicznych materiałów dowodowych.

Grupa **ról to** zestaw ról, które umożliwiają osobom pełniące funkcje w Centrum zabezpieczeń & zgodności. Na przykład grupa ról Administrator zgodności obejmuje (między innymi) role w zarządzaniu sprawą, przeszukiwaniu zawartości i konfiguracji organizacji (oraz innych), ponieważ osoba, która jest administratorem zgodności, będzie potrzebować uprawnień do wykonywania swoich zadań.

Centrum zabezpieczeń & zgodności zawiera domyślne grupy ról dla najczęściej wykonywanych zadań i funkcji, do których musisz przypisać osoby. Zalecamy po prostu dodawanie pojedynczych użytkowników jako **członków** do domyślnych grup ról.

![Diagram przedstawiający relację grup ról z rolami i członkami.](../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="role-groups-in-the-security--compliance-center"></a>Grupy ról w Centrum & zgodności

W poniższej tabeli wymieniono domyślne grupy ról dostępne w Centrum zgodności & zabezpieczeń oraz role, które są domyślnie przypisane do tych grup ról. Aby przyznać użytkownikowi uprawnienia do wykonywania zadania zgodności, dodaj go do odpowiedniej grupy ról Centrum & zabezpieczeń.

Zarządzanie uprawnieniami w Centrum & zgodności zabezpieczeń zapewnia użytkownikom dostęp tylko do funkcji zgodności dostępnych w samym Centrum zabezpieczeń & zgodności. Jeśli chcesz przyznać uprawnienia do innych funkcji zgodności, które nie znajdują się w Centrum zgodności usługi & Security &, takich jak reguły przepływu poczty e-mail programu Exchange (nazywane także regułami transportu), musisz użyć centrum administracyjnego usługi Exchange(EAC). Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

Aby dowiedzieć się, jak udzielić dostępu do Centrum & zgodności zabezpieczeń, zobacz Udzielanie użytkownikom dostępu do centrum [administracyjnego Microsoft 365 zgodności](grant-access-to-the-security-and-compliance-center.md).

> [!NOTE]
> Aby wyświetlić **kartę Uprawnienia** w Centrum zabezpieczeń & zgodności, musisz być administratorem. W szczególności musisz mieć przypisaną rolę zarządzanie rolami, która domyślnie jest przypisana tylko do grupy ról Zarządzanie organizacją  w Centrum zabezpieczeń & zgodności. Ponadto rola Zarządzanie **rolami** umożliwia użytkownikom wyświetlanie, tworzenie i modyfikowanie grup ról.

<br>

****

|Grupa ról|Opis|Przypisane role domyślne|
|---|---|---|
|**Administratorzy symestracyjnych ataków**|Nie używaj tej grupy ról w Centrum & zgodności. Użyj odpowiedniej roli w usłudze Azure AD.|Administrator ataków|
|**Autorzy ataków na payload**|Nie używaj tej grupy ról w Centrum & zgodności. Użyj odpowiedniej roli w usłudze Azure AD.|Autor opłaty za ataki|
|**Zgodność komunikacji**|Zapewnia uprawnienia do wszystkich ról zgodności komunikacji: administratora, analityka, administratora, administratora i przeglądarki.|Zarządzanie sprawą <p> Administrator zgodności komunikacji <p> Analiza zgodności komunikacji <p> Zarządzanie zgodnością komunikacji <p> Badanie zgodności komunikacji <p> Przeglądarka zgodności komunikacji <p> Dostawca opinii o klasyfikacji danych <p> View-Only sprawy|
|**Administratorzy zgodności komunikacji**|Administratorzy zgodności komunikacji, którzy mogą tworzyć/edytować zasady i definiować ustawienia globalne.|Administrator zgodności komunikacji <p> Zarządzanie zgodnością komunikacji|
|**Analitycy zgodności komunikacji**|Analitycy zgodności komunikacji mogą badać dopasowania zasad, wyświetlać dane meta wiadomości i podjąć działania naprawcze.|Analiza zgodności komunikacji <p> Zarządzanie zgodnością komunikacji|
|**Schoweki zgodności komunikacji**|Analitycy zgodności komunikacji mogą badać dopasowania zasad, wyświetlać zawartość wiadomości i podjąć działania naprawcze.|Zarządzanie sprawą <p> Analiza zgodności komunikacji <p> Zarządzanie zgodnością komunikacji <p> Badanie zgodności komunikacji <p> Dostawca opinii o klasyfikacji danych <p> View-Only sprawy|
|**Przeglądarki zgodności komunikacji**|Przeglądarka zgodności komunikacji, która ma dostęp do dostępnych raportów i widżetów.|Zarządzanie zgodnością komunikacji <p> Przeglądarka zgodności komunikacji|
|**Administrator zgodności1**<sup></sup>|Członkowie mogą zarządzać ustawieniami zarządzania urządzeniami, ochrony przed utratą danych, raportów i zachowywania.|Zarządzanie sprawą <p> Administrator zgodności komunikacji <p> Zarządzanie zgodnością komunikacji <p> Administrator zgodności <p> Wyszukiwanie zgodności <p> Dostawca opinii o klasyfikacji danych <p> Recenzent opinii o klasyfikacji danych <p> Zarządzanie badaniem danych <p> Zarządzanie urządzeniami <p> Zarządzanie rozsyłaniem <p> Zarządzanie zgodnością DLP <p> Wstrzymaj <p> Zarządzanie zgodnością IB <p> Administrator ochrony informacji <p> Analityk ochrony informacji <p> Ochrona informacji <p> Czytnik ochrony informacji <p> Administrator zarządzania ryzykiem w niejawnym programie testów <p> Zarządzanie alertami <p> Konfiguracja organizacji <p> RecordManagement <p> Zarządzanie przechowywaniem <p> View-Only inspekcji <p> View-Only sprawy <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami <p> View-Only adresaci <p> View-Only zarządzanie rekordami <p> View-Only zarządzanie przechowywaniem|
|**Administrator danych dotyczących zgodności**|Członkowie mogą zarządzać ustawieniami zarządzania urządzeniami, ochrony danych, ochrony danych, ochrony przed utratą danych, raportów i zachowywania.|Administrator zgodności <p> Wyszukiwanie zgodności <p> Zarządzanie urządzeniami <p> Zarządzanie rozsyłaniem <p> Zarządzanie zgodnością DLP <p> Zarządzanie zgodnością IB <p> Administrator ochrony informacji <p> Analityk ochrony informacji <p> Ochrona informacji <p> Czytnik ochrony informacji <p> Zarządzanie alertami <p> Konfiguracja organizacji <p> RecordManagement <p> Zarządzanie przechowywaniem <p> Administrator etykiet wrażliwości <p> View-Only inspekcji <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami <p> View-Only adresaci <p> View-Only zarządzanie rekordami <p> View-Only zarządzanie przechowywaniem|
|**Administratorzy Menedżera zgodności**|Zarządzanie tworzeniem i modyfikowaniem szablonów.|Administracja Menedżera zgodności <p> Ocena menedżera zgodności <p> Udział menedżera zgodności <p> Czytnik Menedżera zgodności|
|**Ocenianie menedżera zgodności**|Tworzenie testów, wdrażanie działań udoskonalania i aktualizowanie stanu testów w przypadku działań udoskonalania.|Ocena menedżera zgodności <p> Udział menedżera zgodności <p> Czytnik Menedżera zgodności|
|**Współautorzy Menedżera zgodności**|Twórz oceny i wykonuj prace, aby wdrożyć działania ulepszeń.|Udział menedżera zgodności <p> Czytnik Menedżera zgodności|
|**Czytelnicy Menedżera zgodności**|Wyświetlanie całej zawartości Menedżera zgodności z wyjątkiem funkcji administratora.|Czytnik Menedżera zgodności|
|**Przeglądarka zawartości Eksploratora zawartości**|Wyświetl pliki zawartości w Eksploratorze zawartości.|Podgląd zawartości klasyfikacji danych|
|**Przeglądarka list Eksploratora zawartości**|Wyświetlanie wszystkich elementów w Eksploratorze zawartości tylko w formacie listy.|Przeglądarka listy klasyfikacji danych|
|**Data  Wiad.**|Przekonuj wyszukiwania w skrzynkach pocztowych, SharePoint witrynach online i OneDrive dla Firm lokalizacjach.|Komunikacja <p> Wyszukiwanie zgodności <p> Szybki <p> Zarządzanie badaniem danych <p> Eksportowanie <p> Wersja zapoznawcza <p> Recenzja <p> Odszyfrowywanie usługi RMS <p> Wyszukiwanie i przeczyszczanie|
|**Menedżer zbierania elektronicznych materiałów dowodowych**|Członkowie mogą przeprowadzać wyszukiwania i umieszczać blokady w skrzynkach pocztowych, witrynach SharePoint Online i OneDrive dla Firm lokalizacjach. Członkowie mogą również tworzyć sprawy zbierania elektronicznych materiałów dowodowych i zarządzać nimi, dodawać i usuwać członków do sprawy, tworzyć i edytować wyszukiwania zawartości skojarzone ze sprawą oraz uzyskać dostęp do danych sprawy w Advanced eDiscovery. <p> Administrator zbierania elektronicznych materiałów dowodowych jest członkiem grupy ról Menedżer zbierania elektronicznych materiałów dowodowych, do których przypisano dodatkowe uprawnienia. Oprócz zadań, które może wykonywać menedżer zbierania elektronicznych materiałów dowodowych, administrator zbierania elektronicznych materiałów dowodowych może:<ul><li>Wyświetlanie wszystkich spraw zbierania elektronicznych materiałów dowodowych w organizacji.</li><li>Zarządzanie każdą sprawą zbierania elektronicznych materiałów dowodowych po dodaniu siebie jako członka do sprawy.</li></ul> <p> Podstawowa różnica między Menedżerem zbierania elektronicznych materiałów dowodowych a administratorem zbierania elektronicznych materiałów dowodowych polega na tym, że administrator zbierania elektronicznych materiałów dowodowych może  uzyskać dostęp do wszystkich spraw wymienionych na stronie Sprawy zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń & zgodności. Menedżer zbierania elektronicznych materiałów dowodowych może uzyskać dostęp tylko do spraw, które utworzył, lub spraw, do których należy. Aby uzyskać więcej informacji na temat nabierania użytkownikom uprawnień administratora zbierania elektronicznych materiałów dowodowych, zobacz Przypisywanie uprawnień zbierania elektronicznych materiałów dowodowych w Centrum zabezpieczeń [& zgodności](../../compliance/assign-ediscovery-permissions.md).|Zarządzanie sprawą <p> Komunikacja <p> Wyszukiwanie zgodności <p> Szybki <p> Eksportowanie <p> Wstrzymaj <p> Wersja zapoznawcza <p> Recenzja <p> Odszyfrowywanie usługi RMS|
|**Czytnik globalny**|Członkowie mają dostęp tylko do odczytu do raportów, alertów i mogą widzieć wszystkie konfiguracje i ustawienia.<p> Podstawowa różnica między czytnikiem globalnym a czytnikiem zabezpieczeń polega na tym, że czytnik globalny może uzyskać dostęp do **konfiguracji i ustawień**.|Czytnik zabezpieczeń <p> Czytnik etykiet wrażliwości <p> Widok zapewniania ochrony usługi <p> View-Only inspekcji <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami <p> View-Only adresaci <p> View-Only zarządzanie rekordami <p> View-Only zarządzanie przechowywaniem|
|**Ochrona informacji**|Pełna kontrola nad wszystkimi funkcjami ochrony informacji, w tym etykietami wrażliwości i ich zasadami, zasadą DLP, wszystkimi typami klasyfikatorów, aktywnością i eksploratorami zawartości oraz wszystkimi powiązanymi raportami.|Podgląd zawartości klasyfikacji danych <p> Administrator ochrony informacji <p> Analityk ochrony informacji <p> Ochrona informacji <p> Czytnik ochrony informacji|
|**Administratorzy ochrony informacji**|Tworzenie, edytowanie i usuwanie zasad DLP, etykiet wrażliwości, ich zasad oraz wszystkich typów klasyfikatorów. Zarządzanie ustawieniami DLP punktu końcowego i trybem symulowania na przykład w przypadku zasad automatycznego oznaczania.|Administrator ochrony informacji|
|**Analitycy ochrony informacji**|Uzyskiwanie dostępu do alertów DLP i Eksploratora aktywności oraz zarządzanie nimi. Dostęp tylko do zasad DLP, etykiet wrażliwości i ich zasad oraz do wszystkich typów klasyfikatorów.|Przeglądarka listy klasyfikacji danych <p> Analityk ochrony informacji|
|**Schoweki ochrony informacji**|Dostęp do alertów DLP, Eksploratora aktywności i Eksploratora zawartości oraz zarządzanie nimi. Dostęp tylko do zasad DLP, etykiet wrażliwości i ich zasad oraz do wszystkich typów klasyfikatorów.|Podgląd zawartości klasyfikacji danych <p> Analityk ochrony informacji <p> Ochrona informacji|
|**Czytniki informacji**|Dostęp tylko do raportów dotyczących zasad DLP i etykiet wrażliwości oraz ich zasad.|Czytnik ochrony informacji|
|**Zarządzanie ryzykiem w niejawnym programie testów**|Ta grupa ról pozwala zarządzać zarządzaniem ryzykiem niejawnego programu testów w organizacji w jednej grupie. Dodając wszystkie konta użytkowników przeznaczone dla wyznaczonych administratorów, analityków i osób chłonnych, możesz skonfigurować uprawnienia do zarządzania ryzykiem w ramach poziomu niejawnego programu testów w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień do zarządzania ryzykiem w niejawnym programie testów. Jest to najprostszy sposób na szybkie rozpoczynanie pracy z zarządzaniem ryzykiem w niejawnym programie testów i jest dobrym rozwiązaniem dla organizacji, które nie potrzebują osobnych uprawnień zdefiniowanych dla osobnych grup użytkowników.|Zarządzanie sprawą <p> Administrator zarządzania ryzykiem w niejawnym programie testów <p> Analiza ryzyka w niejawnym programie testów <p> Inspekcja zarządzania ryzykiem w ramach niejawnego programu testów <p> Badanie ryzyka niejawnego programu testów <p> Sesje zarządzania ryzykiem w niejawnym programie testów <p> View-Only sprawy|
|**Administratorzy zarządzania ryzykiem w niejawnym programie testów**|Ta grupa ról umożliwia wstępne skonfigurowanie zarządzania ryzykiem niejawnego programu testów, a później podział administratorów ryzyka niejawnego programu testów na zdefiniowaną grupę. Użytkownicy w tej grupie ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zarządzania ryzykiem niejawnego programu testów, ustawienia globalne i przypisania grup ról.|Zarządzanie sprawą <p> Administrator zarządzania ryzykiem w niejawnym programie testów <p> View-Only sprawy|
|**Analitycy zarządzania ryzykiem wewnętrznym**|Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jako analitycy ds. ryzyka w niejawnym programie testów. Użytkownicy w tej grupie ról mają dostęp do wszystkich szablonów alertów, spraw i powiadomień dotyczących zarządzania ryzykiem w niejawnym programie testów. Nie mogą oni uzyskać dostępu do Eksploratora zawartości z ryzykiem w niejawnym programie testów.|Zarządzanie sprawą <p> Analiza ryzyka w niejawnym programie testów <p> View-Only sprawy|
|**Audytorzy zarządzania ryzykiem w niejawnym programie testów**|Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą insektować działania związane z zarządzaniem ryzykiem w niejawnym programie testów. Użytkownicy w tej grupie ról mają dostęp do dziennika inspekcji ryzyka niejawnego programu testów.|Inspekcja zarządzania ryzykiem w ramach niejawnego programu testów|
|**Badacze zarządzania ryzykiem wewnętrznym**|Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak osoby chłonące dane ryzyka w niejawnym programie testów. Użytkownicy w tej grupie ról mają dostęp do wszystkich alertów zarządzania ryzykiem w niejawnym programie testów, spraw, szablonów powiadomień i Eksploratora zawartości we wszystkich przypadkach.|Zarządzanie sprawą <p> Badanie ryzyka niejawnego programu testów <p> View-Only sprawy|
|**Osoby zatwierdzające sesję zarządzania ryzykiem w niejawnym programie testów**|Zarządzanie żądaniami modyfikacji grupy dla nagrywania sesji.|Sesje zarządzania ryzykiem w niejawnym programie testów|
|**Współautorzy usługi IRM**|Ta grupa ról jest widoczna, ale jest używana tylko przez usługi w tle.|Trwały udział w zarządzaniu ryzykiem w niejawnym programie testów <p> Udział tymczasowy w zarządzaniu ryzykiem w niejawnym programie testów|
|**Administratorzy wiedzy**|Konfiguruj wiedzę, uczenie się, przypisuj szkolenia i inne inteligentne funkcje.|Administrator wiedzy|
|**Administrator przepływu poczty e-mail**|Członkowie mogą monitorować i wyświetlać szczegółowe informacje dotyczące przepływu poczty e-mail oraz raporty w Centrum & zabezpieczeń i zgodności. Administratorzy globalni mogą dodawać zwykłych użytkowników do tej grupy, ale jeśli użytkownik nie jest członkiem grupy administratorów usługi Exchange, nie będzie miał dostępu do zadań związanych z Exchange administratorem.|View-Only adresaci|
|**Zarządzanie organizacją1**<sup></sup>|Członkowie mogą kontrolować uprawnienia dostępu do funkcji w Centrum & zabezpieczeń i zgodności, a także zarządzać ustawieniami zarządzania urządzeniami, ochrony przed utratą danych, raportów i zachowywania. <p> Użytkownicy, którzy nie są administratorami globalnymi, muszą być administratorami usługi Exchange, aby widzieć urządzenia zarządzane przez pakiet Basic Mobility and Security dla usługi Microsoft 365 (wcześniej znany jako Zarządzanie urządzeniami przenośnymi lub MDM). <p> Administratorzy globalni są automatycznie dodawana jako członkowie tej grupy ról.|Dzienniki inspekcji <p> Zarządzanie sprawą <p> Administrator zgodności komunikacji <p> Zarządzanie zgodnością komunikacji <p> Administrator zgodności <p> Wyszukiwanie zgodności <p> Zarządzanie urządzeniami <p> Zarządzanie zgodnością DLP <p> Wstrzymaj <p> Zarządzanie zgodnością IB <p> Administrator zarządzania ryzykiem w niejawnym programie testów <p> Zarządzanie alertami <p> Konfiguracja organizacji <p> Kwarantanna <p> RecordManagement <p> Zarządzanie przechowywaniem <p> Zarządzanie rolami <p> Wyszukiwanie i przeczyszczanie <p> Administrator zabezpieczeń <p> Czytnik zabezpieczeń <p> Administrator etykiet wrażliwości <p> Czytnik etykiet wrażliwości <p> Widok zapewniania ochrony usługi <p> Współautor tagów <p> Menedżer znaczników <p> Czytnik tagów <p> View-Only inspekcji <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only sprawy <p> View-Only zarządzanie alertami <p> View-Only adresaci <p> View-Only zarządzanie rekordami <p> View-Only zarządzanie przechowywaniem|
|**Zarządzanie prywatnością**|Zarządzaj kontrolą dostępu dla priva w Centrum zgodności platformy Microsoft 365.|Zarządzanie sprawą <p> Podgląd zawartości klasyfikacji danych <p> Przeglądarka listy klasyfikacji danych <p> Administrator zarządzania prywatnością <p> Analiza zarządzania prywatnością <p> Badanie zarządzania prywatnością <p> Trwały udział w zarządzaniu prywatnością <p> Zarządzanie prywatnością Udział tymczasowy <p> Przeglądarka zarządzania prywatnością <p> Administrator żądania praw podstawowych <p> View-Only sprawy|
|**Administratorzy zarządzania prywatnością**|Administratorzy rozwiązań do zarządzania prywatnością, którzy mogą tworzyć/edytować zasady i definiować ustawienia globalne.|Zarządzanie sprawą <p> Administrator zarządzania prywatnością <p> View-Only sprawy|
|**Analitycy zarządzania prywatnością**|Analitycy rozwiązania do zarządzania prywatnością mogą sprawdzać dopasowania zasad, wyświetlać dane meta wiadomości i podjąć działania naprawcze.|Zarządzanie sprawą <p> Przeglądarka listy klasyfikacji danych <p> Analiza zarządzania prywatnością <p> View-Only sprawy|
|**Współautorzy zarządzania prywatnością**|Zarządzanie dostępem współautorów w przypadku spraw zarządzania prywatnością.|Trwały udział w zarządzaniu prywatnością <p> Zarządzanie prywatnością Udział tymczasowy|
|**Grupy zarządzania prywatnością**|Nasyć można rozwiązania do zarządzania prywatnością, które mogą badać dopasowania zasad, wyświetlać zawartość wiadomości i podjąć działania naprawcze.|Zarządzanie sprawą <p> Podgląd zawartości klasyfikacji danych <p> Przeglądarka listy klasyfikacji danych <p> Badanie zarządzania prywatnością <p> View-Only sprawy|
|**Przeglądarki zarządzania prywatnością**|Przeglądarka rozwiązania do zarządzania prywatnością, które może uzyskać dostęp do dostępnych pulpitów nawigacyjnych i widżetów.|Przeglądarka listy klasyfikacji danych <p> Przeglądarka zarządzania prywatnością|
|**Administrator kwarantanny**|Członkowie mają dostęp do wszystkich akcji kwarantanny. Aby uzyskać więcej informacji, zobacz [Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w u administratorach usługi EOP.](manage-quarantined-messages-and-files.md)|Kwarantanna|
|**Zarządzanie rekordami**|Członkowie mogą konfigurować wszystkie aspekty zarządzania rekordami, w tym etykiety przechowywania i recenzje rozsyłania.|Zarządzanie rozsyłaniem <p> RecordManagement <p> Zarządzanie przechowywaniem|
|**Recenzent**|Członkowie mają dostęp do zestawów re recenzji [w Advanced eDiscovery](../../compliance/overview-ediscovery-20.md) spraw. Członkowie tej grupy ról mogą widzieć i otwierać listę spraw na stronie Zbierania elektronicznych materiałów dowodowych **> zaawansowanej** w Centrum zgodności platformy Microsoft 365 których są członkami. Gdy użytkownik uzyskuje dostęp do sprawy Advanced eDiscovery, może wybrać pozycję **Przejrzyj zestawy**, aby uzyskać dostęp do danych dotyczących sprawy. Ta rola nie umożliwia użytkownikowi wyświetlania podglądu wyników przeszukiwania kolekcji skojarzonego ze sprawą ani wykonywania innych zadań związanych z wyszukiwaniem lub zarządzaniem sprawą. Członkowie tej grupy ról mają dostęp tylko do danych w zestawie recenzji.|Recenzja|
|**Administrator zabezpieczeń**|Członkowie mają dostęp do wielu funkcji zabezpieczeń Centrum ochrony tożsamości, usługi Privileged Identity Management, monitorowania Microsoft 365 kondycji usługi oraz centrum zabezpieczeń & zgodności. <p> Domyślnie ta grupa ról może nie mieć żadnych członków. Do tej grupy ról jest jednak Azure Active Directory administrator zabezpieczeń z grupy zabezpieczeń. W związku z tym ta grupa ról dziedziczy możliwości i członkostwo w roli Administratora zabezpieczeń po Azure Active Directory. <p> Aby zarządzać uprawnieniami centralnie, dodaj i usuń członków grupy w centrum Azure Active Directory administracyjnego. Aby uzyskać więcej informacji, zobacz [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference). W przypadku edytowania tej grupy ról w Centrum & zabezpieczeń (członkostwa lub ról) te zmiany mają zastosowanie tylko w Centrum zabezpieczeń & zgodności, a nie w żadnych innych usługach. <p> Ta grupa ról zawiera wszystkie uprawnienia tylko do odczytu roli czytnika zabezpieczeń oraz wiele dodatkowych uprawnień administracyjnych dla tych samych usług: Azure Information Protection, Identity Protection Center, Privileged Identity Management, Monitorowanie kondycji usługi Microsoft 365 i Centrum zgodności & zabezpieczeń.|Dzienniki inspekcji <p> Zarządzanie urządzeniami <p> Zarządzanie zgodnością DLP <p> Zarządzanie zgodnością IB <p> Zarządzanie alertami <p> Kwarantanna <p> Administrator zabezpieczeń <p> Administrator etykiet wrażliwości <p> Współautor tagów <p> Menedżer znaczników <p> Czytnik tagów <p> View-Only inspekcji <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami|
|**Operator zabezpieczeń**|Członkowie mogą zarządzać alertami zabezpieczeń, a także wyświetlać raporty i ustawienia funkcji zabezpieczeń.|Wyszukiwanie zgodności <p> Zarządzanie alertami <p> Czytnik zabezpieczeń <p> Współautor tagów <p> Czytnik tagów <p> Menedżer allowblocklist dzierżawy <p> View-Only inspekcji <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami|
|**Czytnik zabezpieczeń**|Członkowie mają dostęp tylko do odczytu do wielu funkcji zabezpieczeń Centrum ochrony tożsamości, usługi Privileged Identity Management, Monitorowanie Microsoft 365 kondycji usługi i Centrum & zabezpieczeń. <p> Domyślnie ta grupa ról może nie mieć żadnych członków. Jednak do tej grupy ról jest przypisana Azure Active Directory czytnika zabezpieczeń z grupy. W związku z tym ta grupa ról dziedziczy funkcje i członkostwo w roli Czytnika zabezpieczeń po Azure Active Directory. <p> Aby zarządzać uprawnieniami centralnie, dodaj i usuń członków grupy w centrum Azure Active Directory administracyjnego. Aby uzyskać więcej informacji, zobacz [Wbudowane role w usłudze Azure AD](/azure/active-directory/roles/permissions-reference). W przypadku edytowania tej grupy ról w Centrum & zabezpieczeń (członkostwa lub ról) te zmiany mają zastosowanie tylko w Centrum zabezpieczeń & zgodności, a nie w żadnych innych usługach.|Czytnik zabezpieczeń <p> Czytnik etykiet wrażliwości <p> Czytnik tagów <p> View-Only zarządzanie urządzeniami <p> View-Only zarządzania zgodnością DLP <p> View-Only zarządzania zgodnością IB <p> View-Only zarządzanie alertami|
|**Użytkownik zapewniania ochrony usługi**|Członkowie mogą uzyskać dostęp do sekcji Zapewnianie ochrony usługi w Centrum & zabezpieczeń. Zapewnianie ochrony usługi zawiera raporty i dokumenty opisujące zasady firmy Microsoft dotyczące zabezpieczeń danych klientów przechowywanych w Microsoft 365. Ponadto udostępnia niezależne raporty z inspekcji raportów z inspekcji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Zapewnianie ochrony usługi w Centrum & zabezpieczeń](../../compliance/service-assurance.md).|Widok zapewniania ochrony usługi|
|**Administratorzy żądania praw podstawowych**|Tworzenie podstawowych żądań praw.|Zarządzanie sprawą <p> Administrator żądania praw podstawowych <p> View-Only sprawy|
|**Przegląd nadzorczy**|Członkowie mogą tworzyć zasady definiujące, które wiadomości mają być przeglądane w organizacji i zarządzać nimi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad zgodności komunikacji dla organizacji](../../compliance/communication-compliance-configure.md).|Administrator przeglądu nadzorczych|
|

> [!NOTE]
> <sup>1</sup> Ta grupa ról nie przypisuje członkom uprawnień niezbędnych do przeszukiwania dziennika inspekcji ani do korzystania z raportów, które mogą zawierać dane programu Exchange, takich jak zasady DLP lub program Defender dla raportów programu Office 365. Aby przeszukiwać dziennik inspekcji lub wyświetlać wszystkie raporty, użytkownik musi mieć przypisane uprawnienia w programie Exchange Online. Jest to spowodowane tym, że polecenie cmdlet służące do przeszukiwania dziennika inspekcji jest poleceniem cmdlet Exchange Online cmdlet. Administratorzy globalni mogą przeszukiwać dziennik inspekcji i wyświetlać wszystkie raporty, ponieważ są one automatycznie dodawane jako członkowie grupy ról Zarządzanie organizacją w u Exchange Online. Aby uzyskać więcej informacji, zobacz [Przeszukiwanie dziennika inspekcji w Centrum & zabezpieczeń](../../compliance/search-the-audit-log-in-security-and-compliance.md).

## <a name="roles-in-the-security--compliance-center"></a>Role w Centrum zgodności & zabezpieczeń

W poniższej tabeli wymieniono dostępne role i grupy ról, do których są domyślnie przypisane.

Zauważ, że do grupy ról Zarządzanie organizacją domyślnie nie są przypisane następujące role:

- Administrator ataków
- Autor opłaty za ataki
- Komunikacja
- Analiza zgodności komunikacji
- Badanie zgodności komunikacji
- Przeglądarka zgodności komunikacji
- Administracja Menedżera zgodności
- Ocena menedżera zgodności
- Udział menedżera zgodności
- Czytnik Menedżera zgodności
- Szybki
- Podgląd zawartości klasyfikacji danych
- Dostawca opinii o klasyfikacji danych
- Recenzent opinii o klasyfikacji danych
- Przeglądarka listy klasyfikacji danych
- Zarządzanie badaniem danych
- Zarządzanie rozsyłaniem
- Eksportowanie
- Administrator ochrony informacji
- Analityk ochrony informacji
- Ochrona informacji
- Czytnik ochrony informacji
- Analiza ryzyka w niejawnym programie testów
- Inspekcja zarządzania ryzykiem w ramach niejawnego programu testów
- Badanie ryzyka niejawnego programu testów
- Trwały udział w zarządzaniu ryzykiem w niejawnym programie testów
- Sesje zarządzania ryzykiem w niejawnym programie testów
- Udział tymczasowy w zarządzaniu ryzykiem w niejawnym programie testów
- Administrator wiedzy
- Wersja zapoznawcza
- Administrator zarządzania prywatnością
- Analiza zarządzania prywatnością
- Badanie zarządzania prywatnością
- Trwały udział w zarządzaniu prywatnością
- Zarządzanie prywatnością Udział tymczasowy
- Przeglądarka zarządzania prywatnością
- Recenzja
- Odszyfrowywanie usługi RMS
- Administrator żądania praw podstawowych
- Administrator przeglądu nadzorczych
- Menedżer allowblocklist dzierżawy

<br>

****

|Rola|Opis|Domyślne przypisania grup ról|
|---|---|---|
|**Administrator ataków**|Nie należy używać tej roli w Centrum & zgodności. Użyj odpowiedniej roli w usłudze Azure AD.|Administratorzy ataków|
|**Autor opłaty za ataki**|Nie należy używać tej roli w Centrum & zgodności. Użyj odpowiedniej roli w usłudze Azure AD.|Autorzy ataków na payload|
|**Dzienniki inspekcji**|Włącz i skonfiguruj inspekcję dla organizacji, wyświetl raporty inspekcji organizacji, a następnie wyeksportuj te raporty do pliku.|Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Zarządzanie sprawą**|Tworzenie, edytowanie, usuwanie i kontrolowanie dostępu do spraw zbierania elektronicznych materiałów dowodowych.|Zgodność komunikacji <p> Schoweki zgodności komunikacji <p> Administrator zgodności <p>Menedżer zbierania elektronicznych materiałów dowodowych <p> Zarządzanie ryzykiem w niejawnym programie testów <p> Administratorzy zarządzania ryzykiem w niejawnym programie testów <p> Analitycy zarządzania ryzykiem wewnętrznym <p> Badacze zarządzania ryzykiem wewnętrznym <p> Zarządzanie organizacją <p> Zarządzanie prywatnością <p> Administratorzy zarządzania prywatnością <p> Analitycy zarządzania prywatnością <p> Grupy zarządzania prywatnością <p> Administratorzy żądania praw podstawowych|
|**Komunikacja**|Zarządzaj całą komunikacją z elementami przechowawczymi zidentyfikowanymi w Advanced eDiscovery przypadku.  Tworzenie powiadomień o wstrzymaniu, blokowania przypomnień i eskalacji do zarządzania. Monitoruj potwierdzenia wstrzymywania powiadomień i zarządzaj dostępem do portalu tym, który jest używany przez każdego opiekuna w przypadku śledzenia komunikacji w przypadkach, gdy zostali zidentyfikowani jako opiekun.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych|
|**Administrator zgodności komunikacji**|Służy do zarządzania zasadami w funkcji zgodności komunikacji.|Zgodność komunikacji <p> Administratorzy zgodności komunikacji <p> Administrator zgodności <p> Zarządzanie organizacją|
|**Analiza zgodności komunikacji**|Umożliwia przeprowadzenie badania, korygowanie naruszeń wiadomości w funkcji Zgodności komunikacji. Może tylko wyświetlać dane meta wiadomości.|Zgodność komunikacji <p> Analitycy zgodności komunikacji <p> Schoweki zgodności komunikacji|
|**Zarządzanie zgodnością komunikacji**|Umożliwia dostęp do spraw zgodności komunikacji.|Zgodność komunikacji <p> Administratorzy zgodności komunikacji <p> Analitycy zgodności komunikacji <p> Schoweki zgodności komunikacji <p> Przeglądarki zgodności komunikacji <p> Administrator zgodności <p> Zarządzanie organizacją|
|**Badanie zgodności komunikacji**|Służy do wykonywania badań, rozwiązywania problemów i przeglądania naruszeń wiadomości w funkcji Zgodności komunikacji. Może wyświetlać dane meta i wiadomości.|Zgodność komunikacji <p> Schoweki zgodności komunikacji|
|**Przeglądarka zgodności komunikacji**|Umożliwia uzyskiwanie dostępu do raportów i widżetów w funkcji zgodności komunikacji.|Zgodność komunikacji <p> Przeglądarki zgodności komunikacji|
|**Administrator zgodności**|Wyświetlanie i edytowanie ustawień i raportów dotyczących funkcji zgodności.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją|
|**Administracja Menedżera zgodności**|Zarządzanie tworzeniem i modyfikowaniem szablonów.|Administratorzy Menedżera zgodności|
|**Ocena menedżera zgodności**|Tworzenie testów, wdrażanie działań udoskonalania i aktualizowanie stanu testów w przypadku działań udoskonalania.|Administratorzy Menedżera zgodności <p> Ocenianie menedżera zgodności|
|**Udział menedżera zgodności**|Twórz oceny i wykonuj prace, aby wdrożyć działania ulepszeń.|Administratorzy Menedżera zgodności <p> Ocenianie menedżera zgodności <p> Współautorzy Menedżera zgodności|
|**Czytnik Menedżera zgodności**|Wyświetlanie całej zawartości Menedżera zgodności z wyjątkiem funkcji administratora.|Administratorzy Menedżera zgodności <p> Ocenianie menedżera zgodności <p> Współautorzy Menedżera zgodności <p> Czytelnicy Menedżera zgodności|
|**Wyszukiwanie zgodności**|Przekonywuj wyszukiwania w skrzynkach pocztowych i uzyskaj szacowany wynik.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych <p> Zarządzanie organizacją <p> Operator zabezpieczeń|
|**Szybki**|Zidentyfikuj i zarządzaj Advanced eDiscovery sprawami oraz używaj informacji z Azure Active Directory i innych źródeł w celu znalezienia źródeł danych skojarzonych z nimi. Skojarz inne źródła danych, takie SharePoint, witryny poczty e-mail i Teams w przypadku przechowywania.  Umieść informacje prawne dotyczące źródeł danych skojarzonych z przechowywaniami, aby zachować zawartość w kontekście sprawy.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych|
|**Podgląd zawartości klasyfikacji danych**|Wyświetl renderowanie w miejscu plików w Eksploratorze zawartości.|Przeglądarka zawartości Eksploratora zawartości <p> Ochrona informacji <p> Schoweki ochrony informacji <p> Zarządzanie prywatnością <p> Grupy zarządzania prywatnością|
|**Dostawca opinii o klasyfikacji danych**|Umożliwia przekazywanie opinii klasyfikatorom w Eksploratorze zawartości.|Zgodność komunikacji <p> Schoweki zgodności komunikacji <p> Administrator zgodności|
|**Recenzent opinii o klasyfikacji danych**|Umożliwia przeglądanie opinii od klasyfikatorów w Eksploratorze opinii.|Administrator zgodności|
|**Przeglądarka listy klasyfikacji danych**|Wyświetl listę plików w Eksploratorze zawartości.|Przeglądarka list Eksploratora zawartości <p> Analitycy ochrony informacji <p> Zarządzanie prywatnością <p> Analitycy zarządzania prywatnością <p> Grupy zarządzania prywatnością <p> Przeglądarki zarządzania prywatnością|
|**Zarządzanie badaniem danych**|Tworzenie, edytowanie, usuwanie i kontrolowanie dostępu do badania danych.|Administrator zgodności <p> Data  Wiad.|
|**Zarządzanie urządzeniami**|Wyświetlanie i edytowanie ustawień i raportów dotyczących funkcji zarządzania urządzeniami.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Zarządzanie rozsyłaniem**|Uprawnienia do kontrolowania dostępu do ręcznego rozsyłania w Centrum & zgodności.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie rekordami|
|**Zarządzanie zgodnością DLP**|Wyświetlaj i edytuj ustawienia i raporty na temat zasad ochrony przed utratą danych (DLP).|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Eksportowanie**|Wyeksportuj zawartość skrzynki pocztowej i witryny zwróconą przez wyszukiwania.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych|
|**Wstrzymaj**|Umieść zawartość w skrzynkach pocztowych, witrynach i folderach publicznych w czeku. W miejscu przechowywania kopia zawartości jest przechowywana w bezpiecznym miejscu. Właściciele zawartości nadal będą mogli modyfikować lub usuwać oryginalną zawartość.|Administrator zgodności <p>Menedżer zbierania elektronicznych materiałów dowodowych <p> Zarządzanie organizacją|
|**Zarządzanie zgodnością IB**|Wyświetlanie, tworzenie, usuwanie, modyfikowanie i testowanie zasad bariery informacyjnej.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Administrator ochrony informacji**| Tworzenie, edytowanie i usuwanie zasad DLP, etykiet wrażliwości, ich zasad oraz wszystkich typów klasyfikatorów. Zarządzanie ustawieniami DLP punktu końcowego i trybem symulowania na przykład w przypadku zasad automatycznego oznaczania.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Ochrona informacji <p> Administratorzy ochrony informacji|
|**Analityk ochrony informacji**|Uzyskiwanie dostępu do alertów DLP i Eksploratora aktywności oraz zarządzanie nimi. Dostęp tylko do zasad DLP, etykiet wrażliwości i ich zasad oraz do wszystkich typów klasyfikatorów.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Ochrona informacji <p> Analitycy ochrony informacji <p> Schoweki ochrony informacji|
|**Ochrona informacji**|Dostęp do alertów DLP, Eksploratora aktywności i Eksploratora zawartości oraz zarządzanie nimi. Dostęp tylko do zasad DLP, etykiet wrażliwości i ich zasad oraz do wszystkich typów klasyfikatorów.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Ochrona informacji <p> Schoweki ochrony informacji|
|**Czytnik ochrony informacji**|Dostęp tylko do raportów dotyczących zasad DLP, etykiet wrażliwości i ich zasad.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Ochrona informacji <p> Czytniki informacji|
|**Administrator zarządzania ryzykiem w niejawnym programie testów**|Tworzenie, edytowanie, usuwanie i kontrolowanie dostępu do funkcji zarządzanie ryzykiem w niejawnym programie testów.|Administrator zgodności <p> Zarządzanie ryzykiem w niejawnym programie testów <p> Administratorzy zarządzania ryzykiem w niejawnym programie testów <p> Zarządzanie organizacją|
|**Analiza ryzyka w niejawnym programie testów**|Dostęp do wszystkich szablonów alertów, spraw i powiadomień dotyczących zarządzania ryzykiem w niejawnym programie testów.|Zarządzanie ryzykiem w niejawnym programie testów <p> Analitycy zarządzania ryzykiem wewnętrznym|
|**Inspekcja zarządzania ryzykiem w ramach niejawnego programu testów**|Zezwalaj na wyświetlanie śladów inspekcji ryzyka w niejawnym programie testów.|Zarządzanie ryzykiem w niejawnym programie testów <p> Audytorzy zarządzania ryzykiem w niejawnym programie testów|
|**Badanie ryzyka niejawnego programu testów**|Dostęp do wszystkich alertów zarządzania ryzykiem w niejawnym programie testów, spraw, szablonów powiadomień i Eksploratora zawartości we wszystkich przypadkach.|Zarządzanie ryzykiem w niejawnym programie testów <p> Badacze zarządzania ryzykiem wewnętrznym|
|**Trwały udział w zarządzaniu ryzykiem w niejawnym programie testów**|Ta grupa ról jest widoczna, ale jest używana tylko przez usługi w tle.|Współautorzy usługi IRM|
|**Sesje zarządzania ryzykiem w niejawnym programie testów**|Zezwalaj na zarządzanie żądaniami modyfikacji grupy na nagrywanie sesji.|Zarządzanie ryzykiem w niejawnym programie testów <p> Osoby zatwierdzające sesję zarządzania ryzykiem w niejawnym programie testów|
|**Udział tymczasowy w zarządzaniu ryzykiem w niejawnym programie testów**|Ta grupa ról jest widoczna, ale jest używana tylko przez usługi w tle.|Współautorzy usługi IRM|
|**Administrator wiedzy**|Konfiguruj wiedzę, uczenie się, przypisuj szkolenia i inne inteligentne funkcje.|Administratorzy wiedzy|
|**Zarządzanie alertami**|Wyświetlanie i edytowanie ustawień oraz raportów dla alertów.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń|
|**Konfiguracja organizacji**|Uruchamianie, wyświetlanie i eksportowanie raportów inspekcji oraz zarządzanie zasadami zgodności dla zasad DLP, urządzeń i zachowywania.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją|
|**Wersja zapoznawcza**|Wyświetl listę elementów zwróconych w wynikach wyszukiwania zawartości i otwórz każdy element z listy, aby wyświetlić jego zawartość.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych|
|**Administrator zarządzania prywatnością**|Zarządzaj zasadami w zarządzaniu prywatnością i masz dostęp do wszystkich funkcji rozwiązania.|Zarządzanie prywatnością <p> Administratorzy zarządzania prywatnością|
|**Analiza zarządzania prywatnością**|Wykonywanie badania i rozwiązywanie problemów dotyczących naruszeń wiadomości w zarządzaniu prywatnością. Może tylko wyświetlać metadane wiadomości.|Zarządzanie prywatnością <p> Analitycy zarządzania prywatnością|
|**Badanie zarządzania prywatnością**|Wykonywanie badań, rozwiązywanie problemów i przeglądanie naruszeń wiadomości w zarządzaniu prywatnością. Może wyświetlać metadane wiadomości i całą wiadomość.|Zarządzanie prywatnością <p> Grupy zarządzania prywatnością|
|**Trwały udział w zarządzaniu prywatnością**|Uzyskiwanie dostępu do spraw zarządzania prywatnością jako stały współautor.|Zarządzanie prywatnością <p> Współautorzy zarządzania prywatnością|
|**Zarządzanie prywatnością Udział tymczasowy**|Uzyskiwanie dostępu do spraw zarządzania prywatnością jako tymczasowy współautor.|Zarządzanie prywatnością <p> Współautorzy zarządzania prywatnością|
|**Przeglądarka zarządzania prywatnością**|Dostęp do pulpitów nawigacyjnych i widżetów w zarządzaniu prywatnością.|Zarządzanie prywatnością <p> Przeglądarki zarządzania prywatnością|
|**Kwarantanna**|Umożliwia wyświetlanie i zwalnianie poddanych kwarantannie wiadomości e-mail.|Administrator kwarantanny <p> Administrator zabezpieczeń <p> Zarządzanie organizacją|
|**RecordManagement**|Wyświetlanie i edytowanie konfiguracji funkcji zarządzania rekordami.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Zarządzanie rekordami|
|**Zarządzanie przechowywaniem**|Zarządzaj zasadami przechowywania, etykietami przechowywania i zasadami etykiet przechowywania.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Zarządzanie rekordami|
|**Recenzja**|Ta rola umożliwia użytkownikom dostęp do zestawów recenzji w Advanced eDiscovery przypadkach. Użytkownicy przypisani do tej roli mogą widzieć i otwierać listę spraw na stronie Zaawansowane zbierania elektronicznych materiałów dowodowych **>** w Centrum zgodności platformy Microsoft 365 których są członkami. Gdy użytkownik uzyskuje dostęp do sprawy Advanced eDiscovery, może wybrać pozycję **Przejrzyj zestawy**, aby uzyskać dostęp do danych dotyczących sprawy. Ta rola nie umożliwia użytkownikowi wyświetlania podglądu wyników przeszukiwania kolekcji skojarzonego ze sprawą ani wykonywania innych zadań związanych z wyszukiwaniem lub zarządzaniem sprawą. Użytkownicy z tą rolą mogą uzyskać dostęp do danych tylko w zestawie recenzji.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych <p> Recenzent|
|**Odszyfrowywanie usługi RMS**|Odszyfrowywanie zawartości chronionej usługą RMS podczas eksportowania wyników wyszukiwania.|Data  Wiad. <p> Menedżer zbierania elektronicznych materiałów dowodowych|
|**Zarządzanie rolami**|Zarządzaj członkostwem w grupach ról oraz twórz lub usuwaj niestandardowe grupy ról.|Zarządzanie organizacją|
|**Wyszukiwanie i przeczyszczanie**|Umożliwia zbiorcze usuwanie danych, które spełniają kryteria wyszukiwania zawartości.|Data  Wiad. <p> Zarządzanie organizacją|
|**Administrator zabezpieczeń**|Wyświetlanie i edytowanie konfiguracji i raportów dotyczących funkcji zabezpieczeń.|Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Czytnik zabezpieczeń**|Wyświetl konfigurację i raporty dotyczące funkcji zabezpieczeń.|Czytnik globalny <p> Zarządzanie organizacją <p> Operator zabezpieczeń <p> Czytnik zabezpieczeń|
|**Administrator etykiet wrażliwości**|Wyświetlanie, tworzenie, modyfikowanie i usuwanie etykiet wrażliwości.|Administrator danych dotyczących zgodności <p> Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Czytnik etykiet wrażliwości**|Wyświetl konfigurację i użycie etykiet wrażliwości.|Czytnik globalny <p> Zarządzanie organizacją <p> Czytnik zabezpieczeń|
|**Widok zapewniania ochrony usługi**|Pobierz dostępne dokumenty z sekcji Zapewnianie ochrony usługi. Zawartość obejmuje niezależną inspekcję, dokumentację dotyczącą zgodności z przepisami i wskazówki dotyczące zaufania dotyczące korzystania z funkcji Microsoft 365 do zarządzania zgodnością z przepisami i zagrożeniami bezpieczeństwa.|Czytnik globalny <p> Zarządzanie organizacją <p> Użytkownik zapewniania ochrony usługi|
|**Administrator przeglądu nadzorczych**|Zarządzaj zasadami przeglądu nadzorczych, w tym informacjami, które należy przejrzeć i kto powinien przeglądać.|Przegląd nadzorczy|
|**Współautor tagów**|Wyświetlanie i aktualizowanie członkostwa w istniejących tagach użytkowników.|Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń|
|**Menedżer znaczników**|Wyświetlanie, aktualizowanie, tworzenie i usuwanie tagów użytkowników.|Zarządzanie organizacją <p> Administrator zabezpieczeń|
|**Czytnik tagów**|Dostęp tylko do odczytu do istniejących tagów użytkowników.|Czytnik zabezpieczeń|
|**Menedżer allowblocklist dzierżawy**|Zarządzaj ustawieniami listy zablokowanych w dzierżawie.|Operator zabezpieczeń|
|**Dzienniki inspekcji tylko do wyświetlania**|Wyświetlanie i eksportowanie raportów inspekcji. Ponieważ raporty te mogą zawierać informacje poufne, tę rolę należy przypisywać tylko osobom jawnym, które muszą je wyświetlać.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń|
|**View-Only Case**||Zgodność komunikacji <p> Schoweki zgodności komunikacji <p> Administrator zgodności <p> Zarządzanie ryzykiem w niejawnym programie testów <p> Administratorzy zarządzania ryzykiem w niejawnym programie testów <p> Analitycy zarządzania ryzykiem wewnętrznym <p> Wąsy związane z zarządzaniem ryzykiem w niejawnym programie testów <p> Zarządzanie organizacją <p> Zarządzanie prywatnością <p> Administratorzy zarządzania prywatnością <p> Analitycy zarządzania prywatnością <p> Grupy zarządzania prywatnością <p> Administratorzy żądania praw podstawowych|
|**Zarządzanie urządzeniami tylko do odczytu**|Wyświetl konfigurację i raporty dotyczące funkcji Zarządzanie urządzeniami.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń <p> Czytnik zabezpieczeń|
|**Zarządzanie zgodnością DLP tylko w widoku**|Wyświetl ustawienia i raporty dotyczące zasad ochrony przed utratą danych (DLP).|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń <p> Czytnik zabezpieczeń|
|**Zarządzanie zgodnością IB tylko do wyświetlania**|Wyświetl konfigurację i raporty dla funkcji Bariery informacyjne.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń <p> Czytnik zabezpieczeń|
|**Zarządzanie alertami tylko do wyświetlania**|Wyświetl konfigurację i raporty dla funkcji zarządzania alertami.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Zarządzanie organizacją <p> Administrator zabezpieczeń <p> Operator zabezpieczeń <p> Czytnik zabezpieczeń|
|**Adresaci tylko do odczytu**|Wyświetlanie informacji o użytkownikach i grupach.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Czytnik globalny <p> Administrator przepływu poczty e-mail <p> Zarządzanie organizacją|
|**Zarządzanie rekordami tylko do odczytu**|Wyświetl konfigurację funkcji zarządzania rekordami.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> <p> Czytnik globalny <p> Zarządzanie organizacją|
|**Zarządzanie przechowywaniem tylko w widoku**|Wyświetl konfigurację zasad przechowywania, etykiet przechowywania i zasad etykiet przechowywania.|Administrator zgodności <p> Administrator danych dotyczących zgodności <p> Administrator globalny <p> Zarządzanie organizacją|
|