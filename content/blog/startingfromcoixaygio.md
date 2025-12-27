---
date: 2025-11-13T16:45:00
tags:
  - personal
  - tusixmode
  - software
title: Starting from Cối Xay Gió
description: Nghe nói Cối Xay Gió là phát minh đầu tiên đánh dấu nền văn mình của nhân loại
image: /assets/images/coixaygio.png
---
Mình thường dùng những ngôn từ quá nghiêm túc để nói tới những chuyện bình thường.

Mình đang thật sự rất sợ em sẽ trở thành người yêu của ai đó trong số những kẻ từng quen biết. *Không nên nói về chuyện tình cảm*.

> Thứ gì người khác không biết thì họ không phá hoại được. Vì có những kẻ chỉ muốn phá hoại những điều tốt đẹp.

Hôm nay mình đặt bảng vẽ, nhưng shipper không giao đúng hạn buổi sáng như những lúc trước. Mình có cảm giác nó đã thấy một mối nguy gì đó ở chuyện này nên đã cố tình tìm cách kéo dài thời gian. Và nó đã đạt được ý định làm mình tức giận. Thậm chí, ở góc nhìn về sự vượt trội, loài người sợ một kẻ như mình làm nên một chuyện gì đó, kẻ thù trước giờ của mình toàn là kẻ thù tự nhiên, bỗng nhiên chúng tiến tới mình và gây thù oán.

Trời ban cho sự vượt bậc của ngoại hình hay tính cách thì cũng kéo theo những mối nguy hiểm tương tự như vậy. Một trong những mối nguy hiểm lớn nhất của đàn ông, là những kẻ tìm đủ mọi cách để hãm hại bạn.

Có một lần đang ngồi đánh đàn với một thằng trong nhóm cũ thì nghe hàng xóm xung quanh chỗ đó nói trỏ qua là: "vậy là thằng này bị hại". Lúc đó mình có một chút suy nghĩ nhưng mình lại không nghĩ nhiều lắm. Đáng ra lúc đó đã phải nhận ra mối nguy đã trực chờ sẵn ngay lúc đó rồi.

---
Chờ đã! Tôi không tin ai cả.

---

> Mình vừa định viết một bài về mã hóa đầu cuối với mục đích, nếu bạn hiểu một điều gì đó, bạn phải giải thích được nó cho một đứa trẻ 15 tuổi hiểu.

Do đứa trẻ 15 vừa đủ thông minh để hiểu một điều gì đó có cấu trúc và logic, không phải như một đứa con nít chỉ nghĩ đến những thứ cơ bản. Hai là một đứa trẻ 15 tuổi vẫn chưa có quá nhiều định kiến trong tâm thức (**định kiến** - sẽ có một related post cho chủ đề này - related) nên nó chỉ đọc hiểu chứ không phán xét.

Lúc 15 tuổi mình đã cố tìm một tài liệu như thế này để đọc về một điều gì đó trên thế giới, nhưng không có. Lúc đó mình chật vật với việc cố hiểu các công thức hóa học, và là một kẻ ngây ngô. Phải tới năm 17, thứ đầu tiên mà mình tự học được là tạo map Warcraft.

Vậy, quay lại với bản tóm tắt về mã hóa đi, cái này trên trang web của một sàn thương mại điện tử rất lớn hiện tại có một bài viết hay đến mức bản tóm tắt này chỉ là bản tóm tắt của bài đó (mình không nêu tên ra vì mình muốn các bài viết này không nằm trên thứ tự thời gian nào của thực tại cả, nó chỉ xuất hiện thôi):

(*Và cũng không dùng định nghĩa màu sơn để không phải giống bản tóm tắt của bài viết trên, nhưng định nghĩa màu sơn rất rất dễ hiểu nếu bạn muốn tìm hiểu*)

Nhưng dùng tên Alice và Bob:

Bối cảnh là, Alice muốn gửi thư cho Bob, nhưng Alice và Bob đều không muốn đơn vị chuyển phát thư đọc được thư của họ. Nhưng đơn vị chuyển phát, dù không muốn, và không hề đọc hay có ý đọc nội dung, vì một lý do gì đó vẫn phải xác nhận đây là một bức thư có nội dung, đây là thông lệ. Và điều này cả Alice và Bob đều không mong muốn.

Vì vậy, sau một hai ngàn năm phát triển hệ thống chuyển phát thư tín của loài người. Alice và Bob cũng phát hiện ra một cách có thể gửi thư cho nhau mà không cần để cho đơn vị trung gian (hay ai đó) đọc được hoặc cố ý đánh cắp nội dung. Bằng cách "mã hóa" thư của họ trước khi gửi bằng một mật mã bí mật.

> Gửi text thì thông qua nhà mạng, gửi qua app thì thông qua nhà cung cấp app hoặc hệ quản trị cơ sở dữ liệu.

Mật mã bí mật này chả ai biết ngoài riêng họ, người còn lại cũng không biết.

##### Câu hỏi tiếp theo là: How?

Làm thế nào mà mã hóa thư, ví dụ như, Alice mã hóa thư của Alice bằng mã bí mật chỉ Alice biết, thì làm sao người kia biết mã bí mật đã mã hóa cái thư đó là gì để giải mã? *(Trước bước đi này thì thư đã mã hóa rồi nên đơn vị chuyển phát nếu có đọc nội dung thì chỉ là một tập hợp mấy cái mã không thể hiểu gì)*

Cách làm như sau:

- Alice và Bob, mỗi người có một **mã bí mật riêng, chỉ có họ biết**.
- Alice và Bob thống nhất một **mã chung có thể chia sẻ công khai** ai cũng có thể biết (*ở đây đơn vị trung gian có thể cung cấp cho họ khóa chung cũng được không vấn đề gì - theo cách thực hiện thực tế*)
- Sau đó, họ tiến hành một thao tác tạm gọi là **trộn mã khóa** (*tạm gọi, trong thực tế dùng công thức toán, này nói sau hoặc chút nói, nhưng trên cơ bản là cũng giống trộn*).
- Thao tác trộn đơn giản là Alice trộn mã bí mật của Alice với khóa chung và gửi cho Bob, ngược lại bob cũng trộn mã bí mật của Bob với khóa chung và gửi cho Alice. **Mỗi bên nhận được mã khóa đã trộn của người còn lại.**

> Đúng ra mình không nên cắt tóc ngay bây giờ hoặc tỉa gọn một chút thôi!

- Sau khi nhận được mã khóa đã trộn của bên còn lại, Alice **dùng mã riêng** của Alice **để trộn vào khóa trộn** mà Bob đã gửi. Bob cũng dùng khóa riêng của Bob trộn vào khóa trộn mà Alice đã gửi. **Việc này đảm bảo cả hai đều có được mã khóa y như nhau** mà không phải tiết lộ cho đơn vị trung gian hay người còn lại mã khóa riêng của mình.
- Tới đây là **xong giao thức bảo mật**, phần còn lại là cả hai lấy cái mã khóa như nhau đó để mã hóa nội dung thư cần gửi. Như vậy là đảm bảo không chia sẻ key bí mật cho bất cứ ai cũng như bảo mật toàn bộ nội dung cần gửi mà chỉ người nhận mới có thể giải mã và đọc được.

##### Tản mạn về công thức toán học dùng để "trộn":

Ví dụ bằng công thức:  **$g^x \mod p = X$**  (X là mã khóa đã trộn)
-  g là một số khác 0
- x là khóa bí mật của Alice hoặc Bob
- p là một số nguyên tố khổng lồ
-  **X** là **mã khóa đã trộn** được gửi công khai

Đây là một hàm một chiều, một phương trình tìm x biết công thức tính ra X là như trên và không biết thêm gì cả.

Nghĩa là không có cách nào để giải phương trình ngoài việc thử từng trường hợp giá trị **x** đến khi tìm ra kết quả đúng.

Chi tiết hơn, với giả sử công thức trên là khóa 2048 bit, thì số lượng khả năng để thử là $\sim 2^{2048}$ khả năng

Với thời gian cần để thử hết các khả năng là: $T = \frac{2^{2048}}{S}$ Với S là số phép thử mỗi giây. Ví dụ ta có một siêu máy tính hiện đại có S $\sim 10^{18}$ phép tính/giây (với các phép tính đơn giản)

Nhưng giả sử có máy thử được $10^{20}$ phép tính/giây và có 1 tỷ máy như vậy, nghĩa là S = $10^{29}$ 

Ta có được công thức tính thời gian cần để thực hiện tất cả các phép thử là: $T = \frac{2^{2048}}{2 \times 10^{29}}$ (chia 2 vì mỗi phép tính chỉ cần nửa không gian) 

Trong đó: $( 2^{10} \approx 10^3 ) → ( 2^{2048} = (2^{10})^{204.8} \approx 10^{616} )$

-> Ta có thời gian cần để thực hiện tất cả các phép thử là $( T \approx \frac{10^{616}}{2 \times 10^{29}} = 5 \times 10^{586} )$ 

**Một năm thì có ~ $( 3.15 \times 10^7 )$ giây** 

-> Suy ra thời gian cần là  $( T \approx 1.5 \times 10^{579} )$ năm

Mà tuổi vũ trụ là 1.38 tỷ năm, là ~ $( 1.38 \times 10^{10} )$ năm

-> Suy ra chúng ta cần ~ $10^{569}$ lần số tuổi của vũ trụ để giải mã

>Xong phần tản mạn

Về cơ bản thì việc giải mã ngược là bất khả thi với hàm một chiều, nhưng không biết có *thiên tài* nào có thể nghĩ ra cách khai thác lỗ hỗng trong cách thức gửi dữ liệu mã khóa hay không. Nhưng theo phương pháp nêu trên hiện tại là không có. Đây gần như là bảo mật tuyệt đối.

> Hoặc là nghĩ về nguyên lý phép thử, như Hàn Tín

---
Không biết mình đã muốn viết ra Nguyên tắc mã hóa đầu cuối này từ hôm nào rồi. Nhưng cứ nghĩ tới nghĩ lui, và không biết post lên đâu hay dựng thêm một blog riêng cho ứng dụng đang làm, vì nó nghiêng về Toán hay lập trình nhiều hơn là Triết học. Hiện tại mình không có ý nói rằng mình biết về những mảng này, chỉ có vô tình tìm hiểu một số ít.

Mình vẫn cứ tự dằn vặt mình mỗi khi đi hớt tóc về. Mong là lần cắt tóc này mình có thể để dài thật dài như ý mình muốn.

---
> Shen2H x Scorprien: from ashes