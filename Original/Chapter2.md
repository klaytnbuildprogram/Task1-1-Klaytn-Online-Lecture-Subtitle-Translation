# 2. The weakness of the Blockchain platform

## 2.1 Scalability
 
 
Scalability means to scale the platform. 
It simply means how much it can process things quickly. 
We don’t know how bitcoin or ethereum will solve an issue of scalability, even though they keep saying that they are working on it. 
Let's talk about what scalability is and why it's important.
 
In terms of scalability, we use the terms TPS and block interval. 
TPS is an abbreviation of transaction per second, which means you can check how many transactions per second can be handled. 
The block interval is the time interval at which each block is created.
 
We compare the processing speed of blockchains with Visa a lot. It is said that the Visa is handling an average of 1700 transactions per second. 
In the case of bitcoin, it is said that it can process 7 transactions per second.
In reality, it can process 2 to 5 transactions
 Ethereum is said to be 15 to 20 TPS.
 
The block interval of bitcoin is 10 minutes and the block interval of Ethereum is 15 to 20 seconds. 
So if Ethereum is 20 TPS and the block interval is 15 seconds, then 20 times 15, so a total of 300 transactions will be in one block.
 
 
Here is a question.
 If you have a blockchain platform with a TPS of 10,000 and a block interval of 10 minutes, how will the user experience be? 
Yes, it is. It means that it takes up to 10 minutes to complete a block that is dealing with ten thousand transactions in a second. 
What happens then? 
I simply want to send money to my friend, so I press the transfer button and it can take up to 10 minutes without completing it. 
It does not make sense. 
Ethereum is also significantly shorter than bitcoin, but 15-20 seconds is quite long for users. 
We are frustrated when we do not get any results within 5 seconds on the Internet. 
It should not happen in the 21st century.
 
 
So let's look at why the existing blockchain is slower. 
First, the characteristics of a blockchain network are characterized by a fact that more nodes don’t mean faster network. 
Our commonly used Web services and mobile services increase the number of servers to respond as quickly as possible to users, and when a large number of requests arrive, they are deployed and handled separately.
 
However, a server called a node that constitutes a blockchain network must process 100 jobs without distributing 100 jobs when 100 jobs are received. 
That is, every node repeats the same thing. 
The result is that the performance of the entire network is downgraded to the slowest node. 
Performance of a computer doesn’t make any difference than that of tens of thousands of different networks or computers.
As a result, blockchain networks such as Bitcoin or Ethereum are not able to handle large volumes of transactions and the network itself is slow.
 
 
## 2.2 Lack of finality
 
 
Finality refers to the unchangeable final state. 
The finality of a block in a blockchain guarantees that transactions in the block can never be changed. 
The transaction must be believed to have been completed without ambiguity. 
However, bitcoin and ethereum's mining mechanism lacks this finality. 
For example, I paid to buy a plane ticket with a bitcoin. 
Then the transaction will be created at that moment. 
This means that a transaction that can be left in the record is created.
 However, this transaction is not processed immediately. 
It is not a perfect guarantee. 
It only provides a probabilistic finality that will eventually be processed. 
It means that I have made a payment but later, I might found that it may not be paid.
 
Now let's see how long it takes to reach the finality on average.
 
(Table picture) 
 
If you look at this table, in the case of bitcoin, the average time to reach the finality is 60 minutes. 
The block mining takes 10 minutes, but it takes 1 hour with 6 steps to reach the finality. Ethereum says it takes 6 minutes to finality. 
The more you verify this step, the more likely it is that your transaction is sufficient to be trusted. 
But it takes too long because we have to go through this verification step a few times. Cryptocurrency is difficult to commercialize because of this. After you make a payment, the rate at which it takes to finality is too unusual.
 How many people will wait for up to an hour? 
So finality plays a very important role. 
In a little difficulty, finality measures how long to wait to get a reasonable guarantee that a transaction is unchangeable.
 
Lastly, waiting for a long time in a blockchain network can have a significant impact on your business, so the fast finality is an important business asset. 
So far I have briefly explained the absence of finality of existing representative blockchains.
 
## 2.3 Fork
  
Fork refers to the phenomenon that the connections of blocks are split into two or more branches. 
The reason forking occurs because all participants in a blockchain p2p network can independently mine. 
First, I'll explain bitcoin or ethereum’s proof of work. 
It solves the problem of finding the hash value to add blocks to the blockchain. 
Several nodes try to solve the problem while competing. 
Sometimes two nodes solve the problem at a similar time. 
Then two blocks are added as candidates to be added to the blockchain. 
At this point, a branch occurs.

For example, let's say you are mining from two nodes. 
A and B nodes. 
One day I wired a remittance to my friend. 
Then a transaction occurs and enters the transaction pool. 
A, B nodes now put transactions in the transaction pool in their own blocks to make the block. 
At this time, both nodes include transactions that I sent to my friend.
 
At the end of this process, the nodes now solve the problem of adding their own blocks to the existing blockchain. 
The nodes have to go through a difficult computation process, and both A and B nodes solve the problem. 
Then the nodes propagate it to other nodes that I solved.
 
When this propagation occurs, some nodes receive the purple block of node A and others receive the black block of node B. 
This is where the branch occurs as in the third block. 
Nodes that receive a purple block in the propagation process will also receive a black block later. 
But they ignore the black block. 
Because the transaction I sent to my friend has already been added to the purple block. Conversely, nodes that receive a black block will ignore the other because they contain the same transaction when they receive a purple block.
 
Next, we find the hash value from node c, solve the problem, and create and propagate the fourth block. 
In this case, the c-node that created the fourth block is the node that received the third black block. 
Blackline will be added because it has the parent hash of the third black block.
 
 
However, the nodes that have the third purple block cannot receive it when the fourth black block arrives later. 
It can’t be received even if It is obviously a valid block created by solving the problem and the fourth block that comes along the height of the block. 
Because the parental hash of the fourth block is not the third purple block but a black block.
 
Then the nodes that received the third purple block immediately discard the purple block they had and download it again, starting with the third black block. 
It means that the black line gets longer. 
The longer the line is, the more likely it will be recognized as the next block and added to the blockchain. 
This is the longest chain rule. 
This process of branching and merging proceeds in a very natural way.
 
 
 
However, there are some areas where this rule can be used maliciously. 
For example, if I have more than 51 percent of the total computing power, I can dig up much faster and produce more blocks than other miners. 
This means that you will be able to continue with the line you created in the branching process.
 
 
For example, in the third block, a branch is formed. 
I have created a black block, and I have to wait for the fourth block as usual, but I don’t have to wait for another node to create a block, and I can create and add it in this case. Strong hashing power allows making blocks faster. In this way, I don’t have to spread the line to other nodes, and I keep extending my own line secretly. 
In this process, you can ignore transactions in a specific address in my block, or record that I haven’t sold my coin to cash it. 
Here’s where my line on the network works. 
This is the rule that adds the block to the blockchain by selecting the longest line at the end of the branch. In other words, if my line has more blocks already compared to other lines, my line will be added as a “legit” one to the blockchain network. Therefore, there is the possibility of confusing the network by using this rule, and every time this occurs, it takes a long time to finalize because the line must go through the validation phase longer.
