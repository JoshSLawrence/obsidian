---
tags:
  - ComputerScience/Cpp
---
# C++ Structures and Classes

## Structures

A structure, or `struct` is a akin to a more primitive class.

Struct Example:

```C++
struct Date {
	int month;
	int day;
	int year;
};

struct Person {
	string first_name;
	string last_name;
	int age;
	double pay_rate;
	Date birthday;
};

// Declare the struct
Person person;

// Set member variables
person.age = 28;
person.birthday.year = 1995;
```

Variables in structs are called *member variables* and their values, *member values*. 

The name of a struct in a struct definition is called the *struct tag*. 

Structs may contain other structs as member variables, this is known as *hierarchical structures*.

Lastly, a struct may contain *structure variables.* A structure variable is defined between the finally closing closing-brace `}` and the terminating semi-colon `;`

```C++
struct StructTag {
	int mamber_variable1;
	double mamber_variable2;
} structure_variable1, structure_variable2;
```

Once a struct is defined it can be used as a return value in a function. Additionally, [[Computer Science - General Terms#Call by Reference|a function can use structs as call-by-reference or call-by-value parameters]].

### Referencing Structure Member Values

Structure member variables can be called using the `.` operator.

```C++
#include <iostream>

using namespace std;

struct Example {
	int number;
};

Example my_struct;

cout << my_struct.number;
```

If a struct contains a member variable that is a struct, the member variables of this inner struct can also be accessed with the `.` operator:

```C++
cout << my_struct.sub_struct.member_var;
```

### Structure Initialization

Struct member values can be set in series as the struct is initialized:

```C++
struct MyStruct {
	int whole_number;
	double decimal_number;
};

MyStruct example = {12, 12.50};
```

## Classes

Classes are similar structs but they contain member functions and member data. Classes are the cornerstone of object-oriented programming.

An initialized class is called an *object*.

### Class declaration

```C++
class DayOfYear {
public: 
	void output(); // Function prototype
	int month;
	int day;
};

int main() {
	//...
}

void DayOfYear::output() {
	// Function definition
}
```

- Order function declarations before variables
- The function declaration is called *prototype*
- The actual function is commonly defined elsewhere

	Note: a class member function definition *must* contain the *scope resolution operator* `::` to related the function definition to the class:
	
		DayOfYear::output()

### Referencing Class Member Values

Similar to [[Cpp - Structures and Classes#Referencing Structure Member Values|structures]], a class's member variables and functions can be called using the `.` operator.

```C++
DayofYear my_class;
my_class.month = 12;
my_class.output();
```

### Class Private Members

A big point of object-oriented programming is to abstract, or *encapsulate* the member function definitions and data away from the programmer.

By setting member variables and functions to `private`, they can only be referenced within the the class and it's member function definitions. The private member cannot be referenced externally.

```C++
class DayOfYear {
public: 
	void output(); // Function prototype
	int setMonth(); // Mutator
	int getDay; // Accessor
private:
	int month;
	int day;
};

int main() {
	// Cannot call the `month` member variable
}

void DayOfYear::getDay() {
	// Can call the `month` member variable
}
```

### Class Mutator Functions

Mutators, or "setter" functions, are public functions that enable private member values to be changed externally.

### Class Accessor Functions

Accessor, or "getter" functions, are public functions that enabled private member values to be returned externally.


## So, What's the Difference?

Ignoring syntax differences, structures and classes are largely the same. A struct can have private members and so on.

A struct will default its members to ***public*** if `public:` or `private:` is not declared.

A class will default its members to ***private*** if `public:` or `private:` is not declared.