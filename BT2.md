# 1.Spark Properties:
  Spark Properties kiểm soát hầu hết các tham số ứng dụng và có thể được thiết lập bằng cách sử dụng đối tượng `SparkConf` hoặc thông qua các thuộc tính hệ thống Java.
  
  Spark Properties kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được cài đặt trực tiếp trên `SparkConf` được chuyển tới `SparkContext`.`SparkConf` cho phép bạn định cấu hình một số thuộc tính phổ biến (ví dụ: URL chính và tên ứng dụng), cũng như các cặp khóa-giá trị tùy ý thông qua phương thức `set()` .
    
    Ví dụ: 
    - Có thể khởi tạo một ứng dụng với hai luồng như sau: Lưu ý rằng chúng ta chạy với local[2], nghĩa là hai luồng - đại diện cho sự song song “tối thiểu”, có thể giúp phát hiện các lỗi chỉ tồn tại khi chạy trong ngữ cảnh phân tán.
    
  ```Javascript
    val conf = new SparkConf()
                  .setMaster("local[2]")
                  .setAppName("CountingSheep")
    val sc = new SparkContext(conf)
   ```
   
# 2.Spark RDD:

# 3.Spark DataFrame:
