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
 
Bởi vì chúng ta đã tạo UI được hiển thị ở trên, bây giờ thực hiện logic cho nó hoạt động.
 Trong Index.js, có nhiều hàm khác nhau trong constant gọi là App. 
Và cuối cùng, khi bạn kéo xuống, bạn sẽ thấy rằng điều đầu tiên khi bạn tải trang, bắt đầu start function trong constant app. 
Vì vậy, chúng ta sẽ triển khai chức năng start, nhưng trước đó, chúng tôi cần tải caver.js tương tác với blockchain Klaytn và khởi tạo nó để có thể sử dụng cho BApp.
import Caver from "caver-js";
 
Ở đầu, nhập caver.js. 
Và tạo một hằng số cho việc thiết lập môi trường làm việc.
 
const config = {
  rpcURL: 'https://api.baobab.klaytn.net:8651'
}
 
 
rpcURL trong cấu hình. 
Chúng tôi đã xác định node Klaytn nào kết nối và sử dụng. 
Tôi đã nói đó là baobab testnet. 
Cuối cùng, chúng ta sẽ tạo hằng số khởi tạo rpcURL bằng cách pass nó đến cấu trúc Caver.
const cav = new Caver(config.rpcURL);
 
 
Công việc khởi tạo đã kết thúc và hằng số cav này hiện có sẵn trong ứng dụng.
 Bây giờ bạn phải bắt đầu chức năng, nhưng trước đó, trước tiên bạn phải kiểm tra xem tài khoản đã được xác minh qua hay chưa thông qua cession. 
Tuy nhiên, tôi sẽ nói phần này  trong bài giảng sau, vì vậy bây giờ hãy để trống start function bây giờ. 
Trước tiên, hãy thực hiện chức năng handleImport.
 Chúng ta có thể nhấp vào nút đăng nhập và chọn tệp keystore sau khi pop-up modal. 
Tuy nhiên, tệp này phải được xác thực cho dù có thực sự là tệp keystore hợp lệ hay không. 
Chúng ta hãy làm điều đó trong chức năng handleimport. 
Đầu tiên, chúng ta tạo FileReader và đặt nó trong một constant.
const fileReader = new FileReader();
 
 
Và sử dụng chức năng readAsText để đọc tệp đã chọn.
fileReader.readAsText(event.target.files[0]);
 
 
event.target.files, phần này có nghĩa là tệp chúng tôi đã chọn. 
Khi quá trình thực thi readAsText hoàn tất, việc tải FileReader đang xảy ra.
fileReader.onload = (event) => {  	
  
}
 
Sự kiện nhận được sẽ gọi lại, hay một nghĩa khác, Nội dung của tệp, giờ đây có thể được sử dụng trong mã của Block này. 
Nội dung của tệp này sẽ được kiểm tra xem đó có phải là keystore hợp lệ hay không. 
Đầu tiên, thử lấy Block bên trong.
 
  try {
   	
  } catch (event) {
   	
  }
 
 
Bây giờ chúng tôi sẽ kiểm tra liệu nội dung câu có hợp lệ hay không, nói cách khác, nếu đây là tệp keystore thực.
if (!this.checkValidKeystore(event.target.result)) {
 
}
 
 
Tôi đã chuyển nội dung của tệp mà chúng ta đã đọc cho hàm checkValidKeystore nhưu là đối số.
 Bây giờ hãy xem lại hàm checkValidKeystore. 
Hàm này lấy keystore làm đối số và nhận tệp. 
Và tệp keystore tôi nhận được là tệp json. 
Tôi sẽ thay đổi nó thành Javascript để sử dụng các thuộc tính trong tệp json này làm biến.
	const parsedKeystore = JSON.parse(keystore);
 
 
Tôi đã sử dụng hàm json để phân tích nội dung của tệp keystore, chuyển nó thành object và lưu trữ nó trong hằng số. 
Chúng ta nên làm gì tiếp theo? 
Đảm bảo rằng các thuộc tính cần thiết cho cấu hình keystore, nhập chính xác. 
Hãy xem tập tin keystore và xem những gì chúng ta cần. 
Các yếu tố thiết yếu của cấu hình keystore là phiên bản, id, địa chỉ và tiền điện tử. 
Nếu không có bốn trường này, nó không thể trở thành tệp keystore. 
Vì vậy, tôi sẽ kiểm tra nó thông qua code.
const isValidKeystore = parsedKeystore.version &&
  	parsedKeystore.id &&
  	parsedKeystore.address &&
  	parsedKeystore.crypto;
 
 
Cuối cùng, quay lại hằng số này.
return isValidKeystore;
 
 
Tôi kéo lên lại và xác minh nếu tệp tôi vừa nhập là tệp keystore hợp lệ.. 
Nếu không, tin nhắn thông báo không hợp lệ và kết thúc chức năng.
$('#message').text('유효하지 않은 keystore 파일입니다.');
return;
 
Nếu nó vượt qua bước xác minh, chúng tôi sẽ lưu nội dung của tệp keystore vào hàm biến toàn cầu.
Đầu tiên chúng ta cần tạo một biến toàn cầu. Tạo nó trước khi bắt đầu function
 
auth: {
	accessType: 'keystore',
	keystore: '',
	password: ''
  },
 
 
Có ba trường trong trong Auth object.
 AccessType là một phương thức xác minh, gồm loại keystore và private key.. 
Chúng ta đang tiến hành với loại keystore. 
Keystore lưu trữ toàn bộ nội dung của tệp.
 Cuối cùng, password là chứa mật khẩu sẽ kết hợp với tệp keystore. 
Nếu chúng ta quay trở lại chức năng và vượt qua bước xác nhận, sẽ hiển thị,
this.auth.keystore = event.target.result;
 
 
Gửi toàn bộ nội dung của tệp được tải đến keystore của biến auth mà chúng ta đã tạo. 
Sau đó, gửi tin nhắn nói rằng tôi đã thành công.
$('#message').text('keystore 통과. 비밀번호를 입력하세요.');
 
Nếu có thể hãy nhập mật khẩu trong trường password.
 
document.querySelector('#input-password').focus();
 
Cuối cùng, trong khi đọc tệp, nếu phát hiện lỗi, hãy gửi thông báo lỗi trong Block và ngừng chức năng này.
$('#message').text('유효하지 않은 keystore 파일입니다.');
return;
 
 
Vâng, chức năng Handleimport xử lý tốt. 
Hãy kiểm tra ngay bây giờ. Chọn tệp keystore. 
Thông báo sẽ được hiển thị và phần trọng tâm sẽ được chuyển đến phần có thể nhập mật khẩu. 
Để kiểm tra trường hợp ngược lại, hãy để chọn một tập tin ngẫu nhiên. 
Ok, thông báo lỗi đã xuất hiện. 
Nhưng nó vẫn hoạt động tốt. 
Bây giờ, hãy tạo chức năng lưu trữ mật khẩu trong hàm biến toàn cầu khi chúng ta nhập mật khẩu. 
Nó rất đơn giản. 
Nếu bạn truy cập html, handlepassword sẽ thông báo khi bạn nhập mật khẩu. 
TSau đó, tại hàm handlepassword,
this.auth.password = event.target.value;
 
Lấy mật khẩu thông qua html và sau đó, dán nó vào trường mật khẩu của hàm biến toàn cầu auth.
 Nó rất đơn giản. 
Nãy giờ, tôi đã thực hiện tệp xác thực tệp keystore.
Trong bài giảng tiếp theo, tôi sẽ tạo một khóa bí mật và thêm thông tin tài khoản của tôi vào Ví.
 
## 5.7 Xác minh tài khoản (tích hợp ví)
 

Chúng tôi đã hoàn thành phần truy xuất tệp keystore và nhập mật khẩu, 
ây giờ chúng ta sẽ kiểm tra xem tài khoản có được xác minh thành công hay không khi chúng tôi gửi thông tin này đến node baobab.
Trước đó, tôi sẽ thay thế http trong rpcURL thành https. 
Hãy xem Index.html. 
Khi tôi nhấp vào node gửi, nó gửi đến hàm handlelogin. 
Vì vậy, hãy thực hiện chức năng. 
Đầu tiên, hãy chắc chắn rằng accesstype là keystore.
if (this.auth.accessType === 'keystore') { 
}

Lý do chúng ta viết “if” là khi xác minh tài khoản, chúng ta sử dụng keystore hoặc private key.
Bây giờ chúng ta chỉ sử dụng keystore. 
Tuy nhiên, tôi đã thêm các câu lệnh if này để khi bạn muốn sử dụng private key để xác minh,
 bạn có thể sử dụng nó. Hãy thêm “try catch” ngay bên dưới. 
 
 
try {       
} catch (e) 
}

Đã đến lúc sử dụng instance caver.
Tôi sẽ đưa ra câu hỏi cho bạn. 
Chúng ta có thể kiếm được gì từ sự kết hợp của tệp keystore và mật khẩu? 
Nếu bạn nhớ tốt, bạn có thể biết ngay. 
Có, bạn có thể nhận khóa cá nhân của bạn. 
Với khóa cá nhân này sẽ cho phép bạn tạo ta một instance Ví. 
Vì vậy, điều đầu tiên bạn cần làm là lấy secret key (khóa bí mật) thông qua tập tin keystore và mật khẩu..
const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;

Bạn có thể sử dụng chức năng giải mã thông qua tài khoản của instance caver. 
 Nó có nghĩa là giải mã. 
 Nếu bạn giải mã nó, bạn có thể trở về  đối tượng tài khoản được mã háo bằng cách chuyển nội dung của tệp keystore và mật khẩu như đối số. 
Có nhiều thành viên khác nhau trong đối tượng và trong số đó, chúng ta nhận được private key và lưu trữ nó trong hằng số. 
Nếu có lỗi sai trong giải mã, tin nhắn sẽ thông báo.
$('#message').text('비밀번호가 일치하지 않습니다.');
$(‘#message’).text(‘password is not matched.’);
 
Nếu không có lỗi, nó sẽ tạo ra instance ví thông qua secret key của bạn.
 
this.integrateWallet(privateKey);



Đưa private key cho hàm integwallet. 
Bây giờ, truy cập vào hàm integwallet. 
Ở dâu,chúng ta thêm code để lấy instance Ví instance bằng cách sử dụng privatekey.
 
const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);
 

walletinstance có thông tin tài khoản của tôi. 
Sau đó thêm instance này vào Ví của tôi.
cav.klay.accounts.wallet.add(walletInstance)
 

Nếu bạn thêm tài khoản vào ví caver, 
bạn có thể dễ dàng gọi lại thông tin tài khoản của mình thông qua instance caver khi bạn tạo ra một giao dịch trong tương lai. 
Bước tiếp theo là lưu trữ instance ví trong session lưu trữ. 
SessionStorage sẽ lưu trữ instance Wallet trong không gian lưu trữ trong trình duyệt web cho đến khi tab được đóng hoặc trình duyệt web bị đóng.
sessionStorage.setItem('walletInstance', JSON.stringify(walletInstance))
 
 

SetItem nhận giá trị key value là một cặp. 
Tham số đầu tiên là key và tham số thứ hai là value. 
Vì vậy, tôi sẽ phải tải thông tin tài khoản của mình vào session sau. 
Khi bạn gọi WalletInstance bằng key value, giá trị được lưu trong cặp sẽ tự động tải.
Lý do sử dụng sessionStorage là để giữ cho tài khoản được đăng nhập. 
Bởi vì thông tin tài khoản của tôi được lưu trữ trong ví caver của tôi biến mất khi tôi truy cập trang web khác hoặc trang làm mới thông tin đó. 
Tuy nhiên, nếu bạn lưu vào bộ nhớ session, 
thông tin tài khoản của bạn sẽ vẫn được duy trì ngay cả khi bạn truy cập một trang web khác trong một thời gian và sau đó quay lại trang đó hoặc làm mới trang. 
Vì vậy, tôi sẽ triển khai session instance wallet trong phần sau khi bắt đầu function và tiếp tục đăng nhập. 
Ngay bây giờ tôi cần cập nhật giao diện (UI) người dùng. 
Bây giờ chúng ta đã hoàn thành xác minh tài khoản thông qua integWallet, chúng ta cần thay đổi UI một cách thích hợp.
this.changeUI(walletInstance);  

Tôi đang gửi instance Wallet tới hàm ChangeUI . 
Vậy chúng ta phải làm gì với hàm ChangeUI? 
 Đóng lại modal.
$('#loginModal').modal('hide');
 

Ẩn nút đăng nhập.
$("#login").hide();
 
Ngoài ra, thay đổi nút Đăng xuất mà bạn đã ẩn trước đó.
 
$('#logout').show();

Và vì bạn đã đăng nhập, tôi muốn địa chỉ tài khoản của tôi hiển thị .
$('#address').append('<br>' + '<p>' + '내 계정 주소: ' + walletInstance.address + '</p>');   
 

Mã code này cho tôi biết rằng nó là địa chỉ tài khoản trong html trong đó thuộc tính id là địa chỉ. 
Tôi sẽ truy cập  index.html và thêm 1 div.
  <div class="text-center" id="address"></div>    

Vâng, bạn có thể thấy địa chỉ tài khoản của tôi tại vị trí này. 
Tôi sẽ thực hiện tại đây. 
Bây giờ hãy kiểm tra nó. 
Nhấp vào nút Đăng nhập và mở tệp keystore. 
Nếu bạn nhập mật khẩu và nhấn nút gửi, tài khoản của bạn sẽ được xác minh và nút đăng xuất xuất hiện. 
Dưới đây bạn có thể thấy địa chỉ tài khoản của tôi. 
Cuối cùng, hãy thực hiện hàm để đăng xuất. 
Truy cập Index.html. 
Lưu ý rằng khi tôi nhấp vào nút đăng xuất, tôi gọi đến hàm handlelogout. 
Tôi sẽ truy cập. 
Ở đây chúng ta sẽ gọi một hàm là removeWallet.
this.removeWallet();
 

chúng ta sẽ xóa ví và xóa bộ sessionstorage với hàm này. 
Truy cập hàm removeWallet và thêm mã code này.
cav.klay.accounts.wallet.clear();
 
Đây là quá trình xóa instance Wallet của tôi: thông tin tài khoản đã được thêm vào ví. 
Sau đó, xóa session.
 
sessionStorage.removeItem('walletInstance');

Khi bạn xóa nó, chỉ cần nhập giá trị key value. 
Cuối cùng, nó sẽ gửi tới hàm reset và ends.
this.reset();
 

hàm reset này chỉ đơn giản là khởi tạo biến toàn cầu auth. 
Truy cập hàm reset và khởi tạo auth.
this.auth = {
      keystore: '',
      password: ''
    };
 

Ngoài ra còn có một accesstype trong Auth. 
Nhưng, bạn không phải xóa accesstype vì dù sao nó cũng là một keystore. 
Thay vào đó, khi chúng ta đăng nhập, một giá trị sẽ được nhập vào keystore và mật khẩu. 
Tôi muốn đăng xuất và xóa nó một cách an toàn. 
Quay trở lại hàm handleLogout và đặt code làm mới trang và hoàn thành nó. 
Lý do cho việc làm mới là để trở về giao diện người dùng trạng thái ban đầu.
location.reload();
 

Bây giờ hãy thử nghiệm và hoàn thành nó. 
Nhấp vào nút Đăng xuất, thông tin tài khoản sẽ biến mất và bạn được đưa trở lại màn hình khởi tạo bằng cách làm mới nó. 
Bây giờ bạn hoàn thành logic xác minh tài khoản của mình, 
hãy hoàn thành phần phần này mà xác minh tài khoản thông qua session lưu trữ trong bài giảng tiếp theo.
 
 
## 5.8 Session tài khoản 

Hãy xem điều gì xảy ra khi chúng ta đăng nhập và làm mới trang. 
Nhấp vào nút đăng nhập và chọn tệp keystore. 
Trong trạng thái này, Nhấn F5 để làm mới. 
 Sau đó, nó sẽ được thiết lập lại. 
Sẽ tốt hơn nếu tôi tiếp tục đăng nhập. 
Làm thế nào để tôi làm điều đó? 
Nếu chúng ta đăng nhập thành công, chúng ta đã lưu thông tin lưu trữ tài khoản vào session lưu trữ. 
Tôi sẽ sử dụng nó bây giờ. 
Hàm đầu tiên được tải khi BApp chạy là hàm start. 
Ở đây tôi lấy thông tin tài khoản của tôi được lưu trữ trong session lưu trữ. 
Vì thế, chúng ta hãy truy cập hàm start,
const walletFromSession = sessionStorage.getItem('walletInstance');
 

Nếu bạn sử dụng getItem và chuyển giá trị của key, giá trị đó sẽ được tìm nạp và lưu trữ trong constant. 
 Tôi đã lưu instance Wallet của tôi. 
Tiếp theo, hãy đảm bảo hằng số WalletFromSession chứa giá trị.
if (walletFromSession) {
 
}
 

Nếu có một giá trị, tạo ra một try catch
try { 
     
} catch (e) {
 
  }
 

Sau đó thêm thông tin tài khoản của bạn trở lại ví caver.
cav.klay.accounts.wallet.add(JSON.parse(walletFromSession));

Khi trang được làm mới hoặc truy cập lại, thông tin tài khoản hiện được thêm vào Ví sẽ bị xóa, vì vậy tôi thêm nó trở lại qua session này. 
Cập nhật giao diện người dùng (UI) để hiển thị rằng bạn đã đăng nhập như tiếp theo.
  this.changeUI(JSON.parse(walletFromSession));
 

Nó sẽ chuyển thành nút đăng xuất và cho tôi xem địa chỉ tài khoản của bạn.  
Cuối cùng, khi giá trị trong sessionStorage không phải là instance Wallet hợp lệ, nó sẽ chuyển đến câu lệnh catch. 
 Sau đó xóa walletinstance trong session lưu trữ.
sessionStorage.removeItem('walletInstance');
 
Đã thực hiện xong ở đây. 
Bây giờ, hãy để thử nghiệm nó.
Khi bạn làm mới, nó sẽ tiếp tục đăng nhập mà không trở về trạng thái khởi tạo. 
 Nãy giờ, chúng ta đã thực hiện một phần của việc duy trì xác minh tài khoản.
 
 
 
 
## 5.9 Chuyển KLAY qua hợp đồng (deposit)
 
 
Bây giờ tôi sẽ gửi KLAY đến hợp đồng bằng cách sử dụng tài khoản quản trị. 
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
 

Vui lòng làm mờ video và thêm phần này. 
Tôi sẽ giải thích ngắn gọn. 
Tôi đã thiết lập phần UI để gửi tiền vào hợp đồng vô hình thông qua css. 
Chúng ta đã thiết lập hàm deposit để chạy khi chúng ta nhập số tiền và nhấn nút gửi. 
Bây giờ hãy đến hàm deposit và thực hiện nó. 
 
Tôi sẽ giải thích ở đây làm thế nào để thực hiện nó đầu tiên. 
Chuyển Klay sang hợp đồng chỉ có thể được thực hiện với tài khoản chủ sở hữu. 
Điều này chỉ có thể với tài khoản của người đã tạo ra Hợp đồng.
Nói cách khác, chỉ có người quản trị mới có thể gửi nó.
Nếu chúng ta đang sử dụng tài khoản chủ sở hữu, chúng ta sẽ truy cập hàm deposit trong hợp đồng và chuyển khoản KLAY.  
Quy trình rất đơn giản. 
Đầu tiên, chúng ta sẽ tạo hàm instance để chúng ta có thể truy cập vào hợp đồng mà chúng ta đã tạo. 
Khi bạn tạo một instance hợp đồng, bạn cần thông tin abi và địa chỉ của hợp đồng bạn đã tạo. 
Trong các hằng số cav ở trên cùng, 
const agContract = new cav.klay.Contract(DEPLOYED_ABI, DEPLOYED_ADDRESS);

Ở deployed_abi và deployed_address là các hằng số toàn cục có thể được sử dụng trong BApp. 
Khi chúng ta phái triển hợp đồng, chúng ta lưu thông tin vào tệp deployedabi và tệp deployedaddreess. 
Đặt nó trong gói web để chúng ta có thể đọc thông tin này và nó sử dụng nó như một hằng số toàn cục. 
Nếu bạn truy cập tệp Webpack.config.js, sẽ có một phần chú thích. 
Giải quyết điều này ngay bây giờ. 
At compile time in webpacks, run this part to set global constants called deployed address and deployed abi.
 
Nói một cách đơn giản, chúng ta đọc tệp deployedaddres và gán địa chỉ hợp đồng cho hằng số toàn cục. 
Theo cách tương tự, chúng ta lưu trữ thông tin abi trong các hằng số toàn cục có trong tệp deployedabi. 
Hãy để lại cho tập tin Index.js.
 
 

Vì vậy, hãy nhớ rằng cả thông tin abi và địa chỉ được gửi cho người tạo ra instance hợp đồng chuyển qua các hằng số toàn cục được tạo bởi webpack.  
Bây giờ chúng ta đã tạo một instance 4 hợp đồng, chúng ta sẽ tiếp tục với hàm deposit. 
Có một cái gì đó chúng ta phải kiểm tra trước khi gửi tiền.
 Bạn nên xác minh rằng tài khoản bạn vừa đăng nhập là tài khoản chủ sở hữu. 
Vì vậy, tôi phải đưa ra hai mẫu thông tin. 
Đầu tiên, tôi đang truy xuất thông tin tài khoản hiện đang đăng nhập.
Thứ hai, tôi sẽ lấy biến trạng thái chủ sở hữu được lưu trong hợp đồng. 
Đầu tiên, tôi sẽ lấy thông tin đăng nhập của tôi.
const walletInstance = this.getWallet();

Chuyển đến hàm getwallet và nhận thông tin tài khoản tồn tại trong ví caver đang có.
if (cav.klay.accounts.wallet.length) {
      return cav.klay.accounts.wallet[0];
    }

Wallet [0] là tài khoản đầu tiên được thêm vào Wallet, tài khoản tôi hiện đang đăng nhập. 
Bạn đã hoàn thành xong hàm.  
Tiếp theo, hãy gọi giá trị của biến trạng thái của chủ sở hữu trong hợp đồng. 
 Truy cập hàm callOwner
return await agContract.methods.owner().call();
 

chúng ta sẽ truy cập hàm chủ sở hữu thông qua thể hiện instance hợp đồng additiongame mà chúng ta đã tạo và gọi giá trị. 
Sử dụng từ khóa đang chờ để nhận các giá trị không đồng bộ. 
Vì chúng ta đã tạo các nội dung cần thiết trước khi gửi tiền cho bạn, chúng ta sẽ tiếp tục với hàm deposit.
if (walletInstance) {
 
    }
 

Nếu một instance wallet tồn tại thông qua hàm getwallet, 
so sánh địa chỉ tài khoản đã đăng nhập hiện tại với địa chỉ tài khoản của chủ sở hữu được trả lại từ hợp đồng.
if (await this.callOwner() !== walletInstance.address) return; 
 

Nếu chúng ta so sánh chúng, nhưng chúng là các giá trị khác nhau, chúng ta không thể tiến hành nữa và chúng ta chấm dứt hàm.
 Nếu nó giống nhau
else {
}
 

Nhận giá trị đầu vào Html .
var amount = $('#amount').val();

nếu giá tri đầu vào tồn tại
if (amount) {
}
 
Gửi giá trị cho hàm deposit bằng cách sử dụng một instance contract.
 
agContract.methods.deposit().send({
 
})

Ở đây chúng tôi gửi một đối tượng giao dịch như là một hệ số gửi.
Chúng ta cần xác định ba điều. 
Đầu tiên chúng ta phải nói ai đang gọi hàm này.
from: walletInstance.address,
 
Tôi đã nói rằng chúng ta sẽ gọi hàm này bằng tài khoản hiện đang đăng nhập.
Lưu ý rằng địa chỉ của Walletinstance là tài khoản đã hoàn tất xác minh tài khoản và nó có quyền tạo chữ ký trong giao dịch.
Vì vậy, tôi có thể đặt bất kỳ địa chỉ nào trong ‘from'. 
Chỉ các địa chỉ đã được xác minh trong BApp có thể được sử dụng làm giá trị. 
Và đặt gas sẽ được tiêu thụ là 250.000.
 
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
 
 
## 5.10 Chuyển  KLAY thông qua hợp đồng (thay đổi và kiểm tra UI)
 
 

Tôi sẽ thử thay đổi UI và thử nghiệm. 
Khi chúng ta gửi KLAY đến hàm deposit ở bài trước và nhận được biên lai, giao dịch đã thành công. 
Tôi nên làm gì sau khi thành công? 
Sẽ thật tuyệt nếu hệ thống có thể hiển thị cho tôi tin nhắn nhắc nhở.
   alert(amount + " KLAY를 컨트랙에 송금했습니다.");  
 

Và tôi sẽ làm mới trang để xem số dư của hợp đồng.
   location.reload();     
.

Tôi đã nói rằng tôi sẽ làm cho số dư của hợp đồng được hiển thị. 
Hãy nhớ rằng chúng ta đã tạo một hàm sẽ tải số dư của hợp đồng khi chúng ta viết hợp đồng thông minh. 
Chúng ta sẽ gọi hàm getBalance này để có thể thấy số dư của hợp đồng. 
Trước tiên, chúng ta sẽ thêm div hiển thị số dư của hợp đồng trong html. 
Truy cập Index.html và thêm div dưới địa chỉ hiển thị địa chỉ tài khoản của tôi.
  <div class="text-center" id="contractBalance"></div>

Và sau đó chúng ta sẽ cho bạn thấy số dư của hợp đồng ở đây. 
Bây giờ, chế độ xem đã sẵn sàng, hãy tạo một hàm mà có thể tải số dư từ backend. 
Truy cập hàm callcountractbalance và thêm code.
return await agContract.methods.getBalance().call();
 

Phần truy cập hàm getbalance thông qua instance hợp đồng và tải giá trị. Vâng, nó thật đơn giản. 
Từ đâu tôi gọi hàm callcountractbalance? 
Tôi nên gọi nó ở đâu? 
Nếu giao dịch thành công trong hàm deposit và nhận được biên nhận, nó sẽ làm mới trang thông qua location.reload (). 
Hàm đầu tiên nào thực thi khi trang được làm mới? 
Hàm start được thực thi trước. 
Sau đó, chúng ta gọi hàm changeUI từ hàm start. 
Tôi cần thêm code để tải số dư hợp đồng từ hàm ChangeUI thay đổi UI ngay lập tức.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(await this.callContractBalance(), "KLAY") + ' KLAY' + '</p>');     

Nó khá dài. 
Tôi sẽ giải thích.
chúng ta sẽ thêm thông báo vào phần hiển thị số dư hợp đồng Trong html. 
Gọi hàm callContractBalance để lấy số dư. 
Tuy nhiên, số dư sau đó được tải vào đơn vị tối thiểu của KLAY, peb. 
Điều đó sẽ khiến bạn khó thấy được còn lại bao nhiêu, vì đơn vị này quá lớn. 
Vì vậy, utility caver có hàm gọi là fromPeb.
Nó là một hàm có thể chuyển đổi từ peb sang đơn vị khác. 
Tôi đã chỉ định trong tham số thứ hai để chuyển đổi sang KLAY. 
Kết quả là, nó cho thấy số dư hợp đồng được chuyển đổi thành KLAY trong html.
 

Cuối cùng, việc chuyển KLAY vào hợp đồng phải được thiết lập chỉ cho tài khoản chủ sở hữu. 
Bạn chỉ phải cấp phép cho việc tạo ra các sự kiện. 
Vì vậy, tôi sẽ thay đổi nó để hiển thị UI chỉ có thể được chuyển khi tôi đăng nhập bằng tài khoản chủ sở hữu. Chuyển đến hàm changeUI
if (await this.callOwner() === walletInstance.address) {
      $("#owner").show(); 
    }     
 
Tôi đã đặt div chủ sở hữu hiển thị khi địa chỉ tài khoản chủ sở hữu và địa chỉ tài khoản đã đăng nhập giống nhau. 
Trong html, div chủ sở hữu được đặt ẩn theo mặc định.
Vì vậy, khi bạn đăng nhập bằng tài khoản chủ sở hữu, bạn sẽ thấy phần này.
Bây giờ hãy thử kiểm tra. 
Tôi sẽ tạo lại nó một lần. 
Trước tiên, hãy đảm bảo rằng khóa bí mật của tài khoản của bạn được nhập chính xác vào truffle.js. 
Tôi sẽ triển khai lại nó từ terminal.
‘truffle deploy -compile-all -reset -network klaytn’ Tôi đang triển khai lại nó cho những người chưa làm. 
Việc triển khai của bạn đã kết thúc. 
Hãy kiểm tra nó bằng cách chạy npm run dev. Nhấn F12 để mở cửa sổ giao diện console. 
Nhấp vào nút Đăng nhập
Vì bạn đã đăng nhập bằng tài khoản chủ sở hữu của mình, bạn có thể thấy phần bạn có thể gửi tiền. 
Hãy gửi tiền ngay bây giờ. Gửi 1 KLAY.
 
 

Bạn có thể thấy thông tin hàm băm và nhận thông tin thông qua log trên console khi giao dịch của bạn thành công. 
Tin nhắn thông báo hoạt động tốt. 
Có vẻ như thời gian cần thiết cho giao dịch là ít hơn 3 giây. 
Trong 3 giây này, có bốn quy trình từ tạo giao dịch đến tạo block và truyền nó tới mạng lưới khi giao dịch hoàn tất. 
So với các nền tảng blockchain khác, tốc độ xử lý rất nhanh. 
Nhấp vào tin nhắn thông báo, làm mới trang và hàm start được gọi đầu tiên, 
à số dư hợp đồng cập nhật được hiển thị bởi hàm ChangeUI trong đó. 
hàm transaction đang hoạt động tốt.. 
Tôi muốn có một công cụ tải spinner cho thấy giao dịch có hoạt động tốt hay không.Tôi muốn có một công cụ tải spinner cho thấy giao dịch có hoạt động tốt hay không.
This is not a requirement, but I recommend you to do it for a good UI. 
Truy cập Index.js and truy xuất spin.js trên cùng.
import {Spinner} from 'spin.js';

Đi đến hàm showspinner và trả về instance spinner.
var target = document.getElementById('spin');
    return new Spinner(opts).spin(target);

Gọi hàm này từ hàm deposit
var spinner = this.showSpinner();
 
Sau khi nhận nhận biên lai, dừng spinner.
 
  spinner.stop();  

Cuối cùng thêm một div để hiển thị spinner trong html.<br /> dưới tag.
<div id="spin"></div>    
 

Bây giờ hãy thử kiểm tra. 
Vâng. Khi spinner xuất hiện, một cảnh ngoạn mục hơn đang được tạo ra.
hàm chuyển hoạt động tốt và giao diện người dùng được phản ánh tốt. 
Cho đến nay, tôi đã chi trả cho việc chuyển KLAY từ tài khoản chủ sở hữu tới hợp đồng.

## 5.11 Tạo 1 số ngẫu nhiên

Bây giờ hãy thử làm một phần thú vị. 
Hãy tạo hai số ngẫu nhiên được sử dụng để cộng vào. 
Tôi sẽ làm Html đầu tiên 
Vui lòng thêm code này trực tiếp trên div spin.
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
 

Tôi làm cho nó không nhìn thấy với css. 
Và tôi sẽ làm cho nó hiển thị sau khi tôi đăng nhập. 
Nhấp vào nút bắt đầu gọi hàm generateNumbers. 
Sau đó, hàm sẽ tạo hai số, một cho num1 và một cho num2. 
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
 
Bây giờ chúng ta sẽ lưu giá trị đã cộng tăng từ hai số trong session lưu trữ. 
Tôi sẽ lưu câu trả lời.
 
sessionStorage.setItem('result', num1 + num2);    

Điều này sau đó sẽ đưa câu trả lời chính xác trở lại khi người dùng trả lời và sẽ cố gắng so sánh các câu trả lời được cung cấp bởi người dùng. 
Bây giờ chúng ta đã tạo ra các số, chúng ta sẽ phải sử dụng nó. 
Khi tôi nhấp vào Start trong html, tôi sẽ ẩn phần bắt đầu này và làm cho nó hiển thị câu hỏi div below. Và đồng thời, tôi sẽ làm cho hai số được tạo từ hàm hiển thị trong các trường num1 và num2. 
Chúng ta hãy quay trở lại hàm và thực hiện những gì chúng ta vừa nói.
$('#start').hide();
 

làm nó không thể nhìn thấy.
$('#num1').text(num1);
$('#num2').text(num2);

Hãy để nó hiển thị các số được tạo ra trong các trường num1 và num2. 
Nó hiển thị câu hỏi div
$('#question').show(); 
	

Cuối cùng, di chuyển trọng tâm đến nơi tôi viết câu trả lời để tôi có thể trả lời ngay.
document.querySelector('#answer').focus();

Tôi sẽ kiểm tra nó ngay bây giờ. 
Khi bạn bấm Start, các số ngẫu nhiên của bạn được tạo và hiển thị bằng html. 
Ngay sau đó, tập trung di chuyển đến nơi tôi viết câu trả lời. 
Đây là sự kết thúc bài hôm nay và tôi sẽ cố gắng tạo một bộ Timer trong bài giảng tiếp theo.

## 5.12  Tạo bộ Timer



Tạo một bộ timer và thiết lập timeout cho vấn đề phép cộng trong 3 giây.
 Truy cập Html và tạo một div hiển thị bộ đếm thời gian. Tôi sẽ làm cho nó ngay dưới div spin.
<div class="row text-center">
        <p id="timer"></p>
      </div>   
 
Truy cập index.js và chuyển đến hàm showtimer. Ở đây chúng ta sử dụng hàm setInterval để hiển thị số cần đếm ngược. chúng ta sẽ làm cho vấn đề biến mất sau 3 giây và màn hình trở lại click Start.
 

Tạo một biến để lưu trong 3 giây.
$('#timer').text(seconds);

Hiển thị số 3 trực tiếp vào html đang hiển thị bộ Timer. 
Tôi sử dụng hàm setinterval và đặt nó ở khoảng thời gian 1 giây.
  var interval = setInterval(function() {  
  }, 1000);
 

Bây giờ, tôi có thể chạy một cái gì đó trong khoảng thời gian 1 giây.
$('#timer').text(--seconds);  
 

Giảm số từng số một và nó hiện thị trong html. 
Bây giờ, giá trị của biến giây này là 0, nghĩa là reset lại nó khi setinterval bằng 0 sau 3 giây.
if (seconds <= 0) {
}     
 
Khi Seconds là 0
 
$('#timer').text('');
 

Khởi tạo phần hiển thị số
     $('#answer').val('');
답적었던input도 초기화시키구요	

Cũng khởi tạo đầu vào là câu trả lời.
$('#question').hide();
 
Cài đặt div không hiển thị ra vấn đề. Và,
 
$('#start').show();          
 

Hiển thị div một lần nữa mà bạn có thể nhấp vào start. Cuối cùng,
  clearInterval(interval);
 

Sử dụng ClearInterval để dừng thời gian chạy trong setinterval. Vâng, tôi đã tạo ra hàm showtimer. Bây giờ hãy gọi hàm này trong hàm generateNumbers.
this.showTimer();
 
Nếu bạn làm điều này, ngay khi bạn nhấp vào Start, bộ Timer sẽ được tạo và đếm ngược sẽ được bắt đầu. Hãy thử kiểm tra.
Bấm vào Start. Một bộ Timer sẽ được tạo ra bên dưới và bắt đầu đếm ngược trong 3 giây. Sau 3 giây, nó được thiết lặp lại.
Cho đến nay, tôi đã tạo ra một bộ đếm thời gian.
 
 
 
## 5.13 Gửi câu trả lời và nhận KLAY
 
Đây là bài giảng cuối cùng. Nếu người dùng gửi câu trả lời và câu trả lời là chính xác, hãy thực hiện phần gửi KLAY đến tài khoản người dùng từ hợp đồng. Chuyển đến hàm submitAnswer. Tải giá trị của câu trả lời đúng được lưu trữ trong session lưu trữ.
const result = sessionStorage.getItem('result');
 

Và, lưu trữ các câu trả lời mà người dùng đã thực hiện trong các biến.
var answer = $('#answer').val();  
 

Now, do a comparison.
if (answer === result) { }
 

Nếu người dùng đã trả lời đúng câu trả lời, nhấn nút xác nhận trong khi mở cửa sổ tin nhắn xác nhận và gửi KLAY cho người dùng.
if (confirm("대단하네요^^ 0.1 KLAY 받기")) { }
 

Nếu người dùng nhấp vào nút OK, hãy đảm bảo số dư trong hợp đồng ít nhất là 0,1 KLAY trước khi gửi.
if (await this.callContractBalance() >= 0.1) { }

Nếu vậy, hãy gọi hàm receiveKlay.
this.receiveKlay();
 

Nếu hàm không tồn tại, gửi tin nhắn thông báo.
else { alert("죄송합니다. 컨트랙의 KLAY가 다 소모되었습니다."); }    
 

Cuối cùng, nếu người dùng không nhận được câu trả lời chính xác, hãy gửi thông báo.
else { alert("땡! 초등학생도 하는데 ㅠㅠ"); }
 
 
 

Có hàm submitanswer ở đây. 
Hãy thử nó một lần. 
Tin nhắn này được hiển thị khi câu trả lời sai. 
Khi điều này được thực hiện, một cửa sổ tin nhắn xác nhận sẽ xuất hiện để nhận được KLAY. 
Khi bạn bấm OK, bạn sẽ gọi hàm receiveklay để chuyển KLAY. 
Tôi chưa thực hiện nó xong. 
Hãy thực hiện hàm này.
Đây là hàm cuối cùng của chúng ta.
 
Khi người dùng trả lời đúng câu trả lời, họ trả phí giao dịch thông qua tài khoản của họ và nhận được KLAY. 
chúng ta sẽ chuyển đổi 0,1 KLAY trong hàm transfer của hợp đồng của chúng ta sang peb và chuyển nó làm một đối số. 
Trước tiên, hãy chỉ cho bạn cách tải bằng cách sử dụng một spinner vòng trong quá trình xử lý giao dịch.
var spinner = this.showSpinner();

Ngoài ra, chúng ta cần địa chỉ tài khoản được xác minh là cần thiết cho giao dịch, vì vậy, hãy tải instance Ví.
const walletInstance = this.getWallet();
 

Nếu giá trị của instance ví không tồn tại, hãy thoát khỏi hàm.
if (!walletInstance) return;  
 

Nếu vậy, sử dụng instance hợp đồng để truy cập hàm transfer trong hợp đồng.
agContract.methods.transfer().send({
})
 
Hàm transfer của hợp đồng nhận một đối số. 
Bạn cần sử dụng utility caver để chuyển đổi KLAY sang peb.
 
cav.utils.toPeb(“0.1”, "KLAY")
 
Và bạn nói rằng bạn cần gửi một đối tượng giao dịch vào trong tham số gửi. 
Bạn cần chỉ định ai gọi hàm này và gas limits cần được đặt.
 
from: walletInstance.address,
gas: '250000'
 
Thông qua instance wallet, địa chỉ xác minh tài khoản của bạn và đặt gas trong vòng 250.000. 
Lưu ý rằng trường giá trị là không bắt buộc. 
Tôi sẽ không chuyển giá trị vì hàm transfer không phải là một khoản phải trả. 
Nếu bạn làm điều này, bạn đã hoàn thành tất cả thì các giá trị sẽ được thông qua.  
Bây giờ, sau khi giao dịch được xử lý, bạn nên kiểm tra xem nó có thành công hay không. 
Tôi có thể kiểm tra xem nó (deposit) có thành công hay không thông qua .once. 
Tuy nhiên, có một cách khác. 
Tôi có thể nhận được một biên nhận bằng cách sử dụng promise.
 
.then(function (receipt) {
});     

Chờ không đồng bộ và nhân giá trị biên nhận.
if (receipt.status) { }

Có một trường được gọi là trạng thái trong đối tượng Receipt. 
Nếu điều này là đúng, nó thành công 
Vì vậy, nếu bạn thành công, Dừng spinner.
spinner.stop(); 
 

Ngoài ra, hiển thị tin nhắn thông báo
alert("0.1 KLAY가 " + walletInstance.address + " 계정으로 지급되었습니다.");      
 

Ngoài ra, hãy tạo một liên kết trong html để có thể kiểm tra giao dịch được xử lý trực tiếp từ scope. 
Tôi sẽ tạo ra một div mới. 
Tôi sẽ làm cho nó theo div Timer.
<div class="row text-center">
   <div id="transaction"></div>
</div>  

<br />
 

Bạn sẽ thấy liên kết trong phần này. 
Quay trở lại hàm và xóa div giao dịch đầu tiên.
    $('#transaction').html("");
 

Tôi xóa dữ liệu div giao dịch để hiển thị một liên kết mới mỗi khi giao dịch được tạo. 
Tiếp theo, tôi sẽ thêm một liên kết.
    $('#transaction')
      .append(`<p><a href='https://baobab.klaytnscope.com/tx/${receipt.txHash}' 
                   target='_blank'>클레이튼 Scope에서 트랜젝션 확인</a></p>`);
 
 
Trong biên nhận được trả lại bởi promise, 
Thông qua trường transactionhash đến tham số url của site KlaytnScope để bạn có thể thấy thông tin giao dịch vừa được xử lý. 
Cuối cùng, hiển thị cho bạn số dư hợp đồng được cập nhật mới nhất trong html.
 
return agContract.methods.getBalance().call()
  .then(function (balance) {
});        
 
Gọi hàm getBalance của hợp đồng để gọi lại số dư còn lại trong hợp đồng.
 
 $('#contractBalance').html("");          
 

Xóa hiện thị số dư hiện có và hiển thị số dư cập nhật ngay lập tức.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(balance, "KLAY") + ' KLAY' + '</p>');           
 
Toàn bộ quá trình hoàn thành cho đến nay. 
Bây giờ, hãy thử kiểm tra.
Lần này, tôi cố gắng đăng nhập bằng một tài khoản khác, không phải tài khoản chủ sở hữu.
Bạn có thể tiếp tục với tài khoản chủ sở hữu.
Nếu bạn đã tạo một tài khoản khác, bạn cũng có thể dùng thử.

 
Nếu bạn giải quyết vấn đề và nhấn nút OK, hàm receiveKlay sẽ được gọi.
Thông báo thông báo được hiển thị và giao dịch đã được hoàn thành.
Bạn có thể đóng tin nhắn thông báo và thấy rằng số dư của bạn đã giảm.
Số dư trong hợp đồng đã bị giảm khi nó chuyển đến tài khoản của bạn.
Và liên kết đã được tạo ra ở phía dưới.
Nếu bạn nhấp vào liên kết, bạn có thể thấy thông tin về chúng ta vừa tạo trên scope.
Nhấp vào địa chỉ tài khoản của bạn và bạn sẽ thấy số dư đang tăng lên.
Cho đến nay, tôi đã cố gắng giải quyết vấn đề và chuyển KLAY trong hợp đồng vào tài khoản của mình.
