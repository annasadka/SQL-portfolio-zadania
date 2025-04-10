# SQL-queries

## query1.sql: Tworzenie bazy danych i struktur tabel

Utwórz bazę danych sklep_internetowy
Utwórz tabele:

klienci (id, imie, nazwisko, email, data_rejestracji, wiek)
kategorie (id, nazwa, opis)



query2.sql: Operacje CRUD na danych

Wstawianie danych do tabeli klienci
Aktualizacja danych klienta
Usuwanie wybranego klienta
Wyświetlenie wszystkich klientów

query3.sql: Modyfikacje struktury tabel

Dodanie nowej kolumny telefon do tabeli klienci
Zmiana typu danych kolumny
Usunięcie kolumny
Dodanie kolumny z domyślną wartością

query4.sql: Podstawowe zapytania SELECT z warunkami

Wyświetlanie klientów, którzy mają wiek poniżej 30 lat
Wyświetlanie klientów, którzy zarejestrowali się po określonej dacie
Aktualizacja wieku klientów
Wyświetlanie klientów, których wiek jest różny od 25

query5.sql: Zaawansowane warunki filtrowania

Użycie operatora BETWEEN dla wieku
Użycie operatora IN dla imion klientów
Użycie operatora LIKE do wyszukiwania wzorców w nazwiskach
Użycie operatorów IS NULL i IS NOT NULL

query6.sql: Operatory logiczne

Użycie AND do filtrowania wyników
Użycie OR do łączenia warunków
Użycie NOT dla negacji warunków

query7.sql: Sortowanie wyników

Sortowanie klientów według wieku rosnąco (ASC)
Sortowanie klientów według daty rejestracji malejąco (DESC)
Sortowanie z wieloma kolumnami
Filtrowanie i sortowanie w jednym zapytaniu

query8.sql: Nowa tabela i relacje

Tworzenie tabeli produkty (id, nazwa, cena, id_kategorii, dostepna_ilosc)
Dodawanie produktów
Aktualizacja produktów
Wyświetlanie produktów z różnymi warunkami filtrowania

query9.sql: Funkcje agregujące i grupowanie

Liczenie klientów (COUNT)
Znajdowanie średniego wieku klientów (AVG)
Znajdowanie najwyższej i najniższej ceny produktów (MAX, MIN)
Sumowanie dostępnych ilości produktów (SUM)
Grupowanie według kategorii (GROUP BY)
Filtrowanie grup (HAVING)

query10.sql: Funkcje tekstowe i matematyczne

Użycie funkcji CONCAT do łączenia imienia i nazwiska
Użycie funkcji UPPER i LOWER do zmiany wielkości liter
Użycie funkcji matematycznych (ROUND, ABS)
Użycie funkcji do formatowania dat

query11.sql: Podzapytania i widoki

Tworzenie podzapytań
Tworzenie widoku dla najnowszych klientów
Tworzenie widoku dla najdroższych produktów
Wyświetlanie danych z widoków

query12.sql: Wyrażenia regularne

Wyszukiwanie klientów według wzorców w emailach
Wyszukiwanie produktów według wzorców w nazwach

query13.sql: Łączenie tabel (JOIN)

Tworzenie tabeli zamowienia (id, id_klienta, data_zamowienia)
Tworzenie tabeli zamowienia_szczegoly (id, id_zamowienia, id_produktu, ilosc)
Użycie LEFT JOIN
Użycie RIGHT JOIN
Użycie INNER JOIN

query14.sql: Łączenie trzech tabel

Łączenie tabel zamowienia, klienci i produkty
Wyświetlanie pełnych danych zamówienia

query15.sql: Wyzwalacze (Triggers)

Tworzenie triggerów do automatycznej aktualizacji stanu magazynowego

query16.sql: Procedury składowane

Tworzenie procedury do wyszukiwania klientów
Tworzenie procedury do dodawania nowego zamówienia

query17.sql: Praktyczne zadanie

Stworzenie pełnej analizy sprzedaży
Znajdowanie najlepszych klientów
Znajdowanie najpopularniejszych produktów

query18.sql: Kompleksowe zadanie z procedurami i triggerami

Tworzenie systemu obsługi zamówień
Zarządzanie stanem magazynowym
Raportowanie sprzedaży
