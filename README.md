# CJZCoin
Shell script to install a [CryptoJobz Masternode](https://www.cryptojobz.online/) on a Linux server running Ubuntu 16.04.
***

## VPS installation
```
wget -N https://raw.githubusercontent.com/cryptojobz/CJZCoin-Masternode-Script/master/cjzmn_install.sh
bash cjzmn_install.sh
```
***

## Desktop wallet setup

After the Masternode is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the CryptoJobz Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **2100** CJZ to **MN1**. You need to send all 2100 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to  **Tools -> "Open Wallet Configuration File"**
11. Insert the following into that file:
```
rpcuser=AnyUsername
rpcpassword=Any Password
txindex=1
listen=1
server=1
daemon=1
addnode=45.76.63.253
addnode=140.82.15.2
addnode=217.163.11.120
addnode=45.63.7.226
addnode=104.156.238.199
addnode=45.76.126.193
logtimestamps=1
maxconnections=256
masternode=1
masternodeprivkey=Masternode Private Key
masternodeaddr=VPS IP:37676
```
12. Save and close the file.
13. **Restart your wallet**
14. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
15. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
16. Select your MN and click **Start Alias** to start it.
17. Alternatively, open **Debug Console** and type:
```
startmasternode alias 0 MN1
```
18. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
cjzcoin-cli masternode status
```

***

## Usage:
```
cjzcoin-cli masternode status #To check your MN status
cjzcoin-cli getinfo #To get general info such as cjzcoin version and current block numnber
cjzcoin-cli mnsync status #To check if your MN is synced.
```
Also, if you want to check/start/stop **cjzcoin**, run one of the following commands as **root**:

```
systemctl status cjzcoin #To check if cjzcoin service is running
systemctl start cjzcoin #To start cjzcoin service
systemctl stop cjzcoin #To stop cjzcoin service
systemctl is-enabled cjzcoin #To check if cjzcoin service is enabled on boot
```
***

## Donations	
Any donation is highly appreciated	
**BTC**: 
**ETH**: 