Nazwa narzędzia: WindowsDefenderEnabler.exe

Wersja: 1.0
Suma kontrolna SHA256: 721B6CC43875DA7C06BADB62876519921258A0B4C7F774D62272209F24DB5D9F
Rozmiar pliku: 14,5 KB
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

Cel: narzędzie Windows przeznaczone dla laboratoriów SOC oraz kontrolowanych środowisk testowych, służące do włączania 16 komponentów Windows Defender (9 funkcjonalnych mechanizmów ochrony oraz 7 usług i sterowników) w celu wsparcia badań nad złośliwym oprogramowaniem, inżynierii detekcji oraz szkoleń zespołów obronnych typu Blue Team.
Licencja: Darmowa do użytku osobistego i komercyjnego.

Funkcjonalność aplikacji:

(1) działa jako narzędzie Windows przeznaczone do przywracania funkcjonalności Windows Defender w środowiskach laboratoryjnych i wymaga uprawnień administratora;
(2) usuwa wartości rejestru na poziomie polityk, które były wykorzystywane do wyłączenia funkcjonalnych mechanizmów ochrony Defendera;
(3) przywraca konfigurację uruchamiania usług i sterowników powiązanych z Defenderem, ponownie ustawiając je w domyślnym trybie automatycznym;
(4) usuwa zadanie Harmonogramu zadań odpowiedzialne za wymuszanie trwałości stanu wyłączenia Defendera;
(5) zapisuje pojedynczy wpis z sygnaturą czasową przy każdym uruchomieniu do tego samego współdzielonego pliku dziennika, który jest używany przez narzędzie wyłączające, jednoznacznie wskazując, że Windows Defender został włączony oraz zachowując ciągłość audytu;
(6) wyświetla informacyjne okno dialogowe wyłącznie wtedy, gdy zadanie Harmonogramu zadań odpowiedzialne za wyłączenie Defendera istniało i zostało pomyślnie usunięte.

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

Tabela powyżej dokumentuje wszystkie funkcjonalne komponenty, usługi oraz sterowniki Windows Defender objęte egzekwowaniem na poziomie rejestru i usług; narzędzie usuwa lub przywraca te ustawienia w celu ponownego włączenia funkcjonalności Windows Defender.