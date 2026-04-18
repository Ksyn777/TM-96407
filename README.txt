📱 Mobile Automation & Cloud-Ready Testing Suite
Prowadzący: mgr Mariusz Dworniczak

Student: Kamil Synowiec

Numer Albumu: 96407

🏗️ Architektura Projektu
Ten projekt to moje kompletne środowisko testowe. Zamiast instalować dziesiątki programów bezpośrednio na komputerze i zaśmiecać system, postawiłem na konteneryzację (Docker) i podejście Cloud-Ready. Dzięki temu cały zestaw narzędzi do testów mobilnych mogę uruchomić na dowolnym komputerze w kilka minut.

Mój Tech Stack:

Język: Python (logika testów i skrypty automatyzujące)

Automatyzacja UI: Appium (mózg operacji na interfejsie telefonu)

Infrastruktura: Docker (izolacja narzędzi od systemu)

Raportowanie: Allure (żeby błędy ładnie wyglądały na wykresach)

Analiza: MobSF & ADB (zaglądanie pod maskę aplikacji APK)

📅 PRZEBIEG LABORATORIUM (Co zrobiłem?)
🔹 BLOK 1: Tooling & Environment
Co zrobiono: Skonfigurowałem obrazy Dockera dla Appium i MobSF.

Wniosek: Używamy Dockera, bo dzięki temu nie musimy się martwić o "u mnie nie działa". Każdy ma dokładnie taką samą wersję narzędzi, a po skończonej pracy możemy jednym ruchem wszystko wyłączyć, nie zostawiając śmieci w systemie.

🔹 BLOK 2: Debugowanie i Analiza Statyczna (MobSF)
Co zrobiono: Przeskanowałem pliki APK w poszukiwaniu luk bezpieczeństwa.

Wniosek: Analiza statyczna pozwala testerowi dowiedzieć się, do czego aplikacja chce mieć dostęp (np. mikrofon, kontakty) i czy programista nie zostawił w kodzie jakichś niebezpiecznych "furtek" (jak tryb debugowania), zanim w ogóle klikniemy pierwszy przycisk.

🔹 BLOK 3-4: Fundamenty Skryptowania (Python for QA)
Co zrobiono: Nauczylem się pisać skrypty obsługujące listy, słowniki i funkcje, które automatyzują powtarzalne czynności.

Wniosek: Python w testach służy do tego, żeby nie klikać wszystkiego ręcznie. Używałem go do tworzenia warunków (jeśli test padnie -> zrób screena) i pętli.

🔹 BLOK 5-7: Hybrydowe Testowanie API
Co zrobiono: Testowałem połączenie aplikacji z serwerem za pomocą biblioteki requests. Sprawdzałem, czy serwer zwraca poprawne dane w formacie JSON.

🔹 BLOK 8: Appium UI Automation
Co zrobiono: Uczyłem się znajdować elementy na ekranie telefonu za pomocą ID oraz XPath. Symulowałem kliknięcia, wpisywanie tekstu i sprawdzanie, czy po kliknięciu wyświetlił się odpowiedni komunikat.

🔹 BLOK 9: Konteneryzacja Serwera (Docker Compose)
Co zrobiono: Spiąłem wszystko w pliku docker-compose.yml, dzięki czemu serwer Appium rusza razem z całym zapleczem jedną krótką komendą.

🔹 BLOK 10: MASTER PIPELINE (Finał) 🏆
To "mózg" mojego projektu. Napisałem skrypt pipeline.py, który robi wszystko za mnie:

Odpala Dockera.

Robi testy API (czy serwer żyje).

Robi testy UI (czy aplikacja działa).

Generuje raport Allure ze screenami błędów.

Sprząta po sobie.

📊 Raportowanie Wyników (Allure)
Dzięki Allure nie muszę czytać nudnych logów w konsoli. Widzę:

Dokładne kroki, które wykonał automat.

Zrzuty ekranu z momentu, w którym test się wywalił.

Informacje o tym, na jakim systemie i wersji Pythona ruszyły testy.

🚀 Jak to odpalić?
Bash
# 1. Wejdź do folderu
cd Artefakt10

# 2. Uruchom magię
python3 pipeline.py

# 3. Zobacz raport w przeglądarce
allure serve allure-results