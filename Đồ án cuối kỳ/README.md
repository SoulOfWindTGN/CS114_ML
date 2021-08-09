<p align="center">
  <img src="https://www.uit.edu.vn/sites/vi/files/banner_uit_0.png" title="avatar_UIT">
</p>

<h1 align="center">
    
  **BÁO CÁO ĐỒ ÁN CUỐI KỲ**
  
  **APPLICATION TO CATEGORIZE DRAGON FRUIT EXPORTAION**
  </h1>

## Giảng viên hướng dẫn:
    PGS.TS. Lê Đình Duy - duyld@uit.edu.vn
    Ths. Phạm Nguyễn Trường An - truonganpn@uit.edu.vn
 
## Thành viên thực hiện
| STT | Họ tên | MSSV | Vai trò | E-mail | Github |
| :---: | --- | --- | --- | --- | --- |
| 1 | Trần Phan Nhật Kha | 19521655 | Nhóm trưởng | 19521655@gm.uit.edu.vn | [trankha1655](https://github.com/trankha1655) |
| 2 | Trần Gia Nghĩa | 19521901 | Thành viên | 19521901@gm.uit.edu.vn | [SoulOfWindTGN](https://github.com/SoulOfWindTGN) |
| 3 | Võ Tá Lâm | 19521744 | Thành viên | 19521744@gm.uit.edu.vn | [volam2001](https://github.com/volam2001) |


## **overwrite**
* [Problem](#chương-1-tổng-quan)
* [Dataset](#chương-3-xây-dựng-bộ-dữ-liệu)
* [Method](#)
* [Predict & evaluate](#)
* [References](#)

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
  <img src="Dataset/img/label_1/Binh_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" />
  <img src="Dataset/img/label_1/Kha_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" /> 
  <img src="Dataset/img/label_1/Ti_s%20cam/Binh_cam.00_06_31_17.Still040.jpg" width="300" />
</p>

Input ở trên dựa vào ngữ cảnh quả thanh long trên băng chuyền rửa quả thanh long. Từng trái thanh long sẽ lần lượt đi theo băng chuyền đi qua khu vực phân loại có đặt sẵn các camera với 2 camera nằm phía trên bên trái và bên phải cùng với một camera nằm ở dưới có ống kính hướng lên. Ánh sáng của ảnh được quay lúc trời quang đãng, ánh sáng rõ ràng, không quá chói.

**2. Output của bài toán**

Loại của quả thanh long (Ở bài toán này sẽ có 3 loại)

Dựa trên output có thể xây dựng hệ thống phân loại khi quả thanh long nằm trên băng chuyền ngay sau giai đoạn rửa sạch và làm khô. Ở khu vực phân loại được bố trí các camera, mỗi trái thanh long đi qua tầm quan sát của camera sẽ được thu nhận tín hiệu và xử lý để phân loại, sau đó thanh long sẽ được đưa vào một trong ba làn đi vào ba kho khác nhau.

## 1.2 Mô tả dữ liệu

- Dữ liệu của bài toán nằm ở một số vườn chuyên canh thanh long ở Bình Thuận. Trong quá trình thu thập dữ liệu, nhóm gặp phải nhiều khó khăn như việc chờ đợi mùa thu hoạch thanh long, thanh long khi được chụp phải vừa được cắt từ cây xuống để đảm bảo độ tươi (do các vựa thường phân loại ngay sau khi cắt từ cây xuống một khoảng thời gian không lâu) nên cần xin phép chủ vườn không gian và thời gian để thu thập dữ liệu.
- Bộ dữ liệu thanh long ở Việt Nam hiện chưa có ai thu thập nên số lượng dữ liệu mà nhóm có tương đối hạn chế do toàn bộ dữ liệu là tự thu thập và xử lý. Mục đích chính của việc tự thu thập dữ liệu của nhóm cũng xuất phát từ các đặc trưng sinh học nổi bật của giống thanh long ở Việt Nam có thể khác với các dữ liệu thanh long có sẵn của nước ngoài và đồng thời phù hợp ngữ cảnh ứng dụng của bài toán.

# Chương 2: Các nghiên cứu trước

Hiện nay, trong lĩnh vực thị giác máy tính nói riêng hay lĩnh vực máy học nói chung, các bài toán phân loại (classification) và nhận diện vật thể (object detection) có rất nhiều bài toán được đặt ra và đã được giải quyết. Những bài toán này được giải quyết bằng các mô hình machine learning và deep learning phổ biến như YOLO, VGG-16, Resnet-50 dựa trên kiến trúc mạng CNN (Convolutional Neural Network) và nhiều mô hình với các kiến trúc khác.

Bài toán của nhóm đặt ra là bài toán phân loại dựa vào chi tiết đặc trưng của vật thể (khá giống với nhận diện khuôn mặt) dành cho nông sản (trái thanh long). Với các bài toán về phân loại nông sản hiện nay vẫn chưa được nghiên cứu nhiều nên nguồn tham khảo thông qua các bài báo khoa học rất khó tìm, nên nhóm vẫn chưa tìm thấy các kết quả nghiên cứu của tiền nhân cho bài toán phân loại thanh long.

Trong quá trình nghiên cứu phương pháp, nhóm có đọc qua một paper về [Multi-View Image Classification](https://towardsdatascience.com/multi-view-image-classification-427c69720f30) có phương pháp nghiên cứu tương tự với phương pháp mà nhóm đề xuất. Bài toán được ứng dụng trong paper này là bài toán nhận diện vật thể với performance đạt 98%

<p align="center">
  <img src="https://miro.medium.com/max/875/1*uyK6DmBr1OgrPYz-kKE0wQ.png">
<p align="center">
  <em> 2.1. Multi-view image classification</em>
</p>

# Chương 3: Xây dựng bộ dữ liệu

## Thu thập dữ liệu

1. Để mô phỏng cho các ứng dụng phân loại thực tế trong xí nghiệp và vựa trái cây có băng chuyền, nhóm quyết định hàn khung sắt mô phỏng băng chuyền, thiết lập 3 vị trí camera cố định quay 3 mặt của trái thanh long.
2. Đặt lần lượt từng quả thanh long lên băng chuyền mô phỏng trong lúc camera đang quay.
3. Trích xuất video từ 3 camera, sau đó đồng bộ 3 đoạn video theo cùng thời gian bằng phần mềm Premiere và cắt từng frame có chứa quả thanh long ra. Một tập dữ liệu của một quả thanh long gồm 3 tấm ảnh độ phân giải 720p. Tên mỗi view được đặt tên trùng nhau. Tiện cho việc quản lí theo dõi. 


<p align="center">
  <img src="storage/labeling1.jpg" width="450" />
  <img src="storage/labeling2.jpg" width="450" />
<p align="center">
  <em> 3.1. Quá trình thu thập dữ liệu</em>
</p>

<p align="center">
  <img src="storage/premiere_frames_export.gif" width="600" />
<p align="center">
  <em> 3.2. Xuất frames bằng premiere</em>
</p>



4. Tiến hành phân chia dữ liệu, có 3 nhãn tương ứng với 3 folder, mỗi folder chứa 3 folder con với mỗi folder trong này chứa ảnh được cắt ra từ camera tương ứng. 

<p align="center">
  <img src="storage/Diagram.png">
<p align="center">
  <em> 3.3. Cấu trúc thư mục chứa dữ liệu</em>
</p>

## Gắn nhãn dữ liệu
Trái được cắt đã qua các bước lọc cơ bản như: bỏ trái nhỏ, chưa chín, hư thúi,... bởi nông dân cắt. Và gắn nhãn này là bước phân loại chất lượng hàng để xuất khẩu, được tư vấn bởi chủ vựa.

### Lalel 1 - Loại đẹp 

Thanh long thuộc loại này phải có chất lượng tốt, xét về đặc điểm bên ngoài vỏ thanh long phải đáp ứng các tiêu chí:
- Khuyết tật nhẹ về hình dạng, màu sắc vỏ quả màu đỏ tươi ngoại trừ tai thanh long phải màu xanh lá.
- Khuyết tật nhẹ trên vỏ quả, không nấm bệnh, không đốm do côn trùng.
- Trong mọi trường họp, các khuyết tật không được ảnh hưởng đến thịt quả và không được ảnh hưởng đến chất lượng ngoại quan chung.
- Được phép có đốm đen (vì có thể rửa được).
   
<p align="center">
  <img src="Dataset/img/label_1/Binh_s%20cam/Binh_cam.00_18_09_23.Still091.jpg" width="300"/>
  <img src="Dataset/img/label_1/Kha_s%20cam/Binh_cam.00_18_09_23.Still091.jpg" width="300"/>
  <img src="Dataset/img/label_1/Ti_s%20cam/Binh_cam.00_18_09_23.Still091.jpg" width="300"/>
<p align="center">
  <em>Trái loại 1 không tì vết</em>
<p align="center">
  <img src="Dataset/img/label_1/Binh_s%20cam/Binh_cam.00_18_27_01.Still095.jpg" width="300"/>
  <img src="Dataset/img/label_1/Kha_s%20cam/Binh_cam.00_18_27_01.Still095.jpg" width="300"/>
  <img src="Dataset/img/label_1/Ti_s%20cam/Binh_cam.00_18_27_01.Still095.jpg" width="300"/>
<p align="center">
  <em>Trái loại 1 có khuyết tật nhẹ</em>
</p>
   
### Label 2 - Loại tiêu chuẩn
Thanh long không thuộc loại 2 sẽ có tiêu chuẩn thấp hơn loại 1:
- Khuyết tật nhẹ về hình dạng, màu sắc vỏ quả màu đỏ tươi ngoại trừ tai thanh long phải màu xanh lá.
- Khuyết tật nhẹ trên vỏ quả. Vẫn không chấp nhận nấm bệnh, không đốm do côn trùng.
- Các khuyết tật không được ảnh hưởng đến thịt quả và được ảnh hưởng mức độ đến chất lượng ngoại quan chung.

<p align="center">
  <img src="Dataset/img/label_2/Binh_s%20cam/l1_extra.00_40_27_19.Still070.jpg" width="300"/>
  <img src="Dataset/img/label_2/Kha_s%20cam/l1_extra.00_40_27_19.Still070.jpg" width="300"/>
  <img src="Dataset/img/label_2/Ti_s%20cam/l1_extra.00_40_27_19.Still070.jpg" width="300"/>

<p align="center">
  <img src="Dataset/img/label_2/Binh_s%20cam/label_2.01_15_05_11.Still041.jpg" width="300"/>
  <img src="Dataset/img/label_2/Kha_s%20cam/label_2.01_15_05_11.Still041.jpg" width="300"/>
  <img src="Dataset/img/label_2/Ti_s%20cam/label_2.01_15_05_11.Still041.jpg" width="300"/>
<p align="center">
  <em>Trái loại 2 có bị ảnh hưởng ngoại quan</em>
</p>
   
### Label 3 - Loại xấu
Thanh long thuộc loại này có chất lượng thấp nhất do có quá nhiều khuyết tật trên vỏ
- Tai thanh long bị gãy, bị lem đỏ.
- Có nhiều nấm bệnh, nhiều đốm do côn trùng.
- Vỏ quả có màu sắc sẫm màu hơn loại 1 hoặc phần vỏ không hoàn toàn màu đỏ (ngoại trừ phần tai thanh long).

<p float="center">
  <img src="storage/Label_3_pic1.jpg" width="1000" />
  <img src="storage/Label_3_pic2(1).jpg" width="1000" /> 
  <img src="storage/Label_3_pic3.jpg" width="1000" />
</p>


## Tiền xử lý dữ liệu: Sử dụng model Semantic Segmentation

- Sử dụng [labelme](https://github.com/wkentaro/labelme) để viền phần trái và dán nhãn
  <p float="left">
  <img src="storage/Binh_cam_labelme.jpg" width="300" />
  <img src="storage/Kha_cam_labelme.jpg" width="300" /> 
  <img src="storage/Ti_cam_labelme.jpg" width="300" />
</p>

- Sử dụng các loại model Semantic Segmentation huấn luyện, tách phần background và giữ lại phần trái để huấn luyện cho mô hình phân loại
<p float="left">
  <img src="Dataset/crop_mask/label_1/Binh_s%20cam/Binh_cam.00_05_50_12.Still029.png" width="300" />
  <img src="Dataset/crop_mask/label_1/Kha_s%20cam/Binh_cam.00_05_50_12.Still029.png" width="300" /> 
  <img src="Dataset/crop_mask/label_1/Ti_s%20cam/Binh_cam.00_05_50_12.Still029.png" width="300" />
</p>  


## Trường hợp dữ liệu khó xử lý

- Ảnh có chứa ngoại vật xen lẫn vào trái thanh long: tay, thanh sắt lúc chụp từ dưới lên.
<p float="center">
  <img src="Dataset/img/label_2/Ti_s%20cam/label_2.01_14_13_26.Still024.jpg" width="450" />
  <img src="Dataset/img/label_2/Ti_s%20cam/label_2.01_13_44_28.Still008.jpg" width="450" /> 
  
  <p align="center">
  <em>Ngoại vật trong trường hợp này là tay người</em>
</p>

<p float="center">
  <img src="Dataset/img/label_2/Kha_s%20cam/Binh_cam.00_09_21_23.Still054.jpg" width="450" /> 
  <img src="Dataset/img/label_2/Kha_s%20cam/Binh_cam.00_09_28_15.Still055.jpg" width="450" /> 
    
  <p align="center">
  <em>Ngoại vật trong trường hợp này là thanh sắt của băng chuyền</em>
</p>

- Ảnh ở camera thứ hai (Kha_cam) có độ sáng cao hơn 2 ảnh ở camera còn lại do góc chụp từ dưới hướng lên trời.
<p float="center">
  <img src="Dataset/img/label_2/Kha_s%20cam/Binh_cam.00_30_53_16.Still149.jpg" width="900" />
<p float="center">
  <img src="Dataset/img/label_2/Ti_s%20cam/Binh_cam.00_30_53_16.Still149.jpg" width="450" />
  <img src="Dataset/img/label_2/Binh_s%20cam/Binh_cam.00_30_53_16.Still149.jpg" width="450" />
<p align="center">
  <em>Độ sáng của ảnh chụp từ dưới lên cao hơn 2 ảnh chụp ở 2 bên từ trên xuống</em>
</p>

## Thông số bộ dữ liệu

Có 3 folder chính được tổ chức, đặt tên giống nhau:
 

### Img

Chứa tất cả ảnh đã gắn nhãn như mô tả trên
- Bộ dữ liệu ban đầu thu thập được khoảng 676 tập dữ liệu trái thanh long (1 tập dữ liệu có 3 ảnh) tương ứng với 2028 ảnh 1280x720x3.
  + 246 tập thuộc label 1
  + 210 tập thuộc label 2
  + 220 tập thuộc label 3
- Dữ liệu sau khi tăng cường bằng cách xoay thủ công trái thanh long trong quá trình quay video thu được khoảng 1120 tập dữ liệu trái thanh long tương ứng với khoảng 3360 ảnh 1280x720x3
  + 406 tập thuộc label 1
  + 412 tập thuộc label 2
  + 301 tập thuộc label 3

<p float="left">
  <img src="Dataset/img/label_1/Binh_s%20cam/label_2.01_13_23_06.Still000.jpg" width="300" />
  <img src="Dataset/img/label_1/Binh_s%20cam/l1_extra.00_04_06_24.Still000.jpg" width="300" /> 
  <img src="Dataset/img/label_1/Binh_s%20cam/l3_extra.02_20_39_13.Still000.jpg" width="300" />
<p align="center">
  <em>Tăng cường dữ liệu bằng cách xoay chuyển vị trí quả thanh long trên cùng một góc quay</em>
</p>

### Json

1299 folder chứa nhãn dạng đuôi .json train cho segmentation model để xóa background, <br/> file này sử dụng tool có sẵn trong [labelme]() để decode thành nparray nhị phân 1280x720:
  + 433 file thuộc view Binh_s cam
  + 433 file thuộc view Kha_s cam
  + 433 file thuộc view Ti_s cam
### Crop_mask

Chứa tất cả 3360 ảnh đã gắn nhãn và đã được xóa background (đây là dữ liệu train cho mô hình phân loại) với shape: 320x640x3
  + 406 tập thuộc label 1
  + 412 tập thuộc label 2
  + 301 tập thuộc label 3
### Csv

Chứa 2 loại:
  - Dữ liệu để phân loại, 1119 tập được trộn và chia 3 file csv:
    + train.csv: 782 dòng
    + val.csv: 218 dòng
    + test.csv: 119 dòng
<p float="left">
    Cột path chứa đường dẫn ảnh: <em> "img/label.../{}/image_name.jpg" </em> với {} lần lượt 3 tên cameras khi đọc ảnh.<br/>Cột y dạng: "label..."
</p>
  
  - Dữ liệu để semantic segmentation, 1299 tập được trộn và chia cho 2 file csv:
    + train_mask.csv: 1100 dòng
    + val_mask.csv: 199 dòng
<p float="left">
  Cột <strong>"path"</strong> chứa đường dẫn ảnh: <em> "img/label.../cam.../image_name.jpg" </em> .<br/>Cột <strong>"label"</strong> dạng: <em> "json/label.../cam.../image_name.json" </em>.
</p>

# Chương 4: Training và đánh giá model
## Cấu hình máy:
<p align="center">
  <img src="storage/Configuration.jpg">
</p>

## Model dùng  xóa background ảnh (Giai đoạn Preprocessing)
Ứng dụng các nghiên cứu cho bài toán semantic segmentation, nhóm xây dựng và thử nghiệm hai model dựa trên kiến trúc mạng [Unet](https://github.com/milesial/Pytorch-UNet) và [Enet](https://github.com/davidtvs/PyTorch-ENet)

<p align="center">
  <img src="storage/Unet/test_Unet%20(2).png",width=600>
  <img src="storage/Unet/test_Unet.png",width=600>
  <br/>
  <em>Xác định phần quả thanh long trên khung hình và tách ra khỏi ảnh (xóa background)</em>
</p>

### MẠNG UNET

#### 1. Sơ lược mạng Unet
Kiến trúc mạng Unet có 2 phần đối xứng nhau: phần encoder (phần bên trái) và phần decoder (phần bên phải). Trong đó
- Encoder để giảm chiều dài và chiều rộng của ảnh, Encoder thường là các mạng CNN thông thường
- Decoder để khôi phục kích thước ảnh gốc
- Nhóm sử dụng repos có sẵn: [Segmentation Models](https://github.com/qubvel/segmentation_models)
<p align="center">
  <img src="storage/Unet/Unet_NN.png",width=500>
  <br/>
  <em>Kiến trúc mạng Unet</em>
</p>

#### 2. Chi tiết Input, Output và xử lí

##### 2.1 INPUT
gồm 1299 mẫu dữ liệu trộn lẫn của cả 3 camera. Trong đó, 1099 mẫu dùng để training và 200 mẫu dùng cho validation. Một mẫu gồm có:
  - **X_input**: Ảnh quả thanh long gốc shape = [720, 1280, 3] được reshape thành [320, 640, 3] (file .jpg)
  - **y_true**: file .json sau khi segment ảnh bằng labelme thu được array nhị phân với shape = [720, 1280] được reshape thành [320, 640]

##### 2.2 OUTPUT & XỬ LÍ
  - **y_predict** là np.array mang các giá trị từ [0, 1] với shape = [320, 640, 1] 
  - sau đó apply **y_predict** vào ảnh gốc thu được phần trái đã được xóa background.

#### 3. Quá trình thiết lập training

##### 3.1 COMPILE
  - backbone nhóm sử dụng là vgg16 vì thấy ít parameter hơn resnet50 hay các mạng khác.
  - batch_size = 16
  - epoch = 100
  - loss: [jaccard_loss](https://segmentation-models.readthedocs.io/en/latest/api.html#segmentation_models.losses.JaccardLoss), metric: [IOU_score](https://segmentation-models.readthedocs.io/en/latest/api.html#segmentation_models.metrics.IOUScore) có sẵn trong repos [Segmentation Models](https://github.com/qubvel/segmentation_models)

 
##### 3.2 SUMMARY

Thông số parameter của model:
- Total params: 23,752,273
- Trainable params: 23,748,241
- Non-trainable params: 4,032


#### 4. Kết quả: ...(updating)(đánh giá performance)
Nhận xét: [Colab train](Colab_train/Preprocessing_Unet.ipynb) có chi tiết quá trình từng epoch:

  - Mỗi epoch mất khoảng 96s để train.
  - Loss giảm mạnh trong 5 epochs đầu và bão hòa sau đó, hầu như ko hề giảm
  - Model huyền thoại này khá ổn, với số lượng data tương đối nhiều, kết quả tốt. 
  - Nhóm thử predict trên batch 16 tấm, model xử lí trong khoảng 0.797s => khoảng 20fps. 



<p align="center">
  <img src="storage/Unet/loss_Unet.png",width = 450>
  <img src="storage/Unet/iou_score_Unet.png",width = 450>
  <br/>
  <em>Đồ thị loss value và iou score của model</em>
</p>



#### 5. Demo
<p align="center">
  <img src="https://github.com/trankha1655/CS114_ML/blob/main/%C4%90%E1%BB%93%20%C3%A1n%20cu%E1%BB%91i%20k%E1%BB%B3/storage/Unet/Plot_Unet.png">
</p>

### Mạng Enet
#### 1. Sơ lược mạng ENet

****ENet (Efficient Neural Network)*** có khả năng phân khúc ảnh qua pixel theo thời gian thực. ENet nhanh hơn đến 18 lần, yêu cầu FLOP (Floating Point Operation Per Second) ít hơn 75 lần và số lượng tham số (parameters) ít hơn 79 lần cho độ chính xác gần tương đương so với các mô hình hiện có (năm 2016). Số liệu trên có được qua các thử nghiệm trên bộ dũ liệu CamVid, Cityscapes và SUN (nguồn: [ENet: A Deep Neural Network Architecture for Real-Time Semantic Segmentation](https://arxiv.org/abs/1606.02147))

#### 2. Chi tiết datasets
Sau khi xem xét bộ dữ liệu, nhận thấy ánh sáng các ảnh trong folder *"Kha_cam"* có độ sáng mạnh hơn các ảnh ở 2 folder còn lại. Vì vậy, nhóm quyết định train 2 model cho 2 trường hợp dữ liệu.
- Một model (**Enet_2cam**) dành cho ảnh chụp bởi 2 camera ở 2 bên có góc nhìn từ trên xuống.
- Một model (**Enet_midcam**) dành cho ảnh chụp bởi camera chụp từ dưới lên.

**Bộ dữ liệu cho model Enet_2cam**: Gồm tổng cộng 433 mẫu dữ liệu. Trong đó, có 361(≈83%) mẫu dùng để training và 72(≈17%) tập dùng cho validation.

**Bộ dữ liệu cho model Enet_midcam**: Gồm tổng cộng 866 mẫu dữ liệu. Trong đó, có 738 (≈85%) mẫu dùng để training và 128(≈15%) tập dùng cho validation.

*Mỗi mẫu dữ liệu bao gồm:*
- ...

#### 3. Quá trình thiết lập training

**(updating...)**


#### 4. Kết quả

**(updating...)**

#### 5. Demo

**Model Enet_2cam**

**Model Enet_midcam**

<p align="center">
  <img src="https://github.com/trankha1655/CS114_ML/blob/main/%C4%90%E1%BB%93%20%C3%A1n%20cu%E1%BB%91i%20k%E1%BB%B3/storage/Enet/2_cam/Plot_demo.png">
</p>

### So sánh hai model
| Tiêu chí đánh giá | UNet | ENet |
| :---: | --- | --- |
| | | |

***Kết luận***

## Model dùng để phân loại thanh long
