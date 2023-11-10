***Token Presale Smart Contract*** 

This Token Presale is like a direct shop for tokens. People can buy tokens by sending Ether during the presale time. There's no waiting or claiming—once you send Ether, you get your tokens right away.

The rate, set by the owner at the start, decides how many tokens you get for each Ether. If the presale doesn't hit the goals (soft or hard cap), anyone can get a refund until the owner decides to reset the presale.

It's designed to be easy for everyone to join and get tokens, with clear rules for refunds if needed.

***Instructions:***

1. Deploy the Contract:
Deploy the smart contract to the Ethereum network of your choice using a tool like Remix, Truffle, or Hardhat.

2. Initialize the Presale:
After deploying, call the initialize function to set the initial parameters of the presale, such as the token contract, rate, soft cap, hard cap, min and max contribution amounts, and the start and end times for the presale.

3. Lock Presale Tokens:
Transfer your tokens to the contract & Call the lockPresaleTokens function to lock the presale tokens in the contract. This step is very important for later calculations.

**(THE ENTIRE REMAINING TOKEN BALANCE WILL BE TRANSFERRED INTO THE LIQUIDITY POOL AFTER THE PRESALE ENDS IF THE SOFT/HARD CAP IS HIT.)**
*Make sure you're calculating your SC/HC ratio properly and that you are providing sufficient tokens for after the presale ends to back liquidity*

*Scenario A - Hard cap is hit and 90% of the ETH + ALL of the tokens remaining in the contract will be used to back LP.*
*Scenario B - Soft cap is hit and 90% of the ETH + ALL of the tokens remaining in the contract will be used to back LP.*
*Scenario C - Soft cap is not hit and the ETH will be refundable via claim to the presale participants until the presale is reset* (After that users cant claim a refund but their contribution is still mapped)*

4. Contribute to the Presale:
Users can contribute to the presale by sending ETH to the contract address. This is done by simply sending ETH to the contract address or calling the buy function.
*(unix startTime & endTime must be valid)*

5. Check Presale Status:
Use the presaleStatus function to check the current status of the presale (Not started yet, Live, or Ended).

6. Claim Refunds:
If the presale ends and the soft cap is not reached, contributors can call the claimRefundAndReturnTokens function to claim a refund. **This is only allowed if the presale has not been reset!**

7. Finalize the Presale:
If the presale ends, and the soft cap is reached, call the finalizePresale function to either add liquidity and lock tokens or set the presale as refunded based on the total raised amount.

8. Withdraw Tokens and ETH:
After finalizing the presale, the owner can call the withdrawTokens function to retrieve any remaining tokens in the contract. The withdrawETH function can be used to withdraw the remaining 10% of ETH.

9. Reset the Presale (Optional):
If needed, the owner can reset the presale by calling the resetPresale function. This can only be done after the presale has ended and the soft cap is NOT reached.

***EXAMPLE DATA FOR INITIALIZING:***

Name           | Type    | Data

_token         | address | 0x0000000000000000000000000000000000000000 (Token Address) **change to yours**

_rate          | uint256 | 2500000000 (2.5 tokens per 1 Gwei) (2.5 billion tokens / 1 ETH) **change to yours**

_softCap       | uint256 | 20000000000000000000 Wei (20 ETH)  **change to yours**

_hardCap       | uint256 | 100000000000000000000 Wei (100 ETH)  **change to yours**

_minContribution | uint256 | 20000000000000000 Wei (0.02 ETH)  **change to yours**

_maxContribution | uint256 | 2000000000000000000 Wei (2 ETH)  **change to yours**

_startTime     | uint256 | 1685120400 (Change Unix timestamp for start time)  **change to yours**

_endTime       | uint256 | 1685552400 (Change Unix timestamp for end time)  **change to yours**

***Tools:***
www.alchemy.com/gwei-calculator
www.unixtimestamp.com/
