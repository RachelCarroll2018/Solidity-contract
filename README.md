# Unit 20 - "Joint Savings Account"

### Background

In this project we act as an employee at a new startup company. Currently, the team is building smart contracts to automate many of the institutions’ financial processes and features, such as hosting joint savings accounts.

To automate the creation of joint savings accounts, I created a Solidity smart contract that accepts two user addresses. These addresses will be able to control a joint savings account. The smart contract will use ether management functions to implement a financial institution’s requirements for providing the features of the joint savings account. These features will consist of the ability to deposit and withdraw funds from the account.

### Instructions

The steps for this project are divided into the following sections:

1. Create a Joint Savings Account Contract in Solidity

2. Compile and Deploy Smart Contract in the JavaScript VM

3. Interact with the Deployed Smart Contract

#### Step 1: Create a Joint Savings Account Contract in Solidity

1. From the provided [starter code](Starter_Code), open the Solidity file named `joint_savings.sol` in the Remix IDE.

2. Define a new contract named `JointSavings`.

3. Define the following variables in the new contract:

    * Two variables of type `address payable` named `accountOne` and `accountTwo`

    * A variable of type `address public` named `lastToWithdraw`

    * Two variables of type `uint public` named `lastWithdrawAmount` and `contractBalance`


4. Define a function named `withdraw` that accepts two arguments: `amount` of type `uint` and `recipient` of type `payable address`. In this function, code the following:

    * Define a `require` statement that checks if `recipient` is equal to either `accountOne` or `accountTwo`. If it isn’t, the `require` statement returns the “You don't own this account!” text.

    * Define a `require` statement that checks if `balance` is sufficient for accomplishing the withdrawal operation. If there are insufficient funds, it returns the “Insufficient funds!” text.

    * Add an `if` statement to check if `lastToWithdraw` is not equal (`!=`) to `recipient`. If it’s not equal, set it to the current value of `recipient`.

    * Call the `transfer` function of the `recipient`, and pass it the `amount` to transfer as an argument.

    * Set `lastWithdrawAmount` equal to `amount`.

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance` to reflect the new balance of the contract.


5. Define a `public payable` function named `deposit`. In this function, code the following:

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance`.

6. Define a `public` function named `setAccounts` that takes two `address payable` arguments, named `account1` and `account2`. In the body of the function, set the values of `accountOne` and `accountTwo` to `account1` and `account2`, respectively.

7. Add a fallback function so that the contract can store ether that’s sent from outside the deposit function.

#### Step 2: Compile and Deploy Contract in the JavaScript VM

1. Compile the smart contract. If an error occurs, review the code, and make the necessary changes for a successful compilation.

2. In the Remix IDE, navigate to the “Deploy & Run Transactions” pane, and then make sure that “JavaScript VM” is selected as the environment.

3. Click the Deploy button to deploy smart contract, and then confirm that it successfully deployed.

#### Step 3: Interact with Deployed Smart Contract

Now that the contract is deployed, it’s time to test its functionality! After each step, there is an image in the Execution Results folder to show completion.

Cmplete the following steps:

1. Use the `setAccounts` function to define the authorized Ethereum address that will be able to withdraw funds from the contract.

2. Test the deposit functionality of the smart contract by sending the following amounts of ether. After each transaction, use the `contractBalance` function to verify that the funds were added to your contract:

    * Transaction 1: Send 1 ether as wei.

    * Transaction 2: Send 10 ether as wei.

    * Transaction 3: Send 5 ether.

3. Once having successfully deposited funds into the contract, test the contract’s withdrawal functionality by withdrawing 5 ether into `accountOne` and 10 ether into `accountTwo`. After each transaction, use the `contractBalance` function to verify that the funds were withdrawn from the contract. Also, use the `lastToWithdraw` and `lastWithdrawAmount` functions to verify that the address and amount were correct.
