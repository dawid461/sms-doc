5. Procedura uruchomienia aplikacji
+++++++++++++++++++++++++++++++++++

5.1. Środowisko dla dewelopera
==============================

Co jest potrzebne do uruchomienia aplikacji SMS?
------------------------------------------------

* Zainstalowanie wymaganych zmiennych środowiskowych z dokumentacji technicznej.
* SQL Server w najnowszej wersji.
* Dwa dowolne edytory kodu IDE z wbudowanym terminalem do obsługi warstwy aplikacji dla klienta i serwera (np. Visual Studio Code, Visual Studio 2022).

Uruchomienie aplikacji SMS
--------------------------

* Otwórz folder z projektami warstwy serwerowej w Visual Studio 2022 i wybierz jako projekt startowy SalesManagmentSoftware.API, następnie go uruchom. Po uruchomienie zostanie automatycznie utworzona nowa bazy danych jeśli jeszcze nie istnieje i następnie w przeglądarce otworzy się okienko z Swaggerem.
* W Visual Studio Code otwórz folder z projektem warstwy dla klienta. Następnie w terminalu wpisz polecenie ``npm i``, które zainstaluje wszystkie potrzebne biblioteki w projekcie. Po poprawnym zainstalowaniu bibliotek, aby uruchomić aplikację należy wpisać polecenie ``npm start``.

5.2. Proces budowy nowej wersji
===============================
Utworzenie nowego brancha --> Wysłanie gotowego brancha z nową wersją aplikacji do testów --> Odpowiedź testera z listą funkcjonalności do poprawy lub zaakceptowanie brancha --> Przekazanie brancha do wdrożenia w nowej wersji aplikacji    

5.3. Testy
==========
Testy jednostkowe oraz integracyjne uruchamiane są automatycznie przy commitowaniu zmiań na danym branchu.

5.4. Dokumentacja
=================
Dokumentacje należy tworzyć w narzędziu Read the Docs po wprowadzeniu nowej funkcjonalności do projektu lub zmian w już istniejących funkcjonalnościach. 
