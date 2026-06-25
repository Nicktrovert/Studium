# Programmieren 2 – Rump-Stil Probeklausur 2026

Orientiert an:

- deinen aktuellen Folien
    
- der echten Probeklausur von Prof. Rump
    
- typischen Hochschulklausuren
    

**Bearbeitungszeit:** 90 Minuten  
**Gesamt:** 60 Punkte

---

# Aufgabe 1 – Theorie (6 Punkte)

## a) Generics (3P)

Erläutern Sie den Zweck von Generics in Java.

Gehen Sie dabei insbesondere auf folgende Aspekte ein:

- Typsicherheit
  > Der unterliegende Typ bleibt bekannt und gleich
    
- Typecasts
  > Es müssen weniger Typecasts durchgeführt werden
    
- Compilerfehler
  > Fehler werden zur Compilezeit bekannt und nicht erst zur Runtime
    

---

## b) Wrapperklassen (3P)

Was sind Wrapperklassen?

Nennen Sie drei Beispiele und erläutern Sie kurz den Zusammenhang mit Autoboxing.
> Integer, String, Character
> Autoboxing: ?

---

# Aufgabe 2 – Fehleranalyse (8 Punkte)

Betrachten Sie folgendes Programm:

```java
import java.util.*;

public class Test {

    public static void main(String[] args) {

        ArrayList<Object> list =
                new ArrayList<String>();

        list.add("Hallo");

        Integer x = (Integer) list.get(0);

        System.out.println(x);
    }
}
```

### a)

Beschreiben Sie kurz, was der Autor vermutlich erreichen wollte. (2P)
> Der Autor wollte vermutlich den ersten buchstaben des strings erhalten? Oder er wollte binärwerte? Oder den ascii wert des ersten buchstabens? Irgendein bullshit
### b)

Finden Sie alle Fehler. (6P)
> 1. ArrayList<\String> zu ArrayList<\Object> konvertierung
> 2. String zu Object List hinzugefügt
> 3. String zu Integer konvertierung

---

# Aufgabe 3 – Rekursion (10 Punkte)

Implementieren Sie folgende Methode rekursiv:

```java
String reverse(String s)
```

Beispiele:

```java
reverse("Hallo")
→ "ollaH"

reverse("abc")
→ "cba"
```

Vorgaben:

- Keine Schleifen
    
- Rekursive Lösung
    
- Leere Zeichenkette korrekt behandeln

```java
String reverse(String s){
	if (String.isEmpty(s))
		return s;
	
	return s[s.length-1] + reverse(s.substring(0, s.length-2))
}
```

---

## Zusatzfrage (2P)

Welche zwei Bedingungen müssen erfüllt sein, damit eine rekursive Lösung terminieren kann?

> Die abbruchbedingung muss existieren und erreichbar sein.

---

# Aufgabe 4 – Dateiverarbeitung (8 Punkte)

## a) Theorie (4P)

Erläutern Sie die Unterschiede zwischen:

```java
FileWriter
PrintWriter
BufferedReader
```

> FileWriter: Schreibt in dateien
> PrintWriter: Schribt in terminals
> BufferedReader: Ließt Streams (dateien)
---

## b) Praxis (4P)

Schreiben Sie ein Programmstück, das eine Datei

```text
zahlen.txt
```

zeilenweise einliest und jede Zeile auf der Konsole ausgibt.

Verwenden Sie dabei:

- BufferedReader
    
- try-with-resources

```java
try (BufferedReader in = new BufferedReader(new FileReader("zahlen.txt"))){
	String line
	while ((line = in.readLine()) != null){
		System.out.println(line);
	}
} catch (Exception e){

}
```

---

# Aufgabe 5 – Threads (8 Punkte)

Gegeben:

```java
class Counter {

    private int value = 0;

    public void increment() {
        value++;
    }

    public int getValue() {
        return value;
    }
}
```

Zwei Threads greifen gleichzeitig auf dieselbe Counter-Instanz zu.

---

## a) Problem (3P)

Beschreiben Sie ausführlich, welches Problem auftreten kann.
> Die Threads blockieren sich gegenseitig

---

## b) Lösung (3P)

Wie kann das Problem behoben werden?
> Beim aufruf 'synchronized' prefixen

---

## c) Theorie (2P)

Erläutern Sie den Unterschied zwischen:

```java
run() // synchronized aufruf im aktuellen thread
```

und

```java
start() // starten eines neuen threads
```

---

# Aufgabe 6 – Swing (10 Punkte)

Entwerfen Sie eine Swing-Anwendung mit folgenden Eigenschaften:

- Fenster mit Titel „Farbtest“
    
- Vier Buttons
    
- Anordnung 2×2
    
- Beim Klick auf einen Button soll dessen Text auf der Konsole ausgegeben werden
    

---

## Gefordert

Nennen bzw. verwenden Sie:

- JFrame
    
- JButton
    
- passenden LayoutManager
    
- ActionListener
    

Es genügt Java-Code, der das Prinzip zeigt.

```java
public Farbtest extends JFrame{
	public Farbtest(){
		JPanel p = new JPanel();
		this.setTitle("Farbtest")
		
		JButton b1 = new JButton("Red");
		b1.addActionListener(() -> {
			System.out.println("Red");
		});
		
		JButton b2 = new JButton("Blue");
		b2.addActionListener(() -> {
			System.out.println("Blue")
		});
		
		JButton b3 = new JButton("Green");
		b3.addActionListener(() -> {
			System.out.println("Green")
		});
		
		JButton b4 = new JButton("Cyan");
		b4.addActionListener(() -> {
			System.out.println("Cyan");
		});
		
		p.add(b1, BorderLayout.NORTH);
		p.add(b2, BorderLayout.NORTH);
		p.add(b3, BorderLayout.SOUTH);
		p.add(b4, BorderLayout.SOUTH);
		
		add(p, BorderLayout.CENTER);
	}
}
```

---

# Aufgabe 7 – Lambda & Streams (8 Punkte)

Gegeben:

```java
ArrayList<Integer> list =
        new ArrayList<>();

list.add(1);
list.add(2);
list.add(3);
list.add(4);
list.add(5);
```

---

## a) Lambda (3P)

Erzeugen Sie ein Runnable mittels Lambda-Ausdruck, das

```text
Hallo Welt
```

ausgibt.

```java
Runnable r = () -> {
	System.out.println("Hallo Welt");
};
r.start();
```

---

## b) Streams (5P)

Verwenden Sie Streams, um:

1. alle geraden Zahlen auszuwählen
    
2. diese mit 10 zu multiplizieren
    
3. das Ergebnis auszugeben

```java
list.foreach((i) -> {
	if (i % 2 == 0){
		System.out.println(i);
	}
});

list.map((i) -> {if (i % 2 == 0) {return i *= 10; } });

list.foreach((i) -> {
	if (i % 2 == 0){
		System.out.println(i);
	}
});
```

---

# Aufgabe 8 – Kurzfragen (10 Punkte)

Kreuzen Sie an bzw. beantworten Sie kurz.

---

### a)

Welche Aussage über ArrayList ist richtig?

-  Größe ist fest
    
-  Elemente werden über Index angesprochen [!R]
    
-  Nur primitive Datentypen erlaubt
    
-  ArrayList gehört zu java.io
    

---

### b)

Welche Aussage ist richtig?

-  Runnable ist eine Klasse [!R]
    
-  Thread ist ein Interface
    
-  Runnable ist ein Interface
    
-  start() wird automatisch vom Konstruktor aufgerufen
    

---

### c)

Welche Klasse repräsentiert eine URL?
> Java.net.URL

---

### d)

Was liefert:

```java
list.size()
```

zurück?

> Die Anzahl an elementen in list

---

### e)

Was macht:

```java
stream.filter(...)
```

> gibt alle werte zurück, die einer bedingung entsprechen
---

### f)

Was macht:

```java
stream.map(...)
```
> Verändert alle werte auf eine angegebene art

---

### g)

Ist folgende Zuweisung gültig?

```java
ArrayList<Object> a =
    new ArrayList<String>();
```

Begründen Sie.

> Nein. ArrayList<\String> ist nicht 'derived' von ArrayList<\Object>. ArrayList konvertiert den inhalt nicht, es sind unabhängige arten von ArrayListen.

---

## Schwierigkeit

Diese Klausur liegt deutlich näher an der echten Rump-Probeklausur als die erste:

- mehr Theorie
    
- mehr Erklären
    
- weniger reine Syntax
    
- Fehleranalyse
    
- Rekursion selbst schreiben
    
- Streams und Generics als Verständnisaufgaben
    

Wenn du sie bearbeitest, korrigiere ich sie streng nach Hochschulmaßstab und schätze daraus deine aktuelle Bestehenswahrscheinlichkeit für die echte Prüfung.