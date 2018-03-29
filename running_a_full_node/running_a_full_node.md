# Caveat
**Please note that you do not need to run your own node in order to use the ETC network. This is more advanced documentation geared towards users who want to further support the ETC network in a low cost but effective way, miners who need a node running, developers who might need a full node, and other technically-skilled users.**

# Why run a node?
You have a few reasons why you'd run a node, including:
1. You're solo mining or running a mining pool, if this is the case then you need a node in order to talk to the network.
1. You want to make sure your transactions to the network yourself. Remote nodes are generally reliable but are controlled by 3rd parties and typically throttle heavy usage.
1. You want to help secure the network; the more independent nodes running the more copies there are of the blockchain and the more resilient it is.
1. You want to make the network faster and secure; the more nodes the lower the latency in sharing blocks and the more copies of the blockchain that exist.

# What do I need?
You'll need node software, either Geth, Parity, or Mantis.

You'll also likely want a computer that is running 24/7 or a VPS/remote server that can run all day. This will ensure that your node is always in sync. You can also choose to start your node up only when you need it but this has a tradeoff of you'll need to wait for it to sync the newest portions of the chain, and your impact on the network will be less.

All instructions are for Linux/Mac but would pretty much be the same on Windows.
# Setup

Below I will detail how to setup a node using all three available client softwares. For the most part geth or parity are likely what you want but if you're feeling adventurous you can also try running the brand new mantis client from IOHK.

## Geth

Geth is the defacto/reference implementation for all Ethereum-based networks, ETC's version of it is particularly efficient and this makes it an excellent choice for node software.

You can also install and run Emerald Wallet either alongside geth, or use their built-in feature to start a "Full Node" which will run geth for you. For more information [check out this guide](https://forum.ethereumclassic.org/t/using-emerald-wallet/1157) which is an excellent option for an easy-to-run full node.

*Note: If you go this route you don't need to run geth separately. You still can though if you want your geth node to run even when you're not using Emerald Wallet.*

*Tip: You can actually use Emerald Wallet alongside any of the node software listed here, if one is running on your machine it will automatically detect and use it when you select the "Full Node" option.*

### Installation
1. Download Geth from here: https://github.com/ethereumproject/go-ethereum/releases
1. Unzip (`unzip`) or Untar (`tar -xvzf`) the archive
1. `chmod +x geth`
1. `cp geth /usr/local/bin`
1. `source ~/.bashrc` (for bash)
1. `geth`

### Running / Options
The most common flag you'll want for `geth` is `--fast` if you want a much faster, although slightly less secure sync. If you're mining, running an exchange, or doing other very mission-critical tasks then you're best off waiting for the full sync.

## Parity
Parity has always been a well performing, reliable, and space-efficient node software so it's a great choice. It also comes with a built-in GUI so if you're planning on using your node to transact on the ETC blockchain then you may want to go this route.

### Installation
1. Download Geth from here: https://github.com/ethereumproject/go-ethereum/releases
1. Unzip (`unzip`) or Untar (`tar -xvzf`) the archive. If you have Debian/Ubuntu grab the `*.deb` file instead and run `sudo dpkg -i <filename>.deb`.
1. If you installed from a Debian/Ubuntu package then skip to step 5. If you didn't install a package then, you'll `chmod +x parity`
1. `cp parity /usr/local/bin`
1. `source ~/.bashrc` (for bash)
1. `parity --chain=classic`

### Running / Options
To run parity on ETC you'll need to pass the flag `--chain=classic`. You can also specify this in a `config.toml` file [as described here](https://wiki.parity.io/Configuring-Parity).

## Mantis
Mantis is a brand new client created by IOHK for ETC. It is stable on the ETC network but has not been as long term proven as the Geth and Parity codebases so please keep this in mind. However, IOHK is full of brilliant programmers and I have no doubt that Mantis will prove very reliable over time.

### Installation
[TODO]
### Running / Options
[TODO]

## Keeping your node running
If you're on a VPS you'll want to keep your node running so you may want to setup a systemd service or similar to insure that it's always running. An excellent [set of instructions](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-Managing_Services_with_systemd-Unit_Files#sect-Managing_Services_with_systemd-Unit_File_Create) are provided by RedHat.

One tip, you'll want your `Type=simple` in most cases unless you know what you're doing and your node software can be configured to daemonize itself.