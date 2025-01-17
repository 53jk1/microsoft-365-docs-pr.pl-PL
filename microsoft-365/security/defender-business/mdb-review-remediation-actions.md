---
title: Przeglądanie akcji korygowania w Microsoft Defender dla Firm
description: Wyświetlanie korygowania, które zostały wykonane automatycznie lub oczekujące na zatwierdzenie w Centrum akcji
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 15a64491f6e97137d1e919aa126d4bf134c47999
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862219"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Przeglądanie akcji korygowania w centrum akcji

> [!NOTE]
> Microsoft Defender dla Firm jest teraz uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md). 

W miarę wykrywania zagrożeń w grę wchodzą akcje korygowania. W zależności od konkretnego zagrożenia i sposobu konfigurowania ustawień zabezpieczeń akcje korygowania mogą być wykonywane automatycznie lub tylko po zatwierdzeniu. Przykłady akcji korygowania obejmują wysyłanie pliku do kwarantanny, zatrzymywanie procesu przed uruchomieniem i usuwanie zaplanowanego zadania. Wszystkie akcje korygowania są śledzone w centrum akcji.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Zrzut ekranu centrum akcji":::

**W tym artykule opisano**:

- [Jak używać centrum akcji](#how-to-use-the-action-center)
- [Działania naprawcze](#remediation-actions)

>
> **Masz minutę?**
> Weź udział w <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótkiej ankiecie dotyczącej bezpieczeństwa</a>. Chcielibyśmy usłyszeć od Ciebie!
>

## <a name="how-to-use-the-action-center"></a>Jak używać centrum akcji

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. W okienku nawigacji wybierz pozycję **Centrum akcji**.

3. Wybierz kartę **Oczekujące** , aby wyświetlić i zatwierdzić (lub odrzucić) wszystkie oczekujące akcje. Takie akcje mogą wynikać z ochrony antywirusowej/ochrony przed złośliwym kodem, zautomatyzowanych badań, działań ręcznego reagowania lub sesji odpowiedzi na żywo.

4. Wybierz kartę **Historia** , aby wyświetlić listę ukończonych akcji. 

## <a name="remediation-actions"></a>Działania naprawcze

Microsoft Defender dla Firm obejmuje kilka akcji korygowania. Te akcje obejmują ręczne akcje reagowania, akcje po zautomatyzowanym badaniu i akcje odpowiedzi na żywo.

W poniższej tabeli wymieniono dostępne akcje korygowania:

| Źródło  | Działania  |
|---------|---------|
| [Zautomatyzowane badania](../defender-endpoint/automated-investigations.md)      | — Kwarantanna pliku <br/>— Usuwanie klucza rejestru <br/>- Zabij proces <br/>— Zatrzymywanie usługi <br/>— Wyłączanie sterownika <br/>— Usuwanie zaplanowanego zadania        |
| [Ręczne akcje odpowiedzi](../defender-endpoint/respond-machine-alerts.md)   | — Uruchamianie skanowania antywirusowego <br/>- Izolowanie urządzenia <br/>— Zatrzymywanie i kwarantanna <br/>- Dodaj wskaźnik, aby zablokować lub zezwolić na plik       |
| [Odpowiedź na żywo](../defender-endpoint/live-response.md)   | - Zbieranie danych kryminalistycznych <br/>- Analizowanie pliku <br/>— Uruchamianie skryptu <br/>— Wysyłanie podejrzanej jednostki do firmy Microsoft w celu analizy <br/>— Korygowanie pliku <br/>- Proaktywne wyszukiwanie zagrożeń         |

## <a name="next-steps"></a>Następne kroki

- [Reagowanie na zagrożenia w Microsoft Defender dla Firm i eliminowanie ich](mdb-respond-mitigate-threats.md)
- [Zarządzanie urządzeniami w Microsoft Defender dla Firm](mdb-manage-devices.md)