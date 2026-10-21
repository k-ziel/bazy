**ZESTAW 1: OCENA STUDENTOW I PRZEDMIOTY**

**Zadanie 1 : Wyświetl numery przedmiotów, które mają średnią ocenę wyższą niż 3.5. Wyniki posortuj malejąco według średniej.**


SELECT oceny.NR\\\_PRZEDM, avg(oceny.OCENA) as "srednia\\\_ocen" FROM oceny
GROUP BY oceny.NR\\\_PRZEDM
HAVING avg(oceny.OCENA) > 3.5
ORDER BY srednia\\\_ocen DESC;



**Zadanie 2 : Dla ocen z terminem 1 (WHERE TERMIN = 1), znajdź numery przedmiotów, na których wystawiono więcej niż 3 oceny, a ich średnia jest wyższa niż 3.0. Posortuj po**

**numerze przedmiotu.**





SELECT oceny.NR\_PRZEDM FROM oceny

WHERE oceny.TERMIN = 1

GROUP BY oceny.NR\_PRZEDM

HAVING AVG(oceny.OCENA) > 3 AND count(oceny.OCENA) > 3

ORDER BY oceny.NR\_PRZEDM



**Zadanie 3 : Wyświetl nazwy przedmiotów, które mają średnią ocen wyższą niż ogólna średnia wszystkich ocen w bazie danych, pod warunkiem, że na dany przedmiot przypada więcej**

**niż 2 studentów. Wynik posortuj według nazwy przedmiotu.**





SELECT przedmioty.NAZWA\_PRZEDM, AVG(oceny.OCENA), COUNT(DISTINCT oceny.NR\_STUD) FROM przedmioty

INNER JOIN oceny ON przedmioty.NR\_PRZEDM = oceny.NR\_PRZEDM

GROUP BY przedmioty.NR\_PRZEDM

HAVING avg(oceny.OCENA) > (SELECT avg(oceny.OCENA) FROM oceny) and COUNT(DISTINCT oceny.NR\_STUD) > 2

ORDER BY przedmioty.NAZWA\_PRZEDM;







**-------------------------------------------**







**Zadanie 1 : Znajdź numery pracowników, którzy otrzymali łącznie wypłaty na kwotę większą niż 5000. Wyniki posortuj malejąco według sumy.**



SELECT wyplaty.NR\_PRAC FROM wyplaty

GROUP BY wyplaty.NR\_PRAC

HAVING SUM(wyplaty.KWOTA) > 5000

ORDER BY SUM(wyplaty.KWOTA) DESC





**Zadanie 2 : Weź pod uwagę tylko wypłaty naliczone po 1985 roku. Wyświetl numery pracowników, którzy w tym okresie dostali więcej niż 2 wypłaty, a ich średnia pojedyncza wypłata**

**przekraczała 400. Posortuj po ID pracownika.**



SELECT wyplaty.NR\_PRAC FROM wyplaty

WHERE wyplaty.DATA\_NALICZ > "1985-12-31"

GROUP BY wyplaty.NR\_PRAC

HAVING COUNT(wyplaty.ID\_WYPL) > 2 AND AVG(wyplaty.KWOTA) > 400

ORDER BY wyplaty.NR\_PRAC;





**Zadanie 3 : Wyświetl nazwiska pracowników, których łączna suma wypłat jest wyższa niż średnia suma wypłat przypadająca na jednego pracownika w całej firmie. Posortuj**

**alfabetycznie.**



SELECT pracownicy.NAZWISKO, SUM(wyplaty.KWOTA) FROM pracownicy

INNER JOIN wyplaty ON wyplaty.NR\_PRAC = pracownicy.NR\_PRAC

GROUP BY pracownicy.NR\_PRAC

HAVING SUM(wyplaty.KWOTA) > (SELECT avg(wyplaty.KWOTA) FROM wyplaty)

ORDER BY pracownicy.NAZWISKO ASC





**-------------------------------------------**







**Zadanie 1**

**Podaj kody funkcji w przydziałach, ktore są przypisane do więcej niż 10 rożnych projektow (tematow). Posortuj od najczęstszej.**



SELECT przydzialy.KOD\_FUNKCJI, COUNT(DISTINCT przydzialy.NR\_TEM) FROM przydzialy

GROUP BY przydzialy.KOD\_FUNKCJI

HAVING COUNT(DISTINCT przydzialy.NR\_TEM) > 10

ORDER BY COUNT(DISTINCT przydzialy.NR\_TEM) DESC;





**Zadanie 2**

**Interesują nas tylko przydziały do tematów o numerach poniżej 100. Znajdź kody funkcji, które w tych tematach pojawiają się u więcej niż 5 różnych pracowników. Posortuj alfabetycznie według kodu funkcji.**



SELECT przydzialy.KOD\_FUNKCJI FROM przydzialy

WHERE przydzialy.NR\_TEM < 100

GROUP BY przydzialy.KOD\_FUNKCJI

HAVING COUNT(DISTINCT przydzialy.NR\_PRAC) > 5

ORDER BY przydzialy.KOD\_FUNKCJI ASC;



**Zadanie 3**

**Wyświetl pełne nazwy funkcji z tabeli funkcje, które zostały przydzielone w tematach kierowanych przez pracownika o nazwisku 'WILK' częściej niż 2 razy. Posortuj po nazwie funkcji.**



**SELECT f.NAZWA\_FUNKCJI**

**FROM funkcje f**

**JOIN przydzialy p ON f.KOD\_FUNKCJI = p.KOD\_FUNKCJI**

**JOIN tematy t ON p.NR\_TEM = t.NR\_TEM**

**JOIN pracownicy prac ON t.NR\_PRAC\_KT = prac.NR\_PRAC**

**WHERE prac.NAZWISKO = 'WILK'**

**GROUP BY f.KOD\_FUNKCJI, f.NAZWA\_FUNKCJI**

**HAVING COUNT(p.ID\_PRZYD) > 2**

**ORDER BY f.NAZWA\_FUNKCJI ASC;**



