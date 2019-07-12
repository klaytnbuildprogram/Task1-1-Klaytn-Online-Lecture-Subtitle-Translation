# 5. 클레이튼 덧셈 게임 프론트엔드 개발

## 5.1 설정

앞선 강좌들을 통해 bApp에 쓰일 컨트랙트를 만들었으니까요 이제 프론트엔드 개발을 해보겠습니다.
먼저 기본적인 환경설정을 진행하도록 할건데 이 강좌에서는 node.js, npm, truffle 프레임워크 그리고 비쥬얼 스튜디오 코드를 다운받아 보겠습니다. 
node.js는 서버사이드 자바스크립트 플랫폼인데 우리가 만들 BApp에서 꼭 필요합니다.
npm은 node.js 설치하면 같이 설치되는데요 개발하면서 툴이나 라이브러리를 다운받기 위해 꼭 필요한 존재이구요.
우리가 설치할 truffle 프레임워크도 이 npm을 통해서 다운받아야 합니다.
혹시 이미 node.js와 npm이 설치 되어 있으면 버전을 확인하시고 node.js가 버전 8 이상이고 npm이 버전 5 이상이면 이 부분 스킵하셔도 됩니다.

nodejs.org로 오셔서 오늘 강좌 촬영 기준으로 10.15.3 LTS가 최신 버전이구요. 
자 이거 클릭하셔서 다운 받으시면 됩니다.
다운 다 받으면 설치해주시구요.
저는 이미 설치가 다 되어서 이 부분 스킵하도록 하겠습니다.

설치 끝나셨으면 파워셸에서 node.js가 잘 설치되었는지 확인해 볼 건데요.
자 파워셸을 키겠습니다.
네 파워셀에서 node -v 치시고 버전 확인 하시구요
npm도 확인해 보겠습니다. npm -v
네 그러면 npm도 설치가 잘 되었죠.

마지막으로 truffle을 설치해 볼건데요 truffle은 bApp을 쉽게 개발할 수 있도록 도와주는 프레임워크입니다.
스마트 계약을 컴파일하고 테스트하며 배포도 할 수 있게 해주죠.
아주 많이 쓰고 있는 대중화된 프레임워크입니다.
최근에 트러플 버전이 5로 업데이트 되었구요.
하지만 클레이튼이 버전 4에 맞춰져서 개발이 됬기 때문에 일단은 truffle 버전 4에 맞춰서 진행하겠습니다.
버전 4 이하거나 5가 이미 설치되어 있다면 먼저 지우도록 하겠습니다.
파워셸에서 npm uninstall -g truffle 치셔서 지우시면 되구요.
자 그리고 이제 npm install -g truffle@4.1.15 치셔서 자 버전 4를 받겠습니다.
네 다 받으시면 truffle version 커맨드를 통해 버전을 확인하시구요.
네 그러면 4.1.15 버전이고 밑에 솔리디티는 이 컴파일러는 0.4.25 버전이라고 합니다.
솔리디티는 스마트 계약을 작성할 수 있는 프로그래밍 언어이구요.

네 마지막으로 최고의 코드 에디터인 비쥬얼 스튜디오 코드를 다운받아 보겠습니다.
code.visualstudio.com으로 오셔서 여기에 Download for Windows 클릭하시고요.
저는 이것도 미리 다운 받아서 스킵하겠습니다.
다운 다 받으시면 설치하고 실행시켜 주시구요.

비주얼스튜디오 코드는 크로스 플랫폼이 지원되서 리눅스, 윈도우즈, 맥에서 다 돌아가고 디버깅 지원과 깃 제어, 구문 강조 기능 등 여러가지 편리한 기능들이 포함되어 있습니다.
네 비쥬얼 스튜디오 코드에서 여기 확장탭 클릭해 주시구요.
여기에서 솔리디티 언어 서포트 되는 익스텐션 하나 설치해보도록 하겠습니다.
여기다가 solidity 치시고 맨 위에꺼 선택해 주세요.
설치 클릭합니다.
이 익스텐션은 솔리디티 문법마다 강조되는 색깔을 제공하고 또 컴파일도 할 수 있게 해줍니다.
네 설치가 완료 되었구요 여기까지의 프론트엔드 개발에 필요한 환경 설정을 끝내도록 하겠습니다.

## 5.2 기본 템플릿(boilerplate) 다운로드

개발을 위한 보일러 플레이트 즉 기본 템플릿을 다운받아 보겠습니다.
클레이튼 비앱이 트러플 프레임워크에서 개발될 수 있다고 했었죠.
트러플에서 비앱 개발에 필요한 표준 템플릿들을 다운 받을 수 있게 해준 곳이 있습니다.
트러플 박스라고 하는데요
이곳으로 오시면은 여러가지 종류들을 볼 수 있습니다.
예를 들어, 앵귤러나 리액트를 사용해서 비앱개발 하고 싶으면 거기에 맞춰진 템플릿을 다운받으시면 됩니다.
자 여기 보시면은 리액트도 있구요 또 앵귤러 사용하시는 분들은 또 앵귤러 템플릿 다운받으시면 됩니다.
하지만 여기에서 다운받는 템플릿들은 이더리움 디앱에 특화됬기 때문에 다운받으시고 안에 있는 이더리움 부분들을 지우셔야 합니다.
그리고 클레이튼에 맞게 설정하셔야 하구요.
그닥 어려운 부분은 아니지만 제가 여기서 미리 웹팩이라는 템플릿을 다운받고 우리 강좌에 맞게 클레이튼 식으로 바꿨습니다.
그리고 여러분들이 다운받으실 수 있도록 깃허브에 올려놓았구요.
참고로 저희는 공평성을 위해 자바스크립트 네이티브와 제이쿼리로 진행하겠습니다.
처음 접하셨더라도 쉽게 따라하실 수 있구요.
파워셸을 여시고 다운받고 싶은 위치에서 git clone https://github.com/kkagill/addition-game-starter.git 커맨드를 실행합니다. 
그러면 다운받구요.
네 다운로드 받았구요 해당 경로로 들어가겠습니다.
cd addition-game-starter
네 이제 code .을 쳐서 구조를 보도록 하겠습니다.
이게 비쥬얼 스튜디오 코드로 여는거 구요.
자 먼저 위에서부터 차근차근 확인하도록 하죠.
이 컨트랙트 폴더에는 솔리디티 컨트랙트 파일들을 보관하는 곳이구요.
우리가 만들었던 AdditionGame 컨트랙트가 미리 추가가 되어 있구요.
그리고 아래 Migrations라는 컨트랙트가 있는데 이게 스마트 계약을 배포할 때 아래에 있는 migrations폴더 안에 있는 이 스크립트 파일들을 지금 하나지만 나중에는 하나더 생길거에요.
그파일들을 실행하게 합니다.
그래서 이 Migrations 파일이 정말 중요해요 배포하는데 꼭 필요한 파일이니까 절대 지우시면 안되구요
그다음에 migration 폴더 안에 있는 스크립트 파일, 이 파일에는 배포하는 과정에 쓰이는 로직이 담겨 잇습니다.
이 파일 보시면 마이그레션스 컨트랙트 파일을 불러와서 그내용을 클레이튼 노드에 디플로이 즉 배포를 하죠, 그런 역할이구요.
이제 소스 폴더 안에는 비앱의 프론트엔드를 담당하는 구조를 설정했습니다.
index.html파일은 앞에 보여주는 뷰를 담당할 거 구요.
여기 보시면 비앱에 쓰일 제이쿼리나 부트스트랩을 cdn으로 불러오고 그리고 맨 아래에는 css 부분을 미리 추가해 놓았습니다.
별로 중요하지 않은 파트라서 미리 추가 했구요.
index.js 파일은 기능들을 실행하기 위한 엔진과 같은 파일입니다.
우리가 앞으로 쓰게 될 함수들 이름들만 이렇게 미리 정의해 놓았구요.
맨 아래에 있는 이 옵션 opts 변수는 로딩할 때 스피너 보여주는 환경 설정 변수입니다.
이것도 중요한 부분이 아니라서 미리 추가를 했구요.
package.json은 npm을 통해 필요한 디팬던시를 추가한 곳 입니다.
중요하게 보셔야 할 것이 caver.js, 즉 클레이튼 블록체인과 소통하게 해주는 라이브러리 파일들을 다운 받은 거구요 ethereum의 web3.js비슷한 존재 이죠
truffle.js는 환경 설정을 담당하는데요 어느 네트워크에 스마트계약을 배포할지 여기다가 정의를 하는 겁니다. 
다음 강좌에서 내용들을 추가하도록 하구요
마지막으로 이 webpack.config.js 파일은 파일들을 최적화 시켜주고 또 코드의 변화가 있을 때마다 감지를 해서 브라우저에 변경사항을 새로고침 할 필요없이 반영해 주는 역할을 합니다.
여기까지 클레이튼 덧셈 비앱을 만듥기 위한 스타터 템플릿을 다운 받고 구조도 설명해 드렸습니다.

## 5.3 바오밥 테스트넷에 스마트 컨트랙트 배포하기 1

지금부터 바오밥 테스트넷에 우리가 만든 AdditionGame 스마트 계약을 배포해보도록 하겠습니다.
시작하기 전에 터미널에서 npm install 커맨드를 실행하고 비앱에 필요한 디펜던시를 설치하겠습니다.
아래 터미널  안보이시는 분들은 위의 터미널 탭에서 새 터미널을 선택하시면 되구요.
이제 npm install 커맨드를 실행시킵니다.
살짝 시간이 걸리고요 끝나면 node_modules라는 폴더가 생기면서 디펜던시 설치가 완료됩니다. 
이거 끝나고 다시 돌아오도록 하겠습니다.
네 설치가 완료되었습니다.
먼저 마이그레이션즈 폴더안에 새로운 파일 하나 만들어 보죠
여기서 오른쪽 클릭하시고 새 파일 선택합니다.
이름은 2_deploy_contracts.js라고 하시면 되구요.
네 여기에다가 AdditionGame 컨트랙트를 노드에 배포하는 로직을 추가할 겁니다.
그러면 1_initial_migration.js 파일로 가셔서 이거 코드 다 복사하세요.
컨트롤 c 누르시ㅣ고 다시 이쪽 온 다음에 붙여넣기 하겠습니다.
위에 Migrations.sol 이거 AdditionGame.sol로 바꿔 주시고요.
이제 AdditionGame 컨트랙트를 가져온다고 변경을 하는거죠.
자 이름도 바꿔 주시고 아래의 디플로이 여기 받는 인자도 AddtionGame으로 바꿔 줍니다.
여기까지 하면 간단하게 배포하는 기본적인 로직은 끝났어요.
하지만 배포하는 과정에서 얻을 수 있는 몇가지 정보들을 비앱내에 어떤 파일들에다가 저장하는 코드를 작성할 겁니다.
나중에 그 정보 가지고 컨트랙트 인스턴스 만드는데 아주 유용하게 쓸 수 있구요.
자 그래서 여기 아래다가 deployer가 AdditionGame 컨트랙트를 deploy하고 나서 then을 통해 Promise로 json 데이터를 받습니다. 
자 then
그리고 이 안에다가

if (AdditionGame._json) {

AdditionGame의 json 데이터를 받았다면 파일 시스템 모듈을 통해 파일에다가 저장할 겁니다.
그러기 위해서는 import 시켜야 되구요. 
맨 위에다가 const fs = require('fs') 파일 시스템을 추가합니다.
자 그리고 두개의 파일을 만들거에요.
abi와 컨트랙트 주소를 저장할 수 있는 곳인데요.
여기 밖에다가 오른쪽 클릭하시고 새 파일 선택합니다.
이름은 deployedABI라고 하구요 또하나 만드셔서 이름은 deployedAddress 주소죠 라고 하시구요.
이제 파일 시스템을 써서 각각의 파일들에다가 저장을 하겠습니다.
먼저 abi의 정보를 저장하는 코드를 만들어보죠
abi는 블록체인과 컨트랙트 간의 상호작용을 할 수 있는 내용입니다.
자 다시 여기로 가셔서 if 안에 다가 

fs.writeFile(
    	'deployedABI',
    	JSON.stringify(AdditionGame._json.abi),
 
설명하죠
파일시스템 안에 writeFile 함수가 있는데 두가지를 넘기죠.
첫번째는 어떤 파일에다가 이거를 쓸건지 정의를 해 주고 두번째로는 json 파일, json으로 받은 abi의 정보를 스트링화 시켜서 이렇게 인자로 넘기는 겁니다.
마지막으로 에러처리 하겠습니다.
에러가 났을 때는 throw를 해라 아니면 콘솔에다가 성공했다고 메세지를 쓰죠.

(err) => {
    if (err) throw err
    console.log("파일에 ABI 입력 성공");
})

에러가 있으면 throw 하고 없으면 콘솔에다가 로그를 찍겠습니다.
이렇게 하면 이 deployedABI 파일에 배포된 컨트랙트의 abi 정보가 문자화 되어서 저장이 되는 거고요.

계속해서 배포된 컨트랙트 주소도 파일에다가 저장하겠습니다.
여기 아래에다가

fs.writeFile(
  	'deployedAddress',
  	AdditionGame.address,
  	(err) => {
    	if (err) throw err
    	console.log("파일에 주소 입력 성공");
	})

이번에는 주소입니다. 그리고 에러처리 하구요. 에러가 나면 자 throw하고 아니면 콘솔을 찍어라. 파일에 주소 입력 성공.

네 여기까지 하면은 매번 배포할 때, 저희가 원하는 정보들을 각 파일에다가 바로 저장할 수 있게 되었습니다. 
계속해서 다음 강좌에서 truffle.js안에다가 환경설정을 하고 배포 하겠습니다.

## 5.4 바오밥 테스트넷에 스마트 컨트랙트 배포하기 2

이제 마지막으로 환경설정을 해야되는데요.
배포를 할 때, 어느 네트워크에다가 할껀지 정의해야합니다.
truffle.js 파일로 가시구요. 여기에다기 이제부터 정의를 하겠습니다.
먼저 connect-privkey-to-provider 라는 라이브러리를 가져오구요.

const PrivateKeyConnector = require('connect-privkey-to-provider')

그리고 network ID라는 상수도 만듭니다.

const NETWORK_ID = '1001'

이 1001은 바오밥 고유의 network ID를 의미하구요.  

const GASLIMIT = '20000000'

배포하는데 들어가는 가스 한도를 이정도 줍니다.
0이 총 7개 이구요.

자 다음으로 

const URL = `https://api.baobab.klaytn.net:8651`

URL은 클레이튼 풀노드가 현재 돌아가고 있는 주소를 대입했습니다.
바오밥 테스트넷이구요.

마지막으로 비밀키를 담는 상수가 필요한데 우리가 예전에 클레이튼 월렛을 통해 생성했던 계정의 비밀키를 가져오겠습니다.
제가 예전 강좌에서 비밀키 다른 곳에 저장하시라고 했었죠.
저는 메모장에 저장했던 것을 복사해서 붙여넣기 하겠습니다.

const PRIVATE_KEY = ''

자 저는 붙여 넣었구요.
이제 이 설정들을 module.exports 안에다가 사용해보겠습니다.
설명을 해 드리도록 하죠.
자 여기 네트워크는 klaytn을 쓴다고 했고요
그리고 이 안에다가 네 가지 옵션들을 명세합니다.
먼저 provider 즉 클레이튼 노드를 제공하는 공급자를 명시하는 건ep
private-key-connector 인스턴스를 생성하고 2개의 인자들을 넘깁니다.
첫번째는 내 계정 비밀 키를 넘기고 두번째는 풀노드가 돌아가고 있는 네트워크 주소를 넘기구요.
이렇게 하면 내 비밀키를 사용해서 바오밥 테스트넷에 연결할 수 있게 되는 겁니다.
그다음으로 네트워크 id,그리고 gas대입하고 마지막으로 gas price 즉 가스 가격은 여기다 null 값을 주는데 이거는 바오밥 네트워크에서 자동적으로 가스 가격을 잡아주기 때문에요 이렇게 null 값을 넘기는 겁니다.
여기까지 스마트 계약을 배포할 수있는 환경 설정을 마쳤구요.
나름 간단했죠. 이제 배포를 해보겠습니다.
아래 터미널에 truffle deploy --network klaytn 자 이거를 실행을 합니다.
자 그러면 클레이튼 네트워크에 배포를 하게 되구요.
배포하는데 조금 시간이 걸리지만 금방 될겁니다.
성공적으로 배포를 했구요.
여기 콘솔로 찍힌 이 성공 문구 표시가 있죠.
제가 예전에 했던거 이렇게 나오면서 이제 deplyedABI 파일 가보시면은 여기에 abi정보가 저장되어 있죠.
그리고 deployedAddress 가 보시면 배포된 컨트랙트의 주소가 이렇게 저장되었습니다.
잘 작동하네요.
마지막으로 배포를 하게되면 이 위에 build라는 폴더가 생성이 되는데요 그안에 contracts폴더가 있고 또 그안에 2개의 json파일들이 있죠.
얘네들 영어로 artifact라고 하는데요.
자 각각의 artifact 파일은 해당 컨트랙트의 abi의 정보와 추가적으로 컨트랙트와 관련된 모든 정보들을 담고 있습니다.
자 여기 abi 우리가 아깐 deployedABI 파일에다가 따로 저장한 내용이에요.
abi는 application binary interface의 약자입니다.
이안에 보시면 우리가 AdditionGame 컨트랙트에서 쓰는 함수들과 변수들이 이렇게 json 형식으로 나타냈습니다.
이게 간단하게 말해서 블록체인의 이 컨트랙트를 배포했을때 그 컨트랙트에 있는 함수들을 호출하고 또 데이터가 내가 예상했던 형식으로 리턴될 수 있도록 보장하는 겁니다.
컨트랙트와 상호 작용할 수 있는 방법을 정의한 곳이에요.
맨 아래쪽으로 내려가 보시면은 엄청 길거든요 쭉 땡겨서 아래로 가보시면
여기에 네트워크 섹션 있죠, 여기 보면은 1001 이거는 클레이튼 고유의 네트워크 id라고 했었죠.
그리고 밑에 있는 address는 이 컨트랙트의 현제 바오밥 테스트넷에 지금 이 주소로 배포가 되어 있다라는 겁니다.
마지막으로 클레이튼 노드의 컨트랙트를 재배포하고 싶을 때, 이 커맨드를 사용하면 됩니다.
예를 들어서 우리가 컨트랙트을 수정해야 되는데 그러면 노드에다가 재배포 해야겠죠
그럴때 truffle deploy -compile-all -reset -network klaytn
여기 -compile-all은 모든 컨트랙트를 재컴파일 시키구요 -reset은 migrations 폴더 안에 있는 스크립트 파일들을 강제적으로 다시 실행시킵니다.
그러면 실행시켜보죠.
실행을 시키면 노드에 컨트랙트를 다시 재배포 하구요.
네 거의 완성이 되면서 성공적으로 마쳤습니다.
자 deployedAddress 파일 열어보시면 주소가 바뀌어 있다는 걸 확인하실 수 있을 거에요.
이렇게 배포를 할 때마다 주소가 계속 바뀌는 겁니다.
여기까지 truffle을 이용해서 컨트랙트를 클레이튼 바오밥 네트워크에 배포해 보았습니다.
 
## 5.5 계정 검증 UI

바오밥 월렛을 통해 만들어진 계정으로 로그인을 해보는 부분을 지금부터 시작해 보도록 하겠습니다.
우리가 계정 인증하기 위한 방법이 두가지가 있었죠.
키스토어 파일과 비밀 번호 조합을 사용하는 것과 프라이빗 키, 즉 비밀 키를 사용해서 인증하는 방법이 있습니다.
저희가 구현할 방법은 키스토어 파일과 비밀번호 조합을 통해 인증할 건데요.
먼저 html 코드를 작성하겠습니다.
index.html 파일로 오셔서 여기 바디 태그 있죠. 여기 안에다가 내용을 추가할 껀데
일단 먼저 추가 했구요. 여러분들 지금 이 영상 멈추고 코드 작성해 주시기 바랍니다.

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

아주 간단한 세팅인데 제가 설명해 드릴게요.
위에서부터 이 class 안에 container나 row나 col-md-8, text-center 이런 애들은 ui를 이쁘기 위해 부트스트랩을 사용하는 거구요.
이게 별로 중요한게 아니라서 부트스트랩에 대한 자세한 설명은 건너 뛰도록 하겠습니다.
우선 윗부분에는 이렇게 설명하는 문구들을 넣었구요.
아래쪽에는 로그인 버튼과 로그아웃 버튼을 추가를 했습니다.
로그인 버튼을 클릭했을 때, 모달창을 띄울거 구요.
로그아웃 버튼을 클릭했을 때에는 이 handleLogout() 함수를 실행시킬 겁니다.
참고로 로그아웃 버튼은 여기 있는 css 부분을 통해 안보이게 세팅을 해두었구요.
일단 앱 실행해서 우리가 작성한 코드가 잘 나오나 확인해 보겠습니다.
터미널에 npm run dev 커맨드 실행시키시구요.
그리고 브라우저 하나 열어서 여기서 localhost:8081 입력하시고 오시면 됩니다.
그러면 그렇게 아름답지는 않지만 보기 괜찮은 뷰가 렌더링 됬습니다. 
이제 로그인 버튼을 클릭했을때 뜨게 되는 모달을 작성해 볼건 데요.
이 사이트로 오시면은 부트스트랩 사이트입니다. 제가 이걸 링크 걸어드릴게요. 'https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals'
자 여기서 모달 코드를 가져올 수가 있는데 아래쪽으로 내려가 보시면은 이 부분이에요.
여기 있는거 다 복사해 옵니다. 
복사하시고 다시 html파일로 오셔서 이 container div 바깥쪽에다가 붙여넣습니다. 이렇게요.
이제 이 모달 안에 있는 내용들을 변경을 해 보겠습니다.
먼저 여기 맨 위쪽에 div id를 loginModal로 설정하겠습니다.

<div class="modal fade" tabindex="-1" role="dialog" id="loginModal">

네 이렇게 해야 로그인 버튼 클릭했을 때 이 모달이 열릴 수 있어요.
위쪽 로그인 버튼 이 data-target 속성 보시면은 loginModal 이라고 했죠.
자 이 값과 지금 서로 매칭을 해주는 겁니다. 그렇죠 이렇게 해야 열릴 수 있구요.
자 그 다음으로는 모달의 크기를 작은걸로 좀 바꾸겠습니다.
여기다가 modal-sm, 그리고 이 modal-header 부분은 지우시고요. 네 다 지웁니다.
그리고 modal-body 안에도 이 내용 지금 지우구요.
네 이 modal-body 안에다가 이제 keystore 파일 불러올 수 있는 부분이랑 비밀번호 입력하는 부분 추가할 건데요.
자 이렇게 해 주십니다.

<div class="form-group">

자 부트스트랩 사용해서 이쁘게 만들거구요.
레이블 하나 추가합니다.

<label for="keystore">Keystore</label>

자 인풋 하나 추가하구요.

<input type="file" id="keystore" onchange="App.handleImport()">

여기까지 하면 됐구요. 다시한번 설명을 하면은 input 타입은 file 그리고 onchange 이벤트를 통해 index.js 파일 안에 있는 handleImport() 함수를 실행시킵니다.
그리고 그 밑에 비밀번호 입력할 수 있는 부분도 추가할 껀데 자 form-group 바로 아래다가 이거 일단 복사를 할게요.
똑같은 복사하시고 붙여넣구요. 그다음에 이름만 좀 변경을 하겠습니다.
자 label for에는 input-password로 바꾸어 주시구요.
여기는 비밀번호 타입은 비밀번호겠죠. password
자 그리고 부트스트랩을 써서 좀 이쁘게 만들겠습니다.
id는 input-password 자 여기도 onchange 이벤트를 사용할껀데 이번에는 handlePassword() 함수를 불러올껍니다. 호출할 꺼구요.
마지막으로 p 섹션 하나를 추가를 하죠.

<p class="help-block" id="message"></p>

네 자 이 부분이 지금 인증을 통과했거나 에러났을 때, 메세지로 보여주는 부분을 추가한 거 구요.
마지막으로 footer에 Close는 닫기로 바꿔주시고 그리고 save chages는 제출로 바꿉니다.
그리고 이 부분에 id 속성 하나 추가 하는데요. submit라고 하고 onclick 이벤트를 또 실행시킵니다.
클릭했을 때 handleLogin()이라는 함수를 호출을 할꺼구요.
자 이제 완성된 코드가 뷰에서 잘 작동하나 확인해 보겠습니다.
다시 이쪽으로 가셔서 로그인 버튼 클릭해보구요.
그러면 모달이 뜨고 파일 선택할 수 있는 옵션과 비밀번호 입력할 수 있는 부분이 잘 생성됬습니다.
여기까지 계정 인증하는 ui를 만들어 보았습니다.

## 5.6 계정 검증 로직(키스토어 확인)

앞에서 보여지는 ui를 만들었으니 이제 작동하게끔 로직을 구현해보도록 하죠.
index.js 파일로 가시면은 위에 App이라는 상수고 있구요 그 안에 여러가지 함수들이 있습니다.
그리고 맨 마지막으로 내려가면은 페이지가 로드될 때, 제일 먼저 App 상수 안에 있는 이 start() 함수를 실행시킨다는 걸 알 수 있구요.
그래서 이 start() 함수를 구현을 할 껀데, 그전에 klaytn 블록체인과 소통할 수 있는 caver.js 라이브러리를 불러오고 BApp안에서 쓸 수 있도록 인스턴스화 시켜야 합니다.
자 맨 위에다가 여기다가 임포트 하나 할게요.

import Caver from "caver-js";

맨 위에다가 caver.js 임포트 시켰구요.
그리고 환경설정 상수 하나 만듭니다. 자 여기 위에다가

const config = {
  rpcURL: 'https://api.baobab.klaytn.net:8651'
}

config 안에 rpcURL이 있는데요.
우리가 어떤 클레이튼 노드에 연결해서 쓸지 여기에다가 정의를 한 겁니다.
바오밥 테스트넷이라구 했구요.
마지막으로 이 rpcURL을 Caver 생성자에 넘겨서 인스턴스화하는 상수를 만들겠습니다.
바로 아래에다가 

const cav = new Caver(config.rpcURL);

인스턴스화 작업이 이렇게 끝났구요. 이 caver 상수를 이제 BApp 안에서 쓸 수 있게 해놓았습니다.
이제 start() 함수를 꾸미면 되는데, 사실 start() 함수에서는 session이라는 것을 통해 계정 인증을 했던 적이 있었는지 체크를 먼저 해야합니다.
그런데 session 사용하는 부분이 나중에 있어서 일단 start() 함수를 공백으로 납두도록 하겠습니다.
handleImport() 함수부터 구현하도록 하죠.
우리가 로그인 버튼 클릭하고 모달이 뜬 다음에 키스토어 파일을 선택할 수가 있죠.
그런데 이파일이 과연 유효한 키스토어 파일인가 먼저 검사를 해야합니다. 
그 과정을 이 handleImport() 함수에서 해 보도록 하구요.
먼저 FileReader 객체를 생성해서 상수에 담습니다.

const fileReader = new FileReader();

그리고 readAsText() 함수를 통해 선택한 파일을 읽구요.

fileReader.readAsText(event.target.files[0]);

event.target.files 이 부분은 우리가 선택한 파일을 뜻합니다.
이제 readAsText()가 실행이 완료 되면, FileReader의 onload 이벤트가 발생합니다.

fileReader.onload = (event) => {  	
  
}

callback으로 받은 이 event, 즉 파일의 내용을 이제 이 코드 블록 안에서 쓸 수 있는데요.
이 파일의 내용이 유효한 키스토어 파일인가 검사를 할 겁니다.
먼저 안에다가 try catch 블록 추가 하구요.

try {
   	
} catch (event) {

}

이제 파일의 내용이 유효한지, 즉 진짜 키스토어 파일이 맞는지 if문을 통해 확인을 합니다.

if (!this.checkValidKeystore(event.target.result)) {
 
}

이 checkValidKeystore()라는 함수에 우리가 읽은 파일의 내용을 인자로 이렇게 넘겼죠.
자 이제 checkValidKeystore() 함수를 꾸며 보도록 하겠습니다.
이쪽으로 가시면은 이 함수가 인자로 keystore를 받구요, 파일을 받은거죠.
그리고 받은 keystore 파일이 json 파일인데 이 json 안에 있는 속성들을 변수로 활용하기 위해서 자바스크립트 오브젝트로 바꾸겠습니다.

const parsedKeystore = JSON.parse(keystore);

JSON의 parse함수를 써서 keystore 파일 안에 있는 내용을 분해하고 오브젝트로 변환해서 이 상수에다가 저장을 했습니다.
그다음에는 무엇을 해야 할까요?
네 키스토어 구성에 필요한 속성들이 잘 들어가 있는지 확인을 합니다.
제가 키스토어 파일을 직접 보면서 뭐가 필요한지 보도록 하죠.
여기 보시면은 키스토어 구성에 필수적인 요소들이 이 version, id, address, 그리고 crypto가 있습니다.
이 네가지 field들이 존재해야 키스토어 파일인 거 구요.
그래서 코드를 통해 체크하겠습니다.

const isValidKeystore = parsedKeystore.version && (버전 필드가 있는지 그리고)
  	parsedKeystore.id && (id가 있는지)
  	parsedKeystore.address && (그리고 주소 address가 있는지)
  	parsedKeystore.crypto; (마지막으로 crypto 필드가 있는지 확인해 줍니다.)

이 네가지가 있어야 되구요.
마지막으로 이 상수를 return해주면 마무리가 됩니다.

return isValidKeystore;

네 이렇게 하면 마무리가 되구요.
이제 다시 위로 올라가서 이제 불러온 파일이 유효한 키스토어 파일인지 저희가 검증을 했죠.
만약에 아니면은 메세지로 유효하지 않다고 보여주고 또 함수를 종료합니다.

$('#message').text('유효하지 않은 keystore 파일입니다.');
return;

다시한번 정리를 하죠. 저희가 보낸 파일이 키스토어 파일인지 유효한 키스토어 파일이 아니면 이 에러 메시지도 보내고 함수를 종료합니다.
반대로 검증을 통과했어요. 그러면 키스토어 파일의 내용을 전역변수에 저장합니다. 
그러면 먼저 전역변수를 만들어야 하는데요. 
start함수 바로 위에다가 auth라는 전역변수를 하나 만들구요.
세개의 필드를 갖고 있을껍니다. accessType 값으로 저희는 keystore를 줄거구요.
두번째 필드는 keystore, 마지막은 password입니다.	

auth: {
	accessType: 'keystore',
	keystore: '',
	password: ''
  },

자 이렇게 바꿔주고요. 자 이 auth 오브젝트 안에 세가지 필드가 있다고 했죠.
accessType은 인증 방식인데요. 'keystore'타입과 'privatekey' 타입이 있죠.
우리는 keystore타입으로 진행하는 거구요.
두번째로 keystore 필드는 키스토어 파일의 전체내용을 저장하고 마지막으로 password는 키스토어 파일과 조합되는 비밀번호를 담는 필드입니다.
다시 함수로 돌아가서 자 이제 검증을 통과하면은

this.auth.keystore = event.target.result;

네 우리가 만든 auth 이변수에 keystore 필드에다가 불러온 keystore 파일 전체 내용을 대입을 했습니다.
자 그 다음에 성공했다는 메시지를 보냈구요. 자 이 위에꺼 복사하죠.
복사해서 성공했다라는 메시지 "keystore 통과. 비밀번호를 입력하세요"
그리고 곧바로 password 필드를 타이핑할 수 있도록 만듭니다.

document.querySelector('#input-password').focus();

마지막으로 파일 읽으면서 에러가 났을 시에 이 catch 블록 안에서 에러 메시지를 보내고 함수를 종료시키겠습니다.
자 여기도 똑같이 복사하셔서 맨 위에꺼 복사하죠 똑같은 에러니까.
이렇게 하고 return 문을 통해 함수를 종료 시킵니다.
handleImport() 함수는 여기까지 하면 구현이 됬구요. 이제 테스트를 해보겠습니다.
npm run dev해서 실행시켜주시구요.
실행이 되면 브라우저로 가서 로그인 버튼 클릭하시구요. 키스토어 파일 선택합니다.
네 그러면 통과 메시지가 떴죠. 그리고 비밀번호 입력하는 곳으로 포커스가 바로 옮겨졌습니다.
네 반대로 아무 파일이나 선택해 보겠습니다.
아무 파일, 키스토어 파일 말고 선택하면 유효하지 않은 keystore 파일입니다 라고 에러 메시지 떴죠.
잘 작동을 하구요. 이제 이 아래에 비밀번호를 입력하면 비밀번호를 전역 변수에 저장하는 함수를 구현해 보도록 하겠습니다.
아주 간단한 거 구요.
html로 가보시면 우리가 비밀번호 입력할 때, 이 handlePassword 함수가 호출되죠.
그러면은 handlePassword 함수에다가 여기서

this.auth.password = event.target.value;

html onchange 이벤트를 통해 이렇게 비밀번호 값을 불러오고 전역변수 auth에 password 필드에다가 대입을 했습니다.
간단했죠. 여기까지 키스토어 파일의 유효성 검사를 해보았구요.
다음 강좌에서 비밀키를 생성하고 wallet에 내 계정 정보를 추가하는 작업을 해보겠습니다.

## 5.7 계정 검증(지갑 통합)

키스토어 파일 불러오는 부분이랑 비밀번호 입력하는 부분 완성했으니까요 이제 이 정보들을 바오밥 노드에 보냈을 때, 인증을 성공할 수 있는 계정인지 확인해 보겠습니다.
그전에 이 rpcURL에 http가 아니라 https로 바꾸겠습니다.
index.html로 가보시면 제출 버튼 클릭시에 handleLogin() 함수를 호출하죠.
이제 이것을 구현을 할텐데 어서 구현을 해보자.
handleLogin() 여기 있습니다.
여기다가 먼저 accessType이 keystore인지 확인을 해야해요.

if (this.auth.accessType === 'keystore') { 
}

저희가 이 if문을 쓰는 이유가 계정을 인증할 때 keystore나 프라이빗 키 사용하는게 있다고 했었죠.
저희는 비록 키스토어만 써서 하지만 나중에 여러분들이 프라이빗 키도 넣어서 인증을 하고 싶을때 그때를 대비해서 이런 if문을 추가를 했습니다.
그리고 이 아래다가 try catch 문을 추가를 하시구요.

try {       
} catch (e) 
}

네, 드디어 caver 인스턴스를 사용할 때가 되었습니다.
여기서 문제하나 내드릴게요.
키스토어 파일과 비밀번호 조합을 통해 얻을 수 있는 게 무엇일까요?
잘 기억하신다면 바로 아실 수 있는데
바로 프라이빗 키(비밀 키)를 얻을 수 있죠.
이 비밀 키를 통해 월렛 인스턴스를 생성할 수가 있습니다.
자 그래서 제일 먼저 해야될 것이 키스토어 파일과 비밀번호를 통해 비밀키를 가져와야 되요.

const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;

네 설명해 드리죠.
caver 인스턴스의 accounts 멤버를 통해서 decrypt 함수를 쓸 수 있습니다.
해독한다는 뜻이죠.
어떻게 해독하냐면 keystore 파일의 내용과 비밀번호를 인자로 넘겨서 decrypt된 계정 object를 반환 받을 수 있습니다.
그 object안에는 여러가지 멤버들이 있는데 그중에서 privateKey를 가져와서 상수에다가 저장시키는 겁니다.
아시겠죠?
만약 decrypt하는데 에러가 났다면 메시지를 보냅니다.
catch 밑에다가 저 위에 껄 일단 복사해오죠.
그리고 붙여놓고요 내용만 변경하겠습니다.
비밀번호가 일치하지 않습니다.
에러가 안 났다면 비밀키를 통해서 월렛 인스턴스를 만들 거구요.
그래서 아래다가 

this.integrateWallet(privateKey);

intergrateWallet 함수에 프라이빗키, 비밀키를 넘깁니다.
자 그러면 이 함수로 가 보시구요.
여기서 이 인자로 받던 privateKey를 사용해서 월렛 인스턴스를 가져오는 코드를 추가할 겁니다.

const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);

네 이 walletInstance가 내 계정 정보들을 가지고 있는거에요.
그리가 이 인스턴스를 월렛에 추가를 해야 됩니다.
바로 아래에다가

cav.klay.accounts.wallet.add(walletInstance)

이렇게 caver 월렛에 내 계정을 추가하면, 앞으로 어떤 트랜잭션을 생성하게 될 때, 쉽게 내 계정 정보를 이 caver 인스턴스를 통해 다시 불러와서 트랜잭션을 처리할 수가 있습니다.
다음은 sessionStorage에다가 walletInstance를 또 저장할 건데요.
드디어 이제 세션 놔왔죠.
sessionStorage는 탭이 닫히거나 웹브라우저가 꺼지기 전까지 웹브라우저 내의 저장 공간에다가 walletInstance를 저장하게 됩니다.
아주 유용한 기능이구요.

sessionStorage.setItem('walletInstance', JSON.stringify(walletInstance))

setItem은 key, value를 쌍으로 받습니다.
그래서 첫 번째 파라미터가 key고, 두번째 파라미터가 value인데 나중에 내가 세션으로 내 계정 정보를 불러와야 되요 그러면 이 key 값만 불러옵니다. 
그래서 우리는 walletInstance를 키 값으로 이렇게 했죠. 그럼 나중에 이거를 불러오면 쌍으로 같이 저장된 이 value 값이 자동적으로 불러와 집니다.
우리가 세션 스토리지를 쓰는 이유는 계정에 로그인된 상태를 계속 유지하기 위해서에요.
이 부분, 왜냐하면 caver 월렛에 저장된 내 계정 정보는 내가 다른 사이트 방문했다가 오거나 아니면 페이지가 새로고침하면 그 정보가 날라가요.
하지만 세션 스토리지에 저장하면은 내가 잠시 따른 사이트 방문했다가 돌아와도 그게 유지가 되고 또는 페이지가 새로고침되도 계정 정보가 계속 유지가 됩니다.
그래서 나중에 start 함수에서 wallet instance 세션을 불러오고 로그인된 상태를 계속 유지하도록 구현 할거에요.
자 그래서 우리가 처음에 start 함수는 구현을 안 했던 거고요.
세션을 사용할때까지 기다린 겁니다.
네 이제 지금 당장은 ui를 업데이트 시켜야 되는데요.
우리가 이 integrateWallet 함수를 통해 계정인증을 완료했으니까 ui를 알맞게 변경해야 됩니다.
바로 밑에다가 

this.changeUI(walletInstance);  

changeUI 함수에 제가 walletInstance를 보냈죠.
그러면 changeUI 함수에서는 무엇을 해야 될까요?
changeUI 함수로 가보면은 일단은 모달을 닫습니다.

$('#loginModal').modal('hide');
 
그다음에는 로그인 버튼도 안보이게 다시 하구요.

$("#login").hide();

또, 안보이게 했던 로그아웃 버튼도 다시 보이도록 변경을 합니다.

$('#logout').show();

그 다음에 로그인 했으니까 내 계정 주소도 보이게 하면 좋겠죠.

$('#address').append('<br>' + '<p>' + '내 계정 주소: ' + walletInstance.address + '</p>'); 

주소에 접근해서 이렇게 메시지를 저희가 보내주는 거에요.
네 다 작성했습니다.
이 $('#address').append 이 부분이 html에서 id 속성이 address인 것에 계정 주소를 지금 이 메시지를 보내주는 겁니다.
그러면은 html로 가서 그 부분을 작성을 해보죠.
메시지를 보여주는 부분은 저희가 이 h3 태그 바로 밑에다가 해보도록 하겠습니다.

<div class="text-center" id="address"></div>   

이렇게 하면 바로 이 위치에서 내 계정 주소를 볼 수 있게 되는거구요.
여기까지 하겠습니다. 이제 잘 작동하나 테스트를 해보도록 하죠.
터미널에서 npm run dev 하시구요.
네 로그인버튼 클릭하고 키스토어 파일 불러오구요
비밀번호 입력하고 제출버튼을 누르면
계정 인증이 완료되고 로그아웃 버튼으로 바뀌었구요.
아래에는 내 계정 주소가 보입니다.
마지막으로는 로그아웃하는 기능도 구현해 보도록 하죠.
네 html로 가보시면 로그아웃 버튼을 클릭했을 때 handleLogout() 함수를 호출해서 거기로 가 보겠습니다.
handleLogout 함수 네 여기 있네요.
여기다가 removeWallet이라는 함수를 불러올 껀데요.

this.removeWallet();

이 함수를 통해서 wallet을 클리어시키고 세션 스토리지도 clear시키겠습니다.
removeWallet 함수로 가셔서 이 코드를 추가합니다.

cav.klay.accounts.wallet.clear();

저희가 로그아웃을 하니까 기존에 인증됬던 정보들을 wallet에 추가됬던 정보들을 clear하는 거에요.
자 계정 정보를 지우는 과정이구요. 그 다음으로 세션을 지웁니다.

sessionStorage.removeItem('walletInstance');

지울때는 이 key값만 입력해서 지우면 되구요.
마지막으로 reset 함수를 호출하면 끝이납니다.

this.reset();

이 reset 함수에서는 그냥 단순하게 글로벌 변수, 즉 전역변수죠. 전역변수 auth를 초기화시키면 되구요.
함수로 가셔서 자 위에 있네요.
auth 변수를 초기화 시킵니다.

this.auth = {
    keystore: '',
    password: ''
};

auth에 accessType도 있는데 accessType은 어차피 값이 keystore가 될꺼라서 안 지워도 되는거구요.
대신 우리가 로그인 했을 때 이 키스토어와 패스워드 필드에는 값이 입력이 됬었죠.
그부분을 로그아웃하면서 안전하게 지우는 겁니다.
다시 handleLogout 함수로 가셔서요.
페이지 새로고침하는 코드를 넣고 마무리를 하겠습니다.
새로고침을 하는 이유는 처음 상태 때의 ui로 돌아가기 위해서 하는 거구요.

location.reload();

잘 하셨습니다. 이제 마지막으로 테스트하고 끝내도록 하겠습니다.
로그인 하시구요. 계정 인증이 됬고 이제 로그아웃 버튼을 클릭하면서 계정 정보가 사라지고 새로고침을 통해 초기화 화면으로 돌아왔습니다.
여기까지 계정인증 로직을 완료해 보았구요. 다음강좌에서 세션 스토리지를 통한 계정 인증 상태를 유지하는 부분을 완성해 보겠습니다.

## 5.8 계정 세션

우리가 로그인하고 페이지 새로고침하면 어떻게 되는지 한번 보겠습니다.
로그인 버튼 클릭하고 키스토어 파일 선택하시구요.
비밀번호 입력한 다음에 제출버튼 클릭하면 계정인증이 됬구요.
이 상태에서 f5 눌러서 새로고침 해보죠.
자 그러면 다시 초기화 상태가 됬죠.
로그인 상태를 유지하면 좋을텐데 어떻게 하면 될까요?
우리가 로그인에 성공하면 계정인증한 정보를 세션 스토리지에 저장했었죠.
이거를 이제 활용할 겁니다.
BApp이 실행 되면서 가장 먼저 부르는 함수가 start 함수이죠.
여기에서 세션 스토리지에 저장된 내 계정정보를 불러옵니다.
네 그럼 start 함수로 가서 맨위에 있죠

const walletFromSession = sessionStorage.getItem('walletInstance');

getItem을 써서 key 값을 넘기면, 쌍으로 저장됬던 value 값을 불러오고 그거를 상수에다가 저장을 하는 겁니다.
내 wallet instance를 저장을 한거에요.
다음으로는 walletFromSession 에 값이 들어가 있는지 확인을 합니다. 
if문을 통해서

if (walletFromSession) {
 
}

만약 값이 있다면 try catch 생성하구요.

try { 
     
} catch (e) {
 
  }

그리고 caver 월렛에 다시 내 계정 정보를 추가합니다.

cav.klay.accounts.wallet.add(JSON.parse(walletFromSession));

페이지가 새로고침 되거나 다시 방문 되면 wallet에 추가 됬었던 기존의 계정 정보가 다 지워지기 때문에 세션을 통해서 다시 추가를 하는 겁니다.
다음으로 로그인 되었다는 상태를 보여주기 위해 ui를 업데이트 시켜야 되는데요.

this.changeUI(JSON.parse(walletFromSession));

이렇게 하면 로그아웃 버튼으로 바뀌고 내 계정 주소를 보여주겠죠.
마지막으로 세션 스토리지에 있던 값이 유효한 walletInstance가 아닐 때, catch문으로 가게 됩니다.
그리고 세션 스토리지에 있는 walletInstance를 지우구요.

sessionStorage.removeItem('walletInstance');

네 여기까지하면 됬고요.
잘 작동하나 테스트를 해보죠.
여기서 이제 새로고침 하면은 f5 눌러서 그러면 초기화 상태로 돌아가지 않고 로그인된 상태를 계속 유지합니다.
여기까지 계정 인증 상태를 계속 유지하는 부분을 구현해 보았습니다.


## 5.9 컨트랙트에 클레이 전송하기(입금)

이제 운영자 계정을 사용해서 컨트랙트로 클레이를 송금해 보겠습니다. 
먼저 ui를 만들어 보구요, html에서 여기 <div class="row"> 이 부분 아래에다가 만드시면 됩니다.

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

영상 퍼즈 하시고 이 부분 추가해주시고요. 간단하게 설명해 드리겠습니다.
컨트랙트의 송금하기 ui 부분을 여기 이 css를 통해 또 안 보이게 설정을 했구요.
액수를 입력하고 송금버튼을 클릭하면 deposit 함수를 실행하도록 설정했습니다.
자 그러면 deposit 함수로 가서 구현해 보도록 하죠.
deposit 함수로 가셔서 여기서 뭘 어떻게 구현할 건지 설명 먼저 해 드리겠습니다.
컨트랙트로 클레이 송금하는 것은 무조건 owner 계정으로만 할 수 있습니다.
컨트랙트를 배포한 사람의 계정으로만 가능하구요.
즉 이 이벤트 게임의 주최자만 보낼 수 있는 거죠.
owner 계정이 맞다면, 컨트랙트의 deposit 함수에 접근하고 클레이를 송금하는 겁니다.
플로우는 엄청 간단한 편이에요.
그러면 먼저 우리가 배포했던 컨트랙트를 접근할 수 있도록 인스턴스를 하나 만들겠습니다.
컨트랙트 인스턴스를 만들 때에는 배포한 컨트랙트의 abi 정보와 주소가 필요한데요.
맨 위에 cav 상수 아래에다가 두개를 넘깁니다.

const agContract = new cav.klay.Contract(DEPLOYED_ABI, DEPLOYED_ADDRESS);

네 2개를 넘겼는데 여기에 DEPLOYED_ABI와 DEPLOYED_ADDRESS는 BApp 내에서 쓸 수 있는 전역 상수들입니다.
우리가 컨트랙트 배포하고 나서 DEPLOYED_ABI 파일이랑 DEPLOYED_ADDRESS 파일에 정보들을 저장하게 되죠.
이 정보들을 읽어서 전역 상수로 쓸 수 있도록 웹팩에서 세팅 합니다.
webpack.config.js 파일로 오시면 여기에 주석 처리된 부분이 있죠. 이걸 이제 푸시고요.
웹팩에서 컴파일 타임 때, 이 부분을 실행해서 DEPLOYED_ADDRESS와 DEPLOYED_ABI라는 전역 변수를 설정하는 겁니다.
간단히 말씀드려서 파일 시스템을 통해 DEPLOYED_ADDRESS 파일을 읽고 그 안에 있는 컨트랙트 주소를 전역 상수에다가 대입을 하는 겁니다.
동일하게 DEPLOYED_ABI 파일에 있는 abi 정보를 읽고 DEPLOYED_ABI라는 전역 상수에 저장하는 거구요.
자 index.js 파일로 다시 돌아오죠.
네 그래서 컨트랙트 인스턴스의 생성자로 보내는 이 두 abi와 주소 정보가 웹팩에서 생성된 전역 상수를 통해 값이 넘어간다는 것을 기억하시길 바랍니다.
컨트랙트 인스턴스 만들었으니까요 이제 deposit 함수에서 계속 진행하겠습니다.
deposit 함수로 내려가셔서..
네 송금하기 전에 제일 먼저 확인해야 될 것이 있죠.
바로 지금 로그인된 계정이 owner 계정인지 확인해야 합니다.
그래서 두가지 정보를 불러야 하는데, 첫번째는 현재 로그인된 계정 정보를 불러오고요 두번째는 컨트랙트에 저장된 owner 상태의 값을 불러옵니다.
먼저 로그인된 내 계정 정보를 불러 오겠습니다.

const walletInstance = this.getWallet();

getWallet 함수로 가서 현재 caver 월렛에 존재한 내 계정 정보를 가져옵니다.
여기 getWallet에서 if 문을 통해 

if (cav.klay.accounts.wallet.length) {
	return cav.klay.accounts.wallet[0];
}

지금 klay.accounts.wallet의 length 길이가 있다면 어떤 계정이 추가가 되어 있다면 제일 첫번째에 있는 account를 return 합니다.
이 wallet 0번째 인덱스는 wallet에 추가된 계정들 중 다시 말씀드리지만 제일 첫번째 계정 즉 지금 제가 로그인 되어있는 계정을 말하는 거구요 여기까지 되면은 이 함수 구현 다 한 것입니다.
다음으로 컨트랙트의 owner 상태 변수 값을 불러와 보죠.
자 이 callOwner 함수에서 

return await agContract.methods.owner().call();

되게 간단했습니다. 우리가 만든 AdditionGame 컨트랙트 인스턴스를 통해 이 owner 함수에 접근하고 값을 불러오는 겁니다.
await 키워드를 써서 비동기로 값을 받았구요.
네 송금하기 전에 필요한 내용들을 이렇게 만들었으니까요 이제 deposit 함수에서 계속해서 진행하도록 하겠습니다.

if (walletInstance) {
 
}

그리고 위에서 좀 땡기죠. getWallet 함수에서 받은 이 walletInstance가 존재한다면 현재 로그인된 계정 주소와 컨트랙트에서 리턴 받은 owner의 계정 주소를 비교해 봅니다.

if (await this.callOwner() !== walletInstance.address) return; 

한번 보죠. 만약 서로 이렇게 비교를 했는데 값이 다르면, 더이상 진행하지 않고 함수를 리턴문을 통해서 종료를 합니다.
하지만 같다면, 만약 값이 같다면 else 문을 통해서 html input에 있는 값을 가져옵니다. 

var amount = $('#amount').val();

html input 값을 이렇게 가져오고요 또 입력한 값이 존재한다면

if (amount) {
}

컨트랙트 인스턴스를 사용해서 deposit 함수로 값을 보냅니다.

agContract.methods.deposit().send({
 
})

네 여기서 이 send의 인자로 트랜잭션 object를 보내야 되는데요 세 가지는 명시해야 합니다.
먼저 누가 이 함수를 호출하는 건지 밝혀야 하고요.

from: walletInstance.address,

현재 로그인된 계정으로 이 함수를 호출한다고 했습니다. 
참고로 walletInstance의 address는 계정 인증 완료한 계정이라 트랜잭션을 서명할 수 있는 권리가 생깁니다.
그래서 이 from에는 아무 주소나 넣을 수 없고요. BApp 내에서 계정인증이 완료된 주소만 값으로 쓸 수 있습니다.
자 다음으로 gas는 250,000 안에서 소비할 수 있게 설정하고요.

gas: '250000',
 
마지막으로 컨트랙트의 deposit 함수가 payable 타입이라 value 필드를 무조건 넘겨야 합니다.

value:

여기다가는 html 인풋에서 받아온 숫자를 클레이의 최소단위인 Peb으로 변환해서 넘겨야 하는데요 caver 라이브러리의 util을 써서 변환하겠습니다.

cav.utils.toPeb(amount, "KLAY")

이렇게하면 컨트랙트 deposit 함수로 돈을 보낼 수 있게 되었구요.
그런데 트랜잭션을 이렇게 마무리하기 보다는 비동기로 받을 수 있는 정보들을 또 활용할 수가 있습니다.
여기 바로 안에다가 

.once('transactionHash', (txHash) => {
    console.log(`txHash: ${txHash}`);
})

우선 트랜잭션 해쉬를 리턴받을 수 있습니다. 그리고 그거를 콘솔에 보이게 했고요.
참고로 이 콘솔 내용 감싸는 애들 여기 바깥쪽 쪼끄만 애들 있죠. 얘네들 작은 따옴표가 아니라 숫자 1 왼편에 있는 코텐션 마크입니다.
주의하시고요. 다음으로 receipt 즉 영수증을 리턴 받을 수도 있습니다.

.once('receipt', (receipt) => {
   console.log(`(#${receipt.blockNumber})`, receipt);          
})

receipt를 받으면 트랜잭션이 성공적으로 블록에 추가가 되었다는 뜻입니다. 그래서 어느 블록에 추가가 됬는지 receipt를 통해서 확인할 수도 있고요. 마지막으로 트랜잭션 처리가 실패했다면 에러를 리턴 받을 수도 있습니다.

.once('error', (error) => {
   alert(error.message);
  }); 

에러가 있다면, 메시지를 띄울거구요.
여기까지 하면 트랜잭션을 보낸 후에 성공 여부를 체크할 수 있는 로직을 완료해 보았습니다.
끝으로 html input으로 받은 amount가 없다면 함수 종료시키는 return 문을 추가하겠습니다.
자 여기 끝에다가

return;

여기까지 컨트랙트의 deposit 함수에 KLAY를 보내는 부분을 완성했고 곧바로 다음 강좌에서 ui 변경 및 테스트를 해보도록 하겠습니다.

## 5.10 컨트랙트에 클레이 전송하기(UI 변경 및 테스트)

UI 변경 및 테스팅을 해보도록 하겠습니다.
우리가 전 강좌에서 deposit 함수에 KLAY를 보내고 receipt를 받으면 트랜잭션이 성공한 것이라고 했었죠.
성공한 다음에는 무엇을 해야 할까요?
어떤 UI적 요소를 보여주면 좋을 것 같습니다.
일단 알림 메시지를 보여줄 거 구요. 이 밑에다가

alert(amount + " KLAY를 컨트랙에 송금했습니다.");  

그리고 페이지를 새로고침해서 컨트랙트 잔액을 볼 수 있게 할 것입니다.

location.reload();     

방금 컨트랙트에 잔액을 볼 수 있게 한다고 했는데 우리가 스마트 계약 작성할 때, 컨트랙트의 잔액을 불러오는 함수를 만들어 썼죠.
이 getBalance 함수
이 getBalance 함수를 불러와서 컨트랙트의 잔액을 볼 수 있게 할 겁니다.
먼저 html에서 컨트랙트의 잔액을 디스플레이하는 div를 하나 추가할 건데요.
여기 내 계정 주소 보여주는 곳 밑에다가 div 하나 추가 합니다.

<div class="text-center" id="contractBalance"></div>

자 그러면 이곳에서 이제 컨트랙트 잔액을 보여줄 거 구요.
뷰는 준비가 되었으니까 백엔드에서 잔액을 불러오는 함수를 만들어 보겠습니다.
callContractBalance 함수로 가셔서 코드를 추가할 거 구요.
여기 있죠. 이 부분에서 

return await agContract.methods.getBalance().call();

컨트랙트 인스턴스를 통해 getBalance 함수 접근해서 값을 불러오는 부분입니다. 
이것도 간단했죠.
이 callContractBalance 함수를 이제 어디에서 불러올 것인가 정해야 하는데요 어디에서 불러야 할까요?
deposit 함수에 트랜잭션이 성공하고 receipt를 받으면 location.reload()를 통해 페이지를 새로고침하게 되죠.
페이지가 새로고침 됬을 때 제일 먼저 실행하는 함수가 무엇일까요?
start 함수가 먼저 실해이 됩니다.
그래서 이 start 함수에서 changeUI 함수를 부르게 되죠.
바로 이곳에서 changeUI 함수에서 컨트랙트의 잔액을 불러오는 부분을 추가를 해야 합니다.	  
네 그래서 여기 일단 복사하고요 좀 고치도록 하죠.

$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(await this.callContractBalance(), "KLAY") + ' KLAY' + '</p>');    

좀 길어서 이것좀 아래로 내리죠. 좀 길죠 설명해 드리겠습니다.
html에서 컨트랙트 잔액 보여주는 부분에 메시지를 추가할껀데, callContractBalance 함수를 불러서 잔액을 일단 가져오고요, 그런데 그 잔액이 클레이 최소 단위인 peb으로 불러와집니다.
그렇게 되면 사용자 입장에서 얼마나 남은 건지 알아보기 힘들겠죠.
단위가 너무 크니까요.
그래서 caver.utils 쪽에 fromPeb라는 함수가 있습니다.
peb에서 어떤 단위로 변환해줄 수 있는 함수인데요 KLAY로 변환하겠다고 두 번째 파라미터에 명시한 것입니다.
결과적으로는 KLAY로 변환된 컨트랙트 잔액을 html에 보여주게 되구요.
메시지로 보여주게 됩니다.
마지막으로 컨트랙트로 클레이를 송금하는 것은 오직 owner 계정으로만 할 수 있도록 세팅해야 하죠.
이벤트 주최자에게만 권한을 줘야 합니다.
그래서 owner 계정으로 로그인했을 때만 송금할 수 있는 UI를 보여주도록 변경하겠습니다.
changeUI 함수에서 여기 아래에다가 if 문을 통해 

if (await this.callOwner() === walletInstance.address) {
    $("#owner").show(); 
}

owner 계정 주소와 로그인된 계정 주소가 똑같을 때에만 owner div를 보여주도록 세팅했구요.
html에서 보시면은 이 owner div가 default로 css를 통해 안 보이게 설정이 되어 있었죠.
그래서 이 부분을 owner 계정으로 로그인 하면 보여주게 되는 겁니다.
네 이제 테스트를 해보죠.
일단 재배포를 해보겠습니다.
truffle.js에서 여러분 계정의 비밀키가 제대로 입력되어있는지 확인해 주시고요 터미널에서 재배포 하겠습니다.

truffle deploy --compile-all --reset --network klaytn

혹시나 배포를 안하셨던 분들을 위해서 재배포를 하는 거구요.
좀만 기다리시면 배포가 이제 끝나갑니다.
배포가 끝났구요.
npm run dev해서 실행해보죠

npm run dev

f12 누르셔서 콘솔 창을 일단 띄워보겠습니다. 그리고 로그인 하시고요.
파일 선택하고 비밀번호 입력한 다음에..
owner 계정으로 로그인 했기 때문에 송금할 수 있는 이 ui가 보입니다.
이제 송금 할거구요 1 KLAY 보내겠습니다.
좀만 기다리시면 송금이 성공하면서 트랜잭션이 성공했죠.
콘솔 로그를 통해 첫번째는 트랜잭션 해쉬와 두번째는 receipt 정보를 볼 수 있습니다.
receipt 안에 어떤 블록 넘버에 저장이 됬는지 저희가 그렇게 define 했었죠.
알림 메시지로 잘 작동합니다.
트랜잭션하는데 소요된 시간이 한 3초 이내였던 것 같은데 이 3초안에는 트랜잭션 생성한 다음에 블록생성하고 트랜잭션 완료되면 네트워크에 전파하기까지 크게 4가지의 과정들이 포함되어 있습니다.
타 블록체인 플랫폼에 비해서 트랜잭션 처리 속도가 엄청 빠르죠.
알림 메시지 클릭하면 페이지가 새로고침 되면서 start 함수를 먼저 호출하고 그 안에 있는 changeUI 함수를 통해 업데이트된 컨트랙트 잔액을 이렇게 불러와 보여줍니다.
네 송금 기능은 잘 작동하는데 트랜잭션 기다리는 동안 어떤 보여주는 로드 스피너가 있으면 좋겠습니다. 
이 부분은 필수 사항은 아니지만 보기 좋은 ui를 위해 같이 한 번 해보시기 바랍니다.
index.js로 가셔서 맨위에다가 spin.js import시켜 주시고요.

import {Spinner} from 'spin.js';

그리고 showSpinner 함수로 가셔서 showSpinner 함수에서 spinner 인스턴스를 리턴하게 만듭니다.

var target = document.getElementById('spin');
return new Spinner(opts).spin(target);

네 완성했고요 그리고 이 함수를 deposit 함수에서 불러옵니다. 
deposit 함수 가셔서 맨위에다가 불러오겠습니다.

var spinner = this.showSpinner();

그러고 나서 receipt를 받고 나면, 트랜잭션을 성공하고 나면 이 스피너를 멈추게 하고요

spinner.stop();  

로직은 완성했고요 마지막으로 html에서 이 스피너를 보여줄 div를 추가하겠습니다.
이 br태그 바로 아래에다가

<div id="spin"></div>   

네 간단했습니다. 이제 테스팅을 해보도록 하죠.
마찬가지로 1 KLAY 송금 할꺼 고요 네 그러면 스피너가 나오면서 좀더 그럴싸한 광경이 연출되고 있습니다.
그리고 alert 메시지 잘 떳고요 송금 기능 잘 작동합니다.
확인 누르면 이벤트 잔액이 업데이트 되고요 ui도 잘 반영을 하네요.
여기까지 owner 계정에서 컨트랙트로 클레이 송금 하는 부분을 다루어 보았습니다.

## 5.11 무작위 숫자 생성하기

이제 재미있는 부분을 만들어보도록 하죠.
랜덤으로 두 개의 숫자를 만들어서 덧셈 하는데 쓰이도록 만들어 보겠습니다.
html을 먼저 꾸며볼 꺼구요.
spin div 바로 위에다가 코드를 추가해 주시기 바랍니다.

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

네 영상 퍼즈하시고 이 부분 추가해주시고요 설명해드리도록 하겠습니다.
이것도 우선 마찬가지로 css 통해 전체 부분을 안보이도록 설정했고요.
로그인 하면 보여주도록 바꿀 겁니다.
시작이라는 부분을 클릭하면 generateNumbers라는 함수를 호출하고요 그러면 그 함수에서 두개의 숫자를 생성하는데 첫번째 숫자는 num1, 이 필드에서 보여줄꺼고 또 다른 숫자는 num2 필드에서 보이게 할 겁니다.
덧셈에 사용되게 하는 거죠.
그리고 밑에 답을 적을 수 있는 input 필드가 있고요 마지막으로 제출 버튼을 클릭하면 답을 제출하게 될 겁니다.
간단한 html이고요 이제 계정 인증이 된 유저만 이 부분을 볼 수 있도록 세팅을 하겠습니다.
changeUI 함수로 가셔서 logout.show() 밑에다가 game div 보이게 추가합니다.

$('#game').show();
 
그리고 이제 html에서 확인해보죠.
로그인이 된 상태면 가운데 노란 박스에 예쁜 UI가 잘 보입니다.
이제 시작 클릭하면 숫자들을 보이게 설정할 껀데요.
generateNumbers 함수에서 랜덤 숫자들을 생성해보겠습니다.
이제 위로 가시고요 generateNumbers 함수 있습니다.

var num1 = Math.random();

먼저 Math 클래스의 random 함수를 호출하는데 random 함수는 0에서 1 아래의 소숫점 있는 숫자들을 랜덤으로 생성하게 됩니다.
그런데 이렇게 하면 숫자가 너무 작죠. 그래서 곱할 껀데요. 여기에다가 곱하기 50을 합니다.

var num1 = Math.random() * 50;

네 이렇게 하면 0에서 49까지의 랜덤한 숫자가 생성이 되고요. 하지만 문제가 또 너무 쉬우면 안되니깐 최소한 두 자릿수 이상 생산할 수 있도록 생산된 값에 10을 더하겠습니다.
자 이렇게 하셔서 더하기 10

var num1 = (Math.random() * 50) + 10;

마지막으로 소수점을 버리게 하는 floor 함수를 써서 완성 하고요.

var num1 = Math.floor((Math.random() * 50) + 10);

네 이렇게 해주면 최소 10에서 최대 59까지의 소수점이 없는 숫자가 생성이 됩니다.
다음으로 똑같은 걸 하나 더 만드시고요. 복사하셔서 num2로 하겠습니다.

var num2 = Math.floor((Math.random() * 50) + 10);

이제 이 두 숫자들을 더한 값을 세션 스토리지에 저장을 할 거에요. 정답을 저장하는 건데요.

sessionStorage.setItem('result', num1 + num2);

네 이게 나중에 유저가 답을 냈을 때, 정답 값을 다시 불러와서 유저가 낸 답이 정답인지 비교를 해봅니다.
우리가 숫자는 생성했으니까요 이제 이거를 써먹어야 되는데 다 html로 다시 가셔서 시작을 눌렀을 때 이 부분을 감추고 아래에 있는 question div를 다시 보이게 하면서 함수로부터 생성된 두 숫자들을 num1과 num2 필드에 보이게 할 겁니다.
자 다시 함수로 가셔서 지금 말한 것 구현해보도록 하죠.
generateNumbers 함수 바로 아래에다가 start 부분을 감출 겁니다.

$('#start').hide();

시작부분을 안보이게 하고 복사하시고요. 두번째는

$('#num1').text(num1);

한번더 복사하셔서 num2로 바꿔주시고요

$('#num2').text(num2);

지금 이 두 개가 생성된 숫자들을 num1 그리고 num2 필드에서 보여주게 하는 부분이고요.
그리고 question div를 보이게 합니다.

$('#question').show(); 

마지막으로 바로 정답 칠 수 있도록 답 적는곳으로 포커스를 옮길 것이고요.

document.querySelector('#answer').focus();

네 이제 테스팅을 해보겠습니다.
시작을 클릭하면, 랜덤 숫자들이 생성된게 html에서 렌더링이 잘 되고요.
곧바로 포커스가 또 정답 적는 곳으로 또 옮겨졌죠.
네 여기까지 하고요 다음 강좌에서 타이머 생성을 해보도록 하겠습니다.

## 5.12 타이머 생성하기

타이머를 생성해서 3초 동안만 덧셈 문제를 맞출 수 있게 해보겠습니다.
html로 가셔서 timer 보여주는 div를 만들 건데요 이 spin div 바로 밑에다가 만들겠습니다.

<div class="row text-center">
	<p id="timer"></p>
</div>   

네 이렇게 타이핑 해주시고요. 그리고 index.js로 가셔서 showTimer 함수로 가겠습니다.
밑에 쪽에 있구요. 네 여기 있죠.
여기에서 setInterval 함수를 사용해 카운트다운 하는 숫자를 보여주며 3초가 지나면 문제를 안보이게 하고 다시 시작 클릭하는 부분으로 되돌리도록 하겠습니다.

var seconds = 3;

3초 저장하는 변수 하나 만들고요.

$('#timer').text(seconds);

타이머 보여주는 html에 곧바로 숫자 3을 보여줍니다.
그리고 setInterval 함수를 사용할 건데요 1초 간격으로 설정합니다.

var interval = setInterval(function() {  
}, 1000);

1000, 이 1000이 밀리세컨드로 1초라는 뜻이고요 이제 이안에서 1초 간격으로 어떤 걸 실행할 수 있게 됬습니다.
그래서 그 안에서 이제 

$('#timer').text(--seconds); 

네 이렇게 숫자 하나씩 감소 시켜서 html에 보이게 할 거에요.
자 그리고 만약 이 seconds 변수의 값이 0이 되었어요. 즉 setInterval 안에서 3초가 지나 0이 되었을때 다시 reset 시킵니다.

if (seconds <= 0) {
}   

seconds가 0이 되었을 때 안에다가

$('#timer').text('');

숫자 보여주는 부분을 초기화시키고

$('#answer').val('');

이제 이 부분은 답적었던 input도 초기화를 시켜주는 거구요.

$('#question').hide();

문제 보여주는 div도 이렇게 안 보이게 설정 합니다. 그리고,

$('#start').show();          

시작 클릭할 수 있는 div는 다시 보여주고요 마지막으로,

clearInterval(interval);

이 clearInterval을 통해 setInterval 안에서 돌아가고 있는 시간을 멈추게 합니다. 여기까지 하면 showTimer 함수 다 만든 거고요.
이제 generateNumbers 함수에서 이 함수를 불러와 보겠습니다.

this.showTimer();

이렇게 하면 시작 클릭하자마자 타이머 생성이 되서 카운트 다운 들어가게 되고요 이제 테스트를 해보죠.
시작을 클릭하면 아래의 타이머가 생성이 되고 3초 카운트 다운 들어가죠.
3초에는 다시 이렇게 reset이 됩니다.
여기까지 타이머 생성을 해 보았습니다.

## 5.13 답안 제출하기 및 클레이 받기

네 드디어 마지막 강좌입니다.
유저가 답을 제출하고 만약 정답이면 컨트랙트에서 유저 계정으로 클레이를 보내는 부분을 구현해 보겠습니다.
submitAnswer 함수로 가시고요.
정답을 세션 스토리지에 저장한 값을 여기서 불러옵니다.

const result = sessionStorage.getItem('result');

그리고 사용자가 낸 답도 변수에 저장하구요.

var answer = $('#answer').val(); 

네 이러면 사용자가 낸 답을 변수에 저장하고요 이제 비교를 합니다.

if (answer === result) { }

앤서랑 정답이 같다면 만약 유저가 정답을 맞추었다면 confirm 메시지 창을 띄우면서 확인 버튼을 누르면 유저에게 KLAY를 송금할 겁니다.

if (confirm("대단하네요^^ 0.1 KLAY 받기")) { }

유저가 확인버튼을 클릭했다면 먼저 송금하기전에 컨트랙트의 잔액이 0.1 KLAY 이상이 있는지 확인을 합니다.

if (await this.callContractBalance() >= 0.1) { }

0.1 KLAY 이상이 있는지 확인을 하고요 만약 있으면 receiveKlay 함수를 불러옵니다.

this.receiveKlay();

자 그리고 없다면 알림 메시지를 보내주고요. else 문을 통해서,

else { alert("죄송합니다. 컨트랙의 KLAY가 다 소모되었습니다."); }    

마지막으로 정답을 못 맞췄다면 알림 메시지를 보내 줍니다.
자 if 문의 else 문을 통해서,

else { alert("땡! 초등학생도 하는데 ㅠㅠ"); }

submitAnswer 함수는 여기까지하시면 되고요 이제 한번 테스트를 해보죠.
시작을 클릭해서 틀렸습니다. 정답을 못맞췄을 때 이런 메시지가 뜨구요.
만약 맞추면은, 겨우 맞췄습니다 스릴이 넘치는 게임이고요 이렇게 맞췄을 때는 confirm 메시지 창이 뜨면서 확인 버튼을 누를 수가 있죠.
확인을 누르면 receiveKlay 함수를 호출해서 KLAY를 transfer하게 되구요.
아직은 구현이 안된 상태죠.
그러면 함수를 구현해 보겠습니다.
우리가 할 마지막 함수인데요.
유저가 정답을 맞췄을 때, 자신의 계정을 통해 트랜잭션 비용을 지불하고 클레이를 받아가는 구조입니다.
우리 컨트랙트에 transfer 함수 보시면은 인자가 있죠.
transfer 함수의 0.1 KLAY를 peb으로 변환해서 인자로 넘기게 될 겁니다.
그러기 전에 먼저 트랜잭션 처리하는 동안 스피너를 사용해서 로딩한다는 걸 보여주고요.

var spinner = this.showSpinner();

또 트랜잭션에 필요한 인증된 계정 주소가 필요해서 wallet 인스턴스를 불러옵니다.

const walletInstance = this.getWallet();

wallet 인스턴스의 값이 없다면 함수를 종료시키구요.

if (!walletInstance) return;  

만약 있다면, 컨트랙트 인스턴스를 사용해서 컨트랙트의 transfer 함수에 접근합니다.

agContract.methods.transfer().send({
})

자 컨트랙트의 transfer 함수가 인자가 하나 받죠.
KLAY를 peb으로 변환해서 넘겨야 하는데 caver util을 사용할 겁니다.

cav.utils.toPeb("0.1", "KLAY")

이렇게 하면 0.1 KLAY를 peb으로 변환해서 넘기게 되는 거구요.
그리고 이 send 파라미터 안에는 트랜잭션 object를 보내야 한다고 했었죠.
누가 이 함수를 호출하고 또 가스 한도는 얼마만큼 설정할 것인지 명시해야 합니다.
그래서,

from: walletInstance.address,
gas: '250000'

wallet 인스턴스, 즉 계정 인증이 된 내 주소를 넘기고, 가스는 250,000 안에서 소비하게 합니다.
참고로 우리가 전에는 여기다가 value 필드도 포함해서 넘겼었는데 여기서 필요하지가 않습니다.
왜냐하면 우리 transfer 함수가 타입이 payable이 아니기 때문에. 
deposit 함수는 타입이 payable이였죠 그래서 value 필드를 넘겨야 했습니다.
하지만 없기 때문에 value는 넘기지 않고요.
이렇게 하면 넘기는 값들은 다 완료했고요 이제 트랜잭션 처리된 후에 성공했는지 아니면 에러가 났는지 확인을 해야 합니다.
우리가 deposit 함수에서는 여기 올라가 보시면은 여기 once 있죠 이 once를 통해서 성공 여부를 알 수 있었는데 또 다른 방법이 있습니다.
Promise를 써서 receipt를 받을 수도 있어요.
receiveKlay로 다시 가시고요. 
여기서 이제 Promise로 값을 비동기로 한 번 받아보도록 하겠습니다.

.then(function (receipt) {
});

비동기로 이렇게 기다려서 receipt 값을 받구요 이제 if 문을 통해서,

if (receipt.status) { }

receipt 오브젝트 안에 status라는 필드가 있는데 이게 true이면 성공한 것입니다.
따라서 성공하면 스피너를 멈추고요.

spinner.stop(); 

알림 메시지도 보여주고,

alert("0.1 KLAY가 " + walletInstance.address + " 계정으로 지급되었습니다.");      

네 0.1 클레이가 어느 계정으로 송금됬다는 알림 메시지를 알려준 거 고요.
또 트랜잭션 처리된 것을 scope에서 바로 확인할 수 있도록 html에서 링크로 생성해 보겠습니다.
새로운 div를 만들 건데요. 자 여기 timer div 있죠 이 밑에다가 만들겠습니다.

<div class="row text-center">
   <div id="transaction"></div>
</div>  

<br />

네 이제 이 transaction div에서 링크가 보일 꺼구요 다시 함수로 가셔서 transaction div를 먼저 클리어하겠습니다.

$('#transaction').html("");

이게 트랜잭션이 생성될 때마다 매번 새로운 링크를 보여주기 위해서 transaction div를 지우는 파트구요.
다음으로 링크를 추가하겠습니다.

$('#transaction')
      .append(`<p><a href='https://baobab.klaytnscope.com/tx/${receipt.txHash}' 
                   target='_blank'>클레이튼 Scope에서 트랜젝션 확인</a></p>`);

설명을 하죠. 이렇게 Promise로 리턴 받은 receipt에서 트랜잭션 해쉬 필드를 클레이튼 스코프 사이트에 url 파라미터로 넘겨서 방금 처리된 트랜잭션 정보를 볼 수 있게 했습니다.
네 마지막으로 업데이트된 컨트랙트 잔액을 html에서 다시 보여주도록 하구요.

return agContract.methods.getBalance().call()
  .then(function (balance) {
});

컨트랙트의 getBalance 함수를 다시 호출해서 컨트랙트에 남아있는 잔액을 불러오는 겁니다.
그리고,

$('#contractBalance').html("");        

기존에 컨트랙트 잔액 보여주는 곳 contractBalance div를 지우고 곧바로 업데이트 된 잔액을 보여줄 거에요.
그래서,

$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(balance, "KLAY") + ' KLAY' + '</p>');      

네 여기까지하면 모든 과정이 완성 되었습니다.
이제 테스트를 해보도록 하죠.
이번에는 owner 계정 말고 다른 계정으로 로그인 해 보겠습니다.
여러분은 owner 계정으로 계속 진행하셔도 되고요, 만약 계정 하나 더 만드셨다면 저처럼 테스트해 보셔도 됩니다.

저는 먼저 로그아웃하고요, 로그인 해서 다른 계정 선택하고 계정 인증을 하겠습니다.
네 그러면 클레이 컨트랙트로 보내는 파트 안 보이죠.
이거는 owner 계정이 아니니까요.
이제 문제를 한 번 맞춰보자.
어려운게 나왔습니다. 근데 또 헤맸구요.
네 맞췄습니다.
정말 스릴 넘치는 게임입니다.
네 이렇게 맞추면은 확인 버튼을 통해 receiveKlay 함수가 호출되구요 그러면 트랜잭션이 진행되고 트랜잭션이 곧바로 마치면서 알림메시지 창이 뜨구요 성공적으로 트랜잭션이 완료됬습니다.
이거 닫으시고 자 그러면은 이벤트 잔액이 줄어 있는 것을 확인할 수 있죠.
컨트랙트에 있는 잔액이 사용자 계정으로 옮겨가면서 이렇게 줄어든 겁니다.
그리고 아래쪽에 링크가 생성이 됬는데 이거 링크 클릭해 보시면은 네 우리가 방금 생성했던 트랜잭션의 정보를 이 스코프에서 바로 확인할 수 있습니다.
그리고 내 계정 주소 클릭해보면은 여기에 balance가 더 늘어나 있는 걸 확인해 보실 수 있을 거에요.
여기까지 정답을 맞추고 컨트랙트에 있는 클레이를 내 계정으로 transfer하는 부분을 같이 해보았습니다.
