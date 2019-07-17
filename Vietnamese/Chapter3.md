# 3. Tìm hiểu về "Klaytn"

## 3.1 Cơ chế đồng thuận



 Trong các tập trước, chúng ta đã cùng nhau thảo luận về những vấn đề mà blockchain hiện tại đang gặp phải. Bây giờ hãy nói về cách blockchain Klaytn giải quyết vấn đề bằng thuật toán đồng thuận. Có nhiều loại thuật toán đồng thuận, chẳng hạn như PoW (Bằng chứng công việc) hay PoS (Bằng chứng cổ phần), thường được sử dụng trong các Blockchain công khai (Public Blockchain) và PBFT (Ngưỡng chịu lỗi Byzantine thực tế) hoặc Raft, được sử dụng trong các Blockchain riêng tư (Private Blockchain). Nhìn chung, blockchain riêng tư có thể đạt được thỏa thuận nhanh hơn so với blockchain công khai. Đặc biệt, blockchain riêng tư dựa trên BFT có thể đạt được hiệu suất và hiệu quả cao bằng cách giới hạn số lượng nút tham gia mạng lưới. Tuy nhiên, cấu hình này giới hạn số lượng nút tham gia đồng thuận, làm giảm đi tính phi tập trung và chỉ một số nhóm nhỏ được tiết lộ về nội dung của kết quả đồng thuận. Do đó, nó hạn chế tính minh bạch và ảnh hưởng xấu đến lợi ích của blockchain.

Mặt khác, Klaytn chọn thuật toán đồng thuận Istanbul BFT vì chúng tôi tin rằng bằng cách sử dụng tốt những ưu điểm của BFT, nó có thể kết hợp những điểm tốt nhất của cả blockchain công khai và riêng tư. Klaytn hướng đến việc trở thành một blockchain công khai mang lại hiệu suất và sự ổn định trong khi vẫn duy trì được tính bảo mật và minh bạch mạnh mẽ cho các doanh nghiệp lớn. Để đạt được mục tiêu này, Klaytn thông qua một mô hình tin tưởng cho các đồng thuận riêng được tiết lộ công khai. Nó bao gồm một số lượng nhỏ các nút riêng tư cùng đạt được sự đồng thuận, và các nút khác có thể truy cập công khai cũng như kiểm tra kết quả tạo khối. Bây giờ chúng ta hãy xem chi tiết về Istanbul BFT (Ngưỡng chịu lỗi Byzantine) mà Klaytn sử dụng làm thuật toán thỏa thuận.




Quá trình đồng thuận của Istanbul BFT bao gồm ba bước. Chuẩn bị trước, chuẩn bị, và cam kết. Klaytn sử dụng một phương pháp round-robin (luân phiên) để chọn nút đề xuất (proposer) trong các nút đồng thuận mỗi vòng. Nó đưa ra đề xuất. Các nút đồng thuận còn lại là nút xác thực (validator). Nó thực hiện việc xác minh.

Nếu bạn nhìn vào hình, có những nút đề xuất, nút xác thực 1, 2, 3, và vân vân. Trong số đó, các nút được đánh dấu X là ở là đang ở trong tình trạng bị lỗi. Có nghĩa rằng nó đang không hoạt động bình thường như một nút xác minh. Khi máy tính bị hỏng, mạng lưới bị ngắt kết nối, hoặc máy tính gây hại có thể khiến điều này xảy ra.

Bước đầu tiên là "đề xuất" đưa ra từ một trong các nút đồng thuận được chọn làm nút đề xuất. 
Bước thứ hai là chuẩn bị trước nơi nút đề xuất tạo khối và đưa ra đề xuất cho các nút khác. 
Sau đó, gửi đề xuất đến nút xác thực 1, nút xác thực 2, và nút xác thực 3. 
Đây là bước để được thông qua cùng với thông điệp.



Trong bước chuẩn bị thứ 3, khi nút xác thực 1, 2, hoặc 3 nhận được thông điệp từ nút đề xuất, chúng gửi đi thông điệp đã nhận được thành công đến các nút khác. Nút xác thực 1 và 2 sẽ gửi thông điệp tới cả 3 nút. 
Tuy nhiên, nút xác thực 3 không gửi mà chỉ nhận thông điệp vì nó hiện đang bị lỗi.

Vào cuối trạng thái chuẩn bị, bạn có thể xem có bao nhiêu nút bên trong hệ thống. Giống như hình ảnh này, chúng ta có thể thấy rằng cả 3 đều tồn tại: nút đề xuất, nút xác thực 1, và nút xác thực 2. 
Quá trình này đảm bảo cho tất cả các nút xác minh nằm trong cùng một vòng.




Cuối cùng, trong giai đoạn cam kết, quá trình giao tiếp với các nút khác diễn ra để quyết định xem có nên chấp nhận một khối nhận được từ một nút đề xuất không. Ví dụ, nó sẽ gửi phản hồi tới các nút để kiểm tra xem khối từ nút đề xuất là đúng hay sai. Nếu hơn 2/3 số nút đồng ý, khối đó sẽ được chấp thuận ngay lập tức. Sau cùng, nó được quyết định trong giai đoạn cam kết và cuối cùng sẽ được tạo ra. Điều đó có nghĩa là ở giai đoạn này, việc thiếu sót tính hữu hạn không còn nữa và trạng thái cuối cùng không thể thay đổi được hình thành. Nó không ở trong trạng thái mơ hồ như PoW.

Vì vậy, ưu điểm của nó là đồng thuận nhờ vào giao tiếp và hoàn thành ngay lập tức. Tuy nhiên, có một nhược điểm là lưu lượng tăng theo cấp số nhân khi số nút đồng thuận tăng lên. Phần này được thiết lập để chỉ chọn một phần của nút đồng thuận và duy trì hình thức BFT.

Hãy xem cách khối được tạo ra và lan truyền trong bài học tiếp theo.

## 3.2 Tạo và lan truyền khối
Chúng ta hãy cùng xem cách Klaytn tạo và lan truyền các khối để đáp ứng được trải nghiệm người dùng.

Đầu tiên hãy quan sát chu trình tạo khối. Chu trình tạo khối của Klaytn được gọi là một 'vòng', một khối mới được tạo ra mỗi vòng và một vòng mới bắt đầu ngay sau khi vòng trước đó kết thúc. Thời gian tạo khối mất khoảng 1 giây.



Hãy xem cách nút đề xuất và Ủy ban lựa chọn công việc. 
Trong mỗi vòng, nút đề xuất tạo ra các khối được kéo ra từ một trong các nút của Hội đồng quản trị một cách ngẫu nhiên nhưng dứt khoát. Hội đồng quản trị là tập hợp các nút cốt lõi hoặc nút đồng thuận. Nếu bạn nhìn vào ảnh, những vòng tròn này là các nút đồng thuận, trong đó màu xanh được chọn là nút đề xuất của vòng hiện tại. Và sau đó chọn một nhóm các nút đồng thuận làm ủy ban của vòng đó. Chúng là những nút xác thực màu hồng được lựa chọn bởi ủy ban. Cụ thể hơn, mỗi nút đồng thuận sử dụng một số ngẫu nhiên bắt nguồn từ đầu khối gần nhất để tiến hành mã hóa nhằm chứng minh rằng nó đã được chọn cho vòng này.



Chúng ta hãy xem về đề xuất và xác thực khối. 
Khi một nút đồng thuận được chọn làm nút đề xuất, nó sẽ thông báo cho các nút đồng thuận khác về bằng chứng cho thấy nó đã được chọn làm nút đề xuất trong vòng này. Tại thời điểm đó, nó sẽ chứng minh điều này bằng các bằng chứng được mã hóa có thể xác minh với khóa công khai (Public Key) của nút đề xuất. Sau đó, nhóm nút đồng thuận được bầu vào ủy ban nói với nút đề xuất, tương tự như vậy, với bằng chứng chứng minh tại sao họ được chọn làm một thành viên của ủy ban. (Click) Bây giờ bạn biết ai là nút đề xuất và Ủy ban, nút đề xuất sẽ lựa chọn và sắp xếp các giao dịch trong pool giao dịch và tạo ra khối. Sau đó đồng ý với Ủy ban và các khối mới được tạo ra, và kết thúc.


Cuối cùng, chúng ta cùng xem khối lan truyền như thế nào. 
Khối được đề xuất phải có chữ ký của 2/3 số thành viên ủy ban để hoàn thành thành công. Khi ủy ban đạt được thỏa thuận, khối mới được gửi đến tất cả các nút đồng thuận và vòng đồng thuận này kết thúc. Sau đó bạn có thể truyền khối đến các nút tại điểm cuối thông qua (click) nút Proxy. 
Cho đến lúc này, chúng ta đã tìm hiểu về cách các nút đề xuất và ủy ban có thể được lựa chọn và thống nhất để tạo và lan truyền khối.




## 3.3 Cấu trúc mạng

Hãy dành một chút thời gian để giải thích về cấu trúc mạng Klaytn. Bên trái là bản tóm tắt mạng. Có một core cell (phần trung tâm) trong toàn bộ mạng và có một nút điểm cuối (endpoint) bao quanh core cell. Nếu bạn nhìn vào phần mở rộng bên cạnh nó, bên trong ô màu đỏ là core cell của mạng và ô màu xanh bên ngoài là mạng điểm cuối. Trong core cell của mạng, phần màu vàng là Mạng lưới nút đồng thuận - CNN, và phần màu đỏ Mạng lưới nút Proxy - PNN. CNS trong ô vàng sẽ chịu trách nhiệm về sự đồng thuận.



Một core cell được vận hành bởi một người tham gia. Nó hoạt động với một CN và một số nút Proxy kết nối với CN. Để tham gia vào CN, bạn phải đáp ứng nhiều điều kiện chặt chẽ. Và CN đều kết nối để có thể giao tiếp với nhau. Nếu có 10 CN, chúng được kết nối với nhau. Tất cả được kết nối bởi chúng phải giao tiếp với nhau nhanh nhất có thể khi chúng đang trong quá trình đồng thuận. CN không thể kết nối trực tiếp với bên ngoài. Bởi vì nó là một môi trường rất riêng tư không chịu sự can thiệp nào nên có lợi thế trong việc nhanh chóng quyết định liệu có tạo ra khối hay không, như một nút đồng thuận. Vậy bạn có thể tiếp cận nó như thế nào? Là một người tham gia trong core cell, nó giống như việc bạn chạy một mạng proxy mà bạn có thể quản lý và tin tưởng để đại diện cho chúng. 

Và ở bên ngoài, các nút điểm cuối được kết nối với mạng của core cell. Những nút điểm cuối có thể kết nối đến nút proxy trong core cell để nhận được thông tin. Tất nhiên, các nút điểm cuối có thể kết nối và trao đổi thông tin với nhau. Tuy nhiên, nếu các nút điểm cuối kết nối đến nút proxy, bạn có thể nhận được các khối nhanh hơn. Lưu ý rằng không có yêu cầu nào cho việc trở thành một nút điểm cuối. Bất cứ ai cũng có thể là một nút điểm cuối và chuyển thông tin đến khách hàng như trang web hoặc điện thoại di động. Đó là nút điểm cuối đóng vai trò như một nhà cung cấp dịch vụ.


Và một lần nữa, bạn có một nút khởi động CN, một nút khởi động PN, và một nút khởi động EN, là một loại nút đặc biệt được vận hành bởi Klaytn giúp nút mới đăng ký vào mạng và kết nối với nút khác. Nút khởi CN động ở trong mạng CN và không được công bố. Các nút khởi động PN và EN là các nút công khai. Nút khởi động PN chỉ cho phép bạn các nút proxy và giúp bạn kết nối với các nút điểm cuối. Nút khởi động EN cung cấp thông tin đến các nút điểm cuối về việc nút Proxy nào để kết nối. Cho đến lúc này, chúng tôi đã mô tả một cách ngắn gọn về cấu trúc mạng Klaytn.

## 3.4 Core Cell




Hãy nói thêm về Core cell (phần trung tâm). Khi mainnet (mạng chính) ra mắt, Core cell chịu trách nhiệm về sự đồng thuận sẽ hoạt động trong hàng chục đơn vị. Khi các dịch vụ hoạt động tốt hơn, chúng ta nên làm gì về khả năng mở rộng khi có nhiều kết nối đến core cell? 
Trong một trường hợp chung, không phải blockchain, khi người dùng tăng lên, chúng tôi sẽ phát triển máy chủ và chia nhỏ các yêu cầu. Tuy nhiên, trong trường hợp blockchain, số lượng các nút tăng lên có thể làm chậm tốc độ xử lý vì có thêm thông tin cần phải được thông qua mỗi nút cùng với sự phát triển đó. Số lượng các nút tăng lên không làm tăng hiệu suất. Vì vậy, thay vì tăng số nút, tăng hiệu quả hoạt động của nút là cách hợp lý hơn. Ví dụ, bạn có thể tăng hiệu suất của RAM hoặc CPU. Hãy xem xét điều kiện để trở thành một nút đồng thuận. Cấu hình của người tham gia


1. Hơn 40 lõi vật lý
2. 256GB RAM
3. Lưu khoảng 14TB dữ liệu trong một năm
4. Mạng 10G



 Lưu ý rằng hiệu suất cao của một trong những nút đồng thuận từ người tham gia không có nghĩa là tốc độ của toàn bộ mạng core cell cao. Bởi vì các nút còn lại với hiệu suất thấp đang hoạt động với thông số kỹ thuật thấp của chúng. Do đó, để cải thiện hiệu suất của core cell, các nút cần phải có thông số kỹ thuật tương tự nhau để cải thiện hiệu suất.
 
 
 

 Và khi nhìn vào cấu trúc của core cell một lần nữa, ta có thể thấy nó bao gồm một CN và một vài PN. Có nhiều lý do tại sao một nút proxy được gọi là PN. Bởi vì CN bị giới hạn tài nguyên để kết nối và số CN là giới hạn, nó hỗ trợ các kết nối của điểm cuối sử dụng PN. Ví dụ, giả sử các nút điểm cuối có thể kết nối trực tiếp đến CN. Nếu CN này có thể chấp nhận tới một nghìn kết nối điểm cuối, sau đó nếu nó vượt quá số lượng này, nó sẽ được xử lý bởi các CN và nó có thể xử lý sai. Vì vậy, PN đang làm phần này để thay thế. PN kết nối với các nút điểm cuối và chuyển thông tin cho CN. Và vì CN chỉ cần kết nối với một vài PN, nó chỉ phải xử lý ít hơn, và bạn có thể giải quyết các vấn đề kết nối điểm cuối đang cố gắng để kết nối với core cell bằng cách đặt nhiều PN.

Để tóm tắt bài học, vì CN là nút chịu trách nhiệm thỏa thuận, kết nối không nên là một trở ngại cho việc thực hiện. Vì vậy, vai trò của PN là để bảo vệ CN, và các vấn đề về khả năng mở rộng có thể được giải quyết bằng cách đặt nhiều PN.







## 3.5 Chuỗi dịch vụ





Chuỗi dịch vụ của Klaytn là một blockchain hoạt động độc lập được kết nối với mainnet. Ý tưởng này xuất phát từ khả năng mở rộng. Trong trường hợp bạn muốn sử dụng một chuỗi dịch vụ, bạn cần phải đặt nó trong một môi trường nút đặc biệt, hoặc nếu bạn muốn thay đổi mức độ bảo mật, ví dụ, khi muốn chạy một blockchain cá nhân. Dịch vụ thường yêu cầu thông lượng rất lớn. Khi việc phân phối dịch vụ đến mainnet là không khả thi về mặt kinh tế, họ sử dụng các chuỗi dịch vụ.

Nếu bạn nhìn vào ảnh, vòng tròn lớn ở giữa là mainnet. Có thể thấy rằng các chuỗi dịch vụ giữ sự tin tưởng trong chuỗi chính, mà không thể tự do giao tiếp giữa chuỗi chính và chuỗi dịch vụ, và chỉ một số giao dịch hạn chế có thể được sử dụng. Ngoài ra, việc truyền tải của KLAY sẽ được phép chỉ khi có những hạn chế sau này





Nói cách khác, các chuỗi dịch vụ xây dựng một không gian dịch vụ riêng biệt và khóa tin cậy trên mainnet khi cần thiết. Nền tảng blockchain khác cũng đang tiến tới việc áp dụng công nghệ như các chuỗi dịch vụ. Trong trường hợp của Ethereum, tôi cảm thấy nó có hạn chế về năng lực và tốc độ của mainnet. Chúng ta hầu như đều biết Crypto Kitty, là nguyên nhân làm cho mạng chính Ethereum bị tắc nghẽn nghiêm trọng. Vì vậy, về phía Ethereum họ đưa ra một khái niệm dựa trên công nghệ chuỗi phụ (sidechain) gọi là plasma, trong đó, nếu được thực hiện một cách chính xác, nó sẽ giúp giảm bớt gánh nặng cho chuỗi chính và cho phép nhiều giao dịch được xử lý mỗi giây. Nhưng nó vẫn chưa ra mắt.

Bằng cách này, trong chuỗi dịch vụ Klaytn, bạn có thể thiết lập một khoản phí gas bằng không cho tất cả các giao dịch. Nó có nghĩa là các nhà phát triển BApp hoặc nhà cung cấp dịch vụ có thể xây dựng môi trường riêng của họ và cung cấp dịch vụ cho người sử dụng trong chuỗi dịch vụ. Vâng, đến đây tôi đã nói tất cả về chuỗi dịch vụ Klaytn.







## 3.6 Sự khác biệt giữa Klaytn và Ethereum - Vai trò khác nhau của các nút


Hãy nói ngắn gọn về sự khác nhau giữa Ethereum và Klaytn.

Ethereum là một mạng đơn. Không có sự phân biệt giữa các thành viên trong mạng. Bất cứ ai cũng có thể tạo ra một khối, nhưng khi nói đến việc tạo ra một khối, người đó cần phải là người đầu tiên thông báo rằng mình đã tạo ra nó, và nó nên được biết đến ở nhiều nơi. 
Vì vậy, nếu bạn thêm một khối vào blockchain, bạn nhận được phần thưởng. 
Đây là PoW, một phương pháp Bằng chứng công việc được sử dụng bởi Ethereum làm giao thức đồng thuận.


Trong Ethereum, bạn cần phải gắn vào nhiều nhiều nút nhất có thể bởi vì bạn không biết ai sẽ là nút khai thác khối.  
Nói cách khác, các nút viết ra khối phải có thông tin cập nhật. 
Vì vậy, tôi muốn nhận thông tin một cách nhanh chóng nhưng tôi không biết nút đó ở đâu. 
Nếu bạn biết rằng nút A luôn nhanh nhất trong việc viết một khối lên trên nút, bạn chỉ cần gắn vào nút A này, sau đó bạn có thể nhận được thông tin nhanh nhất.

Tuy nhiên, vì Ethereum luôn thay đổi nút của nó, bạn phải gắn vào nhiều nút nhất có thể, do đó có thể giao tiếp với nhiều nút hơn.


Sau đó, điều này sẽ cung cấp cho bạn một cơ hội để có được những thông tin mới nhất. 
Vì bất kỳ nút nào cũng có thể viết và lan truyền các khối, bạn cần phải kết nối với nhiều nút nhất có thể để nhận những dữ liệu mới nhất.

Klaytn thì khác, nó không phải là mạng đơn mà là một mạng với hai lớp. 
Tôi cho rằng một trong các nút đồng thuận trong mạng core cell sẽ được lấy làm một nút đề xuất và đóng vai trò viết khối mỗi vòng. 
Vì vậy, làm thế nào bạn có thể nhận được những thông tin mới nhất? 
Tôi nên bám vào xung quanh. 
Các nút điểm cuối gắn vào core cell biết rằng nút đồng thuận đang xây dựng khối, do đó chúng được gắn bên cạnh CN


Bằng cách đó bạn có thể tải hoặc ghi được những thông tin đáng tin cậy. 
Khi chúng tôi tạo ra một ứng dụng, chúng ta xây dựng các máy chủ được hiển thị ở đây. 
Bạn có thể triển khai Cơ sở dữ liệu Java hoặc SQL đến đám mây hoặc máy chủ riêng tư như Azure hay AWS. 
Tuy nhiên, do máy chủ này không thể liên kết trực tiếp với core cell, trước tiên bạn phải kết nối đến nút điểm cuối để truy cập vào dữ liệu blockchain. 
Bạn có thể kết nối máy tính của mình đến một nút điểm cuối hoặc sử dụng nó để kết nối với một nút điểm cuối khác. 
Tuy nhiên, việc chạy nút điểm cuối cá nhân này không hề dễ dàng.  
Vì hệ thống blockchain cần phải đồng bộ hóa tất cả các nút khi một nút hoạt động, nó cần được đồng bộ hóa mỗi khi khối mới được thêm vào nhằm viết khối một cách chính xác.






Ngoài ra, người ta cũng quan tâm liệu máy tính có thể bị hỏng bởi một cuộc tấn công không. 
Vì những vấn đề này, bạn có thể kết nối với một nút bên ngoài đáng tin cậy, chẳng hạn như nút cơ sở hạ tầng của Ethereum. 
Ví dụ, bạn có một nhà phát triển web ở đây. Anh ta muốn kết nối với Klaytn và chỉ đọc dữ liệu. Sau đó, việc kết nối đến nút công cộng bên ngoài sẽ tốt hơn và sử dụng nó để làm cho việc chạy một nút điểm cuối cá nhân dễ dàng và ít tốn thời gian hơn.

Cuối cùng, không giống như Ethereum, chúng tôi có một chuỗi dịch vụ có thể giao tiếp một phần với mainnet ở bên phải và xây dựng một không gian dịch vụ riêng biệt. 
Tóm lại, Klaytn là một mạng lưới trong đó có hai lớp tin tưởng lẫn nhau, và khi truy cập vào một blockchain nội bộ, nút điểm cuối có thể kết nối với mạng core cell và viết hoặc nhận dữ liệu một cách nhanh chóng.
