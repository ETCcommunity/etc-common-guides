This topic is in progress, if you've found a common pitfall please comment below and I'll add it here.

# Network
## Can't connect
#### Light Client/Web Client
If you're using Emerald Wallet/CEW/MEW then try another node, there is a drop down in the top right of each of these. Choose another ETC-related node (such as Ethereum Commonwealth, gastracker, or epool).

#### Full Node
If you're running a full node make sure your time is synced.
* Windows: Control Panel > Date & Time > Internet Time > Change settings > Update 
* Linux/Mac: `sudo ntpdate -vu pool.ntp.org`. In some cases you may need to install the ntpdate program with your package manager.

# Contracts
## Sending 0 value (Ether/ETC vs. Wei/ETC)
If you're using a contract, it's working correctly, but it's sending you say 0 ETC when you asked it to send you 1 ETC then perhaps your contract is using Wei instead of Ether/ETC and actually sending you a very tiny amount of funds that aren't always displayed on block explorers.

To fix this you'll need to provide the amount to send in Wei instead of Ether/ETC. You can do this by calculating `amount to send * 10^18` (`amount_to_send * 10**18`). Or you can use MEW's handy calculator here: https://www.myetherwallet.com/helpers.html

*Note: This is normally only the case when working with contracts, when doing regular transactions that amount is typically specified in Ether/ETC*

## I want to query the blockchain without using a full node
Try a public JSON RPC end point. Remember to rate limit (something sane like <1 request per second)

https://mewapi.epool.io:8545 (Epool)
https://web3.gastracker.io:8545 (ETCDEV)
https://etc-geth.0xinfra.com:8454 (Ethereum Commonwealth)
https://etc-parity.0xinfra.com:8545 (Ethereum Commonwealth)