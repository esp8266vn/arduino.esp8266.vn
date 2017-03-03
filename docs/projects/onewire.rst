Onewire
-------
Đọc cảm biến nhiệt độ DS18B20 và hiển thị ra OLED

Demo
====

.. youtube:: https://www.youtube.com/watch?v=xwWSdrXhcqo

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
| Cảm biến nhiệt độ  | https://iotmaker.vn/cam-bien-nhiet-do-probe-ds18b20.html |
| DS18B20            |                                                          |
+--------------------+----------------------------------------------------------+

Đấu nối
=======

.. image:: ../_static/projects/iot-uno-onewirte_bb.png
    :target: ../_static/projects/iot-uno-onewirte.fzz

Cài đặt thư viện
================

+--------------------+----------------------------------------------------------+
| **Thư viện**       | **Link**                                                 |
+====================+==========================================================+
| OneWire            | https://github.com/PaulStoffregen/OneWire                |
+--------------------+----------------------------------------------------------+
| DallasTemperature  | https://github.com/adafruit/MAX31850_DallasTemp          |
+--------------------+----------------------------------------------------------+
| OLED               | https://github.com/squix78/esp8266-oled-ssd1306          |
+--------------------+----------------------------------------------------------+


Lập trình
=========

.. code:: cpp

    #include "SH1106.h"
    SH1106  display(0x3c, 4, 5);
    #include <OneWire.h>
    #include <DallasTemperature.h>


    // OneWire DS18S20, DS18B20, DS1822 Temperature Example

    OneWire  ds(2);  // on pin D4 (a 4.7K resistor is necessary)
    DallasTemperature DS18B20(&ds);

    char temperatureCString[10];
    char temperatureFString[10];

    void getTemperature() {
      float tempC;
      float tempF;
      do {
        DS18B20.requestTemperatures();
        tempC = DS18B20.getTempCByIndex(0);
        dtostrf(tempC, 2, 2, temperatureCString);
        tempF = DS18B20.getTempFByIndex(0);
        dtostrf(tempF, 3, 2, temperatureFString);
        delay(100);
      } while (tempC == 85.0 || tempC == (-127.0));
    }

    void setup() {
      // put your setup code here, to run once:
      Serial.begin(115200);
      display.init();
      display.flipScreenVertically();
      display.setFont(ArialMT_Plain_24);
      DS18B20.begin();
      pinMode(2, INPUT_PULLUP);
    }

    void loop() {
      // put your main code here, to run repeatedly:
      Serial.print("  Reading \n");
      getTemperature();
      display.clear();
      display.drawString(0, 0, temperatureCString);
      display.display();
    }

Lưu ý
=====

* Có thể xem hướng dẫn cài đặt thư viện tại `đây <https://www.arduino.cc/en/guide/libraries>`_
* Có thể sử dụng OLED ``SS1306`` bằng cách thay đổi ``SSD1306  display(0x3c, 4, 5);``

