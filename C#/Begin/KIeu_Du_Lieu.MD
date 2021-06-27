# Kiểu dữ liệu

- Hệ thống kiểu dữ liệu, phân biệt giữa kiểu dữ liệu xây dựng
sẵn (như int, bool, string…) với kiểu dữ liệu do người dùng định nghĩa (lớp hay cấu trúc
do người lập trình tạo ra...). Một số cơ bản khác về lập trình như tạo và sử dụng biến dữ
liệu hay hằng cũng được đề cập cùng với cấu trúc liệt kê, chuỗi, định danh, biểu thức và
cậu lệnh.

- Như chúng ta đã biết C# là một ngôn ngữ hướng đối tượng rất mạnh, và công việc của
người lập trình là kế thừa để tạo và khai thác các đối tượng. Do vậy để nắm vững và
phát triển tốt người lập trình cần phải đi từ những bước đi dầu tiên tức là đi vào tìm hiểu
những phần cơ bản và cốt lõi nhất của ngôn ngữ.
Kiểu dữ liệu

- C# là ngôn ngữ lập trình mạnh về kiểu dữ liệu, một ngôn ngữ mạnh về kiểu dữ liệu là
phải khai báo kiểu của mỗi đối tượng khi tạo (kiểu số nguyên, số thực, kiểu chuỗi, kiểu
điều khiển...) và trình biên dịch sẽ giúp cho người lập trình không bị lỗi khi chỉ cho phép
một loại kiểu dữ liệu có thể được gán cho các kiểu dữ liệu khác. Kiểu dữ liệu của một
đối tượng là một tín hiệu để trình biên dịch nhận biết kích thước của một đối tượng (kiểu
int có kích thước là 4 byte) và khả năng của nó (như một đối tượng button có thể vẽ,
phản ứng khi nhấn,...).

- Tương tự như C++ hay Java, C# chia thành hai tập hợp kiểu dữ liệu chính: Kiểu xây
dựng sẵn (built- in) mà ngôn ngữ cung cấp cho người lập trình và kiểu được người dùng
định nghĩa (user-defined) do người lập trình tạo ra.

- C# phân tập hợp kiểu dữ liệu này thành hai loại: Kiểu dữ liệu giá trị (value) và kiểu dữ
liệu tham chiếu (reference). Việc phân chi này do sự khác nhau khi lưu kiểu dữ liệu giá
trị và kiểu dữ liệu tham chiếu trong bộ nhớ. Đối với một kiểu dữ liệu giá trị thì sẽ được
lưu giữ kích thước thật trong bộ nhớ đã cấp phát là stack. Trong khi đó thì địa chỉ của
kiểu dữ liệu tham chiếu thì được lưu trong stack nhưng đối tượng thật sự thì lưu trong
bộ nhớ heap.

- Nếu chúng ta có một đối tượng có kích thước rất lớn thì việc lưu giữ chúng trên bộ nhớ
heap rất có ích, trong chương 4 sẽ trình bày những lợi ích và bất lợi khi làm việc với 
kiểu dữ liệu tham chiếu, còn trong chương này chỉ tập trung kiểu dữ kiểu cơ bản hay
kiểu xây dựng sẵn.

- Tất cả các kiểu dữ liệu xây dựng sẵn là kiểu dữ liệu giá trị ngoại trừ các đối tượng và
chuỗi. Và tất cả các kiểu do người dùng định nghĩa ngoại trừ kiểu cấu trúc đều là kiểu
dữ liệu tham chiếu.

- Ngoài ra C# cũng hỗ trợ một kiểu con trỏ C++, nhưng hiếm khi được sử dụng, và chỉ
khi nào làm việc với những đoạn mã lệnh không được quản lý (unmanaged code). Mã
lệnh không được quản lý là các lệnh được viết bên ngoài nền .MS.NET, như là các đối
tượng COM.

# Kiểu dữ liệu xây dựng sẵn

- Ngôn ngữ C# đưa ra các kiểu dữ liệu xây dựng sẵn rất hữu dụng, phù hợp với một ngôn
ngữ lập trình hiện đại, mỗi kiểu dữ liệu được ánh xạ đến một kiểu dữ liệu được hỗ trợ
bởi hệ thống xác nhận ngôn ngữ chung (Common Language Specification: CLS) trong
MS.NET. Việc ánh xạ các kiểu dữ liệu nguyên thuỷ của C# đến các kiểu dữ liệu của
.NET sẽ đảm bảo các đối tượng được tạo ra trong C# có thể được sử dụng đồng thời
với các đối tượng được tạo bởi bất cứ ngôn ngữ khác được biên dịch bởi .NET, như
VB.NET.

- Mỗi kiểu dữ liệu có một sự xác nhận và kích thước không thay đổi, không giống như
C++, int trong C# luôn có kích thước là 4 byte bởi vì nó được ánh xạ từ kiểu Int32 trong
. NET.

Bảng sau sẽ mô tả một số các kiểu dữ liệu được xây dựng sẵn
******************************************************************

- Kiểu giá trị logic chỉ có thể nhận được giá trị là true hay false mà thôi. Một giá trị
nguyên không thể gán vào một biến kiểu logic trong C# và không có bất cứ chuyển đổi
ngầm định nào. Điều này khác với C/C++, cho phép biến logic được gán giá trị
nguyên, khi đó giá trị nguyên 0 là false và các giá trị còn lại là true.
Chọn kiểu dữ liệu

- Thông thường để chọn một kiểu dữ liệu nguyên để sử dụng như short, int hay long
thường dựa vào độ lớn của giá trị muốn sử dụng. Ví dụ, một biến ushort có thể lưu giữ
giá trị từ 0 đến 65.535, trong khi biến ulong có thể lưu giữ giá trị từ 0 đến 4.294.967.295,
do đó tùy vào miền giá trị của phạm vi sử dụng biến mà chọn các kiểu dữ liệu thích hợp
nhất. Kiểu dữ liệu int thường được sử dụng nhiều nhất trong lập trình vì với kích thước
4 byte của nó cũng đủ để lưu các giá trị nguyên cần thiết.

- Kiểu số nguyên có dấu thường được lựa chọn sử dụng nhiều nhất trong kiểu số trừ khi
có lý do chính đáng để sử dụng kiểu dữ liệu không dấu.

- Cách tốt nhất khi sử dụng biến không dấu là giá trị của biến luôn luôn dương, biến này
thường thể hiện một thuộc tính nào đó có miền giá trị dương. Ví dụ khi cần khai báo
một biến lưu giữ tuổi của một người thì ta dùng kiểu byte (số nguyên từ 0-255) vì tuổi
của người không thể nào âm được.

- Kiểu float, double, và decimal đưa ra nhiều mức độ khác nhau về kích thước cũng như
độ chính xác.Với thao tác trên các phân số nhỏ thì kiểu float là thích hợp nhất. Tuy nhiên
lưu ý rằng trình biên dịch luôn luôn hiểu bất cứ một số thực nào cũng là một số kiểu
double trừ khi chúng ta khai báo rõ ràng. Để gán một số kiểu float thì số phải có ký tự f
theo sau.

float soFloat = 24f;

- Kiểu dữ liệu ký tự thể hiện các ký tự Unicode, bao gồm các ký tự đơn giản, ký tự theo
mã Unicode và các ký tự thoát khác được bao trong những dấu nháy đơn. Ví dụ, A là
một ký tự đơn giản trong khi \u0041 là một ký tự Unicode. Ký tự thoát là những ký tự
đặc biệt bao gồm hai ký tự liên tiếp trong đó ký tự dầu tiên là dấu chéo ‘\’. Ví dụ, \t là
dấu tab. 

************************************************************************

# Chuyển đổi các kiểu dữ liệu

- Những đối tượng của một kiểu dữ liệu này có thể được chuyển sang những đối tượng
của một kiểu dữ liệu khác thông qua cơ chế chuyển đổi tường minh hay ngầm định.
Chuyển đổi nhầm định được thực hiện một cách tự động, trình biên dịch sẽ thực hiện
công việc này. Còn chuyển đổi tường minh diễn ra khi chúng ta gán ép một giá trị cho
kiểu dữ liệu khác.

- Việc chuyển đổi giá trị ngầm định được thực hiện một cách tự động và đảm bảo là không
mất thông tin. Ví dụ, chúng ta có thể gán ngầm định một số kiểu short (2 byte) vào một
số kiểu int (4 byte) một cách ngầm định. Sau khi gán hoàn toàn không mất dữ liệu vì bất
cứ giá trị nào của short cũng thuộc về int:

short x = 10;

int y = x; // chuyển đổi ngầm định

- Tuy nhiên, nếu chúng ta thực hiện chuyển đổi ngược lại, chắc chắn chúng ta sẽ bị mất
thông tin. Nếu giá trị của số nguyên đó lớn hơn 32.767 thì nó sẽ bị cắt khi chuyển đổi.
Trình biên dịch sẽ không thực hiện việc chuyển đổi ngầm định từ số kiểu int sang số
kiểu short:

short x;
int y = 100;
x = y; // Không biên dịch, lỗi !!!
Để không bị lỗi chúng ta phải dùng lệnh gán tường minh, đoạn mã trên được viết lại như
sau:
short x;
int y = 500;
x = (short) y; // Ép kiểu tường minh, trình biên dịch không
báo lỗi

