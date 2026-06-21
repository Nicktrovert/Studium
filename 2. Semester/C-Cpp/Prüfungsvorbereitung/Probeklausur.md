Punkte: 100

### Aufgabe 1 - Kontrollfluss (10 Punkte)
Was wird ausgegeben?

```cpp
#include <iostream>

int main() {
    int x = 1;

    while(x < 5){
        if(x % 2 == 0)
            std::cout << x;
        x++;
    }

    return 0;
}
```

### Aufgabe 2 - Referenzen (10 Punkte)
Was ist der Wert von `a` nach dem Aufruf?
```cpp
void modify(int& x){
    x = x * 2;
}

int main(){
    int a = 7;
    modify(a);
}
```

### Aufgabe 3 - Structs (10 Punkte)
Gegeben:
```cpp
struct Student{
    int matrikelnummer;
    double note;
};
```
Erzeuge eine Variable `s` mit Matrikelnummer `12345` und Note `1.7`

### Aufgabe 4 - Klassen (10 Punkte)
Implementiere die Klasse:
```cpp
class Counter
```
mit
- privatem int `value`
- Methode `increment()`
- Methode `getValue()`

### Aufgabe 5 - Konstruktoren (10 Punkte)
Welche Ausgabe entsteht?
```cpp
#include <iostream>

class Test{
public:
    Test(){
        std::cout << "C";
    }

    ~Test(){
        std::cout << "D";
    }
};

int main(){
    Test t;
}
```

### Aufgabe 7 - Vererbung (10 Punkte)
Gegeben:
```cpp
class Animal{
public:
    void eat(){}
};

class Dog : public Animal{
};
```
Welche Methode besitzt ein Objekt vom Typ `Dog`?

### Aufgabe 8 - Virtual Functions (10 Punkte)
Was bewirkt `virtual`?
```cpp
virtual void speak();
```

### Aufgabe 9 - Copy Constructor (10 Punkte)
Welcher Konstruktor wird benutzt?
```cpp
MyClass a;
MyClass b = a;
```

### Aufgabe 10 - Operator Overloading (10 Punkte)
Implementiere den Vergleichsoperator.
```cpp
struct Point{
    int x;
    int y;
};
```
Zwei Punkte sind gleich, wenn x und y gleich sind.

### Bonusaufgabe (20 Punkte)
Analysiere die Aufgabe:
```cpp
#include <iostream>

class Base{
public:
    Base(){
        std::cout << "B";
    }

    ~Base(){
        std::cout << "b";
    }
};

class Derived : public Base{
public:
    Derived(){
        std::cout << "D";
    }

    ~Derived(){
        std::cout << "d";
    }
};

int main(){
    Derived x;
}
```
