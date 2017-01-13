# Các phương thức Magic

Để giúp cho việc sử dụng các object trở nên thuận tiện hơn, PHP đã cung cấp một số phương thức magic, chúng thường được gọi khi có những action nhất định thường xuyên xảy ra trong các object. Điều này cho phép lập trình viên thực thi một số tác vụ hữu ích dễ dàng.

##### Sử dụng Constructors \(hàm dựng\) và Destructors \(hàm hủy\)

Khi một object được khởi tạo, nó thường kèm theo nhu cầu thiết lập một vài thứ ngoài lề. Để xử lý điều này, PHP cung cấp phương thức magic `__construct()`, phương thức này sẽ tự động được gọi ngay khi một object mới được khởi tạo.

Để minh họa cho khái niệm constructor, chúng ta sẽ thêm một hàm dựng \(constructor\) vào Myclass có nhiệm vụ xuất ra một thông tin bất kỳ \(do chúng ta thiết lập\) ngay khi có một object thể hiện của class được khởi tạo.

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function __construct() 
    { 
        echo 'The class "', __CLASS__, '" was initiated!<br />'; 
    } 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo object 
$obj = new MyClass; 

// echo giá trị thuộc tính $prop1 
echo $obj->getProperty(); 

echo "End of file.<br />"; 

?>
```

Chú ý `__CLASS__` trả về tên của chính class gọi nó; nó được gọi hằng số magic \(magic constant\). Trong PHP, thì có một vài hằng số magic, để tìm hiểu thêm về chúng bạn tìm đọc trong PHP manual.

Đọc lại file trên trình duyệt, bạn sẽ thấy kết quả như sau:

```
The class "MyClass" was initiated!
I'm a class property!
End of file.
```

Để gọi một hàm khi object bị hủy, chúng ta có sẵn phương thức magic `__destruct()`. Thông thường nó được sử dụng vào mục đích dọn dẹp một cái gì đó \(ví dụ: đóng một kết nối cơ sở dữ liệu\).

Để minh họa, chúng ta sẽ xuất ra một đoạn thông tin khi object bị hủy bằng cách sử dụng phương thức `__destruct()` trong MyClass:

```php
<?php 
class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function __construct() 
    { 
        echo 'The class "', __CLASS__, '" was initiated!<br />'; 
    } 

    public function __destruct() 
    { 
        echo 'The class "', __CLASS__, '" was destroyed.<br />'; 
    } 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo object 
$obj = new MyClass; 

// Echo giá trị thuộc tính $prop1 
echo $obj->getProperty(); 

echo "End of file.<br />"; 

?>
```

Với một hàm hủy được định nghĩa trong class, bạn reload lại trình duyệt để nhận được kết quả như sau:

```
The class "MyClass" was initiated!
I'm a class property!
End of file.
The class "MyClass" was destroyed.
```

_"Khi kết thúc một file, PHP sẽ tự động giải phóng mọi tài nguyên."_

Vì vậy, để hiểu rõ bản chất hàm hủy hơn, chúng ta sẽ hủy object trước khi kết thúc file bằng hàm unset\(\):

```php
<?php 

class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function __construct() 
    { 
        echo 'The class "', __CLASS__, '" was initiated!<br />'; 
    } 

    public function __destruct() 
    { 
        echo 'The class "', __CLASS__, '" was destroyed.<br />'; 
    } 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo object 
$obj = new MyClass; 

// Echo giá trị thuộc tính $prop1 
echo $obj->getProperty(); 

// Hủy object 
unset($obj); 

echo "End of file.<br />"; 

?>
```

Bây giờ kết quả trên trình duyệt sẽ hiển thị như sau:

```
The class "MyClass" was initiated!
I'm a class property!
The class "MyClass" was destroyed.
End of file.
```

##### Convert qua một Chuỗi

Nếu bạn muốn `echo` MyClass ra dưới dạng chuỗi, bạn sẽ gặp lỗi. Để tránh được lỗi này, bạn cần sử dụng một phương thức magic khác được gọi là `__toString()`.

Nếu không có `__toString()`, mọi cố gắng để echo object ra dưới dạng chuỗi sẽ đều cho ra một kết quả lỗi nghiêm trọng \(fatal error\). Dưới đây là một ví dụ về việc echo một object ra dưới dạng chuỗi mà không sử dụng một phương thức magic:

```php
<?php 

class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function __construct() 
    { 
        echo 'The class "', __CLASS__, '" was initiated!<br />'; 
    } 

    public function __destruct() 
    { 
        echo 'The class "', __CLASS__, '" was destroyed.<br />'; 
    } 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo object. 
$obj = new MyClass; 

// Echo object ra dưới dạng một chuỗi 
echo $obj; 

// Hủy object 
unset($obj); 

echo "End of file.<br />"; 

?>
```

Kết quả sẽ hiển thị như sau:

```
The class "MyClass" was initiated!

Catchable fatal error: Object of class MyClass could not be converted to string in /Applications/XAMPP/xamppfiles/htdocs/testing/test.php on line 40
```

Để tránh được lỗi này, chúng ta thêm phương thức `__toString()` vào trong class:

```php
<?php 

class MyClass 
{ 
    public $prop1 = "I'm a class property!"; 

    public function __construct() 
    { 
        echo 'The class "', __CLASS__, '" was initiated!<br />'; 
    } 

    public function __destruct() 
    { 
        echo 'The class "', __CLASS__, '" was destroyed.<br />'; 
    } 

    public function __toString() 
    { 
        echo "Using the toString method: "; 
        return $this->getProperty(); 
    } 

    public function setProperty($newval) 
    { 
        $this->prop1 = $newval; 
    } 

    public function getProperty() 
    { 
        return $this->prop1 . "<br />"; 
    } 
} 

// Tạo object 
$obj = new MyClass; 

// Echo object ra dưới dạng một chuỗi 
echo $obj; 

// Hủy object 
unset($obj); 

echo "End of file.<br />"; 

?>
```

Lần này, khi bạn `echo`object, vì trong MyClass chúng ta đã xây dựng hàm `__toString()` nên nó sẽ tự động được triệu gọi, và chúng ta thấy kết quả sẽ trả về như sau:

```
The class "MyClass" was initiated!
Using the toString method: I'm a class property!
The class "MyClass" was destroyed.
End of file.
```

Ngoài những phương thức magic chúng ta đã thảo luận ở đây, PHP còn cung cấp sẵn cho chúng ta một số phương thức magic khác. Để tìm hiểu thêm về danh sách các phương thức magic, bạn đọc thêm trong PHP manual.

##### Reference

  + http://www.qhonline.info/php-nang-cao/58/lap-trinh-huong-doi-tuong-tim-hieu-phuong-thuc-magic.html





