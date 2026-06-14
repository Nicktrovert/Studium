## Vererbung & Pointer
### A1

Geg.
```cpp
class Animal {};
class Dog : public Animal {};
```

Welche Zuweisungen sind erlaubt?
```cpp
Animal a; // erlaubt, gewöhnliche objekt erstellung
Dog d; // erlaubt, gewöhnliche objekt erstellung

Animal* pa; // Erlaubt, Objekt erstellung
Dog* pd; // Erlaubt, Objekt erstellung

pa = &a; // Erlaubt, selber typ
pa = &d; // Erlaubt, stammt davon ab.
pd = &a; // nicht erlaubt, fehlende implementationen
pd = &d; // erlaubt, selber typ.
```
Begründe jede Antwort kurz.

### A2
```cpp
class Shape{
public:
    virtual void draw(){
        std::cout << "Shape";
    }
};

class Circle : public Shape{
public:
    void draw() override{
        std::cout << "Circle";
    }
};

int main(){

    Shape* p = new Circle();

    p->draw();
}
```

Fragen:
1. Welche Ausgabe?
   > Circle
2. Warum?
   Weil die `draw` funktion aus Shape von Circle überschrieben wird.
3. Was würde passieren, wenn `virtual`entfernt wird?
   Es würde einen fehler wegen doppelter implementation geben.

### A3
Geg.
```cpp
class Base{};
class Derived : public Base{};
```
Ist erlaubt?
```cpp
Base* p = new Derived();
```
Ja, Derived ist ein child von Base.


Ist erlaubt?
```cpp
Derived* p = new Base();
```
Nein, Base ist ein parent von Derived, Base implementiert nicht alle funktionen die Derived besitzt.

### A4
Geg.
```cpp
class Shape{
public:
    virtual ~Shape(){
        std::cout << "Shape";
    }
};

class Circle : public Shape{
public:
    ~Circle(){
        std::cout << "Circle";
    }
};

int main(){

    Shape* p = new Circle();

    delete p;
}
```
Welche Ausgabe entsteht?
> CircleShape

### A5
Geg.
```cpp
class Base{
public:
    virtual void foo(){
        std::cout << "Base";
    }
};

class Derived : public Base{
public:
    void foo() override{
        std::cout << "Derived";
    }
};

int main(){

    Derived d;

    Base* p = &d;

    p->foo();
}
```
Welche Ausgabe?
> Derived

Warum?
Weil Derived die foo funktion aus Base überschreibt.

## Konstruktoren & Destruktoren
### B1
Welche Ausgabe?
```cpp
class A{
public:
    A(){ std::cout << "+A "; }
    ~A(){ std::cout << "-A "; }
};

int main(){
    A a;
}
```
> +A-A


### B2
Welche Ausgabe?
```cpp
class A{
public:
    A(){ std::cout << "+A "; }
    ~A(){ std::cout << "-A "; }
};

class B : public A{
public:
    B(){ std::cout << "+B "; }
    ~B(){ std::cout << "-B "; }
};

int main(){
    B b;
}
```

> +A+B-B-A

### B3
Welche Ausgabe?
```cpp
class A{
public:
    A(){ std::cout << "+A "; }
    ~A(){ std::cout << "-A "; }
};

class B : public A{
public:
    B(){ std::cout << "+B "; }
    ~B(){ std::cout << "-B "; }
};

class C : public B{
public:
    C(){ std::cout << "+C "; }
    ~C(){ std::cout << "-C "; }
};

int main(){
    C c;
}
```

> +A+B+C-C-B-A

### B4
Welche Ausgabe?
```cpp
class A{
public:
    A(){ std::cout << "+A "; }
    ~A(){ std::cout << "-A "; }
};

void foo(){
    A a;
}

int main(){

    foo();

    std::cout << "END ";
}
```

> +A-AEND 
### B5
Welche Ausgabe?
```cpp
class A{
public:
    A(){ std::cout << "+A "; }
    A(const A&){
        std::cout << "*A ";
    }
    ~A(){
        std::cout << "-A ";
    }
};

void foo(A a){
}

int main(){

    A a;

    foo(a);
}
```

> +A* A-A

## Initializer Lists
### C1
Vervollständige:
```cpp
class Base{
public:
    Base(int x);
};

class Derived : public Base{

private:
    int y;

public:
    Derived(int a,int b) : Base(a), y(b);
};
```

### C2
Warum ist das besser?
```cpp
Point(int x)
: _x(x)
{
}
```
als 
```cpp
Point(int x){
    _x = x;
}
```

Man bekommt einen fehler, wenn man werte übersieht und es ist lesbarer/kompakter

### C3
Warum MUSS man Initializer Lists verwenden bei:
```cpp
const int x;
```
und
```cpp
int& r;
```
?

Weil es nicht veränderbare typen sind, also nach der Initialization kann man sie nicht neu zuweisen.

### Die fiese Klausuraufgabe
Welche Ausgabe entsteht?
```cpp
class Base{
public:
    Base(){
        std::cout << "B ";
    }

    ~Base(){
        std::cout << "b ";
    }
};

class Derived : public Base{
public:
    Derived(){
        std::cout << "D ";
    }

    ~Derived(){
        std::cout << "d ";
    }
};

int main(){

    Base* p = new Derived();

    delete p;
}
```

> BDb

Zusatfrage:
Ändert sich die Ausgabe, wenn `~Base()` als
```cpp
virtual ~Base()
```
deklariert wird?

Wenn ja, wie?

Die ausgabe ändert sich zu
> BDdb


