## SOP

**4.1.1 Setup**

Step1: Run the command ```docker-compose up -d```.

Step2: Run the command ```docker ps``` will see two containers web-client and web-10.9.0.5 running.

![](images/Screenshot%202024-10-19%20135049.png)

Step3: open vnc viewer, then search ```localhost:5900```.

![](images/Screenshot%202024-10-19%20135451.png)

Step4:

Run the command ```docker exex -it web-client sh -l``` to enter the web-client container.

Then run the command ```cat /tmp/hosts >> /etc/hosts``` to write from /tmp/hosts at the end of the /etc/hosts file.

![](images/Screenshot%202024-10-19%20140621.png)

**4.1.2 Using JS to access DOM objects of the web site**

*a,* in firefox open the "http://sitea.com" website and try the DOM commands (document.body, document.body.innerText, ...).

![](images/Screenshot%202024-10-19%20140945.png)

*b,* use the command ```document.getElementById("header").innerText="text"``` to change the text of the h1 tag with Id="header".

![](images/Screenshot%202024-10-19%20141200.png)

*c,* using the command ```var newwin = window.open(http://siteb.com,"right")``` Firefox will issue a warning, but if the warning can be accepted, the "http://siteb.com" website will still be opened.

*d,* ```window.opener.location="http://parentsite.com```.

**4.1.3 Frame objects**

*a,*  using the command ```window.framea``` or ```window.frameb``` to display the URLs of both framea and frameb.

*b,* Unable to access the doccument.body of framea or frameb from the parentsite.

![](images/Screenshot%202024-10-19%20212312.png)

*c,d * from sitea.com can see the URL of the parentsite but cannot access the DOM of the parentsite, the image for the ladder is selecting framea, and cannot access the DOM of the parentsite.

![](images/Screenshot%202024-10-19%20212841.png)

*e,* First, select parentsite and define a variable ```var hello="world"```, then select sitea or siteb and try to print out the hello variable, but the hello variable will not be accessible from the parentsite.

![](images/Screenshot%202024-10-19%20213328.png)

**4.1.4. Sending POST request to a site**

*a,* Use the ```http://sitea.com/post.html``` command to access the website.

*b,* Enter a text guess in the textbox and submit will redirect to the "http://siteb.com" page because the submit button is in a form whose action is the URL of siteb and method="POST".

![](images/Screenshot%202024-10-19%20212312.png)

*c,* This is the request and response

![](images/Screenshot%202024-10-19%20214151.png)

*d,* 

look at it and see a POST request made to "http://siteb.com", the browser indicates that the request is sent from "http://sitea.com/post.html"

Response Status: 200 OK

![](images/Screenshot%202024-10-19%20214151.png)

**4.1.5. Access image, stylesheet from other sites**

*a,* It is possible to change a sitea image to an image from siteb

![](images/Screenshot%202024-10-19%20214712.png)

*b,* Can change sitea stylesheet from siteb

![](images/Screenshot%202024-10-19%20215042.png)

**4.1.6. SOP applies to web storage**

*a,* open a sitea tab and use the command ```window.localStorage["first"] = 100``` to add 1 variable first=100 and localStorage

![](images/Screenshot%202024-10-20%20094048.png)

*b,*  Then open 1 more sitea tab and change the first=200 variable again, then through the first tab, you can see that the first variable in the first tab is also changed

![](images/Screenshot%202024-10-20%20094942.png)

*c,* In siteb, the first variable of sitea cannot be accessed because this is the local variable of sitea

![](images/Screenshot%202024-10-20%20095052.png)

*d,* After closing all the sitea tabs and reopening it, the first variable is still

*e,* After closing the browser and reopening it, the first variable remains, if you want the first variable to be deleted, you can go to Delete or Delete Web Data

*f,*
Local Storage:
store the data permanently until you delete it or delete the browser data.
Each website has a separate localStorage.
Data in localStorage has a limited capacity.

Session Storage:
Session Storage is suitable for storing temporary data in a working session, when closing a tab or closing the browser, the data will be lost
The data in Session Storage also has a limited capacity.
