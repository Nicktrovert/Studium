Ja. Tatsächlich lernt man Streams am schnellsten, wenn man einfach 20–30 kleine Aufgaben löst und die Stream-Pipeline selbst baut.

Wichtig ist dabei:

```java
list.stream()
    .filter(...)
    .map(...)
    .forEach(...)
```

als Grundmuster im Kopf zu verankern.

---

# Aufgabe 1 – Gerade Zahlen

Gegeben:

```java
ArrayList<Integer> list =
    new ArrayList<>(List.of(1,2,3,4,5,6,7,8,9,10));
```

Gib nur die geraden Zahlen aus.

Erwartete Ausgabe:

```text
2
4
6
8
10
```

---

# Aufgabe 2 – Quadrieren

Gegeben:

```java
1 2 3 4 5
```

Gib aus:

```text
1
4
9
16
25
```

Benutze `map()`.

---

# Aufgabe 3 – Namen filtern

Gegeben:

```java
ArrayList<String> names =
    new ArrayList<>(List.of(
        "Anna",
        "Bob",
        "Alexander",
        "Chris",
        "Tom"
    ));
```

Gib nur Namen mit mindestens 5 Zeichen aus.

---

# Aufgabe 4 – Großbuchstaben

Gegeben:

```java
Anna
Bob
Chris
```

Ausgabe:

```text
ANNA
BOB
CHRIS
```

Tipp:

```java
String.toUpperCase()
```

---

# Aufgabe 5 – Kombination

Gegeben:

```java
Anna
Bob
Alexander
Chris
Tom
```

1. Nur Namen mit mindestens 5 Zeichen
    
2. In Großbuchstaben umwandeln
    
3. Ausgeben
    

Erwartet:

```text
ALEXANDER
CHRIS
```

---

# Aufgabe 6 – Vielfache von 3

Gegeben:

```java
1 bis 20
```

Gib alle Zahlen aus, die durch 3 teilbar sind.

---

# Aufgabe 7 – Preise

Gegeben:

```java
ArrayList<Double> prices =
    new ArrayList<>(List.of(
        9.99,
        12.50,
        4.99,
        20.00
    ));
```

Erhöhe jeden Preis um 19%.

Ausgabe:

```text
11.8881
14.875
5.9381
23.8
```

---

# Aufgabe 8 – Strings und Zahlen

Gegeben:

```java
"1"
"2"
"3"
"4"
```

Wandle sie in echte Integer um.

Tipp:

```java
Integer.parseInt(...)
```

---

# Aufgabe 9 – Mehrere Schritte

Gegeben:

```java
1 2 3 4 5 6 7 8 9 10
```

1. Nur gerade Zahlen
    
2. Mit 10 multiplizieren
    
3. Ausgeben
    

Erwartet:

```text
20
40
60
80
100
```

---

# Aufgabe 10 – Klausurniveau

Gegeben:

```java
ArrayList<String> names =
    new ArrayList<>(List.of(
        "Anna",
        "Bob",
        "Alexander",
        "Chris",
        "Tom",
        "Jonathan"
    ));
```

Verarbeite die Liste so:

1. Nur Namen mit mehr als 4 Zeichen
    
2. In Großbuchstaben
    
3. Länge des Namens berechnen
    
4. Ergebnis ausgeben
    

Erwartet:

```text
5
9
5
8
```

---

# Bonus – Fast wie eine echte Klausur

Gegeben:

```java
ArrayList<String> words =
    new ArrayList<>(List.of(
        "java",
        "stream",
        "lambda",
        "thread",
        "file"
    ));
```

Erzeuge folgende Ausgabe:

```text
STREAM
LAMBDA
THREAD
```

Bedingungen:

- Nur Wörter mit mindestens 6 Zeichen
    
- In Großbuchstaben umwandeln
    
- Mit Streams lösen
    

---

Wenn du die ersten 5–10 Aufgaben löst und mir deinen Code schickst, korrigiere ich ihn und erkläre dabei genau, **wann man `filter()` verwendet und wann `map()`**, denn das ist der Knackpunkt, an dem die meisten Studenten hängen bleiben.