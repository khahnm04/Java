# **Xử lý chuỗi (String) trong Java**

## **1. String trong Java là immutable (bất biến)**
Trong Java, String là một đối tượng bất biến (immutable), có nghĩa là một khi giá trị của nó được tạo ra, nó không thể thay đổi.

Ví dụ:
```java
String s = "Hello world";
String t = " Java Core";
```
Chuỗi `s` và `t` không thể thay đổi giá trị sau khi được gán.

---
## **2. Các phương thức xử lý chuỗi trong Java**
### **2.1. Lấy thông tin về chuỗi**
```java
s.length();          // Trả về số ký tự trong chuỗi
s.charAt(i);         // Trả về ký tự tại vị trí i
```

### **2.2. Kiểm tra ký tự trong chuỗi**
```java
Character.isLowerCase(s.charAt(i));   // Kiểm tra ký tự có phải chữ thường không
Character.isUpperCase(s.charAt(i));   // Kiểm tra ký tự có phải chữ hoa không
Character.isAlphabetic(s.charAt(i));  // Kiểm tra ký tự có phải chữ cái không
Character.isDigit(s.charAt(i));       // Kiểm tra ký tự có phải chữ số không
```

### **2.3. Chuyển đổi chữ hoa - chữ thường**
```java
Character.toLowerCase(s.charAt(i));  // Chuyển ký tự thành chữ thường
Character.toUpperCase(s.charAt(i));  // Chuyển ký tự thành chữ hoa
s.toUpperCase();  // Trả về chuỗi viết hoa, không thay đổi chuỗi ban đầu
s.toLowerCase();  // Trả về chuỗi viết thường, không thay đổi chuỗi ban đầu
```

### **2.4. Ghép nối và so sánh chuỗi**
```java
s.concat(t);  // Nối chuỗi t vào chuỗi s

s.compareTo(t); // So sánh hai chuỗi theo thứ tự từ điển
// Trả về 0 nếu bằng nhau, số âm nếu s < t, số dương nếu s > t

s.compareToIgnoreCase(t); // So sánh nhưng không phân biệt hoa thường
```

### **2.5. Cắt chuỗi con**
```java
s.substring(x);     // Cắt chuỗi từ vị trí x đến hết
s.substring(x, y);  // Cắt chuỗi từ vị trí x đến y - 1
```

### **2.6. Kiểm tra và tìm kiếm chuỗi con**
```java
s.contains("...");   // Kiểm tra chuỗi con có tồn tại trong chuỗi không
s.indexOf(t);         // Vị trí đầu tiên của t trong s (nếu không có trả về -1)
```

### **2.7. Xử lý khoảng trắng**
```java
s.trim();  // Loại bỏ khoảng trắng ở đầu và cuối chuỗi
```

### **2.8. Chuyển chuỗi thành mảng ký tự**
```java
char[] arr = s.toCharArray();
for (char c : arr) {
    System.out.println(c);
}
```

---
## **3. Tách từ trong chuỗi: split & StringTokenizer**

### **3.1. Dùng `split()`**
```java
String s = "java   28tech  C++   28tech.com.vn";
String[] arr = s.split("\\s+"); // Tách chuỗi theo khoảng trắng
```

### **3.2. Dùng `StringTokenizer`**
```java
import java.util.StringTokenizer;

String s = "  nguyen,van...nam?di  ! hoc lap trinh";
StringTokenizer st = new StringTokenizer(s, ",.!?");

while(st.hasMoreTokens()) {
    System.out.println(st.nextToken());
}
```

---
## **4. Lớp `StringBuilder` - Chuỗi có thể thay đổi**
Trong Java, `String` là bất biến, nhưng `StringBuilder` có thể thay đổi giá trị.

Ví dụ:
```java
String s = "28tech hoc lap trinh";
StringBuilder builder = new StringBuilder(s);
builder.setCharAt(3, '@');
System.out.println(builder.toString());  // Kết quả: 28t@ch hoc lap trinh
```

---
## **5. Chuyển đổi giữa số và chuỗi**
### **5.1. Số thành chuỗi**
```java
int n = 83868386;
String s = "" + n;  // Hoặc dùng String.valueOf(n);
```

### **5.2. Chuỗi thành số**
```java
String s = "12345678";
int n = Integer.parseInt(s);
```

---
## **6. Xử lý số nguyên lớn với `BigInteger`**
Khi làm việc với số quá lớn không thể lưu trữ trong kiểu `int` hoặc `long`, ta dùng `BigInteger`.

```java
import java.math.BigInteger;

String s1 = "18238128381283812381123123123123";
String s2 = "192399239192393";

BigInteger num1 = new BigInteger(s1);
BigInteger num2 = new BigInteger(s2);

System.out.println(num1.add(num2));      // Cộng
System.out.println(num1.subtract(num2)); // Trừ
System.out.println(num1.multiply(num2)); // Nhân
System.out.println(num1.divide(num2));   // Chia
```

---
### **Kết luận**
- `String` là bất biến, không thể thay đổi sau khi tạo.
- Dùng `StringBuilder` nếu cần thao tác thay đổi nội dung chuỗi.
- Java cung cấp nhiều phương thức mạnh mẽ để xử lý chuỗi như tìm kiếm, cắt, nối, kiểm tra ký tự, chuyển đổi số và chuỗi.
- Khi làm việc với số lớn, `BigInteger` là giải pháp tối ưu.

🚀 Hãy thực hành ngay để làm chủ các thao tác với chuỗi trong Java!
