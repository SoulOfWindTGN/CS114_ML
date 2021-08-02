<p align="center">
  <img src="https://www.uit.edu.vn/sites/vi/files/banner_uit_0.png" title="avatar_UIT">
</p>

<h1 align="center">
    
  **BÁO CÁO ĐỒ ÁN CUỐI KỲ**
  
  **APPLICATION TO CATEGORIZE DRAGON FRUIT EXPORTAION**
  </h1>

## Giảng viên hỗ trợ:
    PGS.TS. Lê Đình Duy - duyld@uit.edu.vn
    Ths. Phạm Nguyễn Trường An - truonganpn@uit.edu.vn
 
## Thành viên thực hiện
| STT | Họ tên | MSSV | Vai trò | E-mail | Github |
| :---: | --- | --- | --- | --- | --- |
| 1 | Trần Phan Nhật Kha | 19521655 | Nhóm trưởng | 19521655@gm.uit.edu.vn | [trankha1655](https://github.com/trankha1655) |
| 2 | Trần Gia Nghĩa | 19521901 | Thành viên | 19521901@gm.uit.edu.vn | [SoulOfWindTGN](https://github.com/SoulOfWindTGN) |
| 3 | Võ Tá Lâm | 19521744 | Thành viên | 19521744@gm.uit.edu.vn | [volam2001](https://github.com/volam2001) |

# Chương 1: Tổng quan
## 1.1 Mô tả bài toán

Việt Nam hiện trồng rất nhiều loại trái cây thơm ngon, chất lượng cao đã được xuất khẩu, góp phần mang lại các giá trị cao về thương mại dịch vụ Logistic. Trong đó, thanh long hiện được đánh giá khá cao bởi tiềm năng rất tốt. Thanh long Việt Nam đang có tổng diện tích trồng và cho năng suất cao nhất châu Á. Song song đó, nước ta cũng là quốc gia xuất khẩu thanh long đứng hàng đầu thế giới. Thanh long là loại trái cây có tỷ trọng xuất khẩu cao nhất trong 3 tháng đầu năm 2021 của nước ta với tỷ trọng 34.1% (Nguồn: [Xuất khẩu rau quả tăng 9,5% trong 4 tháng đầu năm](https://vietnambiz.vn/xuat-khau-rau-qua-tang-95-trong-4-thang-dau-nam-20210513154103216.htm))
<p align="center">
  <img src="https://cdn.vietnambiz.vn/171464876016439296/2021/5/13/135-rau-qua-1620894667305280819784.jpg">
</p>

Việc xuất khẩu trái cây trong đó có thanh long cũng được lựa chọn khắc khe qua các tiêu chí phân loại phù hợp vói nhu cầu của từng thị trường. Để biết thêm chi tiết, có thể tham khảo bài viết sau: [TIÊU CHUẨN CỦA QUẢ THANH LONG XUẤT KHẨU SANG THỊ TRƯỜNG HIỆN NAY](https://ratracosolutions.com/n/tieu-chuan-thanh-long-xuat-khau-sang-thi-truong/)

Hiện nay, các vựa thanh long truyền thống trên cả nước phần lớn vẫn chưa cơ giới hóa khâu phân loại mà cần khá nhiều nhân lực cho khâu này. Đặc biệt trong tình hình dịch bệnh Covid 19 đang diễn biến khá phức tạp, khi nhiều tỉnh thành phía nam phải thực hiện giãn cách xã hội ngay trong mùa thu hoạch thanh long khiến cho việc tập trung nhiều nhân lục tại một địa điểm rất khó khăn. [Sản lượng thanh long ở nước ta tăng rất nhanh](https://nongnghiep.vn/viet-nam-tiep-tuc-la-nha-san-xuat-thanh-long-hang-dau-d264006.html) do nhu cầu xuất khẩu đến các nước ngày càng cao đòi hỏi cần cơ giới hóa nhiều quy trình nhằm tăng năng suất cũng như rút ngắn thời gian sản phẩm đến tay người tiêu dùng, trong đó có khâu phân loại.

🠊 ***Vì những nhu cầu thực tế trên, chúng tôi nghiên cứu phương pháp phân loại trái thanh long thông qua hình ảnh bằng machine learning***

**1. Input của bài toán**

Ba ảnh trích xuất từ 3 góc của camera với độ phân giải mỗi ảnh là 720p (1280 x 720 pixels). Mỗi ảnh chụp một mặt của cùng một quả thanh long

<p float="left">
  <img src="https://github.com/trankha1655/CS114_ML/blob/main/Dataset/img/label_1/Binh_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" />
  <img src="https://github.com/trankha1655/CS114_ML/blob/main/Dataset/img/label_1/Kha_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" /> 
  <img src="https://github.com/trankha1655/CS114_ML/blob/main/Dataset/img/label_1/Ti_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" />
</p>

Input ở trên dựa vào ngữ cảnh quả thanh long trên băng chuyền rửa quả thanh long. Từng trái thanh long sẽ lần lượt đi theo băng chuyền đi qua khu vực phân loại có đặt sẵn các camera với 2 camera nằm phía trên bên trái và bên phải cùng với một camera nằm ở dưới có ống kính hướng lên. Ánh sáng của ảnh được quay lúc trời quang đãng, ánh sáng rõ ràng, không quá chói.

**2. Output của bài toán**

Loại của quả thanh long (Ở bài toán này sẽ có 3 loại)

Dựa trên output có thể xây dựng hệ thống phân loại khi quả thanh long nằm trên băng chuyền ngay sau giai đoạn rửa sạch và làm khô. Ở khu vực phân loại được bố trí các camera, mỗi trái thanh long đi qua tầm quan sát của camera sẽ được thu nhận tín hiệu và xử lý để phân loại, sau đó thanh long sẽ được đưa vào một trong ba làn đi vào ba kho khác nhau.

## 1.2 Mô tả dữ liệu
- Dữ liệu của bài toán nằm ở một số vườn chuyên canh thanh long ở Bình Thuận. Trong quá trình thu thập dữ liệu, nhóm gặp phải nhiều khó khăn như việc chờ đợi mùa thu hoạch thanh long, thanh long khi được chụp phải vừa được cắt từ cây xuống để đảm bảo độ tươi (do các vựa thường phân loại ngay sau khi cắt từ cây xuống một khoảng thời gian không lâu) nên cần xin phép chủ vườn không gian và thời gian để thu thập dữ liệu.
- Bộ dữ liệu thanh long ở Việt Nam hiện chưa có ai thu thập nên số lượng dữ liệu mà nhóm có tương đối hạn chế do toàn bộ dữ liệu là tự thu thập và xử lý. Mục đích chính của việc tự thu thập dữ liệu của nhóm cũng xuất phát từ các đặc trưng sinh học nổi bật của giống thanh long ở Việt Nam có thể khác với các dữ liệu thanh long có sẵn của nước ngoài và đồng thời phù hợp ngữ cảnh ứng dụng của bài toán.

# Chương 2: Các nghiên cứu trước
