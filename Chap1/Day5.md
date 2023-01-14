# String - Character

## Mục lục nội dung

- [1. String là gì](#1-string-là-gì)
- [2. Syntax](#2-syntax)
- [3. Method](#3-method)
  - [3.1 length()](#31-length)
  - [3.2 charAt()](#32-charat)
  - [3.3 substring()](#33-substring)
  - [3.4 Nối chuỗi](#34-nối-chuỗi)
  - [3.5 indexOf()](#35-indexof)
  - [3.6 lastIndexOf()](#36-lastindexof)
  - [3.7 equals()](#37-equals)
  - [3.8 equals() và == trong String](#38-equals-và--trong-string)
  - [3.9 compareTo()](#39-compareto)
  - [3.10 toLowerCase() và toUpperCase()](#310-tolowercase-và-touppercase)
  - [3.11 trim()](#311-trim)
  - [3.12 replace()](#312-replace)
  - [3.13 startsWith() và endsWith()](#313-startswith-và-endswith)
  - [3.14 contains()](#314-contains)
  - [3.15 Ký tự đặc biệt và enscape](#315-ký-tự-đặc-biệt-và-enscape)
  - [3.16 Ép kiểu](#316-ép-kiểu)
  - [3.17 Split](#317-split)
  - [3.18 Gán String vào char](#318-gán-string-vào-char)
  - [3.19 intern()](#319-intern)
  - [3.20 join()](#320-join)
  - [3.21 repeat()](#321-repeat)
  - [3.22 Empty và null](#322-empty-và-null)
 - [4. Character](#4-character) 

## 1. String là gì

- Là một array chứa các ký tự **không thể thay đổi - immutable** khi tạo. 
- Ký tự sẽ bao gồm cả **khoảng trắng** và index bắt đầu như 1 array là 0.
- Luôn bắt đầu và kết thúc **`""`** ở phía trước và phía sau **`String`** được tạo.

> Khi **String** được gán = **null**, lúc này các thao tác với method dành cho **String** sẽ gây ra lỗi **runtime**.

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 2. Syntax

```java 
String x = null; // trỏ vào vùng null
String x = new String(null); // compile

// tạo vùng object trong string
String x = ""; // chuỗi rỗng
String literal = "Hello"; // literal, POOL
String x = new String(); // chuỗi rỗng
String newKeyword = new String("hello");
```

> Khi ta không muốn lưu giá trị gì cả nên trỏ String về null

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 3. Method 

### 3.1 length()

Trả về đô dài của String.

```java
String str = "thong thai";
System.out.println(str.length()); // 10
```

### 3.2 charAt()

Trả về ký tự theo index chỉ định.

```java
String str = "thong thai";
System.out.println(str.charAt(3)); // n
```

### 3.3 substring()

Trả về chuỗi con chỉ định.

```java
String str = "thong thai";

// c1 trả về substring từ vị trí chỉ định đến hết
System.out.println(str.substring(2)); // ong thai

// c2 trả về substring từ vị trí chỉ định đến nhỏ hơn vị trí kết thúc
System.out.println(str.substring(2,9)); // ong tha
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.4 Nối chuỗi

Trả về chuỗi sau khi nối, ta có 2 cách nối.

```java
String firstName = "John";
String lastName = "Doe";
int age = 22;
int dob = 2000;

// không phân biệt kiểu sẽ tự ép qua string
System.out.println(firstName + age + dob); // John 222000 
System.out.println(age + dob + firstName); // 2022John

// concat chỉ sử dụng khi 2 thằng cùng kiểu String
firstName.concat(lastName); // JohnDoe
```

### 3.5 indexOf()

Trả về index của text được chỉ định **xuất hiện gần nhất**, bắt đầu từ 0 và không có thì trả về -1.

```java
String str = "long thien thang thai";

System.out.println(str.indexOf("th")); // c1, return 5
// return string "th" bắt đầu tính từ vị trí 6 thay vì 0
System.out.println(str.indexOf("th",6)); // c2, return 13

// tương tự string nhưng áp dụng được cho cả char
System.out.println(str.indexOf('a')); // 13
System.out.println(str.indexOf('a',14)); // 19
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.6 lastIndexOf()

Trả về index của text được chỉ định **xuất hiện lần cuối cùng**, bắt đầu từ 0 và không có thì trả về -1.

```java
String str = "abcd dabe fabg";

System.out.println(str.indexOf("ab")); // c1, return 11
System.out.println(str.indexOf("ab", 6)); // c2, return 6

// áp dụng cho char
System.out.println(str.lastIndexOf('a')); // 11
System.out.println(str.lastIndexOf('a', 6)); // 6
```

### 3.7 equals()

Để so sánh ta có thể sử dụng **`equals`** trong **`String`**.

```java
String str1 = "hello";
String str2 = "hello";
System.out.println(str1.equals(str2)); // true
/*
 * trường hợp str1 ta nên dùng thẳng là "hello".equals(str2)
 * để tránh trường hợp nếu str1 là null sẽ gây lỗi
 */
```

> Ngoài ra ta có thể sử dụng **`equalsIgnoreCase()`** để khi so sánh không phân biệt chữ hoa hay chữ thường

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.8 equals() và == trong String

- **`==`** được sử dụng để so sánh tham chiếu (so sánh địa chỉ), kiếm tra xem cả 2 object có cùng trỏ đến cùng 1 vị trí bộ nhớ.
- **`equals()`** để so sánh nội dung bên trong của 2 object. 
> Khi String gán cho 1 chuỗi thì ta có thể so sánh với **==** nhưng khi sử dụng **subString** hoặc **+** thì lúc này không thể so sánh với 1 chuỗi "" bằng toán tử **==**

```java
String str1 = "HELLO";
String str2 = "HELLO";
String str3 =  new String("HELLO"); // refer tới bộ nhớ heap
String str4 = null;
String str5 = "";
String str6 = new String();
System.out.println(str1 == str2); // true
System.out.println(str1 == str3); // false
System.out.println(str4 == null); // true
System.out.println(str4 == ""); // false
System.out.println(str1.equals(str2)); // true
System.out.println(str1.equals(str3)); // true
System.out.println(str4.equals(null)); // exception
System.out.println(str1.equals(null)); // false
System.out.println(str4.equals("")); // exception
System.out.println(s5.equals(str6)); // true
str1 += "WORLD";
str2 += "WORLD";
System.out.println(str1 == str2); // false
// => thay đổi string literal dẫn đến không xác định được refer
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.9 compareTo() 

So sánh giữa 2 ký tự unicode.

```java
String str1 = "abc";
String str2 = new String("abc");
String str3 = "Abc";
String str4 = "ABc";
String str5 = "def";
        
// tính bằng cách lấy vị trí đầu tiên nếu khác nhau sẽ lấy chuỗi str1 - str2
System.out.println(str1.compareTo(str2)); // 0
System.out.println(str1.compareTo(str3)); // 32 (a-A === 97-65)
System.out.println(str1.compareTo(str4)); // 32
System.out.println(str1.compareTo(str5)); // -3
System.out.println(str1.compareTo(null)); // exception
```

> - Ngoài ra ta có thể sử dụng **compareToIgnoreCase()** để khi so sánh không phân biệt chữ hoa hay chữ thường
> - Nên sử dụng **equals()** trong so sánh giá trị, **compareTo()** trong sắp xếp và **==** trong reference.

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.10 toLowerCase() và toUpperCase()

In hoa hoặc in thường trong String.

```java
String txt = "Hello World";
System.out.println(txt.toUpperCase());   // Outputs "HELLO WORLD"
System.out.println(txt.toLowerCase());   // Outputs "hello world"
```

### 3.11 trim()

Xóa space ở cả 2 bên.

```java
String str = "  abc  ";
System.out.println(str); // abc có space
System.out.println(str.trim()); // xuất ra abc đã xóa space ở trước và sau
```

### 3.12 replace()

Trả về String sau khi được thay thế bởi 1 ký tự hoặc String được chỉ định.

```java
String str = "Hello";
System.out.println(str.replace('l', 'p')); // Heppo
System.out.println(str.replace("lo", "de")); // Helde
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.13 startsWith() và endsWith()

`startsWith()` kiểm tra xem có phải bắt đầu bằng String chỉ định không.

```java
String str = "John";
System.out.println(str.startsWith("jo")); // false

// String java luôn bắt đầu là "" ở phía trước mặc dù có trim
System.out.println(str.startsWith("")); // true

// kiểm tra vị trí bắt đầu nhưng tính từ vị trí chỉ định
System.out.println(str.startsWith("oh",1)); // true
```

`endsWith()` kiểm tra xem có phải kết thúc bằng String chỉ định không.

```java
String str = "John";
System.out.println(str.endsWith("hn")); // true

// String java luôn kết thúc là "" ở phía sau
System.out.println(str.endsWith("")); // true
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.14 contains()

Kiểm tra xem môt String có chứa một String khác không.

```java
String str = "Java";
System.out.println(str.contains("Java")); // true
System.out.println(str.contains("java")); // false
```

### 3.15 Ký tự đặc biệt và enscape

Ký tự đặc biệt thường sử dụng là `'`, `"` và `\`

```java
String txt = "We are the so-called \"Vikings\" from the north.";
String txt = "The character \\ is called backslash.";
String txt = "It\'s alright.";
```

**Enscape** thường sử dụng là `\n <=> new line`, `\t <=> tab`, `\b <=> backspace`, `\f <=> Formfeed`, `\r <=> Carriage Return`, `\' <=> '`, `\" <=> "`, `\\ <=> \`

```java
String str1 = "thong";
String str2 = "thai";
System.out.println(str1 + "\b"); // thon
System.out.println(str1 + "\n" + str2); // thong xong xuống dòng in thái
System.out.println(str1 + "\t" + str2); // thong  thai
// \f dùng cho ngắt trang
System.out.println("\t" + "\r" + str2); // thai (nhảy về đầu dòng)
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.16 Ép kiểu

```java
// nối String trong số hay còn gọi là ép kiểu
String firstName = "John";
int age = 5;
// john 55 vì age lúc này được ép sang string nên có cộng với 5 thì nó vẫn xem age là string
System.out.println(firstName + " " + age + 5); 

char[] c = s.toCharArray(); // convert string to char
String s = new String(c); // convert char to string or dung valueOf
int number = 12;
String convert = String.valueOf(number); //c1
String convert = "" + number; //c2
int reverse = Integer.parseInt(convert);
```

> khi convert sang String sử dụng valueOf và ngược lại thì dùng parse áp dụng với **primitive (trừ short và byte), object, array char, array**

### 3.17 Split

Tách 1 String thành 1 mảng các subString.

```java
String str = "01/02/03/04/05";
// lưu ý trường hợp này ứng với limit = 0;
String[] limit = str.split("/"); // [01,02,03,04,05]
limit = str.split("/",1); // [01/02/03/04/05]
limit = str.split("/",2); // [01,02/03/04/05]
limit = str.split("/",3); // [01,02,03/04/05]

// lưu ý để split nhiều ký hiệu nên để trong []
str = "1 + 2 - 3 + 4"
// lưu ý split sẽ tính luôn khoảng trắng là 1 ký tự vì sau ký tự split mới tính nên trước 2 3 4 sẽ có thêm khoảng trắng
limit = str.split("[+-]"); // [1, _2, _3, _4] 
```

> lưu ý **`\\s`** đại diện cho space nhưng trường hợp có nhiều space thì nó vẫn giữ lại nếu ta chỉ split 1 space, để giải quyết điều này thì sử dụng **`\\s+`** để split hết tất cả space.

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.18 Gán String vào char 

```java
String s = "helloscript";
char[] dst = {'j', 'a', 'v', 'a', '1', '3', '0', '1', '5', '6'};
s.getChars(5, 11, dst, 4); // lấy từ vị trí 5 đến 10 của String gán vào vị trí 4 của char
System.out.println(dst); // javascript
```

### 3.19 intern()

```java
String it1 = "intern";
String it2 = new String("intern").intern();
String it3 = new String("intern");
String it4 = "intern".intern();

System.out.println(it2==it1); // true
System.out.println(it2==it3); // false
System.out.println(it2==it4); // true
```

### 3.20 join()

```java
// S / M / L / XL
String all = String.join(" / ", "S", "M", "L", "XL");
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.21 repeat()

Áp dụng cho java 11 trở lên 

```java
String repeated = "Java".repeat(3); // JavaJavaJava
```

### 3.22 Empty và null

- Một chuỗi gọi là empty khi nó `str.equals("")` ra true hay `str.length()==0`
- Kiểm tra chuỗi không trống và khác null thì điều kiện khác null phải viết trước 
  - `if (str != null && str.length() != 0)`
  
## 4. Character 

```java
char letter = 'a', digit = '0';
System.out.println("character is letter ? " + Character.isLetter(letter));
System.out.println("character is digit ? " + Character.isDigit(digit));
System.out.println("character is letter or digit ? " + Character.isLetterOrDigit(digit));
System.out.println("character is space ? " + Character.isWhitespace(' '));
System.out.println("character is tab ? " + Character.isWhitespace('\t'));
System.out.println("character is new line ? " + Character.isWhitespace('\n'));
System.out.println("character is upperCase ? " + Character.isUpperCase(letter)+ " => convert lowerCase to upperCase " + Character.toUpperCase(letter));
System.out.println("character is lowerCase ? " + Character.isLowerCase(letter));
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [Operator - Math - Type Conversion](/Chap1/Day4.md)
- [Scanner Input - Format](/Chap1/Day6.md)

