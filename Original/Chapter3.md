## 3. Understanding "Klaytn"

# 3.1 Consensus
 
 
 
In previous chapters, we discussed the problems of the existing blockchain. Let's talk about how the Klaytn blockchain solves problems using a consensus algorithm. There are many types of consensus algorithms, such as PoW (Proof-of-Work) or PoS (Proof-of-Stake), which are commonly used in public blockchains, and PBFT (Practical Byzantine Fault Tolerance) or Raft, which are used in private blockchains. In general, private blockchains can reach an agreement more efficiently than public blockchains. In particular, BFT-based private blockchains can achieve high performance and efficiency by limiting the number of participating nodes. However, this configuration limits the number of consensus nodes, weakens decentralization, and the content of consensus results is only disclosed to small groups. As a result, it limits transparency and harms the benefit of blockchain.

On the other hand, Klaytn chooses Istanbul BFT as a consensus algorithm since it believes that by well utilizing BFT's advantages, it can combine both advantages of public and private blockchains. It’s aiming for a public blockchain that provides big enterprises-supporting performance and stability while maintaining strong security and transparency. To achieve this goal, Klaytn adopts a trust model of private consensus with public disclosure. It consists of a small number of private nodes that achieve consensus, and other nodes that can publicly access and verify the outcome of block generation. Now let's see more about Istanbul BFT (Byzantine Fault Tolerance) that Klaytn is using as an agreement algorithm.
 

 
 
The Istanbul BFT has a three-step consensus process. There are pre-prepare, prepare, and commit steps. Klaytn uses a round-robin method to pick proposer among the consensus nodes every round. It means to be a proposer. The remaining consensus nodes are validators. And do the verification.
 
If you look at the picture, there are proposer, validator 1, 2, 3, and so on. Among them, the node marked with X is in a state that it is currently in a faulty state. It means that it is not functioning properly as a verifier. When the computer is broken, the network is disconnected, or the computer maliciously acts this kind of thing happens.
 
The first step is a “propose” in which one of the consensus nodes is selected as a proposer.
The second step is a pre-prepare where the proposer node creates blocks and makes suggestions to other nodes.
Then, send the suggestion to the validator 1 node, send it to the validator 2 node, and send it to the validator 3 node.
This is the step to pass along with the message.
 
 
 
In the third prepare step, when the verifier 1, 2, or 3 nodes receive the message from the proposer, they send messages that they have received the node successfully to the other nodes. The validator 1 node sends the message to all three nodes, and the validator 2 node also sends the message to all three nodes.
However, the validator 3 node sends nothing and just receive the messages because it is currently faulted.
 
At the end of the prepare state, you can see how many nodes are in the system. Like this image here, we can see that all three are survived: proposers, validator 1, and validator 2.
This process will ensure that all the verifiers are in the same round.
 
 
 
 
Finally, in the commit phase, it is the process of communicating with other nodes to decide whether to accept a block received from a proposer. For example, it sends a response to nodes to check if blocks from the proposer are okay or wrong. If nodes more than two-thirds agree, the block will be immediately approved. In the end, it is decided in the commit phase and the finality is made. That is, the absence of finality doesn’t exist and unchangeable final state is formed at this stage. It's not a vague state like PoW.
 
So the advantage is that communication leads to consensus and completeness immediately. However, there is a disadvantage that traffic increases exponentially as the number of consensus nodes increases. This part is set to pick only the part of the consensus node and maintain the form BFT.
 
Let's see how the block is created and propagated in the next class.
 
## 3.2 Block generation and dissemination
Let's see how Klaytn creates and propagates blocks to provide a satisfying user experience.
 
Let's first look at the block creation cycle. Klaytn's block creation cycle is called a `round,` and a new block is created each round and a new round is started as soon as it ends. The block creation interval takes about 1 second.



Let's see how the proposer and committee choices work.
In each round, the proposer to generate the block is pulled from one of the governance council nodes randomly but decisively. The governance council is a collection of core cells or consensus nodes. If you look at the image, these circles are the consensus nodes, of which the blue color was chosen as the proposer of the current round. And then select another consensus node group as the committee of that round. They are the validator nodes with pink color that is selected by the committee. More specifically, each consensus node uses a random number derived from the most recent block header to perform a cryptographic operation to prove that it has been selected for this round.
 


Let's take a look at the block suggestion and verification.
When a consensus node is selected as a proposer, it will notify other consensus nodes of the evidence that it has been selected as a proposer in the round. At this time, it’ll prove this with the cryptographic proof which can be verified with the public key of the proposer. Then, the consensus node group which is elected to the committee in the round tells the proposer, likewise, with evidence, why they were chosen to be a member of the committee. (Click) Now that you know who is the proposer and the committee, the proposer selects and sorts the transactions in the transaction pool and creates blocks. It then consents with the committee, agrees to the newly created block, and finishes.
 

Finally, let's look at block propagation.
The proposed block must be signed by two-thirds of the members of the committee to be successfully completed. When the committee reaches an agreement, the new block is delivered to all consensus nodes and the consensus round ends. Then you can now propagate the block to the endpoint nodes through the (click) proxy node.
So far, we have come to understand how proposers and committees can be selected and agreed to block generation and propagate.

 
 

## 3.3 Network structure
 
Let's take a moment to explain Klaytn's network structure. On the left is the summarized version of the network. There is a core cell network in the whole network, and there is an endpoint node network surrounding the core cell. If you look at the enlargement next to it, inside the red box is the core cell network and the blue box outside is the endpoint network. In the core cell network, the yellow part is the CNN, consensus node network, and the red part is the PNN, proxy node network. The CNs in the yellow will be in charge of the consensus.
 
 
 
One core cell is operated by one participant. It operates with one CN and several proxy nodes connected to CN. To participate in CN, you have to meet up with tough conditions. And the CNs are all connected together so that they can communicate with each other. If there are 10 CNs, they are connected to each other. It's all connected because they have to communicate with each other as fast as they can when they are in the process of consensus. And the CNs cannot make direct contact with the outside. Because it is a very private environment with no interference, it has the advantage of being able to decide quickly whether to make the block or not, as a consensus node. So, how do you approach it? As a core cell participant, it’s like you run your proxy network that you can manage and trust to represent them. 
 
And on the outside, the endpoint nodes are connected to the core cell network. These endpoint nodes can connect to the proxy node in the core cell to receive information. Of course, the endpoint nodes can connect and exchange information with each other. However, if the endpoint node connects to the proxy node, you can receive the block more quickly. Note that there is no requirement to be an endpoint node. Anyone can be an endpoint node and pass the information to clients such as the web or mobile. It's the endpoint node that acts as a service provider.
 
 
And again, you have a CN boot node, a PN boot note, and an EN boot node, which is a special type node operated by Klaytn that helps new nodes register to the network and connect to another node. The CN boot node is inside the CN network and is not published. The PN and EN boot nodes are public nodes. PN boot nodes allow you to register only allowed proxy nodes and helps you to connect to endpoint nodes. The EN boot node provides information to the endpoint nodes about which proxy node to connect to. So far we have briefly covered the Klaytn network structure.
 
## 3.4 Core Cell
 

 
 
Let's talk more about core cells. When the main net is launched, in the core cell which is responsible for the consensus will operate in a few dozen units. As services become better, what should we do in terms of scalability if there are more connections to the core cell?
In a general case, not blockchain, as users grow, we'll grow the server and split up the requests. However, in the case of a blockchain, increasing the number of nodes can slow down the processing speed because more information needs to be passed to each node as it grows. Increasing the number of nodes does not increase performance. So, rather than increasing the number of nodes, increasing the performance of the node itself is the right way. For example, you can increase the performance of RAM or CPU. Let's look at the conditions for joining as a consensus node. The performance of the participant
 
 
1. More than 40 physical cores
2. 256GB RAM
3. Saving approximately 14TB of data for one year
4. 10G network
 
 
 
Note that the high performance of one of the participant's consensus nodes doesn’t mean the high speed of the entire core cell network. Because the remaining nodes with lower performance are operating at their low specifications. Therefore, in order to improve the performance of the core cell, it is necessary to match the same specifications to improve the performance.
 
 
 
 
And looking at the structure of the core cell again, it can be seen that it consists of one CN and several PNs. There are several reasons why a proxy node is called a PN. Because CN has limited resources to connect and the number of CNs is limited, it supports the connection of endpoints using PN. For example, let's say that endpoint nodes can connect directly to the CN. If this CN can accept up to a thousand endpoint connections, then if it goes beyond that, it will be burdened by the CN and its performance might go wrong. So PN is doing this part instead. The PN connects with the endpoint nodes and passes the transits to the CN. And since CN only needs to connect to a few PNs, it is much less burdensome, and you can solve the connectivity problems of endpoints trying to connect to the core cell by placing multiple PNs.
 
To summarize, because CN is the node responsible for the agreement, the connection should not be a performance hindrance. So, the role of the PN is to protect the CN, and the problem of scalability can be solved by placing multiple PNs.
 
 
 
 
 
 
 
## 3.5 Service Chain
 



 
Klaytn's service chain is an independently operated blockchain connected to the mainnet. This idea comes from scalability. In a situation where you want to use a service chain, you need to set it in a special node environment, or if you want to customize the security level, for example, when you want to run a private blockchain. Services that require tremendous throughput. When it is not economically feasible to distribute services to the mainnet, they use the service chain.
 
If you look at the image, the big circle in the middle is the mainnet. It can be seen that the service chain holds trust in the main chain, which is not free to communicate between the main chain and the service chain, and only limited transactions can be used. Also, the transmission of the KLAY will be allowed only when there are later restrictions.
 
 
 
 
 
In other words, the service chain builds a separate service space and locks the trust on the mainnet when needed. Other blockchain platforms are also moving toward adopting technologies such as service chains. In the case of Ethereum, I felt the limitations of the main network in terms of capacity and speed. It is well known that Crypto Kitty, which once made a huge boom slowed the Ethereum main network. So, on the Ethereum side, they put a concept based on a sidechain technology called Plasma, which, if done correctly, would lessen the burden on the main chain and allow more transactions to be processed per second. But it is still not coming out.
 
By the way, in Klaytn's service chain, you can set a zero gas fee for all transactions. It means that the BApp developers or service providers can build their own environment and provide services to users in the service chain. Yes, I've talked about what Klaytn's service chain is all about.
 
 
 
 
 
 
 
##3.6  Difference between Klaytn and Ethereum - Different roles of nodes
 
 
Let's talk briefly about the difference between Ethereum and Klaytn.
 
Ethereum is a single network. There is no distinction between network members. Anyone can create a block, but when it comes to creating a block, a person needs to be the first to notify that he or she made it first, and that it should be known to many places.
So if you add a block to a blockchain, you get a compensation.
This is PoW, a proof-of-work method used by Ethereum as a consensus protocol.
 
 
In Ethereum, you need to stick to as many nodes as possible because you do not know who will be the block mining node.
In other words, nodes that write blocks have up-to-date information.
So I want to get information quickly but I do not know where this node is.
If you know that node A is always fastest at writing a block on the node, you only need to stick to this node A, then you can receive information most fast.
 
However, since Ethereum is always changing its node, you have to stick to as many as possible, thereby, being gossiped to as many nodes as possible.
 
 
Then this will give you a chance to get the latest information.
Since any node can write and propagate blocks, you need to connect with as many nodes as possible to get the latest data.
 
Klaytn, on the other hand, is not a single network, but a network with two layers.
I said that one of the consensus nodes in the core cell network would be taken as a proposer and played a role of block writing per round.
So how do you get the latest information?
I should stick around.
The end-point nodes stuck to core cell know that consensus nodes are building blocks, so they are attached next to CNs.
 
 
That way you can load or write reliable information.
When we create an application we build servers that are shown here.
You can deploy Java or SQL DB to cloud or private servers like Azure or AWS.
However, because this server cannot be directly associated with the core cell, you must first connect to the endpoint node to access blockchain data.
You can connect your computer to an endpoint node or use it to connect to another endpoint node.
However, running this endpoint node personally is not easy.
Since the blockchain system needs to synchronize all nodes when operating a node, it needs to be synchronized every time new blocks are added in order to write properly.
 
 
 
 
 
 
In addition, there is also a concern that the computer may be crashed by an attack.
Because of these problems, you can connect to a trusted external node, such as Ethereum’s infrastructure node.
For example, you have a web developer here. He wants to connect to Klaytn and just read the data. Then, it’s better to connect to the external, public node and use it to make it much easier and less time-consuming than to run a personal endpoint node.
 
Finally, unlike Ethereum, there is a service chain that can communicate partially with the main net on the right and builds a separate service space.
To summarize, Klaytn is a network in which two layers trust each other, and when accessing an internal blockchain, the endpoint node can connect to the core cell network and write or receive data quickly.
