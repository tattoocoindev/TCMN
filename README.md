<h1>TattooCoin Masternode Edition</h1>
<p>ALGO:XEVAN</p>
<p>Dark Gravity wave retarget</p>
<p>1Mil Collateral</p>
<p>POW blocks every 3 minutes/ Rewards 150TME</p>
<p>instant-tx</p>
<p>Darksend</p>
<p>Obfuscation:coinjoin</p>
<p>rpc:12502 p2p:12401</p>
<p>Premine 20,000000 </p>
<p>- 10% Pos reward roughly every 40k blocks</p>
<p>+ %90 to pos and MN</p>

<p>-------------------------------------
 
-----------------------------------------------------------------------
Go to Tools -> Debug console and enter the command "masternode genkey".

In Debug Console enter the command "getaccountaddress MyMasternode".

send exactly 1 Mil to the address generated

Enter "masternode outputs" and copy the output
------------------------------------------------------------------------
Edit masternode.conf 
</p>
-----------------------------------------------------------------------
<p>
It should look something like this</p>
-------------------------------------------------------------------------------------------------------
<p><masternode> <yourip:12401> <PRIVATEKEY> <Proof of transaction> </p>

<p>rpcuser=</p>
<p>rpcpassword=</p>
<p>rpcallowip=127.0.0.1</p>
<p>listen=0</p>
<p>server=1</p>
<p>daemon=1</p>
<p>logtimestamps=1</p>
<p>maxconnections=256</p>
<p>masternode=1</p>
<p>externalip=your public ip address:25070</p>
<p>bind=your public ip address:25070</p>
<p>masternodeaddr=your public ip address:25070</p>
<p>masternodeprivkey= Masternode private key output </p>
-----------------------------------------------------------------------------------------------------------
Restart your wallet
Activate your MN in Masternode tab 
Your wallet must be unlocked for MN to earn
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++</p>
<p>each Masternode is secured with collateral of 1Mil</p>
<p>rpc: 12502 p2p: 12401 </p>
