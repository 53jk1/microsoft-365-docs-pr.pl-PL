---
title: Konfigurowanie łącznika do archiwizowania danych Jive w Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych Jive z usługi Veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych innych firm w Microsoft 365, dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania do zarządzania danymi innych firm w organizacji.
ms.openlocfilehash: 4fd5d7bbecd6fc6b0bfeeb90c0102ef30b67bdfe
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000493"
---
# <a name="set-up-a-connector-to-archive-jive-data"></a>Konfigurowanie łącznika do archiwizowania danych Jive

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy współpracy do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Jive](https://globanet.com/jive/) skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość, taką jak wiadomości e-mail, czaty i załączniki z konta Jive użytkownika, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po zapisaniu danych Jive w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Jive może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-jive-data"></a>Omówienie archiwizowania danych Jive

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych Jive w Microsoft 365.

![Przepływ pracy archiwizacji danych Jive.](../media/JiveConnectorWorkflow.png)

1. Twoja organizacja współpracuje z aplikacją Jive w celu skonfigurowania i skonfigurowania witryny Jive.

2. Raz na 24 godziny elementy z narzędzia Jive są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość elementów Jive na format wiadomości e-mail.

3. Łącznik Jive tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Nowy podfolder w folderze Skrzynka odbiorcza o nazwie **Jive** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Jive zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownikowi, który tworzy łącznik Jive w kroku 1 (i kończy go w kroku 3) musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-jive-connector"></a>Krok 1. Konfigurowanie łącznika Jive

Pierwszym krokiem jest uzyskanie dostępu do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych Jive.

1. Przejdź do pozycji [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  **danychJive**.

2. Na stronie Opis produktu **Jive** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-jive-connector"></a>Krok 2. Konfigurowanie łącznika Jive

Drugim krokiem jest skonfigurowanie łącznika Jive w lokacji Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika Jive, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Jive%20User%20Guide.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj poniższe kroki:

1. Na stronie **Mapowanie użytkowników Jive na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Jive zawierają właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-jive-connector"></a>Krok 4. Monitorowanie łącznika Jive

Po utworzeniu łącznika Jive możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **Jive** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych zaimportowanych do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.