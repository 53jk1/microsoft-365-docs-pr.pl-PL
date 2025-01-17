---
title: Wyświetlanie i organizowanie kolejki Ochrona punktu końcowego w usłudze Microsoft Defender alertów
description: Dowiedz się, jak działają Ochrona punktu końcowego w usłudze Microsoft Defender alertów oraz jak sortować i filtrować listy alertów.
keywords: alerty, kolejki, alerty w kolejce, sortowanie, porządek, filtrowanie, zarządzanie alertami, nowy, w toku, rozwiązany, najnowszy, czas w kolejce, ważność, okres, alerty ekspertów ds. zagrożeń firmy Microsoft
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: 0d6b012d2e3dbe6778c8d9c70552cf24427f8a3d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472050"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Wyświetlanie i organizowanie kolejki Ochrona punktu końcowego w usłudze Microsoft Defender alertów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

W **kolejce alertów** jest wyświetlona lista alertów oflagowanych przez urządzenia w Twojej sieci. Domyślnie w widoku pogruponym w kolejce są wyświetlane alerty z ostatnich 30 dni. Najnowsze alerty są wyświetlane na początku listy, co ułatwia wyświetlanie najnowszych alertów.

> [!NOTE]
> Alerty są znacznie ograniczane dzięki zautomatyzowanym narzędziom do badania i rozwiązywania problemów, dzięki czemu eksperci w zakresie operacji zabezpieczeń mogą skoncentrować się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. Jeśli alert zawiera obsługiwaną jednostkę do automatycznego badania (na przykład pliku) na urządzeniu z obsługiwanym systemem operacyjnym dla tego urządzenia, można uruchomić automatyczne badanie i rozwiązywanie problemów. Aby uzyskać więcej informacji na temat zautomatyzowanych badań, zobacz [Omówienie zautomatyzowanych badań](automated-investigations.md).

Istnieje kilka opcji, które można wybrać, aby dostosować widok alertów.

W górnym okienku nawigacji możesz:

- Dostosowywanie kolumn w celu dodania lub usunięcia kolumn
- Stosowanie filtrów
- Wyświetlanie alertów dla określonego czasu trwania, takiego jak 1 dzień, 3 dni, 1 tydzień, 30 dni i 6 miesięcy
- Eksportowanie listy alertów do programu Excel
- Zarządzanie alertami

:::image type="content" source="images/alerts-queue-list.png" alt-text="Strona kolejki alertów" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Sortowanie i filtrowanie alertów 

Aby ograniczyć listę alertów i uzyskać bardziej skoncentrowany widok alertów, możesz zastosować następujące filtry.

### <a name="severity"></a>Ważność

Ważność alertu|Opis
---|---
High (Wysoki) <br> (Czerwony)|Alerty często spotykane z zaawansowanymi trwałymi zagrożeniami (MZ). Alerty te oznaczają duże ryzyko ze względu na poważne szkody, które mogą one spowodować na urządzeniach. Przykłady: działania związane z narzędziami do kradzieży poświadczeń, działania oprogramowania wymuszającego okup nieskojarzone z żadnymi grupami, manipulowanie czujnikiem zabezpieczeń lub złośliwą aktywnością osoby adversary.
Średni <br> (Orange)|Alerty wykrywanie i reagowanie w punktach końcowych dotyczące zachowań po naruszeniu zabezpieczeń, które mogą stanowić część zaawansowanego zagrożenia trwałego (MZ). Takie zachowania obejmują obserwowane zachowania typowe dla etapów ataków, nietypowych zmian rejestru, wykonywania podejrzanych plików i tak dalej. Niektóre z nich mogą być częścią wewnętrznych testów zabezpieczeń, ale wymagają badania, ponieważ mogą być także częścią zaawansowanego ataku.
Niska <br> (Żółty)|Alerty dotyczące zagrożeń związanych z rozpowszechnionym złośliwym oprogramowaniem. Na przykład narzędzia do łamania zabezpieczeń, narzędzia do łamania innych niż złośliwe oprogramowanie, takie jak uruchamianie poleceń eksploracji, czyszczenie dzienników itp., które często nie wskazują zaawansowanego zagrożenia skierowanego do organizacji. Może to być również na przykład wyizolowane narzędzie testowane przez użytkownika w organizacji.
Informacyjne <br> (Szary)|Alerty, które nie mogą być uznawane za niebezpieczne dla sieci, ale mogą zwiększyć świadomość bezpieczeństwa organizacji w sprawie potencjalnych problemów z zabezpieczeniami.

#### <a name="understanding-alert-severity"></a>Opis ważności alertów

Program antywirusowy Microsoft Defender (Microsoft Defender AV) i Defender for Endpoint alert severities are different because they represent different scopes.

Istotność Program antywirusowy Microsoft Defender zagrożenia oznacza bezwzględną ważność wykrytego zagrożenia (złośliwego oprogramowania) i jest przypisywana na podstawie potencjalnego zagrożenia dla poszczególnych urządzeń, jeśli zostało ono zainfekowane.

Ważność alertu programu Defender dla punktu końcowego oznacza powagę wykrytego zachowania, rzeczywiste ryzyko dla urządzenia, ale, co ważniejsze, potencjalne ryzyko dla organizacji.

Na przykład:

- Ważność alertu programu Defender dla punktu końcowego o Program antywirusowy Microsoft Defender, które było niemożliwe i nie infekowała urządzenia, została sklasyfikowana jako "informacyjna", ponieważ nie było żadnych rzeczywistych szkód.
- Alert o komercyjnym złośliwym oprogramowaniu został wykryty podczas wykonywania, ale zablokowany i naprawiony przez program Microsoft Defender AV, jest kategoryzowany jako "Niski", ponieważ mógł spowodować uszkodzenie poszczególnych urządzeń, ale nie stwarza zagrożenia organizacyjnego.
- Alert o wykryciu złośliwego oprogramowania podczas wykonywania, które może stanowić zagrożenie nie tylko dla pojedynczego urządzenia, ale również dla organizacji, niezależnie od tego, czy zostało później zablokowane, może zostać sklasyfikowane jako "Średni" lub "Wysoki".
- Podejrzane alerty o zachowaniu, które nie zostały zablokowane ani usunięte, zostaną sklasyfikowane jako "Niskie", "Średnie" lub "Wysokie" po uwzględnieniu tych samych kwestii zagrożenia organizacyjnego.

### <a name="status"></a>Stan

Możesz filtrować listę alertów na podstawie ich statusu.

### <a name="categories"></a>Kategorie

Ponownie zdefiniowaliśmy kategorie alertów w celu dostosowania do taktyki ataków w przedsiębiorstwie w macierzy [MITRE ATT&CK](https://attack.mitre.org/).[](https://attack.mitre.org/tactics/enterprise/) Nowe nazwy kategorii są stosowane do wszystkich nowych alertów. Istniejące alerty zachowają nazwy poprzednich kategorii.

### <a name="service-sources"></a>Źródła usług

Microsoft Threat Experts wersji Preview mogą teraz filtrować i wyświetlać wykrywanie nowych służb chłonianych zarządzanych przez ekspertów ds. zagrożeń.

Filtruj alerty na podstawie następujących źródeł usługi:

- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft 365 Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender
- Zarządzanie aplikacją
- AAD tożsamości

> [!NOTE]
> Filtr oprogramowania antywirusowego będzie wyświetlany tylko wtedy, gdy urządzenia Program antywirusowy Microsoft Defender jako domyślny produkt ochrony przed złośliwym kodem w czasie rzeczywistym.

### <a name="tags"></a>Tagi

Alerty można filtrować według tagów przypisanych do alertów.

### <a name="policy"></a>Zasady 

Alerty można filtrować w oparciu o następujące zasady:

|Źródło wykrywania|Wartość interfejsu API|
|---|---|
|Czujniki innych firm|ThirdPartySensors|
|Oprogramowanie antywirusowe|WindowsDefenderAv|
|Zautomatyzowane badanie|AutomatedInvestigation|
|Wykrywanie niestandardowe|CustomDetection|
|Niestandardowy zestaw ti|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|OfficeATP|
|Microsoft Threat Experts|ThreatExperts|
|SmartScreen|WindowsDefender SmartScreen|

### <a name="entities"></a>Jednostki

Alerty można filtrować na podstawie nazwy lub identyfikatora jednostki. 

### <a name="automated-investigation-state"></a>Stan zautomatyzowanego badania

Możesz filtrować alerty na podstawie stanu automatycznego badania.



## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender wiadomości](manage-alerts.md)
- [Badanie Ochrona punktu końcowego w usłudze Microsoft Defender alertów](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender pliku](investigate-files.md)
- [Badanie urządzeń na liście Ochrona punktu końcowego w usłudze Microsoft Defender urządzenia](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender adresu IP](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem Ochrona punktu końcowego w usłudze Microsoft Defender domeny](investigate-domain.md)
- [Badanie konta użytkownika w programie Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-user.md)
