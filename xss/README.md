## XSS

**4.1. Setup**

dùng lệnh ```docker-compose up --build```.

sau khi dùng lệnh trên, dùng leenhj```docker ps``` thì thấy các container đã được tạo và chạy.

![](images/Screenshot%202024-10-20%20155134.png)

**4.2. Reflected-xss attack**

truy câp vào web "http://localhost:3128/xss-reflect.php".

*a,*

nhập vào ô input chuỗi text là ```Test```

![](images/Screenshot%202024-10-20%20155547.png)

*b,* 

nhập vào ô input chuỗi text là ```<h1 style="color:red">Hello World</h1>```

![](images/Screenshot%202024-10-20%20155650.png)

**4.2.1. Attack**

*c,* 

sau khi nhập vào ```<script>alert("How are hacked")</script>``` thì

![](images/Screenshot%202024-10-20%20160134.png)
