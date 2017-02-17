Lập trình ESP8266 Arduino
=========================

Đây là một dự án mã nguồn mở giúp hỗ trợ môi trường phát triển Arduino cho ESP8266. Giúp bạn có thể viết 1 Sketches sử dụng các thư viện và hàm tương tự của Arduino, có thể chạy trực tiếp trên ESP8266 mà không cần bất kỳ Vi điều khiển nào khác.

ESP8266 Arduino core đi kèm với thư viện kết nối WiFi hỗ trợ TCP, UDP và các ứng dụng HTTP, mDNS, SSDP, DNS Servers. Ngoài ra còn có thể thực hiện cập nhật OTA, sử dụng Filesystem dùng bộ nhớ Flash hay thẻ SD, điều khiển servos, ngoại vi SPI, I2C.


Nội dung:

.. toctree::
   :caption: Cài đặt
   :maxdepth: 1

   Arduino <install>
   Board mạch <install>

.. Connect - TBA

.. toctree::
   :caption: Build and Flash
   :maxdepth: 1

   Make <make-project>
   Eclipse IDE <eclipse-setup>

.. toctree::
   :caption: What Else?
   :maxdepth: 1

   General Notes <general-notes>
   Build System <build-system>
   Debugging <openocd>
   ESP32 Core Dump <core_dump>
   Partition Tables <partition-tables>
   Flash Encryption <security/flash-encryption>
   Secure Boot <security/secure-boot>
   Deep Sleep Wake Stubs <deep-sleep-stub>
   ULP Coprocessor <ulp>
   Unit Testing <unit-tests>

.. toctree::
   :caption: API Reference
   :maxdepth: 2

   Wi-Fi <api/wifi/index>
   Bluetooth <api/bluetooth/index>
   Ethernet <api/ethernet/index>
   Peripherals <api/peripherals/index>
   System <api/system/index>
   Storage <api/storage/index>
   Protocols <api/protocols/index>

.. toctree::
   :caption: Tham khảo phần cứng

   Technical Reference Manual (PDF) <http://espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_en.pdf>
   Pin List and Functions (PDF) <http://espressif.com/sites/default/files/documentation/esp32_chip_pin_list_en.pdf>
   Chip Pinout (PDF) <http://espressif.com/sites/default/files/documentation/esp32_pinout_v1_0.pdf>
   Silicon Errata (PDF) <http://espressif.com/sites/default/files/documentation/eco_and_workarounds_for_bugs_in_esp32_en.pdf>

.. toctree::
   :caption: Contribute
   :maxdepth: 1

   Contributions Guide <contributing>
   Style Guide <style-guide>
   Documenting Code <documenting-code>
   Contributor Agreement <contributor-agreement>

.. toctree::
   :caption: Legal
   :maxdepth: 1

   COPYRIGHT


Indices
=======

* :ref:`genindex`
