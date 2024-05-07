# Know No Customer (KNC)
KNC stands for Know No Customer and is a potential p2p Bitcoin exchange using bitVM.

Robosats is great, and everything about it could be copied (or this could be implemented on Robosats). The problem with Robosats is it requires a third party to settle disputes.

BitVM allows us to verify data off chain, so no third party is necessary.

## Alice and Bob 

Alice wants to buy 5 BTC. In order to be a trusted buyer, Alice locks 10 BTC into a bitvm contract. Everyone Alice (or her nym) interacts with can see she has 10 BTC. Her collateral can be KYC because nobody will know the UTXO, and her purchase will be a separate output. 

Bob has 100 BTC he wants to sell. No contract is required. Bob simply advertises his price and acceptable payments.

## The Happy Path

When Alice wants to buy, she requests 5 BTC from Bob and waits for him to respond. Bob sees the 10 BTC collateral and decides to complete the transaction.

Bob will lock 10 BTC into a bitVM contract, 5 BTC for collateral and 5 BTC to sell. Alice will enter that contract with her own 5 BTC. Alice pays Bob for 5 BTC and Bob confirms the payment. Alice receives 5 BTC and her collateral back, and Bob receives his collateral back. This is the happy path.

## The Sad Path

If there is a dispute from either party, they will initiate an expensive game that will keep them honest.

If Alice requests 5 BTC from Bob and fulfills her end, but Bob does not lock enough BTC into the contract, then Alice can cancel the deal. 

If Bob does lock 10 BTC into the contract, but Alice does not pay, then Bob can challenge. If Alice does not respond, then Bob gets his 10 BTC back and the deal is over.

If Alice responds with her own challenge (claiming that she did pay and Bob is lying), this will slash funds from her collateral, and the 5 BTC purchase is stuck in the contract. Bob can admit he was lying, or he can counter challenge, slashing funds from his own collateral. 

This game can go back and forth until someone admits they are lying, or they both lose all their money. The 5 BTC that was meant to be purchased will go to the miners. 

So in the worst case, Bob is short 10 BTC and Alice is short 5 BTC + the payment (equal to 5 BTC) and nobody is happy.

Basically a very expensive game of chicken.


## Buyer Collateral Options

The buyer collateral protects the buyer by giving them funds to challenge with. The initial collateral can be KYC, or this could be added to existing non-KYC exchanges for extra security.

However, all the numbers above are arbitrary. People can choose their own risk, and the collateral can be chosen by the relevant parties.

Suppose Alice buys 2 BTC from a friend for cash, and wants to purchase 5 BTC from a KNC exchange. She could make a request for 5 BTC, Bob will see her 2 BTC, and match it in the contract.

In this way, each 2 BTC could be used to challenge the other until the funds are empty. If the dispute is not settled, Bob will receive 3 BTC back from the purchased BTC, and Alice will get nothing.

This would lead to a total loss of 4 BTC for Bob, and either 2 BTC (if Alice is evil), or 2 BTC + the price of 5 BTC if Alice is honest. 

This means the seller always has the same risk factor (losing 2x collateral), but if the buyer pays, they have an additional risk of losing the value of 2x collateral + the price of the unsecured BTC. 



