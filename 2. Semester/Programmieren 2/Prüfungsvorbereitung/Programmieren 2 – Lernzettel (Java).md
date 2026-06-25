# 1. Rekursion

## Definition

Eine rekursive Methode ruft sich selbst auf.

### Direkte Rekursion

```java
void m() {
    m();
}
```

### Indirekte Rekursion

```java
void m() {
    n();
}

void n() {
    m();
}
```

Jeder Methodenaufruf wird Rekursionsschritt genannt.

---

## Voraussetzungen

Eine rekursive Lösung benötigt:

1. Ein Abbruchkriterium
    
2. Einen rekursiven Schritt
    
3. Das Abbruchkriterium muss erreichbar sein
    

Sonst entsteht Endlosrekursion → StackOverflowError.

---

## Allgemeines Schema

```java
if (Problem klein genug)
    löse direkt;
else
    löse kleineres Teilproblem rekursiv;
```

---

## Fakultät

Mathematisch:

```
5! = 5 * 4 * 3 * 2 * 1
```

Rekursiv:

```
n! = n * (n-1)!
1! = 1
```

```java
long fact(int n) {
    if(n == 1)
        return 1;
    return n * fact(n-1);
}
```

---

## Rekursion vs Iteration

### Iteration

Vorteile:

- schneller
    
- weniger Speicher
    

Nachteile:

- oft komplizierter
    

### Rekursion

Vorteile:

- kürzerer Code
    
- oft verständlicher
    

Nachteile:

- höherer Speicherverbrauch
    
- langsamer durch Methodenaufrufe
    

---

## Klausurklassiker

### ggT (Euklid)

```java
int ggt(int x, int y) {
    int rest = x % y;

    if(rest == 0)
        return y;

    return ggt(y, rest);
}
```

### Binäre Suche

Voraussetzung:

⚠️ Array muss sortiert sein.

Laufzeit:

```
O(log n)
```

---

# 2. Collections (ArrayList)

## Warum ArrayList?

Array:

```java
String[] a = new String[100];
```

Größe ist fest.

ArrayList:

```java
ArrayList<String> list = new ArrayList<>();
```

Größe wächst automatisch.

---

## Diamond Operator

Statt

```java
ArrayList<String> list =
    new ArrayList<String>();
```

schreibt man

```java
ArrayList<String> list =
    new ArrayList<>();
```

---

## Elemente hinzufügen

```java
list.add("Hallo");
```

---

## Lesen

```java
String s = list.get(0);
```

---

## Ersetzen

```java
list.set(0, "Neu");
```

---

## Entfernen

Nach Wert:

```java
list.remove("Hallo");
```

Nach Index:

```java
list.remove(0);
```

---

## Weitere wichtige Methoden

### Größe

```java
list.size();
```

### Enthält?

```java
list.contains("Test");
```

### Position

```java
list.indexOf("Test");
```

### Letzte Position

```java
list.lastIndexOf("Test");
```

### In Array umwandeln

```java
String[] a = list.toArray(new String[0]);
```

---

## Wrapperklassen

Primitive Typen sind keine Objekte:

```java
int
double
char
```

Wrapper:

```java
Integer
Double
Character
```

---

## Autoboxing

Automatische Umwandlung:

```java
Integer x = 5;
```

entspricht

```java
Integer x = Integer.valueOf(5);
```

---

## Unboxing

```java
Integer x = 5;

int y = x;
```

---

# 3. Dateiverarbeitung

## Datenstrom

Folge von Bytes.

### Standardströme

```java
System.in
System.out
System.err
```

---

# Klasse File

## Datei erzeugen

```java
File f = new File("test.txt");
```

---

## Wichtige Methoden

```java
exists()
canRead()
canWrite()
isFile()
isDirectory()
length()
getName()
getPath()
getAbsolutePath()
```

---

# Lesen von Dateien

```java
BufferedReader in =
    new BufferedReader(
        new FileReader("test.txt"));
```

---

## Zeilenweise lesen

```java
String line;

while((line = in.readLine()) != null) {
    System.out.println(line);
}
```

---

# Schreiben

```java
PrintWriter out =
    new PrintWriter(
        new FileWriter("out.txt"));
```

---

## Ausgabe

```java
out.println("Hallo");
```

---

# IOException

Viele Dateioperationen können fehlschlagen.

Deshalb:

```java
throws IOException
```

oder

```java
try {
}
catch(IOException e) {
}
```

---

# Try-With-Resources

Best Practice:

```java
try(
    BufferedReader in =
        new BufferedReader(
            new FileReader("test.txt"))
) {
    ...
}
```

Automatisches Schließen.

---

# 4. Threads

## Was ist ein Thread?

Ein eigener Ausführungsfaden innerhalb eines Prozesses.

---

## Variante 1: Vererbung

```java
class MyThread extends Thread {

    public void run() {
        System.out.println("Hallo");
    }
}
```

Start:

```java
MyThread t = new MyThread();
t.start();
```

⚠️ Niemals direkt:

```java
t.run();
```

---

## Variante 2: Runnable

```java
class MyRunnable
implements Runnable {

    public void run() {
        ...
    }
}
```

```java
Thread t =
    new Thread(new MyRunnable());

t.start();
```

---

## Wichtige Methoden

### sleep

```java
Thread.sleep(1000);
```

1 Sekunde warten.

---

### join

```java
t.join();
```

Auf Threadende warten.

---

### interrupt

```java
t.interrupt();
```

Thread unterbrechen.

---

# Synchronisation

Problem:

```java
x++;
```

ist nicht atomar.

Mehrere Threads können sich gegenseitig überschreiben.

---

## Lösung

```java
public synchronized void inc() {
    x++;
}
```

Oder:

```java
synchronized(obj) {
    ...
}
```

---

# 5. Netzwerkprogrammierung

## TCP/IP

Kommunikation im Netzwerk.

Java-Paket:

```java
java.net
```

---

# URL

```java
URL url =
    new URL("https://example.com");
```

---

## Stream öffnen

```java
InputStream in =
    url.openStream();
```

---

# Socket

Client-Seite

```java
Socket s =
    new Socket(host, port);
```

---

## Lesen

```java
s.getInputStream();
```

---

## Schreiben

```java
s.getOutputStream();
```

---

## Schließen

```java
s.close();
```

---

# ServerSocket

Server-Seite:

```java
ServerSocket server =
    new ServerSocket(5000);
```

---

## Verbindung akzeptieren

```java
Socket client =
    server.accept();
```

Blockiert bis Client verbindet.

---

# 6. Swing

## JFrame

Fensterklasse.

```java
JFrame frame =
    new JFrame();
```

---

## Wichtige Methoden

```java
setTitle()
setSize()
setVisible()
setDefaultCloseOperation()
```

---

## Label

```java
JLabel label =
    new JLabel("Text");
```

---

## Button

```java
JButton button =
    new JButton("Klick");
```

---

## Hinzufügen

```java
container.add(button);
```

---

# LayoutManager

Bestimmt Anordnung.

Beispiele:

```java
FlowLayout
BorderLayout
GridLayout
```

---

# ActionListener

```java
button.addActionListener(
    new ActionListener() {
        public void actionPerformed(
            ActionEvent e) {

        }
    }
);
```

---

# 7. Generics

## Problem ohne Generics

```java
Object obj;
```

Beim Lesen:

```java
String s =
    (String)obj;
```

Typecast notwendig.

Fehler erst zur Laufzeit.

---

## Generische Klasse

```java
class Box<T> {

    private T value;

}
```

---

## Verwendung

```java
Box<String> b =
    new Box<String>();
```

---

## Vorteile

- Typsicherheit
    
- weniger Typecasts
    
- Fehler bereits beim Kompilieren
    

---

## Typvariable

Häufig:

```java
T
E
K
V
```

---

# 8. Lambda-Ausdrücke

## Idee

Anonyme Funktion.

Syntax:

```java
(parameter) -> ausdruck
```

oder

```java
(parameter) -> {
    anweisungen
}
```

---

## Beispiele

```java
x -> x * x
```

```java
(a,b) -> a + b
```

```java
() -> System.out.println("Hallo");
```

---

## Runnable mit Lambda

Statt

```java
Runnable r =
    new Runnable() {
        public void run() {
            ...
        }
    };
```

schreibt man

```java
Runnable r =
    () -> ...
```

---

# Funktionale Interfaces

Ein funktionales Interface besitzt genau eine abstrakte Methode.

Beispiele:

```java
Runnable
ActionListener
```

---

# Vordefinierte Interfaces

## Function<T,R>

```java
R apply(T t)
```

---

## Consumer

```java
void accept(T t)
```

---

## Predicate

```java
boolean test(T t)
```

---

# Streams

Streams ermöglichen funktionale Verarbeitung von Daten.

---

## Stream erzeugen

```java
list.stream()
```

---

## Filter

```java
stream.filter(x -> x > 0)
```

---

## Transformation

```java
stream.map(x -> x * 2)
```

---

## Ausgabe

```java
stream.forEach(System.out::println);
```

---

# Klausur-Merkliste (sehr wichtig)

Wenn du diese Punkte sicher beherrschst, deckst du erfahrungsgemäß den Großteil typischer Aufgaben ab:

✓ Rekursion schreiben und Ablauf nachvollziehen  
✓ Rekursion ↔ Iteration vergleichen  
✓ ArrayList-Methoden auswendig kennen  
✓ File, Reader, Writer unterscheiden  
✓ IOException verstehen  
✓ Thread vs Runnable erklären können  
✓ start() vs run() kennen  
✓ synchronized verstehen  
✓ Socket und ServerSocket unterscheiden  
✓ JFrame, JLabel, JButton verwenden können  
✓ Generics lesen und schreiben können  
✓ Lambda-Ausdrücke in normale Klassen umwandeln können  
✓ Funktionale Interfaces erkennen  
✓ einfache Stream-Pipelines lesen können