# Thuộc tính và phương thức

#### Phương thức \(method\)

Phương thức của một lớp thường được dùng để mô tả các hành vi của đối tượng \(hoặc của lớp\). Ví dụ như đối tượng thuộc lớp điện thoại có các hành vi sau: Đổ chuông, chuyển tín hiệu từ sóng sang dạng nghe được, chuyển tín hiệu giọng nói sang dạng chuẩn, chuyển tín hiệu lên tổng đài.v.v. Khi thiết kế, người ta có thể dùng các phương thức để mô tả và thực hiện các hành vi của đối tượng.

Mỗi phương thức thường được định nghĩa là một hàm, các thao tác để thực hiện hành vi đó được viết tại nội dung của hàm. Khi thực hiện hành vi này, đối tượng có thể phải thực hiện các hành vi khác. Ví dụ như điện thoại phải chuyển tín hiệu giọng nói sang dạng chuẩn trước khi chuyển lên tổng đài. Cho nên một phương thức trong một lớp có thể sử dụng phương thức khác trong quá trình thực hiện hành vi của mình.

Người ta còn định nghĩa thêm vài loại phương thức đặc biệt:

* Hàm tạo \(constructor\) là hàm được dùng để tạo ra một đối tượng, cài đặt các giá trị ban đầu cho các thuộc tính của đối tượng đó.

* Hàm hủy \(destructor\) là hàm dùng vào việc làm sạch bộ nhớ đã dùng để lưu đối tượng và hủy bỏ tên của một đối tượng sau khi đã dùng xong, trong đó có thể bao gồm cả việc xóa các con trỏ nội tại và trả về các phần bộ nhớ mà đối tượng đã dùng.

##### Phân loại Function

###### **Có giá trị trả về**

Function chịu trách nhiệm xử lý dữ liệu và trả lại dữ liệu cho Process đang chờ đợi để lấy kết quả.

```php
<?php
    class MyClass
    {
        function getName($firstName, $lastName)
        {
            $name = $firstName . ' ' . $lastName;

            return $name;
        }
    }
?>
```

Như vậy tại một trang xử lý ta dễ dàng lấy được name của class qua cấu trúc đã tạo cho function như sau :

```php
<?php
    $class = new MyClass();
    $name = $class->getName('Brian', 'Tran');
    echo $name; // 'Brian Tran'
?>
```

###### Không có giá trị trả về

Lúc này function sẽ không trả lại giá trị cho biến khi được gọi. Chúng ta cùng xét lại ví dụ trên với cách viết khác một chút, chúng ta sẽ cho echo name ngay trong hàm mà không trả lại giá trị gì cả.

```php
<?php
    class MyClass
    {
        function getName($firstName, $lastName)
        {
            $name = $firstName . ' ' . $lastName;

            echo $name;
        }
    }
?>
```

Khi đó ta chỉ gần gọi hàm này để hiển thị dữ liệu mong muốn mà không cần trả về giá trị nào cả:

```php
<?php
    $class = new MyClass();
    $class->getName('Brian', 'Tran'); // 'Brian Tran'
?>
```

#### Thuộc tính \(attribute\)

Thuộc tính của một lớp bao gồm các biến, các hằng, hay tham số nội tại của lớp đó. Ở đây, vai trò quan trọng nhất của các thuộc tính là các biến vì chúng sẽ có thể bị thay đổi trong suốt quá trình hoạt động của một đối tượng. Các thuộc tính có thể được xác định kiểu và kiểu của chúng có thể là các kiểu dữ liệu cổ điển hay đó là một lớp đã định nghĩa từ trước.

Khi một lớp đã được thực thể hoá thành đối tượng cụ thể thì tập hợp các giá trị của các biến nội tại làm thành trạng thái của đối tượng. Giống như trường hợp của phương thức, tùy theo người viết mã, biến nội tại có thể chỉ được dùng bên trong các phương thức của chính lớp đó, có thể cho phép các câu lệnh bên ngoài lớp, hay chỉ cho phép các lớp có quan hệ đặc biệt như là quan hệ lớp con,  được phép dùng tới nó \(hay thay đổi giá trị của nó\). Mỗi thuộc tính của một lớp còn được gọi là thành viên dữ liệu của lớp đó.

Các thuộc tính được khai báo và sử dụng dễ dàng trong class:

```php
<?php
    class MyClass
    {
        var $name = "Brian";
        function getName()
        {
            return $this->name;
        }
    }
?>
```

#### Gán tầm vực cho Thuộc Tính và Phương Thức

Để gia tăng khả năng kiểm soát các object, các phương thức và thuộc tính sẽ được gán thêm những giá trị tầm vực. Nó cho phép chúng ta kiểm soát khả năng truy cập \(như thế nào và ở nơi đâu\) của thuộc tính và phương thức. Chúng ta có ba từ khóa để đảm nhiệm việc này:public,protected, vàprivate. Ngoài ra, còn có một từ khóa nữa cũng có khả năng đảm nhiệm việc này, đó là static, nó cho phép các thuộc tính và phương thức có thể được truy cập mà không cần khởi tạo class.

###### Tầm vực Public

Public là một tính chất được dùng để gán cho các phương thức, các biến nội tại, hay các lớp mà khi khai báo thì người lập trình đã cho phép các câu lệnh bên ngoài cũng như các đối tượng khác được phép dùng đến nó.

Khi bạn khai báo một thuộc tính hay phương thức mà không gán tầm vực cho chúng, thì PHP tự hiểu nó thuộc nhóm public.

```php
<?php
    class MyClass
    {
        public $name = 'Brian';

        public function getName()
        {
            return $this->name;
        }
    }

    $class = new MyClass();

    echo $class->name; // Brian
    echo $class->getName(); // Brian
?>
```

###### Tầm vực Protected

Khi một thuộc tính hay phương thức được khai báo tầm vựcprotected, chúng chỉ có thể truy cập được trong chính class chứa chúng, hoặc tại một class kế thừa class này \(xem phần Kế thừa\).

Gán tầm vực protected cho thuộc tính `$name` trong MyClass và thử truy cập nó từ child class:

```php
<?php
    class MyClass
    {
        protected $name = 'Brian';

        protected function getName(){
            return $this->name;
        }
    }

    class MyChildClass extends MyClass
    {
        public function getChildName()
        {
            return $this->getName() . ' Child';
        }        
    }

    $class = new MyChildClass();

    echo $class->getName(); // Fatal error: Call to protected method MyChildClass::getName() from context '' in ...

    echo $class->getChildName(); // 'Brian Child'
?>
```

###### Tầm vực Private

Private là sự thể hiện tính chất đóng mạnh nhất \(của một đặc tính hay một lớp\). Khi dùng tính chất này gán cho một biến, một phương thức thì biến hay phương thức đó chỉ có thể được sử dụng bên trong của lớp mà chúng được định nghĩa. Mọi nỗ lực dùng trực tiếp đến chúng từ bên ngoài qua các câu lệnh hay từ các lớp con sẽ bị phủ nhận hay bị lỗi.

Để chứng minh điều này, chúng ta sẽ khai báo phương thức getName\(\) là private trong MyClass, và cố gắng truy cập nó thông qua một phương thức public getChildName\(\)từ MyChildClass\(class kế thừa MyClass\):

```php
<?php
    class MyClass
    {
        protected $name = 'Brian';

        private function getName(){
            return $this->name;
        }
    }

    class MyChildClass extends MyClass
    {
        public function getChildName()
        {
            return $this->getName() . ' Child';
        }        
    }

    $class = new MyChildClass();

    echo $class->getName(); // Fatal error: Call to protected method MyClass::getName() from context '' in ...

    echo $class->getChildName(); // Fatal error: Call to private method MyClass::getName()  from context 'MyChildClass' in ...
?>
```

#### Các thành phần khác

###### Biến Static

Một phương thức hay thuộc tính được gán từ khóa static có thể truy cập được ngay cả khi bạn không khởi tạo class, bạn chỉ cần cung cấp tên class, toán tử phân giải phạm vi \(::\), và tên thuộc tính hoặc phương thức.

"Một trong những lợi ích chính khi sử dụng thuộc tính static là chúng giữ các giá trị được lưu trữ trong suốt khoảng thời gian script tồn tại."

Để chứng minh điều này, chúng ta sẽ thêm vào MyClass một thuộc tính static được gọi là `$count` và một phương thức static được gọi là `plusOne()`. Sau đó xây dựng một vòng lặp do...while để xuất ra các giá trị tăng dần mà nhỏ hơn 10 của `$count`:

```php
<?php 
    class MyClass 
    { 
        public static $count = 0; 

        public static function plusOne() 
        { 
            return "The count is " . ++self::$count; 
        } 

        public function getCount()
        {
            return self::$count;
        }
    } 

    // Gọi plusOne mà không khởi tạo MyClass 
    echo MyClass::plusOne(); // The count is 1

    // Giá trị dùng chung cho tất cả các object của class này
    $class1 = new MyClass();
    echo $class1->getCount();// 1

    echo MyClass::plusOne(); // The count is 2

    $class2 = new MyClass();
    echo $class2->getCount(); // 2
?>
```

Chú ý: Khi truy cập các thuộc tính static,ký tự độ la \($\) sẽ nằm sau toán tử phân giải phạm vi \(::\).

###### Hằng số Constant

Một constant là một cái gì đó giống như một biến, trong đó nó giữ một giá trị, nhưng thực sự thì nó giống một hàm hơn, bởi vì một hằng là không thể thay đổi. Một khi bạn khai báo một hằng, nó không thay đổi và nó cũng được truy xuất giống với biến static.

Khai báo một hằng trong PHP là khá dễ dàng, như được thực hiện trong phiên bản MyClass này.

```php
<?php
class MyClass 
{
   const FIRST_NAME = 100; // từ khóa const
   
   public function getFirstName()
   {
      return self::FIRST_NAME;
   }
}

echo MyClass::FIRST_NAME; // 100
?>
```

Trong lớp này, FIRST\_NAME là một hằng. Nó được khai báo với từ khóa const trong PHP, và giá trị của nó sẽ không thay đổi trong bất kỳ tình huống nào. Ghi nhớ rằng, tên hằng không bắt đầu với $, như trong tên biến.

###### Từ khóa final

Một phương thức được gán từ khóa final sẽ ngăn cản các lớp con ghi đè nó. Nếu class được khai báo là final, thì nó không thể được kế thừa.

Ví dụ sau tạo lỗi: `Fatal Error: Cannot override final method MyClass::getName()`

```php
<?php
class MyClass
{
    final public function getName()
    {
        return 'Brian';
    }
}

class MyChildClass
{
    public function getName()
    {
        return 'Brian Tran';
    }
}
?>
```

##### Reference

* [http://www.qhonline.info/php-nang-cao/59/lap-trinh-huong-doi-tuong-tim-hieu-su-ke-thua-va-tam-vuc.html](http://www.qhonline.info/php-nang-cao/59/lap-trinh-huong-doi-tuong-tim-hieu-su-ke-thua-va-tam-vuc.html)

* [https://vi.wikipedia.org/wiki/L%E1%BA%ADp\\_tr%C3%ACnh\\_h%C6%B0%E1%BB%9Bng\\_%C4%91%E1%BB%91i\\_t%C6%B0%E1%BB%A3ng](https://vi.wikipedia.org/wiki/L%E1%BA%ADp\_tr%C3%ACnh\_h%C6%B0%E1%BB%9Bng\_%C4%91%E1%BB%91i\_t%C6%B0%E1%BB%A3ng)



