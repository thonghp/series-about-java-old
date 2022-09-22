# Array

## Mục lục nội dung

- [1. Array](#1-array)
- [2. One dimentional](#2-one-dimentional)
  - [2.1 Khai báo](#21-khai-báo)
  - [2.2 Khởi tạo](#22-khởi-tạo)
  - [2.3 Duyệt mảng](#23-duyệt-mảng)
  - [2.4 Note](#24-note)
  - [2.5 Sao chép trong mảng 1 chiều](#25-sao-chép-trong-mảng-1-chiều)
  - [2.6 sort và toString trong Arrays](#26-sort-và-tostring-trong-arrays)
  - [2.7 Chèn phần tử vào trong mảng](#27-chèn-phần-tử-vào-trong-mảng)
  - [2.8 Đếm số lần xuất hiện của từng phần tử](#28-đếm-số-lần-xuất-hiện-của-từng-phần-tử)
  - [2.9 In tất cả phần tử nếu trùng lặp thì in 1 lần](#29-in-tất-cả-phần-tử-nếu-trùng-lặp-thì-in-1-lần)
  - [2.10 Arrays.equals()](#210-arraysequals)
- [3. Two dimentional](#3-two-dimentional)
  - [3.1 Khởi tạo](#31-khởi-tạo)
  - [3.2 Duyệt mảng](#32-duyệt-mảng)
  - [3.3 Ragged](#33-ragged)
  - [3.4 clone](#34-clone)
  - [3.5 Arrays.deepEquals() để so sánh 2 matrix](#35-arraysdeepequals-để-so-sánh-2-matrix)

## 1. Array

- Là tập hợp các element có **cùng data type** và **size cố định**.
- Các element trong array được sắp xếp theo thứ tự và thao tác dựa trên **index**.
- Nếu mảng là primitive thì tất cả số khởi tạo mặc định là **0** còn object là **null** ngay cả khi chưa initialize.

## 2. One dimentional

- Index bắt đầu từ 0 đến **`array.length - 1`** và độ dài của array là **`array.length`**;
- Truy cập element bằng cách tham chiếu đến index.
- Duyệt qua array bằng **`for`** hoặc **`for-each`**

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.1 Khai báo

- Có 3 kiểu khai báo nhưng thường sử dụng kiểu 1

```java
// declare
int[] array; // c1
int []array; // c2
int array[]; // c3
```

### 2.2 Khởi tạo

- Có 2 dạng khởi tạo giá trị:

```java
// initialize
Object[] array = new Object[2]; // [null, null]
int[] array = new int[2]; // [0, 0]
array[1] = 1;
array[2] = 2;

// array literal/anonymous array
String[] name = {"thong","thai"}; // c1 sử dụng chủ yếu
int[] integer = new int[]{1,2,3}; // c2

// truy cập element
System.out.println(integer[0]); // 1
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.3 Duyệt mảng

- Có 2 dạng duyệt qua mảng là **`for`** và **`for-each`**

```java
int[] integer = {1,2,3};
for (int i = 0; i < integer.length; i++) {
  System.out.println(integer[i]); // 1 2 3
}

// lưu ý i sẽ cùng datatype vs integer
for (int i : integer) { // duyệt qua mỗi i trong integer
  System.out.println(i); // 1 2 3
}

// lưu ý array trong char không cần duyệt for để lấy value
char[] city = {'t', 'p', 'h', 'c', 'm'};
System.out.println(city); // tphcm
```

> - **for-each** chỉ duyệt qua các phần tử của array không phải các giá trị index
> - chỉ nên sử dụng **for-each** để duyệt mảng hoặc tính toán đơn giản không nên sử dụng trong điều kiện

### 2.4 Note

```java
// Array có length = 0 sẽ khác mảng null
int[] empty = new int[0];
int[] empty = new int[]{};
int[] arrayNull = null;

int[] a,b // a, b là mảng
int a[],b // a là mảng, b là int

// vượt quá phạm vi => ném lỗi ArrayIndexOutOfBoundsException
int[] arr = {1,2,3};
System.out.println(arr[3]); // ArrayIndexOutOfBoundsException
System.out.println(arr[-1]); // ArrayIndexOutOfBoundsException
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.5 Sao chép trong mảng 1 chiều

```java
/*
 * khi ta muốn sao chép từ đầu đến 1 độ dài chỉ định sử dụng copyOf
 * khi ta muốn sao chép từ 1 vị trí bất kỳ đến 1 vị trí bất kỳ thì ta sử dụng system.arraycopy hoặc arrays.copyOfRange
 */

int[] arr = {1, 2, 3, 4, 5};

// sao chép y chang
int[] arrClone = array.clone(); // [1, 2, 3, 4, 5]

/*
 * copy từ vị trí chỉ định đến array.length - 1 của mảng gốc
 * vào array mới theo vị trí chỉ định 
 * điều kiện tiên quyết phải tạo một mảng mới
 */
int[] arrCopy = new int[3];
/*
 * lấy element từ vị trí (2 -> arr.length-1) [3, 4 ,5]
 * copy vào vị trí 1 -> 2 của arrCopy [0, 0, 0]
 * arrCopy [0, 3, 4]
 */
System.arraycopy(arr, 3, arrCopy, 1, 2);

// copy từ vị trí 0 và đến newLength
int[] arrCopyOf = Arrays.copyOf(arr, 2); // [1, 2]

// copy từ theo vị trí chỉ định có thể mở rộng mảng
// [3, 4, 5, 0, 0, 0]
int[] arrCopyOfRange = Arrays.copyOfRange(arr, 2, 8); 
```

> Tất cả cách trên đều khác reference với mảng gốc

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.6 sort và toString trong Arrays

```java
public static void arraysSort(int[] array) {
    System.out.println("array sau khi sắp xếp: ");
    // chỉ sắp xếp tăng dần
    Arrays.sort(array);
    // in mảng
    System.out.println(Arrays.toString(array));
}
```

### 2.7 Chèn phần tử vào trong mảng

```java
public static int[] insertElement(int index, int[] arr, int value) {
    int[] newArr = new int[arr.length + 1];
    int temp = 0;
    for (int i = 0; i < newArr.length; i++) {
        if(index == i) {
            newArr[i] = value;
        } else {
            newArr[i] = arr[temp++];
        }
    }
    return newArr;
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.8 Đếm số lần xuất hiện của từng phần tử

Phân tích bài toán: ở bài toán này sẽ thực hiện 2 bước

- Bước 1 là đếm số lượng
  - Tạo một mảng để lưu số lượng
- Bước 2 là phần tử nào trùng không đếm nữa
  - Sẽ gán nó bằng một giá trị gì đó để khi tới ô đó nó ko đếm dc

```java
int[] arr = new int[]{1, 2, 8, 3, 2, 2, 2, 5, 1};
int[] fr = new int[arr.length]; // sử dụng để lưu số lần xuất hiện của phần tử đó
int visited = -1;
for (int i = 0; i < arr.length; i++) {
    int count = 1;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[i] == arr[j]) {
            count++;
            fr[j] = visited; // mục đích là những ô trùng sẽ được gán = -1
        }
    }
    if (fr[i] != visited)
        fr[i] = count;
}

// fr = {2,4,1,1,-1,-1,-1,1,-1}
for (int i = 0; i < fr.length; i++) {
    if (fr[i] != visited) // những vị trí = -1 (là những vị trí trùng ko hiển thị)
        System.out.println("    " + arr[i] + "    |    " + fr[i]);
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.9 In tất cả phần tử nếu trùng lặp thì in 1 lần

- Mảng phải được sắp xếp

```java
public static int removeDuplicateElements(int arr[], int n) {
    if (n == 0 || n == 1) {
        return n;
    }

    // {10, 20, 20, 30, 30, 40, 50, 50};

    int[] temp = new int[n];

    int j = 0;
    for (int i=0; i<n-1; i++)
        if (arr[i] != arr[i+1])
            temp[j++] = arr[i];

    // [10, 20, 30, 40, 0, 0, 0, 0]

    temp[j++] = arr[n-1];
    // [10, 20, 30, 40, 50, 0, 0, 0]

    // Modify original array
    for (int i=0; i<j; i++)
        arr[i] = temp[i];

    return j; // 5
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 2.10 Arrays.equals()

Lưu ý khi so sánh array muốn so sánh phần tử bên trong coi 2 mảng có giống nhau không thì ta sử dụng Arrays.equals()

```java
int arr[] = {12, 13, 14, 15, 16, 17, 18};
int[] arr2 = {12, 13, 14, 15, 16, 17, 18};
System.out.println(Arrays.equals(arr, arr2)); // true
```

Một số method có sẵn thường dùng nằm trong Arrays API => **asList(), binarySearch(), copyOf(), copyOfRange(), equals(), fill(), sort(), toString()**

## 3. Two dimentional

### 3.1 Khởi tạo

Ma trận mxn với m là hàng và n là cột

```java
// có 4 cách declare và thường sử dụng c1 là chủ yếu
int[][] matrix; // c1
int [][]matrix; // c2
int matrix[][]; // c3
int []matrix[]; // c4

// initialize
int[][] matrix;
matrix = new int[2][2];
matrix[0][0] = 1;
matrix[0][1] = 1;
matrix[1][0] = 1;
matrix[1][1] = 2;

int[][] matrix = {{1,2},{3,4}};

// truy cập
System.out.println(matrix[1][0]); // in ra vị trí ở hàng 1 cột 0 là 3
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.2 Duyệt mảng

```java
for (int i = 0; i < matrix.length; i++) {
  for (int j = 0; j < matrix[i].length; j++) {
      System.out.print(matrix[i][j]+" ");
  }
  System.out.println();
}

for (int[] row : matrix) {
    for (int value : row) {
        System.out.print(i);
    }
    System.out.println();
}
```

### 3.3 Ragged

```java
// ragged array là chỉ định cột cho từng hàng,
int[][] error = new int[][1]; // lỗi
int[][] jagged = new int[2][];
jagged[0] = new int[2];
jagged[1] = new int[3];
int count = 0;
for (int i = 0; i < jagged.length; i++) {
    for (int j = 0; j < jagged[i].length; j++) {
        jagged[i][j] = count++;
    }
}
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

### 3.4 clone

```java
// clone matrix sẽ khác array là nó chỉ tạo mảng mới duy nhất còn mảng con sẽ share với nhau
int intArray[][] = {{1,2,3},{4,5}};
int cloneArray[][] = intArray.clone();

// khác reference
System.out.println(intArray == cloneArray); // false

// will print true, do các mảng con sẽ share với nhau
System.out.println(intArray[0] == cloneArray[0]);
System.out.println(intArray[1] == cloneArray[0]);
```

### 3.5 Arrays.deepEquals() để so sánh 2 matrix

```java
int[][] a1 = {{2, 4}, {4, 6}, {8, 10}};
int[][] a2 = {{2, 4}, {4, 6}, {8, 10}};
System.out.println(Arrays.deepEquals(a1, a2)); // true
```

**[⬆ Quay trở lại đầu trang](#mục-lục-nội-dung)**

## Xem thêm bài viết khác

- [Control flow](/Chap1/Day7.md)
- [](/Chap1/Day9.md)
