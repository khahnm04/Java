# **String**

## **1. Giới thiệu về lớp String trong Java**
> - String là lớp để xử lý xâu kí tự trong ngôn ngữ lập trình Java. Các bạn có thể nghĩ String như một mảng kí tự nhưng có thể mở rộng, thu hẹp và hỗ trợ rất nhiều hàm xử lý xâu thông dụng. Ví dụ "khanhvippro" là một chuỗi gồm 11 ký tự 'k', 'h', 'a', 'n', 'h', 'v', 'i', 'p', 'p', 'r', 'o' kết hợp lại.
>   
> - Trong Java, String là một trong những kiểu dữ liệu quan trọng nhất. String trong java là một __object immutable__, nó đại diện cho một chuỗi ký tự bất biến có nghĩa nghĩa là bạn không thể thay đổi giá trị của String khi nó đã được khởi tạo.
>   
> - Một số đặc điểm của String:
>   - Immutable: Khi một String được tạo, nó không thể bị thay đổi.
>   - String Pool: Java tối ưu hóa bộ nhớ bằng cách lưu trữ các chuỗi giống nhau trong một vùng nhớ đặc biệt gọi là String Pool.
>   - Hỗ trợ Unicode: Java hỗ trợ đầy đủ Unicode, cho phép lưu trữ các ký tự từ nhiều ngôn ngữ khác nhau.
>
## **2. Khởi tạo String trong java**
> - Trong java chúng ta có 2 cách để tạo một chuỗi
>   - Chuỗi ký tự
>   - Sử dụng từ khoá new
>
> ### **2.1 Tạo string bằng một chuỗi ký tự**
>> - Ví dụ: khởi tạo 2 chuỗi s1 và s2 với giá trị giống nhau
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>       String s1 = "javacore";
>>       String s2 = "javacore";
>>       System.out.println(s);
>>       }
>>   }
>>   ```
>> - Khi khởi tạo s1, chuỗi "javacore" sẽ được lưu trong string pool (vùng nhớ đặc biệt trong heap). Khi khởi tạo s2, JVM sẽ kiểm tra trong string pool, nếu đã có "javacore" thì s2 sẽ trỏ đến chuỗi có sẵn, còn nếu chưa có thì JVM sẽ tạo một chuỗi mới và lưu vào string pool.
>> 
>> - Mình sẽ giải thích đoạn code này sẽ diễn ra như sau:
>>   - Bước 1: Khi gán s1 = "javacore", JVM kiểm tra trong string pool. Nếu chưa có chuỗi "javacore" nào trong đó, JVM sẽ tạo một đối tượng String chứa "javacore" và gán cho s1.
>>   - Bước 2: Khi gán s2 = "javacore", JVM kiểm tra trong string pool. Nếu đã có chuỗi "javacore", JVM sẽ gán s2 trỏ đến chuỗi có sẵn mà không tạo mới.
>
> ### **2.2 Khởi tạo string bằng từ khoá new**
>> - Đây là cách tạo chuỗi bằng từ khóa new. Khi dùng new String("javacore"), JVM không kiểm tra trong string pool, mà luôn tạo một đối tượng mới trong bộ nhớ, ngay cả khi chuỗi đó đã tồn tại.
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s1 = new String("javacore");
>>          String s2 = new String("javacore");
>>       }
>>   }
>>   ```
>> - Với đoạn code trên, JVM sẽ tạo ra hai đối tượng String riêng biệt, hoàn toàn độc lập và không liên quan gì đến nhau.
>
> ### **2.3 String là object immutable**
>> - Như đã đề cập ở trên một object immutable (bất biến) không thể thay đổi giá trị bên trong sau khi đã được tạo.
>>
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "java core";
>>          s.charAt(0) = 'a';
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   Chương trình báo lỗi ở dòng s.charAt(0) = 'a';
>>   ```
>>   
>> - Chúng ta cùng xem ví dụ sau:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String str = "Hello";
>>          System.out.println(str);
>>          str = "Goodbye"
>>          System.out.println(str);
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   Hello
>>   Goodbye
>>   ```
>> - Sao nói rằng object string không thể thay đổi sau khi nó đã được khởi tạo thì đáng lẽ chúng ra phải nhận output là hello chứ nhỉ!
>> - Thật ra là khi bạn gán str = "Hello" trình biên dịch sẽ tiến hành khởi tạo object string và gán cho str. Đến khi bạn lại gán str = "Goodbye" như đúng bản chất nó không thay đổi giá trị object "Hello" mà nó sẽ tạo tạo một object mới với giá trị chuỗi là "Goodbye" và gán lại cho str. Đó là lý do chúng ta có output như trên.

## **3. Nhập xuất String**
> - Để nhập xâu kí tự ta sử dụng hàm nextLine(), hàm này sẽ đọc tới khi gặp kí tự xuống dòng.
>
> - Ví dụ:
>    ```java
>    public class Main {
>       public static void main(String[] args) {
>           Scanner sc = new Scanner("System.in");
>           String s = sc.nextLine();
>           System.out.println(s);
>       }
>   }
>   ```
>   input:
>   ```
>   learn java core
>   ```
>   Output:
>   ```
>   learn java core
>   ```
> 
> - Khi dùng nextLine(), bản chất cách hoạt động của nextLine() sẽ dừng nhập tới khi gặp dấu xuống dòng, vì thế hãy đảm bảo trước khi nhập nextLine(), trong bộ đệm bàn phím không còn thừa dấu enter do các hàm như nextInt(), nextLong()… để lại từ câu lệnh nhập trước
> - Tình huống xảy ra trôi lệnh:
>   ```java
>   public static void main(String[] args) {
>       Scanner sc = new Scanner("System.in");
>       int n = sc.nextInt();
>       String s = sc.nextLine();
>       System.out.println(s);
>   }
>   ```
>   input:
>   ```
>   8386
>   java
>   ```
>   Output:
>   ```
>   8386
>   
>   ```
>   Output chỉ in ra số 8386 mà không in chuỗi "java" vì sau khi nhập n từ bàn phím và nhấn Enter, lệnh sc.nextLine() ngay bên dưới sẽ đọc luôn ký tự Enter đó, khiến nó kết thúc việc nhập mà không chờ người dùng nhập chuỗi tiếp theo.
>    
> - Cách xử lý: Hãy nhớ rằng không phải cứ trước nextLine() là bạn cần xóa bộ đệm, bao giờ trước nextLine() mà có câu lệnh khác nextLine() như nextInt(), nextLong().. thì mới cần phải xóa bộ đệm. Các bạn xóa đi phím enter trong bộ đệm bằng câu lệnh nextLine().
> - Xử lí trôi lệnh:
>    ```java
>    public class Main {
>       public static void main(String[] args) {
>          Scanner sc = new Scanner("System.in");
>          int n = sc.nextInt();
>          sc.nextLine(); // Đọc phím enter thừa
>          String s = sc.nextLine();
>          System.out.println(s);
>       }
>    }
>   ```
>   input:
>   ```
>   8386
>   java
>   ```
>   Output:
>   ```
>   8386
>   

---
## **3. Các phương thức xử lý chuỗi trong Java**
> - Chú ý: String trong Java một khi đã khai báo bạn không thể thay đổi nó, vì thế các hàm của String đều trả về 1 xâu kí tự mới sau khi áp dụng các hàm
> ### **3.1 lenght()**
>> - Dùng để lấy độ dài của chuỗi (Trả về số kí tự trong xâu)
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "Hoc lap trinh Java";
>>          System.out.println(s.length());
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   18
>>   ```
>   
> ### **3.2 charAt()**
>> - String tương tự như mảng, chỉ số bắt đầu từ 0, hàm charAt(index) trả về kí tự ở chỉ số index (Lấy ký tự tại vị trí index của chuỗi)
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "JavaCore";
>>          for (int i = 0; i < s.length(); i++) {
>>             System.out.print(s.charAt(i) + " ");
>>          }
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   J a v a C o r e
>>   ```
>
> ### **3.3 Các hàm kiểm tra và chuyển đổi kí tự**
>> - Hàm kiểm tra kí tự:
>>   - Character.isLowerCase(char c): Kiểm tra xem ký tự có phải chữ thường không.
>>   - Character.isUpperCase(char c): Kiểm tra xem ký tự có phải chữ hoa không.
>>   - Character.isDigit(char c): Kiểm tra xem ký tự có phải số không.
>>   - Character.isAlphabetic(char c): Kiểm tra xem có phải ký tự chữ cái không.
>>   - Character.isWhitespace(char c): Kiểm tra xem có phải khoảng trắng không.
>> 
>> - Hàm chuyển đổi ký tự:
>>   - Character.toLowerCase(char c): Chuyển ký tự thành chữ thường.
>>   - Character.toUpperCase(char c): Chuyển ký tự thành chữ hoa.
>>
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          char ch1 = 'A';
>>          char ch2 = 'a';
>>          char ch3 = '5';
>>          char ch4 = ' ';
>>          char ch5 = '$';
>>          
>>          // Kiểm tra ký tự
>>          System.out.println("isLowerCase('A'): " + Character.isLowerCase(ch1)); // false
>>          System.out.println("isLowerCase('a'): " + Character.isLowerCase(ch2)); // true
>>          System.out.println("isUpperCase('A'): " + Character.isUpperCase(ch1)); // true
>>          System.out.println("isDigit('5'): " + Character.isDigit(ch3)); // true
>>          System.out.println("isAlphabetic('A'): " + Character.isAlphabetic(ch1)); // true
>>          System.out.println("isAlphabetic('5'): " + Character.isAlphabetic(ch3)); // false
>>          System.out.println("isWhitespace(' '): " + Character.isWhitespace(ch4)); // true
>>          System.out.println("isLetter('$'): " + Character.isLetter(ch5)); // false
>>          
>>          // Chuyển đổi ký tự
>>          System.out.println("toLowerCase('A'): " + Character.toLowerCase(ch1)); // a
>>          System.out.println("toUpperCase('a'): " + Character.toUpperCase(ch2)); // A
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   isLowerCase('A'): false
>>   isLowerCase('a'): true
>>   isUpperCase('A'): true
>>   isDigit('5'): true
>>   isAlphabetic('A'): true
>>   isAlphabetic('5'): false
>>   isWhitespace(' '): true
>>   isLetter('$'): false
>>   toLowerCase('A'): a
>>   toUpperCase('a'): A
>>   ```
>
> ### **3.4 toUpperCase()**
>> - Trả về xâu ở dạng in hoa, hàm này không thay đổi xâu ban đầu
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "java core";
>>          String t = s.toUpperCase();
>>          System.out.println(s);
>>          System.out.println(t);
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   java core
>>   JAVA CORE
>>   ```
>
> ### **3.5 toLowerCase()**
>> - Trả về xâu ở dạng in thường, hàm này không thay đổi xâu ban đầu
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "JAVA CORE";
>>          String t = s.toLowerCase();
>>          System.out.println(s);
>>          System.out.println(t);
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   JAVA CORE
>>   java core
>>   ```
>
> ### **3.6 concat()**
>> - nối xâu kí tự khác vào cuối xâu hiện tại, bạn có thể sử dụng toán tử + để làm chức năng tương tự
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "java ";
>>          String t = "colection ";
>>          String st = s.concat(t);
>>          String ts = t + s;
>>          System.out.println(st);
>>          System.out.println(ts);
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   java colection
>>   colection java
>>   ```
>
> ### **3.7 compareTo()**
>> - So sánh 2 xâu theo thứ tự từ điển, nếu 2 xâu bằng nhau trả về 0, trả về số âm nếu xâu hiện tại nhỏ hơn xâu cần so sánh, ngược lại trả về số dương.
>>   
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "java core";
>>          String t = "java CORE";
>>          System.out.println(s.compareTo(t));
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   32
>>   ```
>
> ### **3.8 compareToIgnoreCase()**
>> - Bỏ qua in hoa in thường khi so sánh.
>> 
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>       public static void main(String[] args) {
>>          String s = "java core";
>>          String t = "java CORE";
>>          System.out.println(s.compareToIgnoreCase(t));
>>       }
>>   }
>>   ```
>>   Output:
>>   ```
>>   0
>>   ```
>
> ### **3.9 substring() & subSequence()**
>> - Dùng để cắt ra một chuỗi con từ begin_index đến end_index - 1 (nếu có 2 tham số truyền vào), cắt ra một chuỗi con từ begin_index đến hết chuối (nếu có 1 tham số truyền vào)
>> 
>> - Ví dụ:
>>   ```java
>>   public class Main {
>>    public static void main(String[] args) {
>>      String s = "java 28tech";
>>      System.out.println(s.substring(5));
>>      System.out.println(s.substring(5, 7));
>>      System.out.println(s.subSequence(5, 7));
>>    }
>>   }
>>   ```
>>   Output:
>>   ```
>>   28tech
>>   28
>>   28
>>   ```
>>   - substring(5, 7) trả về một String.
>>   - subSequence(5, 7) trả về một CharSequence (là một interface, String cũng là một kiểu CharSequence).
>>   - Tuy nhiên, vì String cũng là một CharSequence, nên khi in ra màn hình, cả hai đều hiển thị cùng một kết quả.
>

---
## **4. Tách từ trong chuỗi: split & StringTokenizer**
> ### **3.1. Dùng `split()`**
>> ```java
>> String s = "java   28tech  C++   28tech.com.vn";
>> String[] arr = s.split("\\s+"); // Tách chuỗi theo khoảng trắng
>> ```
>>
> ### **3.2. Dùng `StringTokenizer`**
>> ```java
>> import java.util.StringTokenizer;
>>
>> String s = "  nguyen,van...nam?di  ! hoc lap trinh";
>> StringTokenizer st = new StringTokenizer(s, ",.!?");
>>
>> while(st.hasMoreTokens()) {
>>     System.out.println(st.nextToken());
>> }
>> ```

---
## **4. Lớp `StringBuilder` - Chuỗi có thể thay đổi**
> Trong Java, `String` là bất biến, nhưng `StringBuilder` có thể thay đổi giá trị.
>
> Ví dụ:
> ```java
> String s = "28tech hoc lap trinh";
> StringBuilder builder = new StringBuilder(s);
> builder.setCharAt(3, '@');
> System.out.println(builder.toString());  // Kết quả: 28t@ch hoc lap trinh
> ```

---
## **5. Chuyển đổi giữa số và chuỗi**
> ### **5.1. Số thành chuỗi**
>> ```java
>> int n = 83868386;
>> String s = "" + n;  // Hoặc dùng String.valueOf(n);
>> ```
>>
> ### **5.2. Chuỗi thành số**
>> ```java
>> String s = "12345678";
>> int n = Integer.parseInt(s);
>> ```

---
## **6. Xử lý số nguyên lớn với `BigInteger`**
> Khi làm việc với số quá lớn không thể lưu trữ trong kiểu `int` hoặc `long`, ta dùng `BigInteger`.
>
> ```java
> import java.math.BigInteger;
>
> String s1 = "18238128381283812381123123123123";
> String s2 = "192399239192393";
>
> BigInteger num1 = new BigInteger(s1);
> BigInteger num2 = new BigInteger(s2);
>
> System.out.println(num1.add(num2));      // Cộng
> System.out.println(num1.subtract(num2)); // Trừ
> System.out.println(num1.multiply(num2)); // Nhân
> System.out.println(num1.divide(num2));   // Chia
> ```

---
### **Kết luận**
- `String` là bất biến, không thể thay đổi sau khi tạo.
- Dùng `StringBuilder` nếu cần thao tác thay đổi nội dung chuỗi.
- Java cung cấp nhiều phương thức mạnh mẽ để xử lý chuỗi như tìm kiếm, cắt, nối, kiểm tra ký tự, chuyển đổi số và chuỗi.
- Khi làm việc với số lớn, `BigInteger` là giải pháp tối ưu.

🚀 Hãy thực hành ngay để làm chủ các thao tác với chuỗi trong Java!
