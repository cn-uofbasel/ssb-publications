# Publications related to Secure-Scuttlebutt and similar technologies.

[*Implementing the Double Ratchet algorithm in Tremola, a Scuttlebutt based messaging app for Android*](./pdfs/Waldvogel-DoubleRatchet.pdf), Lars Waldvogel, Bachelor Thesis

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
  type={Bachelor's Thesis}
 } 
````
</details>






