5. Front-end for Klaytn Addition Game development

5.1 Settings
 
Trong video trước, bạn đã tạo được một contract dùng cho BApp. Bây giờ hãy phát triển front-end. Đầu tiên,hãy tiến hành với cấu hình cơ bản. Trong bài hướng dẫn này, tôi sẽ tải về node.js, npm, Truffle framework và visual studio code. Node.js là một nền tảng JavaScript phía máy chủ thực sự cần thiết cho BApp. Npm được cài đặt chung với node.js, có vai trò quan trọng trong việc tải xuống các công cụ và thư viện trong khi lập trình. Truffle framework cũng cần được cài đặt bằng cách tải xuống qua npm. Nếu bạn đã cài node.js và npm, hãy kiểm tra phiên bản và bỏ qua phần này nếu node.js bạn đang dùng là phiên bản 8 trở lên và npm là phiên bản 5 trở lên.
Hãy truy cập đến https://nodejs.org và tải xuống 10.15.3 LTS. Bạn hãy cài đặt nó nhé. Tôi đã cài sẵn rồi, nên tôi sẽ bỏ qua bước này. Sau khi cài đặt xong, chúng ta hãy kiểm tra xem node.js đã được cài đặt đúng trong PowerShell chưa. Gõ Node-v và kiểm tra phiên bản. Làm tương tự với npm. Npm -v, vâng, nó đã được cài đặt đúng cách. 
Cuối cùng, tôi sẽ cài Truffle. Truffle là một framework giúp bạn phát triển BApp dễ dàng hơn. Nó cho phép bạn biên soạn, kiểm tra và triển khai các hợp đồng thông minh. Đây là một framework rất phổ biến. Gần đây, Truffle đã được cập nhật phiên bản 5. Tuy nhiên, vì Klaytn đã được phát triển bằng phiên bản 4, nên tôi sẽ tải về Truffle phiên bản 4. Nếu bạn đang có sẵn phiên bản 4, hoặc thấp hơn, hay thậm chí là phiên bản 5, bạn cần xoá nó đi. Gỡ cài đặt bằng cách gõ npm uninstall -g truffle trong PowerShell. Sau đó, gõ ‘npm install -g truffle@4.1.15’ bạn sẽ tải về được phiên bản 4. 

Nếu bạn đã tải xuống mọi thứ, hãy kiểm tra phiên bản thông qua lệnh phiên bản truffle. Đây là phiên bản 4.1.15 và trình biên soạn solidity phiên bản 0.4.25. Solidity là một ngôn ngữ lập trình dùng để viết hợp đồng thông minh. Cuối cùng, hãy tải về trình chỉnh code tốt nhất, Visual Studio code. Truy cập ‘https://code.visualstudio.com/’ để tải về cho Windows. Tôi đã tải về trước rồi. Vì thế, tôi cũng sẽ bỏ qua bước này. Khi tải về, bạn hãy cài đặt và khởi chạy nó. Visual Studio code hỗ trợ đa nền tảng, có thể chạy trên Linux, Windows, Mac và bao gồm nhiều tính năng tiện dụng như hỗ trợ tìm lỗi, kiểm soát git, làm nổi bật cú pháp, v.v. 

Bây giờ bấm vào tab tiện ích mở rộng bên dưới để cài đặt tiện ích mở rộng nhằm hỗ trợ Solidity. Bạn hãy nhập ‘solidity' và chọn cái ở trên cùng. Click vào Setting. Phần mở rộng này giúp tô sáng màu cho từng ngữ pháp solidity và cho phép bạn biên soạn. Phần cài đặt đã hoàn tất. Hướng dẫn cấu hình cơ bản cần thiết để phát triển Frontend xin được kết thúc tại đây.
 
5.2 Download boiler plate

Hãy tải về boiler plate, một template cơ bản trong lập trình. Theo Klaytn, BApp có thể được phát triển trong Truffle framework. Một số vị trí trong Truffle cho phép bạn tải những template mẫu để lập trình BApp. Cái đó được gọi là Truffle Box. ‘https://truffleframework.com/boxes’ . Truy cập đến địa chỉ này, bạn có thể thấy các template. Ví dụ, nếu bạn muốn phát triển BApp bằng Angular hoặc React, bạn có thể tải xuống một template phù hợp với mình. Đây là template Angular và React. Tuy nhiên, các mẫu tải xuống ở đây chuyên về App Ethereum, do đó, bạn cần phải tải xuống và xoá các phần bên trong đi. Và bạn cần thiết lập nó cho Klaytn. Việc này không khó khăn lắm. Tôi đã tải xuống trước template có tên là webpack và thay đổi nó theo “Kiểu Klaytn" để phù hợp với bài giảng này. Tôi đã để nó trên Github, bạn có thể tải về. Thông tin thêm, chúng ta sẽ thao tác với JavaScript native và JQuery. Cho dù là người chưa biết gì về chúng, bạn vẫn có thể dễ dàng theo kịp. 

Mở PowerShell và chạy lệnh git clone trong ‘https://github.com/kkagill/addition-game-starter.git’ tại vị trí bạn muốn tải xuống. Tôi đã tải tất cả xuống này. Gõ ‘Cd addition-game-starter’  và enter. Hãy nhìn vào cấu trúc này bằng cách gõ “code”. Đây chính là cách bạn mở nó bằng Visual Studio. Hãy để tôi bắt đầu từ trên trước. Thư mục Contract là nơi bạn lưu các file contract solidity. Chúng ta đã có file contract Addition Game tạo trước và một contract ‘migrations’ dùng để chạy các file script trong thư mục migrations ở bên dưới. Đây là một file quan trọng để deploy smart contract, vì thế bạn đừng xoá nó nhé. 

Tiếp theo, file script trong thư mục migrations chứa logic dùng để lập trình. Nhìn vào file này bạn sẽ thấy, nó import file contract migrations và deploy nội dung đến node Klaytn. Trong thư mục src, tôi đã thiết lập cấu trúc bao gồm front-end của BApp. Index.html sẽ phụ trách phần “nhìn thấy" được trình bày ở front. Tôi đã tải jquery hoặc bootstrap để dùng trong BApp với cdn và tôi đã thêm trước phần css bên dưới.

File Index.js giống như một động cơ, nó thực thi các chức năng. Chúng tôi đã đặt tên cho các chức năng sẽ được viết trong tương lai. Biến ở dưới là các biến cấu hình hiển thị spinner khi tải. Đây là một phần quan trọng vì thế tôi đã tải trước rồi.  Package.json là nơi bạn thêm các dependencies cần thiết thông qua npm. Điều quan trọng là bạn sẽ tải xuống một file thư viện cho phép bạn giao tiếp với caver-js, blockchain Klaytn. Nó tương tự như web3 js của Ethereum. Truffle.js chịu trách nhiệm thiết lập môi trường. Thông qua Truffle, bạn sẽ xác định mạng nào phù hợp để deploy smart contract. Tôi sẽ trình bày nội dung này trong bài giảng tiếp theo. Webpack tối ưu hóa các file và phát hiện bất cứ khi nào có thay đổi về code và phản ánh các thay đổi cho trình duyệt mà không phải làm mới trang. Như vậy, tôi đã hoàn thành việc tải xuống và giải thích về template để tạo ra một trò chơi bổ sung trên Klaytn BApp. 

5.3 Deploying smart contract to Baobab 1
 
Từ giờ, hãy deploy hợp đồng thông minh AdditionGame mà chúng tôi đã tạo trên mạng thử nghiệm baobab. Trước khi bắt đầu, chúng tôi sẽ chạy lệnh npm install trong Terminal và cài đặt các dependencies cần thiết cho BApp. Nếu bạn không thấy Terminal ở bên dưới, hãy chọn terminal mới trên tab Terminal. Bây giờ hãy chạy lệnh npm install. Nó sẽ cần một chút thời gian. Khi kết thúc, một thư mục có tên ‘node_modules được tạo và cài đặt dependency hoàn tất. Tải về sẽ tốn một ít thời gian. 

Đầu tiên, hãy tạo một file mới trong thư mục migrations. Nhấp chuột phải vào thư mục migrations và chọn New file. Đặt tên là “2_deploy_contuces.js” và chúng tôi sẽ thêm logic để deploy hợp đồng AdditionGame cho node. Rê chuột đến file Initial migrations, copy và paste toàn bộ code. Hãy đổi thành ‘importing the AdditionGame contract’. Thay thế phần sẽ được deploy với AdditionGame. Logic cơ bản để triển khai đã kết thúc. Tuy nhiên, tôi sẽ viết code vào vài file trong BApp để lưu trữ thông tin tôi có được từ quá trình triển khai. 

Sau này, các thông tin đó sẽ hữu ích để tạo các trường hợp contract. Lập trình viên deploy contract AdditionGame và qua lệnh “then" chúng tôi nhận được dữ liệu json. Và trong này, 
if (AdditionGame._json) {
Nếu bạn nhận được dữ liệu json của Additions game, bạn sẽ lưu nó vào một file thông qua module hệ thống file.  Để làm được việc đó, bạn cần phải import nó trước. 
Gõ const fs = require ('fs')  lên trên cùng. Sau đó, tôi sẽ tạo 2 file. Đây là các file dùng để lưu ABI và địa chỉ contract. 

Nhấp chuột phải vào bất cứ đâu trên màn hình và đặt tên cho file mới là ‘deployedABI’. Tạo một file mới và đặt tên là “deployedAddress”. Bây giờ, chúng ta sẽ dùng hệ thống file để lưu từng file mới này. Đầu tiên, hãy tạo một code để lưu thông tin ABI. ABI là nội dung có thể tương tác giữa blockchain và contract. fs.writeFile( 'deployedABI', JSON.stringify(AdditionGame._json.abi),
Có một hàm writeFile trong hệ thống file. Xác định file nào cần viết và xâu chuỗi thông tin abi mà chúng tôi đã nhận được từ json và chuyển nó đến một đối số. Cuối cùng, chúng tôi sẽ xử lý lỗi. 
	(err) => {
  	if (err) throw err
  	console.log("파일에 ABI 입력 성공");
	})
Nếu có lỗi, hãy “throw" nó. Nếu không có, hãy viết log vào chỗ console. Việc này sẽ lưu thông tin ABI của contract đã deploy trong file deployedABI dưới dạng chữ. Để tiếp tục, tôi sẽ lưu địa chỉ của contract đã deploy vào file.  

fs.writeFile( 'deployedAddress', AdditionGame.address, (err) => { if (err) throw err console.log("파일에 주소 입력 성공"); }) 

Nếu bạn đã thực hiện theo các bước trên, bây giờ chúng ta có thể lưu các thông tin ta cần ngay lập tức vào các file sau mỗi lần deploy. Tôi sẽ tiếp tục thiết lập môi trường trong truffle.js và deploy nó trong bài giảng tiếp theo. 
 
5.4 Deploying smart contract to Baobab 2

Cuối cùng, bạn cần thiết lập cài đặt. Bạn nên quyết định mạng lưới để tiến hành deploy. Rê chuột đến file Truffle.js. Tại đây, tôi sẽ xác định mạng lưới luôn. Đầu tiên, tôi sẽ import thư viện gọi là  connect-privkey-to-provider. const PrivateKeyConnector = require('connect-privkey-to-provider') 
và tạo một hằng số là network ID. 

const NETWORK_ID = '1001'
1001 có ý nghĩa là network ID riêng của Baobab. 
const GASLIMIT = '20000000'
Đây là gas limit cho quá trình triển khai. Có 7 số 0. 
const URL = https://api.baobab.klaytn.net:8651 

Về URL, tôi đã điền địa chỉ nơi Klaytn đang khởi chạy full node, đó là mạng thử nghiệm baobab. Cuối cùng, chúng tôi cần một hằng số để giữ secret key, vì thế chúng tôi sẽ lấy secret key của tài khoản chúng tôi đã tạo trước thông qua ví Klaytn. Tôi đã nhắc các bạn lưu secret key ở đâu đó. Tôi đang copy và paste key của tôi vào Notepad. 

 const PRIVATE_KEY = ''
 
Bây giờ, hãy dùng những cài đặt trong module.exports. 
module.exports = { networks: { klaytn: { provider: new PrivateKeyConnector(PRIVATE_KEY, URL), network_id: NETWORK_ID, gas: GASLIMIT, gasPrice: null, } }, }

Tôi sẽ giải thích cho bạn hiểu trước. 
Tôi đã đề cập rằng chúng tôi sẽ sử dụng network “Klaytn". Bây giờ, chúng tôi sẽ chỉ định 4 tuỳ chọn ở đây. Đầu tiên, bạn chọn một provider cung cấp node Klaytn. Tạo một PrivateKeyConnector và truyền 2 đối số. Đối số 1 để truyền secret key của tôi và đối số 2 để truyền địa chỉ network nơi full node đang chạy. Điều này cho phép tôi kết nối với mạng thử nghiệm baobab bằng secret key cuả tôi. 

Tôi đã đề cập rằng chúng tôi sẽ sử dụng network “Klaytn". Bây giờ, chúng tôi sẽ chỉ định 4 tuỳ chọn ở đây. Đầu tiên, bạn chọn một provider cung cấp node Klaytn. Tạo một PrivateKeyConnector và truyền 2 đối số. Đối số 1 để truyền secret key của tôi và đối số 2 để truyền địa chỉ network nơi full node đang chạy. Điều này cho phép tôi kết nối với mạng thử nghiệm baobab bằng secret key cuả tôi. 
Chỉ định ID network và gas, và cuối cùng phí gas được đặt giá trị null. Vì mạng baobab sẽ tự động đặt phí gas nên chúng tôi truyền giá trị là null. Bây giờ tôi đã thiết lập môi trường để deploy smart contract. Nó khá đơn giản. Nào, cùng deploy thôi. Trong Terminal, chạy lệnh truffle deploy -network klaytn. Vâng, đã deploy thành công. 

Deploy cần một ít thời gian, và nó sẽ sớm kết thúc. Bạn có thể thấy cụm từ xác nhận thành công hiển thị trên màn hình. 
Bây giờ, nếu bạn nhìn vào file deployedABI, thông tin abi đã được lưu. Đến file deployed address và lưu ý rằng địa chỉ của contract được deploy đã được lưu lại. Nó đang hoạt động tốt. Cuối cùng, khi bạn deploy, một thư mục tên build sẽ được tạo nên. Nó chứa thư mục contracts ở bên trong và 2 file json trong thư mục contract. Chúng được gọi là artifact. Mỗi file artifact chứa thông tin ABI của hợp đồng tương ứng cũng như các thông tin liên quan đến hợp đồng. 

AIB là cụm viết tắt tiếng Anh của giao diện nhị phân ứng dụng; chúng tôi đã lưu trữ một file ABI đã deploy trong đó. Trong abi, chúng ta thấy các hàm và biến được viết ở định dạng json mà chúng ta sử dụng cho hợp đồng AdditionGame.
Nói một cách đơn giản, khi bạn deploy contract này lên blockchain, abi này đảm bảo gọi các chức năng trong contract và đảm bảo rằng dữ liệu được trả về theo định dạng tôi mong đợi. Đó là nơi bạn xác định cách bạn có thể tương tác với hợp đồng. Nếu bạn kéo xuống phía dưới cùng, sẽ có một phần network. 1001 là ID mạng duy nhất của Klaytn. Địa chỉ là địa chỉ mà contract đang được deploy đến trên mạng thử nghiệm Baobab. 

Cuối cùng, nếu bạn muốn deploy lại contract cho node Klaytn, bạn có thể sử dụng lệnh này. Ví dụ, khi chúng tôi cần sửa đổi contract, chúng tôi cần deploy lại nó cho node. 
truffle triển khai -compile-all -reset -network - Klaytn 

“Compile all" tất cả contract biên soạn lại. Việc thiết lập lại buộc các file script trong thư mục Migrations chạy lại. Chạy nó để deploy lại contract cho node một lần nữa. Vâng. Hoàn tất. Mở file deployedAddress và bạn sẽ thấy rằng địa chỉ đã thay đổi. Như vậy, tôi đã hoàn thành deploy Contract với network Klaytn Baobab bằng truffle. 
 
5.5 Account verification UI

Cùng bắt đầu bằng cách đăng nhập vào tài khoản bạn đã tạo bằng ví baobab. Có 2 cách để chúng ta xác thực tài khoản. Đầu tiên, bạn có thể sử dụng kết hợp file keystore và mật khẩu. Và thứ hai là xác thực bằng private key. Ở đây, chúng ta sẽ chọn cách thứ nhất là kết hợp file keystore và mật khẩu. Đầu tiên, tôi sẽ viết code html. Rê chuột đến Index.html và thêm nội dung vào phần body. 
클레이튼(Klaytn)
속전속결 덧셈 게임
3초안에 맞출 시 0.1 KLAY 지급 이벤트 로그인 로그아웃

Bạn hãy bấm dừng video lại và viết code này. Cài đặt này rất đơn giản. Thuộc tính class ở trong thẻ div sử dụng bootstrapping để giúp UI trông đẹp hơn. Tôi sẽ bỏ qua mô tả bootstrap. Đầu tiên, tôi đặt các cụm từ giải thích lên trên. Phía dưới, tôi đã thêm nút login và logout. Khi tôi nhấp vào nút login, nó sẽ khởi chạy một cửa sổ modal. Khi tôi nhấp vào nút logout, hàm The handleLogout sẽ được thực thi. Lưu ý rằng tôi đã cài đặt để nút logout không xuất hiện trong css. 

Hãy chạy ứng dụng và kiểm tra xem code có đang hoạt động đúng không nhé! 

Chạy lệnh npm run dev trong terminal. Mở Chrome và truy cập đến địa chỉ localhost: 8081. Nhìn không được đẹp lắm, nhưng giao diện vẫn ổn. Bây giờ, hãy tạo một modal để nó mở ra khi chúng ta nhấp vào nút login. 
‘https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals’ 

Nếu bạn truy cập đến trang bootstrap này, bạn có thể lấy được code modal. Copy phần này và quay về file html. Tôi sẽ paste nó bên ngoài nội dung thẻ div. Giờ thì hãy đổi nội dung của modal này.

Đầu tiên, cài div id=loginModal.
Bạn nên làm như thế, vì nó cho phép modal mở ra khi bạn nhấp vào nút login. Nó khớp modal với giá trị data-target của nút login ở phía trên. Tiếp theo, chúng ta sẽ làm cho kích thước modal nhỏ lại . Xoá toàn bộ phần modal header. Và xoá nội dung bên trong body modal. 
Bây giờ, hãy thêm phần để tải keystore và gõ mật khẩu. 
Keystore
Cài dạng input là file và để hàm handleimport được gọi trên sự kiện onchange. Và ở phía dưới, thêm vào phần cho mật khẩu. 
Copy và paste ở đây, và đổi tên. 
Nếu giá trị được viết trong cửa sổ input password, gọi hàm handlePassword. Và tôi đã thêm phần để hiển thị một message khi xác thực thành công hoặc có lỗi xảy ra. Cuối cùng, đổi close thành 닫기 và save changes thành 제출. Thêm thuộc tính id vào và cho phép gọi hàm  handleLogin khi được nhấp. 
Vâng, bây giờ tôi sẽ kiểm tra giao diện xem code có hoạt động tốt không. Nhấp vào nút login. Modal đã hiện ra với các tuỳ chọn là chọn tải lên một file và nhập mật khẩu vào. Như vậy, tôi đã hoàn thành hướng dẫn thiết kế UI cho xác thực tài khoản.
