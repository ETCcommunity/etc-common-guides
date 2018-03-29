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

To fix this you'll need to provide the amount to send in Wei instead of Ether/ETC. You can do this by calculating `amount to send * 10^18`. Or you can use MEW's handy calculator here: https://www.myetherwallet.com/helpers.html

*Note: This is normally only the case when working with contracts, when doing regular transactions that amount is typically specified in Ether/ETC*

## Deployed contracts are uninitialized objects
One thing that takes a bit to realize about contracts is that they're essentially uninitialized objects, each and every address that uses the contract gets its own version of it. There's no persistence within the object itself.

This is rather counter-intuitive since contracts have a constructor when deployed, so you'd *think* that they are instantiated objects waiting to be used but that's not true.

This also means that no deployed Contract has its own static or personal storage, all storage is allocated and managed at whatever address is calling the Contract.