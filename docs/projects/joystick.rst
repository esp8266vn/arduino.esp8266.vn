Đọc dữ liệu từ Joystick - hiển thị lên OLED
-----------------

Demo
====

.. youtube:: https://www.youtube.com/watch?v=Ljsh5_i_W-w

Chuẩn bị
========

+--------------------+----------------------------------------------------------+
| **Tên board mạch** | **Link**                                                 |
+====================+==========================================================+
| Board IoT Wifi Uno | https://iotmaker.vn/esp8266-iot-wifi-uno.html            |
+--------------------+----------------------------------------------------------+
| OLED 128x64 SH1106 | https://iotmaker.vn/ssd1306-oled-096inch-128x64-i2c.html |
| hoặc SSD1306       |                                                          |
+--------------------+----------------------------------------------------------+
| Mạch điều khiển    | https://iotmaker.vn/mach-dieu-khien-joysticks.html       |
| Joystick           |                                                          |
+--------------------+----------------------------------------------------------+

Hướng dẫn
=========

Vì ESP8266 chỉ có một chân analog, nên ở ví dụ này chúng ta sử dụng thêm IC 74HC4051.
Đây là IC chọn kênh nên chúng ta sẽ dựa vào bảng dưới đây để chọn ra 2 kênh A0 và A1
nhằm đọc xung analog từ 2 chân VRX và VRY của Joystick.

+---------+----------+----------+----------+
|         | **S2**   | **S1**   | **S0**   |
+=========+==========+==========+==========+
| A0      | 0        | 0        | 0        |
+---------+----------+----------+----------+
| A1      | 0        | 0        | 1        |
+---------+----------+----------+----------+
| A2      | 0        | 1        | 0        |
+---------+----------+----------+----------+
| A3      | 0        | 1        | 1        |
+---------+----------+----------+----------+
| A4      | 1        | 0        | 0        |
+---------+----------+----------+----------+
| A5      | 1        | 0        | 1        |
+---------+----------+----------+----------+
| A6      | 1        | 1        | 0        |
+---------+----------+----------+----------+
| A7      | 1        | 1        | 1        |
+---------+----------+----------+----------+

Đấu nối
=======



Cài đặt thư viện
================

+--------------------+----------------------------------------------------------+
| **Thư viện**       | **Link**                                                 |
+====================+==========================================================+
| OLED               | https://github.com/squix78/esp8266-oled-ssd1306          |
+--------------------+----------------------------------------------------------+
| OLED 128x64 SH1106 | https://iotmaker.vn/ssd1306-oled-096inch-128x64-i2c.html |
| hoặc SSD1306       |                                                          |
+--------------------+----------------------------------------------------------+

Lập trình
=========

.. code:: cpp


  #include "SSD1306.h"

  #define S0 12
  #define S1 13
  #define S2 14

  int Xsensor, Ysensor; 

  SSD1306  display(0x3c, 4, 5);

  void setup()
  {
    display.init();
    display.flipScreenVertically();
    display.setFont(ArialMT_Plain_16);
    display.drawString(15, 20, "IotMaker.VN");
    display.display(); 
    delay(2000);
    
    pinMode(S0, OUTPUT);
    pinMode(S1, OUTPUT);
    pinMode(S2, OUTPUT);
  }

  void loop()
  {
    display.clear();
    digitalWrite(S0, LOW);
    digitalWrite(S1, LOW);
    digitalWrite(S2, LOW);
    Xsensor = analogRead(A0);
    
    digitalWrite(S0, HIGH);
    digitalWrite(S1, LOW);
    digitalWrite(S2, LOW);
    Ysensor = analogRead(A0);

    display.setFont(ArialMT_Plain_16);
    display.drawString(0, 0, "X Value: " + String(Xsensor));
    display.drawString(0, 30, "Y Value: " + String(Ysensor));

    delay(100);
    display.display();
  }


Lưu ý
=====

* Có thể xem hướng dẫn cài đặt thư viện tại `đây <https://www.arduino.cc/en/guide/libraries>`_
* Có thể sử dụng OLED ``SS1306`` bằng cách thay đổi ``SSD1306  display(0x3c, 4, 5);``

