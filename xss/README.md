## XSS

**4.1. Setup**

Use the command ```docker-compose up --build```.

After using the above command, use the```docker ps``` then see that the containers have been created and running.

![](images/Screenshot%202024-10-20%20155134.png)

**4.2. Reflected-xss attack**

access to the "http://localhost:3128/xss-reflect.php" website.

*a,*

input in the input box of the text string is```Test```

![](images/Screenshot%202024-10-20%20155547.png)

*b,* 

input in the input box of the text string is```<h1 style="color:red">Hello World</h1>```

![](images/Screenshot%202024-10-20%20155650.png)

**4.2.1. Attack**

*c,* 

after entering the```<script>alert("How are hacked")</script>```.

![](images/Screenshot%202024-10-20%20160134.png)
