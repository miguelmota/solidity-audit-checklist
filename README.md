<h1 align="center">
  <br />
  <img src="https://user-images.githubusercontent.com/168240/40218684-0e4f3e12-5a27-11e8-8a4f-ef2e4af685bd.png" alt="Solidity Audit Checklist" width="700" />
  <br />
  <br />
  <br />
</h1>

> A checklist of things to look for when auditing a Solidity Smart contract

This is not a comprehensive list and solidity is quickly evolving so please do due dilegence on your part.

Not all listed items will apply to your specific smart contract.

In no particular order:

- [ ] All functions are `internal` except where explictly required to be `public`/`external`.
- [ ] There are no arithmetic overflows/underflows in math operations.
- [ ] Using the OpenZeppelin safe math library [[?](https://github.com/OpenZeppelin/openzeppelin-solidity/tree/master/contracts/math)].
- [ ] Ether or tokens cannot be accidentally sent to the address `0x0`.
- [ ] State is being set first, transfer actions last.
- [ ] Protected from reentry attacks.
- [ ] Properly implements the ERC20 interface [[?](https://github.com/ethereum/eips/issues/20)].
- [ ] Only using modifier if necessary in more than one place.
- [ ] All types are being explicitly set (e.g. using `uint256` instead of `uint`).
- [ ] All methods and loops are withing the maximum allowed gas limt.
- [ ] There are no unnecessary initalizations in the constructor (remember, default values are set).
- [ ] There is complete test coverage; every smart contract method and every possible type of input is being tested.
- [ ] Performed fuzz testing by using random inputs.
- [ ] Tested all the possible different states that the contract can be in.
- [ ] Ether and token amounts are dealt in wei units.
- [ ] The crowdsale end block/timestamp comes after start block/timestamp.
- [ ] The crowdsale token exchange/conversion rate is properly set.
- [ ] The crowdsale soft/hard cap is set.
- [ ] The crowdsale min/max contribution allowed is set and tested.
- [ ] The crowdsale whitelisting functionality is tested.
- [ ] The crowdsale refund logic is tested.
- [ ] Crowdsale participants are given their proportional token amounts or are allowed to claim their contribution.
- [ ] The length of each stage of the crowdsale set (e.g. presale, public sale).
- [ ] Specified which functions are intented to be controlled by the owner only (e.g. pausing crowdsale, progressing crowdsale stage, enabling distribution of tokens, etc..).
- [ ] The crowdsale vesting logic is tested.
- [ ] The crowdsale has a fallback function in place if it makes reasonable sense.
- [ ] The fallback function does not accept call data or only accepts prefixed data to avoid function signature collisions.
- [ ] Imported contracts have been previously audited.
- [ ] Token transfer statements are wrapped in a `require`.
- [ ] Conditions are checked using `require` before operations and state changes.
- [ ] Using `require` and `assert` properly. Only use `assert` for things that should never happen, typically used to validate state after making changes.
- [ ] Using `keccak256` instead of the alias `sha3`.
- [ ] Protected from ERC20 short address attack. [[?](https://vessenes.com/the-erc20-short-address-attack-explained/)].
- [ ] Protected from recursive call attacks.
- [ ] Arbitrary string inputs have length limits.
- [ ] No secret data is exposed (all data on the blockchain is public).
- [ ] Avoided using array where possible and using mappings instead.
- [ ] Does not rely on block hashes for randomness (miners have influence on this).
- [ ] Does not use `tx.origin` anywhere. [[?](https://vessenes.com/tx-origin-and-ethereum-oh-my/)]
- [ ] Array items are shifted down when an item is deleted to avoid leaving a gap.
- [ ] Using the latest stable version of Solidity.


## Resources

- [List of helper/utility functions](./UTILS.md)
- [Smart contract best pracitices](https://github.com/ConsenSys/smart-contract-best-practices)
- [Solidity idiosyncrasies](https://github.com/miguelmota/solidity-idiosyncrasies)

## License

MIT

<!--

https://ethereum.stackexchange.com/questions/6204/writing-secure-smart-contracts-in-solidity
https://ethereum.stackexchange.com/questions/8551/methodological-security-review-of-a-smart-contract
https://www.kingoftheether.com/contract-safety-checklist.html


http://solidity.readthedocs.io/en/develop/security-considerations.html
-->