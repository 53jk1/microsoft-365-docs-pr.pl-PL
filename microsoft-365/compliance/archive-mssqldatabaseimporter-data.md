---
title: Konfigurowanie łącznika do archiwizowania danych z usługi MS SQL Database
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z usługi MS SQL Database. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 0da93ade15c8cf5ddf758f16da89b46553fb3c83
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997514"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>Konfigurowanie łącznika do archiwizowania danych z usługi MS SQL Database

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Za pomocą łącznika veritas w portalu zgodności usługi Microsoft Purview można importować i archiwizować dane z usługi MS SQL Database do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik usługi MS SQL Database Importer skonfigurowany do przechwytywania elementów z bazy danych przy użyciu pliku konfiguracji XML i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość z usługi MS SQL Database na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po zapisaniu zawartości z ms SQL Database w skrzynkach pocztowych użytkownika można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, wykrywanie elektroniczne, zasady przechowywania i etykiety przechowywania. Użycie łącznika ms SQL Database do importowania i archiwizowania danych w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-the-ms-sql-data"></a>Omówienie archiwizacji danych SQL MS

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych ms SQL w Microsoft 365.

![Przepływ pracy archiwizacji danych ms SQL.](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Twoja organizacja współpracuje z dostawcą ms SQL Database w celu skonfigurowania i skonfigurowania witryny ms SQL Database.

2. Raz na 24 godziny elementy SQL Database MS są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również tę zawartość na format wiadomości e-mail.

3. Łącznik usługi MS SQL Database Importer tworzony w portalu zgodności, codziennie łączy się z witryną Veritas Merge1 i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje konwertowane elementy ms SQL Database do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **MS SQL Database Importer** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element z SQL Database MS zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik usługi MS SQL Database Importer w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>Krok 1. Konfigurowanie łącznika programu MS SQL Database Importer

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla SQL Database MS.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com), a następnie kliknij pozycję **Łączniki** >  **danychMS SQL Database Importer**.

2. Na stronie **Opis produktu MS SQL Database Importer** kliknij pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika programu MS SQL Database Importer w lokacji Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika programu MS SQL Database Importer w lokacji Merge1. Aby uzyskać informacje o sposobie konfigurowania programu MS SQL Database Importer, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika, wykonaj następujące kroki:

1. Na stronie **Mapowanie użytkowników usługi MS SQL Database Importer na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy SQL Database ms obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>Krok 4. Monitorowanie łącznika programu MS SQL Database Importer

Po utworzeniu łącznika usługi MS SQL Database Importer możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki**, a następnie wybierz łącznik **MS SQL Database** **Importer**, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.