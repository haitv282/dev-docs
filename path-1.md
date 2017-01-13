# Object and Class

Trước khi bạn có thể đi sâu vào cái tinh túy của Lập Trình Hướng Đối Tượng, một cái nhìn căn bản về sự khác nhau giữa object và class là rất cần thiết. Phần này chúng ta sẽ đi vào việc xây dựng từng phần của class, khả năng khác nhau và một số công dụng của chúng.

##### Nhận thức sự khác nhau giữa Object và Class

![](/assets/blueprint-houses.jpg)

Đôi khi có một số quan niệm nhầm lẫn trong hướng đối tượng: nhiều lập trình viên có kinh nghiệm cho rằng hai khái niệm object và class có thể thay thế cho nhau. Tuy vậy, đây không phải là vấn đề đáng quan tâm, mặc dù sự khác nhau giữa object và class có thể sẽ rất phức tạp khiến bạn phải bù đầu để tìm hiểu khi mới tiếp xúc với chúng.

Nhìn vào hình ví dụ phía trên, một class cũng giống như một bản thiết kế của một ngôi nhà. Nó định nghĩa hình dạng của ngôi nhà trên giấy, với các mối quan hệ giữa những phần khác nhau của ngôi nhà được xác định rõ và lên kế hoạch cụ thể, mặc dù ngôi nhà chưa thực sự tồn tại.

Một object sau đó, cũng giống như một ngôi nhà thực tế được xây dựng dựa trên bản thiết kế này. Dữ liệu trong object ở đây có thể được xem như là gỗ, dây điện, và bê tông để tạo nên ngôi nhà hoàn chỉnh: mà không hề có chi tiết cách tạo ra chúng trong bản thiết kế. Tuy nhiên, khi kết hợp tất cả lại với nhau, nó sẽ trở thành một ngôi nhà hoàn chỉnh đến từng chi tiết.

Các Class xử lý cấu trúc dữ liệu và các action, đồng thời sử dụng các thông tin đó để xây dựng các object. Có thể có nhiều hơn một object được xây dựng từ cùng một class tại cùng một thời điểm, mỗi object này đều là 1 cá thể độc lập và không phụ thuộc lẫn nhau. Trở lại vấn đề xây dựng, điều này cũng giống như một quần thể các lô nhà có thể được xây dựng trên cùng một bản thiết kế: 150 ngôi nhà khác nhau đều có hình dạng giống nhau, nhưng có các hộ gia đình và nội thất bên trong đều khác nhau.

##### Cấu trúc Class

Cú pháp để tạo ra một class khá đơn giản: để khai báo một class ta sử dụng từ khóa class, theo sau từ khóa là tên của class và một cặp ngoặc nhọn \({ }\):

```php
<?php 
class MyClass { 
// Class properties and methods go here 
} 
?>
```

Sau tạo ra class, bạn có thể khởi tạo và lưu trữ chúng trong một biến bằng cách sử dụng từ khóa new:

```php
<?php
$obj = new MyClass; 
?>
```

Để xem nội dung của class, bạn sử dụng hàm var\_dump\(\):

```php
<?php
var_dump($obj);
?>
```

Hãy thử lại quá trình này bằng cách đặt toàn bộ các mã lệnh phía trên vào tập tin có tên là test.php và đặt nó vào trong locahost của bạn:

```php
<?php 
class MyClass { 
// Class properties and methods go here
} 
$obj = new MyClass; 
var_dump($obj); 
?>
```

Mở trình duyệt của bạn và chạy [http://localhost/test.php](http://localhost/test.php) , bạn sẽ nhìn thấy như sau:

```
object(MyClass)#1 (0) { }
```

Vậy là xong, bạn đã vừa hoàn thành script hướng đối tượng \(OOP\) đầu tiên của bạn dưới hình thức đơn giản nhất.

##### **Định nghĩa thuộc tính của Class**

Để thêm dữ liệu vào một class, người ta sử dụng thuộc tính, hoặc một biến riêng biệt nào đó. Chúng hoạt động tương tự như các biến thông thường, chỉ khác một điều là chúng đang liên kết với object và vì thế để có thể truy cập và sử dụng được chúng ta phải thông qua object hay nói cách khác là sử dụng object.

Để thêm một thuộc tính vào MyClass, bạn thêm đoạn mã sau vào script của bạn:

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 
} 

$obj = new MyClass; 
var_dump($obj); 
?>
```

Từ khóa public xác định tầm vực của thuộc tính. Tiếp đó, tên của thuộc tính được đặt đúng theo chuẩn cú pháp đặt tên cho biến, và một giá trị đã được gán cho nó \(mặc dù thuộc tính của class không nhất thiết phải có giá trị ban đầu\). Tuy nhiên chúng ta sẽ tìm hiểu về chúng ở các phần sau.

Để đọc thuộc tính này và xuất chúng ra trình duyệt, chúng ta sẽ phải tham chiếu chúng thông qua các object:

```php
<?php
echo $obj->prop1;  
?>
```

Nếu chúng ta không khai báo object, chương trình sẽ không thể xác định được thuộc tính đó thuộc object nào \(vì hiểu 1 cách đơn giản object là đại diện cho class\). Sử dụng dấu mũi tên \(-&gt;\) là một cấu trúc của Hướng Đối Tượng, để một object có thể truy cập được nội dung của thuộc tính và phương thức trong class.

Sửa lại mã lệnh file test.php như sau:

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 
} 

$obj = new MyClass; 

echo $obj->prop1; // Xuất thuộc tính ra trình duyệt 
?>
```

Và bây giờ Reload lại trình duyệt của để được kết quả như sau:

```
I'm a class property!
```

##### Định nghĩa Phương thức của Class

Phương thức là các hàm riêng biệt của class. Các action riêng lẻ, mà một object sẽ thực thi, thì được định nghĩa bên trong class như là các phương thức.

Ví dụ, để tạo ra các phương thức có khả năng thiết lập và trả về giá trị của thuộc tính \`$prop1\`, ta thêm đoạn mã như sau:

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

$obj = new MyClass; 
echo $obj->prop1; 
?>
```

**Chú ý:** Hướng Đối Tượng cho phép các object tự tham chiếu chính nó \(tham chiếu bên trong class\) bằng cách sử dụng biến $this. Khi làm việc bên trong 1 phương thức, sử dụng $this cũng giống như cách bạn sử dụng object name bên ngoài class.

Để sử dụng các phương thức này, việc gọi chúng cũng tương tự như sử dụng các hàm thông thường, nhưng chúng ta phải thông qua object để tham chiếu đến chúng. Echo thuộc tính từMyClass, thay đổi giá trị của nó, và echo nó một lần nữa để xem sự thay đổi:

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

$obj = new MyClass; 

echo $obj->getProperty(); // echo giá trị của thuộc tính 

$obj->setProperty("I'm a new property value!"); // Thiết lập giá trị mới 

echo $obj->getProperty(); // echo nó lại 1 lần nữa để xem sự thay đổi 
?>
```

Reload lại trình duyệt, và bạn sẽ nhìn thấy như sau:

```
I'm a class property!
I'm a new property value!
```

_**“Sức mạnh của Hướng Đối Tượng càng bộc lộ rõ khi chúng ta sử dụng cùng một class cho nhiều trượng hợp”**_

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo hai objects 
$obj = new MyClass; 
$obj2 = new MyClass; 

// Echo giá trị của $prop1 từ hai object 
echo $obj->getProperty(); 
echo $obj2->getProperty(); 

// Thiết lập giá trị mới cho thuộc tính $prop1 của từng object 
$obj->setProperty("I'm a new property value!"); 
$obj2->setProperty("I belong to the second instance!"); 

// Echo lại giá trị của $prop1 từ hai object để xem sự thay đổi 
echo $obj->getProperty(); 
echo $obj2->getProperty(); 
?>
```

Khi bạn xem chúng trên trình duyệt, bạn sẽ nhận được kết quả như sau:

```
I'm a class property!
I'm a class property!
I'm a new property value!
I belong to the second instance!
```

Như bạn có thể thấy ,Hướng Đối Tượng giữ các object như các thực thể riêng biệt, nhờ đó làm cho việc tách mã lệnh thành các phần nhỏ khác nhau mà vẫn giữ được mối liên hệ nhất định giữa chúng một cách dễ dàng.

##### Reference

[http://www.qhonline.info/php-nang-cao/57/lap-trinh-huong-doi-tuong-co-ban-ve-nhung-khai-niem.html](http://www.qhonline.info/php-nang-cao/57/lap-trinh-huong-doi-tuong-co-ban-ve-nhung-khai-niem.html)

