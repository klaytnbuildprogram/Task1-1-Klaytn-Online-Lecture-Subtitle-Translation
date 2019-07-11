# 2. Các nhược điểm của nền tảng Blockchain

## 2.1 Khả năng mở rộng
 
 
Khả năng mở rộng có nghĩa là việc mở rộng nền tảng. 
Hiểu đơn giản là nó có thể xử lý nhiều công việc một cách nhanh chóng. 
Chúng tôi không biết Bitcoin hay Ethereum sẽ giải quyết vấn đề về khả năng mở rộng như thế nào, mặc dù họ vẫn đang làm việc để giải quyết vấn đề này. 
Hãy nói về khả năng mở rộng, và tại sao lại quan trọng.

Về khả năng mở rộng, chúng tôi sử dụng thuật ngữ TPS và khoảng thời gian block. 
TPS là từ viết tắt của giao dịch mỗi giây, có nghĩa là bạn có thể kiểm tra số lượng giao dịch trong mỗi giây có thể được xử lý. 
Khoảng thời gian block là khoảng thời gian mà mỗi block được tạo.

Chúng tôi có sự so sánh nhiều lần giữa tốc độ xử lý của Blockchain với Visa. Visa xử lý trung bình 1.700 giao dịch mỗi giây. 
Đối với Bitcoin, điều đáng buồn rằng nó chỉ có thể xử lý 7 giao dịch mỗi giây. 
Nhưng trên thực tế, Bitcoin chỉ có thể xử lý 2 đến 5 giao dịch mỗi giây.
Ethereum thì tầm khoản 15 đến 20 giao dịch mỗi giây.

Khoảng thời gian tạo ra một block của Bitcoin là 10 phút, và thời gian tạo block của Ethereum là 15 đến 20 giây. 
Vì vậy, nếu Ethereum là 20 tps và thời gian tạo block là 15 giây, thì 20 nhân 15, tổng cộng sẽ có 300 giao dịch trong một block.


Đây là một câu hỏi. 
Nếu bạn có một nền tảng blockchain với tps lên tới 10.000 và khoảng thời gian block là 10 phút thì trải nghiệm người dùng sẽ như thế nào? 
Vâng, điều đó có nghĩa là phải mất tới 10 phút để hoàn thành xong một block với 10.000 giao dịch trong một giây. 
Điều gì xảy ra sau đó? 
Chỉ đơn giản tôi muốn gửi tiền cho bạn bè, tôi nhấn nút chuyển và có thể mất tới 10 phút mà giao dịch vẫn chưa hoàn thành.
Điều này không có nghĩa.
Ethereum thì ngắn hơn đáng kể so với Bitcoin, nhưng 15 đến 20 giây cũng là khá dài đối với người dùng. 
Chúng tôi cảm thấy thất vọng vì không nhận được kết quả nào có thể xử lý trong 5 giây trên Internet. 
Điều này là không thể chấp nhận được ở thế kỷ 21.


Vậy, lý do tại sao các Blockchain hiện nay lại chậm. 
Lý do đầu tiên, đặc điểm của một mạng blockchain được đặc trưng bởi một thực tế là nhiều node, nhưng nhiều node không có nghĩa là mạng lưới đó nhanh hơn. 
Các dịch vụ phổ biến như web cũng như mobile của chúng tôi có số lượng máy chủ lớn để đảm bảo sự đáp ứng nhanh chóng cho người dùng khi lượng lớn yêu cầu được gửi tới, các yêu cầu sẽ được phân tách và xử lý.

Mặc dù, một máy chủ được gọi là một node - tạo thành ra mạng lưới blockchain, khi nhận 100 công việc thì sẽ xử lý toàn bộ công việc mà không bị phân tán. 
Như vậy, mỗi node sẽ lặp lại cùng một công việc. 
Kết quả là hiệu suất của toàn bộ mạng lưới sẽ bị chậm lại. 
Hiệu suất của một máy tính không có gì khác biệt so với hàng chục ngàn mạng lưới hoặc máy tính khác. 
Do đó, các mạng blockchain như Bitcoin hay Ethereum không thể xử lý một block lượng giao dịch lớn và chính bản thân mạng lưới chậm đi.
 
 
## 2.2 Thiếu tính hữu hạn
 

Tính hữu hạn đề cập đến trạng thái cuối cùng không thể thay đổi. 
Tính hữu hạn của một block trong blockchain đảm bảo các giao dịch trong block không bị thay đổi. 
Mọi người tin chắc rằng giao dịch này sẽ hoàn thành mà không có nghi ngờ nào. 
Tuy nhiên, cơ chế khai thác trong Bitcoin và Ethereum lại thiếu tính hữu hạn. 
Ví dụ, tôi dùng Bitcoin để mua vé máy bay. 
Giao dịch sẽ được tạo ra tại thời điểm đó. 
Điều này có nghĩa là một giao dịch đó được lưu lại trong hồ sơ. 
Tuy nhiên, giao dịch này không được xử lý ngay. 
Nhưng không có gì đảm bảo. 
Nó chỉ cung cấp tính hữu hạn để cuối cùng các giao dịch được xử lý. 
Điều đó có nghĩa là tôi đã thanh toán nhưng sau đó tôi nhận ra việc thành toán vẫn chưa thành công.

Bây giờ hãy xem trung bình mất bao lâu để đạt đến mức trung bình.

(bảng)

Nếu bạn nhìn vào bức tranh này, trong trường hợp với Bitcoin, trung bình mất 60 phút để đạt đến tính hữu hạn. 
Việc khai thác một block mất 10 phút, nhưng tốn 1 giờ với 6 bước để đạt tính hữu hạn. Còn với Ethereum thì phải mất 6 phút để đạt tính hữu hạn. 
Nếu bạn xác minh bước này, mức độ giao dịch của bạn đáng tin cậy hơn. 
Nhưng sẽ mất rất nhiều thời gian để thực hiện bước xác minh này vài lần. Vì điều này khiến tiền mã hóa rất khó thương mại hóa. Sau khi bạn thanh toán xong, tốc độ đạt đến tính hữu hạn là không khả thi. 
Có bao nhiêu người sẵn sàng đợi đến một tiếng? 
Vì vậy, tính hữu hạn đóng một vai trò rất quan trọng. 
Có một khó khăn nhỏ, tính hữu hạn cần khoảng thời gian chờ nhất định để đảm bảo giao dịch sẽ không bị thay đổi.

Cuối cùng, việc chờ đợi trong thời gian dài ở mạng lưới blockchain có thể có tác động đáng kể đến doanh nghiệp của bạn, vì vậy tính hữu hạn nhanh đóng vai trò như là một loại tài sản kinh doanh. 
Từ nãy giờ, tôi đã ngắn gọn tầm quan trọng tính hữu hạn trong mạng lưới blockchain ngày nay.
 
## 2.3 Fork
 
 
Fork đề cập đến hiện tượng kết nối của các block được chia thành hai hoặc nhiều nhánh. 
Lý do fork xảy ra là vì tất cả những người tham gia vào mạng blockchain P2P có thể khai thác độc lập với nhau. 
Đầu tiên, tôi sẽ giải thích về PoW trong Bitcoin hoặc Ethererum. 
PoW giải quyết giá trị băm để thêm vào các block trên mạng lưới Blockchain. 
Các node cạnh tranh nhau để giải quyết vấn đề này. Đôi khi hai node giải quyết vấn đề tại cùng một thời điểm. 
Sau đó, hai block đóng vai trò như ứng cử viên được thêm vào mạng lưới blockchain. 
Tại thời điểm này, sẽ xuất hiện thêm nhánh.

Ví dụ: Giả sử bạn đang khai thác từ hai node
Node A và node B. 
Một ngày nọ, tôi chuyển tiền cho bạn tôi. 
Sau đó, giao dịch xảy ra và đi vào pool giao dịch. 
Các node A, B đặt giao dịch này trong pool của mỗi block riêng để tạo block. 
Tại thời điểm này, cả hai node bao gồm các giao dịch mà tôi đã gửi cho bạn tôi.

Giai đoạn cuối của quy trình này, các node sẽ giải quyết các vấn đề thêm trong block riêng của chúng vào blockchain đang có. 
Các node phải trải qua một quá trình tính toán về độ khó, các node A và B phải giải quyết quy trình tính toán độ khó. 
Sau đó, các node này sẽ lan truyền vấn đề này đến các node khác.

Khi sự lan truyền này xảy ra, một số node nhận được block màu tím từ node A và các node khác nhận được block màu đen từ nút B. Đây là nơi nhánh được tạo ra như trong block thứ ba. Trong quá trình lan truyền, các node sau khi nhận được một block màu tím, sẽ nhận một block màu đen sau đó. Nhưng các node này bỏ qua block màu đen. Bởi vì giao dịch tôi gửi cho bạn tôi đã được thêm vào block màu tím. Ngược lại, các node nhận được một block màu đen sẽ từ chối các block khác vì chúng chứa trong cùng giao dịch ở block màu tím.

Tiếp theo, chúng tôi tìm giá trị băm từ node C để giải quyết vấn đề và tạo và lan truyền tới block thứ tư. Trong trường hợp này, node C tạo ra block thứ tư và cũng nhận được block đen thứ ba. Blackline sẽ được thêm vào vì nó chứa hàm băm “cha” của block đen thứ ba.

Tuy nhiên, các node có chứa block màu tím thứ ba sẽ từ chối block màu đen thứ tư đến sau. Thậm chí block đen thứ 4 hợp lệ thì vẫn bị từ chối. Bởi vì hàm băm “cha” của block màu đen thứ 4 không phải là block màu tím thứ 3.

Sau đó, các node ngay lập tức loại bỏ block màu tím thứ 3 vừa được nhận và tiến hành tải lại, bắt đầu với block đen thứ 3. Điều này có nghĩa là Blackline sẽ được duy trì mãi. Chuỗi càng dài, càng có nhiều khả năng công nhận cho block tiếp theo và được thêm vào blockchain. Đây là quy tắc chuỗi dài nhất. Quá trình phân nhánh và sáp nhập được tiến hành một cách rất tự nhiên. Tuy nhiên, quy tắc này sẽ không mang lợi ích cho một vài khía cạnh. Ví dụ, nếu tôi có hơn 51% sức mạnh tính toán, tôi có thể đào nhanh hơn nhiều và tạo ra nhiều block hơn so với các thợ mỏ khác. Điều này có nghĩa là bạn sẽ có thể tiếp tục với chuỗi mà bạn vừa tạo.

Ví dụ, nhánh được hình thành trong block thứ ba. Tôi tạo ra một block màu đen và như thường lệ phải đợi block thứ tư, nhưng trong trường hợp tôi không cần phải đợi một node khác tạo ra block. Thay vào đó tôi có thể tạo và thêm block thứ tư vì sức mạnh hàm băm cho phép tạo các block nhanh hơn. Theo cách này, tôi không phải lan truyền cái chuỗi này sang các node khác và tôi tiếp tục mở rộng chuỗi của mình một cách bí mật. Ở quá trình này, bạn có thể phớt lờ các giao dịch có địa chỉ cụ thể trong block của tôi, hoặc ghi lại rằng tôi đã không bán coin ra tiền mặt. Đây là nơi mà chuỗi trong blockchain đang hoạt động. Đây là quy tắc thêm block vào mạng lưới blockchain bằng cách chọn chuỗi dài nhất ở cuối nhánh. Điều này có nghĩ chuỗi dài nhất, thì có nhiều block hợp lệ được thêm vào chuỗi trong blockchain. Một khi mạng lưới bị phá vỡ thì sẽ phải mất rất nhiều thời gian để hoàn thiện vì chuỗi phải trải qua giai đoạn xác thực lâu hơn.
