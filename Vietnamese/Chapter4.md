# 4. Developing an addition game with Klaytn Tools
## 4.1 Intro
 

Chào mọi người. Trong phần hướng dẫn này, tôi sẽ phát triển BApp được gọi là addition game sử dụng Blockchain Klaytn. BApp là từ viết tắt của Blockchain Applications. Chúng ta hãy tạo trò chơi pop-up sẽ trả 0,1 Klay miễn phí nếu bạn giải đúng phép toán cộng trong vòng 3 giây.
 
 
Hãy xem cách nó hoạt động. Đầu tiên, đăng nhập vào tài khoản quản trị. Chúng tôi sẽ xác thực tài khoản bằng file keystore và mật khẩu. Vì vậy, hãy chọn file keystore và nhập mật khẩu. Sau khi xác thực tài khoản, sử dụng nút Send KLAY to Contract để nhập số lượng cần sử dụng. Chúng tôi gửi KLAY đến địa chỉ contract để cho người dùng thấy sự minh bạch về số tiền được sử dụng trong game. Lưu ý rằng chỉ có thể thực hiện với tài khoản quản trị.


Bây giờ, tôi đang gửi 1 KLAY đến contract này. Khi giao dịch hoàn thành, người chơi sẽ biết số tiền cần phải chi. Người dùng có thể bắt đầu addition game. Nếu bạn cài đặt trong 3 giây, Contract sẽ gửi 1 KLAY tới tài khoản người chơi. Hãy bắt đầu nào.
Nếu bạn trả lời sai, hệ thống sẽ khởi động lại. Nếu bạn thử lại và đúng, bạn có thể nhận KLAY bằng cách nhấn nút OK. Khi giao dịch hoàn thành, số dư trong contract sẽ giảm 0,1 KLAY. Như bạn có thể thấy, giao dịch xử lý rất nhanh. Đó là điểm mạnh của Klaytn. Nếu bạn nhấp vào liên kết bên dưới, bạn sẽ được dẫn tới scope Klaytn, nơi bạn có thể xem thông tin của giao dịch vừa rồi.


Nếu bạn có kinh nghiệm phát triển DApp trên Ethereum, bài hướng dẫn này sẽ không thể làm khó bạn. Klaytn là một nền tảng xây dựng từ hard fork Byzantine của Ethereum, vì vậy bạn sẽ cảm thấy quen thuộc. Klaytn đã gỉam bớt độ phức tạp để các lập trình viên Dapp có thể dễ dàng thích ứng. 
Ví dụ: JavaScript library, caver.js dùng để tương tác với Blockchain Klaytn thì tương tự như web3.js của Ethereum. Ngoài ra, Klaytn còn hỗ trợ solidity - ngôn được sử dụng phổ biến để viết smart contract.

Bởi vì Blockchain Klaytn sử dụng framework Truffle nên bạn cũng sẽ dễ dàng trong việc phát triển BApp. Những người không có kinh nghiệm phát triển BApp vẫn có thể phát triển BApp trong nền tảng Blockchain Klaytn thông qua các bài hướng dẫn này. Nhưng trước hết, bạn cần hiểu cơ bản về Blockchain và ngôn ngữ solidity để viết smart contract. Tôi sẽ gửi đường link cho bạn tìm hiểu. 
Chúng tôi phát triển một vài công cụ để hỗ trợ Klaytn. 
Trước tiên, tôi sử dụng IDE để test smart contract, một ví có thể quản lý nhiều tài khoản,
và Klaytn scope để tìm kiếm thông tin của giao dịch.

 
## 4.2 Klaytn Wallet & account management

Để sử dụng mạng lưới blockchain, bạn phải có tài khoản riêng. Và tài khoản để quản lý token KLAY. Vì vậy, tôi sẽ sử dụng ví của Klaytn. Nó thân thiện với người dùng và cực kỳ dễ sử dụng. Truy cập vào https://baobab.klaytnwallet.com/, nó sẽ hiển thị mạng lưới Baobab, tạo mới và quản lý tài khoản của bạn. Xin lưu ý, ví này chỉ dùng để thử nghiệm, và Klay được sử dụng ở đây không có giá trị về mặt tiền tệ. Đầu tiên, hãy tạo một tài khoản mới. Nhấp vào "Create a new wallet". Đây là quá trình tạo mật khẩu và file keystore. Trước khi tiến hành, tôi sẽ giải thích file keystore là gì. Có thể hiểu đây giống như quy trình chúng ta đến ngân hàng để làm sổ ghi tiền gửi, và chúng ta cất nó ở nơi an toàn để những người khác không thể đụng đến. Vault này là sự kết hợp giữ file keystore và mật khẩu, cần thiết để bảo vệ secret key khỏi các hacker và những yếu tố ngoại vi. 


Bây giờ, hãy tiếp tục và tạo một file keystore. Nhập mật khẩu của bạn vào đây, nhấp “next step” và tải xuống file keystore.
Sau khi tải xong, lưu secret key xuất hiện trên màn hình. Secret key rất quan trọng, dùng để ký giao dịch trong BApp Klaytn. Secret key này không nên được tiết lộ ra bên ngoài. Nó giống như mật khẩu tài khoản ngân hàng, nếu không có nó, bạn sẽ mất tiền.


Đó là lý do tại sao tôi tạo file keystore để bảo vệ secret key. Người dùng phải lưu file keystore và mật khẩu trước khi truy cập secret key. Ngay cả khi hacker có được file keystore, nhưng không biết secret key thì cũng không thể truy cập được và dĩ nhiên, không thể lấy được tiền của bạn. Nhưng điều này không có nghĩa là bạn có thể tiết lộ file keystore. Đừng để file keystore bị lộ ra bên ngoài.
Bây giờ, tôi sẽ lưu secret key trong Notepad. Đây chỉ là testnet nên cũng không cần thiết lắm, tuy nhiên, tôi sẽ làm luôn cho đủ các bước. Bạn nên lưu secret key ở nơi bạn thấy an toàn. Sau khi lưu xong, bạn hãy nhấp vào "View wallet info" ở bên trái màn hình. Bây giờ tôi đã truy cập được vào ví của mình.
Có 2 cách để truy cập vào ví. Một là sử dụng secret key và thứ hai là truy cập bằng file keystore cùng mật khẩu. Hãy thử với cách đầu tiên là truy cập bằng secret key. Sao chép secret key từ Notepad và dán vào. 

 
Thông tin ví của bạn sẽ được hiển thị ngay. Đây là địa chỉ ví công khai của tôi và secret key ở bên dưới. Tôi có thể xem danh sách giao dịch của mình ở đây. Ở đây chưa có gì vì tôi chưa thực hiện giao dịch nào. Ở bên phải màn hình, bạn có thể thấy số  KLAY token tôi có và tôi cũng có thể thêm token vào ví bằng cách nhấp vào nút "dấu cộng".
 
Bây giờ, hãy thử nhận KLAY trên tài khoản này. Nhấp vào tab KLAY faucet để nhận KLAY miễn phí. Tài khoản hiện tại của tôi có số dư bằng không. Nếu bạn nhấp vào nút Run Faucet, bạn sẽ nhận được 5 KLAY. Sau khi nhận được KLAY, bạn vẫn có thể nhận nó lần nữa sau 24 giờ. Số block này có nghĩa là sau 24 giờ, đây sẽ là block nơi bạn sẽ nhận tiếp token. 
Vì trong thời gian ngắn bạn không thể nhận được nhiều KLAY, bạn nên chia thành nhiều khoản KLAY để thử nghiệm. Lý do bạn nên nhận KLAY sau 24 giờ vì một số người cũng đang sử dụng KLAY giống bạn một cách mơ hồ. Klaytn chia sẻ họ đang trong quá trình hoàn thiện hơn. Bây giờ, hãy chuyển KLAY sang tài khoản khác. 


Bấm chọn Send klay & token, bạn có thể gửi tiền từ địa chỉ này đến địa chỉ khác. Nhập địa chỉ ví người nhận. Đây là địa chỉ được tạo trước để dùng cho thử nghiệm này. Tôi sẽ gửi 1 KLAY để xem bao nhiêu phí tôi phải trả. Nó sẽ hiển thị tối đa phí giao dịch là 0,000625 KLAY. Đây giống như là phí hoa hồng. Chi phí này được tính bằng gas price nhân với gas limit. Hiểu đơn giản, gas price là chi phí cho lệnh giao dịch đến node đồng thuận. Gas Price của Klaytn luôn cố định, không giống như Ethereum. Rất khó để dự đoán phí hoa hồng vì gas price của Ethereum luôn dao động. Tuy nhiên, gas price của Klaytn luôn cố định ở mức 25 ston, bất kể bạn thực hiện giao dịch nào. 

Gas limit là chi phí tối đa để xử lý giao dịch. Tại sao chúng ta cần có mức tối đa cho gas limit? Giả dụ, chúng ta có một số vòng lặp vô hạn trong một giao dịch. Sau đó, giao dịch đơn giản này sẽ tiếp tục chạy trong mạng lưới. Điều này gây ra sự suy giảm hiệu suất của mạng và gây thiệt hại tới mọi người. Vì vậy, nếu bạn có hơn 25.000 gas, hãy nhận ra rằng có gì đó khác thường và bạn phải ngừng quy trình này.


Và gas price được tính là 25 test_ston, ston là một trong những đơn vị tiền tệ của KLAY. Tương tự như 1 đô la Mĩ có gía trị là 100 xu thì Klay cũng có rất nhiều đơn vị tính. https://docs.klaytn.com/klaytn/design/computing/exec_model - tài liệu chính thức của Klaytn chia sẻ về các đơn vị KLAY. Đơn vị tiêu chuẩn là KLAY được đặt ở giữa, và peb ở trên cùng là đơn vị nhỏ nhất. Đơn vị 10 mũ 9 peb sẽ là ston. Vậy 25 ston sẽ quy đổi thành bao nhiêu KLAY?.
https://blockchains.tools/pebConverter?l=KLAY, truy cập trang web này, bạn có thể quy đổi ra nhiều đơn vị. Nếu nhập 25 ston vào đây, bạn sẽ có kết quả số KLAY tương ứng. Nếu nhân với gas limit là 25.000 thì số KLAY cần dùng là 0,000625 KLAY. Nó được sử dụng như một khoản phí giao dịch. Hãy thử lại trên máy tính. Copy số KLAY này, nhân với gas limit 25000, thì kết quả chi phí giao dịch sẽ xuất hiện. Đây là chi phí xử lý giao dịch.


Lưu ý rằng khi bạn gửi các khoản tiền nhỏ như này từ Klaytn, chi phí giao dịch luôn cố định ở mức 0,000625 KLAY. Tuy nhiên, chi phí giao dịch không cố định trong giao dịch thông qua chức năng smart contract vì gas limit thay đổi theo mức độ phức tạp của giao dịch. Tôi sẽ giải thích thêm về điều này sau.
 
Bạn có thể tự thay đổi gas limit bằng cách nhấp vào nút “Edit” bên cạnh. Nhưng tôi khuyên bạn nên dùng luôn con số đã được mặc định.
Hãy thử gửi giao dịch ngay bây giờ. Ở trang tiếp theo, bạn sẽ thấy thông tin về số tiền bạn đã gửi và phí giao dịch. Bạn nhấp vào “Yes” để trả lời cho câu hỏi “Do you want to continue?” Như vậy, giao dịch đã hoàn thành chỉ trong chớp mắt. Sau đó nhấp “view transaction info”, nội dung bạn nhìn thấy sẽ được lưu lại trong block và hiển thị cho người dùng. Tôi sẽ giải thích chi tiết sau. Như vậy, chúng ta đã hoàn thành bài giảng về ví Klaytn. 


## 4.3 Klaytn IDE & Smart Contract 1
Liên quan tới IDE của Klaytn, hãy tạo một smart contract contract đơn giản cho add-on game của chúng ta. Thay vì tập trung nhiều vào smart contract, tôi sẽ tập trung vào các công cụ Klaytn.
Bạn có thể tạo và kiểm tra các smart contract bằng cách truy cập vào http://ide.klaytn.net/. Nó tương tự như IDE Ethereum, nhưng ở đây nó được kết nối với node Klaytn, chứ không phải với node Ethereum. Bây giờ, hãy xem các tính năng của IDE Klaytn bằng cách tự tạo smart contract cho các add-on game.
 
Như bạn đã biết, “Hợp đồng thông minh” tiếng Anh gọi là “Smart contract”. Tôi sẽ gọi ngắn gọn là “Contract” trong các bài giảng. Nếu bạn nhìn vào đây, bạn sẽ thấy có contract count đã được tạo theo mặc định. Tôi sẽ xóa cái này và bắt đầu. Hãy xóa nó. Nhìn vào dòng mô tả này, bạn thấy rằng IDE Klaytn sử dụng Solidity phiên bản 0.4.24, vì vậy cũng cần làm việc với phiên bản này.
 
Contract này có ba hàm. Đầu tiên là gửi KLAY vào contract, thứ hai để tải số dư của contract và cuối cùng là gửi KLAY từ contract đến tài khoản người dùng. Chúng ta sẽ làm từng bước một và sử dụng các công cụ để kiểm tra. Đầu tiên, hãy đặt tên cho contract là AdditionGame.

 (Code)
Tại thời điểm triển khai, bạn tạo một biến trạng thái có thể lưu trữ địa chỉ của tài khoản quản trị. Và tôi đang tạo ra một constructor. Khoan đã, các constructor thường dùng để làm gì? Vâng, nó có nhiệm vụ khởi tạo.Trong trường hợp của ngôn ngữ solidity, bạn không thể viết hoặc tải lại constructor, đặc biệt là khi đó là constructor được load đầu tiên khi bạn deploy. Tôi có thể tận dụng điều này và thiết lập một tài khoản cho chủ sở hữu của contract. Đầu tiên chúng tôi tạo chủ sở hữu biến trạng thái. Type của nó là address. Tạo một constructor

Owner is msg.Sender.
 Tôi vừa tạo một constructor. Msg.sender là người đang gọi là contract. Msg.sender trong constructor chính là account được dùng để deploy. Vì vậy, tôi sẽ gán tài khoản đó cho biến trạng thái chủ sở hữu và lưu nó mãi mãi vào Blockchain. Đây là sự khởi tạo. Bây giờ, hãy kiểm tra code mà chúng tôi vừa viết. 
Bạn cần biên soạn trước. Nhấp vào Auto ở đầu bảng bên phải để tự động biên soạn mỗi khi bạn viết code. Đầu tiên bạn phải bấm vào nút “compile” để xem nó có biên soạn không. Vâng, các thông tin được biên soạn sẽ hiển thị ở bên dưới. Chúng ta hãy thiết lập lại môi trường. Có 2 sự lựa chọn: DEV NODE và Baobab. Và tôi có thể thêm mạng lưới mới. Chức năng mạng lưới mới vừa được thêm vào sẽ kết nối với địa chỉ rpc nơi node Klaytn hiện đang chạy. Tôi sẽ bỏ qua bước này. Node DEV là một tùy chọn để kết nối và kiểm tra node phát triển bởi Klaytn. Node Dev tạo một tài khoản ngẫu nhiên và cho phép bạn đặt trước 100 KLAY. Và nó được cài đặt miễn phí gas để thử nghiệm. Vì vậy, nhìn vào From Account ở bên dưới, bạn sẽ thấy đã có sẵn 100 KLAY cho thử nghiệm trong tài khoản này. Một lựa chọn khác là kết nối với Baobab, cũng được kết nối với mạng thử nghiệm chính. Và thời điểm bạn chọn Baobab, KLAY trong tài khoản bên dưới thay đổi thành 0. Các node dev và node baobab hoạt động độc lập với nhau, vì vậy các tài khoản tại cùng một địa chỉ được nhận dạng bởi các node khác nhau, và trạng thái của tài khoản sẽ không giống nhau vì các node khác nhau. Vì vậy, số dư sẽ thay đổi.
 
 
Hãy thử làm mới trang bằng việc chọn lại node Dev. Tiếp tới Loading Account, không có tài khoản đã sử dụng trước đây và tôi tạo một tài khoản mới khác. Điều thú vị là bạn có thể tải xuống tài khoản này dưới dạng file keystore hoặc secrekey và sử dụng lại. Nếu bạn đang thử nghiệm trên một máy tính khác, bạn muốn tiếp tục với tài khoản cũ, bạn có thể sử dụng tùy chọn này tại thời điểm đó. Ví dụ: nếu bạn nhấp vào tài khoản, bạn sao lưu tài khoản hiện tại. Khi bạn chọn nó, một cửa sổ sẽ mở ra và bạn có lựa chọn lấy file keystore hoặc secret key của mình. Đơn giản chỉ cần sao lưu secret key của bạn. Khi bạn nhấp Copy, bạn đã sao lưu secret key của tài khoản này.
 
 
Sau đó làm mới trang một lần nữa. Khi tài khoản được tạo, nhấp lại và chọn import an account. Chuyển đến Private Key và dán sao lưu của secret key. Label hiển thị sẽ được gọi là test account.Import. Nếu bạn chọn lại tài khoản, bạn sẽ có tài khoản thử nghiệm mà chúng tôi đã nhập bên dưới. Vì vậy, khi bạn quay lại trang này theo cách trên trên một máy tính khác, bạn có thể thực hiện kiểm tra một cách nhất quán.
 
 
Thay vì giải thích Tx Value, tôi sẽ cố gắng triển khai nó đầu tiên. Deploy
Sau khi bạn nhấp vào nút compile, bạn sẽ triển khai AdditionGame. Nhấn Deploy, việc deploy sẽ hoàn thành trong vòng chưa đầy 3 giây. Có một hàm băm TX trong giữa cái bảng, phải không? Đây là thông tin giao dịch hàm băm được tạo ra khi triển khai. Trên cùng bảng, thông tin hàm băm cho thấy địa chỉ nào đã được triển khai.
 
 
Nếu bạn nhìn vào bảng điều khiển bên cạnh, bạn sẽ thấy địa chỉ nào hiện đang có contract được deploy và bên dưới bạn có lựa chọn tải giá trị của biến trạng thái chủ sở hữu. Đây là một hàm getter. Vì chúng tôi có thể nhìn thấy công khai biến trạng thái của chủ sở hữu, chúng tôi có thể tự động tạo ra một hàm getter để lấy giá trị của biến chủ sở hữu. Khi bạn nhấn nút Call, địa chỉ bên dưới sẽ xuất hiện. Địa chỉ này là gì?
 
Vâng, đây là địa chỉ tài khoản của người đã deploy contract này. Tôi đã deploy contract từ một tài khoản hiển thị khác, vì vậy tài khoản này được lưu dưới dạng giá trị của chủ sở hữu biến trạng thái. Vâng, tôi đã viết code solidity thông qua IDE Klaytn và đã kiểm tra chủ sở hữu của contract. Tiếp theo, chúng ta sẽ viết và kiểm tra hai hàm còn lại trong bài giảng tiếp theo.



 
## 4.4 Klaytn IDE & Smart Contract 2
 

Chúng ta hãy tiếp tục tạo chức năng xem số lượng KLAY còn lại trong contract. Vui lòng bấm tick vào ô "Auto". Bên trong constructor, chúng ta sẽ tạo hàm getBalance.
(Code)

Tên hàm là getBalance(), hiển thị public và type là view. Cuối cùng, xác định loại unit bằng hàm returns.
(Code)

Address ý chỉ contract đang dùng. Đây là contract edition game, và balance là một member có thể truy cập được trong hàm. Hàm dùng để tải số dư KLAY tại địa chỉ hợp đồng này coi như đã hoàn thành. Hãy deploy lại để kiểm tra. Nhấp vào nút Deploy, sau đó chức năng getBalance () được tạo và nút Call được kích hoạt. Hãy nhấp vào "Call", số dư hiện tại bằng 0, nghĩa là tôi chưa gửi token đi.
 
 
Tiếp theo, hãy tạo một hàm gửi KLAY đến địa chỉ contract từ tài khoản chủ sở hữu.
(Code)

Tôi tạo hàm với hiển thị public và type là payable. Bất cứ khi nào bạn dùng hàm gửi KLAY từ tài khoản, hãy chọn type payable. Bằng cách đó tôi có thể nhận được tiền từ hàm. Tiếp theo, chúng ta sẽ kiểm tra tính hợp lệ.
 
(Code)

Nếu bạn không sử dụng từ khóa "require", hàm sẽ không hoạt động. msg.sender ý chỉ tài khoản đang gọi hàm và phân biệt với tài khoản chủ sở hữu biến trạng thái, để mà nếu tài khoản hiện đang tải hàm này không phải là tài khoản chủ sở hữu, nó sẽ không thực thi hàm. Vì vậy, tôi đã kiểm tra tính hợp lệ để xem liệu tôi có thể chuyển KLAY từ tài khoản chủ sở hữu sang contract hay không. Hãy kiểm tra ngay bây giờ nào.
  

Hãy nhấn nút Deploy. Chức năng deposit hiện được kích hoạt. Nếu bạn gửi KLAY với chức năng "deposit", bạn phải sử dụng Tx.Value. Nếu hàm có type là payable, bạn phải sử dụng tx.Value. Với test_KLAY bên cạnh, nhập 1 làm giá trị. Sau đó nhấp vào nút "send" ở chức năng "deposit". Giao dịch của bạn đã thành công và xuất biên lai giao dịch cho bạn. Nhìn vào mục "From Account", số dư sẽ giảm từ 100 KLAY xuống còn 99 KLAY. Nếu là giao dịch thật, chúng ta sẽ phải khấu trừ số dư, bao gồm chi phí gas được sử dụng để xử lý giao dịch, nhưng ở đây chúng ta đã chọn Dev node, không bao các chi phí kia. 
 

Bây giờ, hãy gọi hàm getbalance để xem số dư của contract.  Nó chứa một giá trị. Xin lưu ý rằng chúng ta chỉ gửi 1 KLAY nhưng con số lớn như này có thể khiến bạn hoang mang. Đây là giá trị của 1 KLAY đã được chuyển đổi thành peb, đơn vị nhỏ nhất của KLAY. Trong virtual machine Klayton, bạn cần chuyển đổi KLAY thành đơn vị nhỏ nhất là peb, do đó bạn nhìn thấy con số này. Khi nhập một giá trị từ Tx value và gửi nó đến hàm deposit.
Đây là một tính năng rất hữu ích của mạng thử nghiệm. 
Bạn cũng có thể thử với các đơn vị khác nhau trong tx value. Lần này với đơn vị thấp nhất, peb. Hãy chuyển đổi 2 KLAY thành peb và gửi nó đến contract. Quay trở lại trang web chuyển đổi đơn vị, nhập 2 KLAY, sao chép giá trị đã chuyển đổi sang peb và dán vào Tx value.
 
Và sau đó bạn chọn hàm deposit. Giao dịch đã thành công. "Call" hàm getbalance. Giá trị tăng lên. Bạn có thể kiểm tra bằng việc chuyển đổi đơn vị.
 
Và gas limit là giới hạn gas và nó tự động được đặt mặc định. Nói cách khác, nó tính toán gas limit để vào hàm và tự động xác định nó. Điều này là do tính toán phụ thuộc vào độ phức tạp của hàm. Vì vậy, giới hạn gas để xử lý chức năng là không cố định. Khi chúng tôi gửi tiền bằng ví từ khóa trước, giới hạn gas đã được cố định ở mức 25000. Đó chỉ là một giao dịch gửi tiền, do đó không có sự phức tạp và giới hạn gas được cố định. Trên thực tế, bạn có thể tự nhập giới hạn gas này và thử kiểm tra chính xác hơn. Cho đến nay, tôi đã học được giới hạn gas và tôi đã chi trả phần chuyển tiền từ tài khoản chủ sở hữu bằng cách sử dụng giá trị giao dịch để ký hợp đồng.
 
 
## 4.5 Klaytn IDE & Smart Contract 3
 
Với chức năng cuối cùng này, hãy viết logic để chuyển tiền từ contract vào tài khoản người dùng khi họ đã giải phép tính ở addition game. Thông tin thêm, khi trả lời đúng, người dùng sẽ gọi trực tiếp hàm này để nhận tiền.
 
Lấy giá trị KLAY để truyền cho người dùng làm đối số. Lưu ý rằng giá trị này được chuyển đổi sang peb từ giao diện người dùng và được truyền đi. Và một hàm return bool. Tiếp theo, bạn cần xác thực rằng số dư trong contract bằng với giá trị bạn muốn gửi cho người dùng.
 

Gọi hàm getbalance() ở trên để gọi số dư còn lại trong contract hiện tại và chuyển nó nếu nó bằng hoặc lớn hơn giá trị nhận được dưới dạng đối số.

msg.sender, người dùng có câu trả lời đúng đã gọi hàm này,
(transfer (_value)) để nhận tiền thưởng và gửi KLAY cho người dùng bằng chức năng chuyển tiền. Và cuối cùng, Tôi sẽ return true.

Hiện tại, chúng ta đã viết code cho smart contract mà chúng ta sẽ sử dụng. Nó rất đơn giản. Bây giờ hãy kiểm tra một lần cuối cùng. Để deploy, đặt Tx value bằng 0 và đặt gas limit về (auto). Bấm deploy. Deploy thành công. Để sử dụng hàm chuyển tiền, chúng ta sẽ gửi lại KLAY vì số dư contract đang là 0 sau khi deploy lại. Điền Tx value bằng 3 và đổi Test_peb thành Test_klay. Nhấn nút Send trong hàm Deposit. Nếu giao dịch thành công, hãy nhấp vào ‘get balance’, số tiền bạn có sẽ hiện ra. Hãy nhớ rằng số dư tài khoản của tôi là 94 KLAY.
 
Bây giờ hãy sử dụng chức năng transfer. Đặt Tx value trở về 0 và nhấp vào nút Send của chức năng transfer. Bây giờ, đây là một hàm chứa các tham số, bạn phải gửi giá trị đối số khi cửa sổ xuất hiện. Bạn cũng phải chuyển đổi KLAY sang peb khi bạn gửi nó. Hãy nhớ rằng các giá trị KLAY được gửi đến contract được chuyển đổi thành peb và truyền đi.  Quay trở lại trang web chuyển đổi, và chuyển đổi 1 KLAY. Sao chép giá trị Peb và dán vào. Bấm nút Call, giao dịch sẽ được thực hiện và biên nhận sẽ được trả lại thành công. Số dư trong ‘From account’ đã tăng thêm 1 KLAY, từ 94 KLAY trước đó lên 95. Cuối cùng, khi gọi hàm getBalance hoàn thành, còn lại 2 KLAY và 1 KLAY đã giảm đi.
 

Thông tin thêm, dev node này là một node đang chạy thật, vì thế các giao dịch chúng ta đã thực hiện sẽ được lưu lại trong mạng. Làm thế nào để bạn kiểm tra nó? Chỉ cần có địa chỉ contract. Thông tin dưới nút deploy chính là địa chỉ contract chúng ta đã deploy đến dev node. Hãy sao chép địa chỉ này và làm mới trang.
 

Nhấp vào nút compile một lần nữa và nhấp vào mũi tên Additiongame. Dán địa chỉ contract đã copy vào. Sau đó các chức năng được kích hoạt lại. Hãy "call" hàm Getbalance(). Số dư của bạn sẽ vẫn giữ nguyên như trước. Rất đơn giản. Chỉ cần có địa chỉ, bạn có thể xem thông tin giao dịch tôi vừa thử nghiệm. Như vậy, chúng ta đã tìm hiểu về phép tính cộng và thử nghiệm nó với IDE của Klaytn.
