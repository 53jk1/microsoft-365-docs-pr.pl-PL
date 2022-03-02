---
title: Korzystanie z usługi Microsoft Defender dla interfejsów API punktów końcowych
ms.reviewer: ''
description: Dowiedz się, jak zaprojektować natywną aplikację Windows, aby uzyskać programowy dostęp do usługi Microsoft Defender for Endpoint bez użytkownika.
keywords: apis, api Graph, obsługiwane api, actor, alerts, device, user, domain, ip, file, advanced hunting, query
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f6cc0ea9cac46fa2e6ad2b5fe56422683d4a3e28
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996241"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Korzystanie z usługi Microsoft Defender dla interfejsów API punktów końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Na tej stronie opisano, jak utworzyć aplikację w celu uzyskania dostępu programowego do usługi Defender for Endpoint w imieniu użytkownika.

Jeśli potrzebujesz dostępu programowego Do programu Microsoft Defender for Endpoint bez użytkownika, zobacz Uzyskiwanie dostępu do programu [Microsoft Defender dla punktu końcowego w kontekście aplikacji](exposed-apis-create-app-webapp.md).

Jeśli nie masz pewności, którego dostępu potrzebujesz, przeczytaj stronę [Wprowadzenie](apis-intro.md).

Program Microsoft Defender for Endpoint udostępnia większość danych i akcji za pośrednictwem zestawu programistycznych interfejsów API. Te interfejsy API umożliwią automatyzowanie przepływów pracy i wprowadzania innowacji w oparciu o funkcje programu Microsoft Defender dla punktów końcowych. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Aby korzystać z interfejsów API, musisz wykonać następujące czynności:

- Tworzenie AAD aplikacji
- Uzyskiwanie tokenu dostępu przy użyciu tej aplikacji
- Korzystanie z tokenu w celu uzyskania dostępu do usługi Defender for Endpoint API

Na tej stronie wyjaśniono, jak utworzyć aplikację AAD, uzyskać token dostępu do programu Microsoft Defender dla punktu końcowego i zweryfikować token.

> [!NOTE]
> Podczas uzyskiwania dostępu do interfejsu API programu Microsoft Defender dla punktu końcowego w imieniu użytkownika są potrzebne odpowiednie uprawnienia aplikacji i użytkownika.
> Jeśli nie znasz uprawnień użytkowników do programu Microsoft Defender dla punktu końcowego, zobacz Zarządzanie dostępem do [portalu przy użyciu kontroli dostępu opartej na rolach](rbac.md).

> [!TIP]
> Jeśli masz uprawnienie do wykonywania akcji w portalu, masz uprawnienie do wykonywania tej akcji w interfejsie API.

## <a name="create-an-app"></a>Tworzenie aplikacji

1. Zaloguj się do [platformy Azure](https://portal.azure.com) przy użyciu konta użytkownika z rolą **administratora globalnego** .

2. Przejdź do **Azure Active Directory** \> **Rejestracja aplikacji Nowa** \> **rejestracja**.

   :::image type="content" alt-text="Obraz Microsoft Azure nawigacji do rejestracji aplikacji." source="images/atp-azure-new-app2.png" lightbox="images/atp-azure-new-app2.png":::

3. Gdy zostanie **wyświetlona strona Zarejestruj aplikację** , wprowadź informacje dotyczące rejestracji aplikacji:
   - **Nazwa** — wprowadź zrozumiałą nazwę aplikacji, która będzie wyświetlana użytkownikom aplikacji.
   - **Obsługiwane typy** kont — wybierz konta, które mają być obsługiwane w aplikacji.

     <br>

     |Obsługiwane typy kont|Opis|
     |---|---|
     |**Tylko konta w tym katalogu organizacyjnym**|Zaznacz tę opcję, jeśli budowania aplikacji biznesowej (LOB). Ta opcja nie jest dostępna, jeśli nie rejestrujesz aplikacji w katalogu. <p> Ta opcja jest mapowa na usługę Azure AD tylko z jedną dzierżawą. <p> Jest to opcja domyślna, chyba że rejestrujesz aplikację poza katalogiem. W przypadkach, gdy aplikacja jest zarejestrowana poza katalogiem, wartością domyślną jest wielodostępna usługa Azure AD i osobiste konta Microsoft.|
     |**Konta w dowolnym katalogu organizacyjnym**|Zaznacz tę opcję, jeśli chcesz, aby dotyczyło to wszystkich klientów biznesowych i edukacyjnych. <p> Ta opcja jest mapowa na usługę Azure AD tylko z wieloma dzierżawami. <p> Jeśli aplikacja została zarejestrowana jako tylko jedna dzierżawa usługi Azure AD, możesz ją zaktualizować, aby była wielodostępną dzierżawą usługi Azure AD, a z powrotem do pojedynczej dzierżawy za pośrednictwem bazy **danych uwierzytelniania.**|
     |**Konta w dowolnym katalogu organizacyjnym i osobiste konta Microsoft**|Zaznacz tę opcję, aby kierować użytkowników do najszerszego zestawu klientów. <p> Ta opcja jest mapowa na wielodostępne i osobiste konta Microsoft usługi Azure AD. <p> Jeśli aplikacja została zarejestrowana jako wielodostępna i osobiste konta Microsoft usługi Azure AD, nie można zmienić tego ustawienia w interfejsie użytkownika. Zamiast tego należy zmienić obsługiwane typy kont za pomocą edytora manifestu aplikacji.|

   - **Przekierowywanie URI (** opcjonalnie) — wybierz typ aplikacji, która jest budować, klienta sieci **Web** lub klienta publicznego (dla komputerów & urządzenia przenośnego **), a** następnie wprowadź adres URI przekierowania (lub adres URL odpowiedzi) dla aplikacji.

     - W przypadku aplikacji sieci Web podaj bazowy adres URL aplikacji. Może to być `http://localhost:31544` na przykład adres URL aplikacji sieci Web uruchomionej na komputerze lokalnym. Użytkownicy będą logować się do aplikacji klienckiej sieci Web przy użyciu tego adresu URL.

     - W przypadku publicznych aplikacji klienckich podaj URI używany przez usługę Azure AD do zwracania odpowiedzi tokenu. Wprowadź wartość specyficzną dla aplikacji, na przykład `myapp://auth`.

     Aby zobaczyć konkretne przykłady aplikacji sieci Web lub natywnych aplikacji, zapoznaj się z [przewodnikami Szybki start](/azure/active-directory/develop/#quickstarts).

     Po zakończeniu wybierz pozycję **Zarejestruj**.

4. Zezwalaj aplikacji na dostęp do programu Microsoft Defender dla punktu końcowego i przypisz jej uprawnienie "Odczyt alertów":

   - Na stronie aplikacji wybierz pozycję Uprawnienia **interfejsów API** Dodaj interfejsy **API**  \> \> uprawnień używane przez moją organizację, > **wpisz WindowsDefenderATP** i wybierz pozycję na **WindowsDefenderATP**.

     > [!NOTE]
     > *Funkcja WindowsDefenderATP* nie jest wyświetlana na oryginalnej liście. Zacznij pisać jego nazwę w polu tekstowym, aby ją wyświetlić.

     :::image type="content" alt-text="dodaj uprawnienie." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Wybierz **pozycję Alert uprawnień** **delegowanych.Odczyt** \> > pozycję **Dodaj uprawnienia**.

      :::image type="content" alt-text="uprawnienia aplikacji." source="images/application-permissions-public-client.png" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Wybierz odpowiednie uprawnienia. Tylko przykład to przeczytane alerty.

     Przykład:

     - Aby [uruchomić zapytania zaawansowane](run-advanced-query-api.md), wybierz **pozycję Uruchom uprawnienia zapytania zaawansowanego** .
     - Aby [wyizolować urządzenie](isolate-machine.md), wybierz pozycję **Wyizoluj uprawnienia komputera** .
     - Aby ustalić, jakich uprawnień potrzebujesz, wyświetl **sekcję Uprawnienia** w interfejsie API, który chcesz wywołać.

   - Wybierz **pozycję Ut przyznaj zgodę**.

      > [!NOTE]
      > Za każdym razem, gdy dodajesz uprawnienie, musisz wybrać pozycję U **udzielić** zgody, aby nowe uprawnienie było skuteczne.

      ![Obraz części Udzielanie uprawnień.](images/grant-consent.png)

5. Zategolij swój identyfikator aplikacji i identyfikator dzierżawy.

    Na stronie aplikacji przejdź do strony **Omówienie i** skopiuj następujące informacje:

    :::image type="content" alt-text="Obraz utworzonego identyfikatora aplikacji." source="images/app-and-tenant-ids.png" lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Uzyskiwanie tokenu dostępu

Aby uzyskać więcej informacji na AAD tokenów, zobacz [Samouczek dotyczący usługi Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>Używanie języka C\#

- Skopiuj/wklej poniżej klasy w aplikacji.
- Użyj **metody AcquireUserTokenAsync** z identyfikatorem aplikacji, identyfikatorem dzierżawy, nazwą użytkownika i hasłem, aby uzyskać token.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Sprawdź poprawność tokenu

Sprawdź, czy masz poprawny token:

- Skopiuj i wklej do [pliku JWT](https://jwt.ms) token, który masz w poprzednim kroku, aby go odkodować.
- Sprawdź, czy masz żądanie "scp" z wymaganymi uprawnieniami aplikacji.
- Na poniższym zrzucie ekranu możesz zobaczyć dekodowany token uzyskany z aplikacji w samouczku:

  :::image type="content" alt-text="Obraz sprawdzania poprawności tokenu." source="images/nativeapp-decoded-token.png" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Korzystanie z tokenu w celu uzyskania dostępu do programu Microsoft Defender for Endpoint API

- Wybierz odpowiedni interfejs API — obsługiwany program [Microsoft Defender dla interfejsów API punktów końcowych](exposed-apis-list.md).
- Ustaw nagłówek Authorization (Autoryzacja) w żądaniu HTTP, który wysyłasz na adres "Bearer {token}" (Bearer is the Authorization scheme).
- Czas wygaśnięcia tokenu to 1 godzina (możesz wysłać więcej niż jedno żądanie z tym samym tokenem).

- Przykład wysyłania żądania uzyskania listy alertów przy użyciu **języka C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Zobacz też

- [Interfejsy API programu Microsoft Defender dla punktów końcowych](exposed-apis-list.md)
- [Uzyskiwanie dostępu do programu Microsoft Defender dla punktu końcowego w kontekście aplikacji](exposed-apis-create-app-webapp.md)