## 📝 script18.sql: Kompleksowe zadanie z procedurami i triggerami

> *Kompletny system zarządzania zamówieniami*
1. Tworzenie systemu obsługi zamówień
2. Zarządzanie stanem magazynowym
3. Raportowanie sprzedaży
<br>

``` sql
-- Tworzenie systemu obsługi zamówień

-- 1. Rozbudowa tabeli zamówień
ALTER TABLE zamowienia
ADD COLUMN adres_dostawy TEXT,
ADD COLUMN metoda_platnosci VARCHAR(50),
ADD COLUMN data_platnosci DATETIME,
ADD COLUMN koszt_dostawy DECIMAL(10, 2) DEFAULT 0;

-- 2. Tabela statusów zamówień dla lepszego śledzenia
CREATE TABLE statusy_zamowien (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nazwa VARCHAR(50) NOT NULL UNIQUE
);

INSERT INTO statusy_zamowien (nazwa) 
VALUES ('Nowe'), ('Potwierdzone'), ('W realizacji'), ('Wysłane'), ('Dostarczone'), ('Anulowane');

ALTER TABLE zamowienia
MODIFY COLUMN status VARCHAR(50) DEFAULT 'Nowe',
ADD CONSTRAINT fk_status FOREIGN KEY (status) REFERENCES statusy_zamowien(nazwa);

-- 3. Procedura składowana do tworzenia pełnego zamówienia
DELIMITER //
CREATE PROCEDURE utworz_pelne_zamowienie(
    IN p_id_klienta INT,
    IN p_adres_dostawy TEXT,
    IN p_metoda_platnosci VARCHAR(50),
    OUT p_id_zamowienia INT
)
BEGIN
    -- Tworzymy zamówienie
    INSERT INTO zamowienia (id_klienta, status, adres_dostawy, metoda_platnosci)
    VALUES (p_id_klienta, 'Nowe', p_adres_dostawy, p_metoda_platnosci);
    
    SET p_id_zamowienia = LAST_INSERT_ID();
END //
DELIMITER ;

-- 4. Procedura dodawania produktu do zamówienia
DELIMITER //
CREATE PROCEDURE dodaj_produkt_do_zamowienia(
    IN p_id_zamowienia INT,
    IN p_id_produktu INT,
    IN p_ilosc INT
)
BEGIN
    DECLARE v_cena DECIMAL(10, 2);
    DECLARE v_dostepna_ilosc INT;
    
    -- Sprawdzenie istnienia zamówienia
    IF NOT EXISTS (SELECT 1 FROM zamowienia WHERE id = p_id_zamowienia) THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Zamówienie o podanym ID nie istnieje';
    END IF;
    
    -- Sprawdzenie czy zamówienie nie jest już zrealizowane
    IF EXISTS (SELECT 1 FROM zamowienia WHERE id = p_id_zamowienia AND status IN ('Wysłane', 'Dostarczone')) THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Nie można modyfikować zamówienia w tym statusie';
    END IF;
    
    -- Pobranie ceny i dostępnej ilości
    SELECT cena, dostepna_ilosc INTO v_cena, v_dostepna_ilosc
    FROM produkty WHERE id = p_id_produktu;
    
    -- Sprawdzenie dostępności
    IF v_dostepna_ilosc < p_ilosc THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Niewystarczająca ilość produktu w magazynie';
    END IF;
    
    -- Dodanie produktu do zamówienia
    INSERT INTO zamowienia_szczegoly (id_zamowienia, id_produktu, ilosc, cena_jednostkowa)
    VALUES (p_id_zamowienia, p_id_produktu, p_ilosc, v_cena);
    
    -- Stan magazynowy aktualizowany przez trigger
END //
DELIMITER ;

-- 5. Procedura aktualizacji statusu zamówienia
DELIMITER //
CREATE PROCEDURE aktualizuj_status_zamowienia(
    IN p_id_zamowienia INT,
    IN p_nowy_status VARCHAR(50)
)
BEGIN
    -- Sprawdzenie istnienia zamówienia
    IF NOT EXISTS (SELECT 1 FROM zamowienia WHERE id = p_id_zamowienia) THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Zamówienie o podanym ID nie istnieje';
    END IF;
    
    -- Sprawdzenie istnienia statusu
    IF NOT EXISTS (SELECT 1 FROM statusy_zamowien WHERE nazwa = p_nowy_status) THEN
        SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Podany status nie istnieje';
    END IF;
    
    -- Aktualizacja statusu
    UPDATE zamowienia
    SET status = p_nowy_status
    WHERE id = p_id_zamowienia;

```
