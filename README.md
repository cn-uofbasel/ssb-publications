# Publications related to Secure-Scuttlebutt and similar technologies.

## *Delta-GOC-Ledger: Incremental Checkpointing and Lower Message Sizes for Grow-Only Counters Ledgers with Delta-CRDTs*, Jannick Heisch ([University of Basel](https://dmi.unibas.ch/en/persons/heisch-jannick/)),  [Master Thesis](./pdfs/Heisch-Delta-GOC-Ledger.pdf)

Keywords: Append-Only Logs, Eventually-Consistent Ledger, CRDTs, Delta-CRDTs 

<details>
<summary>Abstract</summary>

The Grow-Only-Counters-Ledger (GOC-Ledger) is a novel consensus-free replicated ledger based on a state-based Conflict-free Replicated Data Type (CRDT). It enables local crypto-tokens that impose lower infrastructure costs for low-volume intra-community transactions than existing blockchain projects. CRDTs ensure that all replicas in the system eventually end up in a consistent state. In order to achieve eventual consistency in state-based CRDTs, the replicas must periodically exchange their entire state. In the GOC-Ledger, the size of full states is unbounded and can become large depending on the number of transactions and accounts. Operation-based CRDTs only transfer operations in their update messages, leading to smaller message sizes, but require a reliable communication channel. Therefore, δ-based CRDTs have been proposed that unite the advantages of both approaches, by relying on the replication of small-states, while guaranteeing correct convergence on unreliable communication channels.

This thesis presents the δ-GOC-Ledger, a δ-based version of the existing state-based GOC-Ledger to reduce the communication overhead and increase scalability while still sup- porting unreliable communication channels. We prove the correctness and convergence of our design and formally show the relation to the state-based approach. A prototype based on Git is presented and demonstrates the implementation of CRDTs with Git. We assess both state-based and δ-based versions of the GOC-Ledger by simulating ERC-20 token transactions to quantify the reduction in message size that can be expected on real-world transactions and to evaluate the suitability of Git as a platform for implementing CRDTs.
We provide formal convergence proofs highlighting that the current state of the δ-based ledger can be incrementally computed. This is achieved by exploiting the associativity of the merge operation, which allows us to merge the latest full state with more recent delta states in any order. This approach enables efficient incremental computation of states from a causal history, as represented in a Git commit graph. Our analysis reveals that Git is quite effective at optimizing the size of state-based CRDT messages by already achieving an average size reduction of 24% compared to a naive approach. Nonetheless, implementing an application-specific δ-CRDT reduces the message size during incremental reconciliation by an additional 10-30%. Based on our results, we identify the overhead associated with the data representation using Git tree objects and highlight additional possibilities to further optimize the communication overhead.
</details>

<details>
<summary>BibTex Citation</summary>

````
@mastersthesis { 
  heisch2024deltagocledger, 
  author = {Jannick Heisch}, 
  title = {{Delta-GOC-Ledger: Incremental Checkpointing and Lower Message Sizes for Grow-Only Counters Ledgers with Delta-CRDTs}}, 
  school = {University of Basel}, 
  year = {2024},
  type={Master Thesis}
 } 
````
</details>

## *tinyISP: A Tunneling Negotiation and Feed Bundling Protocol Based on Secure Scuttlebutt*, Jannick Heisch ([University of Basel](https://dmi.unibas.ch/en/persons/heisch-jannick/)),  [Master Project](./pdfs/Heisch-tinyISP.pdf)

Keywords: Append-Only Logs, Multiplexing, Tunneling 

<details>
<summary>Abstract</summary>

>Today, almost all everyday applications rely on the Internet to collaborate and exchange information with others. The data is usually stored on central servers owned by large, indi- vidual companies. Furthermore, users who do not have access to the Internet infrastructure are excluded from using these applications. Decentralized protocols such as the Secure Scut- tlebutt protocol offer an alternative. With this protocol, individual messages are replicated between participants using append-only logs. In cases where peer-to-peer connections are not available for data exchange, Pub servers are used. However, these servers are not selec- tive and replicate all feeds of all clients, which can lead to scalability issues over time as the number of participants and published messages increases continuously.
>
>Therefore, this project introduces the feed bundling and tunneling protocol called tinyISP, which allows clients to enter into a contract with an ISP that enables them to exchange data with other clients of the same ISP. The data from multiple feeds is bundled into one log and sent via the ISP to the receiving client, who then demultiplexes the data and as- signs it to the corresponding feeds, reducing overhead in the replication layer. Once the contract between the ISP and the client is terminated, the feeds used for communication can be deleted to free up resources. Since the entire coordination of the protocol is based on append-only logs, it is independent of the Internet and can be transmitted through other media. A prototype implementation of tinyISP was integrated into existing Secure Scuttle- butt applications to demonstrate the benefits of such a protocol for everyday applications, such as a chat application.
</details>

<details>
<summary>BibTex Citation</summary>

````
@mastersthesis { 
  heisch2023tinyisp, 
  author = {Jannick Heisch}, 
  title = {{tinyISP: A Tunneling Negotiation and Feed Bundling Protocol Based on Secure Scuttlebutt}}, 
  school = {University of Basel}, 
  year = {2023},
  type={Master Project}
 } 
````
</details>

---------

## *2P-BFT-Log*: 2-Phase Single-Author Append-Only Log for Adversarial Environments, Erick Lavoie, [Arxiv Pre-Print Paper](https://arxiv.org/abs/2307.08381)

Keywords: state-based CRDT, append-only log, security

<details>
<summary>Abstract</summary>
      
> Replicated append-only logs sequentially order messages from the same author such that their ordering can be eventually recovered even with out-of-order and unreliable dissemination of individual messages. They are widely used for implementing replicated services in both clouds and peer-to-peer environments because they provide simple and efficient incremental reconciliation. However, existing designs of replicated append-only logs assume replicas faithfully maintain the sequential properties of logs and do not provide eventual consistency when malicious participants fork their logs by disseminating different messages to different replicas for the same index, which may result in partitioning of replicas according to which branch was first replicated.
> 
> In this paper, we present 2P-BFT-Log, a two-phase replicated append-only log that provides eventual consistency in the presence of forks from malicious participants such that all correct replicas will eventually agree either on the most recent message of a valid log (first phase) or on the earliest point at which a fork occurred as well as on an irrefutable proof that it happened (second phase). We provide definitions, algorithms, and proofs of the key properties of the design, and explain one way to implement the design onto Git, an eventually consistent replicated database originally designed for distributed version control.
>
> Our design enables correct replicas to faithfully implement the happens-before relationship first introduced by Lamport that underpins most existing distributed algorithms, with eventual detection of forks from malicious participants to exclude the latter from further progress. This opens the door to adaptations of existing distributed algorithms to a cheaper detect and repair paradigm, rather than the more common and expensive systematic prevention of incorrect behaviour.
</details>

<details>
<summary>BibTex Citation</summary>

````
@misc{lavoie20232pbftlog,
      title={2P-BFT-Log: 2-Phase Single-Author Append-Only Log for Adversarial Environments}, 
      author={Erick Lavoie},
      year={2023},
      eprint={2307.08381},
      archivePrefix={arXiv},
      primaryClass={cs.DC}
}
````
</details>

## *GOC-Ledger: State-based Conflict-Free Replicated Ledger from Grow-Only Counters*, Erick Lavoie, [Arxiv Pre-Print Paper](https://arxiv.org/abs/2305.16976)

Keywords: state-based CRDT, Ledgers, security

<details>
<summary>Abstract</summary>


> Conventional blockchains use consensus algorithms that totally order updates across all accounts, which is stronger than necessary to implement a replicated ledger. This makes updates slower and more expensive than necessary. More recent consensus-free replicated ledgers forego consensus algorithms, with significant increase in performance and decrease in infrastructure costs. However, current designs are based around reliable broadcast of update operations to all replicas which require reliable message delivery and reasoning over operation histories to establish convergence and safety.
>
>In this paper, we present a replicated ledger as a state-based conflict-free replicated data type (CRDT) based on grow-only counters. This design provides two major benefits: 1) it requires a weaker eventual transitive delivery of the latest state rather than reliable broadcast of all update operations to all replicas; 2) eventual convergence and safety properties can be proven easily without having to reason over operation histories: convergence comes from the composition of grow-only counters, themselves CRDTs, and safety properties can be expressed over the state of counters, locally and globally. In addition, applications that tolerate temporary negative balances require no additional mechanisms and applications that require strictly non-negative balances can be supported by enforcing sequential updates to the same account across replicas.
>
>Our design is sufficient when executing on replicas that might crash and recover, as common in deployments in which all replicas are managed by trusted entities. It may also provide a good foundation to explore new mechanisms for tolerating adversarial replicas.
</details>

<details>
<summary>BibTex Citation</summary>

````
@misc{lavoie2023gocledger,
      title={{GOC-Ledger: State-based Conflict-Free Replicated Ledger from Grow-Only Counters}}, 
      author={Erick Lavoie},
      year={2023},
      eprint={2305.16976},
      archivePrefix={arXiv},
      primaryClass={cs.DC}
}
````
</details>

---------


## *Implementing the Double Ratchet algorithm in Tremola, a Scuttlebutt based messaging app for Android*, Lars Waldvogel ([GitHub](https://github.com/LarsWaldvogel/), [LinkedIn](https://ch.linkedin.com/in/lars-waldvogel)), [Bachelor Thesis](./pdfs/Waldvogel-DoubleRatchet.pdf)

Keywords: Cryptography, Double-Ratchet, Secure Messaging

<details>
<summary>Abstract</summary>

> The Android messaging app Tremola uses the Scuttlebutt peer-to-peer gossiping protocol to transfer its messages from one user to another. This approach already supports encryption out of the box due to the properties of the Scuttlebutt protocol, where every user’s identity is made up of a public/private key pair. However, should a user’s key pair be compromised, all the messages they sent and received can be decrypted. Intercepting these messages is also trivial due to the nature of Scuttlebutt, where all messages are saved in an append-only log and distributed among peers.
>
> In this thesis, we implemented the Signal protocol’s Double Ratchet algorithm to provide forward secrecy and what is known as post-compromise security for these messages. This implementation took the special properties of the Scuttlebutt protocol into account to draw on its strengths, but also required some compromises to be made.
</details>

<details>
<summary>BibTex Citation</summary>

````
@mastersthesis { 
  waldvogel2022doubleratchet, 
  author = {Lars Waldvogel}, 
  title = {{Implementing the Double Ratchet algorithm in Tremola, a Scuttlebutt based messaging app for Android}}, 
  school = {University of Basel}, 
  year = {2022},
  type={Bachelor Thesis}
 } 
````
</details>

---------

## *Decentralized Kanban board using Secure Scuttlebutt and Conflict-Free Replicated Data Types*, Jannick Heisch ([University of Basel](https://dmi.unibas.ch/en/persons/heisch-jannick/)),  [Bachelor Thesis](./pdfs/Heisch-Kanban.pdf)

Keywords: CRDT, Applications, Scuttlesort

<details>
<summary>Abstract</summary>

> In the beginning, the World Wide Web was characterized by a decentralized structure, but it became increasingly centralized over time. Almost all applications we encounter in everyday life are based on a central server-client architecture and require a continuous connection to the Internet. These applications are user-friendly and easy to implement, but user data is stored on individual servers usually maintained by companies that profit from this data. Well-known digital Kanban board applications, which are very popular in the business world for organizing or optimizing workflows in the form of lists and cards, are also built on such centralized structures.
>
>This thesis examines how digital Kanban boards can be realized using an alternative approach, namely in the form of a decentralized structure in which users host their own data and are independent of the Internet. For this purpose, the existing android app Tremola, a Secure Scuttlebutt implementation, was extended by the prototype of a decentralized Kanban board. The main goal of this project is to ensure an eventual consistency between the board states of the individual users, so that the same board is displayed to everyone. Therefore, the board modifications performed by the users are saved as Conflict-free Replicated Data Types in an append-only log and shared with all participants using the Secure Scuttlebutt protocol.
</details>

<details>
<summary>BibTex Citation</summary>

````
@mastersthesis { 
  heisch2022kanban, 
  author = {Jannick Heisch}, 
  title = {{Decentralized Kanban board using Secure Scuttlebutt and Conflict-Free Replicated Data Types}}, 
  school = {University of Basel}, 
  year = {2022},
  type={Bachelor Thesis}
 } 
````
</details>

---------

## *Memory-Bounded Replication of Mutable Data Structures over Immutable Append-Only Logs*, Sebastian Lukas Philipp, [Master Thesis](./pdfs/Philipp-Memory-Bounded.pdf)

Keywords: Memory optimization, Garbage Collection, Data structures

<details>
<summary>Abstract</summary>

> Append-only logs are data structures which permit random-access read operations, but write operations are limited to appending to the end of the log. Nevertheless, arbitrarily modifications of data can be represented by creating an ever-growing stream of update operations appended to such a log. However, if a new consumer of this update stream wishes to recover the state represented by the log, often the entire log must be kept in storage and be replicated again.
>
> In this thesis report, we present PREDSL, a framework which facilitates the implementation of data structures by producing such a sequence of modification operations, and provide implementations for commonly used data structures.
>
> Further on, we designed, implemented and evaluated different strategies by which only a small, contiguous portion of the log – a “sliding window” of the log’s latest entries – must be kept in storage and replicated to new consumers.
>
> The results of our evaluation show that these strategies indeed manage to maintain a small sliding window in which all information relevant to reconstruct the entire state of the encoded data structure is represented in a very compact form, rather than spread over the entire log.
  
</details>

<details>
<summary>BibTex Citation</summary>

````
@mastersthesis { 
  philipp2022memorybounded, 
  author = {Sebastian Lukas Philipp}, 
  title = {{Memory-Bounded Replication of Mutable Data Structures over Immutable Append-Only Logs}}, 
  school = {University of Basel}, 
  year = {2022},
  type={Master Thesis}
 } 
````
</details>






