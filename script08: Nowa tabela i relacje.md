``` sql
-- Tworzenie tabeli produkty
CREATE TABLE produkty (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nazwa VARCHAR(100) NOT NULL,
    cena DECIMAL(10, 2) NOT NULL CHECK (cena > 0),
    id_kategorii INT,
    dostepna_ilosc INT DEFAULT 0 CHECK (dostepna_ilosc >= 0),
    FOREIGN KEY (id_kategorii) REFERENCES kategorie(id)
);

-- Dodawanie kategorii przed dodaniem produktów
INSERT INTO kategorie (nazwa, opis)
VALUES ('Elektronika', 'Urządzenia elektroniczne i akcesoria'),
       ('Odzież', 'Ubrania i dodatki'),
       ('Książki', 'Literatura różnych gatunków'),
       ('Sport', 'Akcesoria i sprzęt sportowy');

-- Dodawanie produktów
INSERT INTO produkty (nazwa, cena, id_kategorii, dostepna_ilosc)
VALUES ('Smartfon XYZ', 1499.99, 1, 50),
       ('Laptop ABC', 3999.99, 1, 30),
       ('Koszulka sportowa', 89.99, 2, 200),
       ('Spodnie jeansowe', 149.99, 2, 150),
       ('Python dla początkujących', 59.99, 3, 100),
       ('Historia sztuki', 129.99, 3, 25),
       ('Piłka do koszykówki', 119.99, 4, 75),
       ('Rower górski', 1999.99, 4, 15);

-- Aktualizacja produktów
UPDATE produkty
SET cena = 1599.99, dostepna_ilosc = 45
WHERE id = 1;

-- Wyświetlanie produktów z różnymi warunkami filtrowania
SELECT * FROM produkty
WHERE cena < 100;

SELECT * FROM produkty
WHERE id_kategorii = 1 AND dostepna_ilosc > 20;
```
