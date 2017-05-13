Hiển thị ký tự với module led matrix MAX7219
--------------------------------------------

Demo
====

.. youtube:: https://www.youtube.com/watch?v=nVMOkoVbVEQ

Chuẩn bị
========

+---------------------------+----------------------------------------------------------+
|    **Tên board mạch**     | **Link**                                                 |
+===========================+==========================================================+
|    Board IoT Wifi Uno     | https://iotmaker.vn/esp8266-iot-wifi-uno.html            |
+---------------------------+----------------------------------------------------------+
| Module led matrix MAX7219 | https://iotmaker.vn/module-led-matrix-max7219.html       |
+---------------------------+----------------------------------------------------------+

Đấu nối
=======

.. image:: ../_static/projects/wifi-uno-led-matrix-max7219_bb.jpg
    :target: ../_static/projects/wifi-uno-led-matrix-max7219.fzz

Cài đặt thư viện
================

+--------------------+----------------------------------------------------------+
| **Thư viện**       | **Link**                                                 |
+====================+==========================================================+
| Thư viện LedMatrix | https://github.com/dbu/arduino-LedMatrix                 |
+--------------------+----------------------------------------------------------+

Lập trình
=========

.. code:: cpp

    #include <SPI.h>
    #include "LedMatrix.h"
    // connect DIN to GPIO13
    // connect CLK to GPIO14
    #define NUMBER_OF_DEVICES 1
    #define CS_PIN 2            // CS ket noi voi GPIO02
    LedMatrix ledMatrix = LedMatrix(NUMBER_OF_DEVICES, CS_PIN);

    void setup() {
      Serial.begin(115200);
      ledMatrix.init();
      ledMatrix.setIntensity(5);       // dieu chinh muc do sang cho led
      ledMatrix.setText("IoTmaker.vn"); //noi dung muon hien thi
    }

    void loop() {
      ledMatrix.clear();
      ledMatrix.scrollTextLeft();
      ledMatrix.drawText();
      ledMatrix.commit();
      delay(100);
    }

Lưu ý
=====

* Cần nạp chương trình xong, sau đó kết nối board với module led matrix MAX7219 sau.

