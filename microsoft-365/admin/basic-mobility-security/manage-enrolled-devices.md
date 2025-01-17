---
title: Zarządzanie urządzeniami zarejestrowanymi w usłudze Mobile Zarządzanie urządzeniami w Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Usługa Basic Mobility and Security może pomóc w zabezpieczeniu urządzeń przenośnych organizacji i zarządzaniu nimi.
ms.openlocfilehash: f2da9a20c496d5229d62e477fcf4cc0024436788
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935242"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Zarządzanie urządzeniami zarejestrowanymi w usłudze Mobile Zarządzanie urządzeniami w Microsoft 365

Wbudowane zarządzanie urządzeniami przenośnymi dla Microsoft 365 ułatwia zabezpieczanie urządzeń przenośnych użytkowników, takich jak telefony iPhone, iPady, Androidy i Windows telefony oraz zarządzanie nimi. Pierwszym krokiem jest zalogowanie się do Microsoft 365 i skonfigurowanie pakietu Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Konfigurowanie pakietu Basic Mobility and Security](set-up.md).

Po skonfigurowaniu tych urządzeń osoby w organizacji muszą zarejestrować swoje urządzenia w usłudze. Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzenia przenośnego przy użyciu pakietu Basic Mobility and Security](enroll-your-mobile-device.md).Następnie możesz użyć pakietu Basic Mobility and Security, aby ułatwić zarządzanie urządzeniami w organizacji. Na przykład można użyć zasad zabezpieczeń urządzeń, aby ograniczyć dostęp do poczty e-mail lub innych usług, wyświetlać raporty urządzeń i zdalnie czyścić urządzenie. Zazwyczaj należy przejść do Centrum zgodności & zabezpieczeń, aby wykonać te zadania. Aby uzyskać więcej informacji, zobacz [Portal zgodności usługi Microsoft Purview](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Zadania zarządzania urządzeniami

Aby przejść do panelu zarządzania urządzeniami, wykonaj następujące kroki:

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Wpisz Mobile Zarządzanie urządzeniami w polu wyszukiwania i wybierz pozycję **Mobile Zarządzanie urządzeniami** z listy wyników.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Opcja zarządzania urządzeniami przenośnymi.":::

3. Wybierz **pozycję Rozpocznijmy**.

## <a name="manage-mobile-devices"></a>Zarządzanie urządzeniami przenośnymi

Po skonfigurowaniu pakietu Basic Mobility and Security poniżej przedstawiono kilka sposobów zarządzania urządzeniami przenośnymi w organizacji.

|Aby to zrobić|Zrób to|
|---|---|
|Czyszczenie urządzenia|W panelu Zarządzanie urządzeniami wybierz *nazwę urządzenia*, a następnie **pozycję Pełne czyszczenie**, aby usunąć wszystkie informacje lub **Selektywne czyszczenie**, aby usunąć tylko informacje organizacyjne na urządzeniu. Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security](wipe-mobile-device.md).|
|Blokuj dostęp nieobsługiwanych urządzeń do Exchange poczty e-mail przy użyciu Exchange ActiveSync|W panelu Zarządzanie urządzeniami wybierz pozycję **Blokuj**.|
|Konfigurowanie zasad urządzeń, takich jak wymagania dotyczące haseł i ustawienia zabezpieczeń|Na panelu Zarządzanie urządzeniami wybierz pozycję **Zasady** >  zabezpieczeń **urządzeńDodaj +**. Aby uzyskać więcej informacji, zobacz [Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security](create-device-security-policies.md).|
|Wyświetlanie listy zablokowanych urządzeń|W panelu Zarządzanie urządzeniami w obszarze **Wybierz widok wybierz pozycję** **Zablokowane**.|
|Odblokowywanie niezgodnego lub nieobsługiwanego urządzenia dla użytkownika lub grupy użytkowników|Wybierz jedną z następujących opcji, aby odblokować urządzenia:<br/>— Usuń użytkownika lub użytkowników z grupy zabezpieczeń, do których zostały zastosowane zasady. Przejdź do Centrum administracyjne platformy Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupy**</a>, a następnie wybierz nazwę grupy. Wybierz pozycję **Edytuj członków i administratorów**.<br/>— Usuń grupę zabezpieczeń, do których należą użytkownicy, z zasad urządzenia. Przejdź do obszaru Centrum zgodności & zabezpieczeń > **Zasady** >  **zabezpieczeńUrządzenia zasad zabezpieczeń**. Wybierz nazwę zasad urządzenia, a następnie wybierz pozycję **EdytujDeployment** > .<br/>— Odblokuj wszystkie niezgodne urządzenia dla zasad urządzeń. Przejdź do obszaru Centrum zgodności & zabezpieczeń > **Zasady** >  **zabezpieczeńUrządzenia zasad zabezpieczeń**. Wybierz nazwę zasad urządzenia, a następnie wybierz pozycję **Edytuj** >  **Wymagania dotyczące funkcjiAccess**. Wybierz pozycję **Zezwalaj na dostęp i naruszenie raportów**.<br/>— Aby odblokować niezgodne lub nieobsługiwane urządzenie dla użytkownika lub grupy użytkowników, przejdź do obszaru Centrum zgodności & zabezpieczeń > **Zasady** >  **zabezpieczeńZarządzanie urządzeniamiZarządzanie** >  **ustawieniami dostępu do urządzeń**. Dodaj grupę zabezpieczeń z elementami członkowskimi, które mają zostać wykluczone z zablokowania dostępu do Microsoft 365. Aby uzyskać więcej informacji, zobacz [Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w Centrum administracyjne platformy Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Usuwanie użytkowników, aby ich urządzenia nie były już zarządzane przez usługi Basic Mobility and Security|Aby usunąć użytkownika, edytuj grupę zabezpieczeń, która ma zasady zarządzania urządzeniami dla pakietu Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Tworzenie, edytowanie lub usuwanie grupy zabezpieczeń w Centrum administracyjne platformy Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Aby usunąć pakiet Basic Mobility and Security ze wszystkich użytkowników Microsoft 365, zobacz [Wyłączanie pakietu Basic Mobility and Security](turn-off.md).|

Na żywo (wersja 14)
