# Logger by JCScripts (PHP)
Logger by JCScripts is a very simple logging framework for small PHP projects. It helps to save messages into a rolling log file that helps to track of the process execution during run time in PHP. [Click here](https://jcwebtechnologies.com) for more information

> Simple, yet powerful!

### Supported logging levels
 - **DEBUG**  - Detailed level of information
 - **INFO**   - High-level application information
 - **WARNING**- Minimal errors that won't harm the system, but to be resolved
 - **ERROR**  - Unwanted situation in an application
 - **FATAL**  - Critical failure that might halt the application

### Available methods in this framework takes message String as parameter with no return value.
 - `debug (string $message)` - DEBUG
 - `info (string $message)` - INFO
 - `warn (string $message)` - WARNING
 - `error (string $message)` - ERROR
 - `fatal (string $message)` - FATAL

### How to integrate?
You can simply integrate JCLogger into your existing following these steps:
1) Include Logger.php file to your PHP script either by explicit include (or) auto class loader. Here is an example of explicit include.
```php
include_once( 'Logger.php' );
```

2) Create an instance of Logger class under namespace **JCScripts**
```php
$log = new JCScripts\Logger();
```

3) Invoke a method of JCLogger on the creted object, based on the type of message that you want to store
```php
$log->info('Entered this method');
```

4) _(Optional, but recommended)_ Invoke close() method on the object to free up any resources created by JCLogger
```php
$log->close();
```

### Example:
---

```php
<?php
include_once('Logger.php');
$log = new JCScripts\Logger();

function divide($a, $b)
{
    global $log;
    $value = null;
    $log->info('Entered divide() method');
    $log->debug("Value of a=${a}, b=${b}");
    if ($b == 0) {
        $log->error('Divide by zero error, parameter #2 should not be 0');
    } else {
        $value = $a / $b;
        $log->debug("Return value is ${value}");
    }
    $log->info('Exit divide() method');
    return $value;
}
// Example call #1
echo divide(10, 2);

// Example call #2
echo divide(10, 0);
?>
```

### Output in log file:
-------------------
For Example call #1:  

19-11-2020 22:18:36 [INFO ] - Entered divide() method  
19-11-2020 22:18:36 [DEBUG] - Value of a=10, b=2  
19-11-2020 22:18:36 [DEBUG] - Return value is 5  
19-11-2020 22:18:36 [INFO ] - Exit divide() method  

For example call #2:

19-11-2020 22:18:36 [INFO ] - Entered divide() method  
19-11-2020 22:18:36 [DEBUG] - Value of a=10, b=0  
19-11-2020 22:18:36 [ERROR] - Divide by zero error, parameter #2 should not be 0  
19-11-2020 22:18:36 [INFO ] - Exit divide() method  
