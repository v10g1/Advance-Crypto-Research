In the classicalpayment systems, ie banks, the major problem is the trust based party system which the end users do towards the bank, the transactions can be reversed and used for anything, the financial
institute won't be able to avoid the mediation, and can reverse the transaction if they want it. This increses the tx cost, and effects scalability

This is why we need a payment system based on cryptograohic proofs without trust. We define an electronic coin as a chain of digital signatures. Each owner transfer the coin by digitally signing the hash of the previous transaction
It works like 
When Alice sends a coin to Bob:

1. She takes the **hash** of the last transaction (the previous owner and value).
    
2. She adds **Bob’s public key**.
    
3. She **digitally signs** that data with her private key.
To counter this the, the transactions should be publicly announced, and we need a system for participants to agree on a single history of the order they in which they were received.

Satoshi proposes a timestamp server, A timestamp server works by taking a hash of a blockm of itmes to be timestamped and widely publishing the hash, such as in a newspaper or Usenet post [2-5]
Each timestamp includes the privious timestamp in the hash, forming a chain, with each additional timestamp reinforcing the ones before

To implement this timestamo server on e peer-to-peer basis, we need to use a proof-of-work system similar to Adam Back's Hash-cash, rather than using the news paper the Proof-of-work uses the system chekc the validity of this system, for this system the nonce (number used once) is increased in each block which is then hashed with SHA256 hashing mechanism, Once the CPU effort has been expended to make it satify the proof-of-work, the block cannot be changed withhout redoing the work. A later blocks re chained after it, the work for and after that block has to be redone, which will expend a lot of CPU power.
The purnodes only need about latest 550 blocks, the archival nodes keep all the nodes.

its possible to verify payments without running the whole node, A user only need to keep a copy of block header of the longest proof-of-work chai, which he can get by querying network nodes until hes convinced he has the lobefst chain, obtain the merkle branch linking the transavtion to the block its timestamped in. He cant check the transaction for himself, but by linking it to a place in the chain, he cn see that the network has accepted i, and blocks added after it futher confim the network haas accepted it.

The Probability of attack->
According to normal distribution 
1−∑ k=0 z  k e − k! 1−q/ p z−k  

when converting this forula to C code
```c
#include double AttackerSuccessProbability(double q, int z) { double p = 1.0 - q; double lambda = z * (q / p); double sum = 1.0; int i, k; for (k = 0; k <= z; k++) { double poisson = exp(-lambda); for (i = 1; i <= k; i++) poisson *= lambda / i; sum -= poisson * (1 - pow(q / p, z - k)); } return sum; }
```

we get the following probability
```
q=0.1 z=0 P=1.0000000 z=1 P=0.2045873 z=2 P=0.0509779 z=3 P=0.0131722 z=4 P=0.0034552 z=5 P=0.0009137 z=6 P=0.0002428 z=7 P=0.0000647 z=8 P=0.0000173 z=9 P=0.0000046 z=10 P=0.0000012 q=0.3 z=0 P=1.0000000 z=5 P=0.1773523 z=10 P=0.0416605 z=15 P=0.0101008 z=20 P=0.0024804 z=25 P=0.0006132 z=30 P=0.0001522 z=35 P=0.0000379 z=40 P=0.0000095 z=45 P=0.0000024 z=50 P=0.0000006
```
Which is very minute, hence proving that the probability is less because of the cost of attack will be huge