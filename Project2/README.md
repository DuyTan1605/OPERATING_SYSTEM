# BÁO CÁO
 ĐỒ ÁN 2 HỆ ĐIỀU HÀNH
LINUX KERNEL MODULE
& SYSTEM CALL HOOKING

1) LINUX KERNEL MODULE:
- Mô tả: 
	+ Viết một kernel module tạo ra số ngẫu nhiên
	+ Module sẽ tạo ra một character device cho phép tiến trình ở phía user space có thể read và open các số ngẫu nhiên
-Các bước thực hiện:
	+ Bước 1: truy cập vào thư mục chứa source code module
		cd randomNumber 
- Tiến hành kiểm tra các thông báo đã được ghi vào dmesg trong suốt các quá trình từ biên dịch,cài đặt,thực thi chương trình phía user đến gỡ bỏ module:
	+ Bước 2:Trước khi thực thi quá trình biên dịch,thực thi có thể thực hiện clear dmesg để dễ quan sát các thông báo được ghi vào dmesg trong quá trình test kernel
		sudo dmesg -c
	+ Bước 3: Để hiển thị các thông báo đã ghi vào dmesg ta thực hiện lệnh
		dmesg -wH
-Sau các bước thiết lập như trên,tiến hành biên dịch,thực thi chương trình:
	+ Bước 4: biên dịch chương trình
		sudo make
	+ Bước 5: Sau khi biên dịch thành công tiến hành cài đặt module
		sudo insmod getRandomNumber.ko
	+ Bước 6: Thực hiện test chương trình thực thi phía user
		sudo  ./test
	+ Bước 7: Gỡ bỏ kernel
		sudo rmmod getRandomNumber.ko

2)HOOKING INTO SYSTEM CALL(OPEN AND WRITE):
- Mô tả:
	+ Hook vào system call open(ghi vào dmesg tên tiến trình mở file và tên file được mở)
	+ Hook vào system call write(ghi vào dmesg tên tiến trình,tên file bị ghi và số bytes được ghi)
-Các bước thực hiện:
	+ Bước 1: truy cập vào thư mục chứa source code hook
		cd hook
- Tiến hành kiểm tra các thông báo đã được ghi vào dmesg trong suốt các quá trình từ biên dịch,cài đặt,thực thi chương trình phía user đến gỡ bỏ module:
	+ Bước 2:Trước khi thực thi quá trình biên dịch,thực thi có thể thực hiện clear dmesg để dễ quan sát các thông báo được ghi vào dmesg trong quá trình test kernel
		sudo dmesg -c
	+ Bước 3: Để hiển thị các thông báo đã ghi vào dmesg ta thực hiện lệnh
		dmesg -wH
-Sau các bước thiết lập như trên,tiến hành biên dịch,thực thi chương trình:
	+ Bước 4: biên dịch chương trình
		sudo make
	+ Bước 5: Sau khi biên dịch thành công tiến hành cài đặt module
		sudo insmod hook_into_sys.ko
	+ Bước 6: Thực hiện test chương trình thực thi phía user
		sudo  ./hooksys_test
	+ Bước 7: Gỡ bỏ kernel
		sudo rmmod hook_into_sys.ko

