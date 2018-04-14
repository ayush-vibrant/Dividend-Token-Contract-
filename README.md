# Dividend-Token-Contract-
ERC20-compliant contract that can divide ether dividends proportionally amongst token owners.

## Problem I am trying to solve
A recurring challenge in smart contract development is the high gas cost of iteration. This challenge is more crucial when it comes to paying dividends equally or in some proportions. When a dividend is deposited, it must be evenly distributed among all token owners. But if Blockchain Network is very large than in that case, there may be millions of token owners, and iterating over all of them would be tremendously expensive in terms of gas. Because such iteration is infeasible, contracts often need to defer such computation until it can be done on a per-item basis.

## Possible Solution
We can widely categorise Dividends state in 3 parts:
    * not yet credited
    * credited but not transferred
    * transferred
All new dividends owed to a particular account start in the “not yet credited” state. Once that account is part of a transfer or withdrawal, the contract code will compute the amount owed to that account and credit it, which moves the amount to the “credited but not transferred” status. Actual withdrawals move those credits to the final “transferred” state.

