# DAY 1: Simple Java Program - Comment - Datatype

## Mục Lục Nội Dung

- [DAY 1: Simple Java Program - Comment - Datatype](#day-1-simple-java-program---comment---datatype)
  - [Mục Lục Nội Dung](#mục-lục-nội-dung)
  - [1. Simple java program](#1-simple-java-program)
  - [2. Comment](#2-comment)
  - [3. Datatype](#3-datatype)
    - [3.1 Primitive](#31-primitive)
      - [3.1.1 Integer](#311-integer)
      - [3.1.2 Floating point](#312-floating-point)
      - [3.1.3 Character](#313-character)
      - [3.1.4 Boolean](#314-boolean)
    - [3.2 Reference](#32-reference)
    - [3.3 Sự khác nhau giữa primitive và reference](#33-sự-khác-nhau-giữa-primitive-và-reference)

## 1. Simple java program

```java
package com.edu.demo
public class DemoJavaProgram {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

- Java rất phân biệt rõ ràng chữ hoa và chữ thường **- case sensitive**
- `public` là access modifier
- Mọi thứ trong chương trình java đều phải nằm trong `class`
- Không thể **đảo thứ tự** `public` với `class`
- Phương thức `main` để thực thi chương trình
- `System.out.println` ==> gọi method `println` của object `System.out` và in ra màn hình console

## 2. Comment

- `\\` comment với nội dung ngắn và chỉ trên 1 dòng.
- `/* */` comment khối với nội dung mô tả nhiều.
- `/** */` comment dành cho document (thường là document API)

Quy tắc khi comment

- Rule 1: comment không trùng với code
- Rule 2: comment phải giải thích code đang làm gì
- Rule 3: comment đường dẫn copy code trên mạng
- Rule 4: comment sau khi fix bug lại

## 3. Datatype

- Chia làm 2 loại là **primitive và reference**

### 3.1 Primitive

- Còn gọi là **kiểu dữ liệu nguyên thuỷ**
- Có 8 primitive data types chia thành các loại **Integer, floating-point, character, boolean**
- **Signed - có dấu** chứa 1 nửa âm nửa dương, **Unsigned - không dấu** chỉ chứa dương
- Java chỉ hổ trợ **Signed** trừ `char` có **Unsigned**

![alt text](/assets/day-02-primitive-data-type.jpg)

#### 3.1.1 Integer

- Số nguyên có 4 loại: `byte, short, int, long`
  - `int` thường dùng nhất
  - `long` dùng trong dân số thế giới, đường kính hành tinh,...
  - `byte, short` dùng trong file

> Trong C/C++ thì size của **int và long phụ thuộc vào nền tảng**, nếu trên máy 16 bit thì nó sẽ có 2 byte và máy 32 bit thì sẽ có 4 byte nhưng trong java thì **không phụ thuộc**, thằng nào cũng như nhau

#### 3.1.2 Floating point

- Dấu phẩy động có 2 loại: `float, double`
- 3 giá trị đặc biệt `positive infinity, negative infinity, NaN` với `NaN` không phải là **1 số**

> Không thích hợp trong tính toán tài chính vì nó không làm tròn. Vd 2.0 - 1.1 ra 0.8999999... chứ không phải là 0.9 muốn chính xác thì dùng **BigDecimal**

#### 3.1.3 Character

- Ký tự có 1 loại: `char`
- Mô tả đơn vị trong **bảng mã UTF-16**
- Các escape thường dùng
  - `\b` ==> backspace
  - `\t` ==> tab
  - `\n` ==> linefeed
  - `\r` ==> carriage return
  - `\"` ==> double quote
  - `\'` ==> single quote
  - `\\` ==> backslash

#### 3.1.4 Boolean

- Boolean có 1 loại: `boolean`

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


