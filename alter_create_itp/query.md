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



**Zadanie 4**

**Utworz tabelę 'Uczniowie' zawierającą: id\_ucznia (klucz główny, AI),imie (wymagane), nazwisko (wymagane), data\_urodzenia oraz id\_klasy jako klucz obcy powiązany z tabelą Klasy.**



**Zadanie 5**

**Utworz tabelę 'Przedmioty' z kolumną id\_przedmiotu (klucz główny), unikalną nazwą przedmiotu oraz kluczem obcym id\_nauczyciela\_prowadzacego zdefiniowanym w osobnej linii na dole polecenia.**



Zadanie 6

Utworz tabelę 'Kursy' z kolumnami: kod\_kursu (klucz główny),nazwa (pole unikalne - UNIQUE) oraz cena (liczba z wartością domyślną 0.00).



Zadanie 7

Utwórz tabelę 'Oceny' reprezentującą relację wiele-do-wielu. Zdefiniuj w niej ZŁOŻONY KLUCZ GŁOWNY (Composite Key) składający się z id\_ucznia i id\_przedmiotu.



Zadanie 8

Utwórz tabelę 'Profile\_Uczniow' (relacja 1:1 z tabelą Uczniowie). Zdefiniuj klucz obcy z regułą kaskadowego usuwania (ON DELETE CASCADE).



Zadanie 9

Utwórz tabelę 'Szkoly' bez definiowania klucza głównego podczas CREATE

