# Utils

> some utils/helpers for when auditing

## File count of solidity files

```bash
$ find . -name '*.sol' | wc -l
      70
```

## Lines of code per solidity file

```bash
$ find . -name '*.sol' | xargs wc -l
      48 ./contracts/token/ExampleToken.sol
     116 ./contracts/whitelist/Whitelist.sol
      23 ./contracts/Migrations.sol
     284 ./contracts/models/LinearSale.sol
     176 ./contracts/vesting/DiscreteVesting.sol
     107 ./contracts/vesting/ContinuousVesting.sol

    ...

      31 ./node_modules/zeppelin-solidity/contracts/LimitBalance.sol
      35 ./node_modules/zeppelin-solidity/contracts/MerkleProof.sol
      28 ./node_modules/zeppelin-solidity/contracts/AddressUtils.sol
    4371 total
 ```

## Number of external calls in solidity files

```bash
$ egrep '\.\w*\(.*\)' contracts/* -nr
contracts/Migrations.sol:1:pragma solidity ^0.4.17;
contracts/Migrations.sol:8:    if (msg.sender == owner) _;
contracts/Migrations.sol:12:    owner = msg.sender;
contracts/Migrations.sol:21:    upgraded.setCompleted(last_completed_migration);
contracts/models/LinearSale.sol:1:pragma solidity ^0.4.21;
contracts/models/LinearSale.sol:3:import 'zeppelin-solidity/contracts/math/SafeMath.sol';

  ...

contracts/models/LinearSale.sol:176:        uint256 tokensRemaining = totalTokensDistributable.sub(numTokensDistributed);
contracts/models/LinearSale.sol:177:        uint256 weiRemaining = totalWeiReceivable.sub(totalWeiCollected);
contracts/models/LinearSale.sol:178:        return endRate.add(TWO.mul(tokensRemaining.sub(previousWeiSubmitted.mul(previousRate)).sub(endRate.mul(weiRemaining))).div(weiRemaining));
contracts/models/LinearSale.sol:185:        require(block.timestamp > endTimestamp);
```

## SHA256 hash of files

```bash
$ shasum -a 256 contracts/*.sol
98a2f9cf3f6d74d71d23374f6b118f9a4ecc12e0b2b701f3b7ba1fb7d5bc8026  contracts/Migrations.sol
```
