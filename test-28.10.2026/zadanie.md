9. Podac liczbe studentów kierunku INFORMATYKA.

SELECT count(DISTINCT studenci.NR_STUD) as "Liczba studentów na INF" FROM studenci
INNER JOIN kierunki ON kierunki.NR_KIER = studenci.NR_KIER
WHERE kierunki.NAZWA_KIER = "INFORMATYKA";

10. Podac srednią ocen studenta KOWALSKIEGO.

SELECT avg(oceny.OCENA) FROM oceny
INNER JOIN studenci ON oceny.NR_STUD = studenci.NR_STUD
WHERE studenci.NAZWISKO = "KOWALSKI";

11. Podac srednią ocen dla studentów kierunku ELEKTRONIKA MED.

SELECT avg(oceny.OCENA) FROM studenci
INNER JOIN oceny ON oceny.NR_STUD = studenci.NR_STUD
INNER JOIN kierunki ON kierunki.NR_KIER = studenci.NR_KIER
WHERE kierunki.NAZWA_KIER = "ELEKTRONIKA MED"

12. Podac najnizszą i najwyzszą ocene uzyskaną przez poszczególnych studentów.

SELECT studenci.NAZWISKO, min(oceny.OCENA) as "min. ocena", max(oceny.OCENA) as "max. ocena" FROM studenci
INNER JOIN oceny ON oceny.NR_STUD = studenci.NR_STUD
GROUP BY studenci.NR_STUD;

13. Dla kazdego studenta podac srednią ocen.

SELECT avg(oceny.OCENA), studenci.NAZWISKO FROM studenci
INNER JOIN oceny ON oceny.NR_STUD = studenci.NR_STUD
GROUP BY studenci.NR_STUD;

14. Podac daty urodzenia najstarszych studentów na poszczególnych kierunkach.

SELECT min(studenci.DATA_UR), kierunki.NAZWA_KIER FROM studenci
INNER JOIN kierunki ON kierunki.NR_KIER = studenci.NR_KIER
GROUP BY kierunki.NR_KIER;

15. Dla kazdego studenta podac liczbe ocen, które otrzymal z poszczególnych przedmiotów.

SELECT studenci.NAZWISKO, przedmioty.NAZWA_PRZEDM, COUNT(oceny.OCENA) FROM studenci
INNER JOIN oceny ON oceny.NR_STUD = studenci.NR_STUD
INNER JOIN przedmioty ON oceny.NR_PRZEDM = przedmioty.NR_PRZEDM
GROUP BY studenci.NAZWISKO, przedmioty.NAZWA_PRZEDM;


16. Podac nazwy przedmiotów, z których wystawiono wiecej niz 8 ocen.

SELECT przedmioty.NAZWA_PRZEDM FROM przedmioty
INNER JOIN oceny ON przedmioty.NR_PRZEDM = oceny.NR_PRZEDM
HAVING COUNT(DISTINCT oceny.ID_OCENY) > 8;

17. Dla kazdego przedmiotu podac liczbe studentów, którzy otrzymali z nich ocene. (Uwaga!
Niektórzy studenci mają kilka ocen z danego przedmiotu).

SELECT przedmioty.NAZWA_PRZEDM, COUNT(DISTINCT studenci.NR_STUD) FROM studenci
INNER JOIN oceny ON oceny.NR_STUD = studenci.NR_STUD
INNER JOIN przedmioty ON przedmioty.NR_PRZEDM = oceny.NR_PRZEDM
GROUP BY przedmioty.NR_PRZEDM;

18. Podac nazwiska studentów, którzy są starsi od studenta WILK. 

SELECT studenci.NAZWISKO FROM studenci
WHERE studenci.DATA_UR < (SELECT studenci.DATA_UR FROM studenci WHERE studenci.NAZWISKO = "WILK");
