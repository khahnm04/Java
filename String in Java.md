# **String trong Java**

## **1. Giới thiệu về lớp String trong Java**
> - String là lớp để xử lý xâu kí tự trong ngôn ngữ lập trình Java. Các bạn có thể nghĩ String như một mảng kí tự nhưng có thể mở rộng, thu hẹp và hỗ trợ rất nhiều hàm xử lý xâu thông dụng.
>   
> - Trong Java, String là một trong những kiểu dữ liệu quan trọng nhất. Nó đại diện cho một chuỗi ký tự bất biến có nghĩa là một khi String đã được tạo, nó không thể thay đổi.
>   
> - Một số đặc điểm của String:
>   - Immutable: Khi một String được tạo, nó không thể bị thay đổi.
>   - String Pool: Java tối ưu hóa bộ nhớ bằng cách lưu trữ các chuỗi giống nhau trong một vùng nhớ đặc biệt gọi là String Pool.
>   - Hỗ trợ Unicode: Java hỗ trợ đầy đủ Unicode, cho phép lưu trữ các ký tự từ nhiều ngôn ngữ khác nhau.
>
> - Khai báo String
>   ```java
>   String name_string;
>   ```
>
> - Ví dụ
>   ```java
>   public class Main {
>     public static void main(String[] args) {
>     String s = "28tech java";
>     System.out.println(s);
>   }
>   ```
> - Có 2 cách khởi tạo (Initialization) trong Java
>   - Using Double Quotes
>     ```java
>     String s1 = "Hello";
>     ```
>     Chuỗi này sẽ được lưu trong __String Pool__.
>     
>   - Using new
>     ```java
>     String s2 = new String("Hello");
>     ```
>     Chuỗi này sẽ được lưu trong __heap memory__ thay vì String Pool.

## **2. Nhập xuất String**
> - Để nhập xâu kí tự ta sử dụng hàm nextLine(), hàm này sẽ đọc tới khi gặp kí tự xuống dòng.
>
> - Ví dụ:
>   ```java
>   public class Main {
>     public static void main(String[] args) {
>       Scanner sc = new Scanner("System.in");
>       String s = sc.nextLine();
>       System.out.println(s);
>     }
>   }
>   ```
> - Khi dùng nextLine(), bản chất cách hoạt động của nextLine() sẽ dừng nhập tới khi gặp dấu xuống dòng, vì thế hãy đảm bảo trước khi nhập nextLine(), trong bộ đệm bàn phím không còn thừa dấu enter do các hàm như nextInt(), nextLong()… để lại từ câu lệnh nhập trước
> - Tình huống xảy ra trôi lệnh:
>   ```java
>   public static void main(String[] args) {
>     Scanner sc = new Scanner("System.in");
>     int n = sc.nextInt();
>     String s = sc.nextLine();
>     System.out.println(s);
>   }
>   ```
>   Output:
>   ```
>   Rỗng
>   ```
>    
> - Cách xử lý: Hãy nhớ rằng không phải cứ trước nextLine() là bạn cần xóa bộ đệm, bao giờ trước nextLine() mà có câu lệnh khác nextLine() như nextInt(), nextLong().. thì mới cần phải xóa bộ đệm. Các bạn xóa đi phím enter trong bộ đệm bằng câu lệnh nextLine().
> - Xử lí trôi lệnh:
>   ```java
>   public static void main(String[] args) {
>     Scanner sc = new Scanner("System.in");
>     int n = sc.nextInt();
>     sc.nextLine(); // Đọc phím enter thừa
>     String s = sc.nextLine();
>     System.out.println(s);
>   }
>   ```

---
## **3. Các phương thức xử lý chuỗi trong Java**
> - Chú ý: String trong Java một khi đã khai báo bạn không thể thay đổi nó, vì thế các hàm của String đều trả về 1 xâu kí tự mới sau khi áp dụng các hàm
> ### **lenght()**
>> Dùng để lấy độ dài của chuỗi (Trả về số kí tự trong xâu)
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        String s = "Hoc lap trinh Java";
>>        System.out.println(s.length());
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  18
>>  ```
>   
> ### **charAt()**
>> String tương tự như mảng, chỉ số bắt đầu từ 0, hàm charAt(index) trả về kí tự ở chỉ số index (Lấy ký tự tại vị trí index của chuỗi)
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        String s = "Hoc lap trinh Java";
>>        for (int i = 0; i < s.length(); i++) {
>>          System.out.print(s.charAt(i) + " ");
>>        }
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  2 8 t e c h  j a v a
>>  ```
>
> ### **Character.isLowerCase(char c)**
>>  Kiểm tra xem ký tự c có phải là chữ in thường hay không.
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        char c1 = 'a';
>>        char c2 = 'A';
>>        System.out.println(Character.isLowerCase(c1));
>>        System.out.println(Character.isLowerCase(c2));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  true
>>  false
>>  ```
>
> ### **Character.isUpperCase(char c)**
>>  Kiểm tra xem ký tự c có phải là chữ in hoa hay không.
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        char c1 = 'a';
>>        char c2 = 'A';
>>        System.out.println(Character.isUpperCase(c1));
>>        System.out.println(Character.isUpperCase(c2));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  false
>>  true
>>  ```
>
> ### **Character.isAlphabetic(char c)**
>>  Kiểm tra xem ký tự c có phải là chữ cái hay không.
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        char c1 = '@';
>>        char c2 = 'a';
>>        System.out.println(Character.isAlphabetic(c1));
>>        System.out.println(Character.isAlphabetic(c2));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  false
>>  true
>>  ```
>
> ### **Character.isDigit(char c)**
>>  Kiểm tra xem ký tự c có phải là chữ số hay không.
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>        char c1 = '1';
>>        char c2 = 'a';
>>        System.out.println(Character.isDigit(c1));
>>        System.out.println(Character.isDigit(c2));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  true
>>  false
>>  ```
>
> ### **Character.toLowerCase(char c)**
>>  Chuyển ký tự c thành chữ in thường (nếu nó là chữ in hoa), còn nếu c đã là chữ in thường hoặc không phải chữ cái thì giữ nguyên.
>>  ```java
>>  public class Main {
>>     public static void main(String[] args) {
>>         char c1 = 'A';
>>         char c2 = 'b';
>>         char c3 = '1';
>>         System.out.println(Character.toLowerCase(c1));
>>         System.out.println(Character.toLowerCase(c2));
>>         System.out.println(Character.toLowerCase(c3));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  a
>>  b
>>  1
>>  ```
>
> ### **Character.toUpperCase(char c)**
>>  Chuyển ký tự c thành chữ in hoa (nếu nó là chữ in thường), còn nếu c đã là chữ in hoa hoặc không phải chữ cái thì giữ nguyên.
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>         char c1 = 'a';
>>         char c2 = 'B';
>>         char c3 = '1';
>>         System.out.println(Character.toUpperCase(c1));
>>         System.out.println(Character.toUpperCase(c2));
>>         System.out.println(Character.toUpperCase(c3));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  A
>>  B
>>  1
>>  ```
>
> ### **toUpperCase()**
>>  Trả về xâu ở dạng in hoa, hàm này không thay đổi xâu ban đầu
>>  ```java
>>  public class Main {
>>     public static void main(String[] args) {
>>         String s = "java core";
>>         String t = s.toUpperCase();
>>         System.out.println(s);
>>         System.out.println(t);
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  java core
>>  JAVA CORE
>>  ```
>
> ### **toLowerCase()**
>>  Trả về xâu ở dạng in thường, hàm này không thay đổi xâu ban đầu
>>  ```java
>>  public class Main {
>>     public static void main(String[] args) {
>>         String s = "JAVA CORE";
>>         String t = s.toLowerCase();
>>         System.out.println(s);
>>         System.out.println(t);
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  JAVA CORE
>>  java core
>>  ```
>
> ### **concat()**
>>  nối xâu kí tự khác vào cuối xâu hiện tại, bạn có thể sử dụng toán tử + để làm chức năng tương tự
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>      String s = "java ";
>>      String t = "colection ";
>>      String st = s.concat(t);
>>      String ts = t + s;
>>      System.out.println(st);
>>      System.out.println(ts);
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  java colection
>>  colection java
>>  ```
>
>> ### **compareTo()**
>>  So sánh 2 xâu theo thứ tự từ điển, nếu 2 xâu bằng nhau trả về 0, trả về số âm nếu xâu hiện tại nhỏ hơn xâu cần so sánh, ngược lại trả về số dương.
>>  ```java
>> public class Main {
>>   public static void main(String[] args) {
>>     String s = "java core";
>>     String t = "java CORE";
>>     System.out.println(s.compareTo(t));
>>   }
>> }
>>  ```
>>  Output:
>>  ```
>>  32
>>  ```
>
>> ### **compareToIgnoreCase()**
>>  Bỏ qua in hoa in thường khi so sánh.
>>  ```java
>> public class Main {
>>   public static void main(String[] args) {
>>     String s = "java core";
>>     String t = "java CORE";
>>     System.out.println(s.compareToIgnoreCase(t));
>>   }
>> }
>>  ```
>>  Output:
>>  ```
>>  0
>>  ```
>
>> ### **substring() & subSequence()**
>>  Dùng để cắt một chuỗi con từ begin_index đến end_index - 1 (nếu có 2 tham số truyền vào), cắt một chuỗi con từ begin_index đến hết chuối (nếu có 1 tham số truyền vào)
>>  ```java
>>  public class Main {
>>    public static void main(String[] args) {
>>      String s = "java 28tech";
>>      System.out.println(s.substring(5));
>>      System.out.println(s.substring(5, 7));
>>      System.out.println(s.subSequence(5, 7));
>>    }
>>  }
>>  ```
>>  Output:
>>  ```
>>  28tech
>>  28
>>  28
>>  ```
>>  - substring(5, 7) trả về một String.
>>  - subSequence(5, 7) trả về một CharSequence (là một interface, String cũng là một kiểu CharSequence).
>>  - Tuy nhiên, vì String cũng là một CharSequence, nên khi in ra màn hình, cả hai đều hiển thị cùng một kết quả.
>

---
## **3. Tách từ trong chuỗi: split & StringTokenizer**
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
