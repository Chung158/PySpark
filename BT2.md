# 1.Spark Properties:
  Spark Properties kiểm soát hầu hết các tham số ứng dụng và có thể được thiết lập bằng cách sử dụng đối tượng `SparkConf` hoặc thông qua các thuộc tính hệ thống Java.
  
  Spark Properties kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được cài đặt trực tiếp trên `SparkConf` được chuyển tới `SparkContext`. `SparkConf` cho phép bạn định cấu hình một số thuộc tính phổ biến (ví dụ: URL chính và tên ứng dụng), cũng như các cặp khóa-giá trị tùy ý thông qua phương thức `set()` . Ví dụ: 
    - Có thể khởi tạo một ứng dụng với hai luồng như sau: Lưu ý rằng chúng ta chạy với local[2], nghĩa là hai luồng - đại diện cho sự song song “tối thiểu”, có thể giúp phát hiện các lỗi chỉ tồn tại khi chạy trong ngữ cảnh phân tán.   
 
 ```Javascript
    val conf = new SparkConf()
                  .setMaster("local[2]")
                  .setAppName("CountingSheep")
    val sc = new SparkContext(conf)
   ```
   
# 2.Spark RDD:
  <p><b>Resilient Distributed Datasets</b> <i>(RDD)</i> là một cấu trúc dữ liệu cơ bản của Spark. Nó là một tập hợp bất biến phân tán của một đối tượng. Mỗi <i>dataset</i> trong <i>RDD</i> được chia ra thành nhiều phần vùng <i>logical</i>. Có thể được tính toán trên các node khác nhau của một cụm máy chủ <i>(cluster)</i>.</p>

  <p><i>RDDs</i> có thể chứa bất kỳ kiểu dữ liệu nào của <i>Python, Java</i> hoặc đối tượng <i>Scala</i>, bao gồm các kiểu dữ liệu do người dùng định nghĩa. Thông thường, <i>RDD</i> chỉ cho phép đọc, phân mục tập hợp của các bản ghi. <i>RDDs</i> có thể được tạo ra qua điều khiển xác định trên dữ liệu trong bộ nhớ hoặc <i>RDDs</i>, <i>RDD</i> là một tập hợp có khả năng chịu lỗi mỗi thành phần có thể được tính toán song song.</p>

  Có hai cách để tạo <i>RDDs</i>:
- Tạo từ một tập hợp dữ liệu có sẵn trong ngôn ngữ sử dụng như Java, Python, Scala.
- Lấy từ dataset hệ thống lưu trữ bên ngoài như HDFS, Hbase hoặc các cơ sở dữ liệu quan hệ.
# 3.Spark DataFrame:
