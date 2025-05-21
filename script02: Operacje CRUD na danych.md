## 📝 script02.sql: Operacje CRUD na danych
Podstawowe operacje na danych w bazie

 1. Wstawianie danych do tabeli klienci
 2. Aktualizacja danych klienta
 3. Usuwanie wybranego klienta
 4. Wyświetlenie wszystkich klientów

```sql

-- Wstawianie danych do tabeli klienci
INSERT INTO klienci (imie, nazwisko, email, data_rejestracji, wiek)
VALUES ('Jan', 'Kowalski', 'jan.kowalski@example.com', '2023-01-15', 35),
       ('Anna', 'Nowak', 'anna.nowak@example.com', '2023-02-20', 28),
       ('Piotr', 'Wiśniewski', 'piotr.wisniewski@example.com', '2023-03-10', 42),
       ('Katarzyna', 'Dąbrowska', 'katarzyna.dabrowska@example.com', '2023-04-05', 31),
       ('Michał', 'Lewandowski', 'michal.lewandowski@example.com', '2023-05-12', 25);

-- Aktualizacja danych klienta
UPDATE klienci
SET email = 'jan.kowalski.nowy@example.com', wiek = 36
WHERE id = 1;

-- Usuwanie wybranego klienta
DELETE FROM klienci
WHERE id = 3;

-- Wyświetlenie wszystkich klientów
SELECT * FROM klienci;
```
