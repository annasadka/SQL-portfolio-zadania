

# 📋 Przegląd projektu
Jest to mój plan nauki SQL, zawierający serię skryptów demonstrujących różne umiejętności - od podstaw do zaawansowanych technik. Skrypty są ponumerowane w kolejności rosnącej złożoności.# 💾 SQL Portfolio - Plan zadań

## ✅ Cele projektu

- [ ] Zrozumienie podstaw baz danych relacyjnych
- [ ] Opanowanie podstawowych operacji SQL
- [ ] Umiejętność tworzenia złożonych zapytań
- [ ] Posługiwanie się zaawansowanymi funkcjami SQL Server
- [ ] Stworzenie portfolio pokazującego umiejętności SQL

## 📚 Materiały źródłowe

- [Microsoft SQL Server Documentation](https://docs.microsoft.com/en-us/sql/)
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [SQL Server Tutorial](https://www.sqlservertutorial.net/)

---
<br>

# 🔍 Skrypty i ich zawartość

## 📝 script01.sql: Tworzenie bazy danych i struktur tabel
> *Podstawy tworzenia i definiowania struktur danych*

- Utworzenie bazy danych `sklep_internetowy`
- Utworzenie tabel:
  - `klienci` (id, imie, nazwisko, email, data_rejestracji, wiek)
  - `kategorie` (id, nazwa, opis)
- Definiowanie ograniczeń i relacji

<br>

<br>

## 📝 script02.sql: Operacje CRUD na danych
> *Podstawowe operacje na danych w bazie*

- [x] Wstawianie danych do tabeli `klienci`
- [x] Aktualizacja danych klienta
- [x] Usuwanie wybranego klienta
- [x] Wyświetlenie wszystkich klientów


<br>

<br>

## 📝 script03.sql: Modyfikacje struktury tabel
> *Zarządzanie strukturą istniejących tabel*

- Dodanie nowej kolumny `telefon` do tabeli `klienci`
- Zmiana typu danych kolumny
- Usunięcie kolumny
- Dodanie kolumny z domyślną wartością
 
<br>

<br>

## 📝 script04.sql: Podstawowe zapytania SELECT z warunkami
> *Filtrowanie danych przy użyciu podstawowych operatorów*

| Operator | Opis | Przykład |
|----------|------|----------|
| `=` | Równość | `WHERE wiek = 25` |
| `>` | Większe niż | `WHERE wiek > 30` |
| `<` | Mniejsze niż | `WHERE wiek < 20` |
| `!=` | Nierówność | `WHERE wiek != 25` |

- Wyświetlanie klientów, którzy mają wiek poniżej 30 lat
- Wyświetlanie klientów, którzy zarejestrowali się po określonej dacie
- Aktualizacja wieku klientów
- Wyświetlanie klientów, których wiek jest różny od 25

<br>

<br>

## 📝 script05.sql: Zaawansowane warunki filtrowania
> *Zaawansowane techniki filtrowania danych*

- Użycie operatora BETWEEN dla wieku
- Użycie operatora IN dla imion klientów
- Użycie operatora LIKE do wyszukiwania wzorców w nazwiskach 
- Użycie operatorów IS NULL i IS NOT NULL


<br>

<br>

## 📝 script06.sql: Operatory logiczne
> *Łączenie warunków przy użyciu operatorów logicznych*

- Użycie AND do filtrowania wyników
- Użycie OR do łączenia warunków
- Użycie NOT dla negacji warunków

<br>

<br>

## 📝 script07.sql: Sortowanie wyników
> *Organizowanie wyników zapytań*

- Sortowanie klientów według wieku rosnąco (ASC)
- Sortowanie klientów według daty rejestracji malejąco (DESC)
- Sortowanie z wieloma kolumnami
- Filtrowanie i sortowanie w jednym zapytaniu

<br>

<br>

## 📝 script08.sql: Nowa tabela i relacje
> *Tworzenie powiązanych struktur danych*

- Tworzenie tabeli `produkty` (id, nazwa, cena, id_kategorii, dostepna_ilosc)
- Dodawanie produktów
- Aktualizacja produktów
- Wyświetlanie produktów z różnymi warunkami filtrowania

<br>

<br>

## 📝 script09.sql: Funkcje agregujące i grupowanie
> *Analizowanie i podsumowywanie danych*

Funkcje agregujące:
- 🔢 COUNT - liczenie rekordów
- 📊 AVG - średnia wartość
- 📈 MAX - wartość maksymalna
- 📉 MIN - wartość minimalna
- 💰 SUM - suma wartości

Przykłady:
- Liczenie klientów (COUNT)
- Znajdowanie średniego wieku klientów (AVG)
- Znajdowanie najwyższej i najniższej ceny produktów (MAX, MIN)
- Sumowanie dostępnych ilości produktów (SUM)
- Grupowanie według kategorii (GROUP BY)
- Filtrowanie grup (HAVING)

<br>

<br>

## 📝 script10.sql: Funkcje tekstowe i matematyczne
> *Manipulowanie i formatowanie danych*

- Użycie funkcji CONCAT do łączenia imienia i nazwiska
- Użycie funkcji UPPER i LOWER do zmiany wielkości liter
- Użycie funkcji matematycznych (ROUND, ABS)
- Użycie funkcji do formatowania dat

<br>

<br>

## 📝 script11.sql: Podzapytania i widoki
> *Zaawansowane techniki zapytań i wirtualne tabele*

- Tworzenie podzapytań
- Tworzenie widoku dla najnowszych klientów
- Tworzenie widoku dla najdroższych produktów
- Wyświetlanie danych z widoków

<br>

<br>

## 📝 script12.sql: Wyrażenia regularne
> *Zaawansowane wzorce wyszukiwania*

- Wyszukiwanie klientów według wzorców w emailach
- Wyszukiwanie produktów według wzorców w nazwach

<br>

<br>

## 📝 script13.sql: Łączenie tabel (JOIN)
> *Relacyjne łączenie danych z różnych tabel*

- Tworzenie tabeli `zamowienia` (id, id_klienta, data_zamowienia)
- Tworzenie tabeli `zamowienia_szczegoly` (id, id_zamowienia, id_produktu, ilosc)
- Użycie LEFT JOIN
- Użycie RIGHT JOIN
- Użycie INNER JOIN

Wizualna reprezentacja typów JOIN:

<img src="https://i.stack.imgur.com/4zjxm.png" alt="JOIN Diagram" width="50%">

<br>

<br>

## 📝 script14.sql: Łączenie trzech tabel
> *Zaawansowane łączenie wielu tabel*

- Łączenie tabel `zamowienia`, `klienci` i `produkty`
- Wyświetlanie pełnych danych zamówienia

<br>
---
<br>

## 📝 script15.sql: Wyzwalacze (Triggers)
> *Automatyczne reakcje na zmiany w danych*

- Tworzenie triggerów do automatycznej aktualizacji stanu magazynowego
- Przykład: zmniejszanie stanu magazynowego po dodaniu nowego zamówienia

<br>
---
<br>

## 📝 script16.sql: Procedury składowane
> *Predefiniowane operacje bazodanowe*

- Tworzenie procedury do wyszukiwania klientów
- Tworzenie procedury do dodawania nowego zamówienia


<br>
---
<br>

## 📝 script17.sql: Praktyczne zadanie analityczne
> *Zaawansowana analiza danych sprzedażowych*

- Stworzenie pełnej analizy sprzedaży
- Znajdowanie najlepszych klientów
- Znajdowanie najpopularniejszych produktów

<br>
---
<br>

## 📝 script18.sql: Kompleksowe zadanie z procedurami i triggerami
> *Kompletny system zarządzania zamówieniami*

- Tworzenie systemu obsługi zamówień
- Zarządzanie stanem magazynowym
- Raportowanie sprzedaży

<br>
---
<br>




