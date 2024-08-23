# PI_CAM.Flask
***********************Phần cứng cần chuẩn bị:***********************
1. Orange Pi Zero hoặc các mẫu Raspberry Pi Zero (Ở đây mình dùng Orange PI Zero).
2. Webcam USB hoặc các camera mà mẫu pi bạn hỗ trợ (Ở đây mình dùng webcam USB).
3. Một thẻ nhớ tối thiểu 8GB (Nên chọn các thẻ có tốc đọc ghi nhanh).
4. Một bộ nguồn 5VDC tối thiếu 2A.
5. Một dây cáp LAN để cấu hình wifi cho Orange PI.

***********************Phần mềm cẩn chuẩn bị:***********************
1. Phần mền ghi thẻ nhớ, mình dùng: balenaEtcher (dành cho Win, source code hỗ trợ cả Mac):
   - Dùng để ghi tệp ảnh phần mềm vào thẻ nhớ.
   - Tải ở link sau: https://balenaetcher.en.download.it
2. Phần mềm dò địa chỉ IP mạng, mình dùng: Advanced IP Scanner (dành cho Win):
   (Hoặc các bạn có thể dùng phần mềm dò IP bằng điện thoại cũng đều được)
   - Dùng để tìm địa chỉ IP của Orange Pi để có thể dùng công cụ SSH để điều khiển từ xa.
   - LƯU Ý: Các bạn nhớ giúp mình số MAC của pi, vì số này sẽ không thay đổi khi các bạn tìm IP.
   - Tải ở link sau: https://www.advanced-ip-scanner.com/vi/   
4. Phần mềm MobaXterm (hỗ trợ nhiều giao thức điều khiển không dây, VD: VNC, SSH,...):
   (Hoặc các bạn có thể dùng Windows PowerShell chạy với quyền quản trị viên cho tiện)
   - Sử dụng công cụ SSh để điều khiển PI, đồng thời cũng hỗ trợ chuyển tệp, xóa tệp một các dễ dàng.
   - Tải ở link sau: https://mobaxterm.mobatek.net
   
*****************************Tiến hành:*****************************
BƯỚC 1: Cài đặt hệ điều hành cho Orange Pi
      - Vào trang sau: https://www.armbian.com/orange-pi-zero/  để tải hệ điều hành cho Orange Pi.
      - Vì Orange Pi Zero ko có bản desktop nên bạn có thể tùy chọn tải về Ubuntu hoặc Debian. 
      - Sau khi tải về, giải nén ra, có 1 file dạng đuôi .img. Đây chính là file ảnh của hệ điều hành.
      - Dùng phần mềm balenaEtcher để ghi vào thẻ nhớ bằng cách chọn tệp ảnh -> chọn ổ đĩa -> tiến hành Flash.
      - Sau khi Flash, rút thẻ nhớ và cắm vào Orange PI
BƯỚC 2: Dò địa chỉ IP của Orange PI (Lưu ý: Nhớ địa chỉ MAC)
      - Cắm nguồn, dây mạng cho Pi và đợi Pi khởi động.
      - Để ý 2 led trên cổng LAN nhấp nháy là đã nhận mạng, sau đó tắt.
      - Dùng phần mềm Advanced IP Scanner để SCAN tìm IP của Orange PI (*Ảnh minh họa)
      ![image](https://github.com/user-attachments/assets/f7e21b52-9f22-404a-9227-e6b895339c92)
      - Sau khi check được IP và lưu lại địa chỉ MAC, tiến hành bước tiếp theo
