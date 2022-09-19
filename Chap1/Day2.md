# Simple Java Program - Comment - Datatype

## Mục Lục Nội Dung

  - [1. Simple java program](#1-simple-java-program)
  - [2. Comment](#2-comment)
  - [3. Datatype](#3-datatype)
    - [3.1 Primitive](#31-primitive)
      - [3.1.1 Integer](#311-integer)
        - [3.1.1.1 Byte](#3111-byte)
        - [3.1.1.2 Short](#3112-short)
        - [3.1.1.3 Int](#3113-int)
        - [3.1.1.4 Long](#3114-long)
      - [3.1.2 Floating point](#312-floating-point)
      - [3.1.3 Character](#313-character)
      - [3.1.4 Boolean](#314-boolean)
    - [3.2 Reference](#32-reference)
    - [3.3 Sự khác nhau giữa primitive và reference](#33-sự-khác-nhau-giữa-primitive-và-reference)

## 1. Simple java program

```java
package com.edu.demo
public class DemoJavaProgram {
/*
 * public static void main(String... args) { cũng hợp lệ
 * static public void main(String[] args) cũng hợp lệ
 */
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

- Java thì **case sensitive** ==> phân biệt chữ hoa chữ thường
- **`public`** là access modifier
- Mọi thứ trong chương trình java đều phải nằm trong **`class`**
- Không thể **đảo thứ tự** **`public`** với **`class`**
- Phương thức **`main`** để thực thi chương trình
- **`System.out.println`** ==> gọi method **`println`** của object **`System.out`** và in ra màn hình console

## 2. Comment

- **`\\`** comment với nội dung ngắn và chỉ trên 1 dòng.
- **`/* */`** comment khối với nội dung mô tả nhiều.
- **`/** */`** comment dành cho document (thường là document API)

Quy tắc khi comment

- Rule 1: comment không trùng với code
- Rule 2: comment phải giải thích code đang làm gì
- Rule 3: comment đường dẫn copy code trên mạng
- Rule 4: comment sau khi fix bug lại

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 3. Datatype

- Chia làm 2 loại là **primitive và reference**

### 3.1 Primitive

- Còn gọi là **kiểu dữ liệu nguyên thuỷ**
- Có 8 primitive data types chia thành các loại **Integer, floating-point, character, boolean**
- **Signed - có dấu** chứa 1 nửa âm nửa dương, **Unsigned - không dấu** chỉ chứa dương
- Java chỉ hổ trợ **Signed** trừ **`char`** có **Unsigned**

![alt text](/assets/day-02-primitive-data-type.jpg)

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

#### 3.1.1 Integer

- Số nguyên có 4 loại: **`byte, short, int, long`**
  - **`int`** thường dùng nhất
  - **`long`** dùng trong dân số thế giới, đường kính hành tinh,...
  - **`byte, short`** dùng trong file
- Có 3 cách lưu trữ Integer: **decimal(10), octal(8), hexadecimal(16)**

```java
int decimal = 12;
int octal = 012;
int hexa = 0xDeadCafe;
// hexa ko phân biệt hoa thường
```

> Trong C/C++ thì size của **int và long phụ thuộc vào nền tảng**, nếu trên máy 16 bit thì nó sẽ có 2 byte và máy 32 bit thì sẽ có 4 byte nhưng trong java thì **không phụ thuộc**, thằng nào cũng như nhau

##### Max và Min

```java
int myMinIntValue = Integer.MIN_VALUE;
int myMaxIntValue = Integer.MAX_VALUE;
// do nó vượt quá miền sẽ quay đầu lại
System.out.println(myMinIntValue - 1); // == myMaxIntValue
System.out.println(myMaxIntValue + 1); // == myMinIntValue

long myMinlongValue = Long.MIN_VALUE;
long myMaxlongValue = Long.MAX_VALUE;

byte myMinByteValue = Byte.MIN_VALUE;
byte myMaxByteValue = Byte.MAX_VALUE;

short myMinShortValue = Short.MIN_VALUE;
short myMaxShortValue = Short.MAX_VALUE;
```

> Nếu **max + 1** và **min - 1** ở trường hợp int và long sẽ **đổi miền** còn byte với short thì sẽ tự động ép sang kiểu int nên không vượt quá miền do ép sang kiểu int

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

##### 3.1.1.1 Byte 

- 1 ký tự biểu diễn 1 byte
- Tiết kiệm bộ nhớ trong array lớn
- Đọc stream của bit
- Đọc file 

##### 3.1.1.2 Short 

- Tiết kiệm bộ nhớ trong array lớn

##### 3.1.1.3 Int 

- Từ **Java 8** trở lên có thể sử dụng Unsigned **0** => **2^32^-1**

##### 3.1.1.4 Long 

- Từ **Java 8** trở lên có thể sử dụng Unsigned **0** => **2^64^-1**
- Từ **java 7** ta có thể sử dụng **`_`** cho phân tách con số cho dễ nhìn nhưng lưu ý
  - Không thể sử dụng **`_`** ở đầu hoặc ở cuối, ở cạnh **`.`**, cạnh **`L,f`** và cạnh **`0x`**
- Vd **`long value = 3_000_000_000L;`**

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

#### 3.1.2 Floating point

- Dấu phẩy động có 2 loại: **`float, double`**
- 3 giá trị đặc biệt **`positive infinity, negative infinity, NaN`** với **`NaN`** không phải là **1 số**

```java
float a = 3.5F; // bắt buộc phải có f hoặc F
```

> Không thích hợp trong tính toán tài chính vì nó không làm tròn. Vd 2.0 - 1.1 ra 0.8999999... chứ không phải là 0.9 muốn chính xác thì dùng **BigDecimal**

#### 3.1.3 Character

- Ký tự có 1 loại: **`char`**
- Mô tả đơn vị trong **bảng mã UTF-16**
- Các escape thường dùng
  - **`\b`** ==> backspace
  - **`\t`** ==> tab
  - **`\n`** ==> linefeed
  - **`\r`** ==> carriage return
  - **`\"`** ==> double quote
  - **`\'`** ==> single quote
  - **`\\`** ==> backslash

#### 3.1.4 Boolean

- Boolean có 1 loại: **`boolean`**

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.2 Reference

- Còn gọi là **non-primitive**, kiểu dữ liệu tham chiếu
- Array, String, Interface, Class, Anotation, Enumeration

### 3.3 Sự khác nhau giữa primitive và reference

| Primitive                             | Reference                                 |
| ------------------------------------- | ----------------------------------------- |
| Lưu trực tiếp giá trị                 | Lưu địa chỉ bộ nhớ của giá trị            |
| Đã được định nghĩa trước              | Phải tạo trước trừ String                 |
| Luôn gán giá trị                      | Không cần gán giá trị vì mặc định là null |
| Kích thước phụ thuộc vào kiểu dữ liệu | Có cùng kích thước                        |
| Không có method                       | Có thể viết method riêng                  |

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [White Paper - Kiến Trúc - Các Nền Tảng](/Chap1/Day1.md)
- [Naming Convention - Variable - Constant](/Chap1/Day3.md)
