Các khái niệm cơ bản về WiFi
============================

* :ref:`Station và Access Point0`
* :ref:`Hotspot0` 
* :ref:`Các chuẩn bảo mật WiFi0`

  - :ref:`WEP0`  
  - :ref:`WPA0` 
  - :ref:`WPA 2 0`

* :ref:`Port (trong mạng máy tính) 0`
* :ref:`Client và Server 0`




.. _Station và Access Point0:

Station vả Access Point
-----------------------


Thiết bị kết nối vào mạng WIFI được gọi là station (trạm). Việc kết nối vào mạng Wifi được hỗ trợ bởi một access point (AP), một AP có chức năng như một hub nhưng dùng cho nhiều station. Một access point thông thường được kết nối vào một mạng dây để phát WIFI (tức là chuyển từ mạng dây sang WIFI). Do đó access point luôn được tích hợp vào router. Mỗi access point được nhận biết bằng một SSID (Service Set IDentifier), SSID cũng là tên của mạng hiển thị khi ta kết nối vào WIFI.

.. _Hotspot0:

Hotspot
---------------

Một hotspot là một nơi mà các thiết bị có thể kết nối Internet, và thường là bằng WiFi, thông qua mạng WLAN (wireless local area network: mạng nội bộ không dây) nối với router.

.. _Các chuẩn bảo mật WiFi0:

Các chuẩn bảo mật WiFi
----------------------

.. _WEP0:

WEP
~~~~~~

WEP (Wired Equivalent Privacy) là một gỉai thuật bảo mật cho mạng không dây chuẩn IEEE 802.11. Ban đầu, các nhà sản xuất chỉ sản xuất các thiết bị WiFI với chuẩn bảo mật 64 bit. Sau này có các cải tiến hơn với các chuẩn bảo mật 128 bit và 256 bit. 
Bảo mật WEP sau đó xuất hiện nhiều lổ hổng. Các khóa WEP ngày nay có thể bị crack trong một vài phút các bằng phần mềm hoàn toàn miễn phí trên mạng. Vào năm 2004, với sự phát triển của các chuẩn bảo mật mới như WPA, WPÀ2, IEEE tuyên bố các chuẩn WEP trong bảo mật WiFi sẽ không còn được hỗ trợ.

.. _WPA0:

WPA
~~~~~~

WPA (Wi-Fi Protected Access) là giao thức và chuẩn bảo mật WiFi phát triển bởi Liên hiệp Wifi (Wifi Alliance). WPA được phát triển để thay thế cho chuẩn WEP trước đó có nhiều lỗ hổng bảo mật.

Phiên bản phổ biến nhất của WPA là WPA-PSK (Pre-Shared Key). Các kí tự được sử dụng bởi WPA là loại 256 bit, nên tính bảo mật sẽ cao hơn rất nhiều so với mã hóa 64 bit và 128 bit có trong hệ thống WEP. Trong WPA có hỗ trợ TKIP (Temporal Key Integrity Protocol). TKIP sử dụng các gỉai thuật để đảm bảo an toàn cho các gói tin truyền trong WIFI để tránh bị đánh cắp. Tuy nhiên TKIP sau này cũng bộc lộ một số lổ hổng bảo mật và bị thay thế bởi AES (Advanced Encryption Standard). Giao thức AES được dùng trong cả WPA và WPA 2.

.. _WPA 2 0:

WPA 2
~~~~~~

WPA 2 ( WiFi Protected Access II ) là giao thức và chuẩn bảo mật thay thế cho WPA từ năm 2006 và được xem là chuẩn bảo mật an toàn nhất đến thời điểm này. Ngoài việc sử dụng giao thức AES,thì WPA 2 còn sử dụng thêm giao thức mã hóa CCMP (CTR mode with CBC-MAC Protocol). Giao thức CCMP là một giao thức truyền dữ liệu và kiểm soát tính truyền dữ liệu thống nhất để bảo đảm cả tính bảo mật và nguyên vẹn của dữ liệu được truyền đi.
Cho đến nay thì giao thức bảo mật WPA2 dùng AES là giao thức bảo mật Wifi tốt nhất.

.. _Port (trong mạng máy tính) 0:

Port (trong mạng máy tính)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Trong giao thức mạng máy tính, port là một điểm đích (endpoint) trong giao tiếp ở một hệ điều hành. Cần phân biệt khái niệm Port trong mạng máy tính với Port trong phần cứng, port trong phần cứng là đầu kết nối female của thiết bị phần cứng. Với giao thức mạng máy tính, Port được dùng để nhận biết một qui trình đặc biệt hay một dịch vụ mạng nào đó.

Một port thường kết hợp với một địa chỉ IP của một host và dạng giao thức của giao tiếp mạng tương ứng, do đó sẽ hoàn thành việc xác định đich đến của một giao tiếp mạng. Một port sẽ được xác định bằng một số 16 bit, thường được gọi là port number (số port). Ví dụ, các thông tin về một giao thức mạng sẽ là: "Giao thức mạng: TCP, IP: 1.2.3.4, port number: 80", ta có thể viết lại thành 1.2.3.4:80.

Các số thứ tự port được dùng để nhận biết một dịch vụ mạng đặc biệt. Ta có danh sách `1024 port thông dụng`_ được dùng để xác định các dịch vụ đặc biệt trên một host.


.. _Client và Server 0:

Client và Server
~~~~~~~~~~~~~~~~

Client là một nhóm các phần cứng hoặc phần mềm máy tính truy cập vào một dịch vụ cung cấp bởi Server. Server có thể hiểu đơn gỉan là một máy tính chứa dữ liệu hoặc dịch vụ mà Client có thể truy cập tới, tuy nhiên không phải tất cả server đều là máy tính. Client sẽ truy cập vào dịch vụ của server thông qua hệ thống mạng, thường là Internet. Từ đây, ta có mô hình client-server

.. image:: ../_static/wifi/Client-server-model.png

Một ví dụ điển hình của mô hinh client-server là việc truy cập của web browser: các web browser là những client kết nối tới web server để được truy cập vào các trang web. Các ví dụ khác của mô hình client-server có thể kể đến như: Email client nhận email từ mail server; các ứng dụng chat online, game online với mỗi máy khi đó sẽ là một client.

.. _1024 port thông dụng: https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Well-known_ports
