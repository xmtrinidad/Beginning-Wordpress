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
[Loops](#loops)     
[Functions](#Functions)
[Basic Error Handling](#basic-error-handling)       
[_GET Variables](#get-variables)       

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

## Loops

PHP uses typical loops found in other programming languages like JavaScript

**while loop example**
```php
<?php $count = 0;
    while ($count < 10) {
        echo "<span>count is $count, </span>";
        $count++;
    }
?>
```

**for loop**
```php
<?php 
    for ($x = 1; $x <= 10; $x++) {
        echo "<p>This is a for loop item $x<p>";
    }
?>
```

**foreach loop**
```php
<ul>
    <?php
        foreach ($list as $item) {
            echo "<li>$item</li>";
        }
    ?>
</ul>
```

## Functions

Just like JavaScript, PHP has almost the same structure for functions:
```php
<?php 
    function hello() {
        echo '<p>Hello, World! Function!!</p>';
    }

    function helloParam($name) {
        echo "<p>Hello $name</p>";
    }
?>
```

The difference is that ```$``` is required for variables.

## Basic Error Handling

**Types of Errors**
1.  Notice
    * Will not stop execution of the script, but indicates something is not being done correctly

2.  Warning
    *  Something is being done wrong and will cause problems so address as soon as possible; will not stop execution of the script

3.  Fatal error
    * Logical or syntax error that prevents the script from being understood.  THese types of errors will stop the execution of a script.


**Displaying Errors On Screen**     
1.  In the php.ini file
2.  In the .htaccess file on your web server
3.  From your own PHP code

The instructions to display errors on the Team Tree House tutorials weren't quite clear enough so after doing my research I found a [thread on Stack Overflow](https://stackoverflow.com/questions/14581460/why-mamp-doesnt-display-errors) that discusses how to display errors

1.  Navigate to the MAMP application

In my case, the MAMP folder was inside the C: drive

2.  Inside the MAMP folder go to the *conf* folder then navigate to the folder of the PHP version MAMP is using.

To find out what version of PHP the MAMP application is using, launch MAMP, click "Open start page" on the toolbar of the page that opens click *phpInfo*.  The page redirects to information about PHP, including the version being used with MAMP.

3.  Open the *php.ini* file within the version file.

The php.ini file was the only file within PHP version folder.

4.  When the php.ini opens in whatever program is chosen to open it, search for *display_errors*

I used VS Code to open the file and used the *ctrl+f* shortcut to search for it

5.  Turn *display_errors = off* to *display_errors = on* and save.

6.  Restart MAMP

## _GET Variables

In a web URL, a GET request would looking something like:
```http://<DOMAIN>/catalog.php?cat=books```

Variables added to the URL in this way get sent to the server along with the request for the web page.

The variable can be accessed with PHP using *$_GET["cat"]*

"cat" can be any name given when linked in the HTML/PHP
```php
<ul class="nav">
    <li class="books"><a href="catalog.php?cat=books">Books</a></li>
    <li class="movies"><a href="catalog.php?cat=movies">Movies</a></li>
    <li class="music"><a href="catalog.php?cat=music">Music</a></li>
    <li class="suggest"><a href="suggest.php">Suggest</a></li>
</ul>
```

Below is an example of displaying conditional data using *$_GET*
```php
<?php 
$pageTitle = "Full Catalog";

if ($_GET["cat"] == "books") {
        $pageTitle = "Books";
    } else if ($_GET["cat"] == "movies") {
        $pageTitle = "Movies";
    } else if ($_GET["cat"]== "music") {
        $pageTitle = "Music";
    }
?>
```

Using this implementation, an error would be displayed if the url didn't contain any GET information, for example if the url looked like ```http://<DOMAIN>/catalog.php```
an *undefined* notice would be displayed.

To avoid this, the *isset()* function is used to check for undefined links:
```php
$pageTitle = "Full Catalog";

if (isset($_GET["cat"])) {
    if ($_GET["cat"] == "books") {
        $pageTitle = "Books";
    } else if ($_GET["cat"] == "movies") {
        $pageTitle = "Movies";
    } else if ($_GET["cat"]== "music") {
        $pageTitle = "Music";
    }
}
```