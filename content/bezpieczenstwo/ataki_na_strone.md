---
title: 'Przeciwdziałanie atakom'
order: 5
---

## Takie czasy...

Duża część naszej aktywności przeniosła się do się do sieci, a wraz z nią także ci :japanese_goblin:, którzy starają się wykorzystać naszą nieuwagę, brak znajomości problemów technicznych, czy czasem zwykły ludzki błąd... np. źle zaprojektowaną aplikację.

Dlatego wybraliśmy te technologie i strategie, które mają zapobiegać tym zjawiskom:

## Ataki typu XSS

Atak XSS (ang. Cross Site Scripting) – to próba umieszczenia w witrynach internetowych :globe_with_meridians: kodu, który zmieni ich treść lub funkcjonalność dla innych użytkowników tej witryny. Działanie takiego kodu zazwyczaj odbiega od oryginalnych zamierzeń twórców witryny czy aplikacji dlatego mówimy, że kod taki jest złośliwy. Do ataków XSS zalicza się bardzo wiele różnych działań — od zamiany arkuszy stylów tak aby powodowały nieprawidłowe kliknięcia użytkownika, podmianę danych wpisywanych w formularzach, różnego rodzaju utrudnienie wykorzystywania witryny kończąc na wykradaniu haseł wpisywanych do formularzy.

### XSS - Jak się bronimy?

Używamy wyłącznie sprawdzone, znane i szeroko przetestowane biblioteki (dodatkowy kod strony) takich dostawców jak Facebook (biblioteka React), które zostały przygotowane w sposób skutecznie zapobiegający podmianie kodu w naszej aplikacji.

## Ataki typu CSRF/XSRF

Cross-site request forgery (w skrócie CSRF lub XSRF) – metoda ataku na serwis internetowy, która często (m.in. na skutek jednoczesnego wykorzystania) mylona jest z cross-site scripting (XSS) bądź jest uznawana za jej podzbiór. Ofiarami CSRF stają się użytkownicy nieświadomie przesyłający do serwera żądania spreparowane przez osoby o wrogich zamiarach. W przeciwieństwie do XSS, ataki te nie są wymierzone w strony internetowe i nie muszą powodować zmiany ich treści. Celem hackera jest wykorzystanie uprawnień ofiary do wykonania operacji w przeciwnym razie wymagających jej zgody.
Atak ma na celu skłonić użytkownika zalogowanego do serwisu internetowego do tego, aby uruchomił on odnośnik :link:, którego otwarcie wykona w owym serwisie akcję, do której atakujący nie miałby w przeciwnym razie dostępu. Na przykład, użytkowniczka Małgosia, na stałe zalogowana do forum internetowego, może w pewnym momencie otworzyć spreparowany przez Jasia link, który zmieni jej dane kontaktowe albo usunie wątek dyskusji. Jako link może również posłużyć obrazek, którego adres został odpowiednio przygotowany, a konsekwencje wykonanej akcji mogą być znacznie poważniejsze.

### CSRF/XSRF - Jak się bronimy?

Wykorzystujemy kilka strategii:

- jednorazowe tokeny (rodzaj zaszyfrowanego hasła) wykorzystywane w komunikacji między użytkownikiem a serwerem np. w trakcie tworzenia konta w aplikacji, resetowania hasła oraz wszystkich innych czynności, które mogą mieć wpływ na bezpieczeństwo danych użytkownika i prawdziwości przekazywanych danych. Dołączamy do każdego przesyłanego formularza (np. rejestracji, wniosku) dodatkowego, specjalnego jednorazowego hasła w ukrytym polu, który, jeśli zostanie w jakikolwiek sposób zmanipulowany zostanie odrzucony przez serwer i przesłanie/pobranie danych zostanie natychmiast skutecznie zatrzymane,
- krótkie czasy ważności tokenów - kilku-, kilkunastogodzinne (w zależności od rodzaju) okresy ważności dodatkowo utrudniają złośliwe wykorzystanie czyjejś nieuwagi (np. nieuprawnione wykorzystanie skrzynki pocztowej, na którą wyślemy link do resetowania hasła)

## Ataki typu SQL injection

Zapytanie SQL to żądanie wykonania jakiejś czynności w bazie danych, zwykle jest to zapytanie ze strony internetowej pytającej o nazwę użytkownika i hasło. Ponieważ jednak większość stron nie wymaga podania żadnych danych poza nazwami użytkownika i hasłami, haker może wykorzystać pola formularzy do wysyłania własnych żądań, tzn. wstrzykiwania kodu SQL do bazy danych. Tym sposobem hakerzy mogą tworzyć, odczytywać, aktualizować, modyfikować i usuwać dane przechowywane w bazach danych, zwykle w celu pozyskania poufnych informacji, takich jak nr PESEL lub karty kredytowej czy inne dane finansowe.

### SQL injection - jak się bronimy?

Zastosowana przez nas technologia przesyłania zapytań SQL pomiędzy użytkownikami (również tymi o złych zamiarach) a serwerem i bazą danych chroni nas i Ciebie. Każdy kawałek kodu (np. wprowadzana treść w każdym polu wypełnianym przez użytkownika), który trafia do bazy jest izolowany i sprawdzany na wypadek umieszczenia w nim kodu SQL, który nie pochodzi z aplikacji i mógłby narobić szkód... Jeżeli taki kod zostałby wykryty - nie dojdzie do jego wykonania.

## Ataki typu DDoS

To chyba najbardziej znany rodzaj ataku na witrynę lub aplikację webową... Ataki typu DDoS (ang. distributed denial of service, w wolnym tłumaczeniu: rozproszona odmowa usługi) są jednymi z najczęściej występujących ataków hackerskich, które kierowane są na systemy komputerowe lub usługi sieciowe aplikacji i mają za zadanie zajęcie wszystkich dostępnych i wolnych zasobów w celu uniemożliwienia funkcjonowania całej usługi w sieci Internet. Atak DDoS polega na przeprowadzeniu ataku równocześnie z wielu miejsc jednocześnie (z wielu komputerów). Atak taki przeprowadzany jest głównie z komputerów, nad którymi przejęta została kontrola przy użyciu specjalnego oprogramowania (np. boty i trojany). Oznacza to, że właściciele tych komputerów mogą nawet nie wiedzieć, że ich komputer, laptop lub inne urządzenie podłączone do sieci, może być właśnie wykorzystywane, bez ich świadomości, do przeprowadzenia ataku DDoS.


### DDoS - jak się bronimy?

Oprócz zabezpieczeń sieciowych (np. w infrastrukturze Urzędu) dodatkowym zabezpieczeniem w aplikacji jest wykrywanie wielu żądań przychodzących (inicjowanych z komputera użytkownika), które następują w krótkim czasie (tzw. rate limiting). Połączenie z takiego komputera zostanie na pewien okres zablokowane.
