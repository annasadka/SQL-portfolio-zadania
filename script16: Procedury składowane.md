``` sql
-- Tworzenie procedury do wyszukiwania klientów
DELIMITER //
CREATE PROCEDURE znajdz_klientow(
    IN p_nazwisko VARCHAR(50),
    IN p_min_wiek INT
)
BEGIN
    SELECT * FROM klienci
    WHERE (p_nazwisko IS NULL OR nazwisko LIKE CONCAT('%', p_nazwisko, '%'))
    AND (p_min_wiek IS NULL OR wiek >= p_min_wiek)
    ORDER BY nazwisko, imie;
END //
DELIMITER ;

-- Tworzenie procedury do dodawania nowego zamówienia
DELIMITER //
CREATE PROCEDURE dodaj_zamowienie(
    IN p_id_klienta INT,
    IN p_id_produktu INT,
    IN p_ilosc INT,
    OUT p_id_zamowienia INT
)
BEGIN
    DECLARE v_cena DECIMAL(10, 2);
    DECLARE v_dostepna_ilosc INT;
    
    -- Pobranie ceny i dostępnej ilości
    SELECT cena, dostepna_ilosc INTO v_cena, v_dostepna_ilosc
    FROM produkty WHERE id = p_id_produktu;
    
    -- Sprawdzenie dostępności
    IF v_dostepna_ilosc < p_ilosc THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Niewystarczająca ilość produktu w magazynie';
    END IF;
    
    -- Rozpoczęcie transakcji
    START TRANSACTION;
    
    -- Utworzenie zamówienia
    INSERT INTO zamowienia (id_klienta, status)
    VALUES (p_id_klienta, 'Nowe');
    
    -- Pobranie ID nowego zamówienia
    SET p_id_zamowienia = LAST_INSERT_ID();
    
    -- Dodanie szczegółów zamówienia
    INSERT INTO zamowienia_szczegoly (id_zamowienia, id_produktu, ilosc, cena_jednostkowa)
    VALUES (p_id_zamowienia, p_id_produktu, p_ilosc, v_cena);
    
    -- Stan magazynowy jest aktualizowany przez trigger
    
    -- Zatwierdzenie transakcji
    COMMIT;
END //
DELIMITER ;

-- Przykłady wywołania procedur
CALL znajdz_klientow('now', 25);
CALL znajdz_klientow(NULL, 30);

SET @id_nowego_zamowienia = 0;
CALL dodaj_zamowienie(2, 4, 2, @id_nowego_zamowienia);
SELECT @id_nowego_zamowienia AS nowe_zamowienie_id;
```
