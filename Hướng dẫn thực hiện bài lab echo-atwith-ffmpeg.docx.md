***Nội dung và hướng dẫn thực hiện bài lab***

**Sử dụng FFmpeg để phá hoại tín hiệu giấu tin trong âm thanh WAV**

**1\. Chuẩn bị môi trường**

* Máy ảo Ubuntu có cài đặt labtainer  
* File imodule của labtainer echo-atwith-ffmpeg

**2\. Các bước thực hiện**

**2.1. Chuẩn bị bài lab**

* Tải bài lab:

*imodule https://github.com/tai1503/echo-atwith-ffmpeg/raw/main/imodule.tar*

* Khởi động bài lab:  
  *labtainer \-r echo-atwith-ffmpeg*

**2.2 Thực hiện bài lab**

Cài đặt các thư viện cần thiết cho bài lab:

*pip3 install numpy*

*pip3 install scipy*

Cài đặt công cụ ffmpeg để phá hoại tín hiệu giấu tin trong file âm thanh:

*sudo apt update*

*sudo apt install ffmpeg*

Thực hiện tách tin từ file âm thanh *sound\_stego.wav,* từ đó xem được nội dung thông điệp:

*python3 echo\_extract.py sound\_stego.wav*

Sử dụng công cụ ffmpeg thêm tiếng ồn trắng vào tệp âm thanh làm sai lệch nội dung tin:

*ffmpeg \-i sound\_stego.wav \-filter\_complex "sine=frequency=1000:duration=2" output\_with\_noise.wav*

Thực hiện tách tin từ file âm thanh đã thêm tiếng ồn và kiểm tra tin thu được:

*python3 echo\_extract.py output\_with\_noise.wav*

Sử dụng công cụ ffmpeg thay đổi sample rate của tệp âm thanh, điều này có thể dẫn đến giảm chất lượng âm thanh:

*ffmpeg \-i sound\_stego.wav \-ar 22050 output.wav*

Thực hiện tách tin từ file âm thanh đã thay đổi sample rate và kiểm tra tin thu được:

*python3 echo\_extract.py output.wav*

Trên terminal đầu tiên:

* Kiểm tra kết quả bài lab:

*checkwork*

* Kết thúc bài lab:

*stoplab*

* Khởi động lại bài lab:

*labtainer \-r echo-atwith-ffmpeg*

