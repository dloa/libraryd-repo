# OIP Daemon

To use Open Index Protocol in a decentralized/trustless way, users must run three daemons:
* florincoind 
  * [Github Repo](https://github.com/flo-blockchain/florincoin) | [Project Site](http://flo.cash/)
* IPFS daemon
  * [Github Repo](https://github.com/ipfs/go-ipfs) | [Project Site](https://ipfs.io/)
* OIP Daemon
  * [Github Release](https://github.com/dloa/oip-daemon/releases)
* ''Users may wish to also run the Bitcoin wallet daemon, bitcoind''
** [Github Repo](https://github.com/bitcoin/bitcoin) | [Bitcoin.org](https://bitcoin.org/)

## RPC Access to Florincoind

* The first step is to set up your '''''florincoin.conf''''' file. If it doesn't exist, create it.
  * For Windows users, it should go here: `%App Data%/Romaing/Florincoin/florincoin.conf`
  * For Mac users, it should go here: `~/Library/Application Support/Florincoin/florincoin.conf`
  * For *nix users, it should go here: <code>~/.florincoin/florincoin.conf</code>

Make sure you've allowed RPC access from localhost, and that you're running in server mode with txindex enabled:

<code><pre>rpcuser=flo rpc username  
rpcpassword=flo rpc password  
rpcallowip=127.0.0.1  
rpcallowip=192.168.0.0/16  
rpcport=7313  
server=1  
daemon=1  
txindex=1</pre></code>

You'll probably also want to include the following network nodes:

<code><pre>addnode=176.9.59.110  
addnode=188.166.6.99  
addnode=54.209.141.153  
addnode=192.241.171.45  
addnode=146.185.148.114  
addnode=54.164.167.95  
addnode=198.27.69.59  
addnode=37.187.27.4  
addnode=192.34.62.214</pre></code>

## Install OIP Daemon

OIP Daemon is currently in a private repo, awaiting a full security audit before opening it up publicly. You can download precompiled binaries for Mac, Windows and Linux below, and if you would like to compile it yourself, just get in touch with the Alexandria team via https://chat.alexandria.io/ and make a request.

* Mac: [oipdaemon-macOS.zip](https://github.com/dloa/oip-daemon/releases/download/0.4.1/oipdaemon-macOS.zip)
* Win: 
* Lin: [oipdaemon-linux64.tar.gz](https://github.com/dloa/oip-daemon/releases/download/0.4.1/oipdaemon-linux64.tar.gz)

## Start Florincoin Client

You can use the Florincoin-QT or florincoind clients, but the daemon is suggested as it consumes much fewer resources.

Let the blockchain fully sync, and then start up OIP Daemon.

<nowiki>*</nowiki>Note: you can download a bootstrap of the FLO blockchain here: <code></code>

## Start OIP Daemon

In Terminal, enter the following commands:

`export F_URI=127.0.0.1:7313`

Note: if you don't do this, the default will be 127.0.0.1:18322, which is Bitcoin's default RPC communication URI.

`export F_USER=flo rpc username`  
`export F_TOKEN=flo rpc password`  

`./oipdaemon`  

You should see something like this:

<pre><code>
   ___                     ___           _           
  / _ \ _ __   ___ _ __   |_ _|_ __   __| | _____  __
 | | | | '_ \ / _ \ '_ \   | || '_ \ / _` |/ _ \ \/ /
 | |_| | |_) |  __/ | | |  | || | | | (_| |  __/>  < 
  \___/| .__/ \___|_| |_| |___|_| |_|\__,_|\___/_/\_\
       |_|                                                                                                                                                                                                     
                                        OIP Spec: v0.4.1

opening config/config.json... done!
opening database ./db/sync89.db?cache=shared&mode=wrc... done!
creating tables and triggers if they don't exist... 
Running table query:  create oip_artifact table

Running table query:  !addcol! ArtCost
Column already added?
duplicate column name: artCost
Running table query:  !addcol! o.pubFeeUSD
Column already added?
duplicate column name: pubFeeUSD
Running table query:  !addcol! m.pubFeeUSD

Running table query:  !addcol! mrrLast24hr
Column already added?
duplicate column name: mrrLast24hr
Running table query:  !addcol! ltcUSD
Column already added?
duplicate column name: ltcUSD
Running table query:  !addcol! publisher.extraInfo
Column already added?
duplicate column name: extraInfo
Running table query:  !addcol! nsfw
Column already added?
duplicate column name: nsfw done!

daemon init successful!

Listening on port 41289

LOADED PROTOCOL: alexandria-media 0.4.1

current block chain height (rpc): 2504120
current max(block) from database: 1202999

syncing 1301121 blocks between 1203000 and 2504120
first, checking past 256 blocks for reorg... 
> no reorg found!


sync at 0.00%
sync at 0.08%
2.078433533s last 1k blocks -- 2.078434157s total time
sync at 0.15%
1.953132595s last 1k blocks -- 4.031576173s total time
sync at 0.23%
1.941965402s last 1k blocks -- 5.973547691s total time
sync at 0.31%
1.917651268s last 1k blocks -- 7.891204902s total time
sync at 0.38%
</code></pre>

You can test that OIP Daemon is running correctly by checking your Index Summary Info local endpoint:
 http://localhost:41289/alexandria/v2/info
