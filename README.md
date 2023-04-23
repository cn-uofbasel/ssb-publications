# Publications related to Secure-Scuttlebutt and similar technologies.

*Implementing the Double Ratchet algorithm in Tremola, a Scuttlebutt based messaging app for Android*, Lars Waldvogel ([GitHub](https://github.com/LarsWaldvogel/), [LinkedIn](https://ch.linkedin.com/in/lars-waldvogel)), [Bachelor Thesis](./pdfs/Waldvogel-DoubleRatchet.pdf)

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

*Decentralized Kanban board using Secure Scuttlebutt and Conflict-Free Replicated Data Types*, Jannick Heisch ([University of Basel](https://dmi.unibas.ch/en/persons/heisch-jannick/),  [Bachelor Thesis](./pdfs/Heisch-Kanban.pdf)

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

*Memory-Bounded Replication of Mutable Data Structures over Immutable Append-Only Logs*, Sebastian Lukas Philipp [Master Thesis](./pdfs/Philipp-Memory-Bounded.pdf)

Keywords: Memory optimization, Garbage Collection, Data structures

<details>
<summary>Abstract</summary>

> Append-only logs are data structures which permit random-access read operations, but write operations are limited to appending to the end of the log. Nevertheless, arbitrarily modifications of data can be represented by creating an ever-growing stream of update operations appended to such a log. However, if a new consumer of this update stream wishes to recover the state represented by the log, often the entire log must be kept in storage and be replicated again.
> In this thesis report, we present PREDSL, a framework which facilitates the implementation of data structures by producing such a sequence of modification operations, and provide implementations for commonly used data structures.
> Further on, we designed, implemented and evaluated different strategies by which only a small, contiguous portion of the log – a “sliding window” of the log’s latest entries – must be kept in storage and replicated to new consumers.
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






