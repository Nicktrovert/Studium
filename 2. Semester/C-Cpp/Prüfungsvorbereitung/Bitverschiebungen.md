Bitverschiebungen sind eines dieser Themen, die viele Leute unnötig verlieren, obwohl die Aufgaben oft einfache Punkte sind.

Ich stelle dir ein paar Klausur-ähnliche Fragen. Rechne sie **ohne Taschenrechner**.

---

# Aufgabe 1

Gegeben:

```cpp
int x = 5;
```

Was ist das Ergebnis von:

```cpp
x << 1
```

### Fragen

1. Binärdarstellung von 5
    
2. Ergebnis nach der Verschiebung
    
3. Dezimalwert
    

---

# Aufgabe 2

Gegeben:

```cpp
int x = 10;
```

Was ist:

```cpp
x << 2
```

### Zusatzfrage

Mit welcher Rechenoperation entspricht das ungefähr?

```text
x << n ≈ ?
```

---

# Aufgabe 3

Gegeben:

```cpp
int x = 40;
```

Was ergibt:

```cpp
x >> 3
```

### Zusatzfrage

Mit welcher Rechenoperation entspricht das ungefähr?

```text
x >> n ≈ ?
```

---

# Aufgabe 4

Gegeben:

```cpp
int x = 128;
```

Führe aus:

```cpp
x >>= 2;
```

Wie lautet das Ergebnis?

---

# Aufgabe 5

Bitoperatoren

Berechne:

```text
1100
1010
----
```

für

```cpp
&
```

---

# Aufgabe 6

Berechne:

```text
1100
1010
----
```

für

```cpp
|
```

---

# Aufgabe 7

Berechne:

```text
1100
1010
----
```

für

```cpp
^
```

---

# Aufgabe 8 (typische Klausurfrage)

Gegeben:

```cpp
int x = 128;
```

Führe schrittweise aus:

```cpp
x |= 64;
x ^= 16;
x &= 192;
```

Wie lautet der Endwert?

---

# Aufgabe 9 (etwas fieser)

Gegeben:

```cpp
int flags = 0;
```

Was bewirkt:

```cpp
flags |= (1 << 3);
```

### Fragen

1. Welches Bit wird gesetzt?
    
2. Welchen Dezimalwert hat `flags` danach?
    

---

# Aufgabe 10 (Prüfungsniveau)

Gegeben:

```cpp
int flags = 13;
```

Binär:

```text
1101
```

Was ergibt:

```cpp
flags & (1 << 2)
```

### Fragen

1. Welches Bit wird geprüft?
    
2. Ist die Bedingung wahr oder falsch?
    

---
