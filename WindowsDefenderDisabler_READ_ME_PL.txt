Nazwa narzędzia: WindowsDefenderDisabler.exe

Wersja: 1.0
Suma kontrolna SHA256: C5C47EE71A2E5709A1CB4E470A909572D557B161A507EDAD7F022E49D70B3376
Rozmiar pliku: 44,5 KB
Napisane w: C# (w oparciu o .NET Framework 4.x).
Skompilowane do: pliku wykonywalnego .exe z nagłówkiem MZ.

Autor: Michał Sołtysik
Cybersecurity Analyst & Consultant | Forensics Examiner | SOC Trainer | Cyber Warfare Organizer
Analityk i Konsultant ds. Bezpieczeństwa Cybernetycznego | Ekspert ds. Informatyki Śledczej | Trener SOC (Centrum Operacji Bezpieczeństwa Cybernetycznego) | Organizator Działań w Cyberwojnie
Oficjalna strona: https://michalsoltysik.com/
LinkedIn: https://www.linkedin.com/in/michal-soltysik-ssh-soc/
Treści z zakresu cyberbezpieczeństwa: https://www.youtube.com/playlist?list=PL0RdRWQWldOAAKBqOVEutxKMP-a6CNoLY
Accredible: https://www.credential.net/profile/michalsoltysik/wallet
Credly: https://www.credly.com/users/michal-soltysik
Email: me@michalsoltysik.com

Cel: narzędzie Windows przeznaczone dla laboratoriów SOC oraz kontrolowanych środowisk testowych, służące do wyłączania 16 komponentów Windows Defender (9 funkcjonalnych mechanizmów ochrony oraz 7 usług i sterowników) w celu wsparcia badań nad malware, inżynierii detekcji oraz szkoleń blue team.
Licencja: Darmowa do użytku osobistego i komercyjnego.

Ważna informacja:

(1) Narzędzie modyfikuje krytyczną konfigurację zabezpieczeń Windows Defender poprzez egzekwowanie ustawień na poziomie rejestru oraz usług, przeznaczone wyłącznie dla izolowanych laboratoriów SOC i kontrolowanych środowisk testowych.
(2) Niewłaściwe użycie w środowisku produkcyjnym, sieci korporacyjnej lub systemie niezarządzanym może znacząco obniżyć poziom bezpieczeństwa systemu, narazić host na złośliwe oprogramowanie lub naruszyć wewnętrzne polityki bezpieczeństwa organizacji.
(3) Uruchomienie narzędzia musi być wyraźnie zatwierdzone przez właściciela systemu lub uprawnionego administratora. Użycie bez odpowiedniej autoryzacji lub poza kontrolowanymi scenariuszami testowymi jest zdecydowanie niewskazane.
(4) Obsługa narzędzia wymaga pełnego zrozumienia jego wpływu oraz pełnej odpowiedzialności za jego użycie.
(5) Narzędzie nigdy nie powinno być wdrażane na systemach produkcyjnych, stacjach roboczych użytkowników końcowych ani w środowiskach, w których mechanizmy ochronne muszą pozostać aktywne.

Funkcjonalność aplikacji:

(1) działa jako narzędzie Windows przeznaczone dla izolowanych środowisk laboratoryjnych i wymaga uprawnień administratora;
(2) wyłącza Windows Defender poprzez zastosowanie zmian w rejestrze na poziomie polityk, wpływających na 9 funkcjonalnych mechanizmów ochrony, w tym ochronę w czasie rzeczywistym, monitorowanie zachowań, raportowanie do chmury, mechanizmy skanowania oraz funkcje Exploit Guard;
(3) wyłącza 7 usług i sterowników powiązanych z Defenderem poprzez modyfikację ich konfiguracji uruchamiania na poziomie systemu;
(4) zapewnia trwałość stanu wyłączenia poprzez utworzenie i uruchamianie zadania Harmonogramu zadań działającego w kontekście SYSTEM z wieloma wyzwalaczami, w tym podczas startu systemu, logowania użytkownika oraz cyklicznego wykonywania, aby zapobiec automatycznemu ponownemu włączeniu Windows Defendera po upływie czasu;
(5) kopiuje się do stałej lokalizacji systemowej i uruchamia się z niej w celu zapewnienia spójnego wykonywania zadania;
(6) zapisuje pojedynczy wpis z sygnatura czasowa przy kazdym uruchomieniu, w tym podczas uruchomien przy starcie systemu, przy logowaniu uzytkownika oraz wielokrotnie w ciagu doby (osobne wyzwalacze czasowe - praktycznie co godzine), do wspoldzielonego pliku dziennika, rejestrujac operacje wylaczania Windows Defendera i zapewniajac prosty slad audytowy;
(7) wyświetla informacyjne okno dialogowe wyłącznie przy pierwszym uruchomieniu, gdy zadanie Harmonogramu zostaje utworzone.

Szczegóły - komponenty Windows Defender objęte działaniem:

| #  | Komponent / usługa / sterownik Defender | Typ                         | Efekt działania                                            |
| -- | --------------------------------------- | --------------------------- | ---------------------------------------------------------- |
| 1  | Rdzeń Antivirus / Antispyware           | Ochrona funkcjonalna        | Główne przełączniki polityk wyłączających Defender AV      |
| 2  | Wykrywanie PUA / PUP                    | Ochrona funkcjonalna        | Wyłącza wykrywanie potencjalnie niechcianych aplikacji     |
| 3  | Ochrona w czasie rzeczywistym           | Ochrona funkcjonalna        | Wyłącza główny silnik skanowania w czasie rzeczywistym     |
| 4  | Monitorowanie zachowań                  | Ochrona funkcjonalna        | Wyłącza silnik analizy behawioralnej                       |
| 5  | Skanowanie przy dostępie                | Ochrona funkcjonalna        | Wyłącza skanowanie przy otwieraniu i zapisie plików        |
| 6  | Skanowanie IOAV                         | Ochrona funkcjonalna        | Wyłącza skanowanie pobrań i załączników                    |
| 7  | Ochrona chmurowa i próbki               | Ochrona funkcjonalna        | Wyłącza backend chmurowy oraz przesyłanie próbek           |
| 8  | Exploit Guard                           | Ochrona funkcjonalna        | Wyłącza Controlled Folder Access i Network Protection      |
| 9  | Utwardzanie silnika skanowania          | Ochrona funkcjonalna        | Osłabia głębokość skanowania i mechanizmy silnika          |
| 10 | WinDefend                               | Usługa (tryb użytkownika)   | Główna usługa antywirusowa Windows Defender                |
| 11 | WdBoot                                  | Sterownik (start przy boot) | Ładuje komponenty Defendera podczas uruchamiania systemu   |
| 12 | WdFilter                                | Sterownik (filtr systemu)   | Minifiltr systemu plików przechwytujący operacje plikowe   |
| 13 | WdNisDrv                                | Sterownik (tryb jądra)      | Sterownik jądra Network Inspection System                  |
| 14 | WdNisSvc                                | Usługa (tryb użytkownika)   | Usługa logiki Network Inspection System                    |
| 15 | SecurityHealthService                   | Usługa (platforma / UI)     | Monitorowanie kondycji i raportowanie zabezpieczeń Windows |
| 16 | Sense                                   | Usługa (czujnik EDR)        | Czujnik Defender for Endpoint (EDR)                        |

Efekt operacyjny:

Tabela powyżej dokumentuje wszystkie funkcjonalne komponenty, usługi oraz sterowniki Windows Defender objęte egzekwowaniem na poziomie rejestru i usług; narzędzie stosuje te ustawienia w celu wyłączenia ochrony oraz zapewnienia, że Windows Defender nie włączy się ponownie automatycznie po upływie czasu.