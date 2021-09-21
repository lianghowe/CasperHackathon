# Get Started With Casper (First 100 Submissions)


## 1. Create and deploy a simple, smart contract with cargo casper and cargo test




![](imgs/reppare.png)

### cargo test

![](imgs/test.png)

### Create and deploy a simple, smart contract


![](imgs/deploy.png)

### Check Deploy Status

![](imgs/check-deploy.png)




## 2. Complete one of the existing tutorials for writing smart contracts

ERC-20 Tutorial

Prepare environment :

![](imgs/erc20-prepare.png)

Compile your contract 

![](imgs/erc20-build.png)

Run the contract unit tests

![](imgs/erc20-test.png)





## 3. Demonstrate key management concepts by modifying the client in the Multi-Sig tutorial to address one of the additional scenarios

Scenario 1: 


```

    
  
const keyManager = require('./key-manager');

    // To achive the task, we will:
    // 1. Set Keys Management Threshold to 1.
    // 2. Set Deploy Threshold to 1.
    // 3. Set fullAccount's weight to 1

(async function () {

    let deploy;

    // 0. Initial state of the account.
    // There should be only one associated key (faucet) with weight 1.
    // Deployment Threshold should be set to 1.
    // Key Management Threshold should be set to 1.
    let masterKey = keyManager.randomMasterKey();
    let fullAccount = masterKey.deriveIndex(1);    


    console.log("\n0.1 Fund main account.\n");
    await keyManager.fundAccount(fullAccount);
    await keyManager.printAccount(fullAccount);
    
    console.log("\n[x]0.2 Install Keys Manager contract");
    deploy = keyManager.keys.buildContractInstallDeploy(fullAccount);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);


    
    // 1. Set Keys Management Threshold to 1.
    console.log("\n1. Set Keys Management Threshold to 1\n");
    deploy = keyManager.keys.setKeyManagementThresholdDeploy(fullAccount, 1);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
    // 2. Set Deploy Threshold to 1.
    console.log("\n2. Set Deploy Threshold to 1.\n");
    deploy = keyManager.keys.setDeploymentThresholdDeploy(fullAccount, 1);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
    // 3. Set fullAccount's weight to 1
    console.log("\n3. Set faucet's weight to 1\n");
    deploy = keyManager.keys.setKeyWeightDeploy(fullAccount, fullAccount, 1);
    await keyManager.sendDeploy(deploy, [fullAccount]);
    await keyManager.printAccount(fullAccount);
    
})();



```


![](imgs/scenacio.png)

## 4. Learn to transfer tokens to an account on the Casper Testnet. Check out this documentation.


![](imgs/transfer.png)![](imgs/check-transfer.png)




## 5.Learn to Delegate and Undelegate on the Casper Testnet. Check out these instructions.



![](imgs/delegation.png)



![](imgs/undelegation.png)
