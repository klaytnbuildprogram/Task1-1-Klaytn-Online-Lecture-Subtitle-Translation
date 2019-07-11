5. Sử dụng Front-end cho việc phát triển trò chơi Klaytn
 5.1 Cài đặt
Bây giờ bạn có thể tạo ra hợp đồng sử dụng cho BApp trong những lớp trước đó thông qua phát triển front-end. Đầu tiên,chúng ta tiến hành với cơ cấu đơn giản. Trong bài hướng dẫn này, tôi sẽ tải node.js, npm, framework truffle và code studio trực quan. Node.js là nền tảng server JavaScript, mà cần thiết cho sự phát triển BApp. Npm cài đặt với node.js để tải công cụ. Framework Truffle hỗ trợ tải xuống thông qua npm. Nếu bạn đã cài đặt node.js và npm, hãy kiểm tra phiên bản đó và bỏ qua phần hướng dẫn này nếu node.js là phiên bản 8 và npm là phiên bản 5 trở lên.
Vui lòng truy cập https://nodejs.org và tải 10.15.3 LTS. Vui lòng cài đặt. Tôi đã thực hiện xong vì vậy tôi bỏ qua bước này. Sau đó, chúng tôi kiểm tra xem node.js có được cài đặt trong PowerShell hay không. Nhập Node-v và kiểm tra phiên bản này với npm. Npm -v,Vâng, chính xác nó được cài đặt.
Cuối cùng, tôi sẽ cài đặt Truffle. Truffle là framework giúp bạn dễ dàng phát triển BApp. Bạn có thể biên soạn trên đó, kiểm tra và mở rộng các hợp đồng thông minh. Framework này rất phổ biến. Gần đây, nó đã cập nhật lên phiên bản tới 5 lần. Tuy nhiên, khi Klaytn phát triển phiên bản thứ 4, tôi đã sử dụng. Nếu bạn đang giữ phiên bản 5 trở xuống, bạn cần xóa nó trước. Gỡ cài đặt nó bằng cách gõ npm uninstall -g truffle ở PowerShell. Bây giờ hãy chèn 'npm install -g truffle@4.1.15' và tôi sẽ nhận phiên bản 4.
Sau đó, kiểm tra phiên bản thông qua lệnh truffle. Nếu nó là phiên bản 4.1.15 và người biên soạn solidity được gọi là 0.4.25. Solidity là ngôn ngữ lập trình mà bạn có thể viết trên các hợp đồng thông minh. Cuối cùng, hãy tải Visual  Studio Code. Truy cập ' https://code.visualstudio.com/'  để tải về máy. Tôi đã tải nó từ trước. Vì vậy, tôi cũng sẽ bỏ qua phần này. Visual Studio Code hỗ trợ đa nền tảng chạy trên Linux, Windows, Mac và một số tính năng tiện dụng như hỗ trợ gỡ lỗi, kiểm soát git, syntax highlighting, v.v.
Bây giờ bấm nút mở rộng tab ở dưới để cài đặt hỗ trợ ngôn ngữ solidity. Vui lòng nhập 'solidity' và chọn cái ở trên cùng. Nhấp vào Cài đặt. Nó sẽ hiển thị độ sáng cho mỗi solidity và cho phép bạn biên soạn lại. Cài đặt hoàn tất. Tôi kết thúc phiên cấu hình mà cần thiết cho Front-end.
5.2 Tải boilerplate
Chúng ta hãy tải boilerplate, khuôn cơ bản cho sự phát triển . Klaytn chỉ ra rằng BApp có thể phát triển trong Truffle framework. Một số vị trí trong Truffle, bạn tải xuống mẫu chuẩn phát triển BApp. Nó có tên là Truffle Box ‘https://truffleframework.com/boxes' Nếu bạn truy cập, bạn có thể xem các mẫu khuôn khác nhau. Ví dụ: nếu bạn muốn phát triển BApp bằng Angular hoặc React, bạn có thể tải mẫu phù hợp. Tuy nhiên, mẫu tải xuống ở đây chuyên về Ethereum App, vì thế bạn phải tải xuống và xóa các phần bên trong. Và bạn phải thiết lập nó cho Klaytn. Đây không phải là một phần khó, nhưng tôi đã tải mẫu webpack trước và thay đổi nó trong Klaytn way cho phù hợp với bài giảng của chúng tôi. Tôi cài nó trên Github để bạn có thể tải xuống. Để tham khảo thêm, chúng tôi sẽ tiến hành với JavaScript và JQuery. Ngay cả khi bạn chưa biết nó, bạn có thể dễ dàng theo dõi
Mở PowerShell và chạy lệnh git clone ở  'https://github.com/kkagill/addition-game-starter.git' . Tôi đã tải nó. Thực hiện 'Cd thêm-game-starter' vào đường dẫn đó. Code. Hãy xem cơ cấu bằng cách chèn ‘Code.' Tôi bắt đầu từ trên cùng. Contracts folder nơi bạn cất giữ tệp hợp đồng solidity. Chúng tôi có Addition Game- tệp hợp đồng mà chúng tôi vừa tạo và bản hợp đồng khác có tên “migrations” ở dưới sẽ cho phép bạn chạy các tệp script trong folder “migration” bên dưới khi bạn triển khai hợp đồng thông minh của mình. Đây là tập tin cần thiết để triển khai hợp đồng, vì vậy bạn không bao giờ xóa nó.
Tiếp theo, các tệp script trong thư mục migrations chứa logic mà sử dụng quá trình triển khai. Nếu bạn thấy tệp này, nó sẽ nhập tệp hợp đồng “migrations” và triển khai nội dung đến nút Klaytn. Trong thư mục src, tôi thiết lập cấu trúc gồm front-end của BApp. Tệp index.html sẽ quản lý về “view” hiển thị ở phía trước. Tôi đã tải jquery hoặc bootstrap được sử dụng trong BApp với cdn và tôi thêm phần css bên dưới trước đó.
Tệp Index.js giống như một máy động cơ, nó thực thi các chức năng. Chúng tôi đưa ra định nghĩa về các chức năng sẽ viết trong tương lai. Ở dưới là biến cấu hình hiển thị spinner khi tải. Nó không phải là phần quan trọng, vì vậy tôi đã thêm nó trước. Package.json là nơi bạn thêm các phụ lục cần thiết thông qua npm. Điều quan trọng là bạn sẽ tải xuống một tệp thư viện cho phép bạn tương tác với caver-js, blockchain Klaytn. Nó tương tự như web3 js của Ethereum. Truffle.js quyết định môi trường của nó. Thông qua truffle, bạn sẽ xác định mạng lưới nào sẽ triển khai hợp đồng thông minh. Tôi sẽ trình bày điều này trong bài giảng tiếp theo. Webpack tối ưu hóa các tệp và phát hiện bất cứ khi nào có thay đổi về code và  trình duyệt mà không phải tải lại trang. Đến giờ, tôi đã tải xong và giải thích cho các bạn về mẫu để tạo ra trò chơi Klaytn trên Bapp.
5.3 Triển khai hợp đồng thông minh cho Baobab 1
Chúng ta hãy triển khai hợp đồng thông minh AdditionGame mà chúng ta tạo trên baobab testnet. Trước khi bắt đầu, chúng ta sẽ chạy lệnh npm install trong terminal và cài đặt các phụ lục cần thiết cho BApp. Nếu bạn không thấy terminal bên dưới, hãy chọn hãy chọn new terminal trên tab Terminal. Bây giờ chạy lệnh npm install. Nó sẽ tốn chút thời gian. Khi kết thúc, thư mục có tên 'node_modules' được tạo và cài đặt phụ lục hoàn tất.
Đầu tiên, hãy tạo một tệp mới trong thư mục migrations. Nhấp chuột phải vào thư mục 'migrations”' và chọn Tệp mới. Đặt tên là '2_deploy_contuces.js' và chúng tôi sẽ thêm logic để triển khai hợp đồng AdditionGame đến node.
Truy cập Initial migrationstập tin và, sao chép và dán tất cả các code. Vui lòng thay đổi nó thành 'importing the AdditionGame contract'. Thay thế nó để triển khai với  AdditionGame.Cho đến nay, logic cơ bản triển khai đã kết thúc. Tuy nhiên, tôi sẽ viết  vào một số tệp trong BApp để lưu trữ thông tin tôi nhận được từ quá trình triển khai. Sau đó, nó sẽ giúp ích để tạo hợp đồng với thông tin này.deployer.deploy (AdditionGame)
Deployer triển khai hợp đồng AdditionGame và nhấp  then chúng tôi nhận dữ liệu json. Và trong này,if (AdditionGame._json) {
Nếu bạn đã nhận được dữ liệu json Additions game, bạn sẽ lưu nó vào tệp thông qua mô-đun. Để làm điều đó, bạn phải nhập nó trước. Thêm const fs = Yêu cầu ('fs') ở đầu. Vậy thì tôi sẽ tạo hai tập tin. Những tập tin đó là nơi chúng ta có thể lưu Abi và địa chỉ hợp đồng. Nhấp chuột phải vào bất cứ nơi nào trên màn hình và đặt tên cho tệp mới là ‘deployedABI’. Bây giờ chúng tôi sẽ sử dụng hệ thống tệp để lưu trữ chúng vào từng tệp. Đầu tiên, hãy tạo code để lưu trữ thông tin abi. Abi là nội dung có thể tương tác giữa blockchain và hợp đồng. Nếu bạn đã nhận được dữ liệu json của trò chơi Bổ sung, bạn sẽ lưu nó vào một tệp thông qua mô-đun hệ thống tệp. Để làm điều đó, bạn phải nhập nó trước. Thêm const fs = Yêu cầu ('fs') ở đầu. Vậy thì tôi sẽ tạo hai tập tin. Những tập tin đó là nơi chúng ta có thể lưu Abi và địa chỉ hợp đồng. Nhấp chuột phải vào bất cứ nơi nào trong nền và đặt tên cho tệp mới ‘triển khaiABI,. Tạo một cái khác và đặt tên là ‘triển khaiAddress. Bây giờ chúng tôi sẽ sử dụng hệ thống tệp để lưu trữ chúng vào từng tệp. Đầu tiên, hãy tạo một mã lưu trữ thông tin abi. Abi là nội dung có thể tương tác giữa blockchain và hợp đồng. fs.writeFile ('triển khaiABI', JSON.opesify (AdditionGame._json.abi),
 
Có một hàm writeFile trong hệ thống tệp. Xác định tập tin nào cần viết và chuỗi thông tin abi mà chúng tôi đã nhận được, từ json và chuyển nó đến đối số. Chúng tôi sẽ xử lý error.
(err) => {
  	if (err) throw err
  	console.log("파일에 ABI 입력 성공");
	})
Nếu có error. Nếu không, viết log tại bảng điều khiển. Điều này lưu thông tin abi của tệp hợp đồng được triển khai. Để tiếp tục, tôi sẽ lưu địa chỉ của hợp đồng đã triển khai vào tệp. fs.writeFile ('triển khaiAddress', AdditionGame.address, (err) => {if (err) throw err console.log ("에 주소 입력 성공");}) Nếu bạn đã theo dõi tất cả các bước cho đến thời điểm này, bây giờ chúng tôi lưu trữ thông tin chúng tôi muốn trong mỗi tệp ngay sau khi chúng tôi triển khai nó mỗi lần. Tôi sẽ tiếp tục thiết lập môi trường trong truffle.js và triển khai nó trong bài giảng tiếp theo.
5.4 Triển khai hợp đồng thông minh cho Baobab 2
Cuối cùng, bạn cần thiết lập cài đặt. Bạn phải quyết định mạng nào bạn sẽ triển khai. Truy cập Truffle.js. Đây, tôi sẽ làm ngay . Đầu tiên, tôi sẽ nhập tệp có tên connect-privkey-to-provider. const PrivateKeyConnector = require('connect-privkey-to-provider')
cũng tạo một hằng số được gọi là ID mạng lưới.
const NETWORK_ID = '1001'
1001 có nghĩa là mạng lưới ID duy nhất của Baobab. const GASLIMIT = '20000000'
 
Đây là gas limit để triển khai. Có bảy số không.const URL = https://api.baobab.klaytn.net:8651
 
Đối với UR, tôi đã chỉ định địa chỉ nơi các node của Klaytn hiện đang chạy, đó là testnet baobab. Cuối cùng, chúng tôi cần một hằng số để giữ khóa bí mật, vì vậy chúng tôi sẽ nhận được khóa bí mật của tài khoản chúng tôi đã tạo trước đó thông qua Ví Klaytn. Các bạn hãy llưu chìa khóa bí mật của bạn ở một nơi khác. Tôi đang sao chép và dán cái mà tôi đã lưu trong Notepad. const PRIVATE_KEY = ''
 
Bây giờ hãy sử dụng các cài đặt này trong module.exports. module.exports = { networks: { klaytn: { provider: new PrivateKeyConnector(PRIVATE_KEY, URL), network_id: NETWORK_ID, gas: GASLIMIT, gasPrice: null, } }, }
Tôi  sẽ giải thích. chúng tôi sẽ sử dụng ‘Klaytn’ cho các mạng lưới. Cụ thể,bốn tùy option ở đây. Đầu tiên, bạn chỉ định nhà cung cấp cung cấp nút Klaytn. Tạo PrivateKeyConnector và truyền tới hai đối số. Đầu tiên là truyền khóa bí mật tài khoản của tôi và thứ hai địa chỉ mạng nơi các nút đang chạy. Điều này giúp tôi kết nối với testnet baobab bằng khóa bí mật của mình. Chỉ định ID mạng lưới và gas, và cuối cùng giá gas đặt thành giá trị null. Điều này là do mạng lưới baobab sẽ tự động đặt giá gas, vì vậy chúng tôi chuyển giá trị null. Vâng đến bây giờ tôi đã thiết lập môi trường của mình để triển khai các hợp đồng thông minh. Nó khá đơn giản. Bây giờ hãy triển khai nó. Ở terminal, chạy truffle deploy-network klaytn. Vâng, chỉ cần triển khai thành công. Bạn có thể thấy cụm từ xác nhận được hiển thị trên bàn điều khiển.
 
Bây giờ, nếu bạn xem tệp deployedABI, thông tin abi được lưu trữ. Truy cập địa chỉ hợp đồng triển khai và lưu ý rằng địa chỉ của hợp đồng đã triển khai được lưu trữ. Nó hoạt động tốt. Cuối cùng, khi bạn triển khai nó, thư mục sẽ được tạo. Nó có thư mục hợp đồng bên trong và hai tập tin json nằm trong thư mục hợp đồng. Chúng được gọi là artifact. Mỗi tệp chứa thông tin ABI của hợp đồng tương ứng cũng như tất cả các thông tin liên quan đến hợp đồng. ABI là tên viết tắt của giao diện nhị phân ứng dụng; trước đây chúng tôi đã lưu trữ một tệp đã triển khai trong đó. Trong abi, chúng ta thấy các hàm và biến được viết ở định dạng json mà  sử dụng cho hợp đồng AdditionGame.
 
Nói một cách đơn giản, khi bạn triển khai hợp đồng này lên blockchain, abi này đảm bảo chức năng trong hợp đồng và dữ liệu được trả về. Đó là nơi bạn xác định cách bạn có thể tương tác với hợp đồng. Nếu bạn đi xuống dưới cùng, có một phần mạng. 1001 là ID mạng duy nhất của Klaytn. Địa chỉ là hợp đồng này hiện đang được triển khai đến địa chỉ này trên testnet Baobab.
 
truffle deploy –compile-all –reset –network klaytn
 
Cuối cùng, nếu bạn muốn triển khai lại hợp đồng cho nút Klaytn, bạn có thể sử dụng lệnh này. Ví dụ, khi chúng ta cần sửa đổi hợp đồng, chúng ta cần triển khai lại nút. truffle deploy-compile-all -reset -network - Klaytn biên soạn tất cả các hợp đồng. Reset sẽ giúp script file trong tệp  Migration khởi động lại. Re-deploy cho hợp đồng node. Vâng. Hoàn tất. Mở tệp deployedAddress và bạn sẽ thấy rằng địa chỉ đã thay đổi. Từ nãy giờ, tôi đã triển khai Hợp đồng với mạng lưới Klaytn Baobab mà dùng truffles
5.5 Xác minh tài khoản UI 
Hãy bắt đầu bằng cách đăng nhập bằng tài khoản của bạn được tạo bằng ví baobab. Có hai cách để xác minh tài khoản của bạn. Đầu tiên, Bạn có thể sử dụng kết hợp keystore file và mật khẩu; thứ hai, xác minh bằng private key. Cách chúng tôi thực hiện là xác minh thông qua keystore file và mật khẩu. Đầu tiên, tôi sẽ viết code html. Truy cập Index.html và thêm nội dung bên trong body tag.
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
Hãy dừng video này ngay bây giờ và viết code này. Thiết lập rất đơn giản. Các lớp trong div sử dụng bootstrapping để làm UI trông đẹp. Tôi sẽ bỏ qua phần mô tả bootstrap. Trước hết, tôi sẽ giải thích ở phần trên. Dưới đây tôi đã thêm các nút đăng nhập và đăng xuất. Khi tôi nhấp vào nút đăng nhập, nó sẽ khởi động cửa sổ phương thức. Khi tôi nhấp vào nút đăng xuất chức năng handleLogout sẽ được thực hiện. Lưu ý rằng tôi đặt nút đăng xuất không xuất hiện trong css. Chúng ta chạy app và kiểm tra code chúng tôi đã viết có hoạt động không. Chạy lệnh npm run dev trên terminal. Chạy Chrome và truy cập localhost: 8081 địa chỉ. Vâng, nó không đẹp lắm, nhưng view có vẻ tốt. Bây giờ, hãy tạo một phương thức sẽ hiện lên khi chúng ta nhấp vào nút đăng nhập. ‘Https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals” Nếu bạn truy cập trang web bootstrap này, bạn có thể nhận được code phương thức. Sao chép phần này và quay lại tệp html. Tôi sẽ dán nó bên ngoài container div. Bây giờ hãy thay đổi nội dung của phương thức này. Đầu tiên, đặt id div thành loginModal.
Phương thức này sẽ mở khi bạn nhấn vào nút đăng nhập. Nó phù hợp với phương thức cùng với giá trị của thuộc tính dữ liệu của nút đăng nhập ở trên. Tiếp theo, chúng tôi sẽ thay đổi kích thước của phương thức trở nên nhỏ hơn.
 
Xóa tất cả các phần tiêu đề phương thức. Ngoài ra, xóa nội dung bên trong phương thức. Bây giờ thêm phần tệp keystore và mật khẩu.
 
Keystore
Nhớ loại đầu vào dưới dạng tệp và chức năng hanfleimport được gọi onchange event. Và dưới đây, thêm một phần cho mật khẩu (비밀번호).
 
Sao chép và dán lên trên cùng.
 
비밀번호
Nếu giá trị được ghi trong cửa sổ nhập mật khẩu,  có tên là handlePassword. Và tôi đã thêm phần được hiển thị dưới dạng tin nhắn khi xác minh thành công hoặc xảy ra lỗi. Cuối cùng, close thành 닫기(close) và thay đổi  safe changes thành submission. 닫기 제출
Thêm thuộc tính id và cho phép hàm handleLogin hiển thị khi nhấp vào.  Vâng, bây giờ tôi sẽ kiểm tra xem code vừa hoàn thành có hoạt động tốt trong chế độ xem hay không. Nhấp vào nút đăng nhập. Vậy thì, modal đã hoạt động và bạn có tùy chọn để chọn tập tin và nhập mật khẩu. Cho đến nay, tôi đã tạo UI xác minh tài khoản.
 
5.6 Logic xác thực tài khoản (xác thực Keystore)
Bởi vì chúng ta đã tạo UI được hiển thị ở trên, bây giờ thực hiện logic cho nó hoạt động. Trong Index.js, có nhiều hàm khác nhau trong constant app. Và cuối cùng, khi bạn kéo xuống, bạn sẽ thấy rằng điều đầu tiên khi bạn tải trang, bắt đầu start function trong constant app. Vì vậy, chúng tôi sẽ triển khai chức năng start, nhưng trước đó, chúng tôi cần tải  caver.js tương tác với blockchain Klaytn và khởi tạo nó để có thể sử dụng cho BApp.import Caver from "caver-js";
 
Ở đầu, nhập caver.js. Và tạo một hằng số cho việc thiết lập.
 
const config = {rpcURL: 'https://api.baobab.klaytn.net:8651'}
 
 rpcURL trong cấu hình. Chúng tôi đã xác định nút Klaytn nào kết nối và sử dụng. Tôi đã nói đó là baobab test net. Cuối cùng, chúng ta sẽ tạo hằng số khởi tạo rpcURL bằng cách chuyển nó đến Caver. const cav = new Caver (config.rpcURL);
 
Công việc khởi tạo đã kết thúc và hằng số cav này hiện có sẵn trong ứng dụng. Bây giờ bạn phải bắt đầu chức năng, nhưng trước đó, trước tiên bạn phải kiểm tra xem tài khoản đã được xác minh qua phiên hay chưa. Tuy nhiên, tôi sẽ nói phần này  sau vì chúng tôi sẽ sử dụng nó trong bài giảng sau, vì vậy bây giờ hãy để trống start function bây giờ. Trước tiên, hãy thực hiện chức năng handleImport. Chúng ta có thể nhấp vào nút đăng nhập và chọn tệp keystore sau khi modal hiển thị. Tuy nhiên, tệp này phải được xác thực cho dù có thực sự là tệp keystore hợp lệ hay không. Chúng ta hãy làm điều đó trong chức năng handleimport. Đầu tiên, chúng ta tạo FileReader và đặt nó trong constant. const fileReader = new FileReader ();
 
Và sử dụng chức năng readAsText để đọc tệp đã chọn. fileReader.readAsText (event.target.files [0]);
 
event.target.files, phần này có nghĩa là tệp chúng tôi đã chọn. Khi quá trình thực thi readAsText hoàn tất, việc tải FileReader đang xảy ra.fileReader.onload = (event) => {}
 
Nội dung của tệp, giờ đây có thể được sử dụng trong Block code này. Nội dung của tệp này sẽ được kiểm tra xem đó có phải là keystore hợp lệ hay không. Đầu tiên, thử lấy Block bên trong.
try {} catch (event) {}
Bây giờ chúng tôi sẽ kiểm tra liệu nội dung câu có hợp lệ hay không, nói cách khác, nếu đây là tệp keystore thực.if (!this.checkValidKeystore(event.target.result)) {}
 
Tôi đã chuyển nội dung của tệp mà chúng ta đã đọc cho hàm checkValidKeystore nhưu là đối số. Bây giờ hãy xem lại hàm checkValidKeystore. Hàm này lấy keystore làm đối số và nhận tệp. Và tệp keystore tôi nhận được là tệp json. Tôi sẽ thay đổi nó thành Javascript để sử dụng các thuộc tính trong tệp json này làm biến. const ParsedKeystore = JSON.parse (keystore);
 
Tôi đã sử dụng hàm json để phân tích nội dung của tệp keystore, chuyển nó thành object và lưu trữ nó trong hằng số. Chúng ta nên làm gì tiếp theo? Đảm bảo rằng các thuộc tính cần thiết cho cấu hình keystore nhập chính xác. Hãy xem tập tin keystore và xem những gì chúng ta cần. Các yếu tố thiết yếu của cấu hình keystore là phiên bản, id, địa chỉ và tiền điện tử. Nếu không có bốn trường này, nó không thể trở thành tệp keystore. Vì vậy, tôi sẽ kiểm tra nó thông qua code. const isValidKeystore = ParsedKeystore.version && ParsedKeystore.id && ParsedKeystore.address && ParsedKeystore.crypto;
 
Cuối cùng, quay lại hằng số này.returnisValidKeystore;
 
Tôi kéo lên trở lại và xác minh nếu tệp tôi vừa nhập là tệp keystore hợp lệ. Nếu không, tin nhắn thông báo không hợp lệ và kết thúc chức năng.
$('#message').text('유효하지 않은 keystore 파일입니다.'); return;
 
Nếu nó vượt qua bước xác minh, chúng tôi sẽ lưu nội dung của tệp keystore vào hàm biến toàn cầu. Đầu tiên chúng ta cần tạo nó trên chức năng start
auth: { accessType: 'keystore', keystore: '', password: '' },
 
Có ba trường trong trong Auth object. AccessType là phương thức xác minh, có loại keystore và private key. Chúng tôi đang tiến hành với loại keystore. Keystore lưu trữ toàn bộ nội dung của tệp. Cuối cùng, password là chứa mật khẩu sẽ kết hợp với tệp keystore. Nếu chúng ta quay trở lại chức năng và vượt qua bước xác nhận, sẽ hiển thị auth.keystore = event.target.result;
Gửi toàn bộ nội dung của tệp được tải đến keystore của biến auth mà chúng ta đã tạo. Sau đó, gửi tin nhắn nói rằng tôi đã thành công.$('#message').text('keystore 통과. 비밀번호를 입력하세요.');
 
Nhập mật khẩu trong trường password .
document.querySelector('#input-password').focus();
 
Cuối cùng, trong khi đọc tệp, nếu phát hiện lỗi, hãy gửi thông báo lỗi trong Block và ngừng chức năng này. $('#message').text('유효하지 않은 keystore 파일입니다.'); return;
Vâng, chức năng Handleimport thực hiện tốt. Hãy kiểm tra ngay bây giờ. Chọn tệp keystore. Thông báo mật khẩu sẽ được hiển thị và phần trọng tâm sẽ được chuyển đến phần có thể nhập mật khẩu. Để kiểm tra trường hợp ngược lại, hãy để chọn một tập tin ngẫu nhiên. Ok, thông báo lỗi được tạo ra nhưng nó vẫn hoạt động tốt. Bây giờ, hãy tạo chức năng lưu trữ mật khẩu trong hàm biến toàn cầu khi chúng ta nhập mật khẩu. Nó rất đơn giản. Nếu bạn truy cập html, handlepassword sẽ thông báo khi bạn nhập mật khẩu. Sau đó, tại handlepassword, this.auth.password = event.target.value;
 
Lấy mật khẩu thông qua html và sau đó, dán nó vào trường mật khẩu của hàm biến toàn cầu auth. Nó rất đơn giản. Nãy giờ, tôi đã thực hiện tệp xác thực tệp keystore. Trong bài giảng tiếp theo, tôi sẽ tạo một khóa bí mật và thêm thông tin tài khoản của tôi vào Ví.
 
5.7 Xác minh tài khoản (tích hợp ví)
Chúng tôi đã hoàn thành phần truy xuất tệp keystore và nhập mật khẩu, bây giờ chúng tôi sẽ kiểm tra xem tài khoản có được xác minh thành công hay không khi chúng tôi gửi thông tin này đến nút baobab. Trước đó, tôi sẽ thay thế http trong rpcURL thành https. Hãy xem Index.html. Khi tôi nhấp vào nút gửi, nó gửi đến hàm handlelogin. Vì vậy, hãy thực hiện chức năng. Đầu tiên, hãy chắc chắn rằng accesstype là keystore. if (this.auth.accessType === 'keystore') {}
 
Lý do chúng tôi viết câu nà sử dụng “if” là khi xác minh tài khoản, chúng tôi sử dụng keystore hoặc private key. Bây giờ chúng tôi chỉ sử dụng keystore. Tuy nhiên, tôi đã thêm các câu lệnh if này để khi bạn muốn sử dụng private key để xác minh, bạn có thể sử dụng nó. Hãy thử bắt câu ngay bên dưới.
try {} catch (e) }
Hãy sử dụng caver. Tôi sẽ đưa ra câu hỏi cho bạn. Chúng ta có thể kiếm được gì từ sự kết hợp của tệp keystore và mật khẩu? Nếu bạn nhớ tốt, bạn có thể biết ngay. Có, bạn có thể nhận secret key của bạn. Nó cho phép bạn tạo Ví. Vì vậy, điều đầu tiên bạn cần làm là lấy secret key thông qua tập tin keystore và mật khẩu.
const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;
 
Bạn có thể sử dụng chức năng giải mã thông qua tài khoản của caver instance. Nó có nghĩa là decrypt. Nếu bạn decrypt nó, bạn có thể trở về  ài khoản decrypt bằng cách chuyển nội dung của tệp keystore và mật khẩu làm đối số. Có nhiều thành viên khác nhau trong đối tượng và trong số đó, chúng tôi nhận được private key và lưu trữ nó trong hằng số.
Nếu có lỗi sai trong decrypt, tin nhắn sẽ thông báo.  $('#message').text('비밀번호가 일치하지 않습니다.'); $(‘#message’).text(‘password is not matched.’);
Nếu không có lỗi, nó sẽ tạo ví thông qua secret key của bạn.
this.integrateWallet(privateKey);
Truyền private key cho integwallet. Bây giờ, truy cập chức năng integwallet. Chúng tôi thêm code để lấy Ví instance bằng cách sử dụng privatekey.
const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);
 
walletinstance có thông tin tài khoản của tôi. Sau đó thêm instance này vào Ví của tôi.cav.klay.accounts.wallet.add(walletInstance)  
Tôi đang gửi Ví instance cho chức năng ChangeUI. Vậy chúng ta phải làm gì với chức năng ChangeUI? Đóng lại modal.
$('#loginModal').modal('hide');
Che giấu nút đăng nhập.$("#login").hide();
Cũng thay đổi nút thoát mà bạn che giấu trước đó.
$('#logout').show();
Và vì bạn đã đăng nhập, tôi muốn địa chỉ tài khoản hiển thị $('#address').append('
' + '' + '내 계정 주소: ' + walletInstance.address + '');
Mã code này cho tôi biết rằng nó là địa chỉ tài khoản trong html trong đó thuộc tính id là địa chỉ. Tôi sẽ truy cập  index.html và thêm div.
 
Vâng, bạn có thể thấy địa chỉ tài khoản của tôi tại vị trí này. Tôi sẽ thực hiện tại đây. Bây giờ hãy kiểm tra nó. Nhấp vào nút Đăng nhập và mở tệp keystore. Nếu bạn nhập mật khẩu và nhấn nút gửi, tài khoản của bạn sẽ được xác minh và nút đăng xuất xuất hiện. Dưới đây bạn có thể thấy địa chỉ tài khoản của tôi. Cuối cùng, hãy thực hiện chức năng để đăng xuất. Truy cập Index.html. Lưu ý rằng khi tôi nhấp vào nút đăng xuất, tôi gửi đến hàm handlelogout. Ở đây chúng ta sẽ gọi hàm là removeWallet. this .removeWallet ();
 
Chúng tôi sẽ xóa ví và xóa bộ lưu trữ với chức năng này. Truy cập hàm removeWallet và thêm mã code này. cav.klay.accounts.wallet.clear ();
 
Đây là quá trình xóa Ví instance của tôi: thông tin tài khoản đã được thêm vào ví. Sau đó xóa phiên này. sessionStorage.removeItem('walletInstance');
 
Khi bạn xóa nó, chỉ cần nhập giá trị key. Cuối cùng, nó sẽ gửi tới chức năng reset và kết thúc. this .reset ();
Chức năng reset lại này chỉ đơn giản là khởi tạo biến toàn cầu auth. Truy cập chức năng reset và khởi tạo auth.this.auth = { keystore: '', password: '' };
 
Ngoài ra còn có một accesstype trong Auth. Nhưng, bạn không phải xóa accesstype vì dù sao nó cũng sẽ là keystore. Thay vào đó, khi chúng tôi đăng nhập, một giá trị sẽ được nhập vào keystore và mật khẩu. Tôi muốn đăng xuất và xóa nó một cách an toàn. Quay trở lại chức năng handleLogout và đặt code làm mới trang và hoàn thành nó. Lý do cho việc làm mới là để trở về giao diện người dùng trạng thái ban đầu. location.reload ();
 
Bây giờ hãy thử nghiệm và kết thúc nó. Nhấp vào nút Đăng xuất, thông tin tài khoản sẽ biến mất và bạn được đưa trở lại màn hình khởi tạo bằng cách làm mới nó. Bây giờ bạn hoàn thành logic xác minh tài khoản của mình, hãy hoàn thành phần phần này mà xác minh tài khoản thông qua lưu trữ phiên trong lớp tiếp theo.
5,8 Phiên tài khoản
Hãy xem điều gì xảy ra khi chúng ta đăng nhập và làm mới trang. Nhấp vào nút đăng nhập và chọn tệp keystore.Nhấn F5 để làm mới. Sau đó, nó sẽ được thiết lập lại. Sẽ tốt hơn nếu tôi tiếp tục đăng nhập. Làm thế nào để tôi làm điều đó? Nếu chúng tôi đăng nhập thành công, chúng tôi đã lưu thông tin lưu trữ tài khoản vào bộ lưu trữ phiên. Tôi sẽ sử dụng nó bây giờ. Hàm đầu tiên được tải khi BApp chạy là hàm start. Ở đây tôi lấy thông tin tài khoản của tôi được lưu trữ trong bộ lưu trữ phiên. Vì thế, chúng ta hãy truy cập chức năng start, const walletFromSession = sessionStorage.getItem('walletInstance'); 
Nếu bạn sử dụng getItem và chuyển giá trị của key, giá trị đó sẽ được tìm nạp và lưu trữ trong constant. Tôi đã lưu Ví constant của tôi. Tiếp theo, hãy đảm bảo WalletFromSession chứa giá trị  if (walletFromSession) {}
 
Nếu có giá trị, tạo ra try catchtry {} catch (e) {}
Sau đó thêm thông tin tài khoản của bạn trở lại ví caver. cav.klay.accounts.wallet.add (JSON.parse (víFromSession));
 
Khi trang được làm mới hoặc truy cập lại, thông tin tài khoản hiện được thêm vào Ví sẽ bị xóa, vì vậy tôi thêm nó trở lại qua phiên này. Cập nhật giao diện người dùng (UI) để hiển thị rằng bạn đã đăng nhập như tiếp theo. this .changeUI (JSON.parse (WalletFromSession));
 
Nó sẽ chuyển thành nút đăng xuất và cho tôi xem địa chỉ tài khoản của bạn.
Cuối cùng, khi giá trị trong sessionStorage không phải là Wallet instance hợp lệ, nó sẽ chuyển đến câu lệnh catch. Sau đó xóa walletinstance trong bộ lưu trữ phiên. sessionStorage.removeItem ('WalletInstance');
 
Nó đã được thực hiện bước này. Bây giờ, hãy để thử nghiệm nó. Khi bạn làm mới, nó sẽ tiếp tục đăng nhập mà không trở về trạng thái khởi tạo. Nãy giờ, chúng tôi đã thực hiện một phần của việc duy trì xác minh tài khoản.
 
5,9 KLAY chuyển qua hợp đồng (ký gửi)
Bây giờ tôi sẽ gửi KLAY đến hợp đồng bằng tài khoản nhà điều hành. Đầu tiên, hãy tạo một giao diện người dùng. Bạn có thể tạo nó dưới hàng div class
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
 
Vui lòng làm mờ video và thêm phần này. Tôi sẽ giải thích ngắn gọn. Tôi đã thiết lập phần UI để gửi tiền vào hợp đồng vô hình thông qua css. Chúng tôi đã thiết lập chức năng gửi tiền để chạy khi chúng tôi nhập số tiền và nhấn nút chuyển. Bây giờ hãy đến chức năng gửi tiền và thực hiện nó.
 
Tôi sẽ giải thích ở đây làm thế nào để thực hiện nó đầu tiên. Chuyển Klay sang hợp đồng chỉ có thể được thực hiện với tài khoản chủ sở hữu. Điều này chỉ có thể với tài khoản của người đã triển khai Hợp đồng. Nói cách khác, chỉ có người tổ chức có thể gửi nó. Nếu chúng tôi đang sử dụng tài khoản chủ sở hữu, chúng tôi sẽ truy cập chức năng ký gửi trong hợp đồng và chuyển khoản KLAY. Quy trình rất đơn giản. Đầu tiên, chúng tôi sẽ tạo hàm instance để chúng tôi có thể truy cập vào hợp đồng mà chúng tôi đã triển khai. Khi bạn tạo hợp đồng instance, bạn cần thông tin abi và địa chỉ của hợp đồng bạn đã triển khai. Trong các hằng số cav ở trên cùng, const agContract = new cav.klay.Contract (DEPLOYED_ABI, DEPLOYED_ADDRESS);
 
Ở deployed_abi và deployed_address là các hằng số toàn cầu có thể được sử dụng trong BApp. Khi chúng tôi triển khai hợp đồng, chúng tôi lưu thông tin vào tệp đã triển khai và tệp được triển khai. Đặt nó trong gói web để chúng ta có thể đọc thông tin này và nó sử dụng nó như một hằng số toàn cầu. Nếu bạn truy cập tệp Webpack.config.js, sẽ có một phần chú thích. Giải quyết điều này ngay bây giờ. Tại thời điểm biên soạn  trong các gói web, hãy chạy phần này để đặt các hằng số toàn cầu được gọi là deployed_address và abi 
 
Nói một cách đơn giản, chúng ta đọc tệp được triển khai thông qua hệ thống tệp và gán địa chỉ hợp đồng cho hằng số toàn cầu. Theo cách tương tự, chúng tôi lưu trữ thông tin abi trong các hằng số toàn cầu có trong tệp triển khai. Hãy để lại cho tập tin Index.js.
 
Vì vậy, hãy nhớ rằng hai abi và thông tin địa chỉ được gửi cho người tạo ra hợp đồng instance chuyển qua các hằng số toàn cầu được tạo bởi gói web. Bây giờ chúng tôi đã tạo hợp đồng instance thứ bốn, chúng tôi sẽ tiếp tục với chức năng gửi tiền. Có một cái gì đó chúng ta phải kiểm tra trước khi gửi tiền. Bạn nên xác minh rằng tài khoản bạn vừa đăng nhập là tài khoản chủ sở hữu. Vì vậy, tôi phải đưa ra hai mẫu thông tin. Đầu tiên, tôi đang truy xuất thông tin tài khoản hiện đang đăng nhập. Thứ hai, tôi sẽ lấy biến trạng thái chủ sở hữu được lưu trong hợp đồng. Đầu tiên, tôi sẽ lấy thông tin đăng nhập của tôi. const WalletInstance = this.getWallet ();
Chuyển đến chức năng getwallet và nhận thông tin tài khoản trong ví caver hiện tại
 if (cav.klay.accounts.wallet.length) { return cav.klay.accounts.wallet[0]; }
 
Wallet [0] là tài khoản đầu tiên được thêm vào Wallet, tài khoản tôi hiện đang đăng nhập. Bạn đã hoàn thành chức năng thực hiện nãy g. Tiếp theo, hãy gửi giá trị của biến trạng thái của chủ sở hữu trong hợp đồng. Chuyển đến hàm callOwner trả về await agContract.methods.owner (). Call ();
