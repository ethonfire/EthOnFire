# ETH OnFire
Welcome to Eth OnFire. Eth OnFire is a coin burning contract. The OnFire team took inspiration from the [Bonfire dapp](https://github.com/BonfireEth/Bonfire-15-I) contracts. By burning over half of the coins we can bring value to the entire market not just users of the game. The ETH OnFire contract is made to burn coins but 30% of the ETH from each round is gifted to one randomly chosen user. The winner of the 30% gift is picked using oraclize's random number contract combined with a salt number hidden in a hash submitted before each round. 

# How it Works
1. After the salt number is submitted to the contract by way of hash and the ticket price is set, tickets are open for sale. 

2. After all tickets are sold, a random number must be requested. The random number is requested by any user using the button on the website ("Request Random") or by command line (see "cli" below). The user that successfully requests the random number is gifted the value of one ticket after the coin burn. Their gift can be withdrawn from the contract after the coin burn. Note: there is a 30 minute cool down for the request button/function call.

3. After the random number is received the salt number is revealed by the OnFire team. The salt number modifies the random number to generate the winning ticket number.

4. The last step is to deposit the gifts and burn the coins. This is done by a user (any user) pressing the burn button or calling the burn function using the cli. Note: this function has a 30 minute cool down. 30% of the pot goes to the winning ticket holder, the value of one ticket goes to each of the function callers (Request Random and Burn functions), 1% goes to the OnFire team, and about 69% (less the price of two tickets) is **Burned**.


```javascript

var abi = [{"constant":true,"inputs":[],"name":"senderHolderAddress","outputs":
var foo = web3.eth.contract(abi)
var contract = firePlace.at('0xcvtrr41d6427dfer767jgj391c10acdf850jghgkdsd')


var bar = contract.RevealedHash({}, {fromBlock: 0, toBlock: 'latest'});

bar.watch(function(error, result){console.log(result.args.secretHash + " " + result.args.textOne + " " + result.args.secretNum + " " + result.args.textTwo)});

var baz = contract.GiftDeposited({}, {fromBlock: 0, toBlock: 'latest'});

baz.watch(function(error, result){console.log(result.args.giftRecipient + " " + result.args.amount)});

```

# More Info
1. The OnFire team submits a salt number by way of a hash. The salt number modifies the random number from oraclize to protect against the possibility of a bad actor on the random number generation contract. The salt number is submitted before a round is opened and cannot be changed, because in order to reveal the salt number the hashes must match. 

2. The selfdestruct function burns all of the ETH held in the contract without benefit to the OnFire team.


##### Credits
* Bootstrap timeline by [siddharth4753](https://bootsnipp.com/snippets/Q0ppE) 
* JS and game design [Bonfire](https://github.com/BonfireEth/Bonfire-15-I)
