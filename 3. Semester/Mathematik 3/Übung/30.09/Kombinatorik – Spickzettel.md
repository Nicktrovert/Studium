## 1. Grundfragen bei jeder Aufgabe

1. **Wie viele Elemente gibt es insgesamt?** → (n)
    
2. **Wie viele werden gewählt?** → (k)
    
3. **Ist die Reihenfolge wichtig?**
    
4. **Darf etwas mehrfach vorkommen?**
    
5. Gibt es **Zusatzbedingungen**?
    

---

## 2. Grundformeln

|                         | Ohne Wiederholung                 | Mit Wiederholung                 |
| ----------------------- | --------------------------------- | -------------------------------- |
| **Reihenfolge wichtig** | $\displaystyle \frac{n!}{(n-k)!}$ | $\displaystyle n^k$              |
| **Reihenfolge egal**    | $\displaystyle \binom nk$         | $\displaystyle \binom{n+k-1}{k}$ |

### Alle (n) Elemente anordnen

$$  
\boxed{n!}  
$$

### Binomialkoeffizient

$$
\boxed{\binom nk=\frac{n!}{k!(n-k)!}}  
$$

---

## 3. Gleiche Elemente bei einer Permutation

Wenn Elemente mehrfach identisch vorkommen:

$$
\boxed{\frac{n!}{n_1!n_2!\cdots n_r!}}  
$$

Beispiel: (2,4,4,8,8)

$$
\frac{5!}{2!2!}  
$$

Die Division entfernt Mehrfachzählungen durch identische Elemente.

---

## 4. Produkt- und Summenregel

### UND → multiplizieren

Wenn mehrere Bedingungen gleichzeitig erfüllt werden müssen:

$$
A\text{ UND }B  
\quad\Rightarrow\quad  
A\cdot B  
$$

Beispiel:

2 Männer **und** 4 Frauen:

$$
\binom82\binom64  
$$

### ODER → addieren

Wenn verschiedene, getrennte Fälle möglich sind:

$$
A\text{ ODER }B  
\quad\Rightarrow\quad  
A+B  
$$

Beispiel:

genau 3 **oder** genau 4 Richtige:

$$
(\text{Fall 3})+(\text{Fall 4})  
$$

---

## 5. „Genau“, „mindestens“, „höchstens“

### Genau (k)

Nur diesen Fall zählen.

### Mindestens (k)

$$  
k,;k+1,;k+2,\ldots  
$$

alle möglichen Fälle addieren.

### Höchstens (k)

$$
0,;1,\ldots,k  
$$

alle möglichen Fälle addieren.

Oft ist einfacher:

$$
\boxed{\text{alle Möglichkeiten}-\text{verbotene Möglichkeiten}}  
$$

---

## 6. Auswahl aus verschiedenen Gruppen

Wenn aus Gruppe A und Gruppe B bestimmte Anzahlen benötigt werden:

$$
\boxed{  
\binom{n_A}{k_A}\binom{n_B}{k_B}  
}  
$$

Beispiel:

3 Gewinnlose aus 6 passenden Zahlen und 3 aus 43 anderen:

$$
\binom63\binom{43}{3}  
$$

Merke:

$$
\boxed{\text{Auswahl aus A UND Auswahl aus B}}  
$$

→ multiplizieren.

---

## 7. Spezialbedingungen

### Eine bestimmte Person MUSS dabei sein

Person fest setzen und nur noch die restlichen Plätze wählen.

Beispiel:

5 Personen aus 15, Anna muss dabei sein:

$$
\binom{14}{4}  
$$

---

### Zwei Personen dürfen NICHT gemeinsam dabei sein

Oft:

$$
\boxed{\text{alle Gruppen}-\text{Gruppen mit beiden Personen}}  
$$

---

### Genau ein bestimmtes Element

1. Position des Elements wählen.
    
2. Restliche Positionen mit anderen Elementen füllen.
    

Beispiel: genau ein B auf 2 Buchstabenpositionen:

$$
2\cdot25  
$$

---

## 8. Gegenereignis

Bei Bedingungen wie

- mindestens einmal
    
- nicht gemeinsam
    
- keine ...
    
- höchstens ...
    

kann das Gegenereignis leichter sein:

$$
\boxed{\text{gesucht}=\text{alle}-\text{unerwünscht}}  
$$

Wichtig: Wenn **zwei Bedingungen gleichzeitig erfüllt** sein müssen, die Bedingungen ggf. getrennt behandeln.

Beispiel:

mindestens A/B/C bei Buchstaben **UND** mindestens 4/6 bei Ziffern:

$(\text{alle Buchstabenfolgen}-\text{ohne A/B/C})\cdot(\text{alle Ziffernfolgen}-\text{ohne 4/6})$ 

---

## 9. Blockmethode – Personen müssen nebeneinander sitzen

Personen, die zusammen sitzen müssen, zunächst als **einen Block** behandeln.

1. Blöcke und einzelne Personen anordnen.
    
2. Personen innerhalb jedes Blocks anordnen.
    

Beispielstruktur:

$$  
\boxed{\text{äußere Anordnung}}  
\cdot  
\boxed{\text{interne Anordnung Block 1}}  
\cdot  
\boxed{\text{interne Anordnung Block 2}}  
$$

---

## 10. Stellenweise zählen

Bei Codes, Zahlen, Passwörtern usw. oft am einfachsten:

$$
\boxed{?}\boxed{?}\boxed{?}\boxed{?}  
$$

Für jede Position Möglichkeiten bestimmen und multiplizieren.

Beispiel ohne Wiederholung:

$$
10\cdot9\cdot8\cdot7  
$$

Mit Wiederholung:

$$
10^4  
$$

Sonderbedingungen direkt an der entsprechenden Position berücksichtigen.

Beispiel: erste Ziffer darf keine 0 sein:

$$
9\cdot9\cdot8\cdot7  
$$

---

## 11. Lotto-/Treffer-Aufgaben

Wenn du (n) eigene Zahlen und (N-n) fremde Zahlen hast:

### Genau (r) Richtige

$$
\boxed{  
\binom nr  
\binom{N-n}{k-r}  
}  
$$

Beim Lotto 6 aus 49:

$$
\boxed{  
\binom6r\binom{43}{6-r}  
}  
$$

„Mindestens“, „höchstens“ usw. → entsprechende Werte von (r) addieren.

---

## 12. Mehrere besondere Teilgruppen

Beispiel:

4 Männer sollen gewählt werden.  
Davon gibt es 4 „besondere“ und 4 andere.  
Maximal 2 besondere dürfen gewählt werden.

Erlaubte Fälle einzeln:

$$
\binom40\binom44  
+  
\binom41\binom43  
+  
\binom42\binom42  
$$

Allgemeines Muster:

$$
\boxed{  
\sum_r  
\binom{\text{besondere}}r  
\binom{\text{andere}}{k-r}  
}  
$$

Alternativ:

$$
\text{alle}-\text{verbotene Fälle}  
$$

---

# Entscheidungsbaum

### Werden alle Elemente angeordnet?

**Ja:**

$n!$

Bei identischen Elementen:

$$\frac{n!}{n_1!n_2!\cdots}$$

**Nein → weiter:**

### Reihenfolge wichtig?

**Ja**

- Wiederholung erlaubt → $n^k$
    
- Keine Wiederholung → $\frac{n!}{(n-k)!}$
    

**Nein**

- Wiederholung erlaubt → $\binom{n+k-1}{k}$
    
- Keine Wiederholung → $\binom nk$
    

---

# Wörter, bei denen genauer hinschauen

**„mindestens“**  
→ mehrere Fälle oder Gegenereignis

**„höchstens“**  
→ mehrere Fälle oder Gegenereignis

**„genau“**  
→ nur dieser Fall

**„gemeinsam / zusammen“**  
→ eventuell Blockbildung

**„nicht gemeinsam“**  
→ Ausschlussbedingung / Gegenereignis

**„muss enthalten sein“**  
→ Element fest setzen

**„ohne Zurücklegen / darf nicht mehrfach“**  
→ keine Wiederholung

**„darf mehrfach“**  
→ Wiederholung

**„oder“**  
→ meist addieren

**„und“**  
→ meist multiplizieren

---

# Plausibilitätschecks

Eine gesuchte Teilmenge kann nie größer sein als alle Möglichkeiten:

$$
\boxed{\text{günstige Möglichkeiten}\leq\text{alle Möglichkeiten}}  
$$

Bei Auswahl ohne Reihenfolge:

> Werden dieselben Personen/Elemente nur in anderer Reihenfolge erneut gezählt?

Falls ja → Mehrfachzählung vorhanden.

Bei komplizierten Aufgaben:

> Nicht sofort Formel suchen. Erst die Bedingung in Worte zerlegen.