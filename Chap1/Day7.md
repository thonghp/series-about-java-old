# Control Flow

## Mục lục nội dung

- [1. Conditional statement](#1-conditional-statement)
  - [1.1 if](#11-if)
  - [1.2 if - else](#12-if---else)
  - [1.3 if - else - if](#13-if---else---if)
  - [1.4 nested if](#14-nested-if)
- [2 loops](#2-loops)
  - [2.1 while](#21-while)
  - [2.2 do - while](#22-do---while)
  - [2.3 for](#23-for)
  - [2.4 for - each](#24-for---each)
  - [2.5 Sự khác nhau giữa for và for-each](#25-sự-khác-nhau-giữa-for-và-for-each)
- [3 switch statement](#3-switch-statement)
  - [3.1 switch truyền thống](#31-switch-truyền-thống)
  - [3.2 switch nâng cao](#32-switch-nâng-cao)
- [4 jump statement](#4-jump-statement)
  - [4.1 break](#41-break)
  - [4.2 continue](#42-continue)
  - [4.3 label break](#43-label-break)

## 1. Conditional statement

### 1.1 if

**Syntax:**

```java
if (condition) { // condition true mới excute
  // statement
}
```

- Vd về sử dụng `if`

```java
boolean isValue = true;
if (isValue) { // isValue = true
  System.out.println("hello");
}
```

### 1.2 if - else

**Syntax:**

```java
if (condition) {
    // statement
} else {
  // statement
}
```

- Vd về sử dụng `if-else`

```java
boolean isValue = false;
// in ra hi
if (isValue) {
  System.out.println("hello");
} else {
  System.out.println("hi");
}

// gán isValue = true lúc này nó sẽ cập nhật luôn
if (isValue = true) {
  System.out.println("condition is assigned to true");
}
System.out.println(isValue); // true không còn là false
```

### 1.3 if - else - if

```java
if (condition1) {
    // statement1
} else if (condition2) {
    // statement2
} else {
    // statement3
}
```

### 1.4 nested if

```java
if (condition1) {
  ...
   if (condition2) {
      // statement
   }
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 2 loops

### 2.1 while

- Sử dụng khi số lần lặp chưa xác định

**Syntax**

```java
while (condition) statement
```

- Vd về sử dụng `while`

```java
int i = 0;
while (i < 5) {
  System.out.println(i);
  i++; // để tránh loop vô hạn
}
```

> Sử dụng **while(true)** cho trường hợp điều kiện chưa biết trước.

### 2.2 do - while

- Sử dụng khi số lần lặp không xác định
- Luôn thực thi câu lệnh trong `do` trước khi kiểm tra điều kiện `while` kể cả điều kiện không thỏa

**Syntax**

```java
do statement while (condition);
```

- Vd về sử dụng `do-while`

```java
int i = 1;
// in ra 1
do {
  System.out.println(i);
  i++;
}
while (i > 2);
```

### 2.3 for

Sử dụng khi số lần lặp xác định

```java
for (int i = 0; i < 5; i++) {
  System.out.println(i);
}

// sử dụng i ngoài vòng for
int i;
for (i = 0; i < 5; i++) {}
System.out.println(i); // 5
```

### 2.4 for - each

Được sử dụng để lặp qua các element trong array 1 chiều, xem đầy đủ ở phần array.

```java
for(data_type variable : array) {
  ...
}
```

### 2.5 Sự khác nhau giữa for và for-each

| for                       | for-each                                         |
| ------------------------- | ------------------------------------------------ |
| tùy chỉnh bộ đếm để duyệt | mỗi lần duyệt tăng bộ đếm lên 1 lần              |
| tất cả trường hợp         | chỉ dùng trong array(dạng 1 chiều) và collection |
| duyệt tới hoặc lùi        | chỉ có thể duyệt tới                             |
| có thể thao tác           | Không thể thao tác ở vị trí chỉ định khi duyệt   |

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 3 switch statement

**Syntax:**

```java
switch(expression) {
case value1: // case phải duy nhất và cùng loại với expression
  ...
  break;
case value2:
  ...
  break;
  ...
default: // sẽ thực thi khi điều kiện không thỏa
  ...
}
```

expression chỉ có thể là

- byte, short, int, char (wrapper tương ứng)
- enum
- String

### 3.1 switch truyền thống

```java
int switchTest = 10;
switch (switchTest + 1 + 1) {
    case 111:
        System.out.println("bằng 111");
        break;
    case 10:
        System.out.println("bang 10");
        break;
    case 10 + 1 + 1: // tương đương vs case 12:
        System.out.println("bang 12");
        break;
} // return bang 12
```

- Nhiều trường hợp

```java
switch (itemCode) { // expression
    case "A": // case phải duy nhất và cùng loại với expression
    case "B":
    case "C":
        System.out.println("chữ in hoa");
        break;
    case "a":
    case "b":
        System.out.println("chữ thường");
        break;
    default: // sẽ thực thi khi điều kiện không thỏa
        ...
}
```

### 3.2 switch nâng cao

- java 12

```java
int switchTest = 10;
String assign = switch (switchTest + 1 + 1) {
   case 111 -> "MỘT MỘT MỘT";
   case 10 -> "MƯỜI";
   case 10 + 1 + 1 -> "MƯỜI HAI";
   default -> "";
};
System.out.println(assign); // muoi hai
```

- java 13

```java
String token = "abc";
int tokenType = switch(token) {
    case "123" : yield 0;
    case "abc" : yield 1;
    default : yield -1;
};
System.out.println(tokenType); // 1
```

- Nhiều trường hợp (từ java 12)

```java
switch (itemCode) {
    case "A", "B", "C":
        System.out.println("chữ in hoa");
        break;
    case "a", "b":
        System.out.println("chữ thường");
        break;
    default:
        ...
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## 4 jump statement

### 4.1 break

**Dừng thực thi ngay lập tức** tại nơi thỏa điều kiện không quan tâm vòng lặp, sử dụng trong `switch`, `for loop` và `while-loop`

```java
for (int i = 0; i < 10; i++) {
  if (i == 4) {
    break;
  }
  System.out.println(i); // 0,1,2,3
}
```

### 4.2 continue

**Bỏ qua điều kiện thỏa** và chạy cho đến khi hết vòng lặp, sử dụng trong `for loop` và `while loop`

```java
for (int i = 0; i < 10; i++) {
  if (i == 4) {
    continue;
  }
  System.out.println(i); // 0,1,2,3,5,6,7,8,9
}
```

### 4.3 label break 

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [Scanner Input - Format](/Chap1/Day6.md)
- [Array](/Chap1/Day8.md)
