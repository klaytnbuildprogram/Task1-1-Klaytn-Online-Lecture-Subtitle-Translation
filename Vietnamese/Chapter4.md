# 4. Phát triển trò chơi phép cộng với các công cụ Klaytn
## 4.1 Giới thiệu
 

Chào mọi người. Trong phần hướng dẫn này, tôi sẽ phát triển BApp được gọi là addition game sử dụng Blockchain Klaytn. BApp là từ viết tắt của Blockchain Applications. Chúng ta hãy tạo trò chơi pop-up sẽ trả 0,1 Klay miễn phí nếu bạn giải quyết vấn đề phát sinh trong 3 giây.
 
 
Hãy xem cách nó hoạt động. Đầu tiên, đăng nhập vào tài khoản quản trị. Chúng tôi sẽ xác thực tài khoản sử dụng tệp keystore và mật khẩu. Vì vậy, hãy chọn tệp keystore và nhập mật khẩu. Sau khi xác thực tài khoản, sử dụng Send KLAY tới nút Contract để nhập số lượng cần sử dụng. Lý do chúng tôi gửi KLAY đến địa chỉ contract để thể hiện sự minh bạch về số tiền được sử dụng trong trò chơi. Lưu ý rằng chỉ có thể thực hiện với tài khoản quản trị.


Bây giờ, tôi đang gửi 1 KLAY đến contract này. Một khi giao dịch hoàn thành, người chơi sẽ biết số tiền cần phải chi. Người sử dụng có thể bắt đầu addition game. Nếu bạn cài đặt trong 3 giây, Contract sẽ gửi 1 KLAY tới tài khoản người chơi. Hãy bắt đầu nào.
Nếu bạn thực hiện sai, hệ thống sẽ khởi động lại. Nếu bạn thử lại, bạn có thể nhận KLAY bằng cách nhấn nút OK. Khi giao dịch hoàn thành, số dư sẽ giảm 0,1 KLAY trong contract. Như bạn có thể thấy, giao dịch xử lý rất nhanh, đó là điểm mạnh của Klaytn. Nếu bạn nhấp vào liên kết bên dưới, bạn sẽ tới scope Klaytn, nơi mà bạn có thể xem thông tin giao dịch.


Nếu bạn có kinh nghiệm phát triển DApp trên Ethereum, bài hướng dẫn này sẽ khá dễ dàng cho bạn. Klaytn là một nền tảng fork do Byzantine của Ethereum, vì vậy bạn sẽ cảm thấy quen thuộc. Ví dụ:  JavaScript, caver.js, có thể tương tác với Blockchain Klaytn, tương tự như Ethereum của web3.js. Ngoài ra, chúng tôi còn hỗ trợ các ngôn ngữ solidity được sử dụng cho phát triển smart contract. 


Bởi vì Blockchain Klaytn sử dụng framework Truffle, bạn nhanh chóng thích ứng với việc phát triển BApp. Đối với những người không có kinh nghiệm phát triển BApp vẫn có thể phát triển nó trong nền tảng Blockchain Klaytn. Nhưng trước hết, phải hiểu cơ bản về Blockchain và ngôn ngữ solidity trong smart contract. Tôi sẽ gửi đường link cho bạn tìm hiểu. 
Chúng tôi phát triển một vài công cụ để hỗ trợ Klaytn,
Đầu tiên, tôi sử dụng IDE có thể test quá trình phát triển, một ví có thể quản lý bằng nhiều tài khoản,
và Klatn scope sử dụng để tìm kiếm thông tin của giao dịch.

 
 
## 4.2 Ví Klaytn & quản lý tài khoản
 

Để sử dụng mạng lưới blockchain, bạn phải có tài khoản riêng. Và cần có tài khoản ngân hàng để quản lý token KLAY của mình. Vì vậy, hãy sử dụng ví của Klaytn, nó thân thiện và cực kỳ dễ dùng. Nếu bạn truy cập vào https://baobab.klaytnwallet.com/, nó sẽ hiện thị mạng lưới Baobab và quản lý tài khoản của bạn. Ngoài ra, ví này còn dành cho mục đích thử nghiệm, và Klay được sử dụng ở đây không có giá trị tiền tệ. Đầu tiên, hãy tạo một tài khoản mới, nhấp Create để tạo ví mới. Quá trình này bao gồm việc tạo mật khẩu và tệp keystore. Trước khi làm điều đó, tôi sẽ giải thích tập keystore là gì. Nó giống như quy trình chúng ta đến ngân hàng để làm sổ tiết kiệm, và chúng tôi cất ở nơi an toàn để những người khác không thể sử dụng nó. Vault sự kết hợp giữ tệp keystore và mật khẩu, nó rất cần thiết trong việc bảo vệ khóa bí mật cho chữ ký của giao dịch không bị tấn công từ bên ngoài.


Tiếp tục tạo tệp keystore. Nhập mật khẩu của bạn vào đây, nhấp “next” và tải xuống tệp keystore.
Downloaded,
Sau khi tải xong, lưu khóa bí mật được xuất hiện trên màn hình. Khóa bí mật rất quan trọng cho việc ký giao dịch trong BApp Klaytn. Chìa khóa bí mật này không nên được tiết lộ ra bên ngoài. Nó giống như mật khẩu ngân hàng và sổ tiết kiệm, nếu không có nó, bạn sẽ mất tiền.
 


Đó là lý do tại sao tôi tạo tệp keystore để bảo vệ khóa bí mật. Người dùng phải nắm tệp kho khóa và mật khẩu lưu trữ khóa trước khi truy cập khóa bí mật. Ngay cả khi hacker có được tệp keystore, nhưng không biết khóa bí mật thì cũng không thể truy cập được và dĩ nhiên, không thể lấy được tiền. Bạn không dễ dàng mất tài khoản. Đừng để keystore bị lộ ra bên ngoài.
Bây giờ, tôi sẽ lưu lại chìa khóa bí mật trong Notepad. Bạn nên làm điều đó,, nhưng nó chỉ là một mạng testnet và tôi sẽ làm nó cho thuận tiện ngay bây giờ. Bạn có thể lưu khóa riêng của mình ở nơi an toàn. Sau khi lưu, người dùng có thể nhấp vào the view wallet info ở bên trái màn hình. Bạn có thể truy cập vào ví bằng 2 cách: đầu tiên là sử dụng khóa bí mật và thứ hai là truy cập bằng tệp keystore và mật khẩu của nó. Với cách đầu tiên, hãy truy cập nó bằng khóa bí mật. Sao chép và dán nó trong Notepad.

 
Thông tin ví tôi sẽ được hiển thị, gồm địa chỉ public và khóa bí mật ở bên dưới. Tôi có thể xem danh sách giao dịch của mình. Tôi không phải xử lý với vấn đề này vì tôi chưa có giao dịch nào cả. Ở bên phải màn hình, tôi có thể thấy số lượng KLAY và bạn cũng có thể thêm token vào ví bằng cách nhấp vào nút “plus”.
 
Ngay bây giờ, hãy nhận KLAY trên tài khoản của bạn. Nhấp vào tab KLAY faucet tab để nhận KLAY miễn phí. Tài khoản hiện tại có số dư bằng không. Nếu bạn nhấn nút Run faucet, bạn sẽ nhận được 5 KLAY. Sau khi nhận được KLAY, bạn vẫn có thể nhận nó lần nữa sau 24 giờ. Vì trong thời gian ngắn bạn không thể nhận được nhiều KLAY, bạn nên chia KLAY nhiều nhất có thể khi thử nghiệm. Lý do bạn nên nhận KLAY sau 24 giờ vì một số người cũng đang sử dụng KLAY giống bạn một cách mơ hồ. Klaytn chia sẻ họ đang trong quá trình hoàn thiện hơn. Bây giờ, hãy chuyển KLAY sang tài khoản khác. 
 
 


Nếu bạn chọn Send klay & token, bạn có thể gửi tiền từ địa chỉ bạn đến địa chỉ khác, chỉ cần nhập địa chỉ người nhận. Tôi sẽ gửi 1 KLAY để xem bao nhiêu phí tôi phải trả. Nó sẽ hiển thị tối đa phí giao dịch là 0,000625 KLAY, coi như phí hoa hồng. Chi phí này được tính bằng gas price nhân với gas limit. Bạn có thể nghĩ gas price là chi phí cho lệnh giao dịch đến node đồng thuận. Gas Price của Klaytn luôn cố định, không giống như Ethereum. Rất khó để dự đoán phí hoa hồng vì gas price của Ethereum luôn dao động. Tuy nhiên, gas price của Klaytn luôn cố định ở mức 25 ston, bất kể bạn thực hiện các giao dịch nào.

 

Gas limit là chi phí tối đa xử lý giao dịch. Ví dụ, chúng ta có một số vòng lặp vô hạn trong một giao dịch. Sau đó, giao dịch đơn giản này sẽ tiếp tục chạy trong mạng lưới. Điều này gây ra sự suy giảm hiệu suất của mạng và gây thiệt hại tới mọi người. Vì vậy, nếu bạn có hơn 25.000 gas, hãy nhận ra rằng có gì đó khác thường và bạn phải ngừng quy trình này.



Và gas price được cho là chứa 25 test_ston, ston là một trong những đơn vị tiền tệ của KLAY. Tương tự như 1 USD ở Hoa Kỳ là 100 xu, có rất nhiều đơn vị KLAY. https://docs.klaytn.com/klaytn/design/computing/exec_model - tài liệu chính thức của Klaytn chỉ ra đơn vị KLAY. Có nhiều loại. Có một đơn vị KLAY tiêu chuẩn ở giữa và peb ở trên cùng là đơn vị tối thiểu đại diện cho KLAY.  Đơn vị được sử dụng cho round thứ 10 của peb là ston. Vậy 25 ston sẽ quy đổi thành KLAY như thế nào. https://blockchains.tools/pebConverter?l=KLAY, nếu bạn truy cập trang web này, bạn có thể quy đổi ra nhiều đơn vị. Nếu đặt 25 ston, sẽ tính toán bao nhiêu KLAY sử dụng. Nếu gas limit 25.000 được nhân với 25 ston, xuất hiện 0,000625 KLAY. Nó được sử dụng như một khoản phí giao dịch. Hãy thử nó trên máy tính. Nếu bạn sao chép nó và nhân với gas limit 25000, chi phí giao dịch sẽ xuất hiện. Đây là chi phí xử lý giao dịch.


Lưu ý rằng khi bạn gửi các khoản tiền nhỏ này từ Klaytn, chi phí giao dịch luôn được cố định ở mức 0,000625 KLAY. Tuy nhiên, chi phí giao dịch không cố định trong giao dịch thông qua chức năng smart contract vì gas limit thay đổi theo mức độ phức tạp của giao dịch. Tôi sẽ giải thích thêm về điều này sau.
 
Bạn có thể tự thay đổi gas limit bằng cách nhấp vào nút “Edit” bên cạnh. Nhưng tôi khuyên bạn nên cài đặt mặc định.
Hãy thử gửi giao dịch ngay bây giờ. Ở trang tiếp theo, bạn sẽ thấy thông tin về số tiền và phí giao dịch sẽ là bao nhiêu. Bạn nhấp vào “Yes” sẽ xuất hiện câu hỏi “Do you want to continue?” Ngay lúc đó, nhấp vào và giao dịch được hoàn thành trong chớp mắt. Sau đó nhấp “view transaction info” và nội dung sẽ được lưu lại trong block và hiện thị cho người dùng. Tôi sẽ giải thích điều này sau chi tiết hơn. Từ nãy đến giờ, tôi đưa ra bức tranh tổng thể về ví Klaytn.

 

## 4.3 Klaytn IDE và Smart Contract 1
 
Liên quan tới IDE, hãy tạo smart contract vào trò chơi ứng dụng này. Thay vì tập trung quá nhiều vào smart contract, tôi tập trung vào các công cụ Klaytn.
Bạn có thể tạo và kiểm tra các smart contract bằng cách truy cập vào http://ide.klaytn.net/. Nó tương tự như IDE Ethereum, nhưng ở đây được sử dụng để kết nối với node Klaytn, chứ không phải với node Ethereum. Bây giờ, hãy xem các tính năng của IDE Klaytn bằng cách tạo các smart contract cho các trò chơi ứng dụng.
 
Như bạn đã biết, “Hợp đồng thông minh” tiếng Anh gọi là “Smart contract”. Họ gọi nó là “Contract” trong bài giảng của tôi. Nếu bạn nhìn vào đây, bạn sẽ thấy có hợp đồng đếm ngược được tạo theo mặc định. Tôi sẽ xóa cái này và bắt đầu. Hãy xóa nó. Khi bạn nhìn thấy các dòng bình luận ở trên cùng, IDE Klaytn viết  phiên bản Solidity 0.4.24, vì vậy bạn làm việc với phiên bản này.
 
Contract này có ba chức năng. Đầu tiên là gửi KLAY vào contract, thứ hai để tải số dư của contract và cuối cùng là gửi KLAY từ contract đến tài khoản người dùng. Chúng tôi sẽ làm từng bước một và sử dụng các công cụ để kiểm tra. Đầu tiên, hãy đặt tên cho contract là AdditionGame, trò chơi Contract Edition.

 (Code)
Tại thời điểm triển khai, bạn tạo một biến trạng thái có thể lưu trữ địa chỉ của tài khoản quản trị. Và tôi đang tạo ra một cấu trúc. Trước đó, các cấu trúc thường làm gì? Vâng, nó có nhiệm vụ khởi tạo.Trong trường hợp của ngôn ngữ solidity, bạn không thể viết hoặc tải lại cấu trúc, bởi vì nó là cấu trúc được tải đầu tiên khi bạn triển khai. Tôi có thể tận dụng điều này và thiết lập một tài khoản cho chủ sở hữu của contract. Đầu tiên chúng tôi tạo chủ sở hữu biến trạng thái. Đó là một loại địa chỉ.  Tôi đang xây dựng một cấu trúc, Owner is msg.Sender.
 
(Code)
Tôi vừa tạo một cấu trúc. Msg.sender gọi là contract. Trong cấu trúc Msg.sender được sử dụng để triển khai. Vì vậy, tôi sẽ gán tài khoản đó cho biến trạng thái chủ sở hữu và lưu nó mãi mãi vào Blockchain. Đây là sự khởi tạo. Vì vậy, hãy kiểm tra code mà chúng tôi vừa thêm vào. Bạn cần biên soạn trước. Nhấp vào Auto checkbox ở đầu bảng bên phải để tự động biên soạn mỗi khi bạn viết code. Đầu tiên bạn phải bấm vào nút “compile” để xem nó có biên soạn không. Vâng, các thông tin được biên soạn sẽ hiển thị ở bên dưới. Chúng ta hãy thiết lập lại môi trường. Có 2 sự lựa chọn: DEV NODE và Baobab. Và tôi có thể thêm mạng lưới mới. Chức năng mạng lưới mới vừa được thêm vào sẽ kết nối với địa chỉ rpc nơi node Klaytn hiện đang chạy. Tôi sẽ bỏ qua bước này. Node DEV là một tùy chọn để kết nối và kiểm tra node phát triển. Node Dev tạo một tài khoản ngẫu nhiên và cho phép bạn đặt trước 100 KLAY. Và nó cài đặt chạy hết gas quá trình thử nghiệm. Vì vậy, nếu bạn thấy From Account bên dưới, đã có 100 KLAY thử nghiệm trong tài khoản này. Một sự chọn khác là kết nối với Baobab cũng được kết nối với mạng thử nghiệm chính. Và thời điểm bạn chọn Baobab, KLAY trong tài khoản bên dưới thay đổi thành 0. Các node dev và node baobab hoạt động độc lập với nhau, vì vậy các tài khoản tại cùng một địa chỉ được nhận dạng bởi nhau, nhưng trạng thái của tài khoản sẽ  khác nhau vì các node khác nhau. Vì vậy, số dư sẽ thay đổi.
 
 
Hãy thử làm mới trang bằng việc chọn lại node Dev. Tiếp tới Loading Account, không có tài khoản đã sử dụng trước đây và tôi tạo một tài khoản mới khác. Điều thú vị là bạn có thể tải xuống tài khoản này dưới dạng tệp keystore hoặc khóa bí mật và sử dụng lại. Nếu bạn đang thử nghiệm trên một máy tính khác, bạn muốn tiếp tục với tài khoản cũ, bạn có thể sử dụng tùy chọn này tại thời điểm đó. Ví dụ: nếu bạn nhấp vào tài khoản, bạn sao lưu tài khoản hiện tại. Khi bạn chọn nó, một cửa sổ sẽ mở ra và bạn có lựa chọn lấy tệp keystore hoặc khóa bí mật của mình. Đơn giản chỉ cần sao lưu chìa khóa bí mật của bạn. Khi bạn nhấp Copy, bạn đã sao lưu khóa bí mật của tài khoản này.
 
 
Sau đó làm mới trang một lần nữa. Khi tài khoản được tạo, nhấp lại và chọn import an account. Chuyển đến Private Key và dán sao lưu của khóa bí mật. Label hiển thị sẽ được gọi là test account.Import. Nếu bạn chọn lại tài khoản, bạn sẽ có tài khoản thử nghiệm mà chúng tôi đã nhập bên dưới. Vì vậy, khi bạn quay lại trang này theo cách trên trên một máy tính khác, bạn có thể thực hiện kiểm tra một cách nhất quán.
 
 
Thay vì giải thích Tx Value, tôi sẽ cố gắng triển khai nó đầu tiên. Deploy
. Sau khi bạn nhấp vào nút compile, bạn sẽ triển khai AdditionGame. Nhấn Deploy, việc triển khai sẽ hoàn thành trong vòng chưa đầy 3 giây. Có một hàm băm TX trong giữa cái bảng, phải không?  Đây là thông tin giao dịch hàm băm được tạo ra khi triển khai. Trên cùng bảng, thông tin hàm băm cho thấy địa chỉ nào đã được triển khai.
 
 
Nếu bạn nhìn vào bảng điều khiển bên cạnh, bạn sẽ thấy địa chỉ nào hiện đang có contract được triển khai và bên dưới bạn có lựa chọn tải giá trị của biến trạng thái chủ sở hữu. Đây là một hàm getter. Vì chúng tôi có thể nhìn thấy công khai biến trạng thái của chủ sở hữu, chúng tôi có thể tự động tạo ra một hàm getter để lấy giá trị của biến chủ sở hữu. Khi bạn nhấn nút Call, địa chỉ bên dưới sẽ xuất hiện. Địa chỉ này là gì?
 
Vâng, đây là địa chỉ tài khoản của người đã triển khai contract này. Tôi đã triển khai contract từ một tài khoản hiển thị khác, vì vậy tài khoản này được lưu dưới dạng giá trị của chủ sở hữu biến trạng thái. Vâng, tôi đã viết code solidity thông qua IDE Klaytn và đã kiểm tra chủ sở hữu của contract. Tiếp theo, chúng ta sẽ viết và kiểm tra hai hàm còn lại trong lớp kế tiếp.




 
## 4.4 Klaytn IDE & Smart Contract 2
 

Chúng ta hãy tiếp tục tạo chức năng xem xét số lượng còn lại của KLAY trong địa chỉ hợp đồng. Vui lòng chọn hộp kiểm tự động bên cạnh nó. Bên trong hàm tạo, chúng ta sẽ tạo chức năng getBalance.
(Code)

Từ khóa hàm được sử dụng, tên là “getBalance ()”  hiển thị công khai và chỉ đọc với chế độ xem. Cuối cùng, xác định loại unit như là hàm function.
(Code)

Địa chỉ (this) đề cập đến hợp đồng hiện tại. Đây là hợp đồng edition game, và thành viên có thể truy cập balance. Điều này hoàn thành chức năng tải số dư KLAY tại địa chỉ hợp đồng này. Hãy triển khai lại để thử nghiệm. Nhấp vào nút Deploy, sau đó chức năng getBalance () được tạo và nút Call được kích hoạt. Hãy nhấp một lần, khi đó số dư hiện tại bằng 0, có nghĩa tôi chưa gửi gì cả.
 
 
Tiếp theo, hãy tạo một hàm gửi KLAY đến địa chỉ hợp đồng từ tài khoản chủ sở hữu.
(Code)

Tôi đã hiện thị công khai và thực hiện các khoản phải trả. Bất cứ khi nào bạn gửi KLAY đến hàm solidity trong tài khoản của mình, bạn phải luôn tạo loại mà có thể trả. Bằng cách đó tôi có thể nhận được tiền từ hàm. Tiếp theo, chúng tôi sẽ kiểm tra tính hợp lệ.
 
(Code)

Nếu bạn không sử dụng từ khóa yêu cầu, hàm sẽ không hoạt động. msg.sender nhắc tới đến tài khoản mà được là hàm bây giờ so với tài khoản chủ sở hữu biến trạng thái, để mà nếu tài khoản hiện đang tải chức năng này không phải là tài khoản chủ sở hữu, nó sẽ không thực thi chức năng. Vì vậy, tôi đã kiểm tra tính hợp lệ để xem liệu tôi có thể chuyển KLAY từ tài khoản chủ sở hữu sang hợp đồng hay không. Hãy kiểm tra ngay bây giờ nào.
 
 

Vui lòng nhấn nút Deploy. Chức năng deposit hiện được kích hoạt. Nếu bạn gửi KLAY với chức năng gửi tiền, bạn phải sử dụng Tx.Value. Nếu hàm có loại phải trả, bạn phải sử dụng tx.Value. Với test_KLAY bên cạnh, nhập 1 làm giá trị. Sau đó nhấp vào nút gửi tiền. Giao dịch của bạn đã thành công và đưa biên lai giao dịch cho bạn. Nếu bạn xem tài khoản, số dư sẽ giảm từ 100 KLAY xuống còn 99 KLAY. Nếu đây là bản gốc, chúng tôi sẽ phải khấu trừ số dư, bao gồm chi phí gas được sử dụng để xử lý giao dịch, nhưng chúng tôi đã chọn nút dev, không bao gồm nút phát triển hoặc hóa đơn gas.
 

Bây giờ, hãy gọi hàm cân bằng để xem số dư của hợp đồng là bao nhiêu.  Nó chứa một giá trị. Xin lưu ý rằng chúng tôi chỉ gửi 1 KLAY và số lượng lớn đến mức bạn có thể bị nhầm lẫn.  Đây là giá trị của 1 KLAY được chuyển đổi thành peb, đơn vị tối thiểu của KLAY. Trong máy ảo Klayton, bạn cần chuyển đổi KLAY thành đơn vị peb nhỏ nhất và xử lý nó, để bạn thấy con số này. Khi nhập một giá trị từ giá trị tx và gửi nó đến chức năng ký gửi, rất may IDE sẽ tự động chuyển đổi nó thành đơn vị nhỏ nhất, peb. 
Đây là một tính năng rất hữu ích để thử nghiệm. Ngược lại, bạn cũng có thể kiểm tra với các đơn vị khác nhau trong giá trị tx, lần này với đơn vị thấp nhất, peb. Hãy chuyển đổi 2 KLAY thành peb và gửi nó đến hợp đồng. Quay trở lại trang web chuyển đổi đơn vị, nhập 2 KLAY, sao chép giá trị đã chuyển đổi sang peb và dán vào giá trị tx.
 
 
Và sau đó bạn chọn hàm gửi tiền. Giao dịch đã thành công. Sau đó giá trị tăng lên. Bạn có thể kiểm tra bằng việc chuyển đổi đơn vị.
 
 

Và giới hạn gas được tự động theo mặc định. Nói cách khác, nó tính toán giới hạn gas để vào hàm và tự động xác định nó. Điều này là do tính toán phụ thuộc vào độ phức tạp của hàm. Vì vậy, giới hạn gas để xử lý chức năng là không cố định. Khi chúng tôi gửi tiền bằng ví từ khóa trước, giới hạn gas đã được cố định ở mức 25000. Đó chỉ là một giao dịch gửi tiền, do đó không có sự phức tạp và giới hạn gas được cố định. Trên thực tế, bạn có thể tự nhập giới hạn gas này và thử kiểm tra chính xác hơn. Cho đến nay, tôi đã học được giới hạn gas và tôi đã chi trả phần chuyển tiền từ tài khoản chủ sở hữu bằng cách sử dụng giá trị giao dịch để ký hợp đồng.
 

 
## 4.5 Klaytn IDE & Smart Contract 3
 

Với chức năng cuối cùng này, hãy viết logic để chuyển tiền trong hợp đồng vào tài khoản người dùng khi người dùng đã giải quyết vấn đề của addition game. Để tham khảo, người dùng trả lời đúng câu gọi hàm này để nhận tiền trực tiếp.
 
Lấy giá trị KLAY để truyền cho người dùng làm đối số.  Lưu ý rằng giá trị này được chuyển đổi từ giao diện người dùng sang peb và được thông qua. Và một hàm trả về Boolean. Tiếp theo, bạn cần xác thực rằng số dư trong hợp đồng bằng với giá trị bạn muốn gửi cho người dùng.
 

Gọi hàm getbalance () ở trên để gọi số dư còn lại trong hợp đồng hiện tại và chuyển nó nếu nó bằng hoặc lớn hơn giá trị nhận được dưới dạng đối số.
 

msg.sender, người dùng có câu trả lời đúng đã gọi hàm này,
(transfer (_value)) để nhận tiền thưởng và gửi KLAY cho người dùng bằng chức năng chuyển tiền. Và cuối cùng, Tôi sẽ trở lại cho dù lệnh đã thành công. 
 

Hiện tại, chúng tôi đã viết code hợp đồng thông minh mà chúng tôi sẽ sử dụng. Nó rất đơn giản. Bây giờ hãy làm bài kiểm tra cuối cùng. Để triển khai, đặt giá trị Tx thành 0 và đặt giới hạn gas trở lại tự động.  Việc triển khai của bạn đã thành công. Để sử dụng chức năng chuyển nhượng, chúng tôi sẽ gửi lại KLAY vì số dư hợp đồng là 0 sau khi triển khai cái mới. Giá trị Tx là 3 và tôi sẽ thay đổi Test_peb thành Test_klay. Nhấn nút Send trong chức năng deposit. Nếu giao dịch thành công, hãy nhấp vào ‘get balance’, tiền của bạn sẽ hiển thị. Hãy nhớ rằng số dư tài khoản của tôi là 94 KLAY.
 
Bây giờ hãy sử dụng chức năng transfer. Đặt giá trị Tx trở về 0 và nhấp vào nút Send của chức năng transfer. Bây giờ, đây là một hàm chứa các tham số, bạn phải gửi giá trị đối số khi cửa sổ xuất hiện. Bạn cũng phải chuyển đổi KLAY sang peb khi bạn gửi nó. Hãy nhớ rằng các giá trị KLAY được gửi đến hợp đồng được chuyển đổi thành peb khi được thông qua.  Quay trở lại trang web chuyển đổi, và chuyển đổi 1 KLAY. Sao chép và dán các giá trị Peb. Đặt nút Call, giao dịch sẽ được thực hiện và biên nhận sẽ được trả lại thành công. Số dư của ‘From account’ đã tăng thêm một KLAY, đó là 94 KLAY ngay trước đó. Cuối cùng, khi getBalance hoàn thành, có tổng cộng 2 KLAY còn lại, trong đó 1 KLAY giảm.
 

Để tham khảo, nút dev này  thực sự đang chạy,  vì vậy, theo dõi các giao dịch chúng tôi đã thực hiện sẽ được ghi lại trong mạng. Làm thế nào để bạn kiểm tra nó? Tất cả bạn phải biết là địa chỉ hợp đồng. Thông tin dưới nút deployi là địa chỉ hợp đồng chúng tôi đã triển khai cho nút dev. Sao chép này và làm mới trang.
 

Nhấp vào nút compile một lần nữa và nhấp vào mũi tên addition game. Theo nó, dán địa chỉ hợp đồng một lần nữa. Sau đó các chức năng được kích hoạt lại. Hãy gọi hàm Getbalance. Số dư của bạn sẽ vẫn giữ nguyên số tiền như trước đây. Nếu bạn chỉ biết địa chỉ contract, bạn có thể xem các hồ sơ tôi đã kiểm tra. Cho đến nay, chúng tôi đã nghiên cứu bổ thêm và thử nghiệm addition game bằng cách sử dụng IDE Klaytn.
