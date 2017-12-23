# PHP Basics

Many CMSs are built with PHP (WordPress, Drupal) and many sites like Wikipedia and Facebook use PHP as well.  According to Team Tree House, approximately 25% of the web is built using PHP.

PHP is a Server Side Language -- The code is processed on the web server.  The way it works is that the server receives a request from the client, the script sent is processed on the server then the server returns the results as an HTML response.

In other words, the server sends back plain HTML.  Viewing the source code within a web browser will not show any PHP code, only the HTML that the server outputs after processing the PHP program.

**Table of Contents**       
[PHP Code](#php-code)       
[Variables](#variables)       
[Strings](#strings)       
[PHP with HTML](#php-with-html)       
[Making a list from an Array](#making-a-list-from-an-array)       
[Associative Arrays](#associative-arrays)       

## PHP Code

Placed in code blocks like HTML:
```php
<?php
    echo 'Hello World!';
?>
```
White space is ignored in PHP like in HTML.

**Comments**

* Single line comments: ```// This is a single line comment```
* Multi-line comments: ```/* Multiline comments can go in here */```

## Variables

Variables in PHP always begin with a ```$``` followed by an ```_``` or a letter.

A variable cannot begin with a number.

**Types:**      
* boolean -- $myBoolean = true;
* integer -- $myInteger = 1;
* float -- $myFloat = 2.25;
* string -- $myString = 'Hellow World';

### Determining type of variable in PHP

Using the ```var_dump()``` function, the type of variable can be shown:
```php
<?php
$num_one = 1;

var_dump( $num_one );
var_dump( 1 );
var_dump( '1' );
?>
```

### Basic Unit Converter in PHP
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

## PHP with HTML

Example of h1 tag using PHP:
```php
<h1><?php echo 'Xavier Trinidad' ?></h1>
```

In order for the PHP to render the content within the tag, the file extension for file needs to be .php

### Using PHP with HTML to keep code DRY

Define a PHP variable at the top:
```php
<?php $display_name = 'Xavier Trinidad'; ?>
```

Then use the variable throughout the HTML where needed
```php
<h1><?php $display_name ?></h1>
<footer><?php $display_name; ?></footer>
```

### Using a PHP Function

```php
<section class="footer text-center">
      &copy; <?php echo date('Y'); ?> <?php echo $display_name ?>
</section>
```

Using the *date()* function along with the ```Y``` parameter will display the current year.

###  Include

Including PHP from other files:
```php
<?php include 'inc/units.php'; ?>
```

## Making a list from an Array

```php
$myArr = ['Arr Item 1'];
  array_push($myArr, 'Arr Item 2');
  $list = 
  "
  <ul>
    <li>$myArr[0]</li>
    <li>$myArr[1]</li>
  </ul>
  "
  ```

  This example always uses the *array_push* function to add an item to the end of the array.  A list of PHP array functions can be found [here](http://php.net/manual/en/ref.array.php).

  ## Associative Arrays

  ```php
  //Associative Arrays
$array = [
    "foo" => "<b>bar</b>",
    "bar" => "<i>foo</i>",
];
```

In this example, 'foo' is the key and it points to the value and 'bar' is the key that points to its associated value.  The following line inserted into HTML:

```php
<?php echo $array['bar'] ?>
```

Would place a ```<b>bar</b>``` tag into it.