# Dependency Injection Design Pattern (DI)

## What?
Để hiểu DI là gì . chúng ta cần hiểu rõ Singleton Design Pattern đã có trong bộ Design Pattern và phần S.O.L.I.D có trong bộ SOLID của Blog này.

Đây là một mô hình thiết kế được sử dụng thường xuyên nhất trong các ứng dụng real-time. vì vậy một develop không thể không biết đên DI từ ngay lúc còn là một thực tập sinh.

Theo Wikipedia : Dependency injection là một kĩ thuật trong đó một object (hoặc một static method) cung cấp các dependencies của một object khác. Một dependency là một object mà có thể sử dụng (một service). 

Vậy dependency trong lập trình là gì : Khi 1 class sử dụng một thành phần của 1 class khác thì được coi là phụ thuộc vào class ấy. mà muốn sử dụng được class thì ta lại phải tạo ra một object cho class ấy trước.
Vì vậy công việc chuyển giao nhiệm vụ khởi tạo object đó cho một bên thứ 3 và trực tiếp sử dụng dependency đó được gọi là DI.

## Why? (Tại sao chúng ta cần Dependency Injection)

DI giúp chúng ta phat triển các thành phần của một phần mềm một cách lỏng lẻo. Hiểu theo một cách khác là giảm sự liên kết một cách chặt chẽ giữa các thành phần của phần mềm.Giúp quản lý các thay đổi trong tương lai và sự phức tạp khác trong ứng dụng của mình một cách dễ dàng.

Vậy chúng ta lại đặt ra câu hỏi kết nối chặt ché trong lập trình là gì ?

## What Tight Coupling ?

Tight Coupling (Kết hợp chặt chẽ) có nghĩa là các Class và Object phụ thuộc vào nhau. Điều đó có nghĩa là khi một Class phụ thuộc vào một Class cụ thể khác, thì nó được cho là sự kết hợp chặt chẽ giữa hai Class này. Trong trường hợp đó, nếu chúng ta thay đổi đối tượng phụ thuộc, thì chúng ta cũng cần thay đổi các Class nơi đối tượng phụ thuộc này được sử dụng. Nếu ứng dụng của bạn là một ứng dụng nhỏ, thì không khó để xử lý nhưng nếu bạn có một ứng dụng cấp doanh nghiệp lớn, thì thực sự rất khó xử lý để thực hiện những thay đổi này.

## Loose Coupling?

Loosely coupling (Liên kết lỏng lẻo) có nghĩa là hai đối tượng độc lập với nhau. Điều đó có nghĩa là nếu chúng ta thay đổi một đối tượng thì nó sẽ không ảnh hưởng đến đối tượng khác. Bản chất kết hợp lỏng lẻo của phát triển phần mềm cho phép chúng ta quản lý các thay đổi trong tương lai một cách dễ dàng và cũng cho phép chúng ta quản lý độ phức tạp của ứng dụng.

Cái đậu xanh lại viết theo phong cách lan man chưởng rồi.

## các dòng DI 

1. Constructor injection: các dependency đc cung cấp thông qua constructor của class.

2. Setter injection: client tạo ra một setter method để các class khác có thể sử dụng chúng để cấp dependency.

3. Interface injection: dependency sẽ cung cấp một hàm injector để inject nó vào bất kì client nào đc truyền vào. Các client phải implement một interface mà có một setter method dành cho việc nhận dependency.

## Cách hoạt động?
1. Lớp Client là lớp phụ thuộc vào Lớp Service
2. Lớp Service là lớp cung cấp tính năng có lơp client
3. Lớp Injector là lớp chuyên giao giữa Service và Client

 ![Dependency-Injection-Design-Pattern](https://user-images.githubusercontent.com/63473793/122799435-ed945180-d2eb-11eb-9f60-22c132246e74.png)

=> Dependency Injection tách trách nhiệm tạo một object của lớp Service ra khỏi lớp client.
## code ví dụ 
```c#
    public class EmployeeDto
    {
        public int ID { get; set; }
        public string Name { get; set; }
        public string Department { get; set; }
    }

        public class EmployeeDAL
    {
        public List<EmployeeDto> SelectAllEmployees()
        {
            List<EmployeeDto> ListEmployees = new List<EmployeeDto>();
            ListEmployees.Add(new EmployeeDto() { ID = 1, Name = "Hải Nam", Department = "IT" });
            return ListEmployees;
        }
    }

        public class EmployeeBL
    {
        public EmployeeDAL employeeDAL;
        public List<EmployeeDto> GetAllEmployees()
        {
            employeeDAL = new EmployeeDAL();
            return employeeDAL.SelectAllEmployees();
        }
    }
```
=>  lớp EmployeeBL phụ thuộc vào lớp EmployeeDAL. Trong phương thức GetAllEuineees () của lớp EmployeeBL, chúng ta tạo một thể hiện của lớp EmployeeDAL (Lớp truy cập dữ liệu nhân viên) và sau đó gọi phương thức SelectAllEuineees (). 
=> Đây là sự kết hợp chặt chẽ vì EmployeeDAL được kết hợp chặt chẽ với lớp EmployeeBL. Mỗi khi lớp EmployeeDAL thay đổi, lớp EmployeeBL cũng cần thay đổi.
=> Vậy sử lý nó như thế nào?
```c#
    // tạo ra một interface
    public interface IEmployeeDAL
    {
        List<Employee> SelectAllEmployees();
    }

    // triển khai IEmployeeDAL
    public class EmployeeDAL : IEmployeeDAL
    {
        public List<Employee> SelectAllEmployees()
        {
            List<Employee> ListEmployees = new List<Employee>();
            ListEmployees.Add(new Employee() { ID = 1, Name = "Pranaya", Department = "IT" });
            ListEmployees.Add(new Employee() { ID = 2, Name = "Kumar", Department = "HR" });
            ListEmployees.Add(new Employee() { ID = 3, Name = "Rout", Department = "Payroll" });
            return ListEmployees;
        }
    }

    // sử dụng Constructor injection
    public class EmployeeBL
    {
        public IEmployeeDAL employeeDAL;
        public EmployeeBL(IEmployeeDAL employeeDAL)
        {
            this.employeeDAL = employeeDAL;
        }
        public List<Employee> GetAllEmployees()
        {
            Return employeeDAL.SelectAllEmployees();
        }
    }
```

## ưu điểm
1. Nó tạo một hợp đồng phụ thuộc mạnh mẽ.
2. Nó chuyển qua sử dụng phương thức khởi tạo.
3. Giúp viết Unit test dễ dàng hơn.
4. Mở rộng dự án dễ dàng hơn.

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>