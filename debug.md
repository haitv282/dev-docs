



Debugging: Why this topic? 

- Debugging is a daily task and can be very irritating and time-consuming if not done effectively. 

- Not only help in fixing bugs but also help understanding existed code/framework



Basic term – w.o. debugger 

- Print \(or the likes that output text to screen\)



Basic terms – w. debugger 

• Breakpoints 

• Call Stack 

• Watch/Inspect 

• Controlling Execution: 

  – Step Over \(Next line\) 

  – Step Into 

  – Step Out 

  – Continue/Resume







  Debugging JavaScript 

  • Without debugger: 

    – alert 

    – console.log \(in fact, need a debugger for this command\)



  • With debugger: 

    – Firefox: Firebug 

    – Chrome: Built-in development tool 

    – IE \(8,9\): Built-in development tool 



  Shortcut: F12





 Debugging PHP 

  • Without debugger: 

  – echo, die, var\_dump, print\_r 

  – Mage::log\(\)





  Debugging PHP 

  • With debugger: 

  – Configure XDebug: 

  • php.ini \[XDebug\] 



\`\`\`

\[XDebug\]



\# Uncheck in php.ini



zend\_extension\_ts="D:\xampp\php\ext\php\_xdebug.dll"

\# Paste following lines:

xdebug.remote\_enable=On

xdebug.remote\_host="localhost"

xdebug.remote\_port=9000

xdebug.remote\_handler=dbgp

xdebug.profiler\_enable=1

xdebug.profiler\_output\_dir="D:\xampp\tmp

\`\`\`



Check with command line: 

\`php -m \`



Output

\`\`\` 

\[Zend Modules\] 

Xdebug Zend Extension Manager

\`\`\`



\#\# Configure xDebug in PHPStorm





\#\# Debugging SQL 



\#\#\# Log specific SQL: 

– Use Mage::log\(“SQL=” . $collection-&gt;getSelect\(\)-&gt;\_\_toString\(\)\);



\#\#\# Log all SQL: 



– Edit file: lib/Varien/Db/Adapter/Pdo/Mysql.php



\`\`\`

protected $\_debug = true;

protected $\_logAllQueries = true;

\`\`\`



All queries will be written into: 

\`var/debug/pdo\_mysql.log\`

