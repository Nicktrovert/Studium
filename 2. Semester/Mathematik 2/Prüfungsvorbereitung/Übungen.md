Ja. Tatsächlich würde ich **nicht einfach zufällige Aufgaben** erstellen, sondern eine **Aufgabensammlung**, die sich am Stil eurer Probeklausur orientiert. So trainierst du genau die Arten von Aufgaben, die mit hoher Wahrscheinlichkeit in der Klausur vorkommen.

Ich würde die Aufgaben in drei Schwierigkeitsstufen aufteilen:

- 🟢 **Leicht** – Grundlagen
    
- 🟡 **Mittel** – typisches Klausurniveau
    
- 🔴 **Schwer** – etwas anspruchsvoller als die Klausur
    

---

# Teil A – Kombinatorik

## A1 🟢

Wie viele vierstellige PINs gibt es?

a) Ziffern dürfen mehrfach vorkommen.

b) Alle Ziffern müssen verschieden sein.

---

## A2 🟢

Eine Flagge besteht aus 4 horizontalen Streifen.

Es stehen 7 Farben zur Verfügung.

Jede Farbe darf nur einmal verwendet werden.

Wie viele verschiedene Flaggen gibt es?

---

## A3 🟡

Ein Passwort besteht aus

- 3 Buchstaben
    
- danach 3 Ziffern.
    

Buchstaben dürfen mehrfach vorkommen.

Ziffern ebenfalls.

Wie viele Passwörter gibt es?

---

## A4 🟡

Aus 15 Studenten sollen

- Vorsitzender
    
- Stellvertreter
    
- Schriftführer
    

gewählt werden.

Wie viele Möglichkeiten gibt es?

---

## A5 🟡

Beim Lotto werden

6 Zahlen

aus 49 gezogen.

Wie viele Möglichkeiten existieren?

---

## A6 🔴

Wie viele sechsstellige Zahlen besitzen

- genau zwei Nullen
    
- erste Stelle darf keine Null sein?
    

---

# Teil B – Modulare Arithmetik

## B1 🟢

Berechne

[  
83\mod12  
]

---

## B2 🟢

Berechne

[  
(34+58)\mod9  
]

---

## B3 🟢

Berechne

[  
27\cdot19\mod8  
]

---

## B4 🟡

Bestimme

[  
ggT(91,35)  
]

mit dem Euklidischen Algorithmus.

---

## B5 🟡

Berechne

$7^{-1}\mod23$

ggT(23, 7)


| k   | r             | q            | x                | y                   |
| --- | ------------- | ------------ | ---------------- | ------------------- |
| 0   | $r_0=23$      | -            | $x_0=1$          | $y_0=0$             |
| 1   | $r_1=7$       | -            | $x_1=0$          | $y_1=1$             |
| 2   | $r_2=23\%7=2$ | $q_2=23/7=3$ | $x_2=1-3*0=1$    | $y_2=0-3*1=-3$      |
| 3   | $r_3=7\%2=1$  | $q_3=7/2=3$  | $x_3=0-3*1=-3$   | $y_3=1-3*(-3)=10$   |
| 4   | $r_4=2\%1=0$  | $q_4=2/1=2$  | $x_4=1-2*(-3)=7$ | $y_4=(-3)-2*10=-23$ |
|     |               |              |                  |                     |

$x=-3$
$y=10$

$23*(-3)+7*10=1$

$ggT(23, 7) = 1$


mit dem erweiterten Euklid.

---

## B6 🟡

Löse

$5x\equiv3\pmod{17}$



---

## B7 🟡

Berechne

[  
\varphi(35)  
]

---

## B8 🟡

Berechne

[  
2^{100}\mod7  
]

mit dem Satz von Euler.

---

## B9 🔴

Löse

[  
x\equiv2\pmod3  
]

[  
x\equiv1\pmod5  
]

[  
x\equiv4\pmod7  
]

---

## B10 🔴

RSA

Gegeben

[  
p=5,\quad q=11,\quad e=3  
]

Berechne

a)

den öffentlichen Schlüssel

b)

(\varphi(n))

c)

den privaten Schlüssel

d)

verschlüssele

m=8

---

# Teil C – Graphentheorie

## C1 🟢

Ein Graph besitzt

Knotengrade

```
2 2 4 2
```

Besitzt er

- einen Eulerweg?
    
- einen Eulerkreis?
    

Begründe.

---

## C2 🟢

Ein Graph besitzt

Knotengrade

```
1 2 2 3
```

Eulerweg?

Eulerkreis?

---

## C3 🟡

Erkläre den Unterschied zwischen

Eulerkreis

und

Hamiltonkreis.

---

## C4 🟡

Ein Baum besitzt

18 Knoten.

Wie viele Kanten besitzt er?

---

## C5 🟡

Welche Datenstruktur benutzt

DFS?

Welche benutzt

BFS?

---

## C6 🟡

Erkläre den Unterschied zwischen

Prim

und

Kruskal.

---

## C7 🔴

Gegeben ist folgende Adjazenzliste:

```
A : B C

B : A D E

C : A F

D : B

E : B F

F : C E
```

Bestimme das DFS-Gerüst

(Start A).

---

## C8 🔴

Ist folgender Graph bipartit?

```
A-B

| |

C-D

 \

  E
```

Begründe.

---

# Teil D – Analytische Geometrie

## D1 🟢

Berechne die Länge von

[  
\begin{pmatrix}  
6\  
8  
\end{pmatrix}  
]

---

## D2 🟢

Berechne

[  
\begin{pmatrix}  
2\  
3  
\end{pmatrix}  
\cdot  
\begin{pmatrix}  
5\  
-1  
\end{pmatrix}  
]

---

## D3 🟡

Berechne den Winkel zwischen

[  
\begin{pmatrix}  
1\  
0  
\end{pmatrix}  
]

und

[  
\begin{pmatrix}  
1\  
1  
\end{pmatrix}  
]

---

## D4 🟡

Liegt

P(5|1)

auf

[  
\vec x=  
\begin{pmatrix}  
1\  
3  
\end{pmatrix}  
+t  
\begin{pmatrix}  
2\  
-1  
\end{pmatrix}  
]

?

---

## D5 🔴

Berechne den Abstand zwischen

P(2|5)

und der Geraden

[  
\vec x=  
\begin{pmatrix}  
1\  
1  
\end{pmatrix}  
+t  
\begin{pmatrix}  
2\  
1  
\end{pmatrix}  
]

---

# Bonus – Klausursimulation (80 Punkte)

Nachdem du diese Aufgaben gelöst hast, würde ich dir empfehlen, eine komplette **Prognoseklausur mit etwa 80 Punkten** zu bearbeiten – im gleichen Stil und mit ähnlicher Schwierigkeit wie eure echte Prüfung. Auf Basis der Wiederholungsunterlagen, der Probeklausur und der Informationen aus der Fragestunde kann ich eine solche Klausur sehr realistisch nachbilden. Das wäre aus meiner Sicht die beste Generalprobe direkt vor der Prüfung.