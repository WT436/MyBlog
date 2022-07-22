Tính kế thừa trong C#

Kế thừa là một trong 4 khía cạnh của lập trình hướng đối tượng, nó là khả năng cho phép chúng ta định nghĩa ra một lớp mới dựa trên một lớp khác có sẵn, kế thừa giúp cho việc mở rộng code - bảo trì trở nên dễ hơn.

Lớp cơ sở là lớp mà được lớp khác kế thừa.

Lớp kế thừa là lớp kế thừa lại các thuộc tính, phương thức từ lớp cơ sở.

Ví dụ, lớp NhanVien mô tả chung (thuộc tính) về nhân viên trong một công ty (chức năng, nhiệm vụ, văn bằng ...), kể cả các ứng xử (phương thức) của nhân viên. Từ đó kế thừa lại xây dựng nên lớp mới cho nhân viên lê tân NhanVienLeTan, nhân viên bán hàng NhanVienBanHang ..., nhưng lớp mới đã kế thừa lại các thông tin của lớp cơ sở và thêm vào những đặc tính riêng của nó.

Ví dụ, định nghĩa lớp Animal như sau

class Animal {
    public int Legs {get; set;}
    public float Weigh {get; set;}


    public void ShowLegs()
    {
        Console.WriteLine($"Legs: {Legs}");
    }
}

Animal có 2 thuộc tính Legs và Weigh, có 1 phương thức ShowLegs. Dùng nó làm lớp cơ sở để xây dựng lớp kế thừa có tên 

Cat:

class Cat : Animal {
    public string food;      // thuộc tính mới thêm

    public Cat()
    {
        Legs = 4;           // Thuộc tính Legs có sẵn - vì nó kế thừa từ Animal
        food = "Mouse";
    }

    public void Eat()
    {
        Console.WriteLine(meal);
    }
}

Khi sử dụng Cat

Cat cat = new Cat();
cat.ShowLegs();             // Phương thức này kế thừa từ lớp cơ sở
cat.Eat();                  // phương thức của riêng Cat

Dể khai báo lớp kế thừa dùng cú pháp, lớp cơ sở viết sau ký hiệu :

class LỚP_KẾ_THỪA : LỚP_CƠ_SỞ {
   //...
}
C# không hỗ trợ đa kế thừa (mỗi lớp kế thừa chỉ có một lớp cơ sở)

Lớp niêm phong sealed

Trong kỹ thuật lập trình, bạn có thể đánh dấu một lớp nào đó không bao giờ trở thành lớp cơ sở để phái sinh ra lớp khác - lớp đó gọi là bị niêm phong. Muốn niêm phong một lớp chỉ việc thêm từ khóa sealed

sealed class A {

}

class B : A {  // Chỗ này lỗi vì kế thừa lớp bị niêm phong

}

Dùng kỹ thuật niêm phong lớp (sealed) để đảm bảo không phái sinh các lớp kế thừa một cách thoải mái, mất kiểm soát, nhất là khi số dự án lớn, nhiều người tham gia.

Phương thức hủy và khởi tạo khi kế thừa

Như đã biết, phương thức khởi tạo chạy khi đối tượng được tạo (new), vấn đề là khi có sự kế thừa thì lưu ý: hàm khởi tạo của lớp cơ sở chạy trước, xong đến hàm khởi tạo của lớp kế thừa.

class A {
    public A() {
        Console.WriteLine("A Init");
    }
}

class B : A {
    public B()
    {
        Console.WriteLine("B Init");
    }
}

Khi sử dụng:

new B();
// KẾT QUẢ
// A Init
// B Ini
Tuy nhiên, khi phương thức khởi tạo lớp cơ sở có tham số, hoặc ấn định một phương thức khởi tạo của lớp cơ sở (nếu lớp cơ sở có quá tải nhiều phương thức khởi tạo), thì hàm tạo của lớp kế thừa phải chỉ định sẽ khởi chạy phương thức khởi tạo (và truyền tham số) nào của lớp cơ sở.

class A {
    public A(string mgs) {
        Console.WriteLine("A Init" + mgs);
    }
}

class B : A {
    public B(string abc) : base(abc)
    {
        Console.WriteLine("B Init");
    }
}

Sau phương thức tạo lớp kế thừa thấy có : base(abc) đây chính là chỉ ra hàm tạo lớp cơ sở sẽ chạy, đó là hàm có một tham số - và giá trị tham số được truyền vào.

new B("!ABC");
// KẾT QUẢ
// A Init!ABC
// B Ini

Đối với các phương thức hủy, khi đối tượng hủy nó sẽ thi hành phương thức hủy của lớp kế thừa trước, rồi mới đến phương thức hủy của lớp cơ sở (ngược với khởi tạo).

Chuyển kiểu - tương thích về kiểu khi sử dụng lớp
Trong chuỗi kế thừa ví dụ lớp A là lớp cơ sở, kế thừa bởi lớp B, lớp B lại là lớp cơ sở kế thừa bởi C

class A
{

};

class B : A
{

};

class C : B
{

}
Vậy có thể chuyển kiểu từ C -> B -> A. Bạn có thể chuyển kiểu một cách tường minh, hay ngầm định.

Chiều ngược lại thì không thể

C c = new C();
a = (A)c;       // chuyển kiểu tường minh
a = c;          // ngầm định
a = new C();    // ngầm định

B b = c;        // ngầm định

c = new A();    // lỗi - không thể chuyển kiểu thuận cây kế thừa -  Lớp cha không chuyển thành con được
Lớp kế thừa luôn có thể cast (chuyển) về lớp cơ sở