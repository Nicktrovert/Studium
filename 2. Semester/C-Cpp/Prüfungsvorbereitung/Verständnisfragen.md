# 00_README

### Warum ist das Script in Materialpakete untergliedert?

Damit komplexe Inhalte in kleinere, aufeinander aufbauende Lerneinheiten zerlegt werden. Jedes Paket behandelt ein klar abgegrenztes Thema.

### Welche Voraussetzungen hat ein Materialpaket?

Die vorherigen Pakete sollten verstanden sein. Die Pakete bauen aufeinander auf.

### Reicht das Material aus, um ein guter C++-Programmierer zu werden?

Nein.

Es vermittelt die Grundlagen und viele wichtige Konzepte, aber:

- große Projekte fehlen
    
- Design Patterns fehlen
    
- moderne C++-Features fehlen teilweise
    
- Software Engineering fehlt weitgehend
    
- Praxiserfahrung fehlt
    

Es schafft eine solide Basis.

---

# 01b_TOOL – Toolchain

### Glossar aller Komponenten

**Editor**

- Quelltext schreiben
    

**Präprozessor**

- verarbeitet `#include`, `#define`
    

**Compiler**

- übersetzt C++ → Assembler
    

**Assembler**

- übersetzt Assembler → Objektdatei
    

**Linker**

- verbindet Objektdateien zu einem Programm
    

**Loader**

- lädt das Programm beim Start in den Speicher
    

**Archiver**

- erzeugt Bibliotheken (`.a`)
    

---

### Kann eine Funktion aus einer anderen Quelldatei aufgerufen werden?

Ja.

Voraussetzung:

- Deklaration muss bekannt sein (`.hpp`)
    
- Definition existiert in einer anderen Übersetzungseinheit
    

Der Linker verbindet beides.

---

### Aufgaben des Compilers

- Syntax prüfen
    
- Typprüfung
    
- Optimierung
    
- Erzeugung von Assemblercode
    

---

### Unterschied Objektdatei und ausführbare Datei

**Objektdatei (.o)**

- Teilstück
    
- enthält Maschinencode
    
- meist nicht direkt ausführbar
    

**Ausführbare Datei**

- vollständig gelinkt
    
- kann direkt gestartet werden
    

---

# 02a_FLOW_basic

### Warum Iteration statt vieler gleicher Anweisungen?

Statt:

```cpp
arr[0]=0;
arr[1]=0;
arr[2]=0;
```

schreibt man:

```cpp
for(int i=0;i<3;i++)
    arr[i]=0;
```

Vorteile:

- weniger Code
    
- leichter wartbar
    
- flexibel für beliebige Größen
    

---

### Warum Funktionen?

- Wiederverwendbarkeit
    
- weniger Duplikate
    
- bessere Lesbarkeit
    
- einfacheres Testen
    

---

### Vorteile von Rekursion

- natürliche Beschreibung vieler Probleme
    
- Bäume
    
- Parser
    
- Divide-and-Conquer
    

---

### Nachteile von Rekursion

- mehr Speicherverbrauch
    
- Funktionsaufrufe kosten Zeit
    
- Gefahr von Stack Overflow
    

---

### Schwierigkeit bei FizzBuzz

Nicht die Syntax.

Die Schwierigkeit ist:

- Bedingungen korrekt kombinieren
    
- Reihenfolge beachten
    

```cpp
if(x%15==0)
```

muss vor

```cpp
if(x%3==0)
```

kommen.

---

### Warum Style Guides?

- einheitlicher Code
    
- bessere Lesbarkeit
    
- weniger Fehler
    
- Teamarbeit wird einfacher
    

---

# 02c_FLOW_parse

### Reihenfolge der Berechnung

```text
1+2+3+4
```

linksassoziativ:

```text
((1+2)+3)+4
```

---

```text
2+3*45
```

Multiplikation zuerst:

```text
2+(3*45)
```

---

```text
3+45*2
```

Multiplikation zuerst:

```text
3+(45*2)
```

---

### Warum eignen sich rekursive Funktionen für Parser?

Weil die Grammatik selbst rekursiv ist.

Beispiel:

```ebnf
expression -> term expression
```

kann direkt als rekursive Funktion umgesetzt werden.

---

# 03b_DATA_rep

### Pascal-String vs. C-String

## Pascal

```text
[5]Hallo
```

Länge gespeichert.

Vorteile:

- Länge sofort bekannt
    

Nachteile:

- begrenzte Länge
    

---

## C-String

```text
Hallo\0
```

Nullterminiert.

Vorteile:

- flexibel
    
- Standard in C
    

Nachteile:

- Länge muss gesucht werden
    

---

### Ergebnis der Bitoperationen

Ausgang:

```cpp
128
```

```text
10000000
```

Nach

```cpp
|= 64+32
```

```text
11100000
```

Nach

```cpp
^=16
```

```text
11110000
```

Nach

```cpp
&=(128+64)
```

```text
11000000
```

Nach

```cpp
<<=1
```

```text
110000000
```

dezimal:

```text
384
```

---

# 04a_UDEF

### Warum Abstraktion?

Man denkt in fachlichen Begriffen statt in Bits und primitiven Typen.

Statt:

```cpp
double real;
double imag;
```

schreibt man:

```cpp
Complex
```

Dadurch wird der Code verständlicher.

---

### Warum benutzerdefinierte Typen?

Sie modellieren reale Probleme besser.

Beispiele:

- RationalNumber
    
- Color
    
- PascalString
    

---

# 04b_VAL

### Warum `explicit` bei Konstruktoren mit einem Parameter?

Verhindert ungewollte Typumwandlungen.

Problem:

```cpp
RgbColor c = 5;
```

könnte sonst automatisch konvertieren.

`explicit` macht solche Fehler sichtbar.

---

### Vorteil der Member Initializer List

Statt:

```cpp
x = value;
```

wird direkt konstruiert:

```cpp
A():x(value){}
```

Vorteile:

- effizienter
    
- nötig für const und Referenzen
    

---

# 05a_OO_INH

### Klasse vs Objekt

**Klasse**  
= Bauplan

**Objekt**  
= konkrete Instanz

---

### Zweck von Basisklassen

Gemeinsamkeiten bündeln.

Beispiel:

```cpp
Shape
```

für

```cpp
Circle
Rectangle
Triangle
```

---

### Wann wird eine virtuelle Methode ausgewählt?

**virtual**  
→ Laufzeit (Late Binding)

**nicht virtual**  
→ Compilezeit (Early Binding)

---

### Warum gegen Basisklassen programmieren?

```cpp
Shape*
```

statt

```cpp
Circle*
```

Dadurch wird der Code erweiterbar.

Neue Klassen können später ergänzt werden.

---

# 05b_OO_ENTVAL

### Werttyp oder Entität?

|Begriff|Typ|
|---|---|
|Temperatur|Werttyp|
|Farbton|Werttyp|
|Artikel|Entität|
|Elektronisches Bauteil|Entität|

---

### Äquivalenz vs Identität

**Äquivalenz**

```cpp
a == b
```

gleicher Inhalt

---

**Identität**

```cpp
&a == &b
```

gleiches Objekt

---

### is-a vs has-a

**is-a**

```cpp
Dog is Animal
```

→ Vererbung

---

**has-a**

```cpp
Car has Engine
```

→ Membervariable

---

### Aggregation vs Komposition

**Aggregation**

- Teile können unabhängig existieren
    

**Komposition**

- Teile gehören fest zum Ganzen
    

Beispiel:

```text
Universität → Student
```

Aggregation

```text
Haus → Zimmer
```

Komposition

---

# 05c_OO_CYCL

### Reihenfolge Konstruktoren

```text
Basisklasse
↓
Member
↓
eigene Klasse
```

---

### Reihenfolge Destruktoren

Genau umgekehrt:

```text
eigene Klasse
↓
Member
↓
Basisklasse
```

---

### Zweck der member initializer list

Direkte Initialisierung der Member.

---

### Zweck der base initializer list

Konstruktorparameter an die Basisklasse weitergeben.

---

### Was macht `new`?

1. Speicher reservieren
    
2. Konstruktor aufrufen
    
3. Zeiger zurückgeben
    

---

### Warum sind `new` und `delete` nicht konstant schnell?

Der Heap muss freie Speicherbereiche suchen und verwalten.

Die benötigte Zeit hängt vom Zustand des Heaps ab.

---
# 05d_OO_BIND

### 1. Wozu wird das statische Binden des Aufrufs einer virtuellen Methode zwingend benötigt?

Damit der Compiler überhaupt feststellen kann, **welche Signatur** aufgerufen wird.

Beispiel:

```cpp
Shape* s;
s->draw();
```

Der Compiler muss wissen:

- gibt es `draw()`?
    
- welche Parameter hat `draw()`?
    
- welcher Rückgabetyp?
    

Die konkrete Implementierung wird erst später dynamisch bestimmt.

---

### 2. Wann wird festgelegt, aus welcher Klasse die Implementierung stammt?

**Zur Laufzeit.**

Der dynamische Typ des Objekts entscheidet.

```cpp
Shape* s = new Circle();
s->draw();
```

→ `Circle::draw()`

---

### 3. Wann wird die Signatur einer überladenen Methode festgelegt?

**Zur Compilezeit.**

Overloading = Early Binding.

```cpp
foo(1);
foo("abc");
```

Der Compiler entscheidet anhand der Parametertypen.

---

### 4. Upcast: static_cast oder dynamic_cast?

Normalerweise gar kein Cast nötig:

```cpp
Derived* d;
Base* b = d;
```

implizit erlaubt.

Falls explizit:

```cpp
static_cast<Base*>(d)
```

reicht völlig.

`dynamic_cast` wäre unnötig.

---

### 5. Downcast: static_cast oder dynamic_cast?

Für sichere Downcasts:

```cpp
dynamic_cast<Derived*>(b)
```

weil Laufzeitprüfung erfolgt.

```cpp
static_cast<Derived*>(b)
```

kompiliert zwar, kann aber zu Undefined Behavior führen.

---

### 6. Kann der Compiler einen Downcast implizit vornehmen?

Nein.

```cpp
Base* b;
Derived* d = b;
```

Fehler.

Nicht jedes Base-Objekt ist ein Derived-Objekt.

---

### 7. Basisklassenimplementierung einer virtuellen Methode aufrufen?

Ja.

```cpp
Base::draw();
```

innerhalb einer überschriebenen Methode:

```cpp
void Derived::draw() {
    Base::draw();
}
```

---

### 8. Kann über Basisklassenzeiger eine nicht-virtuelle Methode der abgeleiteten Klasse aufgerufen werden?

Direkt nein.

```cpp
Base* b = new Derived();
b->foo();
```

Wenn `foo()` nur in `Derived` existiert:

→ Compilerfehler.

Man benötigt einen Cast:

```cpp
dynamic_cast<Derived*>(b)->foo();
```

---

### 10. dynamic_cast vs typeid

#### dynamic_cast

Prüft:

```cpp
dynamic_cast<Rectangle*>(s)
```

auch auf Unterklassen.

Wenn

```cpp
class FancyRectangle : public Rectangle
```

existiert:

→ Cast erfolgreich.

---

#### typeid

Prüft exakten Typ.

```cpp
typeid(*s) == typeid(Rectangle)
```

ist bei

```cpp
FancyRectangle
```

falsch.

Das ist der entscheidende Unterschied.

---

### 11. Überladen + virtuell gleichzeitig

Zuerst:

**Overload Resolution**

(Compilezeit)

Danach:

**Virtual Dispatch**

(Laufzeit)

Beispiel:

```cpp
p->foo(5);
```

1. Compiler bestimmt Signatur `foo(int)`
    
2. Laufzeit bestimmt konkrete Implementierung
    

---

### 12. Zusammenhang Funktionszeiger und Interrupt Handler

Interrupt Handler werden oft als Adressen/Funktionszeiger gespeichert.

Interrupt:

```text
IRQ
 ↓
Interrupt Vector Table
 ↓
Funktionsadresse
 ↓
Handler
```

Das Prinzip ist dasselbe wie bei Funktionszeigern.

---

### 13. Alternativen zu Funktionszeigern beim Logging

#### if/else

```cpp
if(level==1)
```

einfach, aber viele Verzweigungen.

---

#### Präprozessor

```cpp
#ifdef DEBUG
```

Compilezeit-Umschaltung.

Keine Laufzeitänderung möglich.

---

#### Linker

Unterschiedliche Objektdateien linken:

```text
logger_debug.o
logger_release.o
```

Entscheidung beim Build.

---

#### Funktionszeiger

Entscheidung zur Laufzeit.

Flexibelste Lösung.

---

# 06_STD

### 1. vector vs list

|vector|list|
|---|---|
|zusammenhängender Speicher|verkettete Elemente|
|schneller Zufallszugriff|langsamer Zufallszugriff|
|cachefreundlich|weniger cachefreundlich|
|Einfügen in Mitte teuer|Einfügen in Mitte günstig|

---

### 2. Warum kann std::sort unbekannte Typen sortieren?

Templates.

Der Compiler erzeugt den Code erst für den konkreten Typ.

Zusätzlich muss normalerweise

```cpp
operator<
```

existieren.

---

### 3. Vorteil STL statt Eigenimplementierung

- getestet
    
- optimiert
    
- standardisiert
    
- weniger Bugs
    
- weniger Entwicklungsaufwand
    

---

### 4. Stapel (Stack) implementieren

Einfach:

```cpp
std::stack<int>
```

verwenden.

Alternativ:

```cpp
std::vector<int>
```

mit

```cpp
push_back()
pop_back()
```

---

### 5. Wird std::list implizit zu std::list?

Nein.

```cpp
char -> int
```

ist erlaubt.

Aber:

```cpp
std::list<char>
```

und

```cpp
std::list<int>
```

sind komplett verschiedene Typen.

Templates sind invariant.

---

# 07_IO

### 1. match_greet_one("Hello,World!")

Vermutlich erkennt der Parser:

```text
Hello
```

und stoppt.

Der Rest

```text
,World!
```

bleibt übrig.

Das ist derselbe Fehler wie:

```cpp
int x;
```

wenn ein Compiler nur

```cpp
int
```

erkennt und den Rest ignoriert.

Ein korrekter Parser muss prüfen:

> Wurde die gesamte Eingabe verbraucht?

Das fehlt hier vermutlich.

---

### 2. Was ist besonders an dieser Grammatik?

```ebnf
expr ::= operand ( OPERATOR operand )*
```

Sie behandelt alle Operatoren gleich.

Dadurch gibt es:

- keine Prioritäten
    
- keine Assoziativität
    

Beispiel:

```text
2+3*4
```

würde nicht zwischen `+` und `*` unterscheiden.

Die Grammatik ist einfach, aber mathematisch unvollständig.

---

### 3. Warum haben alle match_-Funktionen dieselbe Signatur?

Einheitliche Schnittstelle.

Dadurch können Parserfunktionen:

- austauschbar werden
    
- rekursiv kombiniert werden
    
- als Funktionszeiger verwendet werden
    

Das macht den Parser modular.

---

### 4. Warum verwenden viele Sprachen `;`?

Mehrere Gründe:

#### Eindeutiges Ende einer Anweisung

```cpp
a = 1;
b = 2;
```

---

#### Einfacheres Parsing

Der Parser erkennt klar:

```text
Anweisung endet hier
```

---

#### Weniger Mehrdeutigkeit

Zeilenumbrüche sind oft nicht eindeutig.

```cpp
a = b +
c;
```

ist trotzdem eine Anweisung.

---
