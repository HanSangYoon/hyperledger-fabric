peer : simulating

orderer : gen block

app : user - communicate between peer and orderer 


app(User gen trades_propsal and sends these proposals to peers) --> based on the consensus protocols about proposal(a.k.a. RAFT or "endorsement policy") --> peer --> simulation --> app --> orderer(check proposal package had authentication of peers) --> gen block --> peer get block --> update world state


chapter 1.

1. app connects to peer.
2. app invokes chaincodes through WAS using REST API with endorsement policy(n of 1, n of 2 etc). [simulating process]
2-1. peer invokes chaincode with proposal(chaincode has proposals).
2-2. chaincode generates query or update proposal response.
3. peer gives proposal response to the app.
4. app requests to orderer that transactions should be ordered by orderer.
4-1. orderer is gathering transactions and only checks that transactions are being simulated and confirmed by peers not checking the contents of chaincode(smart contract).
4-2. Confirmed transactions are sent to peers for updating blocks. 
4-3. Peer updates block world states(ledger) by appending transaction blocks.


ledger
1. this is the blockchain as we normally say.
2. also called as the world state. 
3. ledger or world state is only contained into Peer. 


chapter 2.
Fabric
1. key + value set(Key-Value Store, KVS).
2. using Database as [the Level DB] or [the Couch DB].

should refer Fabric Documents
(Hyperledger Fabric > Architecture Reference > Read-Write set semantics)
read-write set is prepared for the transaction.

3. Fabic Read-Write set : If the key is written at once, fail to read this. 
4. Because there are two reasons. first, Peers commit responses to App by the endorsement policy, they don't have any information about chaincode, or smartcontract. And Peers don't make blocks for themselves. So there is no any info about key-value records. Second, Orderer does not check chaincodes came from peers. Orderer just piles transactions one by one. Because functions are seperated just like this, this process does not make possible to use or change one variable freely. 
5. Fabric - High Through Put Network.
use different keys(but having same tag) for summation of values.  

