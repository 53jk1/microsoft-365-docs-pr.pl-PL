---
title: Badanie użytkowników w programie Microsoft 365 Defender
description: Badanie użytkowników w przypadku incydentu w portalu Microsoft 365 Defender sieci.
keywords: zabezpieczenia, złośliwe oprogramowanie, Microsoft 365, M365, centrum zabezpieczeń, monitorowanie, raport, tożsamości, dane, urządzenia, aplikacje, zdarzenie, analiza, odpowiedź
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.date: ''
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: bfb8e1fb42dcde1a3140e0990221536c1b76b4f8
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015398"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Badanie użytkowników w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Badanie zdarzenia może obejmować konta użytkowników. Możesz zobaczyć szczegóły kont użytkowników zidentyfikowanych w alertach o zdarzeniu w portalu Microsoft 365 Defender na stronie Zdarzenia **& zdarzenia** \> ***_ \> _* Użytkownicy**. Oto przykład.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Przykład strony Użytkownicy dla zdarzenia." lightbox="../../media/investigate-incidents/incident-users.png":::

Aby szybko podsumować konto użytkownika dotyczące zdarzenia, zaznacz pole wyboru obok nazwy konta użytkownika. Oto przykład.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Przykład okienka podsumowania konta użytkownika dla zdarzenia." lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> Na stronie użytkownika są Azure Active Directory w usłudze Azure AD, a także grupy, co ułatwia zrozumienie grup i uprawnień skojarzonych z użytkownikiem.

W tym okienku możesz przeglądać informacje o zagrożeniach użytkowników, w tym bieżące zdarzenia, aktywne alerty i poziom ryzyka, a także informacje o narażeniu użytkowników, kontach, urządzeniach i innych.

Ponadto możesz podjąć działania bezpośrednio w portalu Microsoft 365 Defender, aby adresować naruszonego użytkownika, na przykład potwierdzić, że konto użytkownika jest naruszone lub wymagać nowego logowania.

W tym miejscu możesz wybrać pozycję **Przejdź do strony użytkownika,** aby wyświetlić szczegóły konta użytkownika. Oto przykład.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Przykład strony konta użytkownika dla zdarzenia." lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Możesz również wyświetlić tę stronę, wybierając nazwę konta użytkownika z listy na **stronie** Użytkownicy.

Członkostwo w grupach dla użytkownika można wyświetlić, wybierając numer w obszarze **Grupy**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Przykład członkostwa w grupach dla użytkownika." lightbox="../../media/investigate-users/user-group-membership.png":::

Wybierając ikonę w **obszarze Menedżer**, możesz zobaczyć, gdzie użytkownik znajduje się w drzewie organizacji.

Strona Microsoft 365 Defender użytkownika portalu łączy informacje z usług Microsoft Defender for Endpoint, Microsoft Defender for Identity i Microsoft Defender for Cloud Apps (w zależności od posiadanych licencji).

Na tej stronie przedstawiono informacje specyficzne dla ryzyka bezpieczeństwa konta użytkownika, w tym ocenę ryzyka oraz ostatnich zdarzeń i alertów, które wywężyły ogólne ryzyko.

Na tej stronie możesz wykonać następujące dodatkowe czynności:

- Oznaczanie konta użytkownika jako naruszonego
- Wymaganie ponownego zalogowania się użytkownika
- Zawieszanie konta użytkownika
- Zobacz ustawienia konta użytkownika usługi Azure AD
- Wyświetlanie plików należących do konta użytkownika
- Wyświetlanie plików udostępnionych temu użytkownikowi.

Oto przykład.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Przykładowe akcje na koncie użytkownika związane z zdarzeniem." lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Wyświetl ścieżki ruchu bocznego

Wybierając kartę  Ścieżki ruchu bocznego, można wyświetlić w pełni dynamiczną i klikaną mapę, która zapewnia wizualną reprezentację ścieżek ruchu bocznego do i od tego użytkownika, których można użyć do infiltracji sieci.

Mapa zawiera listę o tym, ile przeskoków między komputerami lub użytkownikami miałaby mieć atakująca w celu naruszenia poufnego konta, a jeśli użytkownik ma poufne konto, można sprawdzić, ile zasobów i kont jest połączonych bezpośrednio.

Jeśli w ciągu ostatnich dwóch dni nie wykryto dla encji potencjalnej ścieżki ruchu bocznego, wykres nie jest wyświetlany. Wybierz inną datę za pomocą opcji Wyświetl inną datę w celu wyświetlenia poprzednich  lateral movement paths graphs discovered for this entity. Raport ścieżki ruchu bocznego jest zawsze dostępny, aby przekazać informacje o wykrytych potencjalnych lateralnych ścieżkach ruchu i może być dostosowywany do czasu.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Przykład ścieżki ruchu bocznego dla użytkownika." lightbox="../../media/investigate-users/lateral-movement-path.png":::

Aby uzyskać więcej informacji, zobacz [Ścieżki ruchu bocznego](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Następne kroki

W razie potrzeby w przypadku zdarzeń w trakcie procesu kontynuuj [badanie](investigate-incidents.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)