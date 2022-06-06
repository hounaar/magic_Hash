# magic_Hash
Magic Hash Vulnerability, is a vulnerability in PHP (most of the time) that occurs a bad accessability for hackers.
The SQL Injection which is a code injection technique that might destroy your database. Furthermore, it is one of the most common web hacking techniques and it is the placement of malicious code in SQL statements, via web page input.


By the injection type, whether the datapoints and variables have been declared as ```php $_GET[''] ``` superglobe, still there will be some bad vulnerabilities just like Magic Hash.
besides the hash algorithm can sometimes be an integer not a string.

When the administrator try to login with the 'admin' or 'administrator' username, the password must be hashed fully either it can be <a href="https://en.wikipedia.org/wiki/MD5">md5 algorithm </a>. the code below is showing the main vulnerability:


```php

$username = $_GET['username];
$password = $_GET['password];

if($username == 'admininstrator'){
    if(hash('md5', $password, false) == '0e9898'){
        echo "Administrator, Welcome";
    } else {
        echo "You are not admin";
    }
}

```
Either way the password is hashed by the md5 algorithm, it would destroy the database because of two reasons :
- the all equals in the each two conditions which should be ``` === ```
- the hashed one should not start with ZERO(0) or the database will be destroyed by the hacker.



the right way to write the program is this:

```php

$username = $_GET['username];
$password = $_GET['password];

if($username === 'admininstrator'){
    if(hash('md5', $password, false) === 'e9898'){
        echo "Administrator, Welcome";
    } else {
        echo "You are not admin";
    }
}

````


this magix hash has been detected by magic hash-robert hansen for the first time.

#### I hope that dear developers be carefull with this vulerability cause it could destroy everything.
