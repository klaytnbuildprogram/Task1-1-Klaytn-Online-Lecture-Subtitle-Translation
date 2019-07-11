# 2. Điểm yếu của nền tảng Blockchain

## 2.1 Khả năng mở rộng

Khả năng mở rộng có nghĩa là mở rộng nền tảng. 
Bạn có thể hiểu đơn giản là nó có thể xử lý mọi thứ nhanh như thế nào. 
Chúng tôi không biết liệu Bitcoin hay Ethereum sẽ giải quyết vấn đề về khả năng mở rộng như thế nào, mặc dù họ vẫn cứ nói rằng họ đang làm việc với vấn đề đó. 
Hãy cùng nói về khả năng mở rộng là gì và tại sao nó lại quan trọng như vậy.

Về khả năng mở rộng, chúng tôi sử dụng thuật ngữ TPS và thời gian tạo khối. 
TPS là tên viết tắt của Số giao dịch mỗi giây (Transaction Per Second), nghĩa là bạn có thể kiểm tra số lượng giao dịch mỗi giây có thể được xử lý. 
Thời gian tạo khối là khoảng thời gian mà mỗi khối được tạo ra.

Chúng ta thường hay so sánh tốc độ xử lý của blockchain với Visa. Người ta nói rằng Visa đang xử lý trung bình khoảng 1700 giao dịch mỗi giây. 
Trong trường hợp của Bitcoin, người ta nói rằng nó có thể xử lý được 7 giao dịch mỗi giây.
Trong thực tế, nó có thể xử lý từ 2 đến 5 giao dịch
 Ethereum được cho là từ 15 đến 20 TPS.

Thời gian tạo khối của Bitcoin là 10 phút và của Ethereum là từ 15 đến 20 giây. 
Vì vậy, nếu Ethereum là 20 TPS và thời gian tạo khối là 15 giây, lấy 20 nhân với 15 thì tổng cộng 300 giao dịch sẽ nằm trong một khối.

Bây giờ là câu hỏi.
 Nếu bạn có một nền tảng blockchain với tốc độ 10,000 TPS và thời gian tạo khối là 10 phút, trải nghiệm người dùng sẽ như thế nào? 
Phải. Điều đó có nghĩa là nó phải mất tới 10 phút để hoàn thành một khối đang xử lý 10 nghìn giao dịch trong 1 giây. 
Vậy điều gì xảy ra sau đó? 
Tôi đơn giản là chỉ muốn gửi tiền cho bạn mình, vì vậy tôi nhấn nút chuyển và có thể mất tới 10 phút mà không hoàn thành giao dịch. 
Nó chẳng có nghĩa gì cả. 
Ethereum có thời gian tạo khối ngắn hơn đáng kể so với Bitcoin, nhưng 15-20 giây là khá dài đối với người dùng. 
Chúng tôi khá thất vọng khi không nhận được bất kỳ kết quả trong vòng 5 giây nào trên Internet. 
Điều đó không nên xảy ra trong thế kỷ 21.

Vì vậy, hãy xem tại sao blockchain hiện nay lại chậm hơn. 
Đầu tiên, đặc điểm của một mạng lưới blockchain là nếu nó có nhiều nút hơn thì không có nghĩa mạng của nó sẽ nhanh hơn. 
Các dịch vụ web và dịch vụ di động thông dụng của chúng ta tăng số lượng máy chủ để đáp ứng nhanh nhất có thể cho người dùng và khi một số lượng yêu cầu lớn được gửi đến, chúng được triển khai và xử lý riêng.

Tuy nhiên, một máy chủ được gọi là một nút cấu thành nên mạng blockchain phải xử lý 100 công việc mà không phân phối được 100 công việc đi khi nhận được 100 công việc đó. 
Điều đó có nghĩa là, mọi nút lặp lại cùng một thứ. 
Kết quả là hiệu suất của toàn bộ mạng bị hạ xuống bằng với nút chậm nhất. 
Hiệu năng của một máy tính không có gì khác biệt so với hàng chục ngàn mạng hoặc máy tính khác.
Do đó, những mạng blockchain như Bitcoin hay Ethereum không thể xử lý khối lượng giao dịch lớn và chính mạng lưới của nó cũng khá chậm.

## 2.2 Thiếu tính hữu hạn

Tính hữu hạn đề cập đến trạng thái cuối cùng không thể thay đổi. 
Tính hữu hạn của một khối trong blockchain giúp đảm bảo cho các giao dịch trong khối không bao thể bị thay đổi. 
Giao dịch phải được tin là đã được hoàn thành mà không có một chút nghi ngờ nào. 
Tuy nhiên, cơ chế khai thác của bitcoin và ethereum thiếu đi tính hữu hạn này. 
Ví dụ, tôi trả tiền mua vé máy bay bằng bitcoin.
Sau đó, giao dịch sẽ được tạo ngay lập tức. 
Có nghĩa là một giao dịch có thể để lại trong một bản ghi được tạo ra trên blockchain.
Tuy nhiên, giao dịch này không được xử lý ngay lập tức. 
Nó không phải là một sự đảm bảo hoàn hảo. 
Nó chỉ cung cấp một xác suất hữu hạn mà cuối cùng sẽ được xử lý.
Điều đó có nghĩa là tôi đã thanh toán nhưng sau đó nó có thể chưa được thanh toán.

Bây giờ chúng ta hãy xem phải mất bao lâu để đạt được tính hữu hạn trên mức trung bình.

(Bảng hình ảnh) 

Nếu bạn nhìn vào bảng này, với bitcoin, thời gian trung bình để đạt đến mức tới hạn là 60 phút. 
Thời gian khai thác khối mất 10 phút, nhưng phải mất 1 giờ với 6 bước để đạt đến mức tới hạn. Ethereum nói rằng nó mất 6 phút để đến mức tới hạn. 
Bạn xác minh bước này càng nhiều thì khả năng thì giao dịch của bạn đủ tin cậy càng cao. 
Nhưng nó mất quá nhiều thời gian vì chúng ta phải thực hiện các bước xác minh này thêm một vài lần. Bởi vậy mà tiền mã hóa rất khó được thương mại hóa. Sau khi bạn thực hiện thanh toán, tỷ lệ thanh toán đạt đến mức hữu hạn là rất hiếm.
 Bao nhiêu người có thể chờ đến một giờ? 
Vì vậy, tính hữu hạn một vai trò rất quan trọng. 
Với một chút độ khó, tính hữu hạn đo lường thời gian cần thiết phải chờ để có được sự đảm bảo hợp lý rằng một giao dịch là không thể thay đổi.

Cuối cùng là, việc chờ đợi một thời gian dài trên mạng blockchain có thể gây ra tác động đáng kể đến doanh nghiệp của bạn, vì vậy mà tính hữu hạn nhanh là một tài sản quan trọng cho doanh nghiệp. 
Đến lúc này tôi đã giải thích ngắn gọn về sự thiếu sót của tính hữu hạn trong các blockchain phổ biến hiện nay.

## 2.3 Fork

Fork (phân nhánh) đề cập đến hiện tượng các kết nối của các khối bị chia thành hai hoặc nhiều nhánh. 
Lý do xảy ra phân nhánh là vì tất cả những người tham gia vào mạng blockchain p2p có thể khai thác một cách độc lập. 
Đầu tiên, tôi sẽ giải thích về thuật toán Bằng chứng công việc (PoW) của Bitcoin và Ethereum. 
Nó giải quyết vấn đề tìm giá trị băm để thêm các khối vào mạng blockchain. 
Một số nút cố gắng giải quyết vấn đề trong lúc cạnh tranh với các nút khác. 
Đôi khi hai nút giải quyết vấn đề cùng một lúc. 
Sau đó, hai khối tạm thời được thêm vào blockchain.
Tại thời điểm này, việc phân nhánh xảy ra.

Ví dụ: giả sử bạn đang khai thác từ hai nút.
Nút A và B. 
Một hôm tôi chuyển tiền cho bạn mình.
Sau đó, một giao dịch xảy ra và đi vào pool giao dịch. 
Nút A, B đặt ngay các giao dịch trong pool giao dịch vào các khối riêng của chúng để tạo khối.
Tại thời điểm này, cả hai nút chứa các giao dịch mà tôi đã gửi cho bạn mình.

Vào cuối quá trình này, các nút giải quyết vấn đề thêm các khối riêng của chúng vào blockchain hiện có. 
Các nút phải trải qua một quá trình tính toán độ khó và cả hai nút A và B đều giải quyết được vấn đề. 
Sau đó, các nút lan truyền nó đến các nút khác mà tôi đã giải quyết.

Khi sự lan truyền này xảy ra, một số nút nhận được khối màu tím từ nút A và các nút khác nhận được khối màu đen từ nút B. 
Đây là nơi sự phân nhánh xảy ra như trong khối thứ 3. 
Các nút nhận được một khối màu tím trong quá trình lan truyền cũng sẽ nhận được một khối màu đen sau đó.
Nhưng chúng sẽ bỏ qua khối màu đen. 
Bởi vì giao dịch tôi gửi cho bạn mình đã được thêm vào khối màu tím. Ngược lại, các nút nhận được khối màu đen sẽ bỏ qua các khối khác vì chúng chứa cùng một giao dịch khi nhận được khối màu tím.

Tiếp theo, chúng ta tìm ra giá trị băm từ nút C, giải quyết vấn đề, tạo và truyền khối thứ 4. 
Trong trường hợp này, nút C tạo ra khối thứ 4 là nút nhận khối màu đen thứ 3. 
Blackline sẽ được thêm vào vì nó có hàm băm "cha" (parent hash) của khối màu đen thứ 3.

Tuy nhiên, các nút có khối màu tím thứ 3 không thể nhận được nó khi khối màu đen thứ 4 đến sau. 
Ngay cả khi nó rõ ràng là một khối hợp lệ được tạo bằng cách giải quyết vấn đề và khối thứ 4 đến cùng với chiều cao của khối thì nó vẫn có thể không được nhận. 
Bởi vì hàm băm "cha" của khối thứ 4 không phải là khối màu tím thứ 3 mà lại là khối màu đen.

Sau đó, các nút nhận được khối màu tím thứ 3 ngay lập tức bỏ qua khối màu tím mà chúng đang có và tiến hành tải xuống một lần nữa, bắt đầu từ khối màu đen thứ 3. 
Điều đó có nghĩa là chuỗi đen sẽ dài hơn.
Chuỗi càng dài thì nó càng có nhiều khả năng nó được công nhận là khối tiếp theo và được thêm vào blockchain. 
Đây là quy tắc về chuỗi dài nhất. 
Quá trình phân nhánh và hợp nhất này diễn ra một cách rất tự nhiên.

 

Tuy nhiên, có một số trường hợp quy tắc này có thể được sử dụng với mục đích xấu. 
Ví dụ: nếu tôi có hơn 51% tổng sức mạnh tính toán, tôi có thể khai thác nhanh hơn nhiều và tạo ra nhiều khối hơn sơ với các thợ mỏ khác. 
Điều này có nghĩa là bạn sẽ có thể tiếp tục với chuỗi bạn đã tạo ra trong quá trình phân nhánh.

Ví dụ, trong khối thứ 3, một nhánh được hình thành. 
Tôi đã tạo ra một khối màu đen và phải đợi đến khối thứ 4 như thông thường, nhưng không cần phải đợi đến khi một nút khác tạo ra một khối mà tôi có thể tạo và thêm nó trong trường hợp này. Sức mạnh băm lớn hơn cho phép tạo ra các khối nhanh hơn. Theo cách này, tôi không phải truyền chuỗi này này sang các nút khác và tôi tiếp tục mở rộng chuỗi của mình một cách bí mật. 
Trong quá trình này, bạn có thể bỏ qua các giao dịch ở một địa chỉ cụ thể trong khối của tôi hoặc ghi lại việc tôi chưa từng bán đồng coin của mình lấy tiền mặt. 
Đây là nơi mà chuỗi của tôi trên mạng lưới hoạt động. 
Đây là quy tắc thêm khối vào blockchain bằng cách chọn chuỗi dài nhất ở cuối nhánh. Nói cách khác, nếu chuỗi của tôi có nhiều khối hơn so với các chuỗi khác thì nó là một chuỗi "hợp lệ" được thêm vào mạng lưới blockchain. Do đó, chúng ta có thể khiến cho mạng lưới bị nhầm lẫn bằng cách sử dụng quy tắc này và khi điều đó xảy ra, mạng lưới phải mất một thời gian dài để hoàn tất vì chuỗi đó phải trải qua một giai đoạn xác nhận lâu hơn.
