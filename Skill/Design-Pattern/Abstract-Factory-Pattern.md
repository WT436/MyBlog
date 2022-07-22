# Abstract Factory

## 1. Tổng Quan
* Độ Phức tạp :  🔥🔥🔥✖✖
* Mức Phổ Biến : 🔥🔥🔥🔥🔥
> Về bản chất thì dòng Factory là 1 pattern nhưng đã được chia nhỏ làm 3 loại và một loại trong số đó đã không đủ tiêu chuẩn là simple , 2 loại còn lại chính là Factory Method và Abstract Factory.

> Abstract Factory cho phép bạn tạo ra các họ của các đối tượng liên quan mà không cần chỉ định các lớp cụ thể của chúng.
> Hệ thống phân cấp bao gồm: nhiều "nền tảng" có thể có và việc xây dựng một bộ "sản phẩm".
> Một new operator được coi là có hại.

## 2. Tình Huống
Khi một khách hàng đến của hàng của bạn mua một chiếc oto và khi đã có những phụ kiện căn bản thì họ lại muốn có thêm phụ kiện.Cùng là một chiếc oto nhưng sẽ có oto this oto that
## 3. Giải Pháp
DI
## 4. Lợi Ích
* Ưu Điểm
	* Bạn có thể chắc chắn rằng các kết quả bạn nhận được từ factory tương thích với nhau.
	* Tránh được các liên kết chặt chẽ giữa Thực thi code và triển khai code.
	* Có thể tách phần logic code vào một nơi, đảm bảo cho việc maintain
	* Bạn có thể thêm mới code nền mà không ảnh hưởng đến cấu trúc code.
* Nhược điểm
	* Code có thể trở nên phức tạp hơn mức bình thường, vì rất nhiều Interface và Class mới được giới thiệu cùng với mẫu.
## 5. Cấu Trúc
* UML
	1. Abstract Products khai báo giao diện cho một tập hợp các Thành Phần riêng biệt nhưng có liên quan tạo nên một Tập hợp chung.
	2. Concrete Products là các triển khai khác nhau của các thành phần Abstract, được nhóm theo các biến thể. Mỗi thành phần Abstract phải được thực hiện trong tất cả các biến thể nhất định.
	![image](https://user-images.githubusercontent.com/63473793/121797014-9c2ef700-cc47-11eb-8550-5918003ed5d7.png)
	3. Abstract Factory interface khai báo một tập hợp các phương thức để tạo từng Abstract Factory.
	4. Concrete Factories thực hiện các phương pháp tạo của abstract factory. Mỗi factory lõi tương ứng với một biến thể cụ thể của sản phẩm và chỉ tạo ra những biến thể sản phẩm đó.
	5. Client có thể làm việc với factory/product object bất kỳ. Miễn là phải thông qua các abtract interface.
* Detail
  * Class cung cấp
    * Chassis 
    ```c#
    public class Chassis
    {
        public string Show()
        {
            return "Khung Xe";
        }
    }
    ```
    
    * Wheel 
    ```c#
    public class Wheel
    {
        public string Show()
        {
            return "Bánh Xe";
        }
    }
    ```
    
  * Class Sử lý nền
    * IAbstractWheelA 
    ```c#
    public interface IAbstractWheelA
    {
        /// <summary>
        /// Chức năng của dòng Bánh xe này
        /// </summary>
        string UsefulFunctionA();
    }
    ```
    * IAbstractChassisA 
    ```c#
    public interface IAbstractChassisA
    {
        /// <summary>
        /// Chức năng của dòng Khung xe này
        /// </summary>
        string UsefulChassisA();

        /// <summary>
        /// Dòng khung xe sẽ có dòng bánh xe riêng
        /// </summary>
        string AnotherUsefulChassisA(IAbstractWheelA collaborator);
    }
    ```
    * ConcreteWheelA2 
    ```c#
    public class ConcreteWheelA2 : IAbstractWheelA
    {
        public string UsefulFunctionA()
        {
            var wheel = new Wheel();
            return $"Đây là dòng {wheel.Show()} A2";
        }
    }
    ```
    * ConcreteWheelA1 
    ```c#
    public class ConcreteWheelA1 : IAbstractWheelA
    {
        public string UsefulFunctionA()
        {
            var wheel = new Wheel();
            return $"Đây là dòng {wheel.Show()} A1";
        }
    }
    ```
    * ConcreteChassisA2 
    ```c#
    public class ConcreteChassisA2 : IAbstractChassisA
    {
        public string UsefulChassisA()
        {
            var chassis = new Chassis();
            return $"Đây là dòng {chassis.Show()} A2";
        }
        public string AnotherUsefulChassisA(IAbstractWheelA collaborator)
        {
            var result = collaborator.UsefulFunctionA();
            return $"Dòng này đi kèm với : ({result})";
        }
    }
    ```
    * ConcreteChassisA1 
    ```c#
    public class ConcreteChassisA1 : IAbstractChassisA
    {
        // trường hợp thứ nhất
        public string UsefulChassisA()
        {
            var chassis = new Chassis();
            return $"Đây là dòng {chassis.Show()} A1";
        }

        public string AnotherUsefulChassisA(IAbstractWheelA collaborator)
        {
            var result = collaborator.UsefulFunctionA();
            return $"Dòng này đi kèm với : ({result})";
        }
    }
    ```
  * Abstract Factory
    * IAbstractFactory 
    ```c#
    public interface IAbstractFactory
    {
        IAbstractChassisA abstractChassisA();
        IAbstractWheelA abstractWheelA();
    }
    ```
    * ConcreteFactoryA2 
    ```c#
    public class ConcreteFactoryA2 : IAbstractFactory
    {
        public IAbstractChassisA abstractChassisA()
        {
            return new ConcreteChassisA2();
        }

        public IAbstractWheelA abstractWheelA()
        {
            return new ConcreteWheelA2();
        }
    }
    ```
    * ConcreteFactoryA1 
    ```c#
    public class ConcreteFactoryA1 : IAbstractFactory
    {
        // sử lý thông tin
        public IAbstractChassisA abstractChassisA()
        {
            return new ConcreteChassisA1();
        }

        public IAbstractWheelA abstractWheelA()
        {
            return new ConcreteWheelA1();
        }
    }
    ```
  * Triển khai
  ```c#
  Console.OutputEncoding = Encoding.UTF8;
  // khởi tạo nhà máy
  IAbstractFactory factory = new ConcreteFactoryA1();
  // lựa chọn các thuộc tính cho nhà máy
  var productA = factory.abstractWheelA();
  var productB = factory.abstractChassisA();
  // lựa chọn các khu hình kiểu mẫu
  Console.WriteLine(productB.UsefulChassisA());
  Console.WriteLine(productB.AnotherUsefulChassisA(productA));
  Console.WriteLine("Hello World!");
  ```
## 6. Áp Dụng
1. Sử dụng Abstract Factory khi mã của bạn cần hoạt động với nhiều nhóm sản phẩm liên quan khác nhau, nhưng bạn không muốn nó phụ thuộc vào các lớp cụ thể của các sản phẩm đó — chúng có thể chưa được biết trước hoặc bạn chỉ muốn cho phép khả năng mở rộng trong tương lai.

2. Trong một chương trình được thiết kế tốt, mỗi lớp chỉ chịu trách nhiệm về một việc. Khi một lớp xử lý nhiều loại sản phẩm, nó có thể đáng giá khi trích xuất các factory methods của nó thành một factory Class độc lập hoặc triển khai Abstract Factory toàn diện.
## 7. Mối Quan Hệ
> Builder tập trung vào việc xây dựng các đối tượng phức tạp từng bước. Abstract Factory chuyên tạo các family đối tượng liên quan.

> Đóng vai trò thay thế cho Facade khi bạn chỉ muốn ẩn cách các đối tượng hệ thống con được tạo ra khỏi mã máy khách.

> Bạn có thể sử dụng Abstract Factory cùng với Bridge. Việc ghép nối này rất hữu ích khi một số trừu tượng được xác định bởi Bridge chỉ có thể hoạt động với các triển khai cụ thể.

> Có thể được triển khai dưới dạng các Singleton.

> Bạn cũng có thể sử dụng Prototype để viết các phương thức trên các lớp này.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>