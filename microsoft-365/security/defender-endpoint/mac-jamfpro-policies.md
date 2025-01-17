---
title: Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender zasad systemu macOS w narzędziu Jamf Pro
description: Dowiedz się, jak skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender zasad systemu macOS w narzędziu Jamf Pro
keywords: policies, microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8d248eef175da6de3e329b4ec9b75b1111c668a6
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824723"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender zasad systemu macOS w narzędziu Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Usługa Defender dla punktu końcowego na komputerach Mac](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

Ta strona przeprowadzi Cię przez kroki, które należy wykonać, aby skonfigurować zasady systemu macOS w narzędziu Jamf Pro.

Musisz wykonać następujące kroki:

1. [Pobieranie pakietu dołączania Ochrona punktu końcowego w usłudze Microsoft Defender](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Tworzenie profilu konfiguracji w narzędziu Jamf Pro przy użyciu pakietu dołączania](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Konfigurowanie ustawień Ochrona punktu końcowego w usłudze Microsoft Defender](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Konfigurowanie ustawień powiadomień Ochrona punktu końcowego w usłudze Microsoft Defender](#step-4-configure-notifications-settings)
5. [Konfigurowanie usługi Microsoft AutoUpdate (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Udzielanie pełnego dostępu do dysku Ochrona punktu końcowego w usłudze Microsoft Defender](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Zatwierdzanie rozszerzenia jądra dla Ochrona punktu końcowego w usłudze Microsoft Defender](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Zatwierdzanie rozszerzeń systemu dla Ochrona punktu końcowego w usłudze Microsoft Defender](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Konfigurowanie rozszerzenia sieci](#step-9-configure-network-extension)
10. [Planowanie skanowania za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Krok 1. Pobieranie pakietu dołączania Ochrona punktu końcowego w usłudze Microsoft Defender

1. W [Microsoft 365 Defender](https://security.microsoft.com) przejdź do **obszaru Ustawienia > Punkty końcowe > dołączanie**.

2. Wybierz system macOS jako system operacyjny, a jako metodę wdrażania wybierz pozycję Mobile Zarządzanie urządzeniami/Microsoft Intune.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Strona Ustawienia Centrum zabezpieczeń usługi Microsoft Defender" lightbox="images/onboarding-macos.png":::

3. Wybierz pozycję **Pobierz pakiet dołączania** (WindowsDefenderATPOnboardingPackage.zip).

4. Wyodrębnij `WindowsDefenderATPOnboardingPackage.zip`.

5. Skopiuj plik do preferowanej lokalizacji. Na przykład `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Krok 2. Tworzenie profilu konfiguracji w narzędziu Jamf Pro przy użyciu pakietu dołączania

1. Znajdź plik `WindowsDefenderATPOnboarding.plist` z poprzedniej sekcji.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="Plik dołączania Windows Defender ATP" lightbox="images/plist-onboarding-file.png":::

2. Zaloguj się do narzędzia Jamf Pro, przejdź do **pozycji** **KomputeryProfile** >  konfiguracji i wybierz pozycję **Nowy**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Strona, na której tworzysz nowy pulpit nawigacyjny narzędzia Jamf Pro" lightbox="images/jamf-pro-configure-profile.png":::

3. Wprowadź następujące szczegóły:

   **Ogólne**:

   - Nazwa: dołączanie mde dla systemu macOS
   - Opis: dołączanie EDR MDE dla systemu macOS
   - Kategoria: Brak
   - Metoda dystrybucji: Instalowanie automatycznie
   - Poziom: poziom komputera

4.  Przejdź do strony **Ustawienia niestandardowych & aplikacji** i wybierz pozycję **Upload** >  **Dodaj**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Konfigurowanie aplikacji i ustawień niestandardowych" lightbox="images/jamfpro-mac-profile.png":::

5. Wybierz **pozycję plik Upload (plik PLIST),** a następnie w polu **Domena preferencji** wprowadź: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="Plik przekazywania narzędzia jamfpro plist" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Plik listy właściwości pliku przekazywania" lightbox="images/jamfpro-plist-file.png":::

6. Wybierz pozycję **Otwórz** i wybierz plik dołączania.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Plik dołączania" lightbox="images/jamfpro-plist-file-onboard.png":::

7. Wybierz **pozycję Upload**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Przekazywanie pliku plist" lightbox="images/jamfpro-upload-plist.png":::

8. Wybierz kartę **Zakres** .

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Karta Zakres" lightbox="images/jamfpro-scope-tab.png":::

9. Wybierz komputery docelowe.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Komputery docelowe" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Elementy docelowe" lightbox="images/jamfpro-targets.png":::

10. Wybierz **Zapisz**.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Wdrażanie komputerów docelowych" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Wybór komputerów docelowych" lightbox="images/jamfpro-target-selected.png":::

11. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Komputery grupy docelowej" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Lista profilów konfiguracji" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Krok 3. Konfigurowanie ustawień Ochrona punktu końcowego w usłudze Microsoft Defender

Do edytowania poszczególnych ustawień konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender można użyć interfejsu użytkownika jamf Pro gui lub użyć starszej metody, tworząc konfigurację Plist w edytorze tekstów i przekazując ją do Pro JAMF.

Należy pamiętać, że należy użyć dokładnie `com.microsoft.wdav` jako **domeny preferencji**, Ochrona punktu końcowego w usłudze Microsoft Defender używa tylko tej nazwy i `com.microsoft.wdav.ext` załadować jej ustawienia zarządzane!

(Wersja może być używana `com.microsoft.wdav.ext` w rzadkich przypadkach, gdy wolisz używać metody GUI, ale musisz również skonfigurować ustawienie, które nie zostało jeszcze dodane do schematu).

### <a name="gui-method"></a>Gui, metoda

1. Pobierz plik schema.json z [repozytorium GitHub usługi Defender](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) i zapisz go w pliku lokalnym:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Utwórz nowy profil konfiguracji w obszarze Komputery -> Profile konfiguracji, wprowadź następujące szczegóły na karcie **Ogólne** :

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Nowy profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Nazwa: Ustawienia konfiguracji MDAV protokołu MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (wartość domyślna)
    - Poziom: Poziom komputera (domyślny)
    - Metoda dystrybucji: Instalowanie automatycznie (ustawienie domyślne)

3. Przewiń w dół do karty **Ustawienia niestandardowych & aplikacji**, wybierz pozycję **Aplikacje zewnętrzne**, kliknij pozycję **Dodaj** i użyj **schematu niestandardowego** jako źródła do użycia dla domeny preferencji.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Dodawanie schematu niestandardowego" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Wprowadź `com.microsoft.wdav` jako domenę preferencji, kliknij pozycję **Dodaj schemat** i **Upload** plik schema.json pobrany w kroku 1. Kliknij **Zapisz**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="schemat Upload" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Wszystkie obsługiwane ustawienia konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender można wyświetlić poniżej w obszarze **Właściwości domeny preferencji**. Kliknij **pozycję Dodaj/Usuń właściwości** , aby wybrać ustawienia, które mają być zarządzane, a następnie kliknij przycisk **OK** , aby zapisać zmiany. (Ustawienia niezaznaczone nie zostaną uwzględnione w konfiguracji zarządzanej, użytkownik końcowy będzie mógł skonfigurować te ustawienia na swoich maszynach).

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Wybrane ustawienia zarządzane" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Zmień wartości ustawień na żądane wartości. Możesz kliknąć pozycję **Więcej informacji,** aby uzyskać dokumentację dla określonego ustawienia. (Możesz kliknąć pozycję **Plist preview** , aby sprawdzić, jak będzie wyglądać plist konfiguracji. Kliknij **pozycję Edytor formularzy** , aby wrócić do edytora wizualizacji).

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Strona, na której zmieniasz wartości ustawień" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Wybierz kartę **Zakres** .

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Zakres profilu konfiguracji" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. Wybierz **pozycję Grupa maszyn firmy Contoso**.

9. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Zapisz**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Strona, na której można dodać ustawienia konfiguracji" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Strona, na której można zapisać ustawienia konfiguracji" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy **profil konfiguracji**.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Strona, na której zostaną ukończone ustawienia konfiguracji" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Ochrona punktu końcowego w usłudze Microsoft Defender dodaje nowe ustawienia w czasie. Te nowe ustawienia zostaną dodane do schematu, a nowa wersja zostanie opublikowana w usłudze Github.
Aby mieć aktualizacje, wystarczy pobrać zaktualizowany schemat, edytować istniejący profil konfiguracji i **edytować schemat** na karcie **Ustawienia niestandardowych & aplikacji**.

### <a name="legacy-method"></a>Starsza metoda

1. Użyj następujących ustawień konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender:

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Nie włączono domyślnie, jeśli planujesz uruchomić usługę av innej firmy dla systemu macOS, ustaw ją na `true`wartość .

    - Wykluczenia
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR jest na przykładzie, jeśli przechodzisz weryfikację koncepcji, usuń go, zwłaszcza jeśli testujesz EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - Tagi
    - hideStatusMenuIcon

     Aby uzyskać informacje, zobacz [Lista właściwości dla pełnego profilu konfiguracji JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. Zapisz plik jako `MDATP_MDAV_configuration_settings.plist`.

3. Na pulpicie nawigacyjnym narzędzia Jamf Pro otwórz pozycję **Komputery** i ich **profile konfiguracji**. Kliknij **pozycję Nowy** i przejdź do karty **Ogólne** .

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Strona z wyświetlonym nowym profilem" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia konfiguracji MDAV protokołu MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (wartość domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie (wartość domyślna)
    - Poziom: Poziom komputera (wartość domyślna)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="Ustawienia konfiguracji MDATP MDAV" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. W **obszarze & niestandardowe Ustawienia** wybierz pozycję **Konfiguruj**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Ustawienia aplikacji i niestandardowe" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. Wybierz **pozycję plik Upload (plik PLIST)**.

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Plik plist ustawień konfiguracji" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. W **obszarze Domena preferencji** wprowadź ciąg `com.microsoft.wdav`, a następnie wybierz pozycję **Upload plik PLIST**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Domena preferencji ustawień konfiguracji" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. Wybierz **pozycję Wybierz plik**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Monit o wybranie pliku plist" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. Wybierz **plik MDATP_MDAV_configuration_settings.plist**, a następnie wybierz pozycję **Otwórz**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Ustawienia konfiguracji mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. Wybierz **pozycję Upload**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Przekazywanie ustawienia konfiguracji" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Monit o przekazanie obrazu związanego z ustawieniami konfiguracji" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Jeśli nastąpi przekazanie pliku Intune, zostanie wyświetlony następujący błąd:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Monit o przekazanie pliku usługi Intune związany z ustawieniami konfiguracji" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. Wybierz **Zapisz**.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Opcja zapisania obrazu związanego z ustawieniami konfiguracji" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Plik jest przekazywany.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Przekazany plik związany z ustawieniami konfiguracji" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Strona ustawień konfiguracji" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Wybierz kartę **Zakres** .

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Zakres ustawień konfiguracji" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. Wybierz **pozycję Grupa maszyn firmy Contoso**.

15. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Zapisz**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Ustawienia konfiguracji addsav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Powiadomienie o ustawieniach konfiguracji" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy **profil konfiguracji**.

    ![Obraz przedstawiający obraz profilu konfiguracji ustawień konfiguracji.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Ustawienia profilu konfiguracji" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

## <a name="step-4-configure-notifications-settings"></a>Krok 4. Konfigurowanie ustawień powiadomień

Te kroki mają zastosowanie do systemu macOS 10.15 (Catalina) lub nowszego.

1. Na pulpicie nawigacyjnym narzędzia Jamf Pro wybierz pozycję **Komputery**, a następnie pozycję **Profile konfiguracji**.

2. Kliknij pozycję **Nowy** i wprowadź następujące **szczegóły opcji:**

    - Karta **Ogólne**:
        - **Nazwa**: Ustawienia powiadomień MDAV protokołu MDATP
        - **Opis**: system macOS 10.15 (Catalina) lub nowszy
        - **Kategoria**: Brak *(wartość domyślna)*
        - **Metoda dystrybucji**: Instalowanie automatycznie *(ustawienie domyślne)*
        - **Poziom**: Poziom komputera *(domyślny)*

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Nowa strona profilu konfiguracji systemu macOS" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - **Powiadomienia** na karcie, kliknij przycisk **Dodaj** i wprowadź następujące wartości:
        - **Identyfikator pakietu**: `com.microsoft.wdav.tray`
        - **Alerty krytyczne**: kliknij pozycję **Wyłącz**
        - **Powiadomienia**: kliknij przycisk **Włącz**
        - **Typ alertu baneru**: wybierz pozycję **Dołącz** i **tymczasowe** *(wartość domyślna)*
        - **Powiadomienia na ekranie blokady**: kliknij pozycję **Ukryj**
        - **Powiadomienia w Centrum powiadomień**: kliknij pozycję **Wyświetl**
        - **Ikona aplikacji znaczek**: kliknij pozycję **Wyświetl**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="Zasobnik powiadomień mdatpmdav ustawień konfiguracji" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - **Powiadomienia** na karcie, kliknij przycisk **Dodaj** jeszcze raz, przewiń w dół do pozycji **Nowe powiadomienia Ustawienia**
        - **Identyfikator pakietu**: `com.microsoft.autoupdate.fba`
        - Skonfiguruj pozostałe ustawienia na takie same wartości jak powyżej

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Ustawienia konfiguracji mau powiadomień mdatpmdav" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Pamiętaj, że teraz masz dwie "tabele" z konfiguracjami powiadomień: jedną dla **identyfikatora pakietu: com.microsoft.wdav.tray**, a drugą dla **identyfikatora pakietu: com.microsoft.autoupdate.fba**. Chociaż można skonfigurować ustawienia alertów zgodnie z wymaganiami, identyfikatory pakietów muszą być dokładnie takie same, jak opisano wcześniej, a przełącznik **Dołączanie** musi być **włączony** dla **powiadomień**.

3. Wybierz kartę **Zakres** , a następnie wybierz pozycję **Dodaj**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Strona, na której można dodawać wartości ustawień konfiguracji" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. Wybierz **pozycję Grupa maszyn firmy Contoso**.

5. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Zapisz**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Strona, na której można zapisywać wartości dla grupy maszyn contoso ustawień konfiguracji" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Strona, która wyświetla powiadomienie o ukończeniu ustawień konfiguracji" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy **profil konfiguracji**.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Ukończone ustawienia konfiguracji" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Krok 5. Konfigurowanie usługi Microsoft AutoUpdate (MAU)

1. Użyj następujących ustawień konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender:

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
   </dict>
   </plist>
   ```

2. Zapisz go jako `MDATP_MDAV_MAU_settings.plist`.

3. Na pulpicie nawigacyjnym narzędzia Jamf Pro wybierz pozycję **Ogólne**.

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Ustawienia konfiguracji" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia MDAV MAU MDATP
    - Opis: Ustawienia autoupdate firmy Microsoft dla protokołu MDATP dla systemu macOS
    - Kategoria: Brak (wartość domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie (wartość domyślna)
    - Poziom: Poziom komputera (wartość domyślna)

5. W **obszarze & niestandardowe Ustawienia** wybierz pozycję **Konfiguruj**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Ustawienia konfiguracji aplikacji i ustawień niestandardowych" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. Wybierz **pozycję plik Upload (plik PLIST)**.

7. W **polu Domena preferencji** wprowadź: `com.microsoft.autoupdate2`, a następnie wybierz pozycję **Upload plik PLIST**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Domena preferencji ustawienia konfiguracji" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. Wybierz **pozycję Wybierz plik**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Monit o wybranie pliku dotyczącego ustawienia konfiguracji" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. Wybierz **pozycję MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Ustawienia mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. Wybierz **pozycję Upload**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Przekazywanie pliku dotyczącego ustawienia konfiguracji" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Strona z opcją przekazywania pliku dotyczącą ustawienia konfiguracji" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. Wybierz **Zapisz**.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Strona z opcją zapisywania pliku dotyczącą ustawienia konfiguracji" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Wybierz kartę **Zakres** .

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Karta Zakres ustawień konfiguracji" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. Wybierz opcję **Dodaj**.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Opcja dodawania obiektów docelowych wdrożenia" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Strona, na której dodajesz więcej wartości do ustawień konfiguracji" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Strona, na której można dodać więcej wartości do ustawień konfiguracji" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Powiadomienie o ukończeniu dotyczące ustawień konfiguracji" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Krok 6. Udzielanie pełnego dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender

1. Na pulpicie nawigacyjnym narzędzia Jamf Pro wybierz pozycję **Profile konfiguracji**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Profil, dla którego mają zostać skonfigurowane ustawienia" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. Wybierz pozycję **+ Nowy**.

3. Wprowadź następujące szczegóły:

    **Ogólne**
    - Nazwa: MDATP MDAV — udzielanie pełnego dostępu do EDR i AV
    - Opis: W systemie macOS Catalina lub nowszym nowa kontrolka zasad preferencji prywatności
    - Kategoria: Brak
    - Metoda dystrybucji: Instalowanie automatycznie
    - Poziom: poziom komputera

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Ogólnie rzecz biorąc, ustawienie konfiguracji" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. W **obszarze Konfigurowanie kontroli zasad preferencji prywatności** wybierz pozycję **Konfiguruj**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Kontrola zasad ochrony prywatności konfiguracji" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. W obszarze **Kontrola zasad preferencji prywatności** wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav`
    - Typ identyfikatora: identyfikator pakietu
    - Wymaganie dotyczące kodu: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Szczegóły kontroli zasad preferencji prywatności ustawienia konfiguracji" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. Wybierz pozycję **+ Dodaj**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Ustawienie konfiguracji umożliwia dodanie zasad systemowych dla wszystkich plików" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - W obszarze Aplikacja lub usługa: ustaw wartość **SystemPolicyAllFiles**

    - W obszarze "access": ustaw wartość **Zezwalaj**

7. Wybierz pozycję **Zapisz** (nie tę w prawym dolnym rogu).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Operacja zapisywania dla ustawienia konfiguracji" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. `+` Kliknij znak obok pozycji **Dostęp do aplikacji**, aby dodać nowy wpis.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Operacja zapisywania związana z ustawieniem konfiguracji" lightbox="images/tcc-add-entry.png":::

9. Wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav.epsext`
    - Typ identyfikatora: identyfikator pakietu
    - Wymaganie dotyczące kodu: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Wybierz pozycję **+ Dodaj**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="Wpis tcc epsext ustawienia konfiguracji" lightbox="images/tcc-epsext-entry.png":::

    - W obszarze Aplikacja lub usługa: ustaw wartość **SystemPolicyAllFiles**

    - W obszarze "access": ustaw wartość **Zezwalaj**

11. Wybierz pozycję **Zapisz** (nie tę w prawym dolnym rogu).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="Inne wystąpienie ustawienia konfiguracji tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. Wybierz kartę **Zakres** .

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Strona przedstawiająca zakres ustawienia konfiguracji" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. Wybierz pozycję **+ Dodaj**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Strona przedstawiająca ustawienie konfiguracji" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. Wybierz pozycję **Grupy komputerów** > w obszarze **Nazwa grupy** > wybierz pozycję **MachineGroup firmy Contoso**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="Ustawienie konfiguracji grupy maszyn contoso" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. Wybierz opcję **Dodaj**.

16. Wybierz **Zapisz**.

17. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Ustawienie konfiguracji contoso machine-group" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Ilustracja dotycząca ustawienia konfiguracji" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Alternatywnie możesz pobrać [plik fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) i przekazać go do profilów konfiguracji jamf zgodnie z opisem w temacie [Wdrażanie profilów konfiguracji niestandardowych przy użyciu narzędzia Jamf Pro| Metoda 2. Upload profil konfiguracji do narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Krok 7. Zatwierdzanie rozszerzenia jądra dla Ochrona punktu końcowego w usłudze Microsoft Defender

> [!CAUTION]
> Urządzenia Apple Silicon (M1) nie obsługują protokołu KEXT. Instalacja profilu konfiguracji składającego się z zasad KEXT zakończy się niepowodzeniem na tych urządzeniach.

1. W obszarze **Profile konfiguracji** wybierz pozycję **+ Nowy**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Automatycznie wygenerowany wpis w mediach społecznościowych Opis" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenie jądra MDAV MDATP
    - Opis: Rozszerzenie jądra MDATP (kext)
    - Kategoria: Brak
    - Metoda dystrybucji: Instalowanie automatycznie
    - Poziom: poziom komputera

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Jądro mdatpmdav ustawień konfiguracji" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. W **obszarze Konfigurowanie zatwierdzonych rozszerzeń jądra** wybierz pozycję **Konfiguruj**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Strona wyświetlająca zatwierdzone rozszerzenia jądra w ustawieniach konfiguracji" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. W **obszarze Zatwierdzone rozszerzenia jądra** wprowadź następujące szczegóły:

    - Nazwa wyświetlana: Microsoft Corp.
    - Identyfikator zespołu: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Okienko Zatwierdzone rozszerzenia jądra" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Wybierz kartę **Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Karta Zakres konfiguracji" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Wybierz pozycję **+ Dodaj**.

7. Wybierz pozycję **Grupy komputerów** > w obszarze **Nazwa grupy** > wybierz pozycję **Grupa maszyn firmy Contoso**.

8. Wybierz pozycję **+ Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Strona, na której definiujesz dodatkowe wartości ustawień konfiguracji" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Wybierz **Zapisz**.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="Rozszerzenie jądra MDAV MDATP" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Strona szczegółów profilów konfiguracji" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Alternatywnie możesz pobrać [plik kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) i przekazać go do profilów konfiguracji jamf zgodnie z opisem w temacie [Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia Jamf Pro| Metoda 2. Upload profil konfiguracji do narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Krok 8. Zatwierdzanie rozszerzeń systemu dla Ochrona punktu końcowego w usłudze Microsoft Defender

1. W obszarze **Profile konfiguracji** wybierz pozycję **+ Nowy**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Opis automatycznie wygenerowanego wpisu w mediach społecznościowych" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenia systemu MDAV MDATP
    - Opis: Rozszerzenia systemu MDATP
    - Kategoria: Brak
    - Metoda dystrybucji: Instalowanie automatycznie
    - Poziom: poziom komputera

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Nowy profil sysext ustawień konfiguracji" lightbox="images/sysext-new-profile.png":::

3. W **obszarze Rozszerzenia systemu** wybierz pozycję **Konfiguruj**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Okienko z opcją Konfiguruj dla rozszerzeń systemu" lightbox="images/sysext-configure.png":::

4. W **obszarze Rozszerzenia systemu** wprowadź następujące szczegóły:

   - Nazwa wyświetlana: Rozszerzenia systemu Microsoft Corp.
   - Typy rozszerzeń systemu: dozwolone rozszerzenia systemowe
   - Identyfikator zespołu: UBF8T346G9
   - Dozwolone rozszerzenia systemu:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="Okienko rozszerzeń systemu MDAV MDATP" lightbox="images/sysext-configure2.png":::

5. Wybierz kartę **Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Okienko wyboru Komputery docelowe" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Wybierz pozycję **+ Dodaj**.

7. Wybierz pozycję **Grupy komputerów** > w obszarze **Nazwa grupy** > wybierz pozycję **Grupa maszyn firmy Contoso**.

8. Wybierz pozycję **+ Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Okienko Nowy profil konfiguracji systemu macOS" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Wybierz **Zapisz**.

   :::image type="content" source="images/sysext-scope.png" alt-text="Wyświetlanie opcji dotyczących rozszerzeń systemu MDAV MDATP" lightbox="images/sysext-scope.png":::

10. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/sysext-final.png" alt-text="Ustawienia konfiguracji sysext — końcowy" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>Krok 9. Konfigurowanie rozszerzenia sieci

W ramach funkcji wykrywania punktów końcowych i reagowania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS sprawdza ruch gniazd i zgłasza te informacje do portalu Microsoft 365 Defender. Poniższe zasady umożliwiają rozszerzeniu sieci wykonywanie tej funkcji.

Te kroki mają zastosowanie do systemu macOS 10.15 (Catalina) lub nowszego.

1. Na pulpicie nawigacyjnym narzędzia Jamf Pro wybierz pozycję **Komputery**, a następnie pozycję **Profile konfiguracji**.

2. Kliknij pozycję **Nowy** i wprowadź następujące **szczegóły opcji:**

    - Karta **Ogólne**:
        - **Nazwa**: Rozszerzenie sieci usługi Microsoft Defender
        - **Opis**: system macOS 10.15 (Catalina) lub nowszy
        - **Kategoria**: Brak *(wartość domyślna)*
        - **Metoda dystrybucji**: Instalowanie automatycznie *(ustawienie domyślne)*
        - **Poziom**: Poziom komputera *(domyślny)*

    - **Filtr zawartości** karty:
        - **Nazwa filtru**: Filtr zawartości usługi Microsoft Defender
        - **Identyfikator**: `com.microsoft.wdav`
        - Pozostaw **pusty adres usługi**, **organizację**, **nazwę użytkownika**, **hasło**, **certyfikat** (*nie* wybrano opcji **Dołącz**)
        - **Kolejność filtrów**: Inspektor
        - **Filtr gniazd**: `com.microsoft.wdav.netext`
        - **Wymagane ustawienie filtru gniazda**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - Pozostaw puste pola **filtru sieciowego** (*nie* zaznaczono opcji **Dołącz**)

        Należy pamiętać, że dokładne wartości **identyfikatora**, **filtru gniazd** i **filtru gniazda wyznaczone wymagania** , jak określono powyżej.

        :::image type="content" source="images/netext-create-profile.png" alt-text="Ustawienie konfiguracji mdatpmdav" lightbox="images/netext-create-profile.png":::

3. Wybierz kartę **Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Karta sco ustawień konfiguracji" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. Wybierz pozycję **+ Dodaj**.

5. Wybierz pozycję **Grupy komputerów** > w obszarze **Nazwa grupy** > wybierz pozycję **Grupa maszyn firmy Contoso**.

6. Wybierz pozycję **+ Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Adim ustawień konfiguracji" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. Wybierz **Zapisz**.

   :::image type="content" source="images/netext-scope.png" alt-text="Okienko Filtr zawartości" lightbox="images/netext-scope.png":::

8. Wybierz pozycję **Gotowe**.

   :::image type="content" source="images/netext-final.png" alt-text="Netext ustawień konfiguracji — końcowy" lightbox="images/netext-final.png":::

Alternatywnie możesz pobrać [plik netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) i przekazać go do profilów konfiguracji JAMF zgodnie z opisem w temacie [Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia Jamf Pro| Metoda 2. Upload profil konfiguracji do narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Krok 10. Planowanie skanowania przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

Postępuj zgodnie z instrukcjami dotyczącymi [planowania skanowania za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Krok 11. Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

1. Przejdź do miejsca, w którym zapisano plik `wdav.pkg`.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Pakiet wdav eksploratora plików" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. Zmień jego nazwę na `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Pakiet wdavmdm eksploratora plików1" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Otwórz pulpit nawigacyjny narzędzia Jamf Pro.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Ustawienia konfiguracji narzędzia jamfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Wybierz komputer i kliknij ikonę koła zębatego u góry, a następnie wybierz pozycję **Zarządzanie komputerem**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Ustawienia konfiguracji — zarządzanie komputerem" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. W **obszarze Pakiety** wybierz pozycję **+ Nowy**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Opis ptaka dla automatycznie wygenerowanego pakietu" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. W **obszarze Nowy pakiet** wprowadź następujące szczegóły:

    **Karta Ogólne**
    - Nazwa wyświetlana: pozostaw ją na razie pustą. Ponieważ zostanie on zresetowany po wybraniu pkg.
    - Kategoria: Brak (wartość domyślna)
    - Nazwa pliku: wybierz plik

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Karta Ogólne dla ustawień konfiguracji" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Otwórz plik i wskaż go do `wdav.pkg` lub `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Ekran komputera z opisem automatycznie wygenerowanego pakietu" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. Wybierz opcję **Otwórz**. Ustaw **nazwę wyświetlaną** na zaawansowaną **ochronę przed zagrożeniami w usłudze Microsoft Defender i Program antywirusowy Microsoft Defender**.

    **Plik manifestu** nie jest wymagany. Ochrona punktu końcowego w usłudze Microsoft Defender działa bez pliku manifestu.

    **Karta Opcje**: Zachowaj wartości domyślne.

    **Karta Ograniczenia**: Zachowaj wartości domyślne.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Karta ograniczeń ustawień konfiguracji" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. Wybierz **Zapisz**. Pakiet jest przekazywany do narzędzia Jamf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Proces przekazywania pakietu ustawień konfiguracji dla pakietu związanego z ustawieniami konfiguracji" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Udostępnienie pakietu do wdrożenia może potrwać kilka minut.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Wystąpienie przekazywania pakietu dla ustawień konfiguracji" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. Przejdź do strony **Zasady** .

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Zasady ustawień konfiguracji" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Wybierz pozycję **+ Nowy,** aby utworzyć nowe zasady.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Nowe zasady ustawień konfiguracji" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. W **polu Ogólne** wprowadź następujące szczegóły:

    - Nazwa wyświetlana: MDATP Onboarding Contoso 200329 v100.86.92 lub nowsza

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Ustawienia konfiguracji — dołączanie protokołu MDATP" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. Wybierz **pozycję Cykliczne zaewidencjonowanie**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Cykliczne ewidencjonowanie ustawień konfiguracji" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. Wybierz **Zapisz**.

14. Wybierz pozycję **Pakiety, > skonfigurować**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Opcja konfigurowania pakietów" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Wybierz przycisk **Dodaj** obok pozycji **Zaawansowana ochrona przed zagrożeniami w usłudze Microsoft Defender i Program antywirusowy Microsoft Defender**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="Opcja dodawania większej liczby ustawień do rozwiązania MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. Wybierz **Zapisz**.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Opcja zapisywania ustawień konfiguracji" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Wybierz kartę **Zakres** .

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Karta Zakres powiązana z ustawieniami konfiguracji" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Wybierz komputery docelowe.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Opcja dodawania grup komputerów" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Zakres**

    Wybierz opcję **Dodaj**.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Ustawienia konfiguracji — ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Ustawienia konfiguracji — ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Samoobsługi**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Karta Samoobsługowe dla ustawień konfiguracji" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="Stan dołączania firmy Contoso z opcją jego ukończenia" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="Strona zasad" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
