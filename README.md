peer : simulating

orderer : gen block

app : user - communicate between peer and orderer 


app --> proposal(RAFT_endorsement policy) --> peer --> simulation --> app --> orderer(check proposal package had authentication of peers) --> gen block --> peer get block --> update world state



1. app connects to peer.
2. app invokes chaincodes through WAS using REST API.
2-1. peer invokes chaincode with proposal(chaincode has proposals).
2-2. chaincode generates query or update proposal response.
3. peer gives proposal response to the app.
4. app requests to orderer that transactions should be ordered by orderer.
4-1. orderer check that transactions are being simulated and confirmed by peers.
4-2. Confirmed transactions are sent to peers in blocks. 
4-3. Peer updates ledger using transaction blocks.
4-4. Peer updates block world state. 
