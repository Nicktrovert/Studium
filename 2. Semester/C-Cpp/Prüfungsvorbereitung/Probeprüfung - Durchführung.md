Punkte: 100
## Teil A - Theorie ( 30 Punkte)

### Aufgabe A1 - Toolchain (6p)

Beschreibe die Aufgaben von:
```cpp
Preprocessor
Compiler
Assembler
Linker
Loader
```

Antwort:
Preprocessor: Die datei "aufräumen", includes einfügen, defines setzen, etc.
Compiler: Code zu assembler sprache umändern
Assembler: Code zu Cpu-lesbarer Maschinensprache übersetzen
Linker: Objektdateien zu einer ausführbaren Datei kombinieren
Loader: Führt die `.out`datei vom Linker aus.

### Aufgabe A2 - Fehlerarten (6p)

Antwort:

Fall 1: undeclared symbol
Fall 2: undefined function
Fall 3: undefined reference

### Aufgabe A3 - Rule of Zero / Three / Five (8p)
Rule of Zero wird verwendet, wenn die automatisch generierten Dekonstruktor, Copy assignment und zuweisung operator keine probleme verursachen.

Rule of Three wird verwendet, wenn die Klasse inhalt besitzt, welcher verwaltet werden muss (bspw. Pointer). Dekonstruktor, Copy assignment und zuweisung müssen selbst implementiert werden.

Rule of Five wird verwendet, um eine effiziente Ressourcenübergabe zu ermöglichen per Move anweisungen.

### Aufgabe A4 - RAII (4p)

Antwort: Es ist effizienter, da kein Garbage Collector die cpu nutzt um aufzuräumen und es entstehen keine fehler durch das vertrauen, dass der Garbage Collector rechtzeitig durchlief.

### Aufgabe A5 - virtual (6p)

Antwort: bei virtual wird die Zielmethode zur Laufzeit bestimmt. bei nicht-virtual wird die Zielmethode zur compile zeit bestimmt. Es ist wichtig, da fehler auftauchen könnten, wenn virtual methoden zur compile zeit bestimmt werden würden. Es könnte passieren, dass verschiedenste Child Objekte als Parent in einer Liste gespeichert werden und darüber eine `foo()` methode aufgerufen wird. Wenn dies zur Compile zeit zugewiesen wird, würde der Compiler es der Parent klasse zuweisen. Eigentlich müssen aber die Implementationen der Jeweiligen Child Klassen ausgeführt werden, je nach dem welches objekt an der reihe ist.

## Teil B - Typen und Ausdrücke (20 Punkte)

Gib jeweils den Typ an.
```cpp
char c;
int i;
double d;
int* p;
```
Antwort:
- char c -> Character, einzelnes symbol
- int i -> 32 Bit ganzzahl
- double d -> gleitkommazahl
- int* p -> pointer, zeigt auf eine speicheradresse

### Aufgabe B1 (10p)
Antwort:
```cpp
'X'  // Character
42 // int
42.0 // double
&i // int*
*p // int
c + i // int
i + d // double
true && false // bool
```

### Aufgabe B2 (10p)
Gegeben:
```cpp
int func();
```

Bestimme den Typ von:
```cpp
func
func()
&func
```

Antwort:
```cpp
func  // func*
func() // int
&func // int
```

## Teil C - Bitoperationen (10 Punkte)
Gegeben:
```cpp
int x = 128;
```
Führe schrittweise aus:
```cpp
x |= 64;
x ^= 16;
x &= 192;
x >>= 2;
```

Antwort:
```cpp
x |= 64; // x = 192      10000000 | 01000000 = 11000000
x ^= 16; // x = 208      11000000 ^ 00010000 = 11010000
x &= 192; // x = 192     11010000 & 11000000 = 11000000
x >>= 2; // x = 48       11000000 >> 2 = 00110000
```

## Teil D - Kontrollfluss (10 Punkte)

```cpp
#include <iostream>

void recurse(int n){

    if(n <= 0)
        return;

    std::cout << n << " "; // 6 -

    recurse(n-2); // 4 - 2

    std::cout << n << " "; // 2 - 4 - 6
}

int main(){
    recurse(6);
}
```

Antwort:
```cpp
Ausgabe: 6 4 2 2 4 6
```

## Teil E - Datenrepräsentation (10 Punkte)
### Aufgabe E1 (5p)

Antwort:
Pascal Strings sind einfacher zu verwenden, verbrauchen aber immer 1 byte mehr als C String. C String verbrauchen nur so viel wie in ihnen drinne steckt, aber sie sind schwieriger zu benutzen.

### Aufgabe E2 (5p)
Antwort: 49

## Teil F - Objektorientierung (20 Punkte)
Gegeben:
```cpp
class Shape{
public:
    virtual void draw();
};

class Circle : public Shape{
public:
    void draw() override;
};
```

### Aufgabe F1 (4p)
Antwort:
```cpp
Shape s; // erlaubt, insofern virtual void draw() nicht = 0
Circle c; // erlaubt

Shape* ps; // erlaubt, insofern virtual void draw() nicht = 0
Circle* pc; // erlaubt
```

```cpp
ps = &s;  // funktioniert
ps = &c;  // funktioniert
pc = &s;  // funktioniert
pc = &c;  // funktioniert
```

### Aufgabe F2 (6p)
Antwort: Es wird die Implementation von draw() der Circle Klasse ausgeführt, weil der Pointer auf einen Adressbereich eines Circle objektes zeigt.

### Aufgabe F3 (5p)
Antwort: Weil Circle eigene Member variablen besitzen könnte und diese potenziell selbst verwalten muss. Durch virtual kann Circle den Dekonstruktor von Shape überschreiben und eigene verwaltungen anfügen.

### Aufgabe F4 (5p)
Antwort: Man kann alle Child Objekte von Shape über Shape steuern, statt immer überprüfen zu müssen, welches objekt wozu gehört.

## Teil G - Konstruktoren und Lebenszyklus (25 Punkte)

### Aufgabe G1 (15P)
```cpp
#include <iostream>

class Base{
public:
    Base(){
        std::cout << "+B ";
    }

    ~Base(){
        std::cout << "-B ";
    }
};

class Mid : public Base{
public:
    Mid(){
        std::cout << "+M ";
    }

    ~Mid(){
        std::cout << "-M ";
    }
};

class Derived : public Mid{
public:
    Derived(){
        std::cout << "+D ";
    }

    ~Derived(){
        std::cout << "-D ";
    }
};

int main(){
    Derived d;
}
```

- Ausgabe?
- Reihenfolge Konstruktoren?
- Reihenfolge Destruktoren?
#### Antwort:
Ausgabe: +B +M +D -B -M -D
Reihenfolge Konstruktoren: Base -> Mid -> Derived
Reihenfolge Destruktoren: Base -> Mid -> Derived

### Aufgabe G2 (10P)
```cpp
class Base{
public:
    Base(int a);
};

class Derived : public Base{

private:
    int b;

public:
    Derived(int aa,int bb);
};
```

Konstruktor Implementation:
Antwort:
```cpp
Derived::Derived(int aa, int bb) : (int a = aa){
}
```

## Teil H - Value Types (20 Punkte)

Gegeben:
```cpp
class Buffer{

private:
    int* data;

public:

    Buffer(){
        data = new int[100];
    }

    ~Buffer(){
        delete[] data;
    }
};
```

### Aufgabe H1 (5p)
Antwort: Bei Buffer a und Buffer b zeigt die variable `data`auf die selbe speicheradresse.

### Aufgabe H2 (5p)
Antwort: Rule of Three

### Aufgabe H3 (10p)
Antwort: Destruktor, Assignment Operator, Copy konstruktor

## Teil I - Parsing (15 Punkte)

Gegeben:
```cpp
DIGIT ::= '0'|'1'|'2'|'3'|'4'|'5'|'6'|'7'|'8'|'9'

NUMBER ::= DIGIT { DIGIT }
```

### Aufgabe I1 (5p)
Antwort:
```cpp
1  //gültig
123 //gültig
0005 //gültig
A12 //nicht gültig
12A // nicht gültig
```

### Aufgabe I2 (5p)
Antwort:
```cpp
| // or
{} // any amount of following
```

### Aufgabe I3 (5P)
Antwort: Weil sie alle subfunktionen sind, welche von einer hauptfunktion verwendet werden um das tatsächlich parsing vorzunehmen.

## Bonusaufgabe
```cpp
class X{
public:

    X(){
        std::cout << "C ";
    }

    X(const X&){
        std::cout << "CC ";
    }

    X& operator=(const X&){
        std::cout << "A ";
        return *this;
    }

    ~X(){
        std::cout << "D ";
    }
};

int main(){

    X a;

    X b = a;

    X c;

    c = b;
}
```

Antwort: X() -> X(const X&) -> X() -> X& operator=(const X&)
