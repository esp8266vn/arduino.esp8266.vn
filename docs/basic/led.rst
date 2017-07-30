 LED
---

Chúng ta sẽ thực hiện việc chớp tắt đèn LED của board **IoT WiFi Uno** mỗi giây, được nối tới pin ``GPIO16``.

Xem video hướng dẫn và kết quả:

.. youtube:: https://www.youtube.com/watch?v=8jM-JTFeAlg


Chuẩn bị
========

+--------------------+----------------------------------------------------------+
| **Tên board mạch** | **Link**                                                 |
+====================+==========================================================+
| Board IoT Wifi Uno | https://iotmaker.vn/esp8266-iot-wifi-uno.html            |
+--------------------+----------------------------------------------------------+


Đấu nối
=======

Nút nhấn và LED board ``IoT WiFi Uno`` được khoanh tròn như trong hình

.. image:: ../_static/basic/button.png
    :target: ../_static/basic/button.png

Chớp tắt dùng Delay
===================

Với cách chớp tắt này sẽ làm CPU bị dừng tại thời điểm delay và không thực thi được code nào khác

.. code:: cpp

    int ledPin = 16;                 // LED connected to digital pin 16

    void setup()
    {
      pinMode(ledPin, OUTPUT);      // sets the digital pin as output
    }

    void loop()
    {
      digitalWrite(ledPin, HIGH);   // sets the LED on
      delay(1000);                  // waits for a second
      digitalWrite(ledPin, LOW);    // sets the LED off
      delay(1000);                  // waits for a second
    }



Chớp tắt dùng định thời
=======================

.. code:: cpp

    int ledPin = 16;                 // LED connected to digital pin 16
    int ledState = LOW;
    unsigned long previousMillis = 0;
    const long interval = 1000;

    void setup() {
      pinMode(ledPin, OUTPUT);
    }

    void loop()
    {
      unsigned long currentMillis = millis();
      if(currentMillis - previousMillis >= interval) {
        previousMillis = currentMillis;
        if (ledState == LOW)
          ledState = HIGH;  // Note that this switches the LED *off*
        else
          ledState = LOW;   // Note that this switches the LED *on*
        digitalWrite(ledPin, ledState);
      }
    }


Digital IO
==========

Tên chân trong Arduino (Pin number) giống với thứ tự chân của ESP8266.
``pinMode``, ``digitalRead``, và ``digitalWrite`` đều sử dụng Pin Number
như nhau, ví dụ như đọc GPIO2, gọi hàm ``digitalRead(2)``.

Chân GPIO0..15 có thể là ``INPUT``, ``OUTPUT``, hay ``INPUT_PULLUP``.
Chân GPIO16 có thể là ``INPUT``, ``OUTPUT`` hay ``INPUT_PULLDOWN_16``.
Khi khởi động, tất cả các chân sẽ được cấu hình là ``INPUT``.

Mỗi chân có thể phục vụ cho một tính năng nào đó, ví dụ ``Serial``,
``I2C``, ``SPI``. Và tính năng đó sẽ được cấu hình đúng khi sử dụng thư
viện. Hình bên dưới thẻ hiện sơ đồ chân đối với module ESP-12 phổ biến.


GPIO6 và GPIO11 không được thể hiện bởi vì nó được sử dụng cho việc kết
nối với Flash. Việc sử dụng 2 chân này có thể gây lỗi chương trình.

.. note::
    Một số board và module khác (ví dụ ESP-12ED, NodeMCU 1.0) không có GPIO9 và GPIO11, họ sử dụng với chế độ ``DIO`` cho Flash, trong khi ESP12 chúng ta nói bên trên sử dụng chế độ ``QIO``

Ngắt GPIO hỗ trợ thông qua các hàm ``attachInterrupt``, ``detachInterrupt``
Ngắt GPIO có thể gán cho bất kỳ GPIO nào, ngoại trừ ``GPIO16``. Đều hỗ trợ các ngắt tiêu chuẩn của Arduino như: ``CHANGE``, ``RISING``, ``FALLING``.



