# Know No Customer (KNC)

KNC stands for Know No Customer and is a potential p2p Bitcoin exchange using a partially signed transaction and a 2-of-2 multisig.

KNC previously depended on bitVM, but after speaking with [@supertestnet](https://gist.github.com/supertestnet), he explained why a PSBT and multisig would be more appropriate.

## Alice and Bob

Alice wants to buy 5 BTC, and has 5 BTC for collateral. Bob has 10 BTC he wants to sell. He advertises his price and payment methods, and Alice (or her nym) begin the exchange.

## The Happy Path

* Alice and Bob agree on a multisig address that requires 2-of-2 signatures to spend. They generate this multisig address and share it with each other.

* Alice and Bob create a PSBT that includes inputs totaling 15 BTC. Alice adds 5 BTC collateral and Bob adds 10 BTC (5 BTC collateral + 5 BTC purchase), and the PSBT cannot be broadcasted until both parties have signed.

* Once both parties are satisfied, Alice and Bob sign and broadcast it. This ensures both parties have committed to the transaction simultaneously. The funds are now locked in a multisig that requires both parties to unlock. There is no turning back.

* Alice pays Bob, and they both sign the multisig so Bob recuperates his 5 BTC collateral and Alice receives 10 BTC (the purchase + her collateral back).

## The Sad Path

If there is a dispute from either party, then the BTC locked in the multisig is stuck. Neither party will be able to retrieve it until the dispute is settled.

If Bob was paid but refuses to sign, then he has gained the value of 5 BTC, but he lost 10 BTC. Alice has lost 5 BTC and the value of 5 BTC. So it would cost Bob 5 BTC to be evil and attack Alice. 

If Alice refuses to pay, then Alice has lost 5 BTC, and Bob has lost 10 BTC. So it would cost Alice 5 BTC to be evil and attack Bob.

Basically a very expensive game of chicken that should keep both parties honest.

## Buyer Collateral Options

The buyer collateral protects the buyer by giving them funds to challenge with. However, all the numbers above are arbitrary. People can choose their own risk, and the collateral can be chosen by the relevant parties.

Suppose Alice buys 2 BTC from a friend for cash, and wants to purchase 3 BTC from a KNC exchange. She could make a request for 3 BTC, Bob will see her 2 BTC, and match it in the contract.

Therefore, it is on the seller to take this additional risk. Bob could end up losing 5 BTC (2 BTC collateral + 3 BTC purchase) and it only cost Alice 2 BTC. However, Alice could also lose the equivalent of 5 BTC (2 BTC collateral + 3 BTC payment value), and Bob would have the payment for the 3 BTC, costing him 2 BTC to be evil.


I imagine this additional risk would require a premium, and the market can figure out an acceptable price. It should only be used for smaller amounts.



