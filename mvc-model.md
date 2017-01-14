# MVC Model

MVC là chữ viết tắt của Model - View - Controller, đây là một mô hình kiến phần mềm được tạo ra với mục đích quản lý và xây dựng dự án phần mềm có hệ thống hơn. Mô hình này được dùng khá rộng rãi và đặc biệt là trong các ngôn ngữ lập trình web. Trong PHP hiện tại có khá nhiều Framework và tất cả đều xây dựng từ mô hình MVC, từ đó bạn có thể thấy sự quan trọng của nó như thế nào rồi đấy.

Trong mô hình này thì:

* Model: có nhiệm vụ thao tác với cơ sở dữ liệu, nghĩa là nó sẽ chứa tất cả các hàm, các phương thức truy vấn trực tiếp với dữ liệu và controller sẽ thông qua các hàm, phương thức đó để lấy dữ liệu rồi gửi qua View

* View: có nhiệm vụ tiếp nhận dữ liệu từ controller và hiển thị nội dung sang các đoạn mã HTML, bạn có thể hiểu nôm na đây người ta còn gọi là thành phần giao diện.

* Controller: đóng vài trò trung gian giữa Model và View. Nó có nhiệm vụ tiếp nhận yêu cầu từ client sau đó xử lý request, load model tương ứng và gửi data qua view tương ứng rồi trả kết quả về cho client

Để rõ ràng hơn thì bạn xem hình dưới đây:

![](/assets/mo-hinh-mvc-trong-php.png)

Nhìn vào mô hình này các bạn thấy giữa model và view không hề có mối liên hệ mà nó sẽ thông qua controller để giao tiếp với nhau. Hiện trên mạng có khá nhiều mô hình vẽ ra nhưng mình thấy nó quá rắc rối nên mình chọn hình này cho bạn dễ hiểu nhất.

Để hiểu rõ hơn về mô hình MVC, các bạn có thể tham khảo video [https://www.izwebz.com/video-tutorials/bai-12-mo-hinh-mvc/](https://www.izwebz.com/video-tutorials/bai-12-mo-hinh-mvc/ "hướng dẫn") của Clackken Smith ở Izwebz.

##### Reference

* http://freetuts.net/mvc-php-mo-hinh-mvc-la-gi-354.html



