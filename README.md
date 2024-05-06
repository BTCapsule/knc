# Know No Customer (KNC)
KNC stands for Know No Customer and is a potential p2p Bitcoin exchange using bitVM.

Robosats is great, and everything about it could be copied (or this could be implemented on Robosats). The problem with Robosats is it requires a third party to settle disputes.

BitVM allows us to verify data off chain, so no third party is necessary.

## Alice and Bob 

Alice wants to buy 5 BTC. In order to be a trusted buyer, Alice locks 10 BTC into a bitvm contract. Everyone Alice (or her nym) interacts with can see she has 10 BTC. Her collateral can be KYC because nobody will know the UTXO, and her purchase will be a separate output. 

Bob has 100 BTC he wants to sell. No contract is required. Bob simply advertises his price and acceptable payments.

## The Happy Path

When Alice wants to buy, she requests 5 BTC from Bob and waits for him to respond. Bob sees the 10 BTC collateral and decides to complete the transaction.

Bob will lock 5 BTC into a bitVM contract, and Alice will enter that contract with her own 5 BTC. Alice pays Bob for his 5 BTC, Bob confirms the payment, and Alice receives 5 BTC and her collateral back. This is the happy path.

## The Sad Path

If there is a dispute from either party, they will initiate an expensive game that will keep them honest.

If Alice requests 5 BTC from Bob and fulfills her end, but Bob does not lock 5 BTC into the contract, then obviously this deal is over. 

If Bob does lock 5 BTC into the contract, but Alice does not pay, then Bob can challenge. If Alice does not respond, then Bob gets his 5 BTC back and the deal is over.

If Alice responds with her own challenge (claiming that she did pay and Bob is lying), this will slash funds from her collateral, and Bob’s 5 BTC is stuck in the contract. Bob can admit he was lying, or he can counter challenge, slashing funds from his 5 BTC. 

This game can go back and forth until someone admits they are lying, or they both lose all their money. Basically a very expensive game of chicken.

