# Các Ngôn Ngữ Lập Trình

- [1. Java](#1-java)
- [2. Java với C và C++](#2-java-với-c-và-c)
- [3. Java với Javascript](#3-java-với-javascript)

## 1. Java

- Là ngôn ngữ biên dịch - **compiled language**
  - **Viết code => chạy code thông qua compiler => tạo bytecode => bytecode chạy trong JVM**
- Syntax **tương tự** C, C++
- Ngôn ngữ **đa luồng**
- **Ngang bằng hoặc nhanh hơn** hầu hết ngôn ngữ biên dịch và **nhanh hơn nhiều** so với ngôn ngữ thông dịch
- Không phụ thuộc vào nền tảng
- Ít tính năng cấp thấp do được **`jvm`** và **`compiler`** xư lý tự động
- Sử dụng **`garbage collector`** để quản lý memory
- Chạy chậm hơn, tiêu tốn một lượng bộ nhớ đáng kể
- Ngôn ngữ tĩnh (phiên bản trước)
  - Khai báo kiểu dữ liệu trước khi sử dụng

## 2. Java với C và C++

| C                                   | C++                        | Java                     |
| ----------------------------------- | -------------------------- | ------------------------ |
| Procedural language                 | Oop                        | Oop chưa 100%            |
| Dựa trên assembly                   | Dựa trên C                 | Dựa trên C/C++           |
| Chỉ Compiler                        | Chỉ Compiler               | (Compiler + interpreter) |
| Thực thi trực tiếp                  | Thực thi trực tiếp         | Thực thi bới JVM         |
| Tiếp cận theo Top-down              | Tiếp cận theo Bottom-up    | Tiếp cận theo Bottom-up  |
| Ko hỗ trợ kết nối database          | Ko hỗ trợ kết nối database | Hỗ trợ kết nối database  |
| Hỗ trợ con trỏ                      | Hỗ trợ con trỏ             | Ko hỗ trợ con trỏ        |
| Ko hỗ trợ kế thừa                   | Hỗ trợ kế thừa             | Hỗ trợ kế thừa (ko đa)   |
| Ko hỗ trợ xử lý ngoại lệ            | Hỗ trợ xử lý ngoại lệ      | Hỗ trợ xử lý ngoại lệ    |
| Ko hỗ trợ constructor và destructor | Hỗ trợ cả 2                | Chỉ hỗ trợ constructor   |

## 3. Java với Javascript

| Java                                                 | Javascript                                 |
| ---------------------------------------------------- | ------------------------------------------ |
| Ngôn ngữ lập trình                                   | Ngôn ngữ script                            |
| Oop                                                  | Object-Based                               |
| Độc lập                                              | Tích hợp vào html để thực thi              |
| Strongly typed phải chọn datatype khi declare và use | Loosely typed ko quan tâm datatype declare |
| Compiled trước khi thực thi                          | Tích hợp vào html để thực thi              |
| Thục hiện task phức tạp = cách sử dụng multithread   | Không thể thực hiện task phức tạp          |
| Yêu cầu một lượng lớn memory                         | Không yêu cầu một lượng lớn memory         |
