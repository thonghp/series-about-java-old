# Day 2 Naming Convention - Variable - Constant

## Mục lục nội dung
  - [1. Naming convention](#1-naming-convention)
    - [1.1 Các trường hợp đặt tên](#11-các-trường-hợp-đặt-tên)
  - [2. Variable](#2-variable)
    - [2.1 Scope](#21-scope)
    - [2.2 Static variable](#22-static-variable)
    - [2.3 Instance variable](#23-instance-variable)
    - [2.4 Local variable](#24-local-variable)
    - [2.5 Parameter](#25-parameter)
  - [3. Constant](#3-constant)

## 1. Naming convention

- Thiên về kiểu **camel** 
- **Bắt đầu** bằng chữ thường, `$` hay `_` và **không nên bắt đầu** bằng number, ký hiệu khác. 
    - Nhưng **không nên dùng** các ký hiệu `$` và `_` để đặt đầu tiên.
- **Không sử dụng** java keyword để đặt tên 
    - Có 2 keyword không sử dụng trong java là `const, goto`

![50 keyword](/assets/50-keyword.jpg)

### 1.1 Các trường hợp đặt tên  

- Viết hoa đầu mỗi cụm từ **==>** **Vd: HelloWorld**
  - `class` sử dụng `noun` **==>** **Vd: System**
  - `interface` sử dụng `adjective` **==>** **Vd: Runnable**
  - `project` . 
- Bắt đầu bằng chữ thường và đầu mỗi cụm chữ sẽ viết hoa **==>** **Vd: doSomething**
  - `method` sử dụng `verb-noun` **==>** **Vd: getName() ==> do, get, set, is, add, remove**
  - `variable` có nghĩa và ngắn **==>** **Vd: firstName**
- `constant` nên viết hoa hết, phân cách giữa các cụm từ bằng `_` và bắt đầu có `final` ở trước. **==>** **Vd: MAX_SPEED**
- `package` nên viết thường hết, bắt đầu bằng `domain.organization.name` **==>** **Vd: edu.nlu.exercise**

## 2. Variable 

- Là **1 vùng ram** được đặt tên **chiếm số byte** nhất định tuỳ vào data type
- Cấu tạo từ **data type và name**
- Có 3 loại biến là **local, instance, static**
- **non-static field và static field** thuộc về khai báo trong **object**.
- Sử dụng **final** để chỉ định biến hằng chống gán lại giá trị

```java
// declare
double salary, height;

// initialize (phải khởi tạo giá trị trước khi sử dụng)
salary = 3.5;
int age = 22;

// java 10
var salary = 3.5; // double
var age = 22; // int
```

### 2.1 Scope

![variable scope](/assets/variable-scope.jpg)

### 2.2 Static variable

- Còn gọi là **class variable, static field**
- Khai báo từ khoá static khi sử dụng

```java
class MyClass {
  static int number = 1;
  void getNumber() {
    number = 2;
  }
  static void getNumber2() {
    number = 3;
  }
  public static void main(String[] args) {
    sout(number); // 1
    new MyClass().getNumber(); // 2
    getNumber2(); // 3
    sout(number); // 3
  }
}
```

> **không thể** sử từ khoá **static** trong khai báo biến ở method vì **scope nó chỉ có thể là lớp**

### 2.3 Instance variable

- Còn gọi là **Non-Static Field, Member variable**

### 2.4 Local variable

### 2.5 Parameter

## 3. Constant

- Keyword `final` biểu thị là 1 constant

```java
public class Constants {

  public static final int MY_AGE = 22; // hằng số class

  public static void main(String[] args) {
      final double CM_PER_INCH = 2.54; // hằng số 
  }
}
```