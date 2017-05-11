Lập trình ESP8266 Arduino
=========================

Đây là một dự án mã nguồn mở giúp hỗ trợ môi trường phát triển Arduino cho ESP8266. Giúp bạn có thể viết 1 Sketches sử dụng các thư viện và hàm tương tự của Arduino, có thể chạy trực tiếp trên ESP8266 mà không cần bất kỳ Vi điều khiển nào khác.

ESP8266 Arduino core đi kèm với thư viện kết nối WiFi hỗ trợ TCP, UDP và các ứng dụng HTTP, mDNS, SSDP, DNS Servers. Ngoài ra còn có thể thực hiện cập nhật OTA, sử dụng Filesystem dùng bộ nhớ Flash hay thẻ SD, điều khiển servos, ngoại vi SPI, I2C.

.. image:: _static/Iot-wifi-uno-hw-pinout.png
   :width: 500

Dự án hỗ trợ và phát triển bởi `IoT Maker Việt Nam <https://iotmaker.vn>`_



.. toctree::
   :caption: Cơ bản
   :maxdepth: 2

   Cài đặt <basic/index>
   Bật tắt LED <basic/led>
   Nút nhấn <basic/button>
   Sử dụng Promem <basic/promem>
   Ngoại vi <peripherals/index>
   Wi-Fi <wifi/index>

.. toctree::
   :caption: Network/Protocol
   :maxdepth: 1

   HTTP Client <network/http-client>
   HTTP Server <network/http-server>
   MQTT <network/mqtt>
   Websocket <network/websocket>
   mDNS <network/mdns>
   CoAP <network/coap>
   Cập nhật firmware <network/ota>

.. toctree::
   :caption: Dự án
   :maxdepth: 1

   Game Flappy Bird <projects/flappy-bird>
   Đo nhịp tim <projects/heart-rate>
   Cảm biến nhiệt độ (onewire) <projects/onewire>
   Đo nhiệt độ độ ẩm và gởi lên Thingspeak <projects/dht11-thingspeak>
   Photodiode <projects/sensor-photodiode>
   Cảm biến chuyển động HC-SR501 <projects/PIR>
   Cảm biến áp suất BMP280 <projects/BMP280>
   Led 7 đoạn 4 số <projects/4led7seg>
   Hiển thị ký tự với module led matrix MAX7219 <projects/led-matrix-max7219>
   Đọc dữ liệu từ Joystick <projects/joystick>
   Vòng 12 LED RGB <projects/led-12>
   Cảm biến âm thanh <projects/sensor-voice>
   
.. toctree::
   :caption: API
   :maxdepth: 1

.. toctree::
   :caption: Tài liệu ESP8266

   Technical Reference Manual (PDF) <https://espressif.com/sites/default/files/documentation/esp8266-technical_reference_en.pdf>
   Pin List and Functions (XLSX) <https://espressif.com/sites/default/files/documentation/0d-esp8266_pin_list_release_15-11-2014.xlsx>
   Tài nguyên chính thống <https://espressif.com/en/products/hardware/esp8266ex/resources>

.. toctree::
   :caption: Đóng góp và bản quyền
   :maxdepth: 1

   Hướng dẫn đóng góp <contributing>



Indices
=======

* :ref:`genindex`
