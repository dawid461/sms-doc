1. Utrzymanie produktu
++++++++++++++++++++++

1.1. Rozbudowa systemu
======================

Wersjowanie systemu
-------------------

**Zasady wersjowania systemu oraz podnoszenia wersji:**

* Oprogramowanie używające wersjonowania semantycznego MUSI określać swoje publiczne API. API to może być zadeklarowane w samym kodzie lub może istnieć w samej dokumentacji. Jakkolwiek jest zdefiniowane, powinno być precyzyjne i wyczerpujące.
* Standardowy numer wersji MUSI przyjąć formę X.Y.Z, gdzie X, Y i Z są nieujemnymi liczbami całkowitymi i NIE MOGĄ zawierać wiodących zer. X jest wersją major, Y wersją minor, a Z wersją patch. Każdy składnik MUSI rosnąć numerycznie. Przykładowo: 1.9.0 → 1.10.0 → 1.11.0.
* Po wydaniu wersjonowanego pakietu zawartość tej wersji NIE MOŻE być modyfikowana. Jakiekolwiek zmiany MUSZĄ być wydane jako nowa wersja.
* Wersja major zero (0.y.z) jest przeznaczona dla początkowej fazy rozwoju. Wszystko może ulec zmianie w dowolnym momencie. Publiczne API nie powinno być traktowane jako stabilne.
* Wersja 1.0.0 określa publiczne API. Sposób, w jaki numer wersji jest zwiększany po tym wydaniu, zależy od tego publicznego API i jak się ono zmienia.
* Wersja patch Z (x.y.Z | x > 0) MUSI zostać zwiększona, jeśli wprowadza się tylko kompatybilne wstecz naprawy błędów. Naprawa błędu definiowana jest jako zmiana wewnętrzna, która usuwa nieprawidłowe działanie.
* Wersja minor Y (x.Y.z | x > 0) MUSI zostać zwiększona, jeśli nowa, kompatybilna wstecz funkcjonalność zostaje wprowadzona do publicznego API. MUSI zostać zwiększona, jeśli jakakolwiek funkcjonalność publicznego API zostaje zdezaprobowana. MOŻE zostać zwiększona, jeśli wprowadzone zostają nowe znaczące funkcjonalności lub ulepszenia w obrębie prywatnego kodu. MOŻE ona zawierać zmiany na poziomie patch. Numer wersji patch MUSI być ustawiony na 0, gdy wersja minor jest zwiększana.
* Wersja major X (X.y.z | X > 0) MUSI zostać zwiększona, jeżeli do publicznego API są wprowadzane jakiekolwiek wstecznie niekompatybilne zmiany. MOŻE zawierać zmiany na poziomie minor oraz patch. Numery wersji minor oraz patch MUSZĄ być ustawione na 0, gdy wersja major jest zwiększana.
* Wydanie przedpremierowe MOŻE być oznaczone przez dołączenie dywizu oraz zbioru identyfikatorów rozdzielonych kropkami, zaraz za numerem wersji patch. Identyfikatory MUSZĄ składać się wyłącznie ze znaków alfanumerycznych ASCII oraz myślników [0-9A-Za-z-]. Identyfikatory NIE MOGĄ być puste. Numeryczne identyfikatory NIE MOGĄ zawierać wiodących zer. Wydania przedpremierowe poprzedzają powiązane z nimi wersje standardowe. Wydanie przedpremierowe wskazuje na niestabilność wersji i możliwość niespełniania wymogów kompatybilności, które cechują powiązaną z nią standardową wersję. Przykłady: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
* Meta-dane buildu MOGĄ być oznaczone przez dołączenie znaku plus oraz zbioru identyfikatorów rozdzielonych kropkami, zaraz za numerem wersji patch lub wydania przedpremierowego. Identyfikatory MUSZĄ składać się wyłącznie ze znaków alfanumerycznych ASCII oraz myślników [0-9A-Za-z-]. Identyfikatory NIE MOGĄ być puste. Meta-dane buildu POWINNY być ignorowane przy ustalaniu kolejności wersji. Zatem dwie wersje różniące się tylko meta-danymi buildu mają ten sam stopień pierwszeństwa. Przykłady: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
* Pierwszeństwo odnosi się do sposobu porównywania wersji między sobą podczas ich porządkowania. Pierwszeństwo MUSI być ustalane w rozdzieleniu wersji na identyfikatory major, minor, patch oraz identyfikator przedpremierowy w podanej kolejności (meta-dane buildu nie decydują o pierwszeństwie). Pierwszeństwo jest ustalane przez pierwszą różnicę wykrytą podczas porównania każdego z identyfikatorów od lewej do prawej: wersje major, minor, patch są zawsze porównywane numerycznie. Przykład: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1. Gdy numery wersji major, minor i patch są równe, wydanie przedpremierowe poprzedza wersję standardową. Przykładowo: 1.0.0-alpha < 1.0.0. Pierwszeństwo dwóch wydań przedpremierowych z takimi samymi numerami wersji major, minor i patch MUSI być ustalane przez porównywanie każdego z identyfikatorów rozdzielonych kropkami w kierunku od lewej do prawej, póki nie zostanie wykryta różnica w taki sposób: identyfikatory złożone z samych cyfr porównywane są numerycznie, a identyfikatory z literami lub dywizami porównywane są leksykalnie w kolejności ASCII. Identyfikatory numeryczne zawsze poprzedzają identyfikatory nienumeryczne. Większy zbiór przedpremierowych pól poprzedza mniejszy zbiór, o ile wszystkie poprzedzające identyfikatory są sobie równe. Przykład: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.


Kompatybilność wsteczna
-----------------------
Nie musi być utrzymywana.

1.2. Serwisowanie systemu
=========================

Procedura zgłoszenia i obsługi błędu 
------------------------------------
Błąd zgłoszony zostaje poprzez wiadomość email do administratora systemu --> Administrator przekazuję informację o błędzie do odpowiedniego działu IT --> Programiści znajdują i usuwają przyczynę występowania błędu i wysyłają kod do Testera --> Tester akceptuje kod lub odsyła go do poprawy z informacją zwrotną co nie działa --> Działący kod zostaje przesłany do odpowiedniego brancha i następnie uruchomiony na serwerze.

Procedura aktualizacji systemu po usunięciu błędu
-------------------------------------------------
Po usunięciu błędu i przetestowaniu kodu przez testera należy wysłać kod do odpowiedniego brancha. Następnie osoba odpowiedzialna za uruchomienie aplikacji z wykorzystaniem nowego kodu, uruchamia ją na serwerze.

1.3. Testy wydajnościowe
========================

Badania oraz monitorowanie wydajności
-------------------------------------

#. API - na czas odpowiedzi API wpływa ilość użytkowników w systemie oraz zasoby serwera klienta na którym została uruchomiona aplikacja SMS.
#. Interfejs użytkownika - Na wydajność aplikacji wpływa filtrowanie dużej bazy kampanii sprzedażowych. Okres wyszukiwania może być wydłużony nawet do 19 sekund( jest to akceptowalna wartość). 
#. Źródła danych - Najdłużej trwającym zapytaniem sql-owym jest zapytanie podczas filtrowania kampanii sprzedażowych i w zależności od ilości danych może trwać do 19 sekund