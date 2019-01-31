# ethereum-dapp-test-project
ethereum-dapp-test-project

# Node version
10.13.0
# basic tool you need to install npm install -g
$ npm install -g solc  
$ npm install -g truffle  
$ npm install -g ganache-cli  

# The Steps to create ethereum DApp project 
## Step 1 let truffle join
$ truffle init

## Step 2 let npm join 
$ npm init

## Step 3. To set configuation for minimal DApp project 
### Step 3.1 update package.json
In package.json, add the scripts of compile, rpc, migrate:development and clean  
  "scripts": {  
    "test": "echo \"Error: no test specified\" && exit 1",  
    "compile": "truffle compile",  
    "rpc": "ganache-cli",  
    "migrate:development":"truffle migrate:development",  
    "clean": "rm -rf ./node_modules/ && rm package-lock.json && rm -rf ./build && rm -rf ./dist"  
  },  
  
### Step 3.2 update truffl-confige.js
Update truffle.js file with the following content.  
module.exports = {  
  networks: {  

    dev: {  
      host: "127.0.0.1",  
      port: 8545,  
      network_id: "*" // Match any network id  
    }  

  }  
};  

So when you execute   
$ truffle migrate --network dev  
The migrate process of truffle will refernce the dev network setting in truffle-config.js file and deploy it.   
When you run command ganache-cli, this rpc server is run in localhost:8545. That is why we set dev network like above.  


### Step 3.3 install web3 for JavaScript to communicate with smart contract
$ npm install web3 --save  
web3 1.0.0-beta.37 is stable version currently (beta.38, beta.39, beta.40 ,beta.41 may not stable)  

### Step 3.4 understand explaination of added scripts in package.json

#### rpc --> $ ganache-cli
ganache-cli will wake up a rpc server to simulated blockchain interface in local. 

#### compile --> $ truffle compile   
To compile the smart contracts in contracts folder

#### migrate:development --> $ truffle migrate --network dev
follow the dev network setting in truffle-config.js , then and the truffle will deploy to where it is. the migrate process will follow the files in ./migrations folder.

## Step 4. Start to run the project from clean environemnt

### Step 4.1 Make your proejct from clean data (without any compiled thing and local package installation)
$ npm run clean 

### Step 4.2 install dependency package
$ npm install

### Step 4.3 start local rpc server to simulated blockchain interface
To open another terminal, and run the following command  
$ npm run rpc

### Step 4.4 compile smtart contract
$ npm run compile

### Step 4.5 Deploy smart contract to local rpc server that simulated blockchain interface
$ npm run migrate:development





