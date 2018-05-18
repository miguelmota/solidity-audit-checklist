# Solidity Audit Checklist

> A checklist of things to look for when auditing a Solidity Smart contract

Please do due dilegence on your part. This is not a comprehensive list and solidity is quickly evolving. Not all listed items will apply to your specific smart contract.

In no particular order:

- [ ] State is being set first and then tranfers last.
- [ ] Protected from reentry attacks.
- [ ] All functions are internal except where explictly required to be public/external.
- [ ] There are no overflows or underflows.
- [ ] Using the openzeppelin safe math library.
- [ ] Ether or tokens cannot b accidentally sent to the address `0x0`.
- [ ] Properly implements the ERC20 interface.
- [ ] Only using modifier if necessary in more than one place.
- [ ] All types are being explicitly set e.g. using `uint256` instead of `uint`.
- [ ] There are no unecessary initalizations in the constructor (remember, default values are set).
- [ ] There is complete test coverage; every smart contract method and every possible type of input is being tested.
- [ ] Tested all the possible different states that the contract can be in.
- [ ] Ether and token amounts are dealt in wei units.
- [ ] The crowdsale end block/timestamp comes after start block/timestamp.
- [ ] The crowdsale token exchange/conversion rate is properly set.
- [ ] The crowdsale soft/hard cap is set.
- [ ] The crowdsale min/max contributions allowed is set.
- [ ] The crowdsale whitelisting functionality is tested.
- [ ] The crowdsale refund logic is tested.
- [ ] The length of each stage of the crowdsale set (e.g. presale, public sale).
- [ ] Specified which functions are intented to be controlled by the owner only (e.g. pausing crowdsale, progressing crowdsale stage, enabling distribution of tokens, etc..).
- [ ] The crowdsale vesting logic is tested.
- [ ] The imported contracts have been audited.
- [ ] Token transfer statements are wrapped in a `require`.
- [ ] Using `require` and `assert` properly. Only use `assert` for things that should never happen, typically used to validate state after making changes.
- [ ] Using `keccak256` instead of the alias `sha3`.
- [ ] Protected from ERC20 short address attack. [[?](https://vessenes.com/the-erc20-short-address-attack-explained/)].
- [ ] Using latest stable version of Solidity.


<!--
NOTES
The focus of this review was to ensure the following properties:

Security: identifying security related issues within each contract and within the system of contracts.

Sound Architecture: evaluation of the architecture of this system through the lens of established smart contract best practices and general software best practices.

Code Correctness and Quality: a full review of the contract source code. The primary areas of focus include:

Correctness (does it do was it is supposed to do)
Readability (How easily it can be read and understood)
Sections of code with high complexity
Improving scalability
Quantity and quality of test coverage


// General findings
// specifc findings
  // cirticial
  // major
  // medium
  // minor

Minor issues are generally subjective in nature, or potentially deal with topics like "best practices" or "readability". Minor issues in general will not indicate an actual problem or bug in code.

The maintainers should use their own judgement as to whether addressing these issues improves the codebase.


Medium issues are generally objective in nature but do not represent actual bugs or security problems.

These issues should be addressed unless there is a clear reason not to.


Major issues will be things like bugs or security vulnerabilities. These issues may not be directly exploitable, or may require a certain condition to arise in order to be exploited.

Left unaddressed these issues are highly likely to cause problems with the operation of the contract or lead to a situation which allows the system to be exploited in some way.


Critical issues are directly exploitable bugs or security vulnerabilities.

Left unaddressed these issues are highly likely or guaranteed to cause major problems or potentially a full failure in the operations of the contract.



Disclaimerer
Overview of the audit and nice features
Attack made to the contract
Critical vulnerabilites found in the contract
Medium vulnerabilites found in the contract
Low severity vulnerabilites found
Line by line comments
Summary of the audit


// file count
// find . -name '*.sol' | wc -l

// lines of code in project
find . -name '*.sol' | xargs wc -l

// number of external calls in project
egrep '\.\w*\(.*\)' contracts/* -nr

// file signatures
shasum -a 256 *

https://ethereum.stackexchange.com/questions/6204/writing-secure-smart-contracts-in-solidity
https://ethereum.stackexchange.com/questions/8551/methodological-security-review-of-a-smart-contract
https://www.kingoftheether.com/contract-safety-checklist.html


https://github.com/ConsenSys/smart-contract-best-practices
http://solidity.readthedocs.io/en/develop/security-considerations.html
-->