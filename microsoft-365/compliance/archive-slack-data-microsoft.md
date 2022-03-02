---
title: Archiwizowanie danych usługi Slack zbierania elektronicznych materiałów dowodowych Microsoft 365 przy użyciu łącznika danych udostępnianego przez firmę Microsoft
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Dowiedz się, jak skonfigurować łącznik danych usługi Slack eDiscovery dostarczony przez firmę Microsoft i używać go do importowania i archiwizowania danych wiadomości błyskawicznych.
ms.openlocfilehash: 71369f2330193120f252d108641e99434c9fba78
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/28/2021
ms.locfileid: "63018982"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych zbierania elektronicznych materiałów dowodowych w u zapasie czasu (wersja zapoznawcza)

Łącznik danych usługi Slack eDiscovery dostarczony przez firmę Microsoft ułatwia importowanie i archiwizowanie danych wiadomości błyskawicznych (takich jak wiadomości, załączniki, linki i poprawki) z obszarów roboczych usługi Slack organizacji do Microsoft 365. Łącznik danych ściąga dane z interfejsu API zapasu czasu, konwertuje je na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365. Po zaimportowaniu danych z zapasu czasu możesz zastosować do zawartości zapasu czasu rozwiązania zgodności, takie jak zawieszenie w związku z postępowaniem sądowym, Advanced eDiscovery, Zgodność komunikacji i ustawienia przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika danych zbierania elektronicznych materiałów dowodowych usługi Slack może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Omówienie archiwizowania danych zbierania elektronicznych materiałów dowodowych usługi Slack

Poniższe omówienie przedstawia proces używania łącznika danych firmy Microsoft do archiwizowania danych oprogramowania Slack w Microsoft 365.

![Przepływ pracy archiwizacji zbierania elektronicznych materiałów dowodowych usługi Slack.](../media/SlackMSFTConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą Slack, aby skonfigurować i skonfigurować obszar roboczy usługi Slack.

2. Po skonfigurowaniu łącznika danych wiadomości z obszarów roboczych usługi Slack organizacji są kopiowane do skrzynek pocztowych użytkowników w programie Microsoft 365. Łącznik danych konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik zaim importuje przekonwertowane wiadomości czatu do skrzynek pocztowych konkretnych użytkowników. W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Slack eDiscovery** , a elementy wiadomości czatu są importowane do tego folderu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Twoja organizacja potrzebuje subskrypcji siatki Enterprise slack. Aby uzyskać więcej informacji, zobacz [Subskrypcje i funkcje usługi Slack](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Użytkownik tworzący łącznik danych musi mieć przypisaną **rolę aplikacji** Właściciele organizacji w swojej organizacji slack. Aby uzyskać więcej informacji, [zobacz Typy ról w uciekcie.](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack)

- Uzyskaj nazwę użytkownika i hasło do konta firmowego Slack swojej organizacji. Poświadczenia te są używane do logowania się do tego konta podczas tworzenia łącznika danych. Zalecane jest również automatyczne inicjowanie obsługi użytkowników w organizacji usługi Slack skonfigurowane do korzystania z logowania jednokrotnego (SSO).

- Użytkownik tworzący łącznik usługi Slack eDiscovery musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

## <a name="step-1-create-a-slack-ediscovery-connector"></a>Krok 1. Tworzenie łącznika zbierania elektronicznych materiałów dowodowych w u zapasie czasu

1. Przejdź do łączników <https://compliance.microsoft.com> danych w lewym okienku **nawigacji i** kliknij je.

2. Na karcie **Omówienie** kliknij pozycję **Filtruj** i wybierz pozycję **Według firmy Microsoft**, a następnie zastosuj filtr.

3. Kliknij **pozycję Slack eDiscovery (wersja zapoznawcza)**.

4. Na stronie **Opis produktu Slack eDiscovery (wersja zapoznawcza)** kliknij pozycję **Dodaj łącznik**.

5. Na stronie **kreatora Warunki użytkowania** usługi kliknij pozycję **Zaakceptuj**.

6. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**. W wprowadzeniu nazwy łącznika będzie on identyfikowany na **stronie Łączniki** danych po jego utworzeniu.

## <a name="step-2-sign-into-your-slack-organization"></a>Krok 2. Logowanie się do organizacji w u slackie

1. Na stronie **kreatora Sign into Slack (Logowanie do zapasu czasu** ) kliknij pozycję **Sign into Slack** (Zaloguj się do zapasu czasu), aby zalogować się do obszaru roboczego zapasu czasu Twojej organizacji.

2. Na stronie **Podpisywanie zapasu czasu** w obszarze roboczym wpisz nazwę obszaru roboczego, z którego chcesz zarchiwizować dane, a następnie kliknij przycisk **Kontynuuj**.

   Zostanie wyświetlona strona z nazwą obszaru roboczego programu Slack i monitem o zalogowanie się.

3. Kliknij link w ciągu Właściciele **organizacji, który również może zalogować się tutaj**.

4. Na stronie logowania obszaru roboczego wprowadź adres e-mail i hasło konta przedsiębiorstwa usługi Slack organizacji, a następnie kliknij **pozycję Zaloguj.**

   Po pomyślnym zalogowaniu zostanie wyświetlona strona z żądaniem uprawnień dostępu do twojej organizacji usługi Slack za pomocą aplikacji łącznika.

5. Kliknij **pozycję** Zezwalaj, aby zezwolić aplikacji na administrowanie organizacją.

   Po kliknięciu **przycisku Zezwalaj** strona zapasu czasu zostanie zamykana i zostanie wyświetlona strona Mapuj użytkowników zbierania elektronicznych materiałów dowodowych Microsoft 365 **slack** w kreatorze łączników.

## <a name="step-3-map-users-and-select-data-types-to-import"></a>Krok 3. Mapowanie użytkowników i wybieranie typów danych do zaimportowania

1. Skonfiguruj jedną lub obie z poniższych opcji w celu mapowania użytkowników usługi Slack na ich Microsoft 365 pocztowe.

   - **Automatyczne mapowanie użytkowników**. Zaznacz tę opcję, aby automatycznie mapować nazwy użytkowników usługi Slack Microsoft 365 skrzynki pocztowe. Łącznik działa przy użyciu wartości właściwości *Email* , którą zawiera każda wiadomość lub element oprogramowania Slack. Ta właściwość jest wypełniana adresem e-mail każdego uczestnika wiadomości. Jeśli łącznik może skojarzyć adresy e-mail z odpowiadającymi im Microsoft 365, element zostanie zaimportowany do skrzynki Microsoft 365 pocztowej tych użytkowników. Aby użyć tej opcji, musisz mieć skonfigurowane logowanie jednokrotne dla organizacji usługi Slack.

   - **Niestandardowe mapowanie użytkowników**. Możesz również użyć niestandardowego mapowania użytkowników zamiast automatycznego mapowania użytkowników (lub jako dodatku do niego). Przy użyciu tej opcji musisz utworzyć, a następnie przekazać plik CSV, który mapuje identyfikatory użytkowników z usługi Slack na ich Microsoft 365 e-mail. W tym celu kliknij pozycję Pobierz szablon mapowania plików **CSV**, wypełnij plik CSV identyfikatorem członka oprogramowania Slack i adresem e-mail usługi Microsoft 365 wszystkich użytkowników w organizacji, Microsoft 365 następnie wybierz i przekaż plik CSV do kreatora. Pamiętaj, aby nie zmieniać nagłówków kolumn w pliku CSV. Oto przykładowy plik mapowania plików CSV:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Identyfikatory członków dla użytkowników można uzyskać, klikając ... Przycisk Więcej w profilu użytkownika, a następnie wybierz pozycję **Kopiuj identyfikator członka**. Identyfikatory można również uzyskać dla wszystkich członków zespołu usługi Slack za pomocą metody interfejsu [API Slack users.list](https://api.slack.com/methods/users.list) .

   Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz plik mapowania niestandardowego, łącznik najpierw przyjrzy się plikowi mapowania niestandardowego i zamapuje użytkownika usługi Slack na skrzynkę pocztową usługi Microsoft 365 pocztowej. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 odpowiadającego użytkownikowi usługi Slack, łącznik użyje właściwości *Email* elementu Slack. Jeśli łącznik nie znajdzie prawidłowego Microsoft 365 w pliku mapowania niestandardowego lub właściwości Email elementu wiadomości, element nie zostanie zaimportowany.

2. Na **stronie Wybieranie typów danych do zaimportowania** kreatora wybierz typy danych zapasu czasu do zaimportowania. Jeśli chcesz zaimportować wiadomości ze wszystkich kanałów, wybierz wszystkie opcje. W przeciwnym razie wybierz tylko typy danych, które chcesz zaimportować.

     Oprócz komunikatów zapasu czasu można także określić inne typy zawartości zapasu czasu do zaimportowania do Microsoft 365. 

3. Po skonfigurowaniu typów danych do importowania kliknij przycisk **Dalej**, przejrzyj ustawienia łącznika, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>Krok 4. Monitorowanie łącznika usługi Slack eDiscovery

Po utworzeniu łącznika zbierania elektronicznych materiałów dowodowych zapasu czasu można wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie  wybierz łącznik zbierania elektronicznych materiałów dowodowych zapasu czasu, aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.