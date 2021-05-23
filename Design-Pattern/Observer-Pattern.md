# Observer Pattern

## Định Nghĩa: 
 Observer là một mẫu thiết kế hành vi cho phép bạn xác định cơ chế đăng ký để thông báo cho nhiều đối tượng về bất kỳ sự kiện nào xảy ra với đối tượng mà họ đang quan sát.
-  Tại sao nó lại là người quan sát : hiểu nôm na là ntn , giống như trong một  buổi phỏng vấn , người phỏng vấn sẽ đặt ra câu hỏi đúng không , ok vậy người phỏng vấn chính là người quan sát chúng ta . chúng ta người trả lời phỏng vấn chính là người sẽ giải đáp cái thắc mắc đó . nếu như các bạn đang tưởng tưởng 1 vs 1 thì nó cx đúng nhưng hãy mở rộng ra nào , vd như bạn là bill gates chẳng hạn , bạn đến 1 buổi thuyết trình triệu người xem , vậy triệu người xem đó chính là người theo dõi bạn , Bạn nói tôi đã có win 10 xịn xò  chẳng hạn , ngay lập tức , 1 triệu người đang theo dõi bạn sẽ nhận được 1 lời mời setting win 10  sớm nhất , 
![observer](https://user-images.githubusercontent.com/63473793/90074489-8f8afb00-dd25-11ea-873c-b735ec43a368.png)
## Độ Khó : 🔥🔥🔥🔥🔥
## Vấn Đề :
  Hãy tưởng tượng rằng bạn có hai loại đối tượng: Khách hàng và Cửa hàng. Khách hàng rất quan tâm đến một thương hiệu sản phẩm cụ thể (giả sử đó là một Win 10 mới) sẽ sớm có mặt trong cửa hàng.
-  Vấn đề đặt ra ở đây là , để giữ được khách hàng , hay nói cách khác là để  khách hàng có thể biết được thông tin mà chúng ta mới cập nhật , thì  chính khách hàng không thể ngày hôm nay đến của hàng để xem Win 10   mới đã lên kệ hay chưa ....
- Cái tiếp theo , chắc hẳng các bạn sẽ nghĩ là ồ vậy ta sẽ gửi mail cho từng khách đúng không , vậy họ đăng ký ở đâu , như thế nào ,  cách giải quyết ra sao , thay vì tạo ra 1 đống bùi nhùi class để sử lý vấn đề này .
-  khách hàng lãng phí thời gian kiểm tra sản phẩm còn hàng hoặc cửa hàng lãng phí nguồn lực để thông báo sai cho khách hàng.
-  Khi các bạn có thể code cách thông thường  tôi cam đoan code sẽ sảy ra  xung đột. 

## Cấu trúc 
![example](https://user-images.githubusercontent.com/63473793/90077450-57d38180-dd2c-11ea-8bc7-1375d2091987.png)
## Code c#
```c#
public interface INguoiDung
    {
        void Update(IQuanLy subject); 
    }
public interface IQuanLy
    {
        
        //Thêm Người dùng , người dùng đăng ký theo dõi , vào thực tế , các bạn triển khai mạnh ra nhé 
        void Attach(INguoiDung observer);

        //Xóa Người dùng , người dùng đăng ký theo dõi , vào thực tế , các bạn triển khai mạnh ra nhé
        void Detach(INguoiDung observer);

        // Theo dõi người dùng
        void Notify();
    }

 public class QuanLy : IQuanLy
    {
        // cái quần què này là điều kiện vd như mã win 10 là 404 chảng hạn 
        //Người dùng sẽ có điề kiện tôi muốn xem mã này sản phẩm này balabla 
        //hiểu đơn giản nó là thành phần mà người dùng mong đợi
        public int Ma_Mat_Hang_Dang_Duoc_Quan_Tam { get; set; }
        //danh sách người dùng nhé
        private List<INguoiDung> _iobserver = new List<INguoiDung>();
        // THêm người dùng
        public void Attach(INguoiDung observer)
        {
            Console.WriteLine("Quản lý: Thêm người dùng.");
            this._iobserver.Add(observer);
        }
        //Xóa Người Dùng
        public void Detach(INguoiDung observer)
        {
            this._iobserver.Remove(observer);
            Console.WriteLine("Quản lý: Xóa Người dùng.");
        }
        //THông Báo
        public void Notify()
        {
            Console.WriteLine("Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này : ");
            //Lấy Danh Sách Người Dùng nhé
            foreach (var observer in _iobserver)
            {
                //Gọi hàm Gửi Thông Tin 
                observer.Update(this);
            }
        }
        public void SomeBusinessLogic()
        {
            //do không có dữ liệu nên mk lấy random ngẫu nhiên sản phẩm nhé
            this.Ma_Mat_Hang_Dang_Duoc_Quan_Tam = new Random().Next(0, 6);
            Console.WriteLine("\nQuản lý: Cửa Hàng mới nhập về sản phẩm có mã code : " + this.Ma_Mat_Hang_Dang_Duoc_Quan_Tam);
            Thread.Sleep(5000);

            Console.WriteLine("Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : " + this.Ma_Mat_Hang_Dang_Duoc_Quan_Tam +" Cho các khách hàng đang quan tâm ");
            this.Notify();
        }
    }

 public class NguoiDung : INguoiDung
    {
        //triển khai thực tế đa dạng các kiểu con gà mái
        private string nameND;
        private int kieuND;

        public NguoiDung(string name, int vitri)
        {
            nameND = name;
            kieuND = vitri;
        }

        public void Update(IQuanLy subject)
        {
            if ((subject as QuanLy).Ma_Mat_Hang_Dang_Duoc_Quan_Tam == kieuND)
            //chính là điều kiện mk nhắc đến cái này thì tùy các bạn muốn làm ntn , bỏ cx dk ,
            // nhưng mk ko chịu đâu nhé 
            {
                Console.WriteLine("Nguoi Dung "+nameND+" đã Nhận Thông Tin Về mặt hàng : " + (subject as QuanLy).Ma_Mat_Hang_Dang_Duoc_Quan_Tam);
                //ở đây có thể gửi mail , sms , ......
            }
        }
    }

Console.OutputEncoding = Encoding.UTF8;
            var subject = new QuanLy();//tạo
            var observer1 = new NguoiDung("nam",1);
            subject.Attach(observer1);
            var observer2 = new NguoiDung("nam2", 2);
            subject.Attach(observer2);
            var observer3 = new NguoiDung("nam3", 3);
            subject.Attach(observer3);
            var observer4 = new NguoiDung("nam4", 4);
            subject.Attach(observer4);


            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 1
            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 2
            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 3
            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 4
            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 5
            subject.SomeBusinessLogic(); //Thông Báo Sự Kiện lần test 6

            subject.Detach(observer1); //xóa
            subject.Detach(observer2);
            subject.Detach(observer3);
            subject.Detach(observer4);
            Console.WriteLine("Xin chào Mình là  Hải Nam");
```
## Kết Quả 
```console
Quản lý: Thêm người dùng.
Quản lý: Thêm người dùng.
Quản lý: Thêm người dùng.
Quản lý: Thêm người dùng.

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 3
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 3 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :
Nguoi Dung nam3 đã Nhận Thông Tin Về mặt hàng : 3

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 1
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 1 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :
Nguoi Dung nam đã Nhận Thông Tin Về mặt hàng : 1

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 0
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 0 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 5
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 5 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 1
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 1 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :
Nguoi Dung nam đã Nhận Thông Tin Về mặt hàng : 1

Quản lý: Cửa Hàng mới nhập về sản phẩm có mã code : 2
Quản lý: Cửa hàng thông báo về mặt hàng mới về  có mã code là : 2 Cho các khách hàng đang quan tâm
Quản lý:Quét và  Thông Báo cho người Dùng quan tâm đến mã sản phẩm này :
Nguoi Dung nam2 đã Nhận Thông Tin Về mặt hàng : 2
Quản lý: Xóa Người dùng.
Quản lý: Xóa Người dùng.
Quản lý: Xóa Người dùng.
Quản lý: Xóa Người dùng.
Xin chào Mình là  Hải Nam
```
## Mã Nguồn 
- https://www.youtube.com/watch?v=_BpmfnqjgzQ&t=2375s
- https://refactoring.guru/design-patterns/observer
- https://www.dofactory.com/net/observer-design-pattern
- https://drive.google.com/file/d/18DdnryddqNKpLsx8iwqJ4yrUC9QrAF_y/view?usp=sharing
## Người Viết : Trần Hải Nam (WT436)