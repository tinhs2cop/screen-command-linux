screen-command-linux
====================

Hướng dẫn sử dụng lệnh screen trong Linux

### Giới thiệu

*Screen* hiểu nôm na là một câu lệnh cho phép chúng ta quản lý các kết nối SSH tới server Linux bằng các phím tắt trên cùng một cửa sổ console, đồng thời nó cũng cho phép giữ một cửa sổ (một câu lệnh) làm việc liên tục mặc cho việc kết nối từ SSH client bị ngắt.

Các chức năng của *screen*

- Quản lý các phiên làm việc từ xa (SSH)
- Không giới hạn các cửa sổ làm việc
- Copy, paste giữa các cửa sổ
- Phân chia các cửa sổ làm việc
- Khóa cửa sổ làm việc
- ...

### Cách sử dụng Screen

Để sử dụng lệnh screen ta có thể sử dụng trên chính terminal của máy chủ hoặc trên SSH client (Putty, Secure Crt,...)

Chắc chắn rằng bạn đã tắt các bộ gõ tiếng Việt (Unikey, Vietkey,...)

Trên các terminal này ta sử dụng lệnh

    screen

Sau đó màn terminal sẽ vào *screen* mode, hình sau sẽ hiện ra

<img src=http://i.imgur.com/WmYhjlv.png>

Ấn Enter và lúc này ta có thể thao tác với các terminal bằng screen

Để không làm việc với screen nữa ta sử dụng lệnh

    exit

#### Các thao tác với phiên làm việc

| Phím tắt | Hành động |
|----------|-----------|
| Ctrl+a c | Mở một phiên mới, các phiên được đánh số thứ tự tăng dần bắt đầu từ 0 |
| Ctrl+a n | Chuyển cửa sổ hiện tại đến phiên tiếp theo |
| Ctrl+a p | Chuyển cửa sổ hiện tại đến phiên trước đó |
| Ctrl+a " | Liệt kê danh sách các phiên, di chuyển con trỏ đến phiên cần sử dụng và ấn Enter |
| Ctrl+a Ctrl+a | Chuyển đổi giữa các phiên |
| Ctrl+a A | Đặt tên cho phiên hiện tại |

#### Các thao tác với cửa sổ làm việc

| Phím tắt | Hành động |
|----------|-----------|
| Ctrl+a S | Chia đôi cửa sổ hiện tại thành hai nửa trên dưới |
| Ctrl+a | | Chia đôi cửa sổ hiện tại thành hai nửa trái phải |
| Ctrl+a tab | Chuyển sang cửa sổ tiếp theo, sau đó sử dụng các phím tắt với phiên làm việc |
| Ctrl+a :resize | Chỉnh lại kích thước cửa sổ hiện tại, sau đó điền vào số dòng của cửa sổ mới |
| Ctrl+a X | Đóng cửa sổ hiện tại |
| Ctrl+a :remove | Giống Ctrl+a X |
| Ctrl+a x | Khóa cửa sổ làm việc, nhập mật khẩu để mở lại |
| Ctrl+a [ | Copy tại cửa sổ hiện tại, dùng phím Enter để đánh dấu vị trí chọn đầu tiên, đảm bảo Unikey đã tắt, Enter để kết thúc chọn |
| Ctrl+a ] | Paste |
| Ctrl+a > | write paste buffer to file |
| Ctrl+a < | read paste buffer from file |
| Ctrl+a ? | Hiện trợ giúp |
| Ctrl+a : | Vào chế độ nhập phím tắt |

**Lưu ý:** Cách giữ một phiên luôn hoạt động khi tắt Putty hoặc Secure Crt

- Sử dụng ***Ctrl+a d*** để ẩn và chạy ngầm phiên hiện tại, có thể sử dụng cho nhiều phiên khác nhau. Lúc này phiên vẫn đang làm việc bình thường mặc dù có tắt terminal.
- Sử dụng ***screen -list*** để liệt kê các phiên này


        2120.pts-0.network1     (10/01/2014 01:56:11 PM)        (Detached)
        1800.pts-0.network1     (10/01/2014 01:13:20 PM)        (Detached)
        2 Sockets in /var/run/screen/S-root.


- Sử dụng ***screen -r tên phiên*** để mở lại phiên đó. Ví dụ:


        screen -r 2120.pts-0.network1


Sử dụng cách này khi cần giữ một phiên làm việc trong thời gian dài mà không thể để mất kết nối, ví dụ như cần chạy một script cài đặt mất nhiều thời gian.
