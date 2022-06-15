### SQL Functions

1. ABS : Trả ra giá trị tuyệt đối của một  số n
    - Hàm này sẽ nhận bất kỳ đối số nào có thể convert qua số và nó trả về kiểu dữ liệu của đối số
```sql
SELECT ABS('-15') "Absolute" FROM DUAL; -- '15'
SELECT ABS(-15) "Absolute" FROM DUAL;  -- 15
```

2. ACOS 
    - ACOS trả về cosin cung của n. Đối số n phải nằm trong phạm vi từ -1 đến 1 và hàm trả về giá trị trong phạm vi từ 0 đến pi, được biểu thị bằng radian.
    - Hàm này nhận như một đối số bất kỳ kiểu dữ liệu số hoặc bất kỳ kiểu dữ liệu không phải số nào có thể được chuyển đổi hoàn toàn thành kiểu dữ liệu số. Nếu đối số là BINARY_ FLOAT, thì hàm trả về BINARY_DOUBLE. Nếu không, hàm trả về cùng một kiểu dữ liệu số như đối số

```sql
SELECT ACOS(0.5)"Arc_Cosine" FROM DUAL; -- 1.04719755119659774615421446109316762805

SELECT ACOS('0.5')"Arc_Cosine" FROM DUAL; -- 1.04719755119659774615421446109316762805

```

3. ADD_MONTHS 
    - ADD_MONTHS trả về ngày tháng cộng với số tháng nguyên. Đối số ngày có thể là giá trị ngày giờ hoặc bất kỳ giá trị nào có thể được chuyển đổi hoàn toàn thành DATE. 
    - Đối số số nguyên có thể là số nguyên hoặc bất kỳ giá trị nào có thể được chuyển đổi hoàn toàn thành số nguyên. Loại trả về luôn là DATE, bất kể loại dữ liệu của ngày. 
    - Nếu ngày là ngày cuối cùng của tháng hoặc nếu tháng kết quả có ít ngày hơn thành phần ngày của ngày, thì kết quả là ngày cuối cùng của tháng kết quả. Nếu không, kết quả có cùng thành phần ngày với ngày.

```sql 
SELECT hire_date 
FROM employees
WHERE last_name = 'Baer'; -- 07-JUN-02
-- số tháng vượt quá 1 năm sẽ đẩy qua năm mới
SELECT TO_CHAR(ADD_MONTHS(hire_date,7),'DD-MON-YYYY') "Next month"
FROM employees
WHERE last_name = 'Baer'; -- 07-JAN-2003
-- nếu không vượt qua thì cộng như thường
SELECT TO_CHAR(ADD_MONTHS(hire_date,2),'DD-MON-YYYY') "Next month"
FROM employees
WHERE last_name = 'Baer'; -- 07-AUG-2002
```

4. APPENDCHILDXML

    ```sql 
        APPENDCHILDXML ( XMLType_instance , XPath_string , value_expr, namespace_string)
    ```

    - Thêm một giá trị do người dùng cung cấp vào XML đích như là phần tử con của nút được biểu thị bằng biểu thức XPath.
    - XMLType_instance là một phiên bản của XMLType
    - XPath_string là một biểu thức Xpath cho biết một hoặc nhiều nút mà một hoặc nhiều nút con sẽ được nối vào. Bạn có thể chỉ định một chuỗi XPath_string tuyệt đối với một dấu gạch chéo đầu tiên hoặc một chuỗi XPath_string tương đối bằng cách bỏ qua dấu gạch chéo đầu tiên. Nếu bạn bỏ qua dấu gạch chéo đầu tiên, ngữ cảnh của đường dẫn tương đối sẽ được mặc định là nút gốc.
    - Value_expr chỉ định một hoặc nhiều nút của XMLType. Nó phải phân giải thành một chuỗi.

5. ASCIISTR

    - ASCIISTR coi đối số của nó là một chuỗi hoặc một biểu thức phân giải thành một chuỗi, trong bất kỳ bộ ký tự nào và trả về phiên bản ASCII của chuỗi trong bộ ký tự cơ sở dữ liệu. Các ký tự không phải ASCII được chuyển đổi thành dạng \ xxxx, trong đó xxxx đại diện cho một đơn vị mã UTF-16

``` sql 
SELECT ASCIISTR('ABÄCDE') FROM DUAL; -- AB\00C4CDE
```

6. ASCII

    ```sql
    ASCII (char)
    ```

    - ASCII trả về biểu diễn thập phân trong bộ ký tự cơ sở dữ liệu của ký tự đầu tiên của char.
    -  char có thể là kiểu dữ liệu CHAR, VARCHAR2, NCHAR hoặc NVARCHAR2. Giá trị trả về thuộc loại dữ liệu NUMBER. Nếu bộ ký tự cơ sở dữ liệu của bạn là ASCII 7-bit, thì hàm này trả về giá trị ASCII. Nếu bộ ký tự cơ sở dữ liệu của bạn là Mã EBCDIC, thì hàm này trả về giá trị EBCDIC. Không có chức năng ký tự EBCDIC tương ứng.

    ``` sql
    SELECT ASCII(SUBSTR(last_name, 1, 1)) last_name FROM employees
    ```
7. ASIN

    - ASIN trả về cung sin của n. Đối số n phải nằm trong khoảng từ -1 đến 1 và hàm trả về một giá trị trong phạm vi từ -pi / 2 đến pi / 2, được biểu thị bằng radian.
    - Hàm này nhận như một đối số bất kỳ kiểu dữ liệu số hoặc bất kỳ kiểu dữ liệu không phải số nào có thể được chuyển đổi hoàn toàn thành kiểu dữ liệu số. Nếu đối số là BINARY_FLOAT, sau đó hàm trả về BINARY_DOUBLE. Nếu không, hàm trả về cùng kiểu dữ liệu số như đối số.

```sql
SELECT ASIN(.3) "Arc_Sine" FROM DUAL;
SELECT ASIN(0.3) "Arc_Sine" FROM DUAL;
SELECT ASIN('0.3') "Arc_Sine" FROM DUAL;
```

8. ATAN 
- ATAN trả về tiếp tuyến cung của n. Đối số n có thể nằm trong một phạm vi không bị giới hạn và
trả về một giá trị trong phạm vi từ -pi / 2 đến pi / 2, được biểu thị bằng radian.
Hàm này nhận như một đối số bất kỳ kiểu dữ liệu số hoặc bất kỳ kiểu dữ liệu không phải số nào
có thể được chuyển đổi hoàn toàn thành kiểu dữ liệu số. Nếu đối số là BINARY_
FLOAT, sau đó hàm trả về BINARY_DOUBLE. Nếu không, hàm trả về
cùng kiểu dữ liệu số như đối số.

```sql 
SELECT ATAN(.3) "Arc_Tangent" FROM DUAL;
```

9. ATAN2

    - ATAN2 trả về tiếp tuyến cung của n1 và n2. Đối số n1 có thể ở trong một
phạm vi và trả về một giá trị trong phạm vi từ -pi đến pi, tùy thuộc vào các dấu hiệu của n1 và
n2, tính bằng radian. ATAN2 (n1, n2) giống ATAN2 (n1 / n2).
Hàm này nhận làm đối số bất kỳ kiểu dữ liệu số hoặc bất kỳ kiểu dữ liệu không phải số nào
có thể được chuyển đổi hoàn toàn thành kiểu dữ liệu số. Nếu bất kỳ đối số nào là BINARY_
FLOAT hoặc BINARY_DOUBLE, sau đó hàm trả về BINARY_DOUBLE. Nếu không thì
hàm trả về NUMBER

```sql 
SELECT ATAN2(.3, .2) "Arc_Tangent2" FROM DUAL;
```
10. AVG

```sql
AVG (DISTINCT | ALL expr )OVER ( analytic_clause )
```

- AVG trả về giá trị trung bình của expr.
- Hàm này nhận như một đối số bất kỳ kiểu dữ liệu số hoặc bất kỳ kiểu dữ liệu không phải số nào có thể được chuyển đổi hoàn toàn thành kiểu dữ liệu số. 

- Hàm trả về như cũ kiểu dữ liệu là kiểu dữ liệu số của đối số.

```sql
SELECT AVG(salary) "Average" FROM employees;
```

11. BFILENAME