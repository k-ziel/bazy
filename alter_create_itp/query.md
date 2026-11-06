**Zadanie 1**

**Napisz polecenie, ktore utworzy bazę danych o nazwie Szkola\_DB, a następnie ustaw ją jako aktywną.**



CREATE DATABASE if not EXISTS Szkola\_DB; # *(tego if not nie trzeba ale można)*

USE Szkola\_DB; # *(to aby uzyc danej bazy)*





#### 2\. TWORZENIE TABEL (CREATE) ORAZ KLUCZY GŁÓWNYCH I OBCYCH







**Zadanie 2**

**Utworz tabelę 'Klasy' z kolumnami id\_klasy (klucz główny) oraz nazwa\_klasy (tekst o zmiennej długości do 5 znaków).**



CREATE TABLE Klasy (id\_klasy int PRIMARY KEY, nazwa\_klasy varchar(5))



**Zadanie 3**

**Utworz tabelę 'Nauczyciele' zawierającą id\_nauczyciela (liczba całkowita, klucz główny, automatyczna inkrementacja), imie oraz nazwisko.**



CREATE TABLE Nauczyciele (id\_nauczyciela int PRIMARY KEY AUTO\_INCREMENT, imie varchar(25) not null COMMENT "Imie nauczyciela", nazwisko varchar(30) not null COMMENT "Nazwisko nauczyciela", INDEX(nazwisko));



**Zadanie 4**

**Utworz tabelę 'Uczniowie' zawierającą: id\_ucznia (klucz główny, AI),imie (wymagane), nazwisko (wymagane), data\_urodzenia oraz id\_klasy jako klucz obcy powiązany z tabelą Klasy.**



CREATE TABLE uczniowie (id\_ucznia int PRIMARY KEY AUTO\_INCREMENT, imie varchar(20) not null, nazwisko varchar(30) not null, data\_urodzenia date, id\_klasy int, FOREIGN KEY(id\_klasy) REFERENCES klasy(id\_klasy))



**Zadanie 5**

**Utworz tabelę 'Przedmioty' z kolumną id\_przedmiotu (klucz główny), unikalną nazwą przedmiotu oraz kluczem obcym id\_nauczyciela\_prowadzacego zdefiniowanym w osobnej linii na dole polecenia.**



CREATE TABLE przedmioty (id\_przedmiotu int PRIMARY KEY, nazwa\_przedmiotu varchar(30) UNIQUE, id\_nauczyciela\_prowadzacego int, FOREIGN KEY(id\_nauczyciela\_prowadzacego) REFERENCES nauczyciele (id\_nauczyciela));



**Zadanie 6**

**Utworz tabelę 'Kursy' z kolumnami: kod\_kursu (klucz główny),nazwa (pole unikalne - UNIQUE) oraz cena (liczba z wartością domyślną 0.00).**



CREATE TABLE kursy (kod\_kursy int PRIMARY KEY, nazwa varchar(60) UNIQUE, cena decimal(6,2) DEFAULT 0.00)



**Zadanie 7**

**Utwórz tabelę 'Oceny' reprezentującą relację wiele-do-wielu. Zdefiniuj w niej ZŁOŻONY KLUCZ GŁOWNY (Composite Key) składający się z id\_ucznia i id\_przedmiotu.**



CREATE TABLE oceny (

&#x20;   id\_ucznia INT,

&#x20;   id\_przedmiotu INT,

&#x20;   ocena INT NOT NULL,

&#x20;   data\_wystawienia DATE,

&#x20;   PRIMARY KEY (id\_ucznia, id\_przedmiotu),

&#x20;   FOREIGN KEY (id\_ucznia) REFERENCES uczniowie(id\_ucznia),

&#x20;   FOREIGN KEY (id\_przedmiotu) REFERENCES przedmioty(id\_przedmiotu)

);

**Zadanie 8**

**Utwórz tabelę 'Profile\_Uczniow' (relacja 1:1 z tabelą Uczniowie). Zdefiniuj klucz obcy z regułą kaskadowego usuwania (ON DELETE CASCADE).**



CREATE TABLE profile\_uczniow(

&#x20;   id\_ucznia int PRIMARY KEY,

&#x09;adres\_www varchar(50),

&#x09;login varchar(40) not null,

&#x09;haslo varchar(40) not null,

&#x09;FOREIGN KEY (id\_ucznia) REFERENCES uczniowie(id\_ucznia) on DELETE CASCADE)



**Zadanie 9**

**Utwórz tabelę 'Szkoly' bez definiowania klucza głównego podczas CREATE**



CREATE TABLE szkoly (id\_szkoly int, nazwa varchar(50))

