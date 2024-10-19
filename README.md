## SOP

**4.1.1 Setup**

Step1: run command ```docker-compose up -d```.

Step2: run command ```docker ps``` see for list containers is running, container web-client and web-10.9.0.5.
![](sop/images/Screenshot%202024-10-19%20135049.png)

Step3: open vnc viewer, then search ```localhost:5900```.
![](sop/images/Screenshot%202024-10-19%20135451.png)

Step4: 

run command ```docker exex -it web-client sh -l``` for into web-client.

after run command ```cat /tmp/hosts >> /etc/hosts``` for write /etc/hosts from /tmp/hosts.
![](sop/images/Screenshot%202024-10-19%20140621.png)

**4.1.2**
