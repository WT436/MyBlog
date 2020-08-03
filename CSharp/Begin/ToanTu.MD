Toán tử

Toán tử gán

Đến lúc này toán tử gán khá quen thuộc với chúng ta, hầu hết các chương trình minh
họa từ đầu sách đều đã sử dụng phép gán. Toán tử gán hay phép gán làm cho toán hạng
bên trái thay đổi giá trị bằng với giá trị của toán hạng bên phải. Toán tử gán là toán tử
hai ngôi.

Đây là toán tử đơn giản nhất thông dụng nhất và cũng dễ sử dụng nhất.

Toán tử toán học

Ngôn ngữ C# cung cấp năm toán tử toán học, bao gồm bốn toán tử đầu các phép toán cơ
bản. Toán tử cuối cùng là toán tử chia nguyên lấy phần dư. Chúng ta sẽ tìm hiểu chi tiết
các phép toán này trong phần tiếp sau.

Các phép toán số học cơ bản (+,-,*,/)

Các phép toán này không thể thiếu trong bất cứ ngôn ngữ lập trình nào, C# cũng không
ngoại lệ, các phép toán số học đơn giản nhưng rất cần thiết bao gồm: phép cộng (+),
phép trừ (-), phép nhân (*), phép chia (/) nguyên và không nguyên.

Khi chia hai số nguyên, thì C# sẽ bỏ phần phân số, hay bỏ phần dư, tức là nếu ta chia 8/
3 thì sẽ được kết quả là 2 và sẽ bỏ phần dư là 2, do vậy để lấy được phần dư này thì C#
cung cấp thêm toán tử lấy dư sẽ được trình bày trong phần kế tiếp.

Tuy nhiên, khi chia cho số thực có kiểu như float, double, hay decimal thì kết quả chia
được trả về là một số thực.

Phép toán chia lấy dư

Để tìm phần dư của phép chia nguyên, chúng ta sử dụng toán tử chia lấy dư (%). VíThật
sự phép toán chia lấy dư rất hữu dụng cho người lập trình . Khi chúng ta thực hiện một
phép chia dư n cho một số khác, nếu số này là bội số của n thì kết quả của phép chia dư
là 0.

20 % 5 = 0 vì 20 là một bội số của 5.

Điều này cho phép chúng ta ứng dụng trong vòng lặp, khi muốn thực hiện một công việc
nào đó cách khoảng n lần, ta chỉ cần kiểm tra phép chia dư n, nếu kết quả bằng 0 thì thực hiện công việc. Cách sử dụng này đã áp dụng trong ví dụ minh họa sử dụng vòng lặp for
bên trên. Ví dụ sau minh họa sử dụng các phép toán chia trên các số nguyên, thực...
Phép chia và phép chia lấy dư.

-----------------------------------------------------------------------------

using System; class Tester { public static void Main() {
int i1, i2; float f1, f2; double d1, d2; decimal dec1,
dec2; i1 = 17; i2 = 4; f1 = 17f; f2 = 4f; d1 = 17; d2 = 4;
dec1 = 17; dec2 = 4; Console.WriteLine("Integer: \t{0}",
i1/i2); Console.WriteLine("Float: \t{0}", f1/f2);
Console.WriteLine("Double: \t{0}", d1/d2);
Console.WriteLine("Decimal: \t{0}", dec1/dec2);
Console.WriteLine("\nModulus: : \t{0}", i1%i2); } }

-----------------------------------------------------------------------------

Kết quả:
Integer: 4
float: 4.25 double: 4.25 decimal: 4.25
Modulus: 1

-----------------------------------------------------------------------------

Toán tử tăng và giảm

Khi sử dụng các biến số ta thường có thao tác là cộng một giá trị vào biến, trừ đi một
giá trị từ biến đó, hay thực hiện các tính toán thay đổi giá trị của biến sau đó gán giá trị
mới vừa tính toán cho chính biến đó.

Tính toán và gán trở lại

Giả sử chúng ta có một biến tên Luong lưu giá trị lương của một người, biến Luong này
có giá trị hiện thời là 1.500.000, sau đó để tăng thêm 200.000 ta có thể viết như sau:
Trong câu lệnh trên phép cộng được thực hiện trước, khi đó kết quả của vế phải là
1.700.000 và kết quả này sẽ được gán lại cho biến Luong, cuối cùng Luong có giá trị là
1.700.000. Chúng ta có thể thực hiện việc thay đổi giá trị rồi gán lại cho biến với bất kỳ
phép toán số học nào:

Luong = Luong * 2;
Luong = Luong – 100.000;
...

Do việc tăng hay giảm giá trị của một biến rất thường xảy ra trong khi tính toán nên C#
cung cấp các phép toán tự gán (self- assignment). Bảng sau liệt kê các phép toán tự gán.

***********************************

Dựa trên các phép toán tự gán trong bảng ta có thể thay thế các lệnh tăng giảm lương
như sau:

Luong += 200.000; Luong *= 2;
Luong -= 100.000;

Kết quả của lệnh thứ nhất là giá trị của Luong sẽ tăng thêm 200.000, lệnh thứ hai sẽ làm
cho giá trị Luong nhân đôi tức là tăng gấp 2 lần, và lệnh cuối cùng sẽ trừ bớt 100.000
của Luong.

Do việc tăng hay giảm 1 rất phổ biến trong lập trình nên C# cung cấp hai toán tử đặc
biệt là tăng một (++) hay giảm một (--).

Khi đó muốn tăng đi một giá trị của biến đếm trong vòng lặp ta có thể viết như sau:
bienDem++;

Toán tử tăng giảm tiền tố và tăng giảm hậu tố

Giả sử muốn kết hợp các phép toán như gia tăng giá trị của một biến và gán giá trị của
biến cho biến thứ hai, ta viết như sau:

var1 = var2++;

Câu hỏi được đặt ra là gán giá trị trước khi cộng hay gán giá trị sau khi đã cộng. Hay nói
cách khác giá trị ban đầu của biến var2 là 10, sau khi thực hiện ta muốn giá trị của var1
là 10, var2 là 11, hay var1 là 11, var2 cũng 11?

Để giải quyết yêu cầu trên C# cung cấp thứ tự thực hiện phép toán tăng/giảm với phép
toán gán, thứ tự này được gọi là tiền tố (prefix) hay hậu tố (postfix). Do đó ta có thể viết:

var1 = var2++; // Hậu tố

Khi lệnh này được thực hiện thì phép gán sẽ được thực hiện trước tiên, sau đó mới đến
phép toán tăng. Kết quả là var1 = 10 và var2 = 11. Còn đối với trường hợp tiền tố:
var1 = ++var2;

Khi đó phép tăng sẽ được thực hiện trước tức là giá trị của biến var2 sẽ là 11 và cuối
cùng phép gán được thực hiện. Kết quả cả hai biến var1 và var2 điều có giá trị là 11.

Để hiểu rõ hơn về hai phép toán này chúng ta sẽ xem ví dụ minh họa sau
Minh hoạ sử dụng toán tử tăng trước và tăng sau khi gán.

-----------------------------------------------------------------------------

using System; class Tester { static int Main() { int
valueOne = 10; int valueTwo; valueTwo = valueOne++;
Console.WriteLine("Thuc hien tang sau: {0}, {1}", valueOne,
valueTwo); valueOne = 20; valueTwo = ++valueOne;
Console.WriteLine("Thuc hien tang truoc: {0}, {1}",
valueOne, valueTwo); return 0; } }

-----------------------------------------------------------------------------

Kết quả:
Thuc hien tang sau: 11, 10
Thuc hien tang truoc: 21, 21

-----------------------------------------------------------------------------

Toán tử quan hệ

Những toán tử quan hệ được dùng để so sánh giữa hai giá trị, và sau đó trả về kết quả là
một giá trị logic kiểu bool (true hay false). Ví dụ toán tử so sánh lớn hơn (>) trả về giá
trị là true nếu giá trị bên trái của toán tử lớn hơn giá trị bên phải của toán tử. Do vậy 5 >
2 trả về một giá trị là true, trong khi 2 > 5 trả về giá trị false.

Các toán tử quan hệ trong ngôn ngữ C# được trình bày ở bảng 3.4 bên dưới. Các toán tử
trong bảng được minh họa với hai biến là value1 và value2, trong đó value1 có giá trị là
100 và value2 có giá trị là 50.

Như trong bảng trên ta lưu ý toán tử so sánh bằng (==), toán tử này được ký hiệu bởi hai
dấu bằng (=) liền nhau và cùng trên một hàng , không có bất kỳ khoảng trống nào xuất
hiện giữa chúng. Trình biên dịch C# xem hai dấu này như một toán tử.

Toán tử logic

Trong câu lệnh if mà chúng ta đã tìm hiểu trong phần trước, thì khi điều kiện là true thì
biểu thức bên trong if mới được thực hiện. Đôi khi chúng ta muốn kết hợp nhiều điều
kiện với nhau như: bắt buộc cả hai hay nhiều điều kiện phải đúng hoặc chỉ cần một trong
các điều kiện đúng là đủ hoặc không có điều kiện nào đúng...C# cung cấp một tập hợp
các toán tử logic để phục vụ cho người lập trình.

Bảng dưới liệt kệ ba phép toán logic, bảng này cũng sử dụng hai biến minh họa là x, và
y trong đó x có giá trị là 5 và y có giá trị là 7.

Toán tử and sẽ kiểm tra cả hai điều kiện. Trong bảng trên có minh họa biểu thức logic
sử dụng toán tử and:

(x == 3) && (y == 7)
Toàn bộ biểu thức được xác định là sai vì có điều kiện (x == 3) là sai.
Với toán tử or, thì một hay cả hai điều kiện đúng thì đúng, biểu thức sẽ có giá trị là sai
khi cả hai điều kiện sai. Do vậy ta xem biểu thức minh họa toán tử or:

(x == 3) || (y == 7)
Biểu thức này được xác định giá trị là đúng do có một điều kiện đúng là (y == 7) là
đúng.

Đối với toán tử not, biểu thức sẽ có giá trị đúng khi điều kiện trong ngoặc là sai, và
ngược lại, do đó biểu thức:

!( x == 3)

có giá trị là đúng vì điều kiện trong ngoặc tức là (x == 3) là sai.

Như chúng ta đã biết đối với phép toán logic and thì chỉ cần một điều kiện trong biểu
thức sai là toàn bộ biểu thức là sai, do vậy thật là dư thừa khi kiểm tra các điều kiện còn
lại một khi có một điều kiện đã sai. Giả sử ta có đoạn chương trình sau:
int x = 8;

if ((x == 5) && (y == 10))

Khi đó biểu thức if sẽ đúng khi cả hai biểu thức con là (x == 5) và (y == 10) đúng. Tuy
nhiên khi xét biểu thức thứ nhất do giá trị x là 8 nên biểu thức (x == 5) là sai. Khi đó
không cần thiết để xác định giá trị của biểu thức còn lại, tức là với bất kỳ giá trị nào của
biểu thức (y== 10) thì toàn bộ biểu thức điều kiện if vẫn sai.

Tương tự với biểu thức logic or, khi xác định được một biểu thức con đúng thì không
cần phải xác định các biểu thức con còn lại, vì toán tử logic or chỉ cần một điều kiện
đúng là đủ:

int x =8;
if ( (x == 8) || (y == 10))

Khi kiểm tra biểu thức (x == 8) có giá trị là đúng, thì không cần phải xác định giá trị của
biểu thức (y == 10) nữa.

Ngôn ngữ lập trình C# sử dụng logic như chúng ta đã thảo luận bên trên để loại bỏ các
tính toán so sánh dư thừa và cũng không logic nữa!

Độ ưu tiên toán tử

Trình biên dịch phải xác định thứ tự thực hiện các toán tử trong trường hợp một biểu
thức có nhiều phép toán, giả sử, có biểu thức sau:

var1 = 5+7*3;

Biểu thức trên có ba phép toán để thực hiện bao gồm (=, +,*). Ta thử xét các phép toán
theo thứ tự từ trái sang phải, đầu tiên là gán giá trị 5 cho biến var1, sau đó cộng 7 vào
5 là 12 cuối cùng là nhân với 3, kết quả trả về là 36, điều này thật sự có vấn đề, không
đúng với mục đích yêu cầu của chúng ta. 
Do vậy việc xây dựng một trình tự xử lý các toán tử là hết sức cần thiết. 
Các luật về độ ưu tiên xử lý sẽ bảo trình biên dịch biết được
toán tử nào được thực hiện trước trong biểu thức.Tương tự như trong phép toán đại số
thì phép nhân có độ ưu tiên thực hiện trước phép toán cộng, do vậy 5+7*3 cho kết quả là
26 đúng hơn kết quả 36. Và cả hai phép toán cộng và phép toán nhân điều có độ ưu tiên
cao hơn phép gán. Như vậy trình biên dịch sẽ thực hiện các phép toán rồi sau đó thực
hiện phép gán ở bước cuối cùng. Kết quả đúng của
câu lệnh trên là biến var1 sẽ nhận giá trị là 26.

Trong ngôn ngữ C#, dấu ngoặc được sử dụng để thay đổi thứ tự xử lý, điều này cũng
giống trong tính toán đại số. Khi đó muốn kết quả 36 cho biến var1 có thể viết:
var1 = (5+7) * 3;

Biểu thức trong ngoặc sẽ được xử lý trước và sau khi có kết quả là 12 thì phép nhân
được thực hiện.

Bảng dưới liệt kê thứ tự độ ưu tiên các phép toán trong C#.

Các phép toán được liệt kê cùng loại sẽ có thứ tự theo mục thứ thự của bảng: thứ tự trái
tức là độ ưu tiên của các phép toán từ bên trái sang, thứ tự phải thì các phép toán có độ
ưu tiên từ bên phải qua trái. Các toán tử khác loại thì có độ ưu tiên từ trên xuống dưới,
do vậy các toán tử loại cơ bản sẽ có độ ưu tiên cao nhất và phép toán gán sẽ có độ ưu
tiên thấp nhất trong các toán tử.

Toán tử ba ngôi

Hầu hết các toán tử đòi hỏi có một toán hạng như toán tử (++, --) hay hai toán hạng như
(+,-,*,/,...). Tuy nhiên, C# còn cung cấp thêm một toán tử có ba toán hạng (?:). Toán tử
này có cú pháp sử dụng như sau:

<Biểu thức điều kiện > ? <Biểu thức thứ 1> : <Biểu thức thứ 2>

Toán tử này sẽ xác định giá trị của một biểu thức điều kiện, và biểu thức điều kiện này
phải trả về một giá trị kiểu bool. Khi điều kiện đúng thì <biểu thức thứ 1> sẽ được thực
hiện, còn ngược lại điều kiện sai thì <biểu thức thứ 2> sẽ được thực hiện. Có thể diễn
giải theo ngôn ngữ tự nhiên thì toán tử này có ý nghĩa : “Nếu điều kiện đúng thì làm
công việc thứ nhất, còn ngược lại điều kiện sai thì làm công việc thứ hai”. Cách sử dụng
toán tử ba ngôi này được minh họa trong ví dụ sau.
Sử dụng toán tử bao ngôi.

-----------------------------------------------------------------------------

using System; class Tester { public static int Main() {
int value1; int value2; int maxValue; value1 = 10; value2
= 20; maxValue = value1 > value2 ? value1 : value2;
Console.WriteLine("Gia tri thu nhat {0}, gia tri thu hai
{1}, gia tri lon nhat {2}",value1,value2, maxValue);
return 0; } }

-----------------------------------------------------------------------------

Kết quả:
Gia tri thu nhat 10, gia tri thu hai 20, gia tri lon nhat 20

-----------------------------------------------------------------------------

Trong ví dụ minh họa trên toán tử ba ngôi được sử dụng để kiểm tra xem giá trị của
value1 có lớn hơn giá trị của value2, nếu đúng thì trả về giá trị của value1, tức là gán giá
trị value1 cho biến maxValue, còn ngược lại thì gán giá trị value2 cho biến maxValue.
