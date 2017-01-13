# Sự kế thừa

Tính kế thừa trong lập trình hướng đối tượng cho phép một lớp \(class\) có thể kế thừa các thuộc tính và phương thức từ các lớp khác đã được định nghĩa,  từ đó bạn có thể tuỳ biến lại code bên trong một phương thức hoặc thuộc tính nào đó. Lớp được kế thừa còn được gọi là lớp cha và lớp kế thừa được gọi là lớp con.

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



