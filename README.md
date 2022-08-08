# PHP handbook

*Ver 1.0.0*

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
$a = 'word2'; echo 'word1' . $a . 'word3' ; 

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

PHP is a dynamically-typed language (don't need to define type of variable)

*Scalar types*:
- **bool** (true, True, TRUE): `$var1 = true`; true = 1, false = None
	- The following evaluates to False: int (0, -0), floats (0.0, -0.0), strings ('', '0'), array ([]), null
- **int**
	- Print max possible integer: `PHP_INT_MAX`, `PHP_INT_MIN`, `PHP_INT_SIZE`
	- Can assign a hexadecimal number: `$x = 0x2A; // = 42`
	- Binary numbers: `$x = 0b110;`
	- When int overflow occurs (it exceeds `PHP_INT_MAX`), the type changes to float, in the format 9.22E+18
	- Check if integer: `is_int($x)`
- **float**:
	- `$a = 5.3e+10`;
	- Constants: `PHP_FLOAT_MAX`, `PHP_FLOAT_MIN`
	- `ceil(5.8)`, `floor(5.3)`
	- Float overflow -> infinity number
	- Functions: `is_infinite($x)`, `is_finite($x)`, `is_nan($x)`
- **string**

*Compound types*:
- **array**: `$var1 = [1, 2, 3, 'a', 'b', true]; print_r($companies);`
- **object**
- **callable**
- **iterable**

*Special types*
- **resource**
- **null**

```php
echo gettype($x); # Print type of variable
var_dump($varname) # Print all that is known about a variable
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