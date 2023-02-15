# Sudoku_game_KTLT
Bài tập lớn môn Kĩ thuật lập trình C/C++ 

# Tổng quan về project
Phần mềm game Sudoku ncurses đơn giản chạy trên terminal được viết bằng ngôn ngữ C++
## Sudoku
Sudoku ban đầu có tên gọi là Number Place là một trò chơi câu đố sắp xếp chữ số dựa trên theo tổ hợp. 
### Nguồn gốc
Tim Preston, giám đốc Puzzler Media - nhà xuất bản các tạp chí và sách câu đố lớn nhất của Anh, cho rằng Sudoku thực ra là phát minh của nhà toán học thế kỷ XVIII Leonhard Euler.
### Cách chơi
Mục tiêu của trò chơi là điền các chữ số vào một lưới 9×9 sao cho mỗi cột, mỗi hàng, và mỗi phần trong số chín lưới con 3×3 cấu tạo nên lưới chính (cũng gọi là "hộp", "khối", hoặc "vùng") đều chứa tất cả các chữ số từ 1 tới 9. Câu đố đã được hoàn thành một phần, người chơi phải giải tiếp bằng việc điền số. Mỗi câu đố được thiết lập tốt có một cách làm duy nhất.
### Chi tiết về Sudoku
Nếu có hứng thú có thể đọc về thêm về [Sudoku](https://vi.wikipedia.org/wiki/Sudoku)

## Sử dụng phần mềm
### Yêu cầu chung
Yêu cầu cấu hình máy tính đủ để chạy Linux hoặc OSC và install được g++, clang++ bản mới nhất. Nếu sử dụng hệ điều hành Window có thể chạy máy ảo Ubuntu để chơi, hướng dẫn cách set up và chạy máy ảo có thể tham khảo [tại đây](https://www.youtube.com/watch?v=Rzg144v3hfo)
### Cách chơi 
Điền vào tất cả các ô vuông còn thiếu không có chữ số lặp lại trong cột, hàng hoặc hộp 3x3 nào. Sử dụng các phím 'wasd', 'hjkl', hoặc các phím mũi tên từ bàn phím để điều khiển con trỏ trên bảng Sudoku. Nhấn phím 'i' để đưa về chế độ điền đáp án, phím 'p' để đưa về trạng thái note đáp án lên bảng Sudoku. Để đến 1 tọa độ nhất định trên bảng, nhấn phím 'g' tiếp đến là tọa độ của cột và hàng muốn điều đến, ví dụ muốn đưa con trỏ về tọa độ 1-9 thì ấn "g19". Ấn 'c' để hiện những đáp án đã điền sai (màu đỏ) và những đáp án đã điền đúng (màu xanh). Ấn 'c' 1 lần nữa để bỏ màu đi. Ở phần mềm này hỗ trợ note tối đa 3 số trong cùng 1 ô vuông. Để xóa lỗi note gần đây nhất, hãy nhấn phím cách ở các chế độ tương ứng. Để xóa một giá trị note cụ thể, hãy nhập số đó vào hộp khi ở chế độ bút chì.
### Install
Có thể download trực tiếp mã nguồn [tại đây](https://github.com/Haipham2002/sudoku/tree/main/src).
Hoặc có thể git clone trực tiếp về máy và chạy phần mềm sử dụng trình biên dịch g++ hoặc clang++ như dưới đây.
#### Linux
````
git clone https://github.com/flyingpeakock/Console_sudoku.git
cd Console_sudoku/
g++ -Ofast -pthread ./src/*.cpp -lncursesw -o <filename>
./<filename>
````
#### OSX
```
git clone https://github.com/flyingpeakock/Console_sudoku.git
cd Console_sudoku/
clang++ -O3 -pthread -std=c++11 -stdlib=libc++ ./src/*.cpp -lncursesw -o <filename>
```
Trong đó <filename> là tên file tùy ý mà bạn muốn đặt.
### Command line arguments
| Lệnh | Mô tả |
| --- | --- |
| `./<filename>` | Chơi Sudoku với số câu đố mặc định |
| `./<filename> -h` hoặc `<./filename> --help` | In ra cách sử dụng các lệnh (command line arguments), cách sử dụng bàn phím tương tác với trò chơi, cách giải Sudoku |
| `./<filename> -w` hoặc `<./filename> --wasd`| Hiển thị các phím di chuyển con trỏ là "wasd" thay vì "hjkl" |
| `./<filename> -easy` | Chơi Sudoku với chế độ dễ (42/81 ô trống) |
| `./<filename> -medium` | Chơi Sudoku với chế độ trung bình (49/81 ô trống) |
| `./<filename> -hard` | Chơi Sudoku với chế độ khó (56/81 ô trống) |
  
## Ảnh
Dưới đây là các hình ảnh Sudoku ở các chế độ chơi khác nhau
### `./<filename>`
![default game](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/default%20game.png)
### `./<filename> -h`hoặc `./<filename> --help`
![print help](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/help.png)
### `./<filename> -w`hoặc `./<filename> --wasd`
![wasd mode](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/wasd%20mode.png)
### `./<filename> -easy`
![easy game](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/easy-mode.png)
### `./<filename> -medium`
![medium game](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/medium-mode.png)
### `./<filename> -hard`
![hard game](https://github.com/Haipham2002/sudoku/blob/main/documents/Pics/hard-mode.png)

## Quá trình phân tích, thiết kế và phát triển dự án
### Lưu đồ thuật toán cho bộ giải đố và bộ tạo câu đố
![Solver and Generator flowchart](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Solver%26Generator%20flowchart.jpg)
### Sơ đồ Usecase
![Usecase diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Usecase.jpg)
### Sơ đồ lớp thiết kế
![Class diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Class%20.jpg)
### Sơ đồ tương tác tuần tự
![Sequence diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Sequence.jpg)
### Sơ đồ tương tác cộng tác
![Collaboration diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Collaboration.jpg)
### Sơ đồ hoạt động
![Activity diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Activity.jpg)
### Sơ đồ thành phần
![Component diagram](https://github.com/Haipham2002/sudoku/blob/main/documents/UML/Sudoku%20UML-Component.jpg)

## Troubleshooting
Nếu trình biên dịch không thể tìm thấy ncurses.h, hãy install trên terminal (có thể tham khảo [link này](https://www.youtube.com/watch?v=ebEG_EilTaI)). Nếu không tìm thấy thư viện ncurses trong package manager, nó có thể có tên gọi khác như "libcurse". Nếu vẫn không được hãy dùng lệnh ` -lncurses` thay vì ` -lncursesw` khi khởi động phần mềm.
