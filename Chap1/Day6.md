# Scanner Input - Format

## Mục lục nội dung

- [1. Scanner input](#1-scanner-input)
- [2. printf() và format()](#2-printf-và-format)

## 1. Scanner input

Sử dụng để người dùng có thể nhập vào trên màn hình và in ra kết quả.

```java
Scanner input = new Scanner(System.in);
input.nextByte(); // => read một số integer kiểu byte
input.nextShort(); // => read một số integer kiểu short
input.nextInt(); // => read một số integer kiểu int
input.nextLong(); // => read một số integer kiểu long
input.nextFloat(); // => read một số integer kiểu float
input.nextDouble(); // => read một số integer kiểu double

input.next(); // => read một string dừng trước một ký tự space
// vd nhập hello world thì in ra hello vì dừng trước space

input.nextLine(); // => read một string dừng trước phím enter
// vd nhập hello world thì in ra hello world
```

##### Lưu ý khi sử dụng nextLine

- Trường hợp này xảy ra khi **nhập số trước nhập chuỗi**.
- Không có dòng `scanner.nextLine()` ở **dưới age** ==> nhập age xong thì **không thể nhập favorite** mà nó in ra luôn.
  - Nguyên nhân do khi ta nhập age xong ta nhấn enter thì lúc này `\n` vẫn còn nằm trong input nếu khi ta nhập bước kế tiếp là `nextLine()` thì **\n** sẽ được sử dụng cho input lúc này dẫn đến nó sẽ kết thúc mà không cho ta nhập.

```java
System.out.println("nhập name ");
String name = scanner.nextLine();
System.out.println("nhập tuổi ");
int age = scanner.nextInt(); // nếu ta nhập 18 thong
// nextLine nó xóa hết bộ đệm nên \n_thong sẽ bị xóa theo
scanner.nextLine();
System.out.println("nhập sở thích "); // nhập thai
String favorite = scanner.nextLine();
System.out.println("name is " + name + " age is age + " favorite is " + favorite); // thai
```

`hasNextInt` trong scanner có tác dụng **kiểm tra xem đầu vào có phải là int** không, nếu sai sẽ trả về false đúng trả về true.

- syntax: `boolean check = scanner.hasNextInt();`
- lưu ý nếu `scanner.close()` được gọi thì sau hàm này scanner sẽ không sử dụng được

## 2. printf() và format()

- Về cơ bản cả printf() và String.format() đều định dạng chung kiểu chỉ khác ở chổ là printf() sẽ format xong **in ra luôn** còn String.format() sẽ chỉ format thành **String**.
- Định dạng theo kiểu `%[argument_index$][flags][width][.precision]conversion`

- **argument_index** dùng để gán vị trí dành cho đối số

```java
// use arg
int a1 = 100, a2 = 200, a3 = 300;
System.out.println("argument not used yet " + String.format("%d %d %d", a1, a2, a3)); // 100 200 300
// gán thứ tự arg hiển thị
System.out.println("argument used " + String.format("%3$d %1$d %2$d", a1, a2, a3)); // 300 100 200
// copy định dạng trc nó (copy đối số 2 ở vị trí đầu) cho vị trí 2
System.out.println("argument used " + String.format("%2$d %<d %1$d", a1, a2, a3)); // 200 200 100
```

- **flag**

```java
int w = 5, x = 235, v = -235, t = 1234567;

// thay khoảng trắng = 0
System.out.println("flag used " + String.format("w=%04d x=%04d", w, x)); // 0005 và 0235
// chuyển hết sang bên trái
System.out.println("flag used " + String.format("w=%-4d x=%-4d", w, x)); // 5___ và 235_
// chuyển sang hex
System.out.println("flag used " + String.format("w=%#x", w)); // 0x5
// tạo , giữa các số nguyên
System.out.println("flag used " + String.format("t=%,d", t)); // 1,234,567

// sắp xếp ngay ngắn 235 và -235 nó song song nhau nếu không nó lệch
System.out.println("flag used " + String.format("% d", x)); //  235
System.out.println("flag used " + String.format("% d", v)); // -235

// áp dụng cho tọa độ
System.out.println("flag used " + String.format("%+d", x)); // +235
System.out.println("flag used " + String.format("%+d", v)); // -235

// giá trị âm sẽ bị bỏ trong ngoặc
System.out.println("flag used " + String.format("% (d", x)); // 235
System.out.println("flag used " + String.format("%(d", v)); // (235)
```

- **width** là chiều rộng tổng của số ký tự (không có âm nếu có âm nó sẽ căn trái) và căn theo lề phải. Lưu ý là **bao gồm cả dấu . và giá trị sau**

```java
int w = 5, x = 235;
System.out.println("width used " + String.format("w=%4d x=%4d", w, x)); // ___5 và _235
```

- **precision** là hạn chế số ký tự (áp dụng cho dấu phẩy động).

```java
double d = 11.2;
System.out.println("precision used " + String.format("%.2f", d)); // 11.20
```

- **conversion** dùng để xác định kiểu định dạng bao gồm - `%b` định dạng kiểu boolean - `%c` định dạng kiểu char - `%d` định dạng kiểu integer - `%f` định dạng kiểu float và doulbe - `%s` định dạng kiểu String - `%o` định dạng kiểu Octal - `%x` hoặc `%X` định dạng kiểu Hex - `%e` hoặc `%E` định dạng kiểu Scientific
  Tạo định dạng có `%` ở kết quả

```java
System.out.printf("tạo format dạng percent => %.2f%%", 75.22); // 75.22%
```

## Xem thêm bài viết khác

- [String - Character](/Chap1/Day5.md)
- [Control Flow](/Chap1/Day7.md)
