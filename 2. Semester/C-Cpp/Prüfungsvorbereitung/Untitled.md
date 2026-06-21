### Rule of Zero

```cpp
Class MyClass{
	MyClass();
};
```

### Rule of Three

- Copy Constructor
- Assignment Operator
- Destructor

Wenn eins davon -> Alle 3 Implementieren

MyClass.hpp
```cpp
Class MyClass{
	MyClass(); // Constructor
	~MyClass(); // Destructor
	
	MyClass(const MyClass& mc); // Copy
	
	MyClass operator=(const MyClass& mc); // assignment
	
	private:
		int* data;
};
```

main.cpp
```cpp
int main(){
	MyClass a; // Constructor
	
	MyClass b = a; // Copy Constructor
	
	MyClass c; // Constructor
	
	c = a;  // assignment operator
}
// Destructor a, b, c
```

MyClass.cpp
```cpp
#include "MyClass.hpp"

MyClass::MyClass(const MyClass& mc) {
	*data = *mc.data
}

MyClass::operator=(const MyClass& mc) {
	*data = *mc.data
}
```

### Rule of Five

- Copy Constructor
- Assignment Operator
- Destructor
  +
- Move Constructor
- Move Assignment

Resourceneffizienz.

```cpp
MyClass a;

MyClass b = std::move(a);
```


```cpp

class/struct string{
	char* data;
	
	... FUnktionen..
	
}

int main(){
	 char* a = "afs";
	 std::string a = "afs";
}
```