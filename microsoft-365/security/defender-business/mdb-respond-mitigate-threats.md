---
title: Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)
description: Po wykryciu zagrożeń możesz podjąć działania, aby zareagować na te zagrożenia i je zminimalizować.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 85c6262a03541b2aa0f79c69e60d9ebaec71bbe8
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027124"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business-preview"></a>Reagowanie na zagrożenia i ograniczanie ich w programie Microsoft Defender dla firm (wersja Preview)

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Portal Microsoft 365 Defender umożliwia Twojemu zespołowi zabezpieczeń reagowanie na wykryte zagrożenia i ich ograniczanie. W tym artykule opisano przykłady korzystania z usługi Defender dla firm (wersja Preview).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="view-detected-threats"></a>Wyświetlanie wykrytych zagrożeń

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Karty z powiadomieniami na stronie głównej. Karty informują o tym, ile zagrożeń zostało wykrytych wraz z tym, ile kont użytkowników, punktów końcowych (urządzeń) i innych zasobów wpłynęło na nie. Na poniższej ilustracji przedstawiono przykładowe karty:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Zrzut ekranu przedstawiający karty w portalu Microsoft 365 Defender witryny":::

3. Wybierz przycisk lub link na karcie, aby wyświetlić więcej informacji i podjąć działanie. Na przykład karta Ryzyko w **urządzeniach** zawiera przycisk **Wyświetl szczegóły** . Wybranie tego przycisku powoduje przysłanie na stronę **spisu** urządzeń, jak pokazano na poniższej ilustracji:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Zrzut ekranu przedstawiający spis urządzeń":::

   Na **stronie Spis urządzeń** jest wymieniona urządzenia organizacji wraz z ich poziomem ryzyka i poziomem ekspozycji.

4. Wybierz element, na przykład urządzenie. Zostanie otwarte okienko wysuwu z większej liczby alertów i zdarzeń wygenerowanych dla tego elementu, jak pokazano na poniższej ilustracji:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Zrzut ekranu przedstawiający okienko wysuwu dla wybranego urządzenia":::

5. Wyświetlanie wyświetlanych informacji w wysuwanych informacjach. Wybierz wielokropek (...), aby otworzyć menu z listą dostępnych akcji, jak pokazano na poniższej ilustracji: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Zrzut ekranu przedstawiający dostępne akcje dla wybranego urządzenia":::

6. Wybierz dostępną akcję. Możesz na przykład wybrać pozycję **Uruchom skanowanie antywirusowe**, co spowoduje, Program antywirusowy Microsoft Defender szybkie skanowanie na urządzeniu. Możesz też wybrać pozycję **Zainicjuj automatyczne badanie** , aby uruchomić automatyczne badanie na urządzeniu.

## <a name="next-steps"></a>Następne kroki

- [Przeglądanie działań naprawczych w Centrum akcji](mdb-review-remediation-actions.md)

- [Zarządzanie urządzeniami w programie Microsoft Defender dla firm (wersja preview)](mdb-manage-devices.md)

- [Wyświetlanie zdarzeń i zarządzanie nimi w programie Microsoft Defender dla firm (wersja Preview)](mdb-view-manage-incidents.md)