# Operator - Math - Type Conversion 

## Mục lục nội dung

  - [1. Operator](#1-operator)
    - [1.1 Arithmetic](#11-arithmetic)
      - [Một số lưu ý](#một-số-lưu-ý)
        - [Chia cho 0](#chia-cho-0)
        - [Kiểm tra NaN](#kiểm-tra-nan)
        - [Byte](#byte)
    - [1.2 Unary](#12-unary)
    - [1.3 Assignment](#13-assignment)
    - [1.4 Relational](#14-relational)
    - [1.5 Logical](#15-logical)
    - [1.6 Ternary](#16-ternary)
    - [1.7 Bitwise](#17-bitwise)
    - [1.8 Shift](#18-shift)
    - [1.9 Instance of](#19-instance-of)
    - [1.10 Sự khác nhau giữa logical và bitwise](#110-sự-khác-nhau-giữa-logical-và-bitwise)
    - [1.11 Thứ tự ưu tiên trong operator](#111-thứ-tự-ưu-tiên-trong-operator)
  - [2. Một vài Math class thường dùng](#2-một-vài-math-class-thường-dùng)
  - [3. Type conversion](#3-type-conversion)

## 1. Operator

Toán tử gồm **Arithmetic (số học), Assignment, Unary, Relational, Logical, Ternary, Bitwise, Shift, Type Comparison**.

### 1.1 Arithmetic

- Toán tử Arithmetic gồm `+`, `-`, `*`, `/`, `%`.
- Giá trị khi tính sẽ **ưu tiên ép kiểu** theo kiểu lớn hơn

```java
double add = 3 + 2.2; // 5.2
double subtract = 3 - 2.2; // 0.79...8
double multiply = 3 * 2.2; // 6.60...5
double devision = 5 / 2; // 2.0
double devision = 5.0 / 2; // 2.5
double devision = (double) 5 / 2 ; // 2.5
double remainder = 5 % 2; // 1
double remainder = 5.5 % 2; // 1.5
```

#### Một số lưu ý

##### Chia cho 0

```java
int integer = 1 / 0; // runtime
double result = 10 / 0; // runtime
double result = 10.0 / 0; // infinity
```

##### Kiểm tra NaN

```java
// kiểm tra NaN thông qua isNaN ****
double x = 7.0/0.0;
x != Double.NaN; // true
x <  Double.NaN; // false
x <=  Double.NaN; // false
x >  Double.NaN; // false
x >=  Double.NaN; // false
x ==  Double.NaN; // false
```

##### Byte

Khi đổi ra bit thì 0 ở đầu là dương còn 1 là âm 

```java
// -128 -> 127
/*
 * 350 nó là phép tính kiểu int và giá trị trả về cast qua 
 * byte dẫn đến vượt quá miền gây lỗi biên dịch
 */
byte result = 70 * 5; // compile 
byte a = 70, b = 5, c = a * b; // compile

/*
 * khi nó là byte thì vượt quá miền sẽ quay đầu
 * 350 vượt quá 127 => 223 => quay đầu lại -128
 * -128 + 223 = 95 - 1 (có số 0) = 94
 */
byte result = (byte) 70 * 5; // compile
byte result = (byte) (70 * 5); // 94
byte result = 70; 
result *= 5; // 94
```

### 1.2 Unary

- Toán tử Unary gồm `++`, `--`, `!`, `+`, `-`, `~`

```java
int a = 5, b = 6;
System.out.println(++a); // 6
System.out.println(a); // 6
System.out.println(b++); // 6
System.out.println(b); // 7
System.out.println(+b); // 7
System.out.println(-b); // -7
```

> **++** áp dụng với **char** sẽ ra ký tự tiếp theo

### 1.3 Assignment

- Toán tử Assignment gồm `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `^=`, `|=`, `<<=`, `>>=`, `>>>=` 

> Nó sẽ tự động cast cho phù hợp với kiểu dữ liệu

```java
int result = 1 + 3.5; // compile phải (int)(1 + 3.5)
int result = 1;
result += 3.5; // 4.0 nó sẽ tự động hiểu (int)(1 + 3.5)
```
### 1.4 Relational 

- Toán tử Relational gồm `==`, `!=`, `<`, `<=`, `>`, `>=`

### 1.5 Logical 

Toán tử Logical gồm `&&`, `||`

> **short-circuiting ==>** kiểm tra bên trái toán tử đúng mới kiểm tra bên phải 

### 1.6 Ternary

- Toán tử Ternary gồm `? :`

```java
// ưu tiên kiểu nào lớn hơn
int x = 4;
System.out.println(x > 4 ? 99.99 : 9); // 9.0
```

### 1.7 Bitwise

Toán tử Bitwise gồm `&`, `|`, `^`, `-` và làm việc dựa trên `bit`

- `&` => and 
  - `1 & 0 => 0`
  - `0 & 1 => 0`
  - `1 & 1 => 1`
  - `0 & 0 => 0`

```java
System.out.println(10 & 12); // 8
/*
 * 10 => 1010
 * 12 => 1100
 *       1000 => 8
 */
```

- `|` => or 
- `^` => xor 
- `-` => not 

> Kiểm tra cả 2 bên toán tử

### 1.8 Shift

- Toán tử Shift gồm `<<`, `>>`, `>>>`

### 1.9 Instance of 

- Toán tử Type Comparison gồm `instance of` 

```Java
int a = 5, b = 6, c = 12;
System.out.println((a > 4) ^ (b > 5)); // false, khác với || là 1 cái true nhưng không phải cả 2
System.out.println(~10); // -11
System.out.println(~(-10)); // 9
```

> `==` được sử dụng để so sánh giá trị trong primitive và so sánh cùng reference đối với object

**instance of** dùng để kiểm tra xem **object** có phải là **instance** của **class, subclass(extends) hay class implement interface**

```java
String name = "Java";
if (name instanceof String) {
    System.out.println("an instance of String class");
}
 
// test for extends object
if (name instanceof Object) {
    System.out.println("an instance of Object class");
}
 
// test for implement interface charsequence
if (name instanceof CharSequence) {
    System.out.println("an instance of CharSequence interface");
}
```

### 1.10 Sự khác nhau giữa logical và bitwise

Logical sẽ chỉ **kiểm tra bên trái** trừ khi true mới sang bên phải còn bitwise sẽ **kiểm tra cả 2 bên**

```java
int x = 1;
System.out.println((x != 0) & (1 / x) > 1); // false
System.out.println((x != 0) && (1 / x) > 1); // false

int x = 0;
System.out.println((x != 0) & (1 / x) > 1); // runtime
System.out.println((x != 0) && (1 / x) > 1); // false
/*
 * thứ 1 lỗi runtime là do 1/0 không được dẫn đến lỗi
 * thứ 2 logical thì nó sẽ check bên trái mà x = 0 => false
 *       còn bitwise check cả 2 nên bên phải cũng check dẫn 
 *       đến 1 / 0 gây ra lỗi runtime 
 */

String str = null;
if (str != null && !str.equals("")) {}  // không thực thi
// runtime null không thể sử dụng equals
if (str != null & !str.equals("")) {}  

boolean a = true;
boolean b = false;
boolean c = false;

// (((c || b) && b) || a)
boolean result1 = a || b && c||b; // true 
// ((a | b) && (c || b))
boolean result2 = a  | b && c||b; // false 

int a = 10;
if(++a==10 && ++a==12) {}
System.out.println(a); // 11
if(++a==10 & ++a==12) {} 
System.out.println(a); // 12
```

### 1.11 Thứ tự ưu tiên trong operator

![operator precedence](/assets/operator-precedence.png)

## 2. Một vài Math class thường dùng

- Các phương thức trong lớp Math là static method

```Java
System.out.println(Math.abs(-4.7)); // 4.7
System.out.println(Math.ceil(1.4)); // 2.0
System.out.println(Math.floor(1.7)); // 1.0
System.out.println(Math.round(1.49)); // 1
System.out.println(Math.round(1.5)); // 2
System.out.println(Math.max(5, 10)); // 10
System.out.println(Math.min(5.2, 10)); // 5.2

System.out.println(Math.sqrt(64)); // 8.0
System.out.println((double)Math.sqrt(-3)); // NaN tương tự cho float
System.out.println((int)Math.sqrt(-3)); // 0

System.out.println(Math.pow(2,3)); // 8.0
System.out.println(Math.random()); // return 0.0 < x < 1.0
System.out.println((int) (Math.random() * 2)); // return giá trị từ 0 <= value < 2 
```

## 3. Type conversion

- Hay còn gọi là **type casting**, có 2 loại là cast là **wide** (rộng) và **narrow** (hẹp)
- Với mũi tên liền thì độ chính xác giữ nguyên còn với mũi tên không liền thì bị mất độ chính xác

![type conversion](/assets/convertion-datatype.png)


- Wide được ép một cách tự động do chuyển từ loại nhỏ sang loại có kích thước lớn.

```java
int typeInt = 3;
double intToDouble = typeInt;
System.out.println(intToDouble); // 3.0
```

- Narrow được ép một cách thủ công do chuyển từ loại lớn sang loại có kích thước nhỏ:
```java
double typeDouble = 3.5;
int typeCastInt = (int) typeDouble;
System.out.println(typeCastInt); // 3
```

## Xem thêm bài viết khác

- [Naming Convention - Variable - Constant](/Chap1/Day3.md)
- [String - Character](/Chap1/Day5.md)
