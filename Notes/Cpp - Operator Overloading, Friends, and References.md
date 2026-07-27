---
tags:
  - Cpp
---
## Operator Overloading

Operator overloading is similar to function overloading in that you can define a different version of the same function by changing the parameters the function takes in.

In the case of operator functions, the filled parameters at runtime are call operands instead of arguments.

Operators are commonly viewed as the symbols, `+`, `-`, `*`, `/`, `%`, `<<`, `>>`, etc. These operators are still just functions under the hood.

- e.g. `+` can really be viewed as `add(arg1, arg2)`.
- The action of overloading these functions, if operator overloading.

The benefit to operator overloading is the ability to define how an operator will affect objects. 

By default operation on class objects, `object1 + object2` will do nothing, but through operator overloading we can enable common operators to still intuitively function against these objects.

### Problematic Operator Overloading

The `&&`, `||`, and comma operator will not perform as expected when overloaded. While this is not a rule, it is very common, as such it is best to avoid overloading these operators.

## Automatic Type Conversion

Automatic type conversion is enabled by having constructors available in your class definition to handle a combination of operations. For example:

```C++
MyClass MyObject1(1, 2), MyObject2;
MyObject2 = MyObject1 + 25;
```

Assuming the `+` operator is overloaded as a member function, then we have only defined how to add an object to an object in this class a definition. We have not defined how to add an object and an integer as implied by `MyObject + 25`.

Despite lacking this definition, if a constructor exists in the class definition of `MyClass` which instantiates a `MyClass` object with a single argument of type `int`, then `25` will be converted to a `MyClass` object at the time of execution. 

So, in this suggested case `MyObject2 = MyObject1 + 25;` is valid and will correctly leverage the overloaded `+` implementation to return a result because you are still adding 2 `MyClass` objects.

### Limitations of Automatic Type Conversion

Automatic type Conversion runs into problems if the overloaded operator function is implemented as a member function. For example:

```C++
const MyClass MyClass::operator +(const MyClass& secondOperand) const
{
	...
}
```

To even call this overloaded operator the caller must *already* be a `MyClass` object. 

Due to this fact, the previous example of `MyObject2 = MyObject1 + 25;` is valid but `MyObject2 = 25 + MyObject1;` would not be valid. 

The first operand is the caller, and `25` would be of type `int` at the time of the call.

An operator can be overloaded with no calling object if the function is implemented as a non-member function, or as a *Friend Function*.

## Friend Functions

A friend function of a class is not a member function of said class, *but* it can access private members of the associated class.

```C++
// Declaration in the class definition
friend const MyClass operator +(const MyClass& Operand1, 
								const MyClass& Operand2);

// Implementation outside of the class definition
const MyClass operator +(const MyClass& Operand1, const MyClass& Operand2)
{
	...
}
```

#### Quick Notes:

- The function must be declared in the class definition with `friend` prefixed.

- Both operands are present as parameters in the function declaration as there is no implied calling operand.

- Unlike a member function, the qualifier `MyClass::` is not required in front of `operator` in the function definition.

- Both operands private member variables can be referenced in the function definition.

## Friend Classes

Friend classes are similar to friend function in that a friend class can access private members of the class it is a friend to.

#### Guidelines for a friend class relationship:

- The friend class must be declared prior the class it is a friend of. This is called a **Forward Declaration**.

- The friend class must be declared as a friend in the class it is a friend of.

Example:

```C++
class B; // forward declaration

class A
{
	...
	friend class B; // friend declaration
	...
};

class B
{
	...
};
```

## References

A reference is is a storage location.

```C++
int robert;
int& bob = robert;
```

In this above example, `robert` is an integer that can contain a value of type `int`. `bob` is a reference to the the integer `robert` as denoted by the `&` symbol.

This means that value of `bob` is not of type `int`, but rather a memory address. 

This address can be used to return and modify the data that exists in the given address, which in this case is the value of `robert`.

#### Quick Notes:

- The symbol `&` must be present in a function declaration and the the function definition if a reference is being used.

-  A function returning a reference, must precisely return a reference not an expression that may contain a reference.

- A function should not return a reference to a local variable, as once the function execution ends that local variable is destroyed.

