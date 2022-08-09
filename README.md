# PHP handbook

*Ver 2.0.0*

> This is a practical guide for using PHP that I wrote for my everyday use. 
> .
> Evgenii Zorin

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)


# Beginning

PHP code snippet:
```php
<?php
...
?>
// or
<?=
...
?>
```

Comments are written as follows:
```php
// comment 1   
# comment 2   
/* 
multiple lines
comments
*/
```

# Print / Echo 

```php
`echo 'Hello world!';`   
`echo ('...');`
# Concatenate strings
echo 'word1', ' ', 'word2' ;
$a = 'word2'; echo 'word1' . $a . 'word3' . '<br />'; 

print 'Hello world!'; # 'print' returns 1
print('...');
# print can't concatenate 

```


# Variables

Variables CAN start with a letter or an underscore.    
Variables CANNOT start with numbers or contain special characters. 

```php
$name = 'Gio';
$_name = 'Gio';
echo $name;

$x = 1; $y = 10; 
$x = $y; # Assigning the variable by value
$x = &$y; # Assigning by reference - if one variable changes, the other will change too
```

To use variables within print statements, use double quotes:
```php
$name = 'Gio';
echo "Hello, $name";
echo "Hello, {$name}";
```

**Variable variables**

```php
$foo = 'bar'; 
$$foo = 'baz'; # Use the value of variable 'foo' and use it as name for a new variable defined with value 'baz'
echo $bar #or
echo $$foo
```

## Constants

**Pre-defined constants**:
- `echo PHP_VERSION;`

**Custom constants** - once you define them, you cannot change the value:
- Way 1: `define('constant_name', 'value');`
- Way 2: `const constant_name = 'value';` 
- When referencing constants, you don't use the dollar sign: `echo constant_name;`

**Magic constants** - their value can change depending on where they are used:
- Print line number: `echo __LINE__;`
- Print file path where it's used: `echo __FILE__;`





# Data types & type casting

PHP is a dynamically-typed language (don't need to define type of variable). \n
In PHP, there are *scalar data types* (bool, int, float, string), *compound data types* (array, object, callable, iterable), and *special data types* (resource, null). \n

```php
echo gettype($x); # Print type of variable
var_dump($varname) # Print all that is known about a variable
```

## Scalar

### Bool
- Values: true, True, TRUE; true = 1, false = None
- The following evaluates to False: int (0, -0), floats (0.0, -0.0), strings ('', '0'), array ([]), null

### Int

Functions:
```php
- Print max possible integer: `PHP_INT_MAX`, `PHP_INT_MIN`, `PHP_INT_SIZE`
- Can assign a hexadecimal number: `$x = 0x2A; // = 42`
- Binary numbers: `$x = 0b110;`
- When int overflow occurs (it exceeds `PHP_INT_MAX`), the type changes to float, in the format 9.22E+18
- Check if integer: `is_int($x)`
```

### Float
Functions:
```php
- `$a = 5.3e+10`;
- Constants: `PHP_FLOAT_MAX`, `PHP_FLOAT_MIN`
- `ceil(5.8)`, `floor(5.3)`
- Float overflow -> infinity number
- Functions: `is_infinite($x)`, `is_finite($x)`, `is_nan($x)`
```

### String

- Print 1st letter: `echo $var[0];`
- Strings are mutable: `$var[2] = 'I`

```php
# Heredoc 
$x = 1; $y = 2;
$text = <<<TEXT
Line 1 $x
line 2 $y
line 3
TEXT;

echo $text
echo nl2br($text)

# Nowdoc
### Cannot use variables inside
$text = <<<'TEXT'
line 1
line 2
TEXT;

echo nl2br($text)
```

Some functions:
- `nl2br($text)` converts newlines to <br> that are recognised by html

## Compound data types

### Array

Arrays in PHP are **0-based**.

```php
$var1 = [1, 2, 3, 'a', 'b', true]; print_r($companies);
$array2 = array('PHP', 'Python', 'C++');
echo $array2[0];
$array2[1] = 'Ruby';

# Check if an item on specified index exists
isset($array[3]);

# Print items in array
echo '<pre>';
print_r($array2);
echo '</pre>';

# Get length of array
echo count($array);

# Append a value to the array
$array2[] = 'New Value';
#or
array_push($array2, 'Item1', 'Item2', 'Item3');

# Delete the value at an index 0
array_shift($array2);

# Delete the value at a specified index. NOTE: 'unset' doesn't re-index the array
unset($array2[3])
```

There is also a version of an array similar to dictionary in Python (or HashMap in other languages):
```php
$dict1 = [
	'php' => 'ver 9.0',
	'R' => 'ver unknown'
];
# With the same logic, can create multidimensional (nested) arrays, or dictionary of dictionaries

# Add an item
$dict1['go'] = '1.15';

echo $dict1['php'];
```

### Object

### Callable

### Iterable

## Special data types

### Resource

### Null

```php
$x = null;

var_dump(is_null($x));

var_dump($x === null);

# A variable is also a null if it hasn't been defined yet

# also, a variable is null if we unset it
$x = 123;
unset($x);
var_dump($x);
```


## Type Casting

```php
$x = (int) '5';
$x = (integer) PHP_INT_MAX + 1;
$a = (string) true;
$a = (float) 5; 
$a = floatval 5; 
```


# Defining a function

```php
function sum($x, $y) {
	var_dump($x, $y);
	echo '<br />';
	return $x + $y;
}
echo sum(2, 3)

function fun2(int $x, int $y) { # here we specify the datatype of parameters; here, it will convert variables into the specified datatype
	return $x + $y;
}

# Strict type - will throw an error if something weird is passed
declare(strict_types=1);
function sum(int $x, int $y) {return 'a'}

```

# IF conditionals

If a boolean is True:
```php
$isComplete = true;
if ($isComplete) {
	// do something
} else {
	// do sometehing else
}

```



?>


# Expressions

Expressions include variable assignment, comparison, IF conditions, and functions definition. 

```php
$x = 5;
```

Operator is something that takes multiple expressions and results in a value. 

## Operators

**Arithmetic operators**

These include the following: `+` `-` `*` `/` `%` `**`

In division, the result will be float unless both values are int and they are divisible without residual. 

Modulus `%` gives the remainder of the two divisors. 

**Assignment operators**

These are normal `=` and combined operators `+=` `-=` `*=` `/=` `%=` `**=`

```php
$x = 5; 
$x += 10; 
```

**String operators**

These are:
- Concatenation operator: `.`
- Concatenation operator combined with assignment: `.=`

```php
$x = 'Hello';
$x = $x . ' World'; #or
$x .= ' World';
```

**Comparison operators**

These are `==` `===` `!=` `!==` `>` `<` `>=` `<=`


```php
$x = 5; $y = '5'; 
$x == $y # Loose comparison - does typecasting for you; -> True
$x === $y # Strict comparison - considers the original data type; -> False

```

**Error control operator**

```php
$x = file('foo.txt'); # Will throw an error if the file doesn't exist
$x = @file('foo.txt'); # Will not throw an error
```

**Increment / Decrement operator**

These include `++` `--`

```php
$x = 5;
$x++; # PRE-INCREMENT: Returns the value, then increments it
$x--;

++$x; # POST-INCREMENT: Increment the value, then returns it
--$x;
```

**Logical operators**

Examples: `&&` `||` `!` `and` `or` `xor`

```php
# && AND
$x = true; $y = true;
$x && $y # False, because they are different

# || OR
$x || $y # True, because one of them is true

# ! - negation
!$x && $y # NOT x and y

# && , 'and' are both 'and', but have different precedence


```

Other examples include bitwise operators, array operators, execute operators, type operators