Cập nhật firmware
-----------------

Giới thiệu OTA
==============

Cập nhật firmware OTA (Over the Air) là tiến trình tải firmware mới vào
ESP module thay vì sử dụng cổng Serial. Tính năng này thực sự rất hữu
dụng trong nhiều trường hợp giới hạn về kết nối vật lý đến ESP Module.

OTA có thể thực hiện với:

-  `Arduino IDE`_
-  `Web Browser`_
-  `HTTP Server`_

Sử dụng OTA với tùy chọn dùng **Arduino IDE** trong quá trình phát
triển, thử nghiệm, 2 tùy chọn còn lại phù hợp cho việc triển khai ứng
dụng thực tế, cung cấp tính năng cập nhật OTA thông qua web hay sử dụng
HTTP Server.

Trong tất cả các trường hợp, thì Firmware hỗ trợ OTA phải được nạp lần
đầu tiên qua cổng Serial, nếu mọi thứ hoạt động trơn tru, logic ứng dụng
OTA hoạt động đúng thì có thể thực hiện việc cập nhật firmware thông qua
OTA.

Sẽ không có đảm bảo an ninh đối với quá trình cập nhật OTA bị hack. Nó
phụ thuộc vào nhà phát triển đảm bảo việc cập nhật được phép từ nguồn
hợp pháp, đáng tin cậy. Khi cập nhật hoàn tấn, ESP8266 sẽ khởi động lại
và thực thi code mới. Nhà phát triển phải đảm bảo ứng dụng thực trên
module phải được tắt và khởi độn glaij 1 cách an toàn. Nội dung bên dưới
cung cấp bổ sung các thông tin về an ninh, và an toàn cho tiến trình cập
nhật OTA.

Bảo mật
~~~~~~~

Khi ESP8266 được phép thực thi OTA, có nghĩa nó được kết nối mạng không
dây và có khả năng được cập nhập Sketch mới. Cho nên khả năng ESP8266 bị
tấn công sẽ nhiều hơn và bị nạp bởi mã thực thi khác là rất cao. Để giảm
khả năng bị tấn công cần xem xét bảo vệ cập nhật của bạn với một mật
khẩu, cổng sử dụng cố định khác biệt, v.v…

Kiểm tra những tính năng được cung cấp bởi thư viện `ArduinoOTA`_ thường
xuyên, có thể được nâng cấp khả năng bảo vệ an toàn:

.. code:: cpp

    void setPort(uint16_t port);
    void setHostname(const char* hostname);
    void setPassword(const char* password);

Một số chức năng bảo vệ đã được xây dựng trong và không yêu cầu bất kỳ
mã hóa nào cho nhà phát triển. `ArduinoOTA`_ và ``espota.py`` sử dụng
`Digest-MD5`_ để chứng thực việc tải firmware lên. Đơn giản là đảm bảo
tính toàn vẹn của firmware bằng việc tính `MD5`_.

Hãy phân tích rủi ro cho riêng ứng dụng của bạn bạn và tùy thuộc vào ứng
dụng mà quyết định những chức năng cũng như thư viện để thực hiện. Nếu
cần thiết, có thẻ xem xét việc thực hiện các phương thức bảo vệ khỏi bị
hack, ví dụ như cập nhật OTA chỉ cho tải lên chỉ theo lịch trình cụ thể,
kích hoạt OTA chỉ được người dùng nhấn nút chuyên dụng “Cập nhật”, v.v…

An toàn
~~~~~~~

Quá trình OTA tiêu tốn nguồn tài nguyên và băng thông của ESP8266 khi
tải lên. Sau đó, ESP8266 được khởi động lại và một Sketch mới được thực
thi. Cần phải phân tích và kiểm tra để Sketch mới không ảnh hưởng tới
các chức năng hiện có của Sketch hiện tại, cũng như việc cập n

.. _Arduino IDE: using-arduino-ide.md
.. _Web Browser: using-web-browser.md
.. _HTTP Server: using-http-server.md
.. _ArduinoOTA: https://github.com/esp8266/Arduino/tree/master/libraries/ArduinoOTA
.. _Digest-MD5: https://en.wikipedia.org/wiki/Digest_access_authentication
.. _MD5: https://en.wikipedia.org/wiki/MD5
