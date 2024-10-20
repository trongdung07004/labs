## SOP

**4.1.1 Setup**

Step1: chạy lệnh ```docker-compose up -d```.

Step2: chạy lệnh ```docker ps``` sẽ thấy hai container web-client and web-10.9.0.5 đang chạy.

![](sop/images/Screenshot%202024-10-19%20135049.png)

Step3: open vnc viewer, then search ```localhost:5900```.

![](sop/images/Screenshot%202024-10-19%20135451.png)

Step4:

chạy lệnh ```docker exex -it web-client sh -l``` để vào trong container web-client.

sau đó chạy lệnh```cat /tmp/hosts >> /etc/hosts``` để ghi từ /tmp/hosts vào cuối file /etc/hosts.

![](sop/images/Screenshot%202024-10-19%20140621.png)

**4.1.2 Using JS to access DOM objects of the web site**

*a,* trong firefox mở trang web "http://sitea.com" và thử các lệnh DOM (document.body, document.body.innerText, ...)

![](sop/images/Screenshot%202024-10-19%20140945.png)

*b,* dùng lệnh ```document.getElementById("header").innerText="text"``` để thay đổi text của thẻ h1 với Id="header".

![](sop/images/Screenshot%202024-10-19%20141200.png)

*c,* dùng lệnh ```var newwin = window.open(http://siteb.com,”right”)``` thì firefox có đưa ra 1 cảnh báo nhưng có thể chấp nhận cảnh báo đó thì trang web "http://siteb.com" vẫn được mở lên.

*d,* ```window.opener.location=”http://parentsite.com```

**4.1.3 Frame objects**

*a,* dùng lệnh ```window.framea``` or ```window.frameb``` có thể hiển thị ra URL của hai framea và frameb.

*b,* không thể truy cập doccument.body của framea or frameb từ parentsite

![](sop/images/Screenshot%202024-10-19%20212312.png)

*c,d * từ sitea.com có thể xem URL của parentsite nhưng không thể truy cập DOM của parentsite, hình ảnh cho thang đang chọn framea và không thể truy cập DOM của parentsite.

![](sop/images/Screenshot%202024-10-19%20212841.png)

*e,* đầu tiên chọn parentsite và định nghĩa một biến ```var hello="world"``` sau đó chọn sitea or siteb và thử in ra biến hello thì sẽ không truy cấp được biến hello từ parentsite.

![](sop/images/Screenshot%202024-10-19%20213328.png)

**4.1.4. Sending POST request to a site**

*a,* dùng lệnh ```http://sitea.com/post.html``` để truy cập trang web.

*b,* nhập vào textbox một đoán text và submit thì sẽ chuyển hướng đến trang "http://siteb.com" vì button submit nằm trong một form có action là URL của siteb và method="POST"

![](sop/images/Screenshot%202024-10-19%20212312.png)

*c,* đây là request và response 

![](sop/images/Screenshot%202024-10-19%20214151.png)

*d,* 

nhìn vào thì thấy một yêu cầu POST được thực hiện đến "http://siteb.com", trình duyệt chỉ ra rằng yêu cầu được gửi từ "http://sitea.com/post.html" 

Response Status: 200 OK

![](sop/images/Screenshot%202024-10-19%20214151.png)

**4.1.5. Access image, stylesheet from other sites**

*a,* có thể thay đổi image của sitea thành image từ siteb

![](sop/images/Screenshot%202024-10-19%20214712.png)

*b,* có thể thay đổi stylesheet của sitea từ siteb

![](sop/images/Screenshot%202024-10-19%20215042.png)

**4.1.6. SOP applies to web storage**

*a,* mở một tab sitea và dùng lệnh ```window.localStorage["first"] = 100``` để thêm 1 biến first=100 và localStorage

*b,* sau đó mở thêm 1 tab sitea nữa và thay đổi lại biến first=200 sau đó qua tab đầu tiên thì thấy biến first trong tab đầu tiên cũng bị thay đổi theo

*c,* ở siteb không thể truy cập biến first của sitea vì đây là biến local

*d,* sau khi đóng tất cả các tab sitea và mở lại thì biến first vẫn còn

*e,* sau khi đóng trình duyệt mở lại thì biến first vẫn còn, nếu muốn biến first bị xóa thì bạn vào vào xóa hoặc xóa dữ liệu của web

*f,*
Local Storage:
lưu trữ dữ liệu một cách vĩnh viễn cho đến khi bạn xóa nó hoặc xóa dữ liệu trình duyệt.
Mỗi website có một localStorage riêng biệt.
Dữ liệu trong localStorage có dung lượng giới hạn.

Session Storage:
Session Storage phù hợp để lưu trữ dữ liệu tạm thời trong một phiên làm việc, khi đóng tab hoặc đóng trình duyệt thì sẽ bị mất dữ liệu
Dữ liệu trong Session Storage cũng có dung lượng giới hạn.
