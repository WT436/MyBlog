# Factory Method

## 1. Tổng Quan
* Độ Phức tạp :  🔥✖✖✖✖
* Mức Phổ Biến : 🔥🔥🔥🔥🔥
> Về bản chất thì dòng Factory là 1 pattern nhưng đã được chia nhỏ làm 3 loại và một loại trong số đó đã không đủ tiêu chuẩn là simple , 2 loại còn lại chính là Factory Method và abstract Factory.

>Factory Method là một Creational design pattern cung cấp giao diện để tạo các đối tượng trong lớp cha,nhưng cho phép lớp con thay đổi kiểu đối tượng sẽ được tạo.
Nó rất hữu ích khi bạn cần cung cấp mức độ linh hoạt cao cho code của mình.
## 2. Tình Huống
Bạn đang tạo ra một ứng dụng quản lý việc bán hàng. Nhưng lúc bạn code hệ thống đó thì không may là cửa hàng của bạn chỉ đang bán bánh mỳ thôi. Vì vậy phần lớn code của bạn đang tập chung sử lý việc liên quan đến bánh mỳ. Sau một thời gian bạn kinh doanh có hiệu quả bạn muốn mở rộng ra bán tà tưa để tăng hiệu quả. Nhưng hệ thống cũ chỉ đang giải quyết được việc quản lý bánh mỳ và rất khó để tích hợp việc quản lý tà tưa vào.  Mặc dù các thao tác đều giống nhau. Nhưng việc thêm code để giải quyết vấn đề sẽ thay đổi cấu trúc cũ. Nếu nhìn xa hơn thì chả cõ lẽ ..... ak mà thôi!. Cái kết chắc ai cx nghĩ ra. Bạn nhận được một đống tạp nham code dư thừa.
## 3. Giải pháp
Một ngày đẹp trời bạn hà quyết tâm thay đổi cấu chúc cũ sao cho việc mở rộng chỉ cần thêm các Domain vào là code se chạy mà không thay đổi đi tầng Application.
Lúc này khi trò đã sẵn sàng thì thầy sẽ đến. Factory Method

![image](https://user-images.githubusercontent.com/63473793/121778847-0baed300-cbc3-11eb-9960-cbf339cbc89f.png)
## 4. Lợi Ích
 * Ưu điểm
  >Bạn có thể thỏa mái kết hợp giữa thành phần khởi tạo và thành phần thực thi.
  
  >Bạn có thể di chuyển thành phần cốt lõi vào một nơi, giúp cải thiện và chỉnh sửa logic maintain một cách dễ dàng hơn.
  
  >Bạn có thể thêm nhiều chức năng mà không làm phá vỡ đi mạch hệ thống.
  
 * Nhược điểm
 
  >Code có thể sẽ nhìn phức tạp hơn khi bạn cần phải khai báo nhiều thứ.
  
## 5. Cấu Trúc
* Các thành phần thực thi nghiệp vụ chính :
  * IProduct là interface chung cho các thành phần
  ```c#
    public interface IProduct
    {
        // Cách thực thi chung cho sản phẩm
        string ResourcesProduct();
    }
  ```
  * BreadProduct là hàm giải quyết các vấn đề liên quan đến bánh mỳ
  ```c#
    public class BreadProduct : IProduct
    {
        // nghiệp vụ chính của phương thức ở đây. thực thi chuyên biệt như thế nào .....
        public string ResourcesProduct()
        {
            return "Bánh Mỳ";
        }
    }
  ```
  * MilkTeaProduct là hàm giải quyết các vấn đề liên quan đến tà tữa
  ```c#
    public class MilkTeaProduct : IProduct
    {
        // nghiệp vụ chính của phương thức ở đây. thực thi chuyên biệt như thế nào .....
        public string ResourcesProduct()
        {
            return "Trà Sữa";
        }
    }
  ```
* Các thành phần thực thi Factory Method :
  * ProcessingCreator
  ```c#
    public abstract class ProcessingCreator
    {
        // THành phần quan trọng nhất của nó
        // ví dụ như ở đây không phải là sản phẩm nữa
        public abstract IProduct FactoryMethod();

        // các hoạt động chế biến sản phẩm ở đây
        // từ các nguyên liệu trên chúng ta sẽ có một bộ các cách thực thi chung ở đây
        // cách thể hiện cho các interface ra sao 
        // các bước tuần tự như thế nào .....
        public string SomeOperation()
        {
            var product = FactoryMethod();
            var result = "Đầu Bếp : Sản Phẩm : " + product.ResourcesProduct()+" Đã Hoàn Thành!";
            return result;
        }
     }
  ```
   * BreadCreator
  ```c#
    public class BreadCreator : ProcessingCreator
    {
        // khởi tạo chuyên biệt cho quá trình chế biến sản phẩm
        public override IProduct FactoryMethod()
        {
            return new BreadProduct();
        }
    }
  ```
   * MilkTeaCreator
  ```c#
    public class MilkTeaCreator : ProcessingCreator
    {
        // khởi tạo chuyên biệt cho quá trình chế biến sản phẩm
        public override IProduct FactoryMethod()
        {
            return new MilkTeaProduct();
        }
    }
  ```
* Order
```c#
    public class Order
    {
        public void Main()
        {
            Console.WriteLine("Khách : Tôi Yêu cầu một Chiếc bánh mỳ.");
            // khởi tạo phương thức cần thiết hoặc là phương thức đang được yêu cầu
            ClientCode(new BreadCreator());

            Console.WriteLine("");

            Console.WriteLine("Khách : Tôi Yêu cầu một Cốc tà tữa.");
            ClientCode(new MilkTeaCreator());
        }
        private void ClientCode(ProcessingCreator creator)
        {
            // gửi đi yêu cầu sử lý cho sản phẩm
            Console.WriteLine("Phục vụ : Chúng tôi Không biết làm như thế nào.Chúng tôi đã gửi yêu cầu đi. \n" + creator.SomeOperation());
        }
    }
```
## 6. Áp Dụng
1. Sử dụng Factory Method khi bạn không biết trước các loại và phụ thuộc chính xác của các đối tượng mà mã của bạn sẽ hoạt động.
Tách phần hoạt động và phần thực thi.
Do đó, việc mở rộng mã xây dựng sản phẩm độc lập với phần còn lại của mã sẽ dễ dàng hơn.

2. Sử dụng Factory Method khi bạn muốn cung cấp cho người dùng library hoặc framework  của mình một cách để mở rộng các thành phần bên trong của nó.
 Kế thừa có lẽ là cách dễ nhất để mở rộng hành vi mặc định của một library or framework.
 Giải pháp là giảm mã xây dựng các thành phần trong framework thành một phương thức gốc duy nhất và cho phép bất kỳ ai ghi đè phương thức này ngoài việc mở rộng chính thành phần đó.
 
3. khi bạn muốn tiết kiệm tài nguyên hệ thống bằng cách sử dụng lại các đối tượng hiện có thay vì xây dựng lại chúng mỗi lần.

## 7. Mối quan hệ
1. Abstract Factory, Prototype, Builder
  Giảm độ phức tạp của các pattern này
2. Iterator 
 trả về các kết quả khác nhau tương thích với từng tình huống (Random Factory)
3. Và còn nhiều những thứ hay ho khác

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>