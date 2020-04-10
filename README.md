# MusicPlayer

GIẢI THÍCH CODE
Mình sẽ không giải thích về HTML và CSS do không có gì phải giải thích cả :|
Có 1 cái bạn cần lưu ý ở trang HTML đó chính là thẻ Meta Tag: viewport. Tại sao? Vì không có thẻ Meta này thì việc hiển thị trên các thiết bị điện thoại sẽ gặp vấn đề.

NOTE: Nếu muốn sửa nhạc, chỉ cần sửa variable songs(Array) theo dạng sau:
var songs = [{
    artist: "Ca si 1",      // Tên Ca sĩ
    name: "Ten bai hat 1",  // Tên Bài hát
    url: "Link Nhac 1",     // Link file nhạc (flac, wav, mp3, ...)
    picture: "Link Anh 1"   // Link ảnh hiển thị (vuông)
}, {
    artist: "Ca si 2",
    name: "Ten bai hat 2",
    url: "Link Nhac 2",
    picture: "Link Anh 2"
}, ... ]

Về Javascript, ở đây có các Functions sau:
shuffle
playPause
showHover
playFromClickedPos
checkBuffering
selectTrack
initPlayer

Hàm Shuffle:
Hàm này sẽ xáo thứ tự các item trong 1 Array theo thứ tự ngẫu nhiên. (Dành cho bạn nào muốn Xáo cái list nhạc trước khi nghe).

Hàm playPause:
Hàm này Handle event click vào nút Play/Pause. (Dừng nhạc / tiếp tục phát từ điểm dừng cuối cùng).

Hàm showHover:
Ở đây hàm này sẽ chịu trách nhiệm cho event click vào thanh trượt hiển thị thời lượng % bài nhạc đã phát (Click để phát từ chỗ vừa click chuột).
Khi click, 1 argument được truyền vào là thông tin của cái event. Trong Event này bao gồm vị trí click chuột (Event.clientX là vị trí chuột tính theo chiều ngang của web (Mục đích tìm xem chuột di vào vị trí nào mà tính thời gian)). seekT chính là khoảng cách từ điểm bắt đầu của thanh hiển thị tới điểm của chuột. seekLoc là giá trị tính bằng giây.
Hàm này sẽ bị GỌI LIÊN TỤC khi chuột hover trên thanh trượt. (Mục đích là để set giá trị)

Hàm hideHover:
Chuột đi ra khỏi thanh trượt sẽ gọi event này. Mục đích là để set lại cái dải hiển thị phần chuột đã select (từ điểm bắt đầu tới vị trí chuột) về điểm bắt đầu (sHover.width = 0).
Ngoài ra event này cũng set các text đếm thời gian về điểm bắt đầu.

Hàm updateCurrTime:
Gọi để set thời gian, nếu đủ 100% (hết bài) thì chuyển bài và set thời gian về bắt đầu.

Hàm checkBuffering:
Kiểm tra nhạc đã load xong chưa.

Hàm selectTrack:
Chuyển bài (tiến/lùi). Thực chất chỉ là tăng giảm biến currIndex và set các giá trị theo currIndex.

Hàm initPlayer:
Bắt đầu player và gán tuần tự các events.


Player được chỉnh sửa/phát triển từ nguồn giao diện của: CodePen
