## Datentypen
### Primitive Typen
```cpp
bool    // true, false
char    // Zeichen
int     // Ganzzahl
long    // große Ganzzahl
double  // Kommazahl
``` 
### Literale
```cpp
42
3.14
true
false
'A'
"Hallo"
```
### Typumwandlung
Implizit:
```cpp
double d = 5;
```
Explizit:
```cpp
double d = 5.8;
int i = (int)d;
```

---
## Variablen
Deklaration + Initialisierung:
```cpp
int x = 5;
double pi = 3.14;
```
Zuweisung:
```cpp
x = 10;
```

---
## Referenzen
Alias für bestehende Variable:
```cpp
int x = 5;
int& r = x;

r = 10;
// x == 10
```
Parameterübergabe:
```cpp
void increment(int& x){
    x++;
}
```

---
## Boolesche Ausdrücke
Vergleichsoperatoren:
```cpp
==
!=
<
>
<=
>=
```
Logische Operatoren:
```cpp
&&
||
!
```
Beispiel:
```cpp
if(x > 0 && x < 10)
```

---
## Kontrollfluss
### if
```cpp
if(x > 0){
}
else{
}
```
### while
```cpp
while(x < 10){
    x++;
}
```
### for
```cpp
for(int i=0; i<10; i++){
}
```
### Rekursion
```cpp
int fak(int n){
    if(n <= 1)
        return 1;

    return n * fak(n-1);
}
```

---
## Funktionen
Definition:
```cpp
int add(int a, int b){
    return a+b;
}
```
Aufruf:
```cpp
int x = add(3,4);
```

---
## Arrays
Definition:
```cpp
int arr[5];
```
Zugriff:
```cpp
arr[0] = 10;
```
Letztes Element:
```cpp
arr[4]
```

---
## Structs
```cpp
struct Date{
    int day;
    int month;
    int year;
};
```
Verwendung:
```cpp
Date d;

d.day = 1;
d.month = 6;
d.year = 2026;
```

---
## Klassen
```cpp
class Person{
private:
    int age;

public:
    void setAge(int a){
        age = a;
    }
};
```
Objekt:
```cpp
Person p;
```

---
## Konstruktor:
```cpp
class Person{
public:
	Person(){
	}
};
```
Mit Parametern:
```cpp
Person(int a){
    age = a;
}
```

---
## Destruktor
```cpp
~Person(){
}
```
Wird automatisch beim Löschen aufgerufen.

---
## Vererbung
```cpp
class Animal{
};

class Dog : public Animal{
};
```
`Dog` erbt von `Animal`

---
## Virtuelle Methoden
```cpp
class Animal{
public:
    virtual void speak(){
    }
};
```
Überschreiben:
```cpp
class Dog : public Animal{
public:
    void speak() override{
    }
};
```

---
## Abstrakte Klassen
```cpp
class Animal{
public:
    virtual void speak() = 0;
};
```
Kann nicht instanziiert werden.

---
## Heap vs. Stak
### Stack
```cpp
Person p;
```
Automatisch erzeugt und gelöscht.
### Heap
```cpp
Person* p = new Person();
delete p;
```
Manuelles Löschen notwendig.

---

## Copy Constructor
```cpp
class X{
public:
    X(const X& other){
    }
};
```
Wird benutzt bei:
```cpp
X a;
X b = a;
```

---
## Assignment Operator
```cpp
class X{
public:
    X& operator=(const X& other){
        return *this;
    }
};
```
Benutzt bei:
```cpp
a = b;
```

---
## Rule of Zero / Three / Five
### Rule of Zero
Keine Ressourcen -> Compiler macht alles.
### Rule of Three
Wenn du einen eigenen Destructor brauchst (bspw. Pointer handling) dann brauchst du auch:
```cpp
Destructor
Copy Constructor
operator=
```
### Rule of Five
Zusätzlich für effiziente Ressourcenübergabe seit C++11:
```cpp
Move Constructor
Move Assignment
```

---
## Operator Overloading
Addition:
```cpp
MyType operator+(const MyType& rhs);
```
Vergleich:
```cpp
bool operator==(const MyType& rhs);
```

---
## Strings
C-String:
```cpp
char text[6] = "Hallo";
```
Nullterminiert:
```cpp
'H'
'a'
'l'
'l'
'o'
'\0'
```
C++ String:
```cpp
std::string text = "Hallo";
```

---
## Bitoperatoren
AND
```cpp
a & b
```
OR
```cpp
a | b
```
XOR
```cpp
a ^ b
```
NOT
```cpp
~a
```
Bits nach links schieben
```cpp
a << 1
```
Bits nach rechts schieben
```cpp
a >> 1
```

---

## Ein-/Ausgabe
Ausgabe:
```cpp
std::cout << "Hallo";
```
Eingabe:
```cpp
std::cin >> x;
```
Datei lesen:
```cpp
std::ifstream file("data.txt");
```
Datei schreiben:
```cpp
std::ofstream file("data.txt");
```

---
## Toolchain
```cpp
Editor
↓
Preprocessor
↓
Compiler
↓
Assembler
↓
Linker
↓
Executable
↓
Loader
↓
Programm läuft
```



## 5-Minuten-Merkblatt (Toolchain | Bitoperationen | Parsing)
```
TOOLCHAIN
Preprocessor → Compiler → Assembler → Linker → Loader

BITOPERATIONEN
&  AND
|  OR
^  XOR
~  NOT
<< links schieben (*2^n)
>> rechts schieben (/2^n)

PARSING
Token = kleinstes Symbol
Sequenz = A B C
Selektion = A | B
Iteration = { A }
CSV = Werte durch Komma getrennt
EBNF beschreibt erlaubte Eingaben
```
