---
title: Konfigurowanie łącznika do archiwizowania danych programu Refinitiv Eikon Messenger w programie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik 17a-4 Refinitiv Eikon Messenger DataParser i używać go do importowania i archiwizowania tych danych w programie Microsoft 365.
ms.openlocfilehash: 142cd5afa1c79c0a73f0ee810056ce2fb09134a5
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020691"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>Konfigurowanie łącznika do archiwizowania danych programu Refinitiv Eikon Messenger

Za pomocą [programu Refinitiv Eikon Messenger DataParser](https://www.17a-4.com/refinitiv-messenger-dataparser/) z firmy 17a-4 LLC. możesz importować i archiwizować dane z programu Refinitiv Eikon Messenger do skrzynek pocztowych użytkowników Microsoft 365 organizacji. Program DataParser zawiera łącznik refinitiv Eikon Messenger skonfigurowany do przechwytywania elementów ze źródła danych innej firmy i importowania ich do programu Microsoft 365. Łącznik Refinitiv Eikon Messenger DataParser konwertuje dane programu Refinitiv Eikon Messenger na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po zapisaniu danych programu Refinitiv Eikon Messenger w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak Zawieszenie w związku z postępowaniem sądowym, Zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika programu Refinitiv Eikon Messenger może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>Omówienie archiwizowania danych programu Refinitiv Eikon Messenger

Poniższe omówienie przedstawia proces używania łącznika danych do archiwizowania danych programu Refinitiv Eikon Messenger w programie Microsoft 365.

![Archiwizowanie przepływu pracy dla danych programu Refinitiv Eikon Messenger z 17a-4.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem 17a-4 w celu skonfigurowania i skonfigurowania programu Refinitiv Eikon Messenger DataParser.

2. Regularnie produkty Refinitiv Eikon Messenger są zbierane przez firmę DataParser. Program DataParser konwertuje również zawartość wiadomości na format wiadomości e-mail.

3. Łącznik refinitiv Eikon Messenger DataParser, który tworzysz w programie Centrum zgodności platformy Microsoft 365, łączy się z programem DataParser i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. W skrzynkach pocztowych użytkowników zostanie utworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Refinitiv Eikon Messenger DataParser** , a elementy programu Refinitiv Eikon Messenger zostaną zaimportowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element refinitiv Eikon Messenger zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto dataparser dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [działem 17a-4 LLC](https://www.17a-4.com/contact/). Podczas tworzenia łącznika w kroku 1 będzie konieczne zalogowanie się do tego konta.

- Użytkownik, który tworzy łącznik Refinitiv Eikon Messenger DataParser w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych 17a-4 jest dostępny w GCC w chmurze dla instytucji rządowych Microsoft 365 Usa. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie reprezentuje, że używanie tego produktu w celu łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne ze standardem FEDRAMP.

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 1. Konfigurowanie łącznika refinitiv Eikon Messenger DataParser

Pierwszym krokiem jest uzyskanie dostępu do strony Łączniki danych w programie Centrum zgodności platformy Microsoft 365 i utworzenie łącznika 17a-4 dla danych programu Refinitiv Eikon Messenger.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki danychRefinitiv** >  **Eikon Messenger DataParser**.

2. Na stronie **Refinitiv Eikon Messenger DataParser** opis produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta 17a-4 i wykonaj kroki w kreatorze połączenia Refinitiv Eikon Messenger DataParser.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 2. Konfigurowanie łącznika refinitiv Eikon Messenger DataParser

W pomocy technicznej 17a-4 skonfiguruj łącznik Refinitiv Eikon Messenger DataParser.

## <a name="step-3-map-users"></a>Krok 3. Mapowanie użytkowników

Łącznik Refinitiv Eikon Messenger DataParser automatycznie zamapuje użytkowników na ich Microsoft 365 e-mail przed zaimportowaniem danych do Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>Krok 4. Monitorowanie łącznika Refinitiv Eikon Messenger DataParser

Po utworzeniu łącznika refinitiv Eikon Messenger DataParser można wyświetlać stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz utworzony łącznik Refinitiv Eikon Messenger DataParser w celu wyświetlenia strony wysuwu zawierającej właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.