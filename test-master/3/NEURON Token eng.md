**NEURON Token**

**Technical documentation**

Table of contents

1. [NRN Contract as the basis for NEURON Token](#_jv7fkj3n9i1f)
2. [System](#_dh33a2y5371r)

	2.1. [Network-level interaction diagram](#_ek5hbln14u9)
	
	2.2. [System-level interaction diagram](#_dubhxfjuy36d)
	
3. [Dividends](#_hr28y0fdjzes)

	3.1. [Dividend distribution](#_motz8s596ftm)
	
	3.2. [Mechanism of dividends distribution](#_1ng0ln1b5ogs)
	
	3.3. [Distribution of profit](#_eht0t1et6bxz)
4. [Overview](#_fs7kwg8afz5y)
5. [Business logic of a contract](#_v7iuojesj3lz)

	5.1. [ERC-20](#_hx4c423n7p5r)
	
	5.2. [Additional logic](#_ef7b49xm1tji)
6. [Testing a token contract.](#_kf1n4pr3ksyj)
	
	6.1. [Compiling and deploying a contract on the blockchain.](#_4e64e0pyjoxy)
	
	6.2. [Verifying the contract status after it has been created.](#_igrev1wzkdmv)
	
	6.3. [Verifying the name and symbol of a token.](#_e7gi8x5aiiy0)
	
	6.4. [Testing the token transfer ability](#_th9kc88nqmlc)
	
	6.5. [Verifying protection against the transfer of a larger number of tokens than the account’s currently available balance.](#_8lq3z7chqqyx)
	
	6.6. [Verifying protection against overflow in the total number of contract tokens.	](#_cb18qz4050yr)
	
	6.7. [Verifying authorization for token spending](#_yzjimmbbbzdb)
	
	6.8. [Verifying protection against double-spending — prohibition of a spending authorization change.](#_d9g3y07pbw6x)
	
	6.9. [Protection against double-spending of tokens - an opportunity to cancel spending authorization.](#_arbf38xof8ld)
	
	6.10. [Verifying the impossibility of spending tokens without authorization.](#_1z08r27425o7)
	
	6.11. [Verifying the impossibility of spending tokens in excess of an authorized value.](#_wx67clltxhci)
	
	6.12. [Verification of inability to spend tokens within an authorized value in case of an account’s insufficient balance.](#_3pqdl2506ybg)
	
	6.13. [Verification of token spending.](#_p6ga6o8ppgmx)

**NEURON Token**

**Technical documentation**



#### <a id="_jv7fkj3n9i1f"></a> 1. NRN Contract as the basis for NEURON Token

NEURON Token is a token issued on the basis of a NRN contract. The number of NEURON Tokens issued during the ICO is limited and amounts to 

| Number of tokens | NRN 12 352 860,96 |
|--------------------|-------------------|

All tokens surviving this stage of the project will be destroyed.  

 NEURON Token (NRN), a smart Ethereum contract developed by the NEURON team using the Solidity programming language, allows issuing tokens in the Ethereum network affording a wide range of capabilities:
 
- distribution of a profit share under the contract among investor wallets proportionately to the number of tokens they hold;
- permits and access authorization system;
- accounting for commissions at dividend pay-out;
- accounting for the weight of investors’ votes proportionately to the number of tokens when voting on a crowd platform.


| **NEURON'S Parameters** | |
|-------------|-----------|
| Name | Neuron |
| Ticker | NRN |
| The share of investors’ profit in NeuronPlatform income | 20% |
| Income distribution procedure (Inc.) | <a href="https://www.codecogs.com/eqnedit.php?latex=Inc&space;=&space;NEURONprofit\times&space;20&space;\%&space;\times&space;(\frac{\mathrm{NRNinvestor}&space;}{\mathrm{NRNall}})" target="_blank"><img src="https://latex.codecogs.com/png.latex?Inc&space;=&space;NEURONprofit\times&space;20&space;\%&space;\times&space;(\frac{\mathrm{NRNinvestor}&space;}{\mathrm{NRNall}})" title="Inc = NEURONprofit\times 20 \% \times (\frac{\mathrm{NRNinvestor} }{\mathrm{NRNall}})" /></a> |
| Investment income payout term | After year-end reporting |
| Investment income payout procedure | To NEURON’s ETH wallet |
| Investment income payout principle | To investors’ wallets under a smart contract proportionately to NRN share |
| The cost of a token in $ | $5,00 |

NEURON Token (NRN)

[https://github\.com/neuronplatform/token ](https://github.com/neuronplatform/token)

#### <a id="_dh33a2y5371r"></a>2. **System**

#### <a id="_ek5hbln14u9"></a>2.1. Network-level interaction diagram 

The Ethereum network provides the environment for an interaction between companies and users. The parties interact by sending transactions into the NEURON contract. All transactions are verified via the contract’s business logic and are recorded on a block chain. Contract’s API is open for everyone in the Internet and absolutely anyone can become a user of a NEURON token. 

#### <a id="_dubhxfjuy36d"></a>2.2. System-level interaction diagram

The NRN protocol employs two basic account security models: a user-end key and an allocated wallet.

- **User-end key**

In this case, a private key that provides access to an account is only known to the end-user. 

- **Allocated wallet**

In this case, it is the financial structure (exchange or wallet supplier) that is responsible for the security key. 1-2 keys can only be used by a single entity, with transactions routed to a specific user account via ICAP-protocol.

#### <a id="_hr28y0fdjzes"></a>3. Dividends

#### <a id="_motz8s596ftm"></a>3.1. Dividend distribution

Dividend distribution is a process comprising two stages: obtaining accurate data with regards to NRN distribution among users (a dividend report) and distribution of profits among token holders. 

#### <a id="_1ng0ln1b5ogs"></a>3.2. Mechanism of dividends distribution 

In order to prevent the dividends from being distributed to the wrong token holder, the contract will block the token ownership transfer function for the duration of a dividend payout transaction.

With a view to preventing the token ownership transfer activity from affecting the dividend distribution process, the contract will block all token transfer operations until dividends have been paid out. In this case, the shares of investors will remain unchanged throughout the process, thereby facilitating the calculation of dividend sums for each investor.

#### <a id="_eht0t1et6bxz"></a>3.3. Distribution of profit 

The NEURON platform will annually charge 20% of the company’s profits to a dividend distribution smart contract. The dividend distribution date will be announced in advance on the NEURON website plus the NRN owners will be notified twice by email. The dividend distribution smart contract has been pre-set to distribute profit among investors pro rata to their shares. All payments will be made in ETH. The dividends will be sent to the NRN token-owned addresses confirmed by a blockchain snapshot. 

#### <a id="_fs7kwg8afz5y"></a>4. Overview

A token contract uses the secure arithmetic function and protection against double-spending.

An advanced protection against short address vulnerability was added by checking the total length of input parameters in bytes for all public functions.

To enable a contract to be tested or replaced with a new version every time a new vulnerability is found, a number of methods have been added to the contract that allow reading all the balance data and expenses authorization data, a measure that has changed all associated contract methods.

#### <a id="_v7iuojesj3lz"></a>5. Business logic of a contract

#### <a id="_hx4c423n7p5r"></a>5.1. ERC-20


5.1.1. A contract is issued with a fixed number of tokens;

5.1.2. Shareholder transfers tokens to a random wallet;

5.1.3. Shareholder allows debiting (incurring expenses) his tokens in favor of another wallet’s owner;

5.1.4. Tokens are transferred from someone else's wallet to a random wallet within the bounds specified by the owner of the wallet, to which these tokens are attached. 

#### <a id="_ef7b49xm1tji"></a>5.2. Additional logic

5.2.1. Purchase and sale of tokens for an ether;

5.2.2. Receiving dividends;

5.2.3. Providing information to the contract owner with regards to the balances of all shareholders to ensure a balanced account of votes while voting for a new project.

#### <a id="_kf1n4pr3ksyj"></a>6. Testing a token contract.

A private blockchain with three accounts has been designed for testing tokens: zero account for the miner, account 1 for the first contract owner, account 2 for a second party to contract transactions.

The following automated tests have been prepared.

#### <a id="_sch6jj7fschk"></a>6.1. Compiling and deploying a contract on the blockchain. 

#### <a id="_igrev1wzkdmv"></a>6.2. Verifying the contract status after it has been created.

#### <a id="_e7gi8x5aiiy0"></a>6.3. Verifying the name and symbol of a token.
		
6.3.1. Verifying the token cost and the number of decimals after the comma.
		
6.3.2. Verifying of the total number of tokens in the contract.
		
6.3.3. Verifying that all the tokens are balanced on the owner’s account. 

#### <a id="_th9kc88nqmlc"></a>6.4. Testing the token transfer ability

6.4.1. Calling a token transfer method.

6.4.2. Verifying the balances for compliance with the expected values.

#### <a id="_8lq3z7chqqyx"></a>6.5. Verifying protection against the transfer of a larger number of tokens than the account’s currently available balance.


6.5.1. Calling a token transfer method.

6.5.2. Verifying the balances for zero changes.

#### <a id="_cb18qz4050yr"></a>6.6. Verifying protection against overflow in the total number of contract tokens.

6.6.1. An attempt to fill the account with a number of tokens exceeding the maximum uint256 value.
	
6.6.2. Verifying the balances for zero changes.

#### <a id="_yzjimmbbbzdb"></a>6.7. Verifying authorization for token spending

6.7.1. Calling a spending authorization method 
6.7.2. Verifying the conformity of an authorized amount to a set value.

#### <a id="_d9g3y07pbw6x"></a>6.8. Verifying protection against double-spending — prohibition of a spending authorization change.

6.8.1. An attempt to set another value over an already assigned authorization value. 

6.8.2. Verifying that there are no changes in spending authorization value.

#### <a id="_arbf38xof8ld"></a>6.9. Protection against double-spending of tokens - an opportunity to cancel spending authorization.


6.9.1. An attempt to lift spending authorization off authorized spending. 

6.9.2. Verifying that the value authorized for spending is equal to zero.

#### <a id="_1z08r27425o7"></a>6.10. Verifying the impossibility of spending tokens without authorization.


6.10.1. Calling token transfer methods from someone else's account.

6.10.2. Confirming that there are no changes in the balances and spending authorization.

#### <a id="_wx67clltxhci"></a>6.11. Verifying the impossibility of spending tokens in excess of an authorized value.


6.11.1. Issuing authorizations for spending tokens from the first to the second account.

6.11.2. Calling a method of token transfer from the first account on behalf of the second account in excess of the current balance.

6.11.3. Confirming that there are no changes in the balances and spending authorization values.

#### <a id="_3pqdl2506ybg"></a>6.12. Verification of inability to spend tokens within an authorized value in case of an account’s insufficient balance.


6.12.1. Issuing authorizations for spending tokens from the first to the second account.

6.12.2. Calling a method of token transfer from the first account on behalf of second account in excess of the available balance.

6.12.3. Confirming that there are no changes in the balances and spending authorization values.

#### <a id="_p6ga6o8ppgmx"></a>6.13. Verification of token spending.


6.13.1. Issuing authorization for spending tokens from the first to the second account.

6.13.2. Calling a method of token transfer from the first account on behalf of the second account in excess of the available balance.

6.13.3. Verifying that the expected values comply with the expected values.

6.13.4. Verifying a proportionate reduction in the authorized spending amount. 

The success of almost all tests could be attributed to the contract’s extra feature of obtaining necessary data with regards to all balances and all spending authorizations. The contract owner is only allowed to employ the methods. The tests were conducted using the jasminejs framework.

