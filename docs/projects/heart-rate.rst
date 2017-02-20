Do nhịp tim và hiển thị trên OLED
---------------------------------

Demo
====

.. youtube:: https://www.youtube.com/watch?v=KVyuZBbViIM

Chuẩn bị
========

+--------------------+----------------------------------------------------------+
| **Tên board mạch** | **Link**                                                 |
+--------------------+----------------------------------------------------------+
| Board IoT Wifi Uno | https://iotmaker.vn/esp8266-iot-wifi-uno.html            |
+--------------------+----------------------------------------------------------+
| OLED 128x64 SH1106 | https://iotmaker.vn/ssd1306-oled-096inch-128x64-i2c.html |
| hoặc SSD1306       |                                                          |
+--------------------+----------------------------------------------------------+
| Cảm biến nhịp tim  | https://iotmaker.vn/cam-bien-nhip-tim-max30100.html      |
| MAX30100           |                                                          |
+--------------------+----------------------------------------------------------+

Đấu nối
=======

.. image:: ../_static/projects/iot-uno-heartrate_bb.png
    :target: ../_static/projects/iot-uno-heartrate.fzz

Cài đặt thư viện
================
* Thư viện OLED: https://github.com/squix78/esp8266-oled-ssd1306
* Thư viện MAX30100: https://github.com/oxullo/Arduino-MAX30100


Video Cài đặt
=============

.. youtube:: https://www.youtube.com/watch?v=bkH-wATlyNU

Lập trình
=========

.. code:: cpp


    #include "MAX30100_PulseOximeter.h"
    #include "SH1106.h"

    #define REPORTING_PERIOD_MS     1000

    // PulseOximeter is the higher level interface to the sensor
    // it offers:
    //  * beat detection reporting
    //  * heart rate calculation
    //  * SpO2 (oxidation level) calculation
    PulseOximeter pox;



    SH1106  display(0x3c, 4, 5);

    uint32_t tsLastReport = 0;

    // Callback (registered below) fired when a pulse is detected
    void onBeatDetected()
    {
        Serial.println("Beat!");
    }

    void setup()
    {
        Serial.begin(115200);

        // Initialize the PulseOximeter instance and register a beat-detected callback
        pox.begin();
        pox.setOnBeatDetectedCallback(onBeatDetected);
        display.init();

        display.setFont(ArialMT_Plain_16);
    }

    void loop()
    {
        // Make sure to call update as fast as possible
        pox.update();

        // Asynchronously dump heart rate and oxidation levels to the serial
        // For both, a value of 0 means "invalid"
        if (millis() - tsLastReport > REPORTING_PERIOD_MS) {
            display.clear();
            display.drawString(0, 0, "HR: " + String(pox.getHeartRate()) + " bpm");
            display.drawString(0, 32, "SpO2: " + String(pox.getSpO2()) +" %");
            display.display();
            Serial.print("Heart rate:");
            Serial.print(pox.getHeartRate());
            Serial.print("bpm / SpO2:");
            Serial.print(pox.getSpO2());
            Serial.println("%");

            tsLastReport = millis();
        }
    }
