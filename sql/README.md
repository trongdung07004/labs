## SQL

**4.1. Setup**
similar to SOP

**4.2. About the Web application and users’ credential**

information (accounts, passwords) of users in the database

Admin, seedadmin
Alice, seedalice
Boby, seedboby
Ryan, seedryan
Ted, seed ted
Samy, seedsamy

**4.3.1. SQL Injection attack from webpage**

Based on ```Where name='$input_name' and Passwold='$hashed_pwd``` (with $hashed_pwd is the password that has been encrypted via the command ```$hashed_pwd = sha1($input_pwd)```) in unsafe_home.php.

For example, here I only know the account but don't know the password, this image is a way to attack.

![](images/Screenshot%202024-10-20%20203357.png)

After entering the input cell ```username=Admin' or ' 1=1``` then the sql sentence becomes ```Where name='Admin' or '1=1' and Passwold='$hashed_pwd'```(because here the use of or Admin exists in the database, it is always correct without the correct latter).

**4.3.2. SQL Injection attack from command line**

This is a way to attack the URL, but this time I only know the password but not the username.

![](images/Screenshot%202024-10-20%20205218.png)

*%27 is the encoding of the '*

*%3D is the encoding of the =*

The picture above is filled in as an example username=a' or '1=1&Passwold=seedadmin(because there is OR, the first part is only 1=1 is always true, and the next part is Password, because you know, you will be able to log in).
