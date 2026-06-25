# Programmieren 2 – Probeklausur

**Orientiert an den Vorlesungsfolien**

- Bearbeitungszeit: 90 Minuten
    
- Hilfsmittel: Keine
    
- Gesamtpunkte: 100
    

---

# Teil A – Grundlagen (20 Punkte)

## A1 Rekursion (4P)

Gegeben:

```java
int f(int n) {
    if(n <= 1)
        return 1;
    return n + f(n - 1);
}
```

1. Berechnen Sie `f(4)`.
   > 4+3+2+1 = 10
    
2. Zeichnen Sie den vollständigen Rekursionsbaum.
   > f wird aufgerufen mit n = 4 -> return 4 + f(4 - 1) -> f wird aufgerufen mit n = 3 -> return 3 + f(3-1) -> f wird aufgerufen mit n = 2 -> return 2 + f(2-1) -> f wird aufgerufen mit n = 2 -> return 2 + f(2-1) -> f wird aufgerufen mit n=1 -> return 1; Addition aller returns = 10
    

---

## A2 Rekursion (4P)

Nennen Sie die zwei zwingenden Voraussetzungen für eine rekursive Lösung.

> Eine abbruchbedingung und ein rekursiver aufruf

---

## A3 Collections (4P)

Welche Ausgabe erzeugt folgendes Programm?

```java
ArrayList<String> list = new ArrayList<>();

list.add("A");
list.add("B");
list.add("C");

list.remove(1);

System.out.println(list.get(1));
System.out.println(list.size());
```

> C
> 2
---

## A4 Threads (4P)

Erklären Sie den Unterschied zwischen:

```java
t.run();
```

und

```java
t.start();
```

> .run(); währe ein synchroner aufruf im selben thread.
> .start(); aktiviert den thread und läuft asynchron
---

## A5 Generics (4P)

Warum sind Generics gegenüber `Object`-Referenzen vorzuziehen?

Nennen Sie mindestens zwei Vorteile.

> Implicite konvertierung
> Lesbarer

---

# Teil B – Codeanalyse (20 Punkte)

## B1 ArrayList (5P)

Gegeben:

```java
ArrayList<Integer> list =
        new ArrayList<>();

for(int i=0;i<5;i++)
    list.add(i);

list.set(2, 99);

for(Integer x : list)
    System.out.print(x + " ");
```

Welche Ausgabe entsteht?

> 0 1 99 3 4
---

## B2 Dateiverarbeitung (5P)

Gegeben:

```java
try(
    BufferedReader in =
        new BufferedReader(
            new FileReader("test.txt"))
) {
    String line;

    while((line = in.readLine()) != null)
        System.out.println(line);
}
catch(IOException e) {
    System.out.println("Fehler");
}
```

Beantworten Sie:

1. Wozu dient `BufferedReader`?
   > Der BufferedReader liest die zeichen in der Datei, während sie benötigt werden einer nach dem anderen, statt alle auf einmal, und auch erst sobald ein aufruf entsteht, sobald diese benötigt werden.
    
2. Wozu dient `readLine()`?
   > readline, ist einer dieser aufrufe, welche dem BufferedReader sagen, er muss weiter lesen. Bei readLine stoppt der BufferedReader sobald er das ende einer Zeile erreicht, meißt indiziert durch '\n' oder '\r'
    
3. Warum wird kein `close()` benötigt?
   > Weil der BufferedReader innerhalb des try initialisiert wurde, und somit intern automatisch close() aufgerufen wird.
    

---

## B3 Rekursion (5P)

Welche Ausgabe erzeugt:

```java
void print(int n) {
    if(n == 0)
        return;

    System.out.print(n + " ");
    print(n - 1);
}

print(4);
```

> 4 3 2 1

---

## B4 Generics (5P)

Ist folgender Code korrekt?

```java
ArrayList<Object> a =
        new ArrayList<String>();
```

Falls nein:

- Warum nicht?
  > Ein ArrayList Object kann nicht zu einem anderen ArrayList Object konvertiert werden, wenn diese nicht den selben type beinhalten
    
- Welcher Compilerfehler entsteht inhaltlich?
  > cannot convert ArrayList<\String>() to ArrayList<\Object>
    

---

# Teil C – Programmierung (25 Punkte)

## C1 Rekursion (10P)

Implementieren Sie rekursiv:

```java
int sum(int n)
```

Berechnet:

```text
sum(5) = 15
sum(4) = 10
sum(3) = 6
```

Vorgabe:

```java
int sum(int n) {
	if (n <= 1)
		return 1;
	return n + sum(n - 1)
}
```

---

## C2 ArrayList (8P)

Schreiben Sie eine Methode:

```java
int countEven(ArrayList<Integer> list)
```

Die Anzahl aller geraden Zahlen soll zurückgegeben werden.

Beispiel:

```java
[1,2,3,4,5,6]
```

Ergebnis:

```java
3
```

Antwort:
```Java
int countEven(ArrayList<Integer> list){
	int amount = 0;
	for (Integer i : list){
		if (i % 2 == 0)
			amount++;
	}
	return amount;
}
```

---

## C3 Lambda (7P)

Wandeln Sie den folgenden Code in einen Lambda-Ausdruck um.

```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hallo");
    }
};
```
Antwort:
```java
Runnable r = () -> {
	System.out.println("Hallo");
}
```


---

# Teil D – Threads und Netzwerk (15 Punkte)

## D1 Thread (5P)

Vervollständigen Sie:

```java
class Printer extends Thread {

    public void run() {
        System.out.println("Test");
    }
}
```

so, dass daraus ein lauffähiger Thread wird.

---

## D2 Synchronisation (5P)

Warum kann folgendes problematisch sein?

```java
x++;
```

wenn mehrere Threads gleichzeitig arbeiten?
> Es könnte passieren, dass 2 Threads gleichzeitig auf die variable zugreifen wollen, und diese um eins erhöhen.

Welches Java-Schlüsselwort wird häufig zur Lösung verwendet?
> synchronized()

---

## D3 Netzwerk (5P)

Ordnen Sie zu:

| Klasse       | Aufgabe                                                     |
| ------------ | ----------------------------------------------------------- |
| Socket       | Client baut eine netzwerkverbindung zu einem Server auf     |
| ServerSocket | Server erlaubt anderen eine verbindung aufzubauen           |
| URL          | "Adresse" um einen netz aufbau mit einer Website aufzubauen |

---

# Teil E – Swing & Streams (20 Punkte)

## E1 Swing (5P)

Welche Klasse repräsentiert ein Fenster?
> JFrame

---

## E2 Swing (5P)

Welche Swing-Komponente wird verwendet für:

a) Textanzeige
> JLabel

b) Knopf
> JButton

---

## E3 Lambda (5P)

Welche Eigenschaften muss ein Interface besitzen, damit es mit Lambda-Ausdrücken verwendet werden kann?

> ?

---

## E4 Streams (5P)

Beschreiben Sie kurz die Aufgabe von:

```java
filter(...) // gibt nur die daten zurück, welcher der bedingung entsprechen
map(...) // verknüpft daten miteinander
forEach(...) // wendet etwas auf jedes datenobjekt an
```

---

# Bonus – Schwer (10 Punkte)

Gegeben:

```java
public static int f(int n) {
    if(n <= 0)
        return 0;

    return f(n-1) + n;
}
```

1. Was berechnet die Methode?
   > die Methode berechnet die fakultät einer zahl
    
2. Bestimmen Sie:
    

```java
f(5)
```

> 0 + 1 + 2 + 3 + 4 + 5 = 15
3. Formulieren Sie eine iterative Lösung.
   ```java
   public static int f(int n) {
	   int fak = 0;
	   do {
		   fak += n;
		   n--;
	   } while (n > 0)
	   return fak;
   }
   ```
    

---

# Bewertung

|Bereich|Punkte|
|---|---|
|Teil A|20|
|Teil B|20|
|Teil C|25|
|Teil D|15|
|Teil E|20|
|Bonus|10|
|Gesamt|110|

---

Wenn du die Klausur bearbeitet hast, schick mir einfach deine Antworten (z. B. „A1: ..., A2: ...“). Dann korrigiere ich sie streng wie ein Prüfer und schätze deine aktuelle Klausurnote.