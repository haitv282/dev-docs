# Các tính chất cơ bản

Lập trình hướng đối tượng là một phương pháp lập trình có 4 tính chất chính sau:

##### Tính trừu tượng \(abstraction\)

Đây là khả năng của chương trình bỏ qua hay không chú ý đến một số khía cạnh của thông tin mà nó đang trực tiếp làm việc lên, nghĩa là nó có khả năng tập trung vào những cốt lõi cần thiết. Mỗi đối tượng phục vụ như là một "động tử" có thể hoàn tất các công việc một cách nội bộ, báo cáo, thay đổi trạng thái của nó và liên lạc với các đối tượng khác mà không cần cho biết làm cách nào đối tượng tiến hành được các thao tác. Tính chất này thường được gọi là sự trừu tượng của dữ liệu.

Tính trừu tượng còn thể hiện qua việc một đối tượng ban đầu có thể có một số đặc điểm chung cho nhiều đối tượng khác như là sự mở rộng của nó nhưng bản thân đối tượng ban đầu này có thể không có các biện pháp thi hành. Tính trừu tượng này thường được xác định trong khái niệm gọi là lớp trừu tượng hay lớp cơ sở trừu tượng.

###### Abstract Class

Một lớp trừu tượng là một lớp mà không thể được khởi tạo, chỉ được kế thừa. Bạn khai báo một lớp trừu tượng với từ khóa abstract trong PHP, giống như dưới đây.

```php
<?php
abstract class MyAbstractClass
{
    abstract function myAbstractFunction();
}

class MyClass extends MyAbstractClass
{
    function myAbstractFunction(){
        // code thực thi cho hàm này
    }
}
?>
```

Khi kế thừa từ một lớp trừu tượng, tất cả phương thức được đánh dấu abstract trong khai báo lớp cha phải được định nghĩa bởi lớp con; ngoài ra, những phương thức này phải được định nghĩa với cùng tính nhìn thấy.

###### Interface

Interface là một Temlate \(khuôn mẫu\), nó không phải là một lớp đối tượng mà chỉ là một bề nhìn bên ngoài mà nhìn vào đó ta có thể biết được tất cả các hàm của đối tượng implement nó.

Để khai báo một Interface ta dùng từ khóa interface để thay cho từ khóa class. Tất cả các hàm trong interface đểu ở dạng khai báo và không được định nghĩa \(giống lớp abstract\). Nếu một đối tượng implement một interface thì nó phải khai báo và định nghĩa tất cả các hàm trong Interface.

Thoạt nhìn qua các bạn thấy Interface rất giống với Abstract trong php đúng không nào? Câu trả lời là bản chất bên trong hoàn toàn khác nhau. Interface không phải là một lớp cụ thể mà là một khuôn mẫu để cho một đối tượng implement nó, và đương nhiên là ta không thể tạo một biến Interface. Ngược lại lớp Abstract là một lớp cụ thể, có đầy đủ các tính chất của một đối tượng, có thể gọi, định nghĩa các hàm trong nó. Đối với hằng số ở lớp implement không được định nghĩa lại.

```php
<?php
interface ClassInterface
{
    /** get Name of class */
    public function getName();
}

class MyClass implements ClassInterface
{
    public function getName()
    {
        return 'Brian';
    }
}
?>
```

##### Tính đóng gói \(encapsulation\) và che giấu thông tin \(information hiding\)

Tính chất này không cho phép người sử dụng các đối tượng thay đổi trạng thái nội tại của một đối tượng. Chỉ có các phương thức nội tại của đối tượng cho phép thay đổi trạng thái của nó. Việc cho phép môi trường bên ngoài tác động lên các dữ liệu nội tại của một đối tượng theo cách nào là hoàn toàn tùy thuộc vào người viết mã. Đây là tính chất đảm bảo sự toàn vẹn của đối tượng.

Tính chất này thể hiện ở việc sử dụng các tầm vực biến/hàm: public, protected, private.

##### Tính đa hình \(polymorphism\)

Thể hiện thông qua việc gửi các thông điệp \(message\). Việc gửi các thông điệp này có thể so sánh như việc gọi các hàm bên trong của một đối tượng. Các phương thức dùng trả lời cho một thông điệp sẽ tùy theo đối tượng mà thông điệp đó được gửi tới sẽ có phản ứng khác nhau. Người lập trình có thể định nghĩa một đặc tính \(chẳng hạn thông qua tên của các phương thức\) cho một loạt các đối tượng gần nhau nhưng khi thi hành thì dùng cùng một tên gọi mà sự thi hành của mỗi đối tượng sẽ tự động xảy ra tương ứng theo đặc tính của từng đối tượng mà không bị nhầm lẫn.

Ví dụ sau đây sẽ thể hiện tính đa hình khi tính chu vi cho các đối tượng:

```php
<?php
abstract class Geometry
{
    /** Tinh chu vi cho hinh */
    abstract function calculatePerimeter();
}

class Rectangle extends Geometry
{
    protected $chieuDai = 10;
    protected $chieuRong = 5;

    /** Tính chu vi hình chữ nhật */
    function calculatePerimeter()
    {
        return ($this->chieuDai + $this->chieuRong) * 2;   
    }
}

class Circle extends Geometry
{
    const PI = 3.1415;
    protected $banKinh = 5;

    /** Tính chu vi hình tròn */
    function calculatePerimeter()
    {
        return $this->banKinh * self::PI * 2;
    }
}
?>
```

Ví dụ khi định nghĩa hai đối tượng "hinh\_vuong" và "hinh\_tron" thì có một phương thức chung là "chu\_vi". Khi gọi phương thức này thì nếu đối tượng là "hinh\_vuong" nó sẽ tính theo công thức khác với khi đối tượng là "hinh\_tron".

##### Tính kế thừa \(inheritance\)

Đặc tính này cho phép một đối tượng có thể có sẵn các đặc tính mà đối tượng khác đã có thông qua kế thừa. Điều này cho phép các đối tượng chia sẻ hay mở rộng các đặc tính sẵn có mà không phải tiến hành định nghĩa lại. Lớp được kế thừa còn được gọi là lớp cha và lớp kế thừa được gọi là lớp con.

Trong PHP việc kế thừa được thực hiện thông qua sử dụng từ khóa extends. Ở ví dụ dưới đây lớp MyClass được gọi là lớp cha và lớp MyChildClass được gọi là lớp con.

```php
<?php
class MyClass
{
    protected $firstName = 'Brian';
    protected $lastName = 'Tran';

    public function getName()
    {
        return $this->firstName . ' ' . $this->lastName;
    }
}

class MyChildClass extends MyClass
{
    protected $lastName = 'Thomas';

    public function getFirstName()
    {
        return $this->firstName;    
    }

    public function getLastName()
    {
        return $this->lastName;
    }
}

$myClass = new MyClass();
echo $myClass->getName(); // Brian Tran

$myChildClass = new MyChildClass();
echo $myChildClass->getName(); // Brian Thomas
echo $myChildClass->getLastName(); // Thomas
?>
```

###### Tính kế thừa của Interface

Interface trong php tuy không phải là một lớp chính hiệu nhưng nó cũng có một tính chất đó là tính kế thừa, nghĩa là một Interface A có thể kế thừa một Interface B thì lúc này đối tượng nào implement lớp A thì nó phải định nghĩa tất cả các hàm mà cả hai lớp A và B đã khai báo.

```php
<?php
interface A
{
    public function getName();
}

interface B extends A
{
    public function getDescription();
}

class C implements B
{
    public function getName()
    {
        // code for getName function
    }
    
    public function getDescription()
    {
        // code for getDescription function
    }
}
?>
```



