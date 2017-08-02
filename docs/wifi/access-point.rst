WiFi Access Point
=================

**Access Point** (AP - Điểm truy cập) cung cấp khả năng truy cập mạng WiFi cho các thiết bị khác (Station) và kết nối chúng với mạng có dây. ESP8266 có thể làm một AP nhưng nó không kết nối có dây với một mạng. Chế độ hoạt động như vậy gọi là **soft-AP**. Số lượng trạm tối đa kết nối với soft-AP là 5

.. image:: ../wifi/esp8266-soft-access-point.png

Phần mô tả API này gồm có 3 phần: cách thiết lập soft-AP, quản lý kết nối và lấy thông tin về cấu hình soft-AP.

Mục lục
------

* :ref:`Về Access Point 0` 

* :ref:`Thiết lập mạng0` 

  - :ref:`softAP0` 
  - :ref:`softAPConfig0` 

* :ref:`Quản lý kết nối0` 

  - :ref:`softAPdisconnect0` 
  - :ref:`softAPgetStationNum0` 
 
* :ref:`Cấu hình mạng0` 

  - :ref:`softAPIP0` 
  - :ref:`softAPmacAddress0` 

.. _Về Access Point 0:

Về Access Point
---------------

Chế độ soft access point (soft-AP) được dùng 

The soft-AP mode is often used and an intermediate step before connecting ESP to a Wi-Fi in a station mode. This is when SSID and 
password to such network is not known upfront. ESP first boots in soft-AP mode, so we can connect to it using a laptop or a mobile phone. Then we are able to provide credentials to the target network. Once done ESP is switched to the station mode and can connect to the target Wi-Fi.

Another handy application of soft-AP mode is to set up mesh networks. ESP can operate in both soft-AP and Station mode so it can act as a node of a mesh network.

.. _Thiết lập mạng0:

Thiết lập mạng
--------------

Phần này mô tả các chức năng để thiết lập và cấu hình ESP8266 ở chế độ soft-AP.

.. _softAP0:

softAP
~~~~~~

Cách thiết lập đơn giản nhất chỉ yêu cầu một tham số và được sử dụng để thiết lập một mạng Wi-Fi mở.

``WiFi.softAP (ssid)``

Để thiết lập mạng được bảo vệ bằng mật khẩu, hoặc để cấu hình các thông số mạng bổ sung, sử dụng quá tải sau đây:

``WiFi.softAP(ssid, password, channel, hidden)``

Tham số đầu tiên của hàm này là bắt buộc, còn lại ba tùy chọn.

* ssid - chuỗi ký tự chứa SSID mạng (tối đa 63 ký tự)
* password - chuỗi ký tự tùy chọn với mật khẩu. Đối với mạng WPA2-PSK, nó phải có ít nhất 8 ký tự. Nếu không được chỉ định, điểm truy cập sẽ mở ra cho bất kỳ ai kết nối.
* channel - Tham số tùy chọn để thiết lập kênh Wi-Fi, từ 1 đến 13. Kênh mặc định = 1.
* hidden - Tham số tùy chọn, thiết lập là true để ẩn SSID

Trả về ``true`` hoặc ``false`` phụ thuộc vào kết quả của việc cài đặt soft-AP.

.. note::
    
    * Mạng được thiết lập bởi softAP sẽ có địa chỉ IP mặc định là 192.168.4.1. Địa chỉ này có thể được thay đổi bằng cách sử dụng softAPConfig
    * Mặc dù ESP8266 có thể hoạt động đưuọc ở chế độ softAP + station, nó thực sự chỉ có một kênh phần cứng. Do đó trong chế độ softAP, ESP8266 sẽ điều chỉnh channel của nó giống như trong chế độ station. Tham khảo thêm tại `đây <http://bbs.espressif.com/viewtopic.php?f=10&t=324>`_

.. _Cấu hình softAP0:

Cấu hình softAP
~~~~~~~~~~~~~~~

``softAPConfig(local_ip, gateway, subnet)``

Tất cả các thông số đều có kiểu ``IPAddress`` và được định nghĩa như sau:

* local_ip - Địa chỉ IP của điểm truy cập mềm
* gateway - địa chỉ IP gateway
* subnet - mặt nạ mạng con

Trả về ``true`` hoặc ``false`` phụ thuộc vào kết quả của việc thay đổi cấu hình.

.. code:: cpp

	#include <ESP8266WiFi.h>

	IPAddress local_IP(192,168,4,22);
	IPAddress gateway(192,168,4,9);
	IPAddress subnet(255,255,255,0);

	void setup()
	{
	  Serial.begin(115200);
	  Serial.println();

	  Serial.print("Setting soft-AP configuration ... ");
	  Serial.println(WiFi.softAPConfig(local_IP, gateway, subnet) ? "Ready" : "Failed!");

	  Serial.print("Setting soft-AP ... ");
	  Serial.println(WiFi.softAP("ESPsoftAP_01") ? "Ready" : "Failed!");

	  Serial.print("Soft-AP IP address = ");
	  Serial.println(WiFi.softAPIP());
	}

	void loop() {}

*output*

.. code:: cpp

	Setting soft-AP configuration ... Ready
	Setting soft-AP ... Ready
	Soft-AP IP address = 192.168.4.22

.. _Quản lý Mạng0:	

Quản lý Mạng
------------

Khi đã thiết lập softAP, bạn có thể kiểm tra các trạm đã kết nối, hoặc tắt chúng, sử dụng các hàm sau:

.. _softAPgetStationNum0:

softAPgetStationNum
^^^^^^^^^^^^^^^^^^^

Lấy số lượng các station kết nối đến softAP

``WiFi.softAPgetStationNum()``

.. code:: cpp

	Serial.printf("Stations connected to soft-AP = %d\n", WiFi.softAPgetStationNum());

DEMO:

Trả về số lượng các thiết bị (station) kết nối tới mạng Wifi thiết lập bởi ESP8266

.. code:: cpp

	 #include <ESP8266WiFi.h>

     void setup()
     {
     WiFi.softAP("31/8/2017");
     Serial.begin(115200);

     }
     void loop() 
     {
     Serial.printf("Stations connected to soft-AP = %d \n", WiFi.softAPgetStationNum());
 	 delay(2000); //delay trong 2s để kiểm tra xem có thiết bị nào mới kết nối với module không ?
     }


*output*

        .. image:: ../wifi/softAPgetStationNum.png

Ta thấy có 1 thiết bị kết nối tới mạng WIFI: "31/8/2017"

	

Lưu ý: số lượng trạm tối đa có thể kết nối với phần mềm ESP8266 là 5.

.. _softAPdisconnect0:

softAPdisconnect
~~~~~~~~~~~~~~~~

Ngắt kết nối các trạm từ mạng được thiết lập bởi softAP.

``WiFi.softAPdisconnect(wifioff)``

Chức năng sẽ thiết lập cấu hình SSID và password của soft-AP giá trị là ``null``. Tham số ``wifioff`` là tùy chọn. Nếu thiết lập là ``true`` nó sẽ tắt chế độ soft-AP.

Trả về ``true`` nếu hoạt động đã thành công, ``false`` nếu không.

.. _Cấu hình Mạng0:

Cấu hình Mạng
-------------

Các hàm dưới đây cung cấp địa chỉ IP và MAC của soft-AP của ESP8266.

.. _softAPIP0:

softAPIP
~~~~~~~~

Trả lại địa chỉ IP của mạng softAP.

``WiFi.softAPIP()``

Trả về giá trị có kiểu là ``IPAddress``.

.. code:: cpp

	Serial.print("Soft-AP IP address = ");
	Serial.println(WiFi.softAPIP());

*output*

.. code:: cpp

	Soft-AP IP address = 192.168.4.1

.. _softAPmacAddress0:

softAPmacAddress
~~~~~~~~~~~~~~~~

Trả lại địa chỉ MAC của softAP. Chức năng này có hai phiên bản khác nhau về kiểu trả về. Trả về một con trỏ hoặc một ``String``.

Con trỏ

``WiFi.softAPmacAddress(mac)``

Tham số mac là một con trỏ trỏ đến vị trí bộ nhớ (một mảng ``uint8_t`` có 6 phẩn tử) để lưu địa chỉ mac. Cùng một giá trị con trỏ được trả về bởi chính hàm đó.

.. code:: cpp

	uint8_t macAddr[6];
	WiFi.softAPmacAddress(macAddr);
	Serial.printf("MAC address = %02x:%02x:%02x:%02x:%02x:%02x\n", macAddr[0], macAddr[1], macAddr[2], macAddr[3], macAddr[4], macAddr[5]);

*output*

.. code:: cpp

	MAC address = 5e:cf:7f:8b:10:13

MAC như một ``String``

``WiFi.softAPmacAddress()``

Kiểu trả về là một ``String`` chứa địa chỉ MAC của softAP.

.. code:: cpp

	Serial.printf("MAC address = %s\n", WiFi.softAPmacAddress().c_str());

*output*

.. code:: cpp

	MAC address = 5E:CF:7F:8B:10:13


