# 5. Front-end for Klaytn Addition Game development
 
## 5.1 Settings


Bây giờ bạn có thể tạo ra hợp đồng sử dụng cho BApp trong những bài hướng dẫn trước đó, chúng ta hãy phát triển front-end. 
Đầu tiên,chúng ta tiến hành với các config đơn giản. 
Trong bài hướng dẫn này, tôi sẽ tải node.js, npm, framework truffle và visual studio code. 
Node.js là nền tảng JavaScript phía máy chủ thực sự cần thiết trong phát triển BApp. 
Npm được cài đặt chung với node.js, có vai trò cần thiết trong việc tải các công cụ và libraries khi lập trình. 
Framework Truffle mà chúng ta sẽ cài đặt cần được tải thông qua npm. 
Nếu bạn đã cài đặt node.js và npm, hãy kiểm tra phiên bản đó và bỏ qua phần hướng dẫn này nếu node.js bạn đang dùng là phiên bản thứ 8 và npm là phiên bản 5 trở lên.


Hãy truy cập https://nodejs.org và tải 10.15.3 LTS. Bạn hãy cài đặt nó. 
Tôi đã thực hiện xong vì vậy tôi bỏ qua bước này.
Sau đó, chúng ta kiểm tra xem node.js có được cài đặt đúng trong PowerShell hay không.
Nhập Node-v và kiểm tra phiên bản. Làm tương tự với npm. Npm -v,Vâng, nó đã được cài đặt đúng cách.


Cuối cùng, tôi sẽ cài đặt Truffle.
Truffle là một framework giúp bạn dễ dàng phát triển BApp.  
Nó cho phép bạn biên soạn, kiểm tra và triển khai các hợp đồng thông minh. 
Framework này rất phổ biến. 
Gần đây, nó đã cập nhật lên phiên bản thứ 5. 
Tuy nhiên, vì Klaytn đã được phát triển bằng phiên bản thứ 4, nên tôi sẽ sử dụng bản này. 
Nếu bạn đang có sẵn phiên bản 4, hoặc thấp hơn, hay thậm chí là phiên bản 5, bạn cần xóa nó đi. 
Gỡ cài đặt nó bằng cách gõ ‘npm uninstall -g truffle’ trong PowerShell.  
Sau đó, gõ 'npm install -g truffle@4.1.15' và bạn sẽ tải về được phiên bản 4.


Nếu bạn đã tải xuống mọi thứ, hãy kiểm tra phiên bản thông qua lệnh phiên bản truffle.
Đây là phiên bản 4.1.15 và trình biên soạn solidity phiên bản 0.4.25. 
Solidity là ngôn ngữ lập trình dùng để viết hợp đồng thông minh. Cuối cùng, hãy tải về trình chỉnh code tốt nhất - Visual  Studio Code. Truy cập 'https://code.visualstudio.com/' để tải về máy. 
Tôi đã tải nó từ trước. Vì vậy, tôi cũng sẽ bỏ qua phần này. 
Khi đã tải về, bạn hãy cài đặt và chạy nó. 
Visual Studio Code hỗ trợ đa nền tảng, chạy trên Linux, Windows, Mac và gồm một số tính năng tiện dụng như hỗ trợ gỡ lỗi, kiểm soát git, syntax highlighting, v.v.


Bây giờ bấm vào tab tiện ích mở rộng ở bên dưới để cài đặt tiện ích mở rộng hỗ trợ ngôn ngữ solidity. Bạn hãy nhập 'solidity' và chọn cái ở trên cùng. 
Nhấp vào Install. Nó sẽ hiển thị độ sáng cho mỗi solidity và cho phép bạn biên soạn lại. 
Cài đặt hoàn tất. Hướng dẫn config cơ bản để phát triển Front-end xin được kết thúc tại đây. 
 
 
## 5.2 Download boilerplate
 
 
Chúng ta hãy tải boilerplate, một template cơ bản trong lập trình. 
Klaytn chỉ ra rằng BApp có thể phát triển trong framework Truffle.
 Một số vị trí trong Truffle cho phép bạn tải xuống các template mẫu để phát triển BApp..
Cái đó được gọi là Truffle Box. 
‘https://truffleframework.com/boxes’ 
Truy cập đến địa chỉ này, bạn có thể thấy các template khác nhau..
 Ví dụ, nếu bạn muốn phát triển BApp bằng Angular hoặc React, bạn có thể tải template phù hợp. 
Tuy nhiên, các mẫu template tải xuống ở đây chuyên về Ethereum App, vì thế, bạn phải tải xuống và xóa các phần bên trong.
Và bạn phải thiết lập cho Klaytn. 
Việc này không khó khăn lắm. Tôi đã tải template webpack trước  
và thay đổi nó theo 'kiểu Klaytn' cho phù hợp với bài giảng của chúng tôi.
 Tôi đã tải nó lên Github để bạn có thể tải xuống. 
Thông tin thêm, chúng ta sẽ thao tác với JavaScript native và JQuery.
Ngay cả khi bạn chưa biết nó, bạn vẫn có thể dễ dàng theo dõi. 
 
Mở PowerShell và chạy lệnh clone git  'https://github.com/kkagill/addition-game-starter.git' tại vị trí bạn muốn tải xuống. 
Tôi đã tải tất cả xuống. 
Gõ 'Cd addition-game-starter' và enter. Hãy nhìn vào cấu trúc này bằng cách gõ ‘Code.' Đây chính là cách bạn mở nó bằng Visual Studio.
Hãy để tôi bắt đầu từ trên trước. 
Folder Contracts là nơi bạn cất giữ các file contract solidity.
Chúng ta đã có file 'Addition Game'tạo trước và một contract “migrations” ở dưới sẽ cho phép bạn chạy các file script trong folder “migration” bên dưới. Đây là một file quan trọng để deploy smart contract, vì vậy bạn đừng xóa nó nhé.
 
Tiếp theo, các file script trong folder migrations chứa logic dùng để lập trình.  
Nhìn vào file này bạn sẽ thấy, nó sẽ nhập file contract “migrations” và deploy nội dung đến node Klaytn. 
Trong thư mục src, tôi đã thiết lập cấu trúc gồm front-end của BApp. File index.html sẽ quản lý về “view” hiển thị ở Front. 
Tôi đã tải jquery hoặc bootstrap được sử dụng trong BApp với cdn và tôi thêm trước phần css bên dưới.
 
File Index.js giống như một động cơ, nó thực thi các hàm. 
Chúng tôi đã đặt tên cho các hàm sẽ được viết trong tương lai.
Biến ở dưới là các biến cấu hình hiển thị spinner khi tải. Đây không phải là phần quan trọng, vì vậy tôi đã thêm nó trước. 
Package.json là nơi bạn thêm các dependencies cần thiết thông qua npm. 
Điều quan trọng là bạn sẽ tải xuống file thư library cho phép bạn tương tác với caver-js, blockchain Klaytn.
Nó tương tự như web3 js của Ethereum. 
Nhiệm vụ của Truffle.js là thiết lập môi trường làm việc.
Thông qua truffle, bạn sẽ xác định mạng lưới nào phù hợp để deploy smart contract.  
Tôi sẽ trình bày nội dung này trong bài giảng tiếp theo. 
Webpack tối ưu hóa các file và phát hiện bất cứ khi nào có thay đổi về code và phản ánh các thay đổi cho trình duyệt mà không phải tải lại trang. 
Đến giờ, tôi đã tải xong và giải thích cho các bạn về template để tạo ra trò chơi Klaytn trên Bapp.
 

## 5.3 Deploying smart contract to Baobab 1
 
Chúng ta hãy deploy hợp đồng thông minh AdditionGame mà chúng ta đã tạo trên testnet baobab. Trước khi bắt đầu, chúng ta sẽ chạy lệnh npm install trong terminal và cài đặt các dependencies cần thiết cho BApp. 
Nếu bạn không thấy terminal bên dưới, hãy chọn new terminal trên tab Terminal. 
Bây giờ hãy chạy lệnh npm install. 
Nó sẽ tốn chút thời gian. Khi kết thúc, thư mục có tên 'node_modules' sẽ được tạo và cài đặt dependency hoàn tất. Tải về sẽ tốn một ít thời gian. 
 
Đầu tiên, hãy tạo một file mới trong thư mục migrations.
 Nhấp chuột phải vào thư mục 'migrations' và chọn New File. Đặt tên là '2_deploy_contuces.js' và chúng tôi sẽ thêm logic để deploy hợp đồng AdditionGame đến node.
 
Truy cập ‘Initial migrations’, copy và paste toàn bộ code. 
Hãy đổi nó thành 'importing the AdditionGame contract'. 
Thay thế phần sẽ được deploy với 'AdditionGame'. Cho đến nay, logic cơ bản để triển khai đã kết thúc.
Tuy nhiên, tôi sẽ viết code vào một số file trong BApp để lưu trữ thông tin tôi nhận được từ quá trình triển khai. Sau này, các thông tin đó sẽ hữu ích để tạo các trường hợp contract.
 
Deployer deploy contract AdditionGame và qua lệnh 'then' chúng tôi nhận được dữ liệu json.
Và trong này,
 
if (AdditionGame._json) {
 
Nếu bạn đã nhận được dữ liệu json của Additions game, bạn sẽ lưu nó vào một file thông qua hệ thống module. 
Để làm được điều đó, bạn phải nhập nó trước. 
Thêm ‘const fs = require ('fs') lên trên cùng.  
Sau đó, tôi sẽ tạo hai file. Đây là các file dùng để lưu Abi và địa chỉ contract. Nhấp chuột phải vào bất cứ đâu trên màn hình và đặt tên cho file mới là ‘deployedABI’. 
Tạo ra một file mới với tên là ‘deployedAddress’. 
Bây giờ, chúng ta sẽ sử dụng hệ thống file để lưu trữ từng file mới này. 
Đầu tiên, hãy tạo một đoạn code để lưu trữ thông tin abi.
 Abi là nội dung có thể tương tác giữa blockchain và contract.
  	fs.writeFile('deployedABI',JSON.stringify(AdditionGame._json.abi),
 
Có một hàm writefile trong hệ thống file. Xác định file nào cần viết và xâu chuỗi thông tin abi mà chúng tôi đã nhận được từ json và chuyển nó đến một đối số. Cuối cùng, chúng tôi sẽ xử lý lỗi.
 
    	(err) => {
      	if (err) throw err
      	console.log("파일에 ABI 입력 성공");
    	})
Nếu có lỗi xảy ra thì hãy "throw" nó. Nếu không có, hãy viết log vào chỗ console. Việc này sẽ lưu thông tin abi của contract đã deploy trong file deployABI. Để tiếp tục, tôi sẽ lưu lại địa chỉ của contract đã deploy vào file.
fs.writeFile('deployedAddress',AdditionGame.address,(err) => {if (err) throw err console.log("파일에 주소 입력 성공");})

Nếu bạn đã thực hiện theo các bước trên, bây giờ chúng ta có thể lưu các thông tin vào các file sau mỗi lần deploy. Tôi sẽ tiếp tục thiết lập môi trường truffle.js và deploy nó trong bài giảng tiếp theo.
 
 
## 5.4 Deploying smart contract to Baobab 2
 
 
Cuối cùng, bạn cần thiết lập cài đặt. Bạn phải quyết định mạng nào bạn sẽ deploy. 
Truy cập Truffle.js. Tại đây, tôi sẽ làm ngay . Đầu tiên, tôi sẽ nhập library có tên là  connect-privkey-to-provider.const PrivateKeyConnector = require('connect-privkey-to-provider')
 
và tạo một hằng số là network ID. 
const NETWORK_ID = '1001'
 
1001 có nghĩa là ID của mạng lưới duy nhất trên Baobab.
const GASLIMIT = '20000000'
 
Đây là gas limit để triển khai. Có bảy số 0.
const URL = https://api.baobab.klaytn.net:8651
 
Đối với UR, tôi đã chỉ định địa chỉ nơi Klaytn đang khởi chạy full node, đó là testnet baobab. Cuối cùng, chúng tôi cần một hằng số để giữ secret key, vì thế chúng tôi sẽ lất secret key của tài khoản chúng tôi đã tạo trước thông qua ví Klaytn. Tôi đã nhắc các bạn lưu secret key ở đâu đó. Tôi đang copy và paste key của tôi vào Notepad. 

const PRIVATE_KEY = ''
 
Bây giờ, hãy sử dụng các cài đặt này trong module.exports.
module.exports = {networks: {klaytn: {provider: new PrivateKeyConnector(PRIVATE_KEY, URL),network_id: NETWORK_ID,gas: GASLIMIT,gasPrice: null,}},}
 
Tôi sẽ giải thích cho bạn hiểu trước. Tôi đã đề cập rằng chúng tôi sẽ sử dụng network “Klaytn". Bây giờ, chúng tôi sẽ chỉ định 4 tuỳ chọn ở đây. Đầu tiên, bạn chọn một provider cung cấp node Klaytn. Tạo một PrivateKeyConnector và truyền 2 đối số. Đối số 1 để truyền secret key của tôi và đối số 2 để truyền địa chỉ network nơi full node đang chạy. Điều này cho phép tôi kết nối với mạng thử nghiệm baobab bằng secret key cuả tôi. 

Chỉ định ID network và gas, và cuối cùng phí gas đặt thành giá trị null. Vì mạng baobab sẽ tự động đặt phí gas nên chúng tôi truyền giá trị là null. Bây giờ tôi đã thiết lập môi trường để deploy smart contract. Nó khá đơn giản. Nào, cùng deploy thôi. Trong Terminal, chạy lệnh truffle deploy -network klaytn. Yes, đã deploy thành công. 

Nó khá đơn giản. Bây giờ hãy triển khai nó. Ở terminal, chạy 'truffle deploy-network klaytn'. Vâng, chỉ cần triển khai thành công. Bạn có thể thấy cụm từ xác nhận được hiển thị trong console..
 
 
 
Bây giờ, nếu bạn nhìn vào file deployedABI, thông tin abi đã được lưu. Đến file deployed address và lưu ý rằng địa chỉ của contract được deploy đã được lưu lại. Nó đang hoạt động tốt. Cuối cùng, khi bạn deploy, một thư mục tên build sẽ được tạo nên. Nó chứa thư mục contracts ở bên trong và 2 file json trong thư mục contract. Chúng được gọi là artifact. Mỗi file artifact chứa thông tin ABI của hợp đồng tương ứng cũng như các thông tin liên quan đến hợp đồng. 

AIB là cụm viết tắt tiếng Anh của  giao diện nhị phân ứng dụng; chúng tôi đã lưu trữ một file ABI đã deploy trong đó. Trong abi, chúng ta thấy các hàm và biến được viết ở định dạng json mà chúng ta sử dụng cho hợp đồng AdditionGame.

 
Nói một cách đơn giản, khi bạn deploy contract này lên blockchain, abi này đảm bảo hàm trong contarct và dữ liệu được trả về. Đó là nơi bạn xác định cách bạn có thể tương tác với hợp đồng. Nếu bạn kéo xuống dưới cùng, sẽ có một phần mạng lưới. 1001 là ID mạng duy nhất của Klaytn. Địa chỉ là địa chỉ contract đang được deploy đến testnet Baobab.

Cuối cùng, nếu bạn muốn deploy lại contract cho node Klaytn, bạn có thể sử dụng lệnh này. Ví dụ, khi chúng tôi cần sửa đổi contract, chúng tôi cần deploy lại nó cho node. 
 
truffle deploy –compile-all –reset –network klaytn
 
 
“Compile all" tất cả contract biên soạn lại. Việc thiết lập lại buộc các file script trong thư mục Migrations chạy lại. Chạy nó để deploy lại contract cho node một lần nữa. Vâng. Hoàn tất. Mở file deployedAddress và bạn sẽ thấy rằng địa chỉ đã thay đổi. Như vậy, tôi đã hoàn thành deploy Contract với network Klaytn Baobab bằng truffle. 
 
## 5.5 Account verification UI
 
 
Hãy bắt đầu bằng cách đăng nhập bằng tài khoản bạn đã tạo bằng ví baobab. 
Có 2 cách để chúng ta xác thực tài khoản. 
Đầu tiên, bạn có thể sử dụng kết hợp file keystore và mật khẩu; thứ hai, xác minh bằng private key. 
 Ở đây, chúng ta sẽ thực hiện cách thứ nhất là kết hợp file keystore và mật khẩu. 
Đầu tiên, tôi sẽ viết code html. 
Truy cập Index.html và thêm nội dung bên trong body tag.
  <div class="container">
    <div class="row">
  	<div class="col-md-8 col-md-offset-2">
    	<h1 class="text-center">클레이튼(Klaytn)</h1>
    	<h3 class="text-center">속전속결 덧셈 게임</h1>
    	<h3 class="text-center">
      	<code>3초안에 맞출 시 0.1 KLAY 지급 이벤트</code> 
      	<button type="button"
              	class="btn btn-info pull-right"
              	id="login"
              	data-toggle="modal"
              	data-target="#loginModal">
              	로그인
      	</button>
      	<button type="button"
              	class="btn btn-info pull-right"
              	id="logout"
    	          style="display: none;"
              	onclick="App.handleLogout()">
              	로그아웃
      	</button>
    	</h3>        
    	<hr />
  	</div>
	</div>
  </div> 
 
 
 
Hãy tạm dừng video này ngay bây giờ và viết code này. 
Thiết lập rất đơn giản. 
Thuộc tính class ở trong thẻ div sử dụng bootstrapping để giúp UI trông đẹp hơn.
Tôi sẽ bỏ qua phần mô tả bootstrap.
Trước hết, tôi đặt các cụm từ giải thích lên trên.  
Dưới đây tôi đã thêm các nút đăng nhập và đăng xuất. 
Khi tôi nhấp vào nút đăng nhập, nó sẽ khởi động cửa sổ modal. 
Khi tôi nhấp vào nút đăng xuất  hàm The handleLogout sẽ được thực thi. 
Lưu ý rằng tôi đặt nút đăng xuất không xuất hiện trong css. 
Hãy chạy app và kiểm tra xem code có đang hoạt động đúng không nhé! 
Chạy lệnh npm run dev trong terminal. 
Mở Chrome và truy cập địa chỉ localhost:8081. 
Vâng, nhìn nó không đẹp lắm, nhưng view có vẻ ổn. 
Bây giờ, hãy tạo một modal để nó mở ra khi chúng ta nhấp vào nút đăng nhập. ‘https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals” 
Nếu bạn truy cập đến trang bootstrap này, bạn có thể lấy được code modal. 
Sao chép phần này và quay về file html. 
Tôi sẽ dán nó bên ngoài container thẻ div. 
Bây giờ hãy thay đổi nội dung của modal này. 
Đầu tiên, đặt div id = loginModal.

  <div class="modal fade" tabindex="-1" role="dialog" id="loginModal">
 
Bạn nên làm như thế, vì nó cho phép modal mở ra khi bạn nhấp vào nút login. 
Nó khớp modal với giá trị data-target của nút đăng nhập ở trên. 
Tiếp theo, chúng ta sẽ  làm cho kích thước modal nhỏ lại . Xoá toàn bộ phần modal header. \
 
  <div class="modal-dialog modal-sm">
 
Và xoá nội dung bên trong body modal. 
Bây giờ, thêm phần để tải file keystore và nhập mật khẩu.
Keystore  
Cài dạng input là file và để hàm handleimport được gọi trên event onchange. Và phần dưới, thêm vào phần cho mật khẩu. 
 
Copy và paste ở đây, và đổi tên.
 
Nếu giá trị được ghi trong cửa sổ nhập mật khẩu, gọi hàm handlePassword.
Và tôi đã thêm phần để hiển thị thông báo khi xác minh thành công hoặc xảy ra lỗi. 
Cuối cùng, đổi close thành 닫기 và đổi 'save changes' thành 제출. 
 
Thêm thuộc tính id và cho phép gọi hàm handleLogin hiển thị khi nhấp vào. 
Vâng, bây giờ tôi sẽ kiểm tra giao diện để xem code vừa hoàn thành có hoạt động tốt không. 
Nhấp vào nút đăng nhập. Modal đã hiện ra với các tuỳ chọn là chọn tải lên một file và nhập mật khẩu vào. Như vậy, tôi đã hoàn thành hướng dẫn thiết kế UI cho xác thực tài khoản. 
 

## 5.6 Account verification logic (keystore validation)
 
Chúng ta đã hoàn thành phần thiết kế UI, bây giờ hãy đưa logic vào để nó hoạt động được.
Trong file Index.js, có nhiều hàm trong hằng constant gọi là App. 
Và khi bạn kéo xuống dưới, điều đầu tiên bạn sẽ thấy đó là khi tải trang, một hàm start đang hiển thị trong constant app. 
Vì vậy, chúng ta sẽ đưa hàm start vào, nhưng trước tiên, chúng ta cần tải thư viện caver.js để tương tác với blockchain Klaytn và khởi tạo nó để dùng cho BApp. Kéo lên trên cùng, import Caver from "caver-js";
 
và tạo một constant cho cài đặt môi trường. 
 
const config = {
  rpcURL: 'https://api.baobab.klaytn.net:8651'
}
 
Có một rpcURL trong config.
Chúng ta đã xác định node Klaytn nào được chọn để kết nối và sử dụng. 
Tôi đã chọn mạng thử nghiệm baobab. 
Cuối cùng, chúng ta sẽ tạo hằng số khởi tạo rpcURL bằng cách pass nó đến tạo hàm Caver.
const cav = new Caver(config.rpcURL);
 
 
Việc khởi tạo đã kết thúc và hằng số cav này hiện có sẵn trong App.
Bây giờ bạn cần khởi động hàm. Nhưng, trước hết, trong hàm start, bạn cần kiểm tra xem tài khoản đã được xác thực qua session hay chưa. Tuy nhiên, tôi sẽ làm phần này sau vì session sẽ được trình bày trong bài giảng tiếp theo. Vì thế, tôi sẽ để trống hàm start. 
Trước tiên, hãy thực hiện hàm handleImport.
Chúng ta có thể nhấp vào nút đăng nhập và chọn file keystore sau khi pop-up modal hiện ra. 
Tuy nhiên, file này phải được xác thực cho dù nó khả dụng hay không. 
Chúng ta hãy làm việc này trong hàm handleimport. 
Trước hết, chúng ta tạo một hằng const fileReader = new FileReader() 
 
 
và dùng hàm readAsText để đọc file được chọn. 
fileReader.readAsText(event.target.files[0]);
 
 
phần này ý chỉ file chúng ta đã chọn. Khi quá trình thực thi readAsText hoàn tất, onload event của FileReader sẽ xuất hiện. fileReader.onload = (event) => {

event nhận được bởi lệnh gọi lại, nói cách khác, nội dung bây giờ của file có thể được dùng trong khối code này. Nội dung của file này sẽ được kiểm tra xem nó có phải là file keystore khả dụng hay không. 

 Đầu tiên, thêm một try catch block vào. 
try {
} catch (event) {
}
 
Bây giờ chúng ta sẽ kiểm tra bằng câu nếu thì, nếu nội dung của file là khả dụng hay không, nói cách khác, nếu đó đúng là một file keystore. 
if (!this.checkValidKeystore(event.target.result)) {
}
 
Tôi đã chuyển nội dung của file chúng ta đã đọc qua hàm checkValidKeystore như một đối số.
Bây giờ hãy thêm nội dung cho hàm checkValidKeystore. 
Hàm này lấy keystore làm đối số và nhận file. 
Và file keystore tôi nhận được là file json. 
Tôi sẽ thay đổi nó thành Javascript object để sử dụng các thuộc tính trong file json này làm biến.
	const parsedKeystore = JSON.parse(keystore);
 
Tôi dùng hàm json parse để phân tích nội dung của file keystore, chuyển nó thành một object và lưu nó trong một hằng. Chúng ta nên làm gì tiếp theo? 

Hãy đảm bảo rằng các thuộc tính cần cho định dạng file keystore của bạn đã được nhập hoàn chỉnh. Hãy nhìn vào file keystore và xem chúng ta cần những gì. Các yếu tố cần thiết cho định dạng keystore là version, id, address, và crypto. Nếu thiếu 4 trường này, file keystore sẽ không khả dụng. Vì thế, tôi sẽ kiểm tra nó bằng code. 

const isValidKeystore = parsedKeystore.version &&

parsedKeystore.id &&
  	
parsedKeystore.address &&
  	
parsedKeystore.crypto;
 
 
Cuối cùng, return hằng này. 

return isValidKeystore;
 
 
Tôi kéo lại lên trên và xác nhận xem file tôi vừa import có phải là một file keystore khả dụng hay không. Nếu không, message sẽ hiển thị không khả dụng dụng và kết thúc hàm. $('#message').text('유효하지 않은 keystore 파일입니다.'); return;
 
Nếu tôi xác thực thành công, tôi sẽ lưu file keystore vào một biến toàn cục. Trước tiên, chúng ta cần tạo một biến toàn cục. Tạo hàm “Auth" trên hàm Start. 
 
auth: { accessType: 'keystore', keystore: '', password: '' },
 
Có ba trường trong object Auth.
accessType là một phương thức xác thực, chứa một dạng keystore và một dạng private key.
Chúng ta đang thao tác với dạng keystore. 
Cuối cùng, password là trường chứa mật khẩu sẽ được kết hợp với file keystore.
Nếu chúng ta quay lại hàm và vượt qua bước xác nhận, this.auth.keystore = event.target.result;
 
gửi toàn bộ nội dung của file được tải đến trường keystore của biến auth chúng ta đã tạo ra. Sau đó, gửi đi thông báo rằng tôi đã thành công. 

$('#message').text('keystore 통과. 비밀번호를 입력하세요.');
 
Cho phép gõ mật khẩu trong trường password ngay lập tức. document.querySelector('#input-password').focus();
 
Cuối cùng, khi đọc file, nếu có bất kì lỗi nào, gửi đi thông báo trong block catch và kết thúc hàm. 

Copy $('#message').text('유효하지 않은 keystore 파일입니다.'); 
return;
 
Vâng, hàm Handleimport đã được triển khai. Hãy kiểm tra lại xem. 

Nhấp vào nút đăng nhập và chọn file keystore. Ô điền mật khẩu sẽ hiện ra và trỏ chuột sẽ đặt sẵn trong đó để bạn điền mật khẩu. Để kiểm tra trường hợp đối lập, hãy chọn tải lên một file ngẫu nhiên. Ok, thông báo lỗi đã hiện ra. Nó vẫn hoạt động tốt. 

Bây giờ, hãy tạo một hàm để lưu mật khẩu vào một biến toàn cục khi chúng ta nhâp mật khẩu. Việc này sẽ rất đơn giản thôi. Nếu bạn di chuyển đến html, hàm handlepassword sẽ được gọi khi bạn nhập mật khẩu vào. Sau đó, tại hàm handlepassword, this.auth.password = event.target.value;

Lấy giá trị mật khẩu qua event onchange trong html, sau đó, gán nó vào trường password của biến auth toàn cục. Đơn giản như vậy thôi. Như vậy tôi đã hoàn thành bài giảng xác thực file keystore. Trong bài giảng tiếp theo, tôi sẽ tạo một secret key và thêm thông tin tài khoản vào ví.
 
## 5.7 Account verification (integrate wallet)

Chúng ta đã hoàn thành phần lấy file keystore và điền mật khẩu. Bây giờ, chúng ta sẽ kiểm tra xem tài khoản được xác thực thành công hay không khi gửi thông tin đến node baobab nhé.

Trước hết, tôi sẽ thay thế http trong rpcURL thành https. 
Hãy xem Index.html. 
Khi tôi nhấp vào nút submit, nó gọi hàm handlelogin. 
Vì vậy, hãy thực hiện hàm. 
Đầu tiên, hãy đảm bảo rằng accesstype là một keystore.
if (this.auth.accessType === 'keystore') { }

Lý do tôi viết câu lệnh “if" là vì khi xác thực một tài khoản, chúng ta có thể sử dụng keystore hoặc private key. Tuy nhiên, bây giờ chúng ta chỉ dùng keystore thôi. Nên tôi sẽ thêm câu lệnh “if" vào để khi bạn muốn xác thực bằng private key thì bạn vẫn có thể làm được. Hãy thêm try catch vào ngay bên dưới.

try {       
} catch (e)}

Đã đến lúc sử dụng instance caver.
Tôi sẽ đặt một câu hỏi cho bạn. 
Chúng ta có thể thu về được gì từ sự kết hợp giữa tệp keystore và mật khẩu? 
Nếu để ý thì bạn sẽ biết câu trả lời ngay. Vâng, bạn có thể lấy được private key. Secret key này sẽ cho phép bạn tạo ra một instance Wallet. 
Vì vậy, điều đầu tiên bạn cần làm là lấy secret key (khóa bí mật) thông qua tập keystore file và password. 
const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;

Bạn có thể dùng hàm decrypt thông qua tài khoản thành viên của instance caver. Mục đích là để mã hoá. Nếu bạn mã hoá nó, bạn có thể trở về object tài khoản đã mã hoá bằng cách truyền nội dung của file keystore và password như những đối số. Có nhiều thành viên trong object, và trong đó, chúng ta sẽ lấy private key và lưu vào constant. Nếu có lỗi trong quá trình mã hoá, thông báo sẽ được hiện ra. 
Copy và paste dòng ở trên, chỉ thay đổi nội dung 

$('#message').text('비밀번호가 일치하지 않습니다.');
$(‘#message’).text(‘password is not matched.’);
 
Nếu không có lỗi, nó sẽ tạo một instance Wallet từ secret key của bạn. 
 
this.integrateWallet(privateKey);

Truyền private key đến hàm integratewallet. Bây giờ, hãy đi đến hàm integratewallet. Tại đây, chúng ta thêm code đã lấy được từ instance Wallet bằng cách sử dụng private key. 
 
const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);
 
walletinstance chứa thông tin tài khoản của tôi. Sau đó thêm instance này vào wallet của tôi.
cav.klay.accounts.wallet.add(walletInstance)
 
Nếu bạn thêm account vào caver wallet, bạn có thể dễ dàng gọi lại thông tin account bằng instance caver khi bạn thực hiện một giao dịch trong tương lai. 

Bước tiếp theo là lưu trữ instance ví trong session lưu trữ. 
Bước tiếp theo là lưu instance Wallet vào session storage. Session storage sẽ lưu instance Wallet trên trình duyệt web cho đến khi đóng tab hoặc tắt trình duyệt. 
sessionStorage.setItem('walletInstance', JSON.stringify(walletInstance))

SetItem sẽ nhận cặp tham số giá trị key. Tham số thứ nhất là key và tham số thứ hai là giá trị. Vì thế, tôi sẽ cần phải tải thông tin tài khoản vào session sau. Khi bạn gọi walletInstance với một gía trị key, giá trị được lưu trong cặp tham số sẽ tự động tải. 

Lý do sử dụng sessionStorage là để giữ cho tài khoản được đăng nhập. 
Vì tài khoản được lưu trong caver wallet sẽ biến mất sau khi tôi chuyển sang một site khác hoặc làm mới trang. 
Tuy nhiên, nếu bạn lưu vào session storage, thông tin của bạn sẽ được lưu lại mặc cho bạn chuyển sang site khác một lúc rồi quay trở lại hay làm mới trang. Vì thế, sau đó tôi sẽ triển khai một session instance Wallet trong hàm start và giữ trạng thái đăng nhập cho tài khoản. Ngay lúc này, tôi cần cập nhật UI. 
Chúng ta đã hoàn thành xác thực tài khoản qua integrateWallet, chúng ta cần thay đổi UI cho phù hợp. 

this.changeUI(walletInstance);  

Tôi đang gửi một instance Wallet tới hàm ChangeUI . 
Vậy chúng ta nên làm gì với hàm ChangeUI? Chúng ta sẽ chuyển đến hàm changeUI. 
Đóng modal lại.
$('#loginModal').modal('hide');
 

và ẩn nút đăng nhập.
$("#login").hide();
 
Thay đổi nút logout bạn đã ẩn trước đó luôn. 
 
$('#logout').show();

Vì đã đăng nhập tài khoản rồi nên tôi muốn hiển thị địa chỉ ví. 
$('#address').append('<br>' + '<p>' + '내 계정 주소: ' + walletInstance.address + '</p>');   
 

Code này cho tôi biết rằng nó đã hiển thị địa chỉ tài khoản trong html nơi thuộc tính id là địa chỉ. Tôi sẽ đến index.html và thêm một thẻ div. Thẻ này được thêm ở dưới tag h3. 
Vâng, bạn có thể nhìn thấy địa chỉ tài khoản của tôi tại vị trí này. Giờ hãy thử kiểm tra xem. 

Nhấp vào nút Đăng nhập và mở file keystore. 
Nếu bạn nhập mật khẩu và nhấn nút gửi, tài khoản của bạn sẽ được xác minh và nút đăng xuất sẽ hiện ra. 
Phía dưới chính là địa chỉ tài khoản của tôi. Cuối cùng, hãy thực thi hàm để log out. 
Dưới đây bạn có thể thấy địa chỉ tài khoản của tôi. 
Đến Index.html. 
Lưu ý rằng khi tôi nhấp vào nút đăng xuất, tôi gọi hàm handlelogout. 
Tại đây, chúng ta sẽ gọi hàm removeWallet. this.removeWallet();


Chúng ta sẽ xóa địa chỉ ví và xóa sessionstorage bằng hàm này. 

Đến hàm removeWallet và thêm code này vào.
cav.klay.accounts.wallet.clear();
 
Đây là công đoạn xoá instance Wallet của tôi chứa các thông tin tài khoản đã được thêm vào ví. Sau đó, xoá session đi. 
 
sessionStorage.removeItem('walletInstance');

Khi bạn xóa nó, chỉ cần nhập giá trị key. Cuối cùng, nó gọi hàm reset và kết thúc. 

this.reset();
 
hàm reset này chỉ đơn giản là khởi tạo biến toàn cục auth. 
Truy cập hàm reset và khởi tạo biến auth.
this.auth = {
keystore: '',
password: ''
};

Ngoài ra còn có một accesstype trong Auth. Nhưng, bạn không phải xóa accesstype vì dù sao nó cũng là một keystore. 
Thay vào đó, khi chúng ta đăng nhập, một giá trị sẽ được nhập vào keystore và mật khẩu. 
Tôi muốn đăng xuất và xóa nó một cách an toàn. 
Quay trở lại hàm handleLogout, viết code làm mới trang và hoàn thành nó. 
Lý do cho việc làm mới trang là để nó trở về giao diện người dùng trạng thái ban đầu.
location.reload();
 

Bây giờ hãy kiểm tra và kết thúc công đoạn này. 
Nhấp vào nút Đăng xuất, thông tin tài khoản sẽ biến mất và bạn được đưa trở lại màn hình khởi tạo bằng cách làm mới trang. 
Như vậy bạn đã thêm logic xác thực tài khoản thành công. Hãy tiếp tục đến với bước lưu xác thực tài khoản trên session storage trong bài giảng tiếp theo. 
 
 
## 5.8 Account Session

Điều gì sẽ xảy ra khi chúng ta đăng nhập và làm mới trang? 
Nhấp vào nút đăng nhập và chọn file keystore. Điền mật khẩu vào. Bấm nút submit. Tôi đã đăng nhập thành công.  
Ở bước này, bấm F5 để làm mới trang. 
Trang sẽ được reset.
Sẽ thật tốt nếu tài khoản vẫn trong trạng thái đã đăng nhập.
Làm thế nào để tôi làm điều đó? 
Nếu chúng ta đăng nhập thành công, tài khoản sẽ được lưu trong session storage. Tôi sẽ làm như vậy ngay. 
Hàm đầu tiên được tải khi chạy BApp là hàm start. Ở đây tôi lấy thông tin tài khoản đã được lưu trong session storage. Hãy đến hàm start,

const walletFromSession = sessionStorage.getItem('walletInstance');
 
Nếu bạn sử dụng getItem và truyền giá trị của key, giá trị đó sẽ được tìm nạp và lưu trữ trong constant. 
Tôi đã lưu instance Wallet của tôi. 
Tiếp theo, hãy đảm bảo hằng số WalletFromSession chứa giá trị.
if (walletFromSession) {
try {
} catch (e) {
}
Thêm lại thông tin tài khoản vào caver wallet. cav.klay.accounts.wallet.add(JSON.parse(walletFromSession));

Khi trang được làm mới hoặc bạn truy cập lại trang, thông tin tài khoản đã được thêm vào Ví sẽ bị xóa, vì vậy tôi thêm nó trở lại qua session này. 

Cập nhật giao diện người dùng (UI) để hiển thị rằng bạn đã đăng nhập.
this.changeUI(JSON.parse(walletFromSession));
UI sẽ hiển thị một nút đăng xuất và địa chỉ tài khoản của bạn.  
Cuối cùng, khi giá trị trong sessionStorage không phải là instance Wallet hợp lệ, nó sẽ chuyển đến câu lệnh catch. 
Hãy xoá walletinstance trong session storage. 
sessionStorage.removeItem('walletInstance');
 
Vậy là xong. Bây giờ hãy kiểm tra lại. Khi bạn tải lại trang, tài khoản vẫn được đăng nhập mà không trở về trạng thái khởi tạo. 
Như vậy, chúng ta đã hoàn thành một phần của công đoạn duy trì xác minh tài khoản.

## 5.9 KLAY transfer via contract (deposit)
 
Bây giờ tôi sẽ gửi KLAY đến contract đang sử dụng. 
Đầu tiên, hãy tạo một giao diện người dùng (UI). 
Bạn có thể tạo nó dưới hàng class div.
 
<br />     
 
    <div class="row text-center">
      <div class="col-md-2 col-md-offset-5">
        <div id="owner" style="display: none;">
          <hr />
          <label>컨트랙에 KLAY 보내기</label>
          <div class="input-group">             
            <input type="number" class="form-control" id="amount" />
            <span class="input-group-btn">
              <button type="button" class="btn btn-default" onclick="App.deposit()">송금</button>
            </span>
          </div>
        </div>
      </div>       
    </div>
 

Vui lòng bấm dừng video và thực hiện thao tác này.
Tôi sẽ giải thích ngắn gọn. 
Tôi đã thiết lập phần UI để gửi tiền vào hợp đồng thông qua css. 
Chúng tôi cũng đã thiết lập hàm deposit để nó khởi chạy khi tôi nhập vào số lượng và nhấn nút chuyển tiền.
Bây giờ hãy đến hàm deposit và thực hiện nó. 
 
Tôi sẽ giải thích cách thực hiện trước.
Chuyển Klay sang hợp đồng chỉ có thể được thực hiện với tài khoản chủ sở hữu. 
Việc chuyển Klay đi chỉ có thể được thực hiện bởi chủ của contract. 
Nói cách khác, chỉ có người tạo ra event này là được quyền chuyển tiền. Nếu chúng ta đang sử dụng tài khoản chủ sở hữu, chúng ta sẽ truy cập hàm deposit trong hợp đồng và chuyển khoản KLAY.  
Quy trình rất đơn giản. 
Đầu tiên, chúng ta sẽ tạo hàm instance để chúng ta có thể truy cập vào hợp đồng mà chúng ta đã deploy. 
Khi tạo một instance contract, bạn cần abi và địa chỉ của contract đã deploy. Dưới hằng cav ở phía trên, 
const agContract = new cav.klay.Contract(DEPLOYED_ABI, DEPLOYED_ADDRESS);

deployed_abi và deployed_address là các hằng số toàn cục có thể được sử dụng trong BApp. 
Khi deploy contract, chúng ta lưu thông tin vào file deployedabi và file deployedaddreess. 
Cài nó vào trong webpack thì chúng ta có thể đọc được thông tin này và sử dụng nó như một hằng toàn cục.
Nhấp vào file Webpack.config.js, bạn sẽ thấy phần chú thích ở đây. Hãy giải chúng. 
 
Nói một cách đơn giản, chúng ta đọc file deployedaddres và gán địa chỉ hợp đồng cho hằng số toàn cục. 
Theo cách tương tự, chúng ta lưu trữ thông tin abi trong các hằng số toàn cục có trong file deployedabi. 
Hãy trở lại file Index.js.
 
Vì vậy, hãy nhớ rằng cả thông tin abi và địa chỉ được gửi cho người tạo ra instance contract chuyển qua các hằng số toàn cục được tạo bởi webpack.  
Bây giờ chúng ta đã tạo một instance 4 contract, chúng ta sẽ tiếp tục với hàm deposit. 
Có một điều chúng ta phải kiểm tra trước khi gửi tiền.
Bạn nên xác minh rằng tài khoản bạn vừa đăng nhập là tài khoản chủ sở hữu. 
Vì vậy, tôi phải đưa ra hai mẫu thông tin. 
Đầu tiên, tôi đang truy xuất thông tin tài khoản hiện đang đăng nhập.
Thứ hai, tôi sẽ lấy biến trạng thái chủ sở hữu được lưu trong contract. 
Đầu tiên, tôi sẽ lấy thông tin đăng nhập của tôi.
const walletInstance = this.getWallet();

Chuyển đến hàm getwallet và nhận thông tin tài khoản tồn tại trong ví caver đang có.
if (cav.klay.accounts.wallet.length) {
      return cav.klay.accounts.wallet[0];
    }

Wallet [0] là tài khoản đầu tiên được thêm vào Wallet, tài khoản tôi hiện đang đăng nhập. 
Bạn đã hoàn thành xong hàm.  
Tiếp theo, hãy gọi giá trị của biến trạng thái của chủ sở hữu trong hợp đồng. 
Truy cập hàm callOwner return await agContract.methods.owner().call();
 
Chúng ta sẽ truy cập hàm chủ sở hữu thông qua instance contract additiongame mà chúng ta đã tạo và gọi giá trị. 

Sử dụng await keyword để nhận các giá trị không đồng bộ. 
Vì chúng ta đã tạo các nội dung cần thiết trước khi gửi tiền đi, chúng ta sẽ tiếp tục với hàm deposit.
if (walletInstance) {
 
}

Nếu một instance wallet tồn tại thông qua hàm getwallet, 
so sánh địa chỉ tài khoản đã đăng nhập hiện tại với địa chỉ tài khoản của chủ sở hữu được trả lại từ contract.
if (await this.callOwner() !== walletInstance.address) return; 

Nếu chúng ta so sánh chúng, nhưng chúng là các giá trị khác nhau, chúng ta không thể tiến hành nữa và chúng ta chấm dứt hàm.
Nếu nó giống nhau else {}
 
Nhận giá trị đầu vào Html var amount = $('#amount').val();

nếu giá trị đầu vào tồn tại if (amount) {}
 
Gửi giá trị cho hàm deposit bằng cách sử dụng một instance contract.
 
agContract.methods.deposit().send({
 })

Ở đây chúng tôi gửi một đối tượng giao dịch như là một hệ số gửi.
Chúng ta cần xác định ba điều. 
Đầu tiên chúng ta phải xác định ai đang gọi hàm này.
from: walletInstance.address,
 
Tôi đã nói rằng chúng ta sẽ gọi hàm này bằng tài khoản hiện đang đăng nhập.
Lưu ý rằng địa chỉ của Walletinstance là tài khoản đã được xác minh và nó có quyền tạo chữ ký trong giao dịch.
Vì vậy, tôi có thể đặt bất kỳ địa chỉ nào trong ‘from'. 
Chỉ các địa chỉ đã được xác minh trong BApp có thể được sử dụng làm giá trị. 
Và đặt phí gas là 250.000.
 
gas: '250000',
 

Vì hàm deposit trong hợp đồng có thể thanh khoản, bạn phải thông qua trường giá trị.
value:

Chúng ta phải chuyển đổi số nhận được từ đầu vào html sang peb là đơn vị tối thiểu của KLAY. 
Chuyển đổi nó bằng cách sử dụng utility của thư viện caver.
cav.utils.toPeb(amount, "KLAY")

Bây giờ bạn có thể gửi tiền với hàm deposit trong hợp đồng. 
Nhưng tôi có thể sử dụng thông tin có thể được nhận không đồng bộ, thay vì kết thúc giao dịch như thế này.
.once('transactionHash', (txHash) => {
    console.log(`txHash: ${txHash}`);
})
 

Đầu tiên, tôi có thể có được hàm băm giao dịch và tôi đã hiển thị ở console. 
Lưu ý rằng log wrapper trong console không phải là dấu ngoặc kép đơn, mà là dấu ngoặc kép ở bên trái của số 1. 
Hãy cẩn thận. 
Tiếp theo, bạn có thể nhận được một biên lai.
.once('receipt', (receipt) => {
   console.log(`(#${receipt.blockNumber})`, receipt);          
})

Nhận biên lai này có nghĩa rằng giao dịch thành công đã được thêm vào block.
Vì vậy, bạn có thể kiểm tra biên lai để xem Block, nơi mà giao dịch được thêm vào.
Nếu giao dịch có lỗi, bạn sẽ nhìn thấy lỗi
.once('error', (error) => {
   alert(error.message);
  }); 
 

Nếu có lỗi, thông báo sẽ được hiển thị. 
Tôi đã thực hiện logic để kiểm tra thành công sau khi gửi giao dịch. 
Cuối cùng, nếu không có số tiền nhận được ở đầu vào html, hãy thêm câu lệnh return kết thúc hàm.
return;
 

Tôi đã hoàn thành phần gửi KLAY cho hàm deposit của hợp đồng và tôi sẽ thay đổi UI và kiểm tra nó trong phần tiếp theo. 
 
 
## 5.10 KLAY transfer via contract (UI change and testing)
 
Tôi sẽ thử thay đổi UI và thử nghiệm. 
Khi chúng ta gửi KLAY đến hàm deposit ở bài trước và nhận được biên lai, giao dịch đã thành công. 
Tôi nên làm gì sau khi thành công? 
Sẽ thật tuyệt nếu hệ thống có thể hiển thị cho tôi tin nhắn nhắc nhở.
   alert(amount + " KLAY를 컨트랙에 송금했습니다.");  
 
Và tôi sẽ làm mới trang để xem số dư của contract.
   location.reload();     
.

Tôi đã nói rằng tôi sẽ làm cho số dư của hợp đồng được hiển thị. 
Hãy nhớ rằng chúng ta đã tạo một hàm sẽ tải số dư của contract khi chúng ta viết smart contract. 
Chúng ta sẽ gọi hàm getBalance để có thể thấy số dư của hợp đồng. 
Trước tiên, chúng ta sẽ thêm div hiển thị số dư của hợp đồng trong html. 
Truy cập Index.html và thêm div dưới địa chỉ hiển thị địa chỉ tài khoản của tôi.
  <div class="text-center" id="contractBalance"></div>

Và sau đó chúng ta sẽ thấy số dư của hợp đồng ở đây. 
Bây giờ, chế độ xem đã sẵn sàng, hãy tạo một hàm để tải số dư từ backend. 
Đến hàm callcountractbalance và viết code.
return await agContract.methods.getBalance().call();
 

Phần truy cập hàm getbalance thông qua instance contract và tải giá trị. Vâng, nó thật đơn giản. 
Từ đâu tôi gọi hàm callcountractbalance? 
Tôi nên gọi nó ở đâu? 
Nếu giao dịch thành công trong hàm deposit và nhận được biên nhận, nó sẽ làm mới trang thông qua location.reload (). 
Hàm nào được thực thi đầu tiên khi trang được làm mới? 
Hàm start được thực thi trước. 
Sau đó, chúng ta gọi hàm changeUI từ hàm start. 
Tôi cần thêm code để tải số dư contract từ hàm ChangeUI để thay đổi UI ngay lập tức.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(await this.callContractBalance(), "KLAY") + ' KLAY' + '</p>');     

Nó khá dài. 
Tôi sẽ giải thích.
Chúng ta sẽ thêm thông báo vào phần hiển thị số dư contract trong html. 
Gọi hàm callContractBalance để lấy số dư. 
Tuy nhiên, số dư được quy đổi sang đơn vị tối thiểu của KLAY là peb. 
Điều đó sẽ khiến bạn khó thấy được còn lại bao nhiêu, vì đơn vị này quá lớn. 
Vì vậy, utility caver có hàm gọi là fromPeb.
Nó là một hàm có thể chuyển đổi từ peb sang đơn vị khác. 
Tôi đã chỉ định trong tham số thứ hai để chuyển đổi sang KLAY. 
Kết quả là, nó cho thấy số dư hợp đồng được chuyển đổi thành KLAY trong html.
 

Cuối cùng, việc chuyển KLAY vào contract phải được thiết lập chỉ cho tài khoản chủ sở hữu. 
Bạn chỉ phải cấp quyền cho organizer của event. 
Vì vậy, tôi sẽ thay đổi nó để hiển thị UI chỉ có thể được chuyển khi tôi đăng nhập bằng tài khoản chủ sở hữu. Chuyển đến hàm changeUI
if (await this.callOwner() === walletInstance.address) {
      $("#owner").show(); 
    }     
 
Tôi đã đặt div chủ sở hữu hiển thị khi địa chỉ tài khoản chủ sở hữu và địa chỉ tài khoản đã đăng nhập giống nhau. 
Trong html, div chủ sở hữu được đặt ẩn theo mặc định.
Vì vậy, khi bạn đăng nhập bằng tài khoản chủ sở hữu, bạn sẽ thấy phần này.
Bây giờ hãy thử kiểm tra. 
Tôi sẽ tạo lại nó một lần. 
Trước tiên, hãy đảm bảo rằng secret key của tài khoản của bạn được nhập chính xác vào truffle.js. 
Tôi sẽ deploy lại từ terminal.
‘truffle deploy -compile-all -reset -network klaytn’ Tôi đang deploy lại nó cho những người chưa deploy. 
Việc deploy đã kết thúc. 
Hãy kiểm tra lại bằng cách chạy npm run dev. Nhấn F12 để mở cửa sổ giao diện console. 
Nhấp vào nút Đăng nhập
Vì bạn đã đăng nhập bằng tài khoản chủ sở hữu của mình, bạn có thể thấy phần bạn có thể gửi tiền. 
Hãy gửi tiền ngay bây giờ. Gửi 1 KLAY.
 
 

Bạn có thể thấy thông tin hàm băm và biên nhận thông qua log trên console khi giao dịch của bạn thành công. 
Tin nhắn thông báo hoạt động tốt. 
Có vẻ như thời gian cần thiết cho giao dịch là ít hơn 3 giây. 
Trong 3 giây này, có bốn quy trình từ tạo giao dịch đến tạo block và truyền nó tới mạng lưới khi giao dịch hoàn tất. 
So với các nền tảng blockchain khác, tốc độ xử lý rất nhanh. 
Nhấp vào tin nhắn thông báo, làm mới trang và hàm start được gọi đầu tiên, 
và số dư contract mới được hiển thị bởi hàm ChangeUI trong đó. 
Hàm transaction đang hoạt động tốt.
Tôi muốn có một công cụ tải spinner để kiểm tra giao dịch có hoạt động tốt hay không.
Đây không phải là yêu cầu bắt buộc, nhưng tôi gợi ý bạn nên thêm vào để cải thiện UI.
Đến Index.js và import spin.js ở trên đầu.
import {Spinner} from 'spin.js';

Đi đến hàm showspinner và trả về instance spinner.
var target = document.getElementById('spin');
    return new Spinner(opts).spin(target);

Gọi hàm này từ hàm deposit
var spinner = this.showSpinner();
 
Sau khi nhận biên lai, dừng spinner.
 
  spinner.stop();  

Cuối cùng thêm một div để hiển thị spinner trong html.<br /> dưới tag.
<div id="spin"></div>    
 

Bây giờ hãy thử kiểm tra. 
Vâng. Khi spinner xuất hiện, một kết quả tuyệt vời đang được tạo ra.
Hàm chuyển hoạt động tốt và giao diện người dùng được phản ánh tốt. 
Như vậy, tôi đã hoàn thành hướng dẫn chuyển KLAY từ tài khoản chủ sở hữu tới contract. 

## 5.11 Generating a random number

Bây giờ hãy thử làm một điều thú vị sau. 
Hãy tạo hai số ngẫu nhiên để dùng cho phép tính cộng. 
Tôi sẽ làm Html trước. 
Hãy viết thêm code này lên trên div spin.
<div class="row text-center">
        <div id="game" style="display: none;">   
          <div class="yellow-box" id="start">       
            <a href="#" onclick="App.generateNumbers()">시작</a>
          </div>     
          <div class="yellow-box" id="question" style="display: none;">
            <span id="num1"></span> + <span id="num2"></span> = ?          
            <div class="input-group">
              <input type="number" class="form-control" id="answer" />
              <span class="input-group-btn">
                <button type="button" class="btn btn-default" onclick="App.submitAnswer()">제출</button>
              </span>
            </div>
          </div>     
        </div> 
      </div>
<br />
 

Tôi ẩn nó với css. 
Và tôi sẽ làm cho nó hiển thị sau khi tôi đăng nhập. 
Nhấp vào nút bắt đầu gọi hàm generateNumbers. 
Sau đó, hàm sẽ tạo hai số, num1 và num2. 
Được sử dụng cho phép tính cộng. 
Và có một trường input để viết câu trả lời.
Cuối cùng, có một nút để gửi câu trả lời của bạn. 
Html đơn giản. Bây giờ, 
Tôi sẽ thiết lập nó để chỉ những người dùng đã được xác minh mới thấy phần này. 
Đi đến hàm changeUI và thêm nó bên dưới logout.show () để hiển thị div game.
$('#game').show();
 

Bây giờ hãy kiểm tra nó trong html. 
Nếu bạn đã đăng nhập, bạn có thể thấy giao diện người dùng hộp màu vàng ở giữa. 
Bây giờ tôi sẽ đặt các số sẽ hiển thị khi bạn nhấp vào Start. 
Chúng ta hãy tạo các số ngẫu nhiên trong hàm generatenumbers.
var num1 = Math.random();
 

Đầu tiên, chúng ta gọi hàm random của class Math. 
Hàm random được tạo ngẫu nhiên một số có dấu thập phân với 0 và 1. 
Nhưng nếu bạn làm điều này, con số quá nhỏ, vì vậy tôi sẽ nhân nó lên.
var num1 = Math.random() * 50;
 

Điều này sẽ tạo ra một số ngẫu nhiên từ 0 đến 49. 
Nhưng vấn đề không nên quá dễ dàng, vì vậy tôi sẽ cộng thêm 10 vào giá trị được tạo để bạn có thể tạo ít nhất hai chữ số.
var num1 = (Math.random() * 50) + 10;
 

Cuối cùng, chúng ta sử dụng hàm floor để loại bỏ dấu thập phân.
var num1 = Math.floor((Math.random() * 50) + 10);
 
Nếu bạn làm điều này, bạn sẽ có một số thập phân trong khoảng từ 10 đến 59.
Tiếp theo, tạo một cái khác.
 
var num2 = Math.floor((Math.random() * 50) + 10);
 
Bây giờ chúng ta sẽ lưu giá trị đã cộng tăng từ hai số trong session storage. 
Tôi sẽ lưu câu trả lời.
 
sessionStorage.setItem('result', num1 + num2);    

Điều này sau đó sẽ đưa câu trả lời chính xác trở lại khi người dùng trả lời và sẽ cố gắng so sánh các câu trả lời được cung cấp bởi người dùng. 
Bây giờ chúng ta đã tạo ra các số, chúng ta sẽ phải sử dụng nó. 
Khi tôi nhấp vào Start trong html, tôi sẽ ẩn phần bắt đầu này và làm cho nó hiển thị question trong thẻ div dưới. Và đồng thời, tôi sẽ làm hiển thị hai số đã được tạo từ hàm trong các trường num1 và num2. 
Chúng ta hãy quay trở lại hàm và thực hiện những gì chúng ta vừa nói.
$('#start').hide();
 

làm nó không thể nhìn thấy.
$('#num1').text(num1);
$('#num2').text(num2);

Hãy để nó hiển thị các số được tạo ra trong các trường num1 và num2. 
Và hiển thị div question 
$('#question').show(); 
	

Cuối cùng, dùng focus để tạo chỗ viết câu trả lời.
document.querySelector('#answer').focus();

Tôi sẽ kiểm tra nó ngay bây giờ. 
Khi bạn bấm Start, các số ngẫu nhiên của bạn được xuất ra và hiển thị bằng html. 
Ngay sau đó, focus tạo ra ô trống để bạn viết câu trả lời. 
Bài học hôm nay xin kết thúc tại đây. Tôi sẽ trở lại với nội dung tạo timer trong bài giảng tới. 

## 5.12 Generating a timer

Tạo một bộ timer và thiết lập timeout cho phép cộng là 3 giây.
Truy cập Html và tạo một div hiển thị bộ đếm thời gian. Tôi sẽ làm ngay dưới div spin.
<div class="row text-center">
        <p id="timer"></p>
      </div>   
 
Truy cập index.js và chuyển đến hàm showtimer. Ở đây chúng ta sử dụng hàm setInterval để hiển thị số cần đếm ngược. Chúng ta sẽ làm cho phép tính biến mất sau 3 giây và màn hình trở lại click Start.

Tạo một biến để lưu trong 3 giây.
$('#timer').text(seconds);

Viết trực tiếp số 3 vào html đang hiển thị bộ Timer. 
Tôi sử dụng hàm setinterval và đặt nó ở khoảng thời gian 1 giây.
  var interval = setInterval(function() {  
  }, 1000);
 1000 có nghĩa là 1 giây. 

Bây giờ, tôi có thể chạy một cái gì đó trong khoảng thời gian 1 giây.
$('#timer').text(--seconds);  
 

Giảm số từng số một và nó hiện thị trong html. 
Bây giờ, giá trị của biến second này là 0, nghĩa là reset nó khi setinterval bằng 0 sau 3 giây.
if (seconds <= 0) {
}     
 
$('#timer').text('');
 

Khởi tạo phần hiển thị số
     $('#answer').val('');
답적었던input도 초기화시키구요	

Cũng khởi tạo đầu vào là câu trả lời.
$('#question').hide();
 
Cài đặt div không hiển thị question. Và,
 
$('#start').show();          
 

Hiển thị lại div để bạn có thể nhấp vào start. Cuối cùng,
  clearInterval(interval);

Sử dụng ClearInterval để dừng thời gian chạy trong setinterval. Vâng, tôi đã tạo ra hàm showtimer. Bây giờ hãy gọi hàm này trong hàm generateNumbers.
this.showTimer();
 
Nếu bạn làm điều này, ngay khi bạn nhấp vào Start, bộ Timer sẽ được tạo và bắt đầu đếm ngược. Hãy thử kiểm tra.
Bấm vào Start. Một bộ Timer sẽ được tạo ra bên dưới và bắt đầu đếm ngược trong 3 giây. Sau 3 giây, nó được thiết lập lại.
Như vậy, chúng ta đã tạo được một bộ đếm giờ. 
 
## 5.13 Submitting answers and receiving KLAY
 
Đây là bài giảng cuối cùng. Nếu người dùng gửi câu trả lời và câu trả lời là chính xác, hãy thực hiện gửi KLAY đến tài khoản người dùng từ contract. Đến hàm submitAnswer. Tải giá trị của câu trả lời đúng được lưu trữ trong session storage.
const result = sessionStorage.getItem('result');
 

Và, lưu trữ các câu trả lời mà người dùng đã thực hiện trong các biến.
var answer = $('#answer').val();  

Hãy làm một phép so sánh. 
 
if (answer === result) { }
 
Nếu người dùng trả lời đúng, nhấn nút xác nhận trong khi mở cửa sổ tin nhắn xác nhận và gửi KLAY cho người dùng.
if (confirm("대단하네요^^ 0.1 KLAY 받기")) { }

Nếu người dùng nhấp vào nút OK, hãy đảm bảo số dư trong contract ít nhất là 0,1 KLAY trước khi gửi.
if (await this.callContractBalance() >= 0.1) { }

Nếu vậy, hãy gọi hàm receiveKlay.
this.receiveKlay();
 
Nếu không có, hãy gửi thông báo.
else { alert("죄송합니다. 컨트랙의 KLAY가 다 소모되었습니다."); }    
 

Cuối cùng, nếu câu trả lời của người dùng không chính xác, hãy gửi thông báo. 
else { alert("땡! 초등학생도 하는데 ㅠㅠ"); }


Có hàm submitanswer ở đây. 
Hãy thử nó một lần. 
Thông báo này hiện ra khi câu trả lời không đúng. 
Nhấp vào nút Start, khi bạn trả lời đúng, một cửa sổ thông báo sẽ hiện ra để xác nhận việc nhận được KLAY. 
Khi nhấn và nút OK, bạn sẽ gọi hàm receiveklay để chuyển KLAY. 
Tôi vẫn chưa thực thi lệnh này.
Chúng ta hãy triển khai hàm này.
Đây sẽ là hàm cuối cùng trong chuỗi bài giảng. 
 
Khi người dùng trả lời đúng câu, họ sẽ trả phí giao dịch thông qua tài khoản của họ và nhận được KLAY. Khi bạn nhìn thấy hàm transfer trong contract, chúng ta sẽ chuyển đổi 0,1 KLAY trong hàm transfer contract sang peb và truyền nó làm một đối số. 

Trước tiên, tôi sẽ chỉ cho bạn cách tải bằng cách sử dụng một spinner trong quá trình xử lý giao dịch.
var spinner = this.showSpinner();

Ngoài ra, chúng ta cần địa chỉ tài khoản được xác minh là cần thiết cho giao dịch, vì vậy, hãy tải instance Ví.
const walletInstance = this.getWallet();
 

Nếu giá trị của instance ví không tồn tại, hãy thoát khỏi hàm.
if (!walletInstance) return;  
 

Nếu vậy, sử dụng instance contract để truy cập hàm transfer trong contract.
agContract.methods.transfer().send({
})
 
Hàm transfer của contract nhận một đối số. 
Bạn cần sử dụng utility caver để chuyển đổi KLAY sang peb.
 
cav.utils.toPeb(“0.1”, "KLAY")
Khi bạn làm như vậy, 0.1 Klay sẽ được đổi thành Peb. Và bạn nói rằng bạn cần gửi một đối tượng giao dịch vào trong tham số send. 
Bạn cần chỉ định ai gọi hàm này và đặt gas limit. 
 
from: walletInstance.address,
gas: '250000'
 
Truyền instance wallet, địa chỉ tài khoản đã được xác minh và đặt phí gas khoảng 250.000. 
Lưu ý rằng trường giá trị là không bắt buộc. 

Tôi sẽ không chuyển giá trị vì hàm transfer không phải là dạng payable. Vì dạng của hàm deposit là payable nên trường giá trị đã được truyền đi. Nhưng trường giá trị ở đây không phải dạng hàm payabe nên nó không được truyền. 
Bây giờ, sau khi giao dịch được xử lý, bạn nên kiểm tra xem nó có thành công hay không. 
Tôi có thể kiểm tra xem nó (deposit) có thành công hay không thông qua .once. 
Tuy nhiên, có một cách khác. 
Tôi có thể nhận được một biên nhận bằng cách sử dụng promise.
 
.then(function (receipt) {
});     

Chờ không đồng bộ và nhân giá trị biên nhận.
if (receipt.status) { }

Có một trường được gọi là trạng thái trong đối tượng Receipt. 
Nếu điều này là đúng, nó thành công. 
Vì vậy, nếu bạn thành công, dừng spinner.
spinner.stop(); 
 

Và hiển thị thông báo
alert("0.1 KLAY가 " + walletInstance.address + " 계정으로 지급되었습니다.");      
 

Ngoài ra, hãy tạo một liên kết trong html để có thể kiểm tra giao dịch được xử lý trực tiếp từ scope. 
Tôi sẽ tạo ra một div mới. 
Đặt ngay dưới div timer. 
<div class="row text-center">
   <div id="transaction"></div>
</div>  

<br />
 

Bạn sẽ thấy liên kết trong phần này. 
Quay trở lại hàm và xóa div transaction đầu tiên.
    $('#transaction').html("");
 

Tôi xóa dữ liệu div transaction để hiển thị một liên kết mới mỗi khi giao dịch được tạo. 
Tiếp theo, tôi sẽ thêm một liên kết.
    $('#transaction')
      .append(`<p><a href='https://baobab.klaytnscope.com/tx/${receipt.txHash}' 
                   target='_blank'>클레이튼 Scope에서 트랜젝션 확인</a></p>`);
 
 
Trong biên nhận được trả lại bởi promise, 
Thông qua trường transactionhash đến tham số url của site KlaytnScope để bạn có thể thấy thông tin giao dịch vừa được xử lý. 
Cuối cùng, hiển thị số dư contarct mới nhất, được cập nhật  trong html.
 
return agContract.methods.getBalance().call()
  .then(function (balance) {
});        
 
Gọi hàm getBalance của contract để gọi số dư còn lại trong contract.
 
 $('#contractBalance').html("");          
 

Xóa hiển thị số dư hiện có và hiển thị số dư cập nhật ngay lập tức.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(balance, "KLAY") + ' KLAY' + '</p>');           
 
Như vậy, toàn bộ quy trình đã được hoàn thành.
Bây giờ, hãy thử kiểm tra.
Lần này, tôi cố gắng đăng nhập bằng một tài khoản khác, không phải tài khoản chủ sở hữu.
Bạn có thể tiếp tục với tài khoản chủ sở hữu.
Nếu bạn đã tạo một tài khoản khác, bạn cũng có thể dùng thử.
Đầu tiên, đăng nhập. Chọn một tài khoản khác. Xác thực tài khoản. 
Hãy giải phép tính. 
Nếu bạn giải phép tính và nhấn nút OK, hàm receiveKlay sẽ được gọi.
Thông báo được hiển thị và giao dịch đã được hoàn thành.
Bạn có thể đóng tin nhắn thông báo và thấy rằng số dư đã giảm.
Số dư trong contract đã giảm vì Klaytn đã được chuyển đến tài khoản của bạn.
Và liên kết đã được tạo ra ở phía dưới.
Nếu bạn nhấp vào liên kết, bạn có thể thấy các thông tin chúng ta vừa tạo trên scope.
Nhấp vào địa chỉ tài khoản của bạn và bạn sẽ thấy số dư đang tăng lên.
Như vậy, tôi đã giải phép tính và chuyển KLAY từ contract đến tài khoản của mình.
