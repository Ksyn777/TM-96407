RAPORT Z AUDYTU BEZPIECZEŃSTWA: APIDEMOS
Data: 18.04.2026
Audytor: [Kamil], [96407]
Projekt: Mobilny System Demonstracyjny (Android)
OCENA KOŃCOWA (SECURITY SCORE)
WYNIK: 0/100
STATUS: REJECTED / NEEDS FIX
Aplikacja otrzymała najniższą możliwą notę (0/100), co klasyfikuje ją jako krytycznie niebezpieczną. 
Powodem tak niskiej oceny jest nagromadzenie podatności o najwyższym stopniu ważności, w tym błędów konfiguracyjnych oraz krytycznych luk w bibliotekach zewnętrznych.
KLUCZOWE OBSZARY RYZYKA
A. Konfiguracja Systemowa (Zadanie 8.1)
Problem: Aktywna flaga debuggable="true" w pliku AndroidManifest.xml.
Wpływ: Pozwala na podpięcie zewnętrznego debuggera do działającej aplikacji. 
Napastnik może w ten sposób podejrzeć zawartość pamięci RAM, przechwycić zmienne sesyjne oraz ominąć zabezpieczenia ekranu logowania.
B. Wycieki Danych (Zadanie 8.2)
Problem: Wykrycie twardo zakodowanych poświadczeń w strings.xml (np. "password", "googlelogin_bad_login").
Wpływ: Przechowywanie haseł lub kluczy dostępu w zasobach aplikacji sprawia, że są one łatwo dostępne po dekompilacji pliku APK. 
Umożliwia to nieautoryzowany dostęp do usług powiązanych z aplikacją.
C. Biblioteki Zewnętrzne (Zadanie 8.3)
Problem: Wykorzystanie krytycznie podatnej biblioteki org.apache.commons (1.0.0).
Wpływ: Wykryta luka CVE-2015-7501 pozwala na zdalne wykonanie dowolnego kodu (RCE) na urządzeniu użytkownika. 
Dodatkowo biblioteka com.google.android.gms (10.0.1) wykazuje błędy w weryfikacji certyfikatów (CVE-2021-4352).
MAPA DROGOWA NAPRAWCZA (REMEDIATION)
[PRIORYTET 1]: Natychmiastowa aktualizacja biblioteki org.apache.commons do wersji wolnej od podatności oraz aktualizacja usług Google Play Services.
[PRIORYTET 1]: Bezwzględna zmiana wartości android:debuggable na "false" we wszystkich wersjach produkcyjnych aplikacji.
[PRIORYTET 2]: Usunięcie wszystkich zahardkodowanych haseł i kluczy z plików XML oraz wdrożenie mechanizmu Android Keystore do bezpiecznego zarządzania sekretami.
[PRIORYTET 2]: Wdrożenie połączeń szyfrowanych (HTTPS) zamiast wykrytych endpointów HTTP w celu zapobieżenia atakom Man-in-the-Middle (MITM).
WNIOSKI KOŃCOWE
Na podstawie przeprowadzonych zadań 8.1 - 8.4, aplikacja ApiDemos zostaje odrzucona w procesie audytu. 
Liczba błędów w łańcuchu dostaw (SCA) oraz brak podstawowej higieny programistycznej w zakresie przechowywania haseł dyskwalifikują ten produkt z użytku komercyjnego.
Podpis: [Kamil Synowiec]
