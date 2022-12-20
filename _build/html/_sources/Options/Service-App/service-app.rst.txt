Utrzymanie produktu
+++++++++++++++++++

Rozbudowa systemu
=================

Wersjowanie systemu
-------------------

Procedura podnoszenia wersji aplikacji
--------------------------------------

Kompatybilność wsteczna
-----------------------


Serwisowanie systemu
====================

Procedura zgłoszenia i obsługi błędu 
------------------------------------

Procedura aktualizacji systemu po usunięciu błędu
-------------------------------------------------

Testy wydajnościowe
===================

Badania oraz monitorowanie wydajności
-------------------------------------

1 źródła danych - zapytania sql-owe (czas trwania, najbardziej
czasochłonne, najczęstsze)
2 API - czas odpowiedzi i co na niego wpływa – np. obliczenia,
sieć, sql etc
3 rps/throughput - request per second
4 interfejsu użytkownika (czasochłonne operacje – np.
filtrowanie dużej tabeli, obliczenia, skomplikowana animacja
zależna od ilości obiektów na ekranie)


Określenie granic systemu (dla początkowej konfiguracji wdrożeniowej) –
minimalne wymagania aplikacji, maksymalna dopuszczalna ilość
użytkowników (bądź inne wskaźniki określające max dopuszczalne zasoby
– np. rps)