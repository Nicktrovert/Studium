Ja. Wenn du diese Prüfung sauber lösen kannst, bist du für Links Klausur vermutlich deutlich über dem Durchschnitt.

---

# CPP Level C – Endgegnerprüfung

**Regeln**

- Keine Hilfsmittel
    
- Antworten begründen
    
- Bei Codefragen immer erklären, warum
    
- Punkte insgesamt: 100
    

---

# Teil A – Datendarstellung & Bitoperationen (15P)

## A1 (3P)

Wandle um:

1. `11101011₂` → Dezimal
   > 1+2+8+32+64+128 = 235
    
2. `235₁₀` → Binär
   > 11101011
    
3. `0xAF` → Binär
   > 1001 1111
    
4. `10110110₂` → Hex
   > 0xB6
    

---

## A2 (4P)

Gegeben:

```cpp
unsigned char x = 0b10110010;
```

Berechne:

```cpp
x >> 3 // 1011 0010 >> 3 = 0001 0110 = 22
```

und

```cpp
x << 2 // 1011 0010 << 2 = 1100 1000 = 200
```

als

- Binär
    
- Dezimal
    

---

## A3 (4P)

Gegeben:

```cpp
unsigned char flags = 0b01010100;
```

Welche Bits sind nach den folgenden Operationen gesetzt?

```cpp
flags |= 0b00001010; // 0101 0100 | 0000 1010 = 0101 1110
flags ^= 0b00110000; // 0101 1110 ^ 0011 0000 = 0110 1110
flags &= 0b01111110; // 0110 1110 & 0111 1110 = 0110 1110
```

Endwert?

> 0110 1110 >  2+4+8+32+64 = 96 + 14 = 110

---

## A4 (4P)

Implementiere mit Bitoperationen:

1. Bit Nr. 5 setzen
   > x |= 0010 0000
    
2. Bit Nr. 5 löschen
   > x &= 1101 1111
    
3. Bit Nr. 5 invertieren
   > x ^= 0010 0000
    
4. Prüfen ob Bit Nr. 5 gesetzt ist
   > x & (1 << 4)
    

---

# Teil B – Datentypen & Speicher (10P)

## B1 (4P)

Erkläre den Unterschied zwischen:

```cpp
char c = '5'; // 53
```

und

```cpp
int i = 5; // 5
```

im Speicher.

> der char speichert eine zahl, des ASCII Wertes.
> der int speichert die zahl selbst

ASCII-Wert?
> 53

---

## B2 (3P)

Nenne jeweils zwei Vor- und Nachteile von:

- C-Strings
  > Null-Terminiert 	
    
- Pascal-Strings
  > Speichert die länge
    

---

## B3 (3P)

Was wird gespeichert?

```cpp
char text[] = "Hallo"; // {'H', 'a', 'l', 'l', 'o', '\0'}
```

Zeichne den Speicherinhalt.

---

# Teil C – Structs & Arrays (8P)

## C1 (4P)

Gegeben:

```cpp
struct Student{
    std::string name;
    int matrikel;
};
```

Definiere:

1. einen Studenten
   ```cpp
   Student s;
   s.name = "Patrick";
   s.matrikel = 756236;
   ```
    
2. ein Array aus 10 Studenten
   ```cpp
   Student s[10];
   ```
    
3. Zugriff auf Matrikelnummer des dritten Studenten
   ```cpp
   s[2].matrikel;
   ```
    

---

## C2 (4P)

Was gibt das Programm aus?

```cpp
struct Point{
    int x;
    int y;
};

int main(){
    Point p = {3,4}; // erstellung eines Structs mit x = 3 und y = 4

    Point arr[2]; // erstellung einer Array von Points mit 2 elementen

    arr[0] = p; // element 1 = Point p

    arr[1] = {5,6}; // element 2 = neuer struct mit x = 5 und y = 6

    std::cout << arr[0].x
              << arr[1].y;
}
```

> 3 6

---

# Teil D – Funktionen & Operator Overloading (12P)

## D1 (4P)

Was ist der Unterschied zwischen:

```cpp
Deklaration
```

> Dem Compiler mitteilen, dass die Funktion existiert.

und

```cpp
Definition
```

> Implementation. Wie die Funktion funktioniert.

einer Funktion?

Beispiel angeben.

```cpp
int foo(); // Deklaration

...

int foo() {   // Definition
  ...
}
```

---

## D2 (4P)

Warum ist das ungünstig?

```cpp
RationalNumber addRational(
    RationalNumber a,
    RationalNumber b
);
```

Warum ist das besser?

```cpp
RationalNumber addRational(
    const RationalNumber& a,
    const RationalNumber& b
);
```

> Bei dem ersten wird der Copy Constructor von RationalNumber aufgerufen, bei dem Zweiten wird das Objekt durchgegeben und durch das `const` keyword, sicher und unveränderbar gemacht. Dies verhindert, dass falsch implementierte Copy Construtors ausgeführt werden oder daten falsch übergeben werden.

---

## D3 (4P)

Für welchen Operator würdest du jeweils eine Überladung implementieren?

1. Vergleich
   > Ja `Class operator=(const Class& b)`
    
2. Ausgabe mit cout
   > Nein
    
3. Addition
   > Ja `Class operator+(const Type& b)`
    
4. Zugriff per Index
   > Ja `Type operator[](const int& i)`
    

---

# Teil E – Value Types (12P)

## E1 (6P)

Gegeben:

```cpp
struct Number{
    int value;
};
```

Welche Funktionen fehlen, damit sich der Typ wie ein regulärer Werttyp verhält?

> Zuweisungs operator, Copy Constructor, Destructor

Nenne:

- Rule of Zero
  > Nichts, alles default
    
- Rule of Three
  > Zuweisungs operator, Copy Constructor, Destructor
    
- Rule of Five
  > Move Constructor, Move assignment
    

---

## E2 (6P)

Erkläre den Unterschied zwischen:

```cpp
Number a = b;
```

> Es wird der Copy Constructor aufgerufen
> es wird ein neues objekt von Number erstellt mit den werten von `b` und in `a`gespeichert

und

```cpp
a = b;
```

> Es wird der Zuweisungs operator aufgerufen
> Das bestehende objekt `a` kriegt das objekte `b` zugewiesen

Welche Funktion wird jeweils aufgerufen?

---

# Teil F – Konstruktoren & Lebenszyklus (15P)

## F1 (5P)

Was wird ausgegeben?

```cpp
struct A{
    A(){std::cout<<"A";}
    ~A(){std::cout<<"a";}
};

int main(){
    A x;
}
```

> Aa

---

## F2 (5P)

Was wird ausgegeben?

```cpp
struct A{
    A(){std::cout<<"A";}
    ~A(){std::cout<<"a";}
};

struct B{
    A a;
    B(){std::cout<<"B";}
    ~B(){std::cout<<"b";}
};

int main(){
    B x;
}
```
> ABba

Konstruktor:
Base Member -> Base Klasse -> Derived Member -> Derived Klasse
Destruktor:
`Inverse`
Derived Klasse -> Derived Member -> Base Klasse -> Base Member

---

## F3 (5P)

Was wird ausgegeben?

```cpp
struct Base{
    Base(){std::cout<<"Base";}
    virtual ~Base(){std::cout<<"~Base";}
};

struct Derived : public Base{
    Derived(){std::cout<<"Derived";}
    ~Derived(){std::cout<<"~Derived";}
};

int main(){
    Base* p = new Derived();

    delete p;
}
```
> Base Derived ~Derived ~Base

---

# Teil G – Vererbung & OOP (12P)

## G1 (4P)

Erkläre:

- Klasse
  > Ein Bauplan für ein Objekt mit Members, Methoden und Konstruktor/en
    
- Objekt
  > Das Erzeugnis aus einer Klasse/Struct, beinhaltet Daten sowie Funktionen
    
- Methode
  > Eine Funktion innerhalb einer Klasse
    
- Vererbung
  > Eine Klasse kann ein `Child` oder `Parent` einer anderen Klasse sein und so ihre Daten übernehmen/weitergeben.
    

---

## G2 (4P)

Warum ist diese Methode abstrakt?

```cpp
virtual int payload() = 0;
```

> Weil sie nicht definiert ist. "virtual" und " = 0". sie wird in einer `Child` Klasse definiert.

Welche Konsequenz hat das?

> Über die Objekte der Klasse in der `payload` = 0 ist, kann man die Methode nicht ausführen.

---

## G3 (4P)

Was passiert hier?

```cpp
Car* c = new Car(); // es wird ein Objekt von Car erstellt

Vehicle* v = c; // Es wird ein Objekt von Vehicle erstellt und das Objekt der Child klasse Car wird diesem Objekt zugewiesen
```

Warum ist das erlaubt?

> Weil Car ein `Child` von Vehicle ist. `Car is-a Vehicle`.

---

# Teil H – Polymorphie & Fallen (8P)

## H1 (4P)

Was wird ausgegeben?

```cpp
struct Base{
    virtual void print(){
        std::cout<<"Base";
    }
};

struct Derived : Base{
    void print() override{
        std::cout<<"Derived";
    }
};

int main(){
    Base* p = new Derived();

    p->print();
}
```

> Derived

---

## H2 (4P)

Object Slicing:

```cpp
void foo(Base b){
    b.print();
}

Derived d;

foo(d);
```

Erkläre exakt:

1. Was passiert?
    
2. Warum?
    
3. Welcher Teil geht verloren?
    
> d wird zu foo als parameter übergeben. Da foo ein Base verlangt, wird der Copy-Constructor von Base aufgerufen und das Objekt d wird dort reingegeben. Es wird ein neues Base objekt innerhalb der foo Klasse benutzt. Der Derived teil geht verloren.

---

# Teil I – Parser & Grammatik (8P)

## I1 (4P)

Gegeben:

```text
DIGIT ::= '0' | '1' | ... | '9'

DIGITS ::= DIGIT (DIGIT)*
```

Welche der folgenden Strings sind gültig?

```text
123 //gültig
0 // gültig
0005 // gültig
12a // nicht gültig
a12 // nicht gültig
```

---

## I2 (4P)

Erkläre die Bedeutung von:

```text
[] // optional (0 oder 1 mal)
() // Subregel für anwendung von */+
* // 0 oder mehr von vorstehendem Element
+ // 1 oder mehr von vorstehendem Element
| // Oder
::= // Definition einer Grammatik regel
```

in EBNF.

---

# Teil J – Hardcore-Mix (10P)

## J1 (5P)

Was wird ausgegeben?

```cpp
struct A{
    A(){std::cout<<"A";} // Constructor
    A(const A&){ // Copy Constructor
        std::cout<<"C";
    }
};

void foo(A a){ // Parameterübergabe = Copy (Außer Ref &)
}

int main(){
    A x;

    foo(x);
}
```

> AC

---

## J2 (5P)

Welche Konstruktoren / Operatoren werden aufgerufen?

```cpp
Byte a;

Byte b(5);

Byte c = b;

a = c;
```

Nenne die Reihenfolge exakt.

> Default Konstruktor `Byte()`
> Konstruktor mit int `Byte(int x)`
> Copy Construktor `Byte(const Byte& b)`
> Assignment Operator `operator=(const Byte& b)`

---

# Bonus – Professor-Link-Falle (nicht bewertet)

Was ist an folgendem Code problematisch?

```cpp
class Base{
public:
    ~Base(){}
};

class Derived : public Base{
public:
    ~Derived(){
        delete data;
    }

private:
    int* data;
};

Base* p = new Derived();

delete p;
```

- Was passiert?
    
- Warum?
    
- Wie behebt man es?
    
> Der Destructor ist nicht virtual. Wenn `delete p` wird der destructor von Derived nicht aufgerufen, da die funktion durch das fehlen von virtual zur compilezeit ausgewäht wird und der Compiler nicht weiß, das p ein objekt von Derived sein könnte, und `data`nicht gelöscht. Memory Leak. Man muss `~Base(){}` zu `virtual ~Base() {}` ändern.

---

## Bewertung

```text
95–100  → 1,0 Niveau
85–94   → sichere 1.x
70–84   → gute 2
55–69   → wahrscheinlich bestanden
40–54   → kritisch
<40     → nochmal Materialpakete durcharbeiten
```

Die Prüfung deckt praktisch alles ab, was in den Materialpaketen zu Datendarstellung, Value Types, Operator Overloading, OOP, Vererbung, Konstruktoren/Destruktoren, Polymorphie, Object Slicing, Strings, Parsern und Bitoperationen vorkommt.

Wenn du die komplett bearbeitest, korrigiere ich sie anschließend wie ein Prüfer und vergebe Punkte.