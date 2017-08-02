Lớp Scan trong thư viện ESP8266WiFi
======================

* :ref:`Giới thiệu về lớp Scan0`
  - :ref:`Hotspot0` 
  - :ref:`Tổng quát về scanNetworks0`  

* :ref:`Thiết lập mạng0` 

  - :ref:`softAP0` 
  - :ref:`softAPConfig0` 

* :ref:`Quản lý kết nối0` 

  - :ref:`softAPdisconnect0` 
  - :ref:`softAPgetStationNum0` 
 
* :ref:`Cấu hình mạng0` 

  - :ref:`softAPIP0` 
  - :ref:`softAPmacAddress0`


.. _Giới thiệu về lớp Scan0:

Giới thiệu về lớp Scan
----------------------

.. _Hotspot0
Hotspot
^^^^^^^^
Một hotspot là một nơi mà các thiết bị có thể kết nối Internet, và thường là bằng WiFi, thông qua mạng WLAN (wireless local area network: mạng nội bộ không dây) nối với router.

Tổng quát về scanNetworks
^^^^^^^^^^^^^^^^^^^^^^^^^^

Đế kết nối smart phone tới một hotspot, ta mở chức năng setting Wifi trên smart phone, tìm Wifi cần kết nối và chọn kết nối. Với ESP8266, ta có thể làm điều tương tự như thế với hàm WiFi.scanNetworks() cho kết quả trả về là số lượng các WIFI (có mật khẩu và không có mật khẩu) mà module có thế kết nối được.


Scan for Networks
^^^^^^^^^^^^^^^^^

scanNetworks

Hàm scanNetworks thưc hiện scan các Wifi trong vùng mà module có thể kết nối được và kết quả trả về là số lượng các WIFI (ta lập trình để kết quả hiển thị trên Serial Monitor).

``WiFi.scanNetworks()``

Code demo:
.. code:: cpp

    #include <ESP8266WiFi.h>


    void setup()
   {
   Serial.begin(115200);

   Serial.println("** Scan Networks **");

   int numSsid = WiFi.scanNetworks();

   Serial.print("SSID List:");
   Serial.println(numSsid);


   } 
   void loop()
   {

   }

Kết quả:
.. image:: ../wifi/scanNetworks.png


Check for result of asynchronous scanning.

WiFi.scanComplete()
^^^^^^^^^^^^^^^^^^^

Hàm WiFi.scanComplete()


On scan completion function returns the number of discovered networks.

If scan is not done, then returned value is < 0 as follows: * Scanning still in progress: -1 * Scanning has not been triggered: -2
scanDelete

Delete the last scan result from memory.

WiFi.scanDelete()

scanNetworksAsync

Start scanning for available Wi-Fi networks. On completion execute another function.

WiFi.scanNetworksAsync(onComplete, show_hidden)

Function parameters: * onComplete - the event handler executed when the scan is done
* show_hidden - optional boolean parameter, set it to true to scan for hidden networks

Example code:

#include "ESP8266WiFi.h"

void prinScanResult(int networksFound)
{
  Serial.printf("%d network(s) found\n", networksFound);
  for (int i = 0; i < networksFound; i++)
  {
    Serial.printf("%d: %s, Ch:%d (%ddBm) %s\n", i + 1, WiFi.SSID(i).c_str(), WiFi.channel(i), WiFi.RSSI(i), WiFi.encryptionType(i) == ENC_TYPE_NONE ? "open" : "");
  }
}


void setup()
{
  Serial.begin(115200);
  Serial.println();

  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);

  WiFi.scanNetworksAsync(prinScanResult);
}


void loop() {}

Example output:

5 network(s) found
1: Tech_D005107, Ch:6 (-72dBm)
2: HP-Print-A2-Photosmart 7520, Ch:6 (-79dBm)
3: ESP_0B09E3, Ch:9 (-89dBm) open
4: Hack-4-fun-net, Ch:9 (-91dBm)
5: UPC Wi-Free, Ch:11 (-79dBm)



OTA có thể thực hiện với: 

-  :ref:`Arduino IDE0` 
-  :ref:`Web Browser0`
-  :ref:`HTTP Server0`