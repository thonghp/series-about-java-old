# Naming Convention - Variable - Constant

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

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

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

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 2. Variable 

- Là **1 vùng ram** được đặt tên **chiếm số byte** nhất định tuỳ vào data type
- Cấu tạo từ **data type và name**
- Các loại biến: 
  - [Instance variable](#23-instance-variable) (non-static field)
  - [Class variable](#22-static-variable) (static field)
  - [Local variable]((#24-local-variable))
  - [Parameter]((#25-parameter))

```java
public class Employee {
  /*
   * phạm vi này được gọi là field
   * field có thể là class/member variable
   */
  private static int age = 22;
  private double salary;

  public double totalSalary(double salary) {
    int day = 31; // local variable không phải là field
    ...
  }
}

// java 10
var salary = 3.5; // double
var age = 22; // int
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.1 Scope

![variable scope](/assets/variable-scope.jpg)

### 2.2 Static variable

- Còn gọi là **class variable, static field**
- Bất kỳ field nào khai báo với **`static modifier`**
- **Chỉ có một bản sao** của biến tồn tại dù khởi tạo bao nhiêu lần và sẽ **nhận giá trị sau cùng**

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

> **không thể** sử dụng từ khoá **static** trong **khai báo biến ở method** vì **scope nó chỉ có thể là lớp**

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.3 Instance variable

- Còn gọi là **Non-Static Field, Member variable**
- Object lưu trữ state trong **non-static field** => được khai báo mà không có từ khóa **`static`** 
- Khai báo trong 1 lớp ngoài method và chỉ được **khởi tạo khi lớp khởi tạo**
- Không cần khởi tạo giá trị vì đã **có giá trị default**
- Phía trước biến 
  - Có thể sử dụng 4 **access modifier, `final, transient`**
  - Không thể sử dụng **`abstract, synchronized, strictfp, native, static`** (vì lúc này là static variable)

```java
class MyClass {
  private int number; // instance variable
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.4 Local variable

- Biến nằm trong method và scope cũng chỉ ở trong method
- Phải **khởi tạo giá trị** trước khi sử dụng
- Nằm trong **stack không phải heap**
- Phía trước biến chỉ có thể là **`final`** 

```java
class MyClass {
  void getNumber() {
    int number = 2; // local variable
  }
}
```

> Nếu biến **instance cùng tên với local** thì trong **method biến local sẽ ưu tiên hơn**

### 2.5 Parameter

- Các tham số được phân loại là variable chứ không phải là field

```java
public static void main(String[] args) {} // args là tham số
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

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

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [Simple Java Program - Comment - Datatype](/Chap1/Day2.md)
- [Operator - Math - Type Conversion](/Chap1/Day4.md)