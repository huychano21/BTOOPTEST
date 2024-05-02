# Chương trình quản lý môn học

- Date : 02/05/2024 <br/>
Tác giả: Đỗ Duy Anh (B9D54), Trần Quang Huy (B9D54)
<br/><br/>

Chương trình Quản lý Đăng kí Môn học là một ứng dụng được thiết kế để quản lý sinh viên, quản lý học phần, thực hiện đăng kí môn học và thống kê các hoạt động liên quan đến môn học trong một trường đại học. Chương trình cung cấp một giao diện đơn giản và dễ sử dụng, cho phép người dùng thực hiện các tác vụ quản lý dễ dàng.

Khái quát về chương trình quản lý môn học tại một học viện/đại học. 
- Mô tả: Chương trình có 02 loại đối tượng quản lý là học phần (mỗi môn học có thể có nhiều học phần với các lớp học khác nhau) và sinh viên (có thể đăng ký nhiều học phần). Mỗi đối tượng sẽ quản lý ở các trường thông tin riêng trên 2 giao diện khác nhau và liên kết với nhau nhờ chức năng đăng ký môn học (đăng ký môn học cho học viên, tiến hành phân vào các lớp học cụ thể).
- Danh sách các sinh viên sẽ được hiển thị trong bảng danh sách. Khi lựa chọn vào một đối tượng trong bảng, các thông tin sẽ hiện lên khu vực hiển thị. Tương tự với danh sách học phần.
- Các chức năng cơ bản: Thêm, xoá, sửa, làm mới, phân lớp (Để phân chia sinh viên vào các lớp học cụ thể theo từng môn đã chọn).
- Các chức năng khác: Tìm kiếm (theo ký tự), sắp xếp (theo các tiêu chí khác nhau), thống kê tình trạng đăng ký môn, in danh sách thống kê về sinh viên/ học phần (Dưới dạng file Excel trong giao diện thống kê).


## 1. Cài đặt
 - Để chạy chương trình, bạn cần cài đặt Java và Java Swing.
 - Cài đặt NetBeans 21 và tối thiểu JDK11 để chạy chương trình.
 - Để chạy file .jar đã được build (đóng gói), bạn cần truy cập vào Target, sau đó nháy đúp chuột vào App.jar. Hoặc chuột phải vào vùng trống trong Target, chọn *Open in Termial*, sau đó nhập "java -jar App.jar" vào màn hình console và ấn Enter. 


## 2. Các thư mục và tệp tin của dự án
 - README.md: tệp chứa thông tin giới thiệu, cách khởi chạy và hướng dẫn sử dụng chương trình.
 - Student.xml: tệp tin để lưu trữ và truy xuất dữ liệu của sinh viên. Khi ứng dụng được khởi động, các thông tin của từng sinh viên được lưu trữ trong file này sẽ được tải vào ứng dụng và sử dụng trong suốt quá trình chạy của ứng dụng đối với sinh viên tương ứng, đồng thời, ứng dụng cũng sẽ thực hiện ghi thông tin vào file này để phục vụ mục đích lưu trữ lâu dài.
 - Subject.xml: tệp tin để lưu trữ và truy xuất dữ liệu của các môn học. Khi ứng dụng được khởi động, các thông tin được lưu trữ trong file này sẽ được tải vào ứng dụng và sử dụng trong suốt quá trình chạy của ứng dụng đối với môn học tương ứng.
 - pom.xml: tệp tin cấu hình Maven (Maven Project Object Model), chứa thông tin về các thư viện và Framework được sử dụng trong dự án, cách đóng gói ứng dụng, các plugin được sử dụng để biên dịch, kiểm tra và triển khai ứng dụng.
 - lib: thư mục chứa các *thư viện* (libraries) và file *JAR* (Java Archive) được sử dụng trong dự án, đó các file thực thi, chứa các class, interfaces và các tài nguyên được sử dụng trong dự án.
 - target: thư mục chứa tất cả các file được tạo ra bởi quá trình biên dịch và đóng gói, bao gồm các file .class, .jar, các file tài nguyên và các file khác liên quan đến quá trình triển khai ứng dụng. Nó được tự động tạo ra bởi Maven và được sử dụng để triển khai ứng dụng.
 - src: chứa 2 thư mục con là test và main.
   + test: thư mục chứa các unit test để kiểm tra tính đúng đắn của mã nguồn trong thư mục main. Đây là nơi để viết các test case, đảm bảo rằng các phần của mã nguồn hoạt động đúng và cho phép kiểm tra tính đúng đắn của ứng dụng trong quá trình phát triển.
   + main: thư mục chứa mã nguồn chính của ứng dụng để triển khai tính năng và chức năng của ứng dụng(có file resources để lưu trữ các icon, hình ảnh của dự án...).



## 3. Hướng dẫn sử dụng và miêu tả cụ thể chức năng của code
### *3.1 Chạy chương trình*

1. Chạy chương trình bằng cách mở file App.java trong thư mục com.mycompany.quanlydancu_ghp, click chuột phải và chọn Run Project (F6) để khởi chạy chương trình. Giao diện Login sẽ được hiển thị. 

![Login](./task/Loginview.PNG "Login")


2. Giao diện Login: Nhập email "hvan@edu.vn" và mật khẩu "matkhau", sau đó nhấn nút "Login" hoặc ấn Enter để truy cập giao diện chính. 

![Login](./task/LoginviewAccout.PNG "LoginAccout")

Nếu nhập sai email hay mật khẩu sẽ có thông báo "Email không tồn tại" hoặc "Mật khẩu không đúng" trong ô nhập thông tin.


3. Sau khi đăng nhập thành công, chương trình sẽ hiển thị một bảng chọn bốn dịch vụ cơ bản.
   - Lựa chọn *"Thông tin sinh viên"* để hiển thị giao diện quản lý sinh viên.
   - Lựa chọn *"Thông tin học phần"* để hiển thị giao diện quản lý các học phần.
   - Lựa chọn *"Đăng ký môn học"* để thực hiện chức năng đăng ký môn, phân lớp học cho sinh viên.
   - Lựa chọn *"Thống kê"* để hiển thị thông tin thống kê cơ bản về 2 đối tượng chính là sinh viên và môn học, trong đó cập nhật trạng thái có thêm cập nhật trạng thái đăng ký môn của sinh viên và trạng thái đầy hay trống của từng học phần.
    
![OptionView](./task/OptionView.PNG "OptionView")


4. *Chú ý các thông tin cơ bản của 4 giao diện*: 
   - Tại 02 giao diện quản lý: *"Quản lý sinh viên"* và *"Quản lý môn học"*:
      + Các trường thông tin Mã sinh viên, Tên sinh viên, Địa chỉ (đối với quản lý sinh viên) và Tên môn học, Mã lớp, Giảng viên, Số lượng sinh viên tối đa (đối với quản lý học phần) đều được nhập được nhập từ bàn phím. 
      + Trường thông tin "Ngày sinh" có thể nhập từ bàn phím theo định dạng dd/mm/yyyy hoặc có thể lựa chọn từ lịch. Các trường "Giới tính", "Chuyên ngành", "Kỳ học" (đối với QLSV) và trường "Số tín chỉ", "Loại lớp", "Hình thức thi" (Đối với QLHP) là các trường lựa chọn. Trường thông tin "Số tín chỉ giới hạn" phụ thuộc vào kỳ học và không thể sửa đổi (*12 tín/kỳ đối với năm nhất, 14 tín/kỳ đối với năm 2, 16 tín/kỳ đối với năm 3, 18 tín/ kỳ với năm 4 và 20 tín/kỳ đối với năm 5, quy ước mỗi năm có 2 kỳ*).
      + Các trường "Mã sinh viên" và "Mã học phần" là các khóa (hay còn gọi là các *key*), không được trùng lặp với các giá trị có trước đó. 
   - Ở giao diện "Đăng ký môn học" và "Thống kê" chỉ cần thực hiện thao tác từ chuột, không cần phải thực hiện thao tác từ bàn phím    

### *3.2, Thêm, sửa, xóa, làm mới, sắp xếp sinh viên/ môn học cho giao diện "**Quản lý sinh viên**" và "**Quản lý môn học**".*

#### Đối với giao diện "Quản lý sinh viên"

 - Thêm sinh viên: Để thêm sinh viên phải nhập đầy đủ thông tin như: Mã sinh viên, Tên sinh viên, Ngày sinh, Giới tính, Địa chỉ, Chuyên ngành, Kỳ học và nhấn nút: **Thêm**.

-Thêm sinh viên
![Add](./task/StudentViewAdd1.PNG "Add")
Sau khi thêm thành công
![Add](./task/StudentViewAdd2.PNG "Add")

 - Sửa thông tin sinh viên: Để sửa thông tin sinh viên, bạn chọn sinh viên cần sửa trong danh sách, chỉnh sửa thông tin và nhấn nút: **Cập nhật**.

 -Sửa thông tin sinh viên
![Edit](./task/StudentViewEdit1.PNG "Edit")
Sau khi cập nhật thành công
![Edit](./task/StudentViewEdit2.PNG "Edit")

 - Xóa sinh viên: Tương tự như các thao tác trên, để xóa một sinh viên, bạn chọn sinh viên cần xóa trong danh sách và nhấn nút: **Xóa**.

 -Xóa sinh viên
![Delete](./task/StudentViewDelete1.PNG "Delete")
Sau khi xóa thành công
![Delete](./task/StudentViewDelete2.PNG "Delete")

- Chức năng sắp xếp sinh viên theo thứ tự bảng chữ cái

![Sort](./task/StudentViewSort1.PNG "Sort")
Sau khi thực hiện sắp xếp
![Sort](./task/StudentViewSort2.PNG "Sort")


 - Click nút **Làm mới** để làm mới các trường thông tin.

 -Chức năng "Làm mới"
![Refresh](./task/StudentViewRefresh1.PNG "Refresh")
Kết quả thu được
![Refresh](./task/StudentViewRefresh2.PNG "Refresh")


- Chú ý:
    + Nút xóa, cập nhật chỉ khả dụng khi đã chọn một sinh viên từ bảng.
    + Để thêm một sinh viên khi đang chọn một sinh viên khác thì cần nhấn nút làm mới để làm mới trường thông tin trước khi nhập thông tin cho một sinh viên mới.
    + Ngoài ra, chương trình còn bổ sung thêm các chức năng xử lý thông báo lỗi khác như nhập thông tin các trường không hợp lệ (định ngày ngày tháng năm, Số nguyên,....) hay khi nhập thiếu một trường thông tin bắt buộc nào đó.   

#### Đối với giao diện "Quản lý học phần"
- Các chức năng Thêm, Xóa, Cập nhật, Làm mới và Sắp xếp (sắp xếp theo tên, có biểu tượng A->Z) hoạt động tương tự như phần *Quản lý sinh viên*.

-Tổng quan
![Subject](./task/SjViewOverView.PNG "Subject")

- Chức năng Sắp xếp theo số lượng sinh viên đã đăng kí: Tương tự như chức năng sắp xếp theo tên, chức năng trên sắp xếp môn học theo số lượng sinh viên đã đăng ký theo thứ tự giảm dần.

-Sắp xếp số lượng sinh viên đăng ký
![Subject](./task/SjViewSortByRegisStudent.PNG "Sort Registed Student")

### *3.3, Tìm kiếm sinh viên*
 1. Chọn tìm kiếm theo Tên sinh viên, hoặc theo Mã sinh viên,hoặc chuyên ngành (đối với giao diện quản lý sinh viên) và theo Tên môn học, theo Mã học phần (đối với giao diện quản lý học phần) bằng cách click vào *Checkbox* tương ứng.

 2. Nhập từ khóa tìm kiếm vào ô tìm kiếm và nhấn nút **Tìm kiếm**.
   
   -Thực hiện tìm kiếm
   ![Search](./task/StudentViewSearch1.PNG "Search")
   Kết quả thu được
   ![Search](./task/StudentViewSearch2.PNG "Search")


   
 3. Kết quả tìm kiếm sẽ được hiển thị trong bảng danh sách. Nếu giá trị tìm kiếm không hợp lệ hoặc không tìm thấy kết quả phù hợp sẽ trả về hộp thoại thông báo "Không có kết quả phù hợp".

 4. Để tìm kiếm các kết quả khác hoặc thoát chế độ tìm kiếm cần nhấn vào biểu tượng "Dấu X" trên ô tìm kiếm.

 
### *3.4 Thực hiện đăng ký môn học và chức năng **Phân lớp*** 
 - Giao diện đăng kí môn học sẽ hiển thị ra 3 phần riêng biệt: *Danh sách sinh viên đăng ký môn*, các *thông tin sinh viên và thông tin học phần*, *Danh sách học phần sinh viên đã đăng kí*.

![Registed](./task/RegisView.PNG "Overview Registed Student")

- Để thực hiện đăng ký môn học, cần chọn một sinh viên từ danh sách, sau đó, chọn thông tin học phần mà sinh viên đó muốn đăng ký, chọn loại lớp của học phần đó (lớp Lý thuyết hay Thực hành, nếu có) rồi ấn "**Thêm**". 

- Lưu ý: 
   + Tổng số tín chỉ đăng ký phải không vượt quá số tín chỉ giới hạn của sinh viên đó, nếu không chương trình sẽ báo lỗi.
   + Chương trình có cơ chế kiểm soát số lượng sinh viên với từng lớp cho mỗi học phần, do đó, không thể thực hiện thêm những học phần không còn lớp trống.

![DKM](./task/RegisViewAdd1.PNG "Dang ki mon")
Kết quả thu được:
![DKM](./task/RegisViewAdd2.PNG "Dang ki mon thanh cong")
Lỗi khi tổng số TC vượt quá số TC giới hạn
![DKM](./task/RegisViewError1.PNG "Vuot qua so TC gioi han")
Lỗi hết lớp cho học phần nào đó
![DKM](./task/RegisViewError2.PNG "Học phần hết lớp trống")


- Để thực hiện *Phân lớp*, cần chọn một môn học từ danh sách môn học đã đăng ký của một sinh viên, sau đó ấn **Phân lớp**. Chương trình sẽ tự động thêm sinh viên vào các lớp học còn trống. 

![DKM](./task/RegisViewPL1.PNG "Dang ki mon")
Kết quả thu được:
![DKM](./task/RegisViewPL2.PNG "Dang ki mon thanh cong") 

- Lưu ý: Các chức năng "Xóa", "Làm mới" trong giao diện *Đăng ký môn học* hoạt động tương tự các chức năng trên trong giao diện *Quản lý sinh viên* và *Quản lý học phần*.


### *3.5 Giao diện Thống kê và chức năng lập **Biểu đồ thống kê**, **In danh sách sinh viên** và  **In danh sách học phần** dưới dạng file Excel.*

- Giao diện *Thống kê* sẽ hiển thị 2 phần thống kê cơ bản về 2 đối tượng quản lý là "Sinh viên" và "Học phần": 
   + Phần thống kê sinh viên sẽ hiển thị các thống kê cơ bản bao gồm: Tổng số sinh viên; tổng số sinh viên đã đăng ký môn và chưa đăng ký môn; tỉ lệ sinh viên đăng ký môn và chưa đăng ký môn; sinh viên nào của chuyên ngành gì tích lũy được nhiều tín chỉ nhất; Trung bình số TC mà mỗi sinh viên đăng kí là bao nhiêu.
   + Phần thống kê học phần sẽ hiển thị các số liệu thống kê về: Tổng số môn học; tổng số lớp học hiện có; bao nhiêu lớp đầy và bao nhiêu lớp còn trống; tỉ lệ lớp học đã đầy và còn trống; môn học nào nhiều lớp nhất; môn học nào có nhiều sinh viên đăng ký nhất.

   ![Stastic](./task/StasticOverView.PNG "Stastic Overview")

- Đối với chức năng **Lập biểu đồ thống kê**.
   + Hiển thị các thông kê cơ bản về tỉ lệ sinh viên đã đăng ký của mỗi môn học.
   + Biểu đồ được thể hiện dưới dạng cột, chú thích bên phải biểu đồ với các môn học là các màu tương ứng thể hiện trên biểu đồ

![Stastic](./task/StasticChart.PNG "Ve bieu do")
- Đối với chức năng **In danh sách sinh viên** và **In danh sách học phần**
   + Chương trình sẽ tự động xuất ra file Excel thuận thiện cho công việc, thao tác văn phòng.
   + Mỗi file Excel chứa các trường thông tin cơ bản của cả một trong hai đối tượng quản lý (sinh viên hoặc môn học), trong đó bổ sung thêm trường "Các môn học đã đăng ký" với sinh viên và cập nhật trạng thái (còn trống hay đã đầy) đối với từng môn học. 

![Stastic](./task/StasticStudentExcel.PNG "Print Excel Student")
![Stastic](./task/StasticSubjectExcel.PNG "Print Excel Subject")


### *3.6 Chức năng **Quay lại** và **Đăng xuất***
- Có thể sử dụng chức năng *Quay lại* ở bất kỳ giao diện nào tại chương trình. Khi sử dụng chức năng quay lại tại "dấu mũi tên quay lại tại góc phía trên bên trái màn hình". Các trang giao diện sẽ trở lại trang giao diện trước đó.
   ![Return](./task/Return.PNG "Return")

   ![Logout](./task/Logout.PNG "Logout")

### *3.7 Giao diện được thiết kế bắt mắt, thuận tiện sử dụng*
- Các nút (button) đều được thiết kế lại, bo tròn các góc, thay đổi màu, và sử dụng hiệu ứng tô màu cho button. 
![Design](./task/Design.PNG "Design")

- Các panel đã được điều chỉnh Background tránh đơn điệu và đảm bảo không rối, nổi bật được các thông tin cần thiết, các frame đều được thay đổi iconImage thống nhất.


## 4. Phần kết
- Mặc dù chương trình đã hoạt động khá ổn định và thể hiện được thế mạnh trong thực hiện chức năng quản lý và đăng ký môn. Tuy nhiên, trong quá trình chạy không thể có những sai sót. Mọi ý kiến đóng góp để hoàn thiện xin gửi về địa chỉ mail: tranhuyak31cvals@gmail.com hoặc duyanh21062004@gmail.com. 

- Vui lòng không sử dụng vào mục đích thương mại hoặc các mục đích khác khi chưa có sự đồng ý của tác giả/nhóm tác giả.

**Xin chân thành cảm ơn!**


