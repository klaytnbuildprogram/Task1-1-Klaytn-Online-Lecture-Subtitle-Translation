# 3. Nghiên cứu về "Klaytn"

## 3.1 Cơ chế đồng thuận
 
Trong những chương trước, vấn đề Blockchain hiện nay đang gặp phải được trình bày một cách cụ thể. Ở chương này, chúng ta hãy đi tìm hiểu về Blockchain - Klaytn đã giải quyết bằng thuật toán đồng thuận như thế nào. Hiện nay có nhiều loại thuật toán đồng thuận khác nhau, chẳng hạn như PoW hoặc PoS, thường được sử dụng trong Blockchain Public, và PBFT hoặc RAFT trong Blockchain Private. Nhìn chung, Blockchain Private sẽ đạt hiệu quả cao hơn so với Blockchain Public bởi vì thuật toán BFT của nó mang lại hiệu quả cao bằng cách giới hạn số lượng node tham gia. Tuy nhiên, cơ chế này lại giới hạn số lượng node đồng thuận, dẫn đến làm giảm đi sự phân quyền, và kết quả đồng thuận chỉ tiết lộ cho các nhóm nhỏ. Khiến chúng giảm đi tính minh bạch và lợi ích của Blockchain mang lại.

Mặt khác, Klaytn chọn Istanbul BFT làm thuật toán đồng thuận bởi chúng có thể tận dụng điểm mạnh cả Blockchain Private and Public. Mục tiêu nhắm tới Blockchain Public mang lại hiệu suất và tính ổn định cho các doanh nghiệp lớn nhưng vẫn duy trình tính bảo mật cao và minh bạch. Để đạt được tham vọng này, Klaytn áp dụng mô hình về cơ chế đồng thuận trong Blockchain Private nhưng lại công bố công khai. Nó gồm có số lượng ít các node Private để đạt được sự đồng thuận và các node còn lại có thể truy cập công khai và xác thực kết quả của việc tạo block. Chúng ta sẽ đi tìm rõ hơn về thuật toán Istanbul BFT mà Klaytn đang sử dụng.

Qúa trình đồng thuận của thuật toán BFT Istanbul gồm 3 bước: pre-prepare( khởi động), prepare( sẵn sàng), commit steps( bước cam kết). Klaytn sử dụng phương pháp round-robin, mỗi vòng các node đồng thuận sẽ được chọn. Các node đồng thuận còn lại (validator) sẽ được xác thực.

Nếu bạn nhìn bức tranh tổng thể, sẽ có những node xác thực (verifier) 1, 2, 3, v.v. Trong số đó, node được đánh dấu X ở trạng thái bị lỗi, điều đó có nghĩa là nó không hoạt động đúng theo quy trình xác thực. Một khi máy tính bị hỏng, mạng lưới sẽ bị ngắt, sẽ gây hại đến dữ liệu...

Bước đầu tiên là “đề xuất” những node đồng thuận được chọn (proposer). Bước kế tiếp “khởi động” - những node proposer đó sẽ tạo ra block và đưa ra đề xuất cho các node khác (validator).

Tiếp tục, gửi đề xuất đến node validator1, và nó sẽ gửi đến node validator2 , cứ như vậy đến node validator3. Đây chính là thông điệp mà cơ chế muốn truyền tải.

Đến bước thứ 3, khi các node verifier 1, 2 hoặc 3 nhận được thông báo từ node proposer, chúng sẽ thông báo nhận được đề xuất thành công. Ví dụ: Node validator1 gửi thông báo đến cả 3 node và node validator2 cũng gửi đến cả 3 node. Tuy nhiên, node validator3 không thể gửi gì và chỉ nhận được tin nhắn do nó bị lỗi.

Ở cuối giai đoạn prepare (chuẩn bị) này, bạn sẽ thấy toàn bộ node trong hệ thống. Hình ảnh dưới đây, node proposer, node validator 1 và node validator 2 còn tồn tại. Qúa trình này sẽ đảm bảo rằng tất cả các node verifier ở trong cùng một vòng.

Bước cuối cùng (commit step), quy trình này sẽ tương tác các node khác, xem có chấp nhận Block mà nó nhận từ node proposer hay không. Ví dụ, nó sẽ phản hồi tới các node, nếu được hơn 2/3 đồng ý, sẽ phê duyệt Block ngay lập tức. Không tồn tại vô hạn và trạng thái không thay đổi không xuất hiện trong giai đoạn này. Hơn thế nữa, nó không ở trạng thái mơ hồ so với PoW.

Kết luận, điểm mạnh của cơ chế này là sự tương tác giữa các node sẽ dẫn đến tính đồng thuận. Tuy nhiên, vẫn có điểm bất lợi là lưu lượng tăng theo cấp số nhân một khi số lượng node đồng thuận tăng. Cơ chế này sẽ chọn ra node đồng thuận và duy trì cơ chế đồng thuận BFT. Chúng ta tiếp tục khám phá các Block được tạo ra và lan truyền đến các giai đoạn khác như thế nào.






## 3.2 Tạo Block và tính phổ biến
 

Hãy xem cách Klaytn tạo ra Block và cung cấp trải nghiệm thú vị cho người dùng.
 
Chúng ta hãy nhìn vào chu trình tạo Block của Klaytn được gọi là một vòng. Mỗi round tạo ra Block mới, mặt khác sẽ tiến hành round mới khi nó kết thúc. Khoảng thời gian tạo Block mất khoảng 1 giây.



Chúng ta hãy cùng xem qua proposer và việc lựa chọn quản trị.
Mỗi round tạo ra Block mới, mặt khác sẽ tiến hành round mới khi nó kết thúc. Khoảng thời gian tạo Block mất khoảng 1 giây. Chúng ta hãy cùng xem qua proposer và việc lựa chọn quản trị. Ở mỗi round, proposer tạo Block từ một trong các node quản trị ngẫu nhiên. Hội đồng quản trị là tập hợp node cốt lõi hay còn gọi node đồng thuận. Nhìn vào bức hình, các vòng tròn này là các node đồng thuận, trong đó node màu xanh lam xem là node proposer trong round này. Và các node đồng thuận còn lại sẽ là node quản trị . Chúng là node validator màu hồng. Cụ thể hơn, mỗi node đồng thuận chọn ra một số ngẫu nhiên từ Block được tạo gần đây và thực hiện thao tác mã hóa để chứng minh node đồng thuận này được chọn. 
 


Hãy nhìn lướt qua đề xuất Block và tính xác thực của nó.
Khi node đồng thuận chọn làm node proposer, sẽ thông báo cho các node đồng thuận khác thông qua đưa ra chứng cứ mật mã với public key của proposer. Tương tự như vậy, nhóm node đồng thuận còn lại cũng gửi thông báo với những bằng chứng tại sao chúng trở thành một phần của quản trị. (Click) Bây giờ bạn biết ai là proposer và quản trị, proposer lọc ra giao dịch trong pool và tạo các Block. Sau đó, nếu quản trị chấp nhận tạo ra Block vừa rồi, quy trình sẽ hoàn thành.
 

Cuối cùng, hãy xem qua tính lan truyền Block.
Block vừa tạo phải nhận được chữ ký của ⅔ thành viên quản trị, thì mới được coi là thành công. Khi quản trị chấp nhận sự thỏa thuận này, Block mới chuyển đến tất cả node đồng thuận. Bây giờ bạn có thể lan truyền Block tới điểm cuối node (endpoint) thông qua (click) node proxy. 
Từ nãy giờ, bạn có cái nhìn rõ hơn làm sao proposer và quản trị được tạo ra và tính lan truyền của Block.

 
 

## 3.3 Cấu trúc mạng lưới
 
Tôi sẽ giải thích một chút về cấu trúc mang lưới của Klaytn. Bên trái màn hình là phiên bản tóm tắt về mạng lưới. Hiện thị mạng lưới tế bào lõi và điểm cuối node (endpoint) xung quanh mạng lưới tế bào lõi. Nhìn kỹ hơn, bạn sẽ thấy bên trong hộp đỏ là mạng lưới tế bào lõi, và bên ngoài hộp màu xanh bên là điểm cuối node. Trong mạng lưới tế bào lõi, phần màu vàng là mạng lưới các node đồng thuận (CNN) và phần màu đỏ là PNN là mạng node proxy (PNN). Các node đồng thuận (CN) trong màu vàng sẽ quản lý về node đồng thuận.
 
 
 
Một mạng lưới tế bào lõi được vận hành bởi một node tham gia. Nó kết hợp với một CN và một số node proxy- mà đã liên kết với CN. Nhưng để đạt điều đó, bạn phải đáp ứng yêu cầu nghiêm ngặt. Và các CN sẽ liên kết với nhau để dễ tương tác. Nếu có 10 CN, tất cả chúng sẽ kết nối với nhau nhanh nhất có thể khi chúng ở quy trình đồng thuận. Tuy nhiên, CNs không thể liên kết trực tiếp các node bên ngoài. Bởi vì đây môi trường private, không có sự can thiệp bên ngoài. Điểm mạnh là có thể nhanh chóng quyết định Block có nên được tạo hay không. Vậy làm sao đạt được nó? Đóng vai trò tham gia mạng lưới tế bào lõi, nó giống như bạn chạy mạng lưới proxy mà bạn có thể quản lý.
 
Và ở bên ngoài, các node endpoint liên kết mạng lưới mạng lưới tế bào lõi. Các node endpoint này có thể kết nối với node proxy trong ô lõi để nhận thông tin. Tất nhiên, các node endpoint có thể liên kết và trao đổi thông tin với nhau. Tuy nhiên, nếu node endpoint liên kết với node proxy, Block sẽ hoàn thành nhanh hơn. Lưu ý rằng không nhất thiết yêu cầu node endpoint. Bất cứ ai cũng có thể trở thành node endpoint và trao đổi thông tin khách hàng như web hoặc các thiết bị di động. Đó là node endpoint hoạt động như nhà cung cấp dịch vụ.
 
 
Và một lần nữa, node CN, PN và EN boot là những node loại đặc biệt được vận hành bởi Klaytn giúp các node mới đăng ký vào mạng lưới sẽ kết nối với node khác. Node CN boot nằm trong mạng CN và không được công bố. Chỉ có các node PN và EN boot mới được. Chỉ node PN giúp bạn đăng ký và kết nối với các node endpoint. Node EN boot cung cấp thông tin cho các node endpoint về node proxy nào sẽ kết nối. Từ nãy giờ tôi đã chia sẻ về cấu trúc mạng lưới Klaytn.
 
## 3.4 Tế bào lõi
 

 
 
Chúng tôi sẽ đưa ra cái nhìn về các tế bào lõi. Khi mainet được đưa ra, tế bào lõi sẽ quản lý hàng loạt node đồng thuận. Một khi các dịch vụ trở nên tốt hơn, chúng ta nên làm gì về tính mở rộng nếu có nhiều node liên kết với mạng lưới tế bào lõi?
Nhìn chung, không phải riêng Blockchain, chúng tôi sẽ phát triển server và chia nhỏ theo yêu cầu. Tuy nhiên, trong trường hợp của Blockchain, việc tăng số lượng node có thể làm giảm tốc độ xử lý vì cần thêm thông tin cho mỗi node khi phát triển. Tăng số lượng node sẽ làm giảm hiệu suất. Vì vậy, thay vì tăng số lượng node, tăng hiệu suất node hợp lý hơn. Ví dụ: bạn có thể tăng hiệu suất RAM hoặc CPU. Sau đây là điều kiện để liên kết các node
 
 
1. Hơn 40 lõi vật lý
2. 256GB RAM
3. STiết kiệm khoảng 14TB dữ liệu trong một năm 
4. Mạng lưới 10G
 
 
 
Lưu ý rằng hiệu suất cao các node đồng thuận của người tham gia không đồng nghĩa tốc độ cao của toàn thể mạng lưới tế bào lõi. Bởi vì các node còn lại với hiệu suất thấp hơn đang hoạt động với thông số kỹ thuật thấp. Do đó, các thông số kỹ thuật phải khớp với mạng lưới để giúp gia tăng hiệu suất.
 
 
 
 
Lần nữa, hãy nhìn vào cấu trúc tế bào lõi, nó bao gồm một CN và một số PN. Một số lý do tại sao node proxy được gọi là PN. Vì CN có nguồn nhiên liệu hạn chế để liên kết với số lượng CN, nó chỉ hỗ trợ kết nối các endpoint bằng PN. Ví dụ: các node endpoint kết nối trực tiếp với CN. Nếu CN này có thể chấp nhận tới một nghìn kết nối endpoint, con số vượt mức cho phép, dẫn đến năng suất không đạt như mong muốn. Vì vậy, chỉ có PN thay thế. PN kết nối với các node endpoint và chuyển đến CN. Và vì CN chỉ kết nối với một vài PN, bạn có thể giải quyết các vấn đề liên kết của endpoint khi muốn kết nối với tế bào lõi bằng nhiều PN.
 
Tóm lại, do CN là node quản lý về quy trình, việc kết nối sẽ không đạt hiệu suất cao. Vai trò PN là bảo vệ CN và vấn đề liên quan khả năng mở rộng có thể được giải quyết bằng cách nhân đôi nhiều PN.
 
 
 
 
 
 
 
## 3.5 Chuỗi dịch vụ
 



 
Chuỗi dịch vụ Klaytn là Blockchain hoạt động một cách độc lập liên kết với mainet. Ý tưởng này bắt nguồn từ tính mở rộng. Trong tình huống bạn muốn sử dụng chuỗi dịch vụ hay tùy chỉnh mức bảo mật, bạn cần thiết lập nó trong môi trường node đặc biệt, khi chạy trên nền tảng Blockchain riêng. Dịch vụ này đòi hỏi thông lượng rất lớn. Không khả thi về mặt kinh tế cho mainet, khi dùng chuỗi dịch vụ.
 
Nhìn vào hình ảnh, vòng tròn lớn ở giữa chính là mainet. Chuỗi dịch vụ phụ thuộc vào chuỗi chính, không có sự tự do tương tác giữa chuỗi chính và chuỗi dịch vụ, và giới hạn các giao dịch được dùng. Ngoài ra, việc lan truyền KLAY chỉ được thực hiện khi có ràng buộc đằng sau.
 
 
 
 
 
Nói cách khác, chuỗi dịch vụ xây dựng không gian dịch vụ riêng và tạo niềm tin cho mainet khi cần thiết. Các nền tảng Blockchain khác cũng đang chuyển sang áp dụng chuỗi dịch vụ. Đối với trường hợp của Ethereum, những hạn chế về mainnet liên quan tới hiệu suất và tốc độ. Theo như các bạn biết Crypto Kitty, làm mạng lưới chính của Ethereum bị chậm đi rất nhiều. Vì vậy, họ đã đưa ra một khái niệm dựa trên công nghệ sidechain có tên Plasma, giảm bớt gánh nặng cho chuỗi chính và cho phép xử lý nhiều giao dịch hơn mỗi giây. Bây giờ giải pháp này vẫn chưa công bố ra.
 
Nhân tiện, trong chuỗi dịch vụ của Klaytn, bạn có thể đặt phí gas bằng không cho tất cả các giao dịch. Điều đó có nghĩa là các nhà phát triển hoặc nhà cung cấp dịch vụ BApp có thể xây dựng môi trường của riêng họ và cung cấp dịch vụ cho người dùng trong chuỗi dịch vụ. Vâng, tôi đã trình bày xong chuỗi dịch vụ của Klaytn.
 
 
 
 
 
 
 
## 3.6  Sự khác biệt giữa Klaytn và Ethereum - Vai trò khác nhau của các node
 
 
Trình bày sơ qua về sự khác biệt giữa Ethereum và Klaytn.
 
Ethereum là một mạng lưới đơn. Và không có sự phân biệt giữa các thành viên mạng lưới. Bất cứ ai cũng có thể tạo Block, nhưng người đó là người đầu tiên thông báo rằng họ đã tạo ra block trước, và ai cũng biết phải biết sự tồn tại của block đó.
Vì vậy, nếu bạn thêm Block vào mạng lưới Blockchain, bạn sẽ nhận được một khoản tiền thưởng.
TĐây là phương pháp PoW - bằng chứng công việc mà Ethereum sử dụng như là một giao thức đồng thuận.
 
 
rong Ethereum, bạn càng bám nhiều node càng tốt vì bạn không biết ai sẽ là người khai thác node. 
Nói cách khác, các node viết Block và cập nhật thông tin.
Vì vậy, tôi muốn lấy thông tin nhanh chóng nhất nhưng tôi không biết node này nằm ở đâu.
Nếu bạn biết rằng node A nhanh nhất khi viết Block trên node, bạn chỉ cần bám vào node A này, thì bạn sẽ nhận thông tin nhanh nhất.
 
Tuy nhiên, vì Ethereum luôn thay đổi node, bạn phải bám vào càng nhiều node càng tốt.
 
 
Sau đó, điều này sẽ cung cấp cho bạn một cơ hội để có được thông tin mới nhất.
Bởi vì, bất kỳ node nào cũng có thể viết và lan truyền Block, nên bạn cần kết nối nhiều Block để lấy được thông tin dữ liệu mới nhất.
 
Mặt khác Klaytn, không phải là một mạng lưới đơn lẻ, mà là một mạng lưới có hai lớp.
Tôi đã chia sẻ rằng một trong những node đồng thuận trong mạng lưới tế bào lõi sẽ được xem là proposer và đóng vai trò viết Block mỗi round.
Vậy làm thế nào để bạn có được thông tin mới nhất? 
Tôi nên bám xung quanh.
Các node endpoint gắn vào tế bào lõi cho biết node đồng thuận đang tạo ra Block, vì vậy chúng gắn bên cạnh CN.
 
 
Bằng cách đó bạn có thể tải hoặc viết thông tin đáng tin cậy.
Khi chúng tôi tạo ứng dụng, và xây dựng sever sẽ hiển thị ở đây.
Bạn có thể triển khai Java hoặc SQL DB lên cloud hoặc server riêng như Azure hoặc AWS.
Tuy nhiên, máy chủ này không thể liên kết trực tiếp với tế bào lõi, trước tiên bạn phải kết nối với node endpoint để truy cập dữ liệu Blockchain.
Bạn có thể liên kết máy tính của mình với node endpoint hoặc sử dụng node đó để kết nối node endpoint khác.
Tuy nhiên, chạy node endpoint riêng lẻ không phải là dễ.
Vì hệ thống Blockchain cần đồng bộ hóa tất cả các node trong lúc chạy node mỗi khi tạo Block mới được thêm vào để viết cho đúng.
 
 
 
 
 
 
Ngoài ra, cũng có một lo ngại rằng máy tính có thể bị hỏng khi bị tấn công.
Vì những vấn đề trên, bạn có thể kết nối với node bên ngoài đáng tin cậy, chẳng hạn như node của Ethereum.
Ví dụ, bạn có nhà phát triển web ở đây. Anh ta muốn kết nối với Klaytn và chỉ cần đọc dữ liệu.Sau đó, kết nối với node công khai, điều đó sẽ dễ dàng hơn và ít tốn thời gian hơn so với chạy node điểm endpoint riêng lẻ.
 
Cuối cùng, không giống như Ethereum, chuỗi dịch vụ có thể tương tác một phần với mainet ở bên phải và xây dựng một không gian dịch vụ riêng biệt. 
Tóm lại, Klaytn là một mạng lưới trong đó hai lớp hỗ trợ lẫn nhau và khi truy cập vào Blockchain nội bộ, node endpoint có thể kết nối với mạng lưới tế bào lõi và ghi hoặc nhận dữ liệu một cách nhanh chóng.
