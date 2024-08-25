# PI_CAM.Flask
Stream Camera Orange Pi bằng Flash trên Era kết hợp với OpenCV để giám sát trên Mobile Phhone 
***
## Phần cứng cần chuẩn bị:
1. Orange Pi Zero hoặc các mẫu Raspberry Pi Zero (Ở đây mình dùng Orange PI Zero).
2. Webcam USB hoặc các camera mà mẫu pi bạn hỗ trợ (Ở đây mình dùng webcam USB).
3. Một thẻ nhớ tối thiểu 8GB (Nên chọn các thẻ có tốc đọc ghi nhanh).
4. Một bộ nguồn 5VDC tối thiếu 2A.
5. Một dây cáp LAN để cấu hình wifi cho Orange PI.

## Phần mềm cẩn chuẩn bị:
1. Phần mền ghi thẻ nhớ, mình dùng: balenaEtcher (dành cho Win, source code hỗ trợ cả Mac):
   - Dùng để ghi tệp ảnh phần mềm vào thẻ nhớ.
   - Tải ở link sau: https://balenaetcher.en.download.it
2. Phần mềm dò địa chỉ IP mạng, mình dùng: Advanced IP Scanner (dành cho Win):
   _(Hoặc các bạn có thể dùng phần mềm dò IP bằng điện thoại cũng đều được)_
   - Dùng để tìm địa chỉ IP của Orange Pi để có thể dùng công cụ SSH để điều khiển từ xa.
   - LƯU Ý: Các bạn nhớ giúp mình số MAC của pi, vì số này sẽ không thay đổi khi các bạn tìm IP.
   - Tải ở link sau: https://www.advanced-ip-scanner.com/vi/   
3. Phần mềm MobaXterm (hỗ trợ nhiều giao thức điều khiển không dây, VD: VNC, SSH,...):
   _(Hoặc các bạn có thể dùng Windows PowerShell chạy với quyền quản trị viên cho tiện)_
   - Sử dụng công cụ SSh để điều khiển PI, đồng thời cũng hỗ trợ chuyển tệp, xóa tệp một các dễ dàng.
   - Tải ở link sau: https://mobaxterm.mobatek.net
## Tiến hành:
1. Cài đặt hệ điều hành cho Orange Pi:
      - Vào trang sau: https://www.armbian.com/orange-pi-zero/  để tải hệ điều hành cho Orange Pi.
      - Vì Orange Pi Zero ko có bản desktop nên bạn có thể tùy chọn tải về Ubuntu hoặc Debian. 
      - Sau khi tải về, giải nén ra, có 1 file dạng đuôi .img. Đây chính là file ảnh của hệ điều hành.
      - Dùng phần mềm balenaEtcher để ghi vào thẻ nhớ bằng cách chọn tệp ảnh -> chọn ổ đĩa -> tiến hành Flash.
      - Sau khi Flash, rút thẻ nhớ và cắm vào Orange Pi
2. Dò địa chỉ IP của Orange PI (_Lưu ý: Nhớ địa chỉ MAC_):
      - Cắm nguồn, dây mạng cho Pi và đợi Pi khởi động.
      - Để ý 2 led trên cổng LAN nhấp nháy là đã nhận mạng, sau đó tắt.
      - Dùng phần mềm Advanced IP Scanner để SCAN tìm IP của Orange PI (*Ảnh minh họa).
      ![image](https://github.com/user-attachments/assets/d8357b0f-16eb-4946-a054-1f4a2f37e503)
      - Sau khi check được IP ở thiết bị có tên "orangepizero" và lưu lại địa chỉ MAC, tiến hành bước tiếp theo.
3. Tiến hành SSH vào Orange Pi bằng MobaXterm:
      - Mở MobaXterm, chọn Start local Terinal. 
      ![image](https://github.com/user-attachments/assets/392dafa7-eb93-4d2c-a6c8-f39268bd596c)
      - Dùng lệnh: `ssh root@192.168.xxx.xxx` để ssh vào PI (_Thay thế IP vào nhé!_)
      - Sau khi SSH sẽ hiện ra ảnh sau:
      ![image](https://github.com/user-attachments/assets/305276e3-2f5d-48e9-91de-61a4945d7aff)
4. Cấu hình wifi cho Pi để Pi tự động kết nối lần sau mà không cần cáp mạng:
   (_Nếu hệ điều hành của bạn hỗ trợ Network Manager, cách đơn giản nhất là sử dụng nmtui_)
      - Cài đặt nmtui (nếu chưa có):
   ```sudo apt-get install network-manager```
      - Mở nmtui bằng: ```sudo nmtui```
      - Chọn: ```Edit a connection```
      - Sau đó chọn wifi nhập pass và 'back' về màn hình ban đầu.
      ![image](https://github.com/user-attachments/assets/835db4f5-2472-4fec-a089-33771644a7a3)
5. Tải các gói cài đặt cần thiết cho Orange Pi:
      - Gói cập nhật: `sudo apt update`
                       `sudo apt upgrade`
      - Tải gói Pytho và các gói phụ thuộc: `sudo apt install python3-dev python3-pip python3-numpy` và kiểm tra bằng: `python3 --version`
      - Tải xuống OpenCV: `sudo apt install python3-opencv` và kiểm tra bằng cách nhập: `python3`, sau đó nhập `import cv2`
                                                                                                                `print(cv2.__version__)`
      - Tải xuống một số phụ thuộc: 
