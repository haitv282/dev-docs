## Why this topic?

* Debugging is a daily task and can be very irritating and time-consuming if not done effectively.

* Not only help in fixing bugs but also help understanding existed code/framework

### Without debugger

* Print \(or the likes that output text to screen\)

### With debugger

* Breakpoints
* Call Stack

* Watch/Inspect

* Controlling Execution:

* > Step Over \(Next line\)
  >
  > Step Into
  >
  > Step Out
  >
  > Continue/Resume



## Debugging Javascript

### Without debugger

* alert \(\)

* console.log \(in fact, need a debugger for this command\)

### With debugger

Firefox: Firebug 

Chrome: Built-in development tool \(F12 / Ctrl + Shift + I\)

IE / Edge: Built-in development tool \(F12\)



## Debugging PHP

### Without debugger

* echo, die, var\_dump, print\_r

* Magento 1: Mage::log\(\)
* Magento 2: 



### With debugger:

#### Configure XDebug:

**php.ini \[XDebug\]**

```
[XDebug]
# Uncheck in php.ini
zend_extension_ts="D:\xampp\php\ext\php_xdebug.dll"
# Paste following lines:
xdebug.remote_enable=On
xdebug.remote_host="localhost"
xdebug.remote_port=9000
xdebug.remote_handler=dbgp
xdebug.profiler_enable=1
xdebug.profiler_output_dir="D:\xampp\tmp
```

**Check with command line:**

`php -m `

Output

```
[Zend Modules]
Xdebug Zend Extension Manager
```



### Configure xDebug in PHPStorm

#### Debugging SQL

**Log specific SQL:**

* M1: Use Mage::log\(“SQL=” . $collection-&gt;getSelect\(\)-&gt;\_\_toString\(\)\);

**Log all SQL:**

* M1: Edit file: lib/Varien/Db/Adapter/Pdo/Mysql.php



```
protected $_debug = true;
protected $_logAllQueries = true;
```

All queries will be written into:

`var/debug/pdo_mysql.log`

