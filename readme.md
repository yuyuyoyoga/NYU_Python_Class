This is a simple implementation of a blockchain called PandasChain. This blockchain stores transactions in 
pandas DataFrames (in-memory) and does not write to disk. The following are the components of this chain:
1. Transaction - A transaction is an exchange of Pandas coins between two parties. In the case of our blockchain, a transaction 
consists of:
    - Sender: The name of the party that is sending i.e. "Bob"
    
    - Receiver: The name of the party that is receiving i.e. "Alice"
    
    - Value: The float amount of Pandas Coins transferred
    
    - Timestamp: The datetime the transaction occured
    
    - Transaction Hash: A SHA-256 hash of the string concatenation of timestamp, sender, receiver and value
2. Block - A block holds a pool of transactions in a DataFrame. The maximum a single block can hold is 10 transactions. 
When a block is created, it contains zero transactions and has a status of UNCOMITTED. Once a block contains 10 transactions, 
that block then is marked COMMITTED and a new block is created for future transactions. Blocks are chained together by 
their block hash ID and previous block hash. Each block, except the first genesis block, tracks the hash of the previous block. 
When a block generates its own hash identifier, it uses the previous blocks hash as one of several strings it will concantenate. 
