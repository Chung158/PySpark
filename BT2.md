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
   Tham khảo:
   * [Spark Properties](https://apache.googlesource.com/spark/+/master/docs/configuration.md)
# 2.Spark RDD:
  <p><b>Resilient Distributed Datasets</b> <i>(RDD)</i> là một cấu trúc dữ liệu cơ bản của Spark. Nó là một tập hợp bất biến phân tán của một đối tượng. Mỗi <i>dataset</i> trong <i>RDD</i> được chia ra thành nhiều phân vùng <i>logical</i>. Có thể được tính toán trên các node khác nhau của một cụm máy chủ <i>(cluster)</i>.</p>

  <p><i>RDDs</i> có thể chứa bất kỳ kiểu dữ liệu nào của <i>Python, Java</i> hoặc đối tượng <i>Scala</i>, bao gồm các kiểu dữ liệu do người dùng định nghĩa. Thông thường, <i>RDD</i> chỉ cho phép đọc, phân mục tập hợp của các bản ghi. <i>RDDs</i> có thể được tạo ra qua điều khiển xác định trên dữ liệu trong bộ nhớ hoặc <i>RDDs</i>, <i>RDD</i> là một tập hợp có khả năng chịu lỗi mỗi thành phần có thể được tính toán song song.</p>

  Có hai cách để tạo <i>RDDs</i>:
- Tạo từ một tập hợp dữ liệu có sẵn trong ngôn ngữ sử dụng như Java, Python, Scala.
- Lấy từ dataset hệ thống lưu trữ bên ngoài như HDFS, Hbase hoặc các cơ sở dữ liệu quan hệ.

 Tham khảo:
  * [Apache Spark RDD](https://laptrinh.vn/books/apache-spark/page/apache-spark-rdd).
  
# 3.Spark DataFrame:
DataFrames thường đề cập đến một cấu trúc dữ liệu, về bản chất là dạng bảng. Nó đại diện cho các hàng, mỗi hàng bao gồm một số quan sát. Các hàng có thể có nhiều định dạng dữ liệu (không đồng nhất), trong khi một cột có thể có dữ liệu cùng loại (đồng nhất). DataFrames thường chứa một số siêu dữ liệu ngoài dữ liệu; ví dụ, tên cột và hàng.
Chúng ta có thể nói rằng DataFrames không là gì, ngoài các cấu trúc dữ liệu 2 chiều, tương tự như bảng SQL hoặc bảng tính. Bây giờ, hãy tiếp tục với Hướng dẫn về khung dữ liệu PySpark này và hiểu lý do tại sao chính xác chúng ta cần Pyspark Dataframe.
  ### Lợi ích khi sử dụng Dataframe:
  
 1. Xử lý dữ liệu có cấu trúc và bán cấu trúc: 
        DataFrames được thiết kế để xử lý một tập hợp lớn dữ liệu có cấu trúc cũng như bán cấu trúc . Các quan sát trong Spark DataFrame được tổ chức dưới các cột được đặt tên, giúp Apache Spark hiểu sơ đồ của Dataframe. Điều này giúp Spark tối ưu hóa kế hoạch thực hiện trên các truy vấn này. Nó cũng có thể xử lý petabyte dữ liệu.
 2. Cắt lát và thái hạt lựu : 
        API DataFrames thường hỗ trợ các phương thức phức tạp để cắt và xử lý dữ liệu. Nó bao gồm các hoạt động như "chọn" các hàng, cột và ô theo tên hoặc theo số, lọc ra các hàng, v.v. Dữ liệu thống kê thường rất lộn xộn và chứa nhiều giá trị thiếu và không chính xác và vi phạm phạm vi. Vì vậy, một tính năng cực kỳ quan trọng của DataFrames là quản lý rõ ràng dữ liệu bị thiếu.
 3. Nguồn dữ liệu: 
        DataFrames đã hỗ trợ cho một loạt các định dạng và nguồn dữ liệu, chúng ta sẽ xem xét vấn đề này sau trong hướng dẫn Pyspark DataFrames này. Họ có thể lấy dữ liệu từ nhiều nguồn khác nhau.
 4. Hỗ trợ nhiều ngôn ngữ: 
        Nó có hỗ trợ API cho các ngôn ngữ khác nhau như Python, R, Scala, Java, giúp mọi người có nền tảng lập trình khác nhau dễ sử dụng hơn.

Tham khảo:
 * [Hướng dẫn PySpark DataFrame: Giới thiệu về DataFrames](https://helpex.vn/article/huong-dan-pyspark-dataframe-gioi-thieu-ve-dataframes-5c6b21e6ae03f628d053c29e)
 * [Xử lý dữ liệu với Spark Dataframe](https://codetudau.com/xu-ly-du-lieu-voi-spark-dataframe/index.html)
