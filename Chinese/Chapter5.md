# 5. Front-end for Klaytn Addition Game development

## 5.1 Settings


现在您已经创建了一个将在之前的类中用于BApp的合同，让我们进行前端开发。
首先，让我们继续进行基本配置。
在本教程中，我将下载node.js，npm，truffle框架和visual studio代码。
Node.js是一个服务器端JavaScript平台，我们真正需要我们的BApp。
Npm与node.js一起安装，这是在开发时下载工具和库所必需的。
我们将安装的Truffle框架也需要通过npm下载。
如果已经安装了node.js和npm，请检查版本并跳过此部分，如果node.js是版本8或更高版本且npm是版本5或更高版本。


请访问 https://nodejs.org 并下载10.15.3 LTS。请安装它。 我已经安装了它，所以我正在跳过。 安装完成后，我们将检查PowerShell中是否正确安装了node.js. 键入Node-v并检查版本。并检查npm。 Npm -v，是的，它已正确安装。


最后，我将安装松露。
松露是一个框架，可以帮助您轻松开发BApp。
它允许您编译，测试和部署智能合约。
这是一个非常流行的框架。
Truffle版本最近已更新至5。
但是，由于Klaytn已经开发用于版本4，我将使用松露版本4。
如果已安装版本4或更低版本或5，则需要先将其删除。
通过在PowerShell中键入`npm uninstall -g truffle`来卸载它。
现在插入'npm install -g truffle@4.1.15'，我将通过安装它获得版本4。


如果您下载了所有内容，请通过truffle version命令检查版本。
它是4.1.15版本，而solidity编译器称为0.4.25版本。
Solidity是一种编程语言，您可以通过它编写智能合约。最后，让我们下载最好的代码编辑器，Visual Studio代码。来 'https://code.visualstudio.com/' 下载Windows。 我提前下载了它。所以，我也会跳过这一部分。
如果您下载它，请安装并运行它。
Visual Studio代码支持跨平台，因此可在Linux，Windows，Mac上运行，并包含许多便捷功能，如调试支持，git控制，语法突出显示等。




现在单击下面的扩展选项卡以安装扩展以支持可靠性语言。请输入'solidity'并选择顶部的那个。
单击安装。此扩展为每个solidity语法提供颜色突出显示，并允许您编译。
安装完成。我将结束前端开发所必需的配置会话。
 
 
## 5.2 Download boilerplate
 
让我们下载锅炉板，开发的基本模板。
Klaytn说，BApp可以在Truffle框架中开发。
 在Truffle中有一些地方允许您下载BApp开发的标准模板。
 
它被称为 Truffle Box. 
‘https://truffleframework.com/boxes’ 
如果你来这里，你可以看到模板。
 例如，如果您想使用Angular或React开发BApp，可以下载适合您的模板。
但是，此处下载的模板专门用于以太坊应用程序，因此您必须下载并删除内部部件。
 你必须为Klaytn设置它。
这不是一个难点，但我提前下载了名为webpack的模板
并以“Klaytn方式”改变它以适应我们的演讲。
 我把它放在Github上，以便你可以下载它。
 供您参考，我们将继续使用JavaScript native和JQuery以实现公平性。
 即使你是新手，也可以轻松地遵循它
 
使用PowerShell并在要下载它的位置的 'https://github.com/kkagill/addition-game-starter.git' 中运行git clone命令。 
我把这全部下载了。
做'加入 - 游戏 - 初学者'进入那条道路。现在代码。让我们通过插入'代码'来看结构。
让我先从头顶开始。
Contracts文件夹是保存solidity合同文件的位置。
我们已经创建了“Addition Game”合同文件，我们在下面有一个名为“迁移”的合同，允许您在部署智能合约时在下面的迁移文件夹中运行脚本文件。
这是部署合同的必要文件，因此您永远不应删除它。
 
接下来，`migrations`文件夹中的脚本文件包含部署过程中使用的逻辑。
如果您看到此文件，它将导入迁移合同文件并将其内容部署到Klaytn节点。
在src文件夹中，我已经建立了一个包含BApp前端的结构。 index.html文件将负责前面显示的“视图”。
我用cdn加载了用于BApp的jquery或bootstrap，我提前在下面添加了css部分。
 
Index.js文件就像一个引擎 - 它执行函数。
我们已经定义了将来要编写的函数的名称。
底部的变量是一个配置变量，它在加载时显示微调器。它不是一个重要的部分，所以我提前添加了它。
Package.json是通过npm添加必要依赖项的地方。
重要的是你将下载一个库文件，允许你与caver-js，Klaytn区块链进行通信。
它类似于以太坊的web3 js。
Truffle.js负责建立环境。
通过松露，您将定义部署智能合约的网络。
我将在下一讲中介绍这一点。
Webpack优化文件并在代码发生变化时进行检测，并在不必刷新页面的情况下将更改反映到浏览器。
到目前为止，我已经下载并解释了入门模板，以制作Klaytn加法游戏BApp。
 



## 5.3 Deploying smart contract to Baobab 1
 

从现在开始，让我们将我们制作的AdditionGame智能合约部署到猴面包树测试网。在开始之前，我们将在终端中运行npm install命令并为BApp安装必要的依赖项。
如果您没有看到下面的终端，请在“终端”选项卡上选择新终端。
现在运行npm install命令。
这需要一些时间。完成后，将创建名为“node_modules”的文件夹，并完成依赖项安装。
 
 
 
首先，让我们在迁移文件夹中创建一个新文件。
 右键单击“迁移”文件夹，然后选择“新建文件”。将名称设置为“2_deploy_contracts.js”，我们将添加逻辑以将AdditionGame合同部署到节点。
 
转到“Initial migration”文件，然后复制并粘贴所有代码。
请将其更改为“导入AdditionGame合同”。
用`AdditionGame替换要部署的部件。到目前为止，部署的基本逻辑已经结束。
但是，我会在BApp中的一些文件中编写一些代码来存储我从部署过程中获得的信息。稍后，使用此信息创建合同实例非常有用。
deployer.deploy（AdditionGame）
 
部署者部署AdditionGame合同，然后通过`then`我们收到要承诺的json数据。
在这，
 
if (AdditionGame._json) {
 

如果您已收到Additions游戏的json数据，您将通过文件系统模块将其保存到文件中。
要做到这一点，你必须先导入它。
在顶部添加`const fs = require（'fs'）`。
那么，我将创建两个文件。这些文件是我们可以保存Abi和合同地址的地方。右键单击后台中的任意位置，并将新文件命名为“deployedABI”。
创建另一个并将其命名为“deployedAddress”。
现在我们将使用文件系统将它们存储到每个文件中。
首先，让我们创建一个存储abi信息的代码。
Abi是区块链和合同之间可以互动的内容。

  	fs.writeFile(
    	'deployedABI',
    	JSON.stringify(AdditionGame._json.abi),
 
文件系统中有一个writeFile函数。定义要写入的文件，并将我们从json收到的abi信息串起来并将其传递给参数。最后，我们将处理错误。
 
    	(err) => {
      	if (err) throw err
      	console.log("ABI在文件中输入成功");
    	})
	

如果有错误，请抛出它。如果不是，请在控制台写入日志。这会将已部署的合同的abi信息作为文字保存在已部署的ABI文件中。要继续，我将已部署的合同的地址保存到文件中。

fs.writeFile(
  	'deployedAddress',
  	AdditionGame.address,
  	(err) => {
    	if (err) throw err
    	console.log("
地址在文件中成功输入");
	})

如果您已经跟踪了所有阶段，现在我们可以在每次部署后立即将所需信息存储在每个文件中。我将继续在truffle.js中设置环境并在下一讲中进行部署。
 
 
 
## 5.4 Deploying smart contract to Baobab 2
 
 

最后，您需要设置设置。您必须决定要部署哪个网络。
转到Truffle.js文件。在这里，我将从现在开始定义它。首先，我将导入名为的库
`connect-privkey-to-provider.`
const PrivateKeyConnector = require('connect-privkey-to-provider')
 

还创建一个称为网络ID的常量。
 
const NETWORK_ID = '1001'
 
1001表示Baobab唯一的网络ID。
const GASLIMIT = '20000000'
 
This is the gas limit for deployment. There are seven zeros.
const URL = `https://api.baobab.klaytn.net:8651`
 

对于UR，我已经分配了Klaytn的整个节点当前运行的地址，即猴面包树测试网。最后，我们需要一个常量来保存密钥，因此我们将通过Klaytn Wallet获取我们之前创建的帐户的密钥。我告诉过你们要把密钥保存在其他地方。我正在复制并粘贴我在记事本中保存的内容。

const PRIVATE_KEY = ''
 
 
现在让我们在module.exports中使用这些设置。
module.exports = {
  networks: { 
	klaytn: {
  	provider: new PrivateKeyConnector(PRIVATE_KEY, URL),
  	network_id: NETWORK_ID,
  	gas: GASLIMIT,
  	gasPrice: null,
	}
  },
}
 
我先解释一下。我说我们会用'Klaytn'作为网络。
现在，在此处指定四个选项。首先，指定提供Klaytn节点的提供程序。创建一个PrivateKeyConnector实例并传递两个参数。
第一种是传递我的帐户密钥，第二种是传递运行完整节点的网络地址。
这将允许我使用我的密钥连接到猴面包树testnet。
分配网络ID和气体，最后将天然气价格设置为空值。这是因为猴面包树网络会自动设定汽油价格，所以我们传递空值。
是的，到现在为止我已经设置了我的环境来部署智能合约。这很简单。现在让我们来部署它。在终端中，运行`truffle deploy -network klaytn`。是的，刚刚成功部署。您可以在控制台上看到确认短语。
 
 
 
现在，如果查看已部署的ABI文件，则会存储abi信息。转到已部署的地址，并注意已存储已部署合同的地址。它运作良好。最后，在部署它时，会创建一个名为build的文件夹。它里面有`contract`文件夹，两个json文件在contract文件夹中。它们被称为工件。每个工件文件包含相应合同的ABI信息以及与合同相关的所有信息。 ABI是应用程序二进制接口的缩写;我们以前在其中存储了一个已部署的ABI文件。在abi中，我们看到以json格式编写的函数和变量，我们将其用于AdditionGame契约。
 
简单地说，当您将此合同部署到区块链时，此abi保证调用合同中的函数并确保以我期望的格式返回数据。您可以在此定义如何与合同进行交互。如果你到底部，有一个网络部分。 1001是Klaytn独特的网络ID。地址是此合同当前部署在Baobab testnet上的此地址。
 
 
truffle deploy –compile-all –reset –network klaytn
 
 
实际上，如果要将合同重新部署到Klaytn节点，可以使用此命令。例如，当我们需要修改合同时，我们需要将其重新部署到节点。 `truffle deploy -compile-all -reset -network-Klaytn`
编译所有重新编译所有合同。重置会强制重新运行Migrations文件夹中的脚本文件。运行它以再次将合同重新部署到节点。是。成功完成。打开deployAddress文件，您将看到地址已更改。到目前为止，我已经使用松露将合同部署到Klaytn Baobab网络。
 
 
 
 
## 5.5 Account verification UI
 

让我们首先登录您的baobab钱包创建的帐户。
我们有两种方式来验证我们的帐户。
 首先，您可以使用密钥库文件和密码的组合，其次，使用私钥进行验证。
我们实现它的方式是通过密钥库文件和密码的组合进行验证。
首先，我将编写HTML代码。
转到Index.html并在body标记内添加内容。

```
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
 ```
 


请立即停止此视频并编写此代码。
设置非常简单。
div中的类使用bootstrapping使UI看起来不错。
 我将跳过引导程序描述。
首先，我将解释性短语放在上半部分。
下面我们添加了登录和注销按钮。
当我点击登录按钮时，它将启动一个模态窗口。
单击注销按钮时将执行handleLogout功能。
请注意，我设置的注销按钮没有出现在css中。
让我们运行应用程序，我们将检查我们编写的代码是否正常工作。
在终端上运行npm run dev命令。
运行Chrome并转到localhost：8081地址。
是的，它不是那么美丽，但看起来很好看。
现在，让我们创建一个模式，当我们单击登录按钮时会弹出该模态。
‘https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals’ 

如果你来到这个引导站点，你可以获得模态代码。
复制此部分并返回到html文件。
我将它粘贴到容器div之外。
现在让我们改变这个模态的内容。
首先，将div id设置为loginModal。
部分。
  <div class="modal fade" tabindex="-1" role="dialog" id="loginModal">
 
你应该这样，这样你就可以在点击登录按钮时打开模态。
它将模态与顶部登录按钮的data-target属性的值匹配。
接下来，我们将模态的大小更改为更小的模型。
 
  <div class="modal-dialog modal-sm">
 
 
删除所有模态标题部分。
此外，删除模态体内的内容。
现在添加可以加载密钥库文件的部分和输入密码的部分。
<div class="form-group">
   <label for="keystore">Keystore</label>
   <input type="file" id="keystore" onchange="App.handleImport()">
</div>
 

我将输入类型作为文件，并在onchange事件上调用handleimport函数。
 在此之下，添加密码部分
 

复制并粘贴在顶部。
<div class="form-group">
  <label for="input-password">비밀번호</label>
  <input type="password" class="form-control" id="input-password" onchange="App.handlePassword()">
   <p class="help-block" id="message"></p>
</div>
 
 
如果该值写入密码输入窗口，请调用handlePassword函数。
 当验证成功或发生错误时，我添加了要显示为消息的部分。
最后，将“close”更改为“닫기（close）”并将“safe changes”更改为“submission”
<button type="button" class="btn btn-default" data-dismiss="modal">닫기</button>
        	<button type="button" class="btn btn-primary" id="submit" onclick="App.handleLogin()">제출</button>
 

添加id属性并允许在单击时调用handleLogin函数。
是的，我现在将检查已完成的代码在视图中是否正常工作。
单击登录按钮。
那么，模态已启动，您可以选择文件并输入密码。
到目前为止，我已经创建了一个验证帐户的UI。
 
 
## 5.6 Account verification logic (keystore validation)
 
 
 

现在我们已经创建了上面显示的UI，让我们实现逻辑以使其工作。
 在Index.js中，常量中有各种函数叫做App。
最后，当你下来时，你会发现你可以知道的第一件事就是当你加载页面时，它会启动App常量中存在的启动功能。
所以我们将实现start函数，但在此之前，我们需要加载caver.js库以与Klaytn区块链进行通信并实例化它以便它可以用于BApp。
从“caver-js”导入Caver;
 
在顶部，导入caver.js。
并为环境设置创建一个常量。
 
const config = {
  rpcURL: 'https://api.baobab.klaytn.net:8651'
}
 
 

配置中有一个rpcURL。
我们已经定义了要连接和使用的Klaytn节点。
我说这是猴面包树测试网。
最后，我们将创建一个常量，通过将其传递给Caver构造函数来实例化rpcURL。
const cav = new Caver（config.rpcURL）;
 
 
实例化的工作结束了，这个cav常量现在可以在应用程序中找到。
 现在您必须启动该功能，但在此之前，在启动功能中，您必须首先检查该帐户是否已通过会话进行验证。
但是，我将稍后将这部分留待，因为我们将在后面的讲座中使用会话，所以暂时将启动功能留空。
让我们首先实现handleImport函数。
 我们应该能够点击登录按钮并在模态弹出后选择密钥库文件。
但是，必须验证此文件是否实际上是有效的密钥库文件。
我们在handleimport函数中这样做。
首先，我们创建一个FileReader对象并将其放入常量中。
const fileReader = new FileReader（）;
 
 
并使用readAsText函数读取所选文件。
fileReader.readAsText(event.target.files[0]);
 
 
event.target.files, this part means the file we selected. 
When readAsText execution is completed, the FileReader's onload event occurs.
fileReader.onload = (event) => {  	
  
}
 
现在可以在此代码块中使用回调接收的事件，换句话说，文件的内容。
将检查此文件的内容是否是有效的密钥库文件。
首先，在里面添加一个try catch块。

  try {
   	
  } catch (event) {
   	
  }
 
 

现在，如果文件的内容有效，我们将检查if-sentence，换句话说，如果这是一个实际的密钥库文件。

if (!this.checkValidKeystore(event.target.result)) {
 
}
 
 
我将我们读取的文件的内容作为参数传递给函数checkValidKeystore。
 现在让我们来装饰checkValidKeystore函数。
此函数将密钥库作为参数并接收文件。
我收到的密钥库文件是一个json文件。
我将其更改为Javascript对象，以将此json文件中的属性用作变量。

	const parsedKeystore = JSON.parse(keystore);
 
 
我使用json parse函数来分析keystore文件的内容，将其转换为对象，并将其存储在常量中。
接下来我们该怎么办？
确保已正确输入密钥库配置所需的属性。
让我们看看密钥库文件，看看我们需要什么。
密钥库配置的基本要素是版本，标识，地址和加密。
如果没有这四个字段，密钥库文件就不能是密钥库文件。
所以，我会通过代码检查它。

const isValidKeystore = parsedKeystore.version &&
  	parsedKeystore.id &&
  	parsedKeystore.address &&
  	parsedKeystore.crypto;
 
 

最后，返回此常量。

return isValidKeystore;
 
 
我再次上​​去验证我刚刚导入的文件是否是有效的密钥库文件。
如果没有，通过消息显示它无效并结束该功能。
$('#message').text('keystore 文件无效. ');
return;
 

如果它通过了验证，我们将把密钥库文件的内容保存到全局变量中。
首先，我们需要创建一个全局变量。在启动功能上创建它
 
auth: {
	accessType: 'keystore',
	keystore: '',
	password: ''
  },
 
 
Auth对象中有三个字段。
 accessType是一种验证方法，具有密钥库类型和私钥类型。
我们正在进行密钥库类型。
Keystore字段存储密钥库文件的全部内容。
 最后，password是包含将与密钥库文件组合的密码的字段。
如果我们回到函数并通过验证，
this.auth.keystore = event.target.result;
 
 
将加载文件的全部内容发送到我们创建的auth变量的keystore字段。
之后，发送一条消息说我成功了。

$('#message').text('keystore 通过. 请输入您的密码.');
 
可以立即在密码字段中输入密码。
 
document.querySelector('#input-password').focus();
 
最后，在读取文件时，如果有错误，请在catch块中发送错误消息并终止该函数。

$('#message').text('keystore 文件无效. ');
return;
 
 
是的，到目前为止Handleimport功能已经很好地实现了。
我们现在试试吧。选择密钥库文件。
将显示通过消息，焦点将移动到可输入密码的部分。
为了测试相反的情况，让我们选择任何随机文件。
好的，生成错误消息。
它运作良好。
现在，让我们创建一个函数，在输入密码时将密码存储在全局变量中。
这将非常简单。
如果转到html，则在输入密码时会调用handlepassword函数。
然后，在handlepassword函数，
this.auth.password = event.target.value;
 
通过html onchange事件检索密码值，然后将其分配给全局变量auth的密码字段。
 这很简单。
到目前为止，我已经完成了密钥库文件的验证文件。
 在下一讲课中，我将创建一个密钥并将我的帐户信息添加到电子钱包中。
 
## 5.7 Account verification (integrate wallet)
 

我们已经完成了检索密钥库文件和输入密码的部件，
现在，当我们将此信息发送到baobab节点时，我们将检查帐户是否已成功验证。
在此之前，我将rpcURL中的http替换为https。
看看Index.html。
当我点击提交按钮时，它会调用handlelogin函数。
所以让我们实现这个功能。
首先，确保访问类型是密钥库。

if (this.auth.accessType === 'keystore') { 
}


我们写这个'if'语句的原因是，在验证帐户时，我们使用密钥库或私钥。
我们现在只使用密钥库。
但是，我添加了这些if语句，以便在您想使用私钥进行验证时，
你可以用它。请在下面添加`try catch`声明。
 
try {       
} catch (e) 
}

是时候最终使用caver实例了。
我会在这里给你一个测验。
我们可以通过密钥库文件和密码的组合获得什么？
如果你记得很清楚，你马上就能知道。
是的，您可以获得私钥。
此密钥允许您创建Wallet实例。
因此，您需要做的第一件事就是通过密钥库文件和密码获取密钥。

const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;


您可以通过caver实例的accounts成员使用decrypt函数。
这意味着要解密。
如果解密它，则可以通过将密钥库文件的内容和密码作为参数传递来返回解密的帐户对象。
对象中有各种成员，其中，我们获取私钥并将其存储在常量中。
如果解密时出错，将发送一条消息。

$('#message').text('密码不匹配.');
$(‘#message’).text(‘password is not matched.’);
 
 

如果没有错误，它将通过您的密钥创建一个Wallet实例。

 
this.integrateWallet(privateKey);



将私钥传递给integratewallet函数。
现在，转到integrationwallet函数。
在这里，我们使用privatekey添加获取Wallet实例的代码。
 
const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);
 

这个walletinstance有我的帐户信息。
然后将此实例添加到我的电子钱包中。

cav.klay.accounts.wallet.add(walletInstance)
 


如果您将我的帐户添加到caver钱包，
在将来创建交易时，您可以通过caver实例轻松调用您的帐户信息。
下一步是将Wallet实例存储在会话存储中。
SessionStorage会将Wallet实例存储在Web浏览器的存储空间中，直到选项卡关闭或Web浏览器关闭。

sessionStorage.setItem('walletInstance', JSON.stringify(walletInstance))
 
 


SetItem将键值作为一对接收。
第一个参数是键，第二个参数是值。
所以，我必须稍后将我的帐户信息加载到会话中。
当您使用键值调用walletInstance时，将自动加载存储在该对中的值。
使用sessionStorage的原因是保持帐户登录。
因为当我访问其他网站或页面刷新该信息时，存储在我的caver钱包中的帐户信息会消失。
但是，如果您保存到会话存储，
即使您暂时访问其他网站，然后返回该网站或刷新该网页，您的帐户信息仍会保留。
所以我稍后会在start函数中实现一个Wallet实例会话并保持登录状态。
现在我需要更新UI。
现在我们已经通过integrateWallet完成了帐户验证，我们需要适当地更改UI。

this.changeUI(walletInstance);  


我正在向changeUI函数发送一个Wallet实例。
那么我们如何处理changeUI功能呢？
关闭你的模态。
$('#loginModal').modal('hide');
 


隐藏登录按钮
$("#login").hide();
 

此外，更改之前隐藏的“注销”按钮。
 
$('#logout').show();

由于您已登录，因此我希望我的帐户地址可见。
$('#address').append('<br>' + '<p>' + '내 계정 주소: ' + walletInstance.address + '</p>');   
 

此代码告诉我它在html中显示id属性为address的帐户地址。
我将转到index.html并添加一个div。
  <div class="text-center" id="address"></div>    

是的，您可以在此位置查看我的帐户地址。
我会在这里做的。
现在让我们来测试吧。
单击“登录”按钮，然后打开密钥库文件。
如果您输入密码并按提交按钮，则会验证您的帐户并显示退出按钮。
您可以在下面看到我的帐户地址。
最后，让我们实现注销功能。
转到Index.html。
请注意，当我单击注销按钮时，我会调用handlelogout函数。
我会去那里
这里我们将调用一个名为removeWallet的函数。
this.removeWallet();
 


我们将清除钱包并使用此功能清除会话存储。
转到removeWallet函数并添加此代码。
cav.klay.accounts.wallet.clear();
 

这是删除我的电子钱包实例的过程：添加到钱包的帐户信息。
然后清除会话。
 
sessionStorage.removeItem('walletInstance');

当您删除它时，只需输入键值即可。
最后，它调用reset函数并结束。
this.reset();
 

此重置功能只是初始化全局变量auth。
转到重置功能并初始化auth。
this.auth = {
      keystore: '',
      password: ''
    };
 

Auth中还有一个访问类型。
但是，您不必擦除accesstype，因为它无论如何都将是一个密钥库。
相反，当我们登录时，将输入一个值到密钥库和密码字段。
我想退出并安全地删除它。
返回handleLogout函数并放置刷新页面的代码并完成它。
刷新的原因是返回初始状态UI。
location.reload（）;
 

现在让我们进行测试并完成。
单击“注销”按钮，帐户信息将消失，您将通过刷新返回初始化屏幕。
现在您已经完成了帐户验证逻辑，
让我们完成在下一课程中通过会话存储维护帐户验证的部分。
 
 
## 5.8 Account Session 

让我们看看当我们登录并刷新页面时会发生什么。
单击登录按钮，然后选择密钥库文件。
在此状态下，按F5刷新。
然后它将被重置。
如果我一直登录会很好。
我该怎么做？
如果我们成功登录，则会将帐户存储信息保存到会话存储中。
我现在就用它。
BApp运行时加载的第一个函数是start函数。
在这里，我检索存储在会话存储中的帐户信息。
那么，让我们去启动功能，
const walletFromSession = sessionStorage.getItem('walletInstance');
 

如果使用getItem并传递键的值，则会获取存储在该对中的值并将其存储在常量中。
我保存了我的电子钱包实例。
接下来，确保walletFromSession包含值。
if (walletFromSession) {
 
}
 

If there is a value, create a try catch.
try { 
     
} catch (e) {
 
  }
 

然后将您的帐户信息添加回caver钱包。
cav.klay.accounts.wallet.add(JSON.parse(walletFromSession));

刷新或重新访问页面时，添加到电子钱包的现有帐户信息将被删除，因此我会通过会话将其添加回来。
更新UI以显示您已登录为下一个。
  this.changeUI(JSON.parse(walletFromSession));
 

这将变为退出按钮并显示您的帐户地址。
最后，当sessionStorage中的值不是有效的Wallet实例时，它将转到catch语句。
然后删除会话存储中的walletinstance。
sessionStorage.removeItem（ 'walletInstance'）;
 

这是在这里完成的。
现在，让我们来测试一下。
刷新它时，它会保持登录状态而不会返回初始化状态。
到目前为止，我们已经实施了维护帐户验证的一部分。
 
 
 
 
## 5.9 KLAY transfer via contract (deposit)
 

我现在将使用运营商帐户将KLAY发送给合同。
首先，让我们创建一个UI。
您可以在div类行下创建它。
 
<br />     
 
    <div class="row text-center">
      <div class="col-md-2 col-md-offset-5">
        <div id="owner" style="display: none;">
          <hr />
          <label>将KLAY发送给合同</label>
          <div class="input-group">             
            <input type="number" class="form-control" id="amount" />
            <span class="input-group-btn">
              <button type="button" class="btn btn-default" onclick="App.deposit()">송금</button>
            </span>
          </div>
        </div>
      </div>       
    </div>
 

请模糊视频并添加此部分。
我将简要解释一下。
我已经设置了UI部分，通过css将资金发送给隐形合约。
我们将存款功能设置为在输入金额时按下并按下转移按钮。
现在让我们进入存款功能并实施它。
 
我将在这里解释如何首先实现它。
Klay转让合同只能通过所有者帐户进行。
只有部署合同的人员才能进行此操作。
换句话说，只有此事件的组织者才能发送它。
如果我们使用所有者帐户，我们将访问合同中的存款功能并转移KLAY。
流程非常简单。
首先，我们将创建一个实例，以便我们可以访问我们部署的合同。
创建合同实例时，您需要部署的合同的abi信息和地址。
在顶部的腔常数下，
const agContract = new cav.klay.Contract（DEPLOYED_ABI，DEPLOYED_ADDRESS）;

这里的deployed_abi和deployed_address是可以在BApp中使用的全局常量。
部署合同后，我们会将信息保存到deployedabi文件和deployedaddreess文件中。
将它设置在webpack中，以便我们可以读取此信息并将其用作全局常量。
如果您转到Webpack.config.js文件，将会有一个带注释的部分。
现在解决这个问题。
在webpacks的编译时，运行此部分以设置称为已部署地址和已部署abi的全局常量。
 
简而言之，我们通过文件系统读取已部署的地址文件，并将合同地址分配给全局常量。
以同样的方式，我们将abi信息存储在deployabi文件中的全局常量中。
让我们回到Index.js文件。
 
 

所以请记住，发送给合同实例的创建者的这两个abi和地址信息是通过webpack生成的全局常量传递的。
现在我们已经创建了一个四个合同实例，我们将继续使用存款功能。
在寄钱之前我们必须先检查一下。
您应该验证您刚刚登录的帐户是否为所有者帐户。
所以我必须提出两条信息。
首先，我正在检索当前登录的帐户信息。
其次，我将检索存储在合同中的所有者状态变量。
首先，我将检索我的登录信息。
const walletInstance = this.getWallet（）;

转到getwallet函数并获取当前caver钱包中存在的帐户信息。
if（cav.klay.accounts.wallet.length）{
      return cav.klay.accounts.wallet [0];
    }


电子钱包[0]是第一个添加到电子钱包的帐户，我目前登录的帐户。
到目前为止，您已完成功能实现。
接下来，让我们在合同中调用所有者状态变量的值。
转到callOwner函数
return await agContract.methods.owner（）。call（）;
 

我们将通过我们创建的addgame合约实例访问所有者函数并调用该值。
使用await关键字异步接收值。
由于我们在向您发送货款之前已经提供了必要的内容，因此我们将继续使用存款功能。
if（walletInstance）{
 
    }
 

如果通过getwallet函数存在Wallet实例，
将当前登录的帐户地址与合同返回的所有者的帐户地址进行比较。
if（等待this.callOwner（）！== walletInstance.address）return;
 

如果我们比较它们，但值不同，我们不再继续，我们终止该功能。
 如果它是相同的
其他{
}
 

获取为Html输入输入的值。
var amount = $（'＃amount'）。val（）;

如果输入值存在
if（amount）{
}
 
使用合同实例将值发送到存款功能。
 
agContract.methods.deposit（）。发送（{
 
}）


这里我们发送一个事务对象作为发送因素。
我们需要指定三件事。
首先，我们必须告诉谁正在调用此函数。
来自：walletInstance.address，
 
我说我们将使用当前登录的帐户调用此函数。
请注意，Walletinstance的地址是已完成帐户验证的帐户，并且有权签署交易。
所以我不能在'from'中添加任何地址。
只有在BApp中验证过的地址才能用作值。
并将燃气消耗量设定在250,000以内。
 
天然气：'250000'，
 

由于合同中的存款功能是应付的，因此您必须传递价值字段。
值：
 

我们必须将从html输入接收的数字转换为peb，这是KLAY的最小单位并通过它。
使用caver库实用程序转换它。
cav.utils.toPeb（金额，“KLAY”）

您现在可以通过合同存款功能汇款。
但我可以使用异步接收的信息，而不是像这样完成事务。
.once（'transactionHash'，（txHash）=> {
    console.log（`txHash：$ {txHash}`）;
}）
 

首先，我可以获取事务哈希，并使其在控制台上可见。
请注意，控制台日志包装器不是单引号，而是数字1左侧的引号。
小心。
接下来，您可以获得收据。
.once('receipt', (receipt) => {
   console.log(`(#${receipt.blockNumber})`, receipt);          
})


获取收据意味着事务已成功添加到块中。
因此，您可以检查收据以查看添加交易的块。
如果事务处理失败，您可能会收到错误。
.once（'error'，（error）=> {
   警报（返回Error.message）;
  }）;
 

如果出现错误，将显示一条消息。
我已经完成了在发送事务后检查成功的逻辑。
最后，如果html输入中没有收到任何金额，请添加一个终止该函数的return语句。
返回;
 

我已经完成了将KLAY发送到合同存款功能的部分，我将更改UI并在下一课中测试它。
 
 
## 5.10 KLAY transfer via contract (UI change and testing)
 
 

我会尝试更改UI和测试。
当我们将KLAY发送到前一课程的存款功能并收到收据时，交易成功。
我成功后该怎么办？
如果系统可以向我显示您的提醒消息，那将是很好的。
   警告（金额+“我已经将KLAY发送给合同。”）;
 

我将刷新页面以查看合同的余额。
   location.reload（）;
。

我说我打算让合同的余额可见。
请记住，我们创建了一个函数，可以在我们编写智能合约时加载合同的余额。
我们将调用此getBalance函数，以便我们可以看到合同的余额。
首先，我们将添加一个div，用于显示html中合约的余额。
转到Index.html并在显示我的帐户地址的地址下添加一个div。
  <div class =“text-center”id =“contractBalance”> </ div>

然后我们将在这里向您展示合同的余额。
现在视图已准备就绪，让我们创建一个从后端加载平衡的函数。
转到callcountractbalance函数并添加代码。
return await agContract.methods.getBalance（）。call（）;
 

通过契约实例访问getbalance函数并加载值的部分。是的，很简单。
从现在开始我在哪里调用这个callcountractbalance函数？
我应该在哪里打电话？
如果交易在存款功能中成功并收到收据，则会通过location.reload（）刷新页面。
刷新页面时执行的第一个函数是什么？
首先执行启动功能。
然后，我们从start函数调用changeUI函数。
我需要添加代码来从更改UI的changeUI函数加载合同余额。
$（'＃contractBalance'）。append（'<p>'+'이벤트잔액：'+ cav.utils.fromPeb（等待this.callContractBalance（），“KLAY”）+'KLAY'+'</ p>' ）;

这有点长。
我会解释一下。
我们将在显示合同余额的部分中添加一条消息。
调用callContractBalance函数以获得平衡。
但是，天平将加载到KLAY最小单位peb中。
这会让人很难看到用户座位上剩下多少，因为单位太大了。
因此，caver实用程序有一个名为fromPeb的函数。
它是一个可以从peb转换为另一个单元的函数。
我已在第二个参数中指定转换为KLAY。
结果，它显示合同余额在html中转换为KLAY。
 

最后，必须仅为所有者帐户设置KLAY转移到合同。
您只需要授予活动组织者许可。
因此，我将更改它以显示仅在我使用所有者帐户登录时才能传输的UI。转到changeUI函数
if（等待this.callOwner（）=== walletInstance.address）{
      $（ “＃业主”）显示（）。
    }
 
我已将所有者div设置为仅在所有者帐户地址和登录帐户地址相同时显示。
在html中，默认情况下，所有者div设置为不可见。
因此，当您使用所有者帐户登录时，您将看到此部分。
现在让我们试试吧。
我将重新部署一次。
首先，确保在truffle.js中正确输入了您帐户的密钥。
我将从终端重新使用它。
'truffle deploy -compile-all -reset -network klaytn'我正在为没有部署它的人重新部署它。
您的部署已结束。
让我们通过运行npm run dev来检查它。按F12打开控制台窗口。
点击登录按钮...... ......
由于您使用自己的帐户登录，因此可以看到可以汇款的部分。
我们现在就汇款。发送1个KLAY。
 
 

当事务成功时，您可以通过控制台日志查看事务哈希和收据信息。
通知消息很有效。
似乎交易所需的时间少于3秒。
在这3秒内，有四个过程，从创建事务到创建块，并在事务完成时将其传播到网络。
与其他区块链平台相比，处理速度非常快。
单击通知消息，刷新页面，首先调用start函数，
更新的合同余额由其中的changeUI函数显示。
交易功能运作良好。
我想让一个加载微调器显示交易运行良好。
这不是必需的，但我建议您为良好的用户界面做这件事。
转到Index.js并将spin.js导入到顶部。
import {Spinner} from 'spin.js';

转到showspinner函数并使其返回微调器实例。
var target = document.getElementById('spin');
    return new Spinner(opts).spin(target);


并从存款功能调用此功能。
var spinner = this.showSpinner（）;
 
收到收据后，让微调器停止。
 
  spinner.stop();  


最后，添加一个div以在html中显示微调器。 <br />将它放在标签下面。
<div id =“spin”> </ div>
 

现在让我们试试吧。
是。随着微调器的出现，正在制作一个更加壮观的场景。
传递函数运行良好，并且UI得到了很好的反映。
到目前为止，我已经涵盖了从业主账户到合同的KLAY转账。

## 5.11Generating a random number


现在让我们尝试做一个有趣的部分。
让我们创建两个用于添加的随机数。
我先装饰Html。
请在旋转div上方直接添加此代码。

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
 

我用css看不见它。
登录后我会将其显示出来。
单击开始按钮可调用generateNumbers函数。
然后该函数将生成两个数字，一个用于num1，另一个用于num2。
用于添加。
并且有一个输入字段来写答案。
最后，还有一个提交答案的按钮。
简单的HTML。现在，
我会对其进行设置，以便只有经过验证的用户才能看到此部分。
转到changeUI函数并将其添加到logout.show（）下面以显示游戏div。
$('#game').show();
 

现在让我们用html检查一下。
如果您已登录，则可以在中间看到黄色框的漂亮UI。
现在，当您单击“开始”时，我将设置数字。
让我们在generatenumbers函数中创建随机数。
var num1 = Math.random（）;
 

首先，我们调用Math类的随机函数。
随机函数随机生成一个小数点低于0和1的数字。
但如果你这样做，数字太小，所以我要增加它。
var num1 = Math.random（）* 50;
 

这将生成0到49之间的随机数。
但问题不应该太容易，所以我将为生成的值添加10，以便您可以生成至少两位数。
var num1 = (Math.random() * 50) + 10;
 


最后，我们使用floor函数来丢弃小数点。
var num1 = Math.floor((Math.random() * 50) + 10);
 

如果这样做，您将得到10到59之间的十进制数。
接下来，创建另一个。
 
var num2 = Math.floor((Math.random() * 50) + 10);
 

现在我们将在会话存储中存储两个数字的附加值。
我会保存答案。
 
sessionStorage.setItem('result', num1 + num2);    

这将在用户回答时返回正确答案，并尝试比较用户给出的答案。
现在我们已经创建了数字，我们将不得不使用它。
当我点击HTML中的Start时，我会隐藏这个开头并让它显示下面的问题div。同时，我将在num1和num2字段中显示从函数生成的两个数字。
让我们回到功能并实现我们刚才所说的。
$('#start').hide();
 


让开始不可见。
$('#num1').text(num1);
$('#num2').text(num2);

让它显示num1和num2字段中生成的数字。
让它显示问题div。
$('#question').show(); 
	

最后，将焦点移到我写答案的位置，以便我可以立即回答。
document.querySelector('#answer').focus();

我现在要测试一下。
单击“开始”时，将生成随机数并以html格式呈现。
很快，焦点转移到我写答案的地方。
这是今天课程的结束，我将尝试在下一堂课中创建一个计时器。

## 5.12  Generating a timer



让我们创建一个计时器，并将添加问题的超时设置为3秒。
 转到Html并创建一个显示计时器的div。我会在旋转div下做正确的。
<div class="row text-center">
        <p id="timer"></p>
      </div>   
 
转到index.js并转到showtimer函数。这里我们使用setInterval函数来显示要倒计时的数字。我们将在3秒后使问题消失，屏幕恢复到开始点击。
 

创建一个变量以保存3秒钟。
$('#timer').text(seconds);

直接显示数字3到显示计时器的html。
我使用setinterval函数并将其设置为1秒间隔。
  var interval = setInterval(function() {  
  }, 1000);
 

现在我可以在1秒的间隔内运行一些东西。
$('#timer').text(--seconds);  
 


逐个减少数字，使其显示在html中。
现在，这个秒变量的值是0，也就是说，当3秒后setinterval为0时再次重置它。

if (seconds <= 0) {
}     
 

当秒数变为0时
 
$('#timer').text('');
 

初始化显示部分的数字

     $('#answer').val('');

它还初始化已回答的输入。

同时初始化已回答的输入。
$('#question').hide();
 

设置div不显示问题。和,
 
$('#start').show();          
 

再次显示div，您可以单击“开始”。最后，
  clearInterval(interval);
 

使用clearInterval停止在setinterval中运行的时间。是的，我创建了showtimer功能。现在让我们在generateNumbers函数中调用这个函数。
this.showTimer（）;
 
如果执行此操作，则单击“开始”后，将立即创建计时器并开始倒计时。我们来试试吧。
单击“开始”。将在下面生成一个计时器并开始倒计时3秒钟。 3秒后，它会再次重置。
到目前为止，我已经创建了一个计时器。
 
 
 
## 5.13 Submitting answers and receiving KLAY
 

这是最后一堂课。如果用户提交答案并且答案是正确的，那么让我们实现从合同中将KLAY发送到用户帐户的部分。转到submitAnswer函数。加载存储在会话存储中的正确答案的值。
const result = sessionStorage.getItem('result');
 

并且，存储用户在变量中所做的答案。
var answer = $（'＃answer'）。val（）;
 

现在，做一个比较。
if（回答===结果）{}
 

如果用户已回答正确答案，请在打开确认消息窗口时按确认按钮并将KLAY发送给用户。
if (confirm("那很好。^^ 0.1 KLAY 下载")) { }
 

如果用户单击确定按钮，请确保合同中的余额至少为0.1 KLAY，然后再发送。
if (await this.callContractBalance() >= 0.1) { }

如果是这样，请调用receiveKlay函数。
this.receiveKlay();
 


如果它不存在，请发送通知消息。
else { alert("抱歉。音乐会的KLAY已被消费。"); }    
 


最后，如果用户没有得到正确答案，请发送通知。
else { alert("丁！我是一名小学生。"); }
 
 
 

是的，您的submitanswer功能就在这里。
我们来测试一次吧。
答案错误时会显示此消息。
完成后，将出现确认消息窗口以接收KLAY。
单击“确定”后，您将调用receiveklay函数来传输KLAY。
我还没有实现它。
让我们实现这个功能。
这是我们的最后一项功能。
 
当用户回答正确答案时，他们通过他们的帐户支付交易费并获得KLAY。
我们将合同转移函数中的0.1 KLAY转换为peb并将其作为参数传递。
首先，让我们向您展示如何在事务处理期间使用微调器加载。
var spinner = this.showSpinner（）;

此外，我们需要交易所需的经过验证的帐户地址，因此，请加载电子钱包实例。
const walletInstance = this.getWallet();
 

如果钱包实例的值不存在，请退出该功能。
if (!walletInstance) return;  
 

如果是，请使用合同实例访问合同中的转移功能。
agContract.methods.transfer().send({
})
 
合同的转移函数收到一个论点。
您需要使用caver实用程序将KLAY转换为peb并传递它。
 
cav.utils.toPeb(“0.1”, "KLAY")
 
你说你需要在send参数中发送一个事务对象。
您需要指定谁调用此函数以及设置的气体限制量。
 
来自：walletInstance.address，
天然气：'250000'
 
通过电子钱包实例，您的帐户验证地址，让天然气消耗在250,000以内。
请注意，值字段不是必需的。
我不会传递该值，因为传递函数不是应付款类型。
如果这样做，您已完成将传递的所有值。
现在，在处理事务之后，您应该检查它是否成功。
我可以通过这个.once检查它（存款）是否成功。
但是，还有另一种方式。
我可以用诺言来收据。
 
.then(function (receipt) {
});     

异步等待并收到收据值。
if（receipt.status）{}

Receipt对象中有一个名为status的字段。
如果这是真的，那就成功了。
所以，如果你成功了，停止微调器。
spinner.stop（）;
 

另外，显示通知消息
alert("0.1 KLAY " + walletInstance.address + " 支付到您的帐户。");      
 
另外，让我们在html中创建一个链接，以便可以直接从作用域中检查已处理的事务。
我打算创建一个新的div。
我将在计时器div下进行。
<div class="row text-center">
   <div id="transaction"></div>
</div>  

<br />
 

您将在此部分中看到该链接。
返回该函数并首先清除事务div。
    $('#transaction').html("");
 

我正在清除事务div以在每次创建事务时显示新链接。
接下来，我将添加一个链接。
    $('#transaction')
      .append(`<p><a href='https://baobab.klaytnscope.com/tx/${receipt.txHash}' 
                   target='_blank'> 检查Klaytn Scope中的交易</a></p>`);

 
在承诺退回的收据中，
将transactionhash字段传递给KlaytnScope站点的url参数，以便您可以看到刚刚处理的事务信息。
最后，向您展示html中最后更新的合同余额。
 
return agContract.methods.getBalance（）。call（）
  .then（function（balance）{
}）;
 
调用合约的getBalance函数以调用合约中的剩余余额。
 
 $('#contractBalance').html("");          
 

清除现有的节目余额显示并立即显示更新的余额。
$('#contractBalance').append('<p>' + '事件平衡: ' + cav.utils.fromPeb(balance, "KLAY") + ' KLAY' + '</p>');           
 
到目前为止整个过程已经完成。
现在，让我们试试吧。
这次，我尝试使用其他帐户登录，而不是使用所有者帐户登录。
您可以继续使用所有者帐户。
如果您已经创建了另一个帐户，也可以尝试一下。
 
如果您解决了问题并按下OK按钮，则会调用receiveKlay函数。
将显示通知消息，并且已成功完成事务。
您可以关闭通知消息，并查看您的事件余额是否已减少。
合同中的余额在移至您的帐户时已减少。
并且链接是在底部创建的。
如果单击该链接，则可以看到有关我们刚在作用域上创建的轨道的信息。
点击您的帐户地址，您会发现余额正在增长。
到目前为止，我已尝试解决问题并将合同中的KLAY转移到我的帐户。
