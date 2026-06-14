## virtual
### V1
Welche Ausgabe?
```cpp
class Base{
public:
    void foo(){
        std::cout << "Base";
    }
};

class Derived : public Base{
public:
    void foo(){
        std::cout << "Derived";
    }
};

int main(){

    Derived d;

    Base* p = &d;

    p->foo();
}
```

> Base

### V2
Welche Ausgabe?
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

> Derived

### V3
Welche Ausgabe?

```cpp
class Base{
public:
    virtual void foo(){
        std::cout << "Base";
    }
};

class Derived : public Base{
};

int main(){

    Derived d;

    Base* p = &d;

    p->foo();
}
```
> Base

### V4
Welche Ausgabe?

```cpp
class Base{
public:
    virtual void foo(){
        std::cout << "Base";
    }
};

class Derived : public Base{
public:
    void foo(){
        std::cout << "Derived";
    }
};

int main(){

    Base* p = new Derived();

    p->foo();
}
```

> Derived

### V5
Welche Ausgabe?
```cpp
class Base{
public:
    virtual ~Base(){
        std::cout << "Base";
    }
};

class Derived : public Base{
public:
    ~Derived(){
        std::cout << "Derived";
    }
};

int main(){

    Base* p = new Derived();

    delete p;
}
``` 

> DerivedBase

### V6
Welche Ausgabe?
```cpp
class Base{
public:
    ~Base(){
        std::cout << "Base";
    }
};

class Derived : public Base{
public:
    ~Derived(){
        std::cout << "Derived";
    }
};

int main(){

    Base* p = new Derived();

    delete p;
}
```

> Base

## Copy Constructor

### C1
Wie oft wird der Copy Constructor aufgerufen?

```cpp
class X{
public:
    X(){}

    X(const X&){
        std::cout << "COPY ";
    }
};

int main(){

    X a;

    X b = a;
}
```

1 Mal
> COPY 

### C2
Wie oft wird der Copy Constructor aufgerufen?
```cpp
class X{
public:
    X(){}

    X(const X&){
        std::cout << "COPY ";
    }
};

void foo(X x){
}

int main(){

    X a;

    foo(a);
}
```

1 Mal
> COPY

### C3
Wie oft wird der Copy Constructor aufgerufen?
```cpp
class X{
public:
    X(){}

    X(const X&){
        std::cout << "COPY ";
    }
};

int main(){

    X a;

    X b(a);

    X c = b;
}
```

2 Mal
> COPY COPY

### C4
Copy Constructor oder Assignment operator?
```cpp
X a;

X b = a;
```
Copy Constructor

### C5
Copy Constructor oder Assignment operator?
```cpp
X a;
X b;

b = a;
```
Assignment operator

### C6
Welche Ausgabe?
```cpp
class X{
public:

    X(){
        std::cout << "C ";
    }

    X(const X&){
        std::cout << "CC ";
    }

    ~X(){
        std::cout << "D ";
    }
};

void foo(X x){
}

int main(){

    X a;

    foo(a);
}
```

> C CC D D

### C7
Welche Ausgabe?
```cpp
class X{
public:

    X(){
        std::cout << "C ";
    }

    X(const X&){
        std::cout << "CC ";
    }

    ~X(){
        std::cout << "D ";
    }
};

int main(){

    X a;

    X b = a;
}
```

> C CC D D

## Initializer Lists

### I1
Welche Version ist besser?
```cpp
Point(int x)
: _x(x)
{
}
```
oder
```cpp
Point(int x){
    _x = x;
}
```
Warum?

Version 1 ist besser, weil die member variablen direkt mit Initializiert werden. Bei Version 2 wird erst das objekt initialisiert, und dann werden die Variablen zugewiesen. Dies ist wichtig für `const` typen und  `referenzen`.

### I2
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
    Derived(int a,int b);
};
```

```cpp
Derived::Derived(int a, int b) : Base(a), y(b) 
{
}
```

### I3
Warum funktioniert das nicht?
```cpp
class Test{

private:
    const int x;

public:

    Test(int a){
        x = a;
    }
};
```

Weil x `const`ist und somit nur bei der initialisierung gesetzt werden kann, eine zuweisung ist nicht möglich.

### I4
Warum funktioniert das nicht?
```cpp
class Test{

private:
    int& r;

public:

    Test(int& x){
        r = x;
    }
};
```

Weil r `referenz` ist und eine referenz darf nach initialisierung nicht `undefined` sein, er muss bei der initialisierung zugewiesen werden.

### I5
Wie muss der Konstruktor aussehen?
```cpp
class Test{

private:
    const int x;
    int& r;

public:
    Test(int a,int& b);
};
```

```cpp
Test::Test(int a, int& b) : x(a), r(b) {
}
```

### I6
Welche Reihenfolge wird verwendet?
```cpp
class Example{

private:
    int a;
    int b;

public:

    Example(int x,int y)
    : b(y), a(x)
    {
    }
};
```
Wer wird zuerst initialisiert?
```
a oder b?
```

b wird zuerst initialisiert, dann a.

## Bosskampf
Welche Ausgabe?
```cpp
class Base{
public:

    Base(){
        std::cout << "B ";
    }

    Base(const Base&){
        std::cout << "BC ";
    }

    virtual ~Base(){
        std::cout << "b ";
    }

    virtual void foo(){
        std::cout << "BF ";
    }
};

class Derived : public Base{
public:

    Derived(){
        std::cout << "D ";
    }

    Derived(const Derived&){
        std::cout << "DC ";
    }

    ~Derived(){
        std::cout << "d ";
    }

    void foo() override{
        std::cout << "DF ";
    }
};

void test(Base obj){
    obj.foo();
}

int main(){

    Derived d;

    test(d);
}
```
> B D DC DF d b d b