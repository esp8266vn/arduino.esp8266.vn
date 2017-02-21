Smartconfig
-----------
Smartconfig là một khái niệm được nhắc đến khi khi muốn cấu hình thông tin cho thiết bị WiFi kết nối nhanh chóng đến Internet nhất từ người dùng bằng chính thiết bị (điện thoại) của họ.

.. image:: ../_static/smart-config.gif

Để hiểu một cách đơn giản thì Smart config nghĩa là chúng ta gửi thông tin mạng wifi (bao gồm tên wifi và password wifi) cho ESP thông qua smartphone thay cho cách thông thường là phải khai báo thông tin này trong chương trình và nạp firmware xuống.

Lợi ích của Smartconfig
=======================

* Dễ dàng cấu hình wifi cho ESP8266 thông qua smartphone.
* Không cần phải nạp lại code để cấu hình
* Có thể dùng Smartconfig để cấu hình nhiều thiết bị một lúc

ESP Touch
=========

ESP Touch là protocol được dùng trong Smart Config để người dùng có thể kết nối tới các phiên bản modul ESP8266 thông qua cấu hình đơn giản trên Smartphone.
Ban đầu không thể kết nối với ESP8266, nhưng thông qua giao thức ESP-TOUCH thì Smartphone sẽ gửi gói UDP tới Access Point(AP) ở đây là ESP8266, mã hóa SSID và mật khẩu thành trường Length trong gói UDP, để ESP8266 có thể hiểu và giải mã được thông tin.

Cấu trúc gói tin sẽ có dạng

+----+----+--------+-----+------+----------+-----+
| 6  | 6  | 2      | 3   | 5    | Variable | 4   |
+----+----+--------+-----+------+----------+-----+
| DA | SA | Length | LLC | SNAP | DATA     | FCS |
+----+----+--------+-----+------+----------+-----+

Length bao gồm SSID và thông tin key cho ESP8266
