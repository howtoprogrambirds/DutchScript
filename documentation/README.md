<a name="readme-top"></a>

<!-- PROJECT LOGO -->
<img src="../images/pattern 1.png">

# The DutchScript Language


DutchScript is based on the Dutch language. The aim of this programming language is to be able to code in (poor) Dutch an the "syntax order" is close to the C programming language with some "artistic fluff" to make it a bit more possible to write a Dutch sentence. 

Dutchscript includes:
* Object oriented
* Dynamic typing
* Automatic memory management (Garbage Collector)


## Table of Contents

- [Data Types](#data-types)
- [Expressions](#expressions)
  - [Arithmetic](#arithmetic)
  - [Comparison and equality](#comparison-and-equality)
  - [Logical operators](#logical-operators)
  - [Precedence and grouping](#precedence-and-grouping)
- [Statements](#statements)
- [Variables](#variables)
- [Control Flow](#control-flow)
- [Function](#function)
  - [Closures](#closures)
- [Classes](#classes)
  - [Instantiation and initialization](#instantiation-and-initialization)
  - [Inheritance](#inheritance)
- [The Standard Library](#the-standard-library)
- [Artistic Fluff](#artistic-fluff)


## Hello, DutchScript
Here's your very first taste of DutchScript:

```
// Your first DutchScript Program!
Zeg "Hallo Wereld".
```

<!-- ABOUT THE PROJECT -->
## Data Types
DutchScript is a small language with a few data types. 
  
#### Booleans
There are two boolean values, and each have a literal.

```
waarheid. // Not false.
leugen.   // Not true.
```
#### Numbers
DutchScript only has a wide range of integers but only has a double-precision floating point for decimal numbers.

```
1234.  // An integer.
12,34. // A decimal number.
```

#### Strings
The strings of DutchScript are, like most languages, enclosed in double quotes.

``` 
"Ik ben een string".  // I'm a string.
"".                   // The empty string.
"123".                // This ia a string, not a number.
```

#### NULL
This value "no value" and in Dutchscript it is

```
NIKS. // NULL or null or No value.
```


<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Expressions
The expressions of DutchScript has there common ways of expressing, and a literal of words (to make a dutch sentence).

### Arithmetic
DutchScript features the basic arithmetic operators you know.
```
voeg + toe.
trek - af.
vermenigvuldig * met.
gedeeld / door.
```

These arithmetic operators have their literals als in words.
```
voeg plus toe.            // plus = +.
trek min af.              // min  = -.
vermenigvuldig keer met.  // keer = *.
gedeeld deel door.        // deel = /.
```

One of the arithmetic operaters is both **infix** and **prefix**. The `-` operator can also be used negate a number.
```
-9.
```

All of these operators work on numbers, and it's an error to pass any other types to them. The exception is the `+` operator, you can also pass it two strings to concatenate them.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Comparison and equality
These expressions will return a Boolean result, we can compare numbers (only numbers) using these operators.
```
a <  b.             // Less than.
c <= d.             // Less than or equal.
e >  f.             // Greater than.
g >= h.             // Greater than or equal.
```

These expressions are as well in letter form.
```
a minder b.           // minder = <.
c kleiner d.          // kleiner = <=.
e meer f.             // meer = >.
g groter h.           // groter = >=.
```

We can also test two values of any kind for equality or inequality.
```
1 == 2.             //true.
"kat" != "hond".    //false.
3.12 == "pi".       //values of different types are never equivalent.
```

And in letter form.
```
1 hetzelfde 2.        //true.
"kat" anders "hond".    //false.
3.12 hetzelfde "pi".  //values of different types are never equivalent.
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Logical operators
The not operator, a prefix `niet` aka `!` returns `false` id its operand is true, and vice versa.
```
niet waarheid     // false.
niet leugen       // true.
```

The other two logical operators are control flow constructs in the guise of expressions. An `en` determines if two values are **both** true. It returns true if both operands are truthy and false otherwise
```
waarheid en leugen.   // false
waarheid en waarheid. // true
```

And an `of` expression determines if **either** of two values (or both) are true. If any of its arguments are true, it returns true, otherwise it returns false.
```
leugen of leugen.   // false.
waarheid of leugen. // true.
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Precedence and grouping
All of these operators have the same precedences and associativity that you'd expect coming from C. In cases where the precedence isn't what you want, you can use `()` to group stuff.
```
(2 + 4) * 5.
```

To keep it simple I didn't implemented bitwise, shift, modulo or conditional operators, maybe it will be added in the future.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Statements
You've seen a couple of kinds of statements already. The first one was.
```
Zeg "Hallo Wereld".
```

The `Zeg` statement evaluates a single expression and displays the result to the user. You've also seen some statements like this.
```
"een expressie".
```

A expression followed by a point `.` promotes the expression to statement-hood.

If you want to pack a series of statements where a single one is expected, you can wrap them in a block. Starting with a `:` and ending with a `!`.
```
:
  Zeg "eerste statement".
  Zeg "tweede statement".
!
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Variables
You declare variables using `de/De`, `het/Het` or `een/Een` statements. If you omit the initialzer `=` or `is`, the variable's value default to `NIKS`.
```
de ikBenEenVariable = "hier is mijn waarde".
DE variabel is 3.

het ikBenNIKS.
Het ikBenOokNIKS.

een waarde = "ham".
Een nogEenWaarde is "kaas".

```

Once declared you can, naturally, change the variable statement `de/De`, `het/Het` or `een/Een` or change it value.
```
het ontbijt = "bagels".
Zeg het ontbijt. // "bagels".
een ontbijt = "stokbrood".
Zeg het ontbijt. // "stokbrood".
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Control Flow
In addition to the logical operators to control the flow of the code. DutchScript lifts two statements bades on some condition.

An `als` statement executes one of the two statements based on some condition.
```
als (conditie) :
  Zeg "ja".
! anders :
  Zeg "nee".
!
```

A `totdat` loop executes the body repeatedly as long as the condition expression evaluates to true.
```
de a = 1.
totdat (a minder 10) :
  print a.
  a = a + 1.
!
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Function

A function call expression looks like this.
```
Roep het ontbijt 'bacon, eieren, toast'. // Roep = call expression, het ontbijt = function and '' are arguments.
```
You can also call a function passing anything to it.
```
Roep het ontbijt.
```

The way to define a custom function is with `Bekijk`.
```
Bekijk de som 'a, b':
  Zeg a + b.
!
```

The body of a function is always a block `: !`. Inside it, you can return a value using a `Geef` statement.
```
Bekijk de som 'a, b':
  Geef a + b.
!
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Closures

Functions are **first class** in DutchScript, which just means they are real values that you can get a reference to, store in variables, pass around, etc. This works:
```
Bekijk een paar 'a, b':
  Geef a + b.
!

Bekijk de identiteit 'a' :
  Geef a.
!

Zeg de indentiteit 'een paar '1,2''.
```

Since function declarations are statements, you can declare local functions inside another function:
```
Bekijk de buitenFunctie'' :
  Bekijk de lokaleFunctie'' :
    Zeg "ik ben lokaal".
  !
  Geef de lokaleFunctie.
!
```

If you combine local functions, first-class functions, and block scope, you run into this interesting situation.
```
Bekijk de geefTerugFunctie'' :
  de buitenkant = "buitenkant".
  
  Bekijk de binnenkant'' :
    Zeg buitenkant.
  !
  
  Geef de binnenkant.
!

de fn = de geefTerugFunctie.
het fn.
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Classes
You declare a class and its methods like so.
```
De klas eend:
	Bekijk het zeggenschap'':
		Zeg "Dit is een Eend".
	!
  
  Bekijk de poten'':
    Zeg "Het aantal poten zijn:" + "2".
  !
!
```

The body of a class contains its methods. They look like function declarations but without the `Bekijk` keyword. When the class declaration is executed, Dutchscript creates a class object and stores that in a variable named after the class. Just like functions, classes are first class in DutchScript.
```
// Store it in variables.
de variabel = de eend.

// Pass it to functions.
Roep een functie 'de eend'.

```

The class itself is a factory function for instances.
```
de vogel = de eend.
Zeg de vogel. // "eend instance"
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Instantiation and initialization
Classes that only have behavior aren't super useful. The idea behind Object-Oriented Programming is encapsulating behavior and state together. To do that, you need fields. DutchScript, like other dynamically-types languages, lets you freely add properties onto objects.
```
de eend.poten = 2.
de eend.veren = "een kilo".
```

Assigning to a field creates it if it doesn't already exist.

if you want to acces a field or method on the current object from within a method, you use `deze`.
```
De klas eend:
	Bekijk het zeggenschap'':
		Zeg "Dit is een Eend".
	!
  
  Bekijk het voetenwerk'':
    Zeg "Het aantal poten zijn:" + deze.poten.
  !
  
  ...
!
```

To define a initializer the class have to have a method named `het onstaan`, it is called automatically when the object is constructed. Any parameters passed to the class are forwarded to its initializer.
```
de klas eend:
	Bekijk het onstaan 'de poten, een snavel, een naam':
  		deze.poten = de poten.
		deze.snavel = een snavel.
		deze.naam = een naam.
	!
	...
!

de vogel = de eend '2,1,"frans"'.
de vogel.voetenwerk.
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Inheritance
Every Object-Oriented Language lets you not only define methods, but reuse them across multiple classes or objects. For that, DutchScript supports single inheritance. When you declare a class, you can specify a class that it inherits from using a `afkomstig` operator.

```
de klas kip afkomstig eend:
  Bekijk het geluid '':
    Zeg "POOOOOOOOOOOOOOOOOOOOOOOOOOOOK!".
  !
!

de haan = de kip '2,1,"klaasje"'.
de haan.voetenwerk.
```

Even the `het onstaan''` method gets inherited. In practice, the subclass usually wants to define its own `het ontstaan''` method too. But the original one also needs to be called so that the superclass can maintain its state. For that you use the `super` keyword.
```
de klas kip afkomstig eend:
  Bekijk het onstaan 'de poten, een snavel, een naam, de ogen':
    super.ontstaan 'de poten, een snavel, een naam'.
    deze.geluid = de ogen.
  !

  Bekijk het geluid '':
    Zeg "POOOOOOOOOOOOOOOOOOOOOOOOOOOOK!".
  !
!
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## The Standard Library

The saddest part of DutchScript. Its standard library goes beyond minimalism and veers close to outright nihilism. For the sample code, we only need to demonstrate that the code is running and doing what it's supposed to do. For that, we already have the built-in `Zeg` statement.

To see how long it takes to execute code we need to track time do we'll define one built-in function `klok''` that returns the number of seconds since the program started.

## Artistic Fluff

You can add whatever you want to the code to make the sentences/statements more dutch than code, except if it does contains keyword like writen above. 

clean:
```
de klas van de kip afkomstig eend:
  Bekijk het onstaan 'de poten, een snavel, een naam, het geluid':
    super.ontstaan 'de poten, een snavel, een naam'.
    deze.geluid = het geluid.
  !

  Bekijk het geluid '':
    Zeg "POOOOOOOOOOOOOOOOOOOOOOOOOOOOK!".
  !
!
```

dirty:
```
de klas van de kip afkomstig van de eend:
  Bekijk het onstaan met 'de poten, een snavel, een naam, het geluid':
    super.ontstaan 'de poten, een snavel, een naam'.
    deze.geluid is het geluid hard.
  !

  Bekijk nogmaals het geluid '':
    Zeg "POOOOOOOOOOOOOOOOOOOOOOOOOOOOK!" keihard.
  !
!
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>
