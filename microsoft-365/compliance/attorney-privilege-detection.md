---
title: Konfigurowanie wykrywania uprawnień klienta-adwokata w usłudze eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Użyj modelu wykrywania uprawnień klienta-adwokata, aby użyć opartego na uczeniu maszynowym wykrywania zawartości uprzywilejowanej podczas przeglądania zawartości w przypadku zbierania elektronicznych materiałów dowodowych (Premium) w usłudze Microsoft Purview.
ms.openlocfilehash: 477b741cf617179ffd9eb1a4c38230faf5a0fce0
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997301"
---
# <a name="set-up-attorney-client-privilege-detection-in-ediscovery-premium"></a>Konfigurowanie wykrywania uprawnień klienta-adwokata w usłudze eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Głównym i kosztownym aspektem fazy przeglądu każdego procesu zbierania elektronicznych materiałów dowodowych jest przeglądanie dokumentów pod kątem zawartości uprzywilejowanej. Usługa Microsoft Purview eDiscovery (Premium) zapewnia oparte na uczeniu maszynowym wykrywanie uprzywilejowanej zawartości w celu zwiększenia wydajności tego procesu. Ta funkcja jest nazywana *wykrywaniem uprawnień klienta-adwokata*.

## <a name="how-does-it-work"></a>Jak to działa?

Po włączeniu wykrywania uprawnień adwokata klienta wszystkie dokumenty w zestawie przeglądów zostaną przetworzone przez model wykrywania uprawnień adwokata klienta podczas [analizowania danych](analyzing-data-in-review-set.md) w zestawie przeglądów. Model szuka dwóch rzeczy:

- Zawartość uprzywilejowana — model używa uczenia maszynowego do określenia prawdopodobieństwa, że dokument zawiera zawartość o charakterze prawnym.

- Uczestnicy — w ramach konfigurowania wykrywania uprawnień adwokata klienta należy przesłać listę prawników dla swojej organizacji. Model następnie porównuje uczestników dokumentu z listą adwokatów, aby ustalić, czy dokument ma co najmniej jednego uczestnika adwokata.

Model tworzy następujące trzy właściwości dla każdego dokumentu:

- **AttorneyClientPrivilegeScore:** Prawdopodobieństwo, że dokument ma charakter prawny; wartości wyniku to od **0** do **1**.

- **HasAttorney:** Ta właściwość jest ustawiona na **wartość true** , jeśli jeden z uczestników dokumentu jest wymieniony na liście adwokatów; w przeciwnym razie wartość jest **false**. Wartość jest również ustawiona na **wartość false** , jeśli organizacja nie przekazała listy adwokatów.

- **IsPrivilege:** Ta właściwość jest ustawiona na **wartość true** , jeśli wartość **attorneyClientPrivilegeScore** jest powyżej progu *lub* jeśli dokument ma uczestnika adwokata; w przeciwnym razie wartość jest ustawiona na **wartość false**.

Te właściwości (i odpowiadające im wartości) są dodawane do metadanych pliku dokumentów w zestawie przeglądów, jak pokazano na poniższym zrzucie ekranu:

![Właściwości uprawnień adwokata klienta wyświetlane w metadanych pliku.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Te trzy właściwości można również wyszukiwać w zestawie przeglądów. Aby uzyskać więcej informacji, zobacz [Wykonywanie zapytań o dane w zestawie przeglądów](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Konfigurowanie modelu wykrywania uprawnień klienta-adwokata

Aby włączyć model wykrywania uprawnień klienta-adwokata, organizacja musi go włączyć, a następnie przekazać listę adwokatów.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>Krok 1. Włączanie wykrywania uprawnień klienta-adwokata

Osoba, która jest administratorem zbierania elektronicznych materiałów dowodowych w organizacji (członkiem podgrupy administratora zbierania elektronicznych materiałów dowodowych w grupie ról Menedżera zbierania elektronicznych materiałów dowodowych) musi udostępnić model w przypadkach zbierania elektronicznych materiałów dowodowych (Premium).

1. W portalu zgodności usługi Microsoft Purview przejdź do obszaru [eDiscovery (Premium),](https://go.microsoft.com/fwlink/p/?linkid=2173764)a następnie kliknij pozycję **Ustawienia zbierania elektronicznych materiałów dowodowych (Premium**).

   ![Wybierz ustawienia zbierania elektronicznych materiałów dowodowych (Premium)](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę **Analiza**, a następnie przełącz przełącznik **Wykrywanie uprawnień klienta-adwokata** na włączony.

   ![Kliknij przycisk przełącz, aby włączyć wykrywanie uprawnień klienta-adwokata](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Kliknij przycisk **Zapisz** , aby zapisać zmianę.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>Krok 2. Upload listę adwokatów (opcjonalnie)

Aby w pełni wykorzystać model wykrywania uprawnień klienta-adwokata i skorzystać z wyników wcześniej opisanego wykrywania **funkcji ma adwokata** lub **potencjalnie uprzywilejowanego** , zalecamy przekazanie listy adresów e-mail dla prawników i pracowników prawnych, którzy pracują dla Twojej organizacji.

Aby przekazać listę adwokatów do użycia przez model wykrywania uprawnień klienta-adwokata:

1. Utwórz plik .csv (bez wiersza nagłówka) i dodaj adres e-mail dla każdej odpowiedniej osoby w osobnym wierszu. Zapisz ten plik na komputerze lokalnym.

2. Na stronie **Ustawienia** eDiscovery (Premium) wybierz kartę **Analiza**.

   Zostanie wyświetlona strona **Uprawnienia klienta adwokackiego** , a przełącznik **wykrywania uprawnień klienta-adwokata** jest włączony.

   ![Strona wysuwanego uprawnienia klienta-adwokata](..\media\AeDUploadAttorneyList1.png)

3. Wybierz **pozycję Wybierz plik** , a następnie znajdź i wybierz plik .csv utworzony w kroku 1.

4. Wybierz pozycję **Zapisz** , aby przekazać listę adwokatów.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Korzystanie z modelu wykrywania uprawnień klienta-adwokata

Wykonaj kroki opisane w tej sekcji, aby użyć funkcji wykrywania uprawnień klienta-adwokata dla dokumentów w zestawie przeglądów.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>Krok 1. Tworzenie grupy tagów inteligentnych przy użyciu modelu wykrywania uprawnień adwokackiego klienta

Jednym z podstawowych sposobów sprawdzania wyników wykrywania uprawnień klienta-adwokata w procesie przeglądu jest użycie grupy tagów inteligentnych. Grupa tagów inteligentnych wskazuje wyniki wykrywania uprawnień klienta-adwokata i wyświetla wyniki w wierszu obok tagów w grupie tagów inteligentnych. Dzięki temu można szybko identyfikować potencjalnie uprzywilejowane dokumenty podczas przeglądania dokumentów. Ponadto można również użyć tagów w grupie tagów inteligentnych, aby oznaczyć dokumenty jako uprzywilejowane lub nieuprzywilejowany. Aby uzyskać więcej informacji na temat tagów inteligentnych, zobacz [Konfigurowanie tagów inteligentnych w usłudze eDiscovery (Premium)](smart-tags.md).

1. W zestawie przeglądów zawierającym dokumenty analizowane w kroku 1 wybierz pozycję **Zarządzaj zestawem przeglądów** , a następnie wybierz pozycję **Zarządzaj tagami**.

2. W obszarze **Tagi** wybierz ciąg rozwijany obok pozycji **Dodaj grupę** , a następnie wybierz pozycję **Dodaj grupę tagów inteligentnych**.

   ![Wybierz pozycję "Dodaj grupę tagów inteligentnych".](../media/AeDCreateSmartTag.png)

3. Na stronie **Wybieranie modelu tagu inteligentnego** wybierz pozycję **Wybierz** obok **pozycji Uprawnienie adwokata klienta**.

   Zostanie wyświetlona grupa tagów o nazwie **Uprawnienie adwokata klienta** . Zawiera dwa tagi podrzędne o nazwie **Dodatnie** i **Ujemne**, które odpowiadają możliwym wynikom wygenerowanym przez model.

   ![Grupa tagów inteligentnych uprawnień klienta-adwokata.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Zmień nazwę grupy tagów i tagów odpowiednio do przeglądu. Na przykład można zmienić nazwę **Pozytywna** na **Uprzywilejowana** i **Negatywna** na **Nieusłuszona**.

### <a name="step-2-analyze-a-review-set"></a>Krok 2. Analizowanie zestawu przeglądów

Podczas analizowania dokumentów w zestawie przeglądów zostanie również uruchomiony model wykrywania uprawnień klienta-adwokata, a odpowiednie właściwości (opisane w artykule [Jak to działa?](#how-does-it-work)) zostaną dodane do każdego dokumentu w zestawie przeglądów. Aby uzyskać więcej informacji na temat analizowania danych w zestawie przeglądów, zobacz [Analizowanie danych w zestawie przeglądów w obszarze eDiscovery (Premium)](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>Krok 3. Przeglądanie zawartości uprzywilejowanej przy użyciu grupy tagów inteligentnych

Po przeanalizowaniu zestawu przeglądów i skonfigurowaniu tagów inteligentnych następnym krokiem jest przejrzenie dokumentów. Jeśli model ustalił, że dokument jest potencjalnie uprzywilejowany, odpowiedni tag inteligentny w **panelu Tagowanie** będzie wskazywać następujące wyniki wygenerowane przez wykrywanie uprawnień klienta-adwokata:

- Jeśli dokument zawiera zawartość, która może mieć charakter prawny, obok odpowiedniego tagu inteligentnego jest wyświetlana **etykieta Zawartość prawna** (która w tym przypadku jest **domyślnym** tagiem Pozytywny).

- Jeśli dokument zawiera uczestnika, który znajduje się na liście adwokatów organizacji, etykieta **Adwokat** jest wyświetlana obok odpowiedniego tagu inteligentnego (który w tym przypadku jest również domyślnym tagiem **dodatnim** ).

- Jeśli dokument zawiera zawartość, która może mieć charakter prawny *i* zawiera uczestnika znajdującego się na liście adwokatów, wyświetlane są zarówno **treści prawne**  , jak i etykiety **adwokatów** . 

Jeśli model stwierdzi, że dokument nie zawiera zawartości, która ma charakter prawny lub nie zawiera uczestnika z listy adwokatów, żadna etykieta nie jest wyświetlana w panelu tagowania.

Na przykład na poniższych zrzutach ekranu przedstawiono dwa dokumenty. Pierwsza z nich zawiera zawartość, która ma charakter prawny i zawiera uczestnika znajdującego się na liście adwokatów. Drugi nie zawiera żadnej z nich i w związku z tym nie wyświetla żadnych etykiet.

![Dokument z etykietami zawartości Prawnik i Prawne.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Dokument bez etykiet.](../media/AeDTaggingPanelNegative.png)

Po przejrzeniu dokumentu, aby sprawdzić, czy zawiera on uprzywilejowaną zawartość, możesz otagować dokument odpowiednim tagiem.
