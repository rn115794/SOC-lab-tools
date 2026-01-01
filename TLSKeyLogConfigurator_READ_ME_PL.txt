Nazwa narzędzia: TLSKeyLogConfigurator.exe

Wersja: 1.0
Suma kontrolna SHA256: FF0F128CE4E06ABAD6BF8820A269581275699FDC0E68779A6786141CDFA81D0A
Rozmiar pliku: 39 KB
Napisane w: PowerShell, uruchamiane w ramach opartego na .NET środowiska Windows PowerShell.
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

Cel: narzędzie Windows przeznaczone dla laboratoriów SOC oraz środowisk testowych o kontrolowanym dostępie, zapewniające automatyczną konfigurację logowania kluczy TLS na potrzeby analizy zaszyfrowanego ruchu webowego.
Licencja: Darmowa do użytku osobistego i komercyjnego.

Ważna informacja:

(1) Narzędzie konfiguruje logowanie kluczy TLS oraz preferencje Wireshark, umożliwiając deszyfrowanie i inspekcję zaszyfrowanego ruchu webowego do celów analitycznych.
(2) W przypadku niewłaściwego użycia logowanie kluczy TLS może umożliwić deszyfrowanie i wgląd w wrażliwe lub prywatne komunikacje, co może naruszać prywatność, poufność lub wewnętrzne polityki bezpieczeństwa organizacji.
(3) Uruchomienie narzędzia musi być wyraźnie zatwierdzone przez właściciela systemu lub uprawnionego administratora, a jego użycie musi być zgodne z obowiązującym prawem, politykami wewnętrznymi oraz zakresem udzielonej autoryzacji.
(4) Narzędzie jest przeznaczone wyłącznie do laboratoriów SOC, kontrolowanych środowisk testowych oraz autoryzowanych scenariuszy o charakterze śledczym lub szkoleniowym.
(5) Użycie narzędzia wymaga pełnego zrozumienia jego wpływu oraz pełnej odpowiedzialności za jego zastosowanie, w szczególności podczas pracy z odszyfrowanym ruchem sieciowym.

Wymaganie wstępne:

(1) Wireshark musi być zainstalowany w systemie, aby deszyfrowanie ruchu TLS było możliwe; narzędzie konfiguruje logowanie kluczy TLS oraz preferencje Wireshark, lecz nie instaluje samego narzędzia Wireshark.

Funkcjonalność aplikacji:

(1) działa jako aplikacja konsolowa wykonująca konfigurację logowania kluczy TLS w zakresie konta użytkownika oraz aktualizacje preferencji Wireshark; zalecane jest uruchamianie narzędzia z uprawnieniami administratora w celu zapewnienia poprawnego ustawienia Execution Policy dla bieżącego procesu;
(2) automatyzuje konfigurację logowania kluczy TLS w systemie Windows poprzez utworzenie dedykowanego katalogu i pliku z kluczami oraz skonfigurowanie zmiennej środowiskowej SSLKEYLOGFILE w zakresie użytkownika;
(3) aktualizuje preferencje Wireshark w celu umożliwienia deszyfrowania sesji TLS przy użyciu skonfigurowanego pliku z kluczami;
(4) udostępnia szczegółowy widok stanu obejmujący wykrycie instalacji Wireshark, istnienie i rozmiar pliku z kluczami (bajty, KB, MB), stan zmiennych środowiskowych (użytkownika i sesji) oraz status konfiguracji TLS w Wireshark;
(5) obsługuje tryb bezpiecznej konfiguracji (bez nadpisywania) oraz tryby wymuszone, z opcjonalnym tworzeniem kopii zapasowych istniejących plików z kluczami i łagodną obsługą zablokowanych plików;
(6) zapisuje wszystkie działania do pliku transkrypcji przechowywanego na pulpicie użytkownika, umożliwiając audyt oraz powtarzalność czynności w środowiskach śledczych oraz szkoleniowych typu SOC.