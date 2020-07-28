* Creating your own testnet from scratch using Geth, Puppeth, and MyCrypto Wallet

** Download Geth and MyCrypto Wallet before starting. 

1. Open up notes, in order to have something to revert back to and save information for terminal window. 


2.Open up a folder and directory to work in, place nodes in, and place keystores in. 


3. In this folder, also place the Geth " Operating File", originally named "geth-alltools-...etc."


4. Create Node 1 and Node 2 accounts and save the passwords for those accounts, save these password addresses. 

"./geth account new --datadir node1" then do node 2


 "echo 'yourpassswordfornodegoeshere' > node1/password.txt" then do node 2


 5. Run "./puppeth" to begin process genesis block. 


 6. Creating the Genesis block

 a. name network, create new block, POA, default seconds for block.

 b. Seal and Pre-fund accounts with addresses of new nodes (you can find these addresses in your Node1>keystore folder or )

 c. specify chain id, set it to a rememberable 3 or 4 digit number (be sure not to use 1 because ETH reserves these chain id's )


 6. Press control -C, run ./puppeth again. but this time, manage existing genesis, then export genesis configs. 

 and when asked "which folder to save the genesis specs into?..." just press enter for default. 

 7.Initilize the new nodes with geth.

 ./geth init networkname.json --datadir node1/  
 ./geth init networkname.json --datadir node1/ 

 8. In order to begin mining, run this code, inputting your own numbers. 

 ./geth --datadir node1/ --syncmode 'full' --networkid 'any number' --rpc --minerthreads 1 --unlock "node1_sealer_address" --password node1/password.txt --mine --allow-insecure-unlock

 9. Open up a second git bash terminal, and run below. Be sure to grab the "enode address" from the previous gitbash terminal.Also, if running windows, use "ipcdisable" at the end of the node.  

 ./geth --datadir node2/ --syncmode 'full' --networkid 'same number as node 1" --unlock "node2_sealer_address" --password node2/password.txt --mine --allow-insecure-unlock --port 30304 --bootnodes "enode_address_from_node1" --ipcdisable

** Open MyCrypto

1. Press " Change Network", press add custom node, and find your chain id from the Genesis block. Remember you exported it in step 6 previously. Be sure to set node name and network name to the name you chose for your chain. Be sure to set the URL to http://127.0.0.1:8545. 

2. Go to open your wallet, Select Keystore File to open up your wallet. Click “SELECT WALLET FILE” and navigate to node1/keystore file.

3. Send a transaction from Node 1 to a new Node 2. Confirm the transaction. 


