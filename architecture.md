
![](images/2.png)

- CEPH Monitor ( MON) : CEPH monitor theo dõi sức khỏe của các cluster bằng cách lưu trữ các trạng thái của cluser. MON  map thông tin của các thành phần  bao gồm OSD map, MON map, PG map và CRUSH map. Các cluster theo dõi trạng thái các node sau đó gửi về cho MON. Các MON không thực sự lưu trữ dữ liệu và sẽ gửi về OSD
- CEPH object storage device ( ODS ) : Khi các client thực hiện write tới cluster, dữ liệu được gửi vào các ODS dưới dạng object. Thực chấy đây là thành phần duy nhất của CEPH Cluster lưu trữu dữ liệu. và cũng lời nơi duy nhất nhận yêu cầu read từ các client. Thông thường, các ODS được gán một ổ cứng vật lý vào cluster. Vì vậy, tổng số các physical disk trong một Cluster sẽ bằng số ODS daemon đang hoạt động 
- CEPH metdata Server ( MDS ) : MDS theo giói hệ thống tập tin và lưu trữ metadata cho CephFs filesystem. CEPH block device và RADOS không yêu cầu metadata vì vậy sẽ không cần làm việc với MDS. MDS không làm việc trực tiếp với các client, nên sẽ giảm một điểm failure . 

- RADOS : Reliable Autonomic Distributed Object Store (RADOS) nền tảng cho CEPH storage cluster.  Mọi thứ được lưu trong CEPH đều là hiển thị như mội đối tượng , nhiệm vụ cả RADOS object store là lưu trữ các đối tượng này mà không quan tâm đến kiểu dữ liệu gốc. . Ngoài ra các layer trong RADOS đảm nhiệm đảm bảo tính nhất quán của dữ liệu trong Cluster . Để làm được điều này, nó thực hiện repication, failure dection, recovery. cũng như di chuyển và cân bằng tải giữa các cụm . " self-healing, self-managing, intelligent storage nodes and lightweight monitors"

- Ceph exposes  RADOS; có thể  acess RADOS qua : 
    - librados : thư viện cung cấp khả năng làm việc dễ đàng cho RADIOS, hỗ trợ các ngôn ngữ PHP, Ruby, Java, C và C++. Nó cung cấp một giao diện cho Ceph storage cluster  ( RADOS), cũng như các dịch vụ các liên quan đến RADOS như RBD, RGW, and CephFS

- Để lưu trữ và truy cập dữ liệu , thành phần sau quản lý với các storage system khác nhau 
   - RADOS block devices (RBDs) : được biết đến với CEPH block storage, cung cấp các block storage theo hướng persistent, có khả năng thin-provision, resizable, và dữ liệu phân toán trên nhiều ODS. 
   - RADOS gateway interface : ( RGW ) : OpenStack Object Storage and Amazon-S3 compatible RESTful interface (see RADOS_Gateway).
   - CephFS :   Sử dụng như file-baste system , hệ thống tệp tuân thủ POSIX.

- CEPH manager : chạy cùng với các dịch vụ giám sát, cung cấp interface cho các dịch vụ giám sát ngoài. 