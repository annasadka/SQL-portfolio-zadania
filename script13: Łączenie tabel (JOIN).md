## 📝 script13.sql: Łączenie tabel (JOIN)

> *Relacyjne łączenie danych z różnych tabel*

1. Tworzenie tabeli zamowienia (id, id_klienta, data_zamowienia)
2. Tworzenie tabeli zamowienia_szczegoly (id, id_zamowienia, id_produktu, ilosc)
3. Użycie LEFT JOIN
4. Użycie RIGHT JOIN
5. Użycie INNER JOIN
6. Wizualna reprezentacja typów JOIN:
JOIN Diagram
<br>

``` sql
-- Tworzenie tabeli zamowienia
CREATE TABLE zamowienia (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_klienta INT NOT NULL,
    data_zamowienia DATETIME DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(50) DEFAULT 'Nowe',
    FOREIGN KEY (id_klienta) REFERENCES klienci(id)
);

-- Tworzenie tabeli zamowienia_szczegoly
CREATE TABLE zamowienia_szczegoly (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_zamowienia INT NOT NULL,
    id_produktu INT NOT NULL,
    ilosc INT NOT NULL CHECK (ilosc > 0),
    cena_jednostkowa DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (id_zamowienia) REFERENCES zamowienia(id),
    FOREIGN KEY (id_produktu) REFERENCES produkty(id)
);

-- Dodawanie przykładowych zamówień
INSERT INTO zamowienia (id_klienta, status)
VALUES (1, 'Zrealizowane'),
       (2, 'W realizacji'),
       (4, 'Nowe'),
       (5, 'Zrealizowane');

-- Dodawanie szczegółów zamówień
INSERT INTO zamowienia_szczegoly (id_zamowienia, id_produktu, ilosc, cena_jednostkowa)
VALUES (1, 1, 1, 1499.99),
       (1, 3, 2, 89.99),
       (2, 2, 1, 3999.99),
       (3, 5, 1, 59.99),
       (3, 7, 1, 119.99),
       (4, 4, 3, 149.99);

-- Użycie INNER JOIN
SELECT z.id AS zamowienie_id, z.data_zamowienia, k.imie, k.nazwisko
FROM zamowienia z
INNER JOIN klienci k ON z.id_klienta = k.id;

-- Użycie LEFT JOIN
SELECT k.id, k.imie, k.nazwisko, COUNT(z.id) AS liczba_zamowien
FROM klienci k
LEFT JOIN zamowienia z ON k.id = z.id_klienta
GROUP BY k.id, k.imie, k.nazwisko;

-- Użycie RIGHT JOIN
SELECT p.nazwa, zs.ilosc, zs.cena_jednostkowa, z.data_zamowienia
FROM zamowienia_szczegoly zs
RIGHT JOIN produkty p ON zs.id_produktu = p.id
LEFT JOIN zamowienia z ON zs.id_zamowienia = z.id
ORDER BY p.nazwa;
```
