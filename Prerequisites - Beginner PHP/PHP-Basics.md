# PHP Basics

Many CMSs are built with PHP (WordPress, Drupal) and many sites like Wikipedia and Facebook use PHP as well.  According to Team Tree House, approximately 25% of the web is built using PHP.

PHP is a Server Side Language -- The code is processed on the web server.  The way it works is that the server receives a request from the client, the script sent is processed on the server then the server returns the results as an HTML response.

In other words, the server sends back plain HTML.  Viewing the source code within a web browser will not show any PHP code, only the HTML that the server outputs after processing the PHP program.

## PHP Code

Placed in code blocks like HTML:
```php
<?php
    echo 'Hello World!';
?>
```
White space is ignored in PHP like in HTML.

## PHP Comments

* Single line comments: ```// This is a single line comment```
* Multi-line comments: ```/* Multiline comments can go in here */```

## Variables in PHP

Variables in PHP always begin with a ```$``` followed by an ```_``` or a letter.

A variable cannot begin with a number.

**Types:**      
* boolean -- $myBoolean = true;
* integer -- $myInteger = 1;
* float -- $myFloat = 2.25;
* string -- $myString = 'Hellow World';

## Determining type of variable in PHP

Using the ```var_dump()``` function, the type of variable can be shown:
```php
<?php
$num_one = 1;

var_dump( $num_one );
var_dump( 1 );
var_dump( '1' );
?>
```

## Basic Unit Converter in PHP
```php
<?php
// number in pounds we want to convert to kilograms
$pounds = 140;
// floating point value for the pound to kilogram conversion
$lb_to_kg = 0.453592;
// use the variables above to calculate pounds multiplie by the kilogram conversion
$kilograms = $pounds * $lb_to_kg;
// display the pounds to kilograms
echo "Weight: ";
echo $pounds;
echo " lb = ";
echo $kilograms;
echo "kg";
?>
```

## Strings

**Example of using a string within quotes**
```php
<?php
$name = 'Xavier';
$string_one = "Hello $name";
echo $string_one;
?>
```

**String Concatenation**

In PHP strings are concatenated using ```.```
```php
<?php
$name = 'Xavier';
$string_one = 'Hello ';
echo $string_one . $name . "\n";
?>
```