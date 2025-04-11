## 📝 script01.sql: Tworzenie bazy danych i struktur tabel
   

1. Utworzenie bazy danych `sklep_internetowy`
2. Utworzenie tabel:
  - `klienci` (id, imie, nazwisko, email, data_rejestracji, wiek)
  - `kategorie` (id, nazwa, opis)
3. Definiowanie ograniczeń i relacji

```sql
CREATE DATABASE sklep_internetowy;

CREATE TABLE klienci (
  id IDENTITY (1,1) PRIMARY KEY,
  imię NVARCHAR(50) NOT NULL,
  nazwisko NVARCHAR(50) NOT NULL,
  email NVARCHAR (100) UNIQUE,
  data_rejestracji DATA NOT NULL
  wiek INT,
  );

CREATE TABLE kategorie (
  id IDENTITY(1,1) PRIMARY KEY,
  nazwa NVARCHAR(100) NOT NULL,
  opis NVARCHAR(MAX)
  );
```
