# CSRF
**4.1 Setup**

The setup steps are similar to the previous SOP I did.
![](images/Screenshot%202024-10-20%20142032.png)

**4.2. Conducting the Transaction**

*a,* 

In the vnc of the container client, access the "http://mysite.com/login.php" page to log in.


After logging in, you will be redirected to the "http://mysite.com/tranfer.php" page, then enter the amount and recipient and click on the transfer button.

![](images/Screenshot%202024-10-20%20142232.png)

*b,* Open Network to view the Request header and record Cookie: PHPSESSID=ho6u4499qfbnhophl1hhhvdm22 as shown in the picture.

![](images/Screenshot%202024-10-20%20144110.png)

**4.3. Cross-Site-Request-Forgery**

In this section, you will start attacking users by creating a malicious website called "http://darksite.com/tricky.html"

Somehow while the user of the session clicks on the link of the site "http://darksite.com/tricky.html", the site will execute a transfer to an account named Atacker 50 without the user's consent
![](images/Screenshot%202024-10-20%20144117.png)

The explanation for this problem is that when the user clicks on the website and is still logged in, the cockie will be sent to the server by the browser, when the server sees the correct cockie, the command will be executed.

![](images/Screenshot%202024-10-20%20144138.png)

The image above shows that Origin is "http://darksite.com" but Cockie is the same as the user who is logging in, so the command code will be executed as passing to the Atacker 50.

