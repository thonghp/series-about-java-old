# White Paper - Kiến Trúc - Các Nền Tảng

## Mục lục nội dung 

  - [1. White paper](#1-white-paper)
  - [2. Kiến trúc](#2-kiến-trúc)
  - [3. Các nền tảng](#3-các-nền-tảng)

## 1. White paper

Giải thích những lợi ích 1 công nghệ, sản phẩm hay chính sách cụ thể và trong java được thể hiện thông qua 11 từ 

- **Simple ==>** thiết kế **gần với c++**, bỏ qua tính năng ít dùng và khó hiểu 
- **Object oriented ==>** Java không phải là ngôn ngữ thuần hướng đối tượng vì còn có **kiểu dữ liệu nguyên thủy** 
- **Distributed ==>** có 1 thư viện phong phú để đối phó **tcp/ip** như **http và ftp**, có thể mở và truy cập các object trên mạng thông qua **url** 1 cách dễ dàng
- **Robust ==>** kiểm tra lỗi runtime, mô hình con trỏ loại bỏ khả năng ghi đè bộ nhớ và làm hỏng dữ liệu
- **Secure ==>** những mã không đáng tin cậy sẽ được thực thi trong môi trường máy ảo sandbox không thể tác động đến hệ thống server.   
- **Architecture-Neutral ==>** Trình biên dịch tạo ra các lệnh bytecode ko liên quan gì đến kiến trúc máy tính cụ thể mà được thiết kế để thực thi mọi máy
- **Portable ==>** Các kiểu dữ liệu nguyên thuỷ có kích thước cố định 
- **Interpreted ==>** có thể thực thi các mã byte java trực tiếp trên bất kỳ máy nào 
- **High-Performance ==>** nhanh hơn ngôn ngữ lập trình thông dịch (**PHP, Ruby, Js, Python**) truyền thống vì bytecode gần với mã gốc nhưng vẫn chậm hơn ngôn ngữ được biên dịch (**C,C++,Go**)
    - Ngôn ngữ biên dịch được **chuyển đổi trực tiếp thành mã máy** mà bộ xử lý có thể thực thi, cho phép quản lý bộ nhớ, sử dụng cpu, khía cạnh phần cứng **==> cần xây dựng lại mỗi khi có thay đổi**
    - Ngôn ngữ thông dịch **chạy qua từng dòng chương trình và thực hiện từng lệnh** chậm hơn biên dịch nhưng hệ thống biên dịch đúng lúc nên cũng thu hẹp lại tốc độ **==>** Dễ tối ưu hơn
- **Multithreaded ==>** Có thể viết các chương trình có thể thực hiện nhiều tác vụ đồng thời. Ưu điểm chính của đa luồng là nó không chiếm bộ nhớ cho mỗi luồng, nó chia sẻ một vùng bộ nhớ chung
- **Dynamic ==>** Các thư viện có thể tự do thêm các phương thức và biến phiên bản mới mà không có bất kỳ ảnh hưởng nào đến khách hàng của họ.   

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 2. Kiến trúc

![jdk](/assets/jdk.jpg)

- Java Development Kit - `JDK` **==> bộ công cụ phát triển ==> JRE + Development/debugging tools**.

> Ngôn ngữ khác thì jdk chính là sdk

- Java Runtime Environment - `JRE` **==> JVM + Java Packages Classes(like util, math, lang, awt,swing etc) + runtime libraries ==>** Chạy chương trình java **đã biên dịch, không thể tạo chương trình mới**
    - Trên máy người dùng chỉ cần cài JRE là được
    - JRE rời khác JRE trong JDK chổ debug vì chỉ chỉ JRE trong jdk mới đi vào trong lòng mã nguồn, method    
- Java Virtual Machine - `JVM` **==> Class loader system + runtime data area + Execution Engine ==>** quản lý bộ nhớ thông qua `garbage collection`

![architecture](/assets/architecture.jpg)

- **Có 3 giai đoạn** thực thi 1 chương trình **==> viết > biên dịch > chạy** 
    - Trong thời gian chạy **==>** `JVM` thực thi **bytecode**
    - `.class` chỉ phụ thuộc vào code không phụ thuộc vào Platform

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 3. Các nền tảng    

- `Java Standard Edition - Java SE` **==>** dành cho máy tính để bàn và các ứng dụng máy chủ độc lập, là một nền tảng cơ bản cho phép phát triển giao diện điều khiển, các ứng dụng mạng và các ứng dụng dạng WinForm.
- `Java Enterprise Edition - Java EE` **==>** Được xây dựng trên nền tảng Java SE, giúp phát triển các ứng dụng web, các ứng dụng ở cấp doanh nghiệp,…
- `Java Micro Edition - Java ME` **==>** Là một nền tảng cho phép phát triển các ứng dụng nhúng vào các thiết bị điện tử như mobile,…

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [Simple Java Program - Comment - Datatype](/Chap1/Day2.md)