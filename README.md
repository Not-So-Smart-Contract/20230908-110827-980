>**了解智能合约审计和最佳实践请**[点击查看文档](https://safful.com/) 

# 智能合约漏洞，2023 年 Web3 中最常见的 10 个漏洞

## 介绍

由区块链技术支持的智能合约通过提供去中心化和自动化的功能彻底改变了各个行业。然而，它们也给去中心化应用程序的操作和设计带来了新型的安全挑战。
在本文中，我们将探讨开发人员和审计人员应该注意的**十大最常见的智能合约漏洞**，以便构建安全、强大的智能合约。
*注意：通过 Immunefi 提交的大多数项目和错误都使用*基于 EVM 的区块链*。因此，本文将重点讨论这些技术。然而，这些分类可通用扩展到任何区块链技术。*
进入此列表的漏洞是通过分析 2023 年第一季度的黑客攻击和通过 Immunefi 发现的错误修复来确定的。

## V01: 输入验证不正确

### **概述**

不正确的输入验证是通过 Immunefi 提交的大量已确认漏洞报告以及在外被利用的主要原因。输入验证是一项关键的安全实践，涉及验证系统数据输入的完整性、准确性和安全性。未能正确验证输入可能会为攻击者利用和操纵系统行为开辟途径。

### **描述**

当智能合约无法充分验证和清理（sanitize）用户输入时，就会发生不正确的输入验证，从而使他们容易受到各种类型的攻击。此类漏洞可被利用来操纵合约逻辑、注入恶意数据或导致意外行为。正确的输入验证可确保合约仅处理有效且预期的数据，从而降低被利用的风险。

### **预防**

为了防止此类漏洞，开发人员应该实施全面的输入验证例程。这包括验证数据类型、检查边界条件以及清理用户输入以防止发生意外情况。为了确保稳健的输入验证，必须考虑所有可能的输入场景，包括边缘情况和意外输入。一些可以帮助开发人员防止遗漏边缘情况的工具和技术是[模糊测试](https://github.com/crytic/echidna)或[符号执行](https://github.com/ConsenSys/mythril)。这些工具可以帮助开发人员测试各种输入，以确保恶意输入不会破坏智能合约的不变量或执行。

### **例子**

[Beanstalk Logic 错误修复审计](https://medium.com/immunefi/beanstalk-logic-error-bugfix-review-4fea17478716)展示了缺少输入验证漏洞的示例。 Beanstalk Token Facet 合约的 transferTokenFrom() 函数中存在漏洞，其中 msg.sender 的授权额度在 EXTERNAL 模式下未正确验证。该缺陷允许攻击者从之前已批准 Beanstalk 合约的受害者账户中转移资金。

## 参考文章

- [https://medium.com/immunefi/sovryn-loan-vulnerability-postmortem-ffaf4d1d688f](https://medium.com/immunefi/sovryn-loan-vulnerability-postmortem-ffaf4d1d688f)
- [https://medium.com/immunefi/zapper-arbitrary-call-data-bug-fix-postmortem-d75a4a076ae9](https://medium.com/immunefi/zapper-arbitrary-call-data-bug-fix-postmortem-d75a4a076ae9)
- [https://medium.com/immunefi/cream-finance-insufficient-validation-bug-fix-postmortem-1ec7248e8865](https://medium.com/immunefi/cream-finance-insufficient-validation-bug-fix-postmortem-1ec7248e8865)
- [https://medium.com/immunefi/pancakeswap-logic-error-bug-fix-postmortem-f2d02adb6983](https://medium.com/immunefi/pancakeswap-logic-error-bug-fix-postmortem-f2d02adb6983)
- [https://medium.com/immunefi/mcdex-insufficient-validation-bug-fix-postmortem-182fc6cab899](https://medium.com/immunefi/mcdex-insufficient-validation-bug-fix-postmortem-182fc6cab899)
- [https://medium.com/immunefi/polygon-lack-of-balance-check-bugfix-postmortem-2-2m-bounty-64ec66c24c7d](https://medium.com/immunefi/polygon-lack-of-balance-check-bugfix-postmortem-2-2m-bounty-64ec66c24c7d)
- [https://medium.com/immunefi/notional-double-counting-free-collateral-bugfix-review-28b634903934](https://medium.com/immunefi/notional-double-counting-free-collateral-bugfix-review-28b634903934)
- [https://medium.com/immunefi/port-finance-logic-error-bugfix-review-29767aced446](https://medium.com/immunefi/port-finance-logic-error-bugfix-review-29767aced446)
- [https://medium.com/immunefi/aurora-withdrawal-logic-error-bugfix-review-c5b4e30a9160](https://medium.com/immunefi/aurora-withdrawal-logic-error-bugfix-review-c5b4e30a9160)
- [https://medium.com/immunefi/aurora-improper-input-sanitization-bugfix-review-a9376dac046f](https://medium.com/immunefi/aurora-improper-input-sanitization-bugfix-review-a9376dac046f)
- [https://medium.com/immunefi/mt-pelerin-double-transaction-bugfix-review-503838db3d70](https://medium.com/immunefi/mt-pelerin-double-transaction-bugfix-review-503838db3d70)
- [https://medium.com/immunefi/balancer-logic-error-bugfix-review-74f5edca8b1a](https://medium.com/immunefi/balancer-logic-error-bugfix-review-74f5edca8b1a)
- [https://medium.com/immunefi/beanstalk-logic-error-bugfix-review-4fea17478716](https://medium.com/immunefi/beanstalk-logic-error-bugfix-review-4fea17478716)
- [https://medium.com/immunefi/hack-analysis-platypus-finance-february-2023-d11fce37d861](https://medium.com/immunefi/hack-analysis-platypus-finance-february-2023-d11fce37d861)

## V02: 计算错误

### **概述**

在我们在 Immunefi 上看到的已确认错误报告中，计算错误紧随其后。
智能合约中不正确或不一致的计算可能会导致意想不到的后果，例如代币余额不准确、奖励分配不正确或合约执行期间出现意外结果。不正确的计算通常与未充分探索的代码路径配对，并且与不正确的输入验证错误密切相关。然而，不正确的计算处理的是一些漏洞，其中本打算让用户能够执行某些操作，但由于不正确的计算，用户可能会从该操作中获得比预期更多的回报。

### **描述**

在智能合约中，当数学运算执行不正确时，就会发生错误的计算，从而导致意外或不正确的结果。这些漏洞可能由多种原因引起，例如对精度、值范围的错误假设，或合约不同部分的计算不一致。当合约未能考虑边缘情况或正确处理极端情况时，也可能会出现错误的计算。在某些情况下，合约可能无法考虑极值，或者无法处理溢出或下溢，从而导致意外行为或安全风险。攻击者可以利用这些漏洞来操纵计算或在合约中获得未经授权的优势。适当的数学精度和对极端情况的仔细考虑对于防止此类漏洞至关重要。

### **预防**

单元测试以及模糊测试或符号执行可以帮助缺少丢失的边缘情况渗透到代码库中。此外，数学方程的形式验证将有助于为可能存在的状态提供保证。使用经过充分测试且安全的数学库或区块链平台提供的内置函数来准确地执行计算。这些库通常具有针对常见计算错误（例如上溢或下溢）的内置保护。

### **例子**

[88MPH 盗窃无人认领](https://medium.com/immunefi/88mph-theft-of-unclaimed-mph-rewards-bugfix-review-1dec98b9956b)的 MPH 奖励 Bugfix Review 演示了一种计算不正确的情况，其中 MPH 奖励是使用不正确的 rewardPerToken 计算的，这将允许攻击者完全耗尽 MPH 奖励合约无人认领的资金。

### **参考文章**

- [https://medium.com/immunefi/armorfi-bug-bounty-postmortem-cf46eb650b38](https://medium.com/immunefi/armorfi-bug-bounty-postmortem-cf46eb650b38)
- [https://medium.com/immunefi/vesper-rebase-vulnerability-postmortem-and-bug-bounty-55354a49d184](https://medium.com/immunefi/vesper-rebase-vulnerability-postmortem-and-bug-bounty-55354a49d184)
- [https://medium.com/immunefi/pods-finance-bug-fix-postmortem-61a576897ebd](https://medium.com/immunefi/pods-finance-bug-fix-postmortem-61a576897ebd)
- [https://medium.com/immunefi/tidal-finance-logic-error-bug-fix-postmortem-3607d8b7ed1f](https://medium.com/immunefi/tidal-finance-logic-error-bug-fix-postmortem-3607d8b7ed1f)
- [https://medium.com/immunefi/belt-finance-logic-error-bug-fix-postmortem-39308a158291](https://medium.com/immunefi/belt-finance-logic-error-bug-fix-postmortem-39308a158291)
- [https://medium.com/immunefi/cronos-theft-of-transactions-fees-bugfix-postmortem-b33f941b9570](https://medium.com/immunefi/cronos-theft-of-transactions-fees-bugfix-postmortem-b33f941b9570)
- [https://medium.com/immunefi/apwine-incorrect-check-of-delegations-bugfix-review-7e401a49c04f](https://medium.com/immunefi/apwine-incorrect-check-of-delegations-bugfix-review-7e401a49c04f)
- [https://medium.com/immunefi/polygon-consensus-bypass-bugfix-review-7076ce5047fe](https://medium.com/immunefi/polygon-consensus-bypass-bugfix-review-7076ce5047fe)
- [https://medium.com/immunefi/synthetix-logic-error-bugfix-review-40da0ead5f4f](https://medium.com/immunefi/synthetix-logic-error-bugfix-review-40da0ead5f4f)
- [https://medium.com/immunefi/building-a-poc-for-the-uranium-heist-ec83fbd83e9f](https://medium.com/immunefi/building-a-poc-for-the-uranium-heist-ec83fbd83e9f)
- [https://medium.com/immunefi/hack-analysis-saddle-finance-april-2022-f2bcb119f38](https://medium.com/immunefi/hack-analysis-saddle-finance-april-2022-f2bcb119f38)
- [https://medium.com/immunefi/88mph-theft-of-unclaimed-mph-rewards-bugfix-review-1dec98b9956b](https://medium.com/immunefi/88mph-theft-of-unclaimed-mph-rewards-bugfix-review-1dec98b9956b)

## V03: 预言机/价格操纵

### **概述**

智能合约通常依赖于称为预言机的外部数据源来做出明智的决策。如果这些预言机受到损害或操纵，可能会导致兑换定价不正确、奖励计算不正确、借入的资产超过抵押比率允许的资产，或金融交易的其他一般问题。对这些外部数据源的操纵是链上发生 DeFi 攻击的主要原因之一。选择可信的预言机并实施安全的数据验证机制对于减轻与预言机/价格操纵相关的风险至关重要。

### **描述**

由于许多协议会根据用户操作更新资产定价，因此这可能是一个明显但容易被忽视的漏洞，因为价格预计会根据用户交互进行更新。然而，当协议依赖于这些内部或外部定价机制时，应仔细考虑以确保现货价格不会被滥用。价格操纵能否有效执行也很大程度上取决于当前的链上状况。流动性较弱的资金池比流动性较高的资金池面临更高的操纵风险。仔细选择可信的预言机并实施安全的数据验证机制至关重要。过期检查、平均定价机制和只读重入保护可能是实现外部定价机制稳健集成的重要功能。数据源的多样化还可以防止单一协议中的漏洞对整个区块链生态系统造成严重破坏。

### **预防**

为了防止预言机/价格操纵漏洞，开发人员应仔细选择具有良好记录的可信预言机。实施安全数据验证机制，例如加密证明或多数据源聚合，有助于确保接收数据的准确性和完整性。定期审核和监控预言机合约及其与智能合约的交互也可以帮助识别潜在的漏洞。不应对从外部预言机返回的数据的准确性做出假设，并且应采取保护措施以防止临时价格操纵或陈旧数据影响协议的运行。

### **例子**

[BonqDAO](https://medium.com/immunefi/hack-analysis-bonqdao-february-2023-ef6aab0086d6) 经历了价格预言机操纵攻击，攻击者可以暂时抬高 WALBT 代币的价格，以便借入比有权借入的更多的稳定币 (BEUR)。然后，攻击者再次操纵价格，将其降低到非常小的值，以清算 30 多个抵押不足的持仓。 BonqDAO 容易受到攻击的原因并不是其价格报告机制的无许可性质，而是它将协议合约的现货价格视为最后记录的价值。因此，任何人都可以暂时夸大或缩小给定喂价的价值。

### **参考文章**

- [https://medium.com/immunefi/fei-protocol-vulnerability-postmortem-483f9a7e6ad1](https://medium.com/immunefi/fei-protocol-vulnerability-postmortem-483f9a7e6ad1)
- [https://medium.com/immunefi/fei-protocol-flashloan-vulnerability-postmortem-7c5dc001affb](https://medium.com/immunefi/fei-protocol-flashloan-vulnerability-postmortem-7c5dc001affb)
- [https://medium.com/immunefi/mushrooms-finance-theft-of-yield-bug-fix-postmortem-16bd6961388f](https://medium.com/immunefi/mushrooms-finance-theft-of-yield-bug-fix-postmortem-16bd6961388f)
- [https://medium.com/immunefi/enzyme-finance-price-oracle-manipulation-bug-fix-postmortem-4e1f3d4201b5](https://medium.com/immunefi/enzyme-finance-price-oracle-manipulation-bug-fix-postmortem-4e1f3d4201b5)
- [https://medium.com/immunefi/hack-analysis-cream-finance-oct-2021-fc222d913fc5](https://medium.com/immunefi/hack-analysis-cream-finance-oct-2021-fc222d913fc5)
- [https://medium.com/immunefi/hack-analysis-bonqdao-february-2023-ef6aab0086d6](https://medium.com/immunefi/hack-analysis-bonqdao-february-2023-ef6aab0086d6)

## V04: 弱访问控制

### **概述**

薄弱的访问控制机制可能会导致未经授权的用户或恶意行为者未经授权地访问智能合约中的关键功能或数据。访问控制对于确保只有授权实体才能与特定功能交互或修改关键参数至关重要。

### **描述**

必须实施适当的访问控制措施，例如基于角色的权限和强大的身份验证机制，以防止未经授权的访问。清楚地记录系统内参与者的这些限制和能力可以帮助突出哪些操作面临严重漏洞的风险。此类文档可以促进改进的单元测试和潜在冲突的识别，确保系统按预期运行，并最大限度地减少因单个缺失检查而导致严重漏洞的风险。项目还应确保角色在允许的操作中受到尽可能的限制，以防止来自 web2 世界的风险对整个系统造成不可挽回的损害。如果角色不够精细，或者协议严重依赖集中化作为安全模型，那么私钥被盗将造成极其严重的破坏。

### 预防

为了防止弱访问控制漏洞，开发人员应该实施基于角色的访问控制机制。在合约文档中明确定义角色及其相关权限。实施强大的签名验证并使用经过验证和测试的库。定期审查和更新访问控制机制，以应对系统要求或用户角色的任何变化。

### **例子**

[Enzyme Finance](https://medium.com/immunefi/enzyme-finance-price-oracle-manipulation-bug-fix-postmortem-4e1f3d4201b5) 奖励了一位研究人员，因为该研究人员发现了与名为 “Gas Station Network” 的外部组件集成所产生的漏洞。Gas Station Network 是一个去中心化的中继网络，允许 dApp 代替个人用户支付交易费用。Paymaster （代用户发起交易的角色）缺少对可信转发器的验证，该转发器返回中继使用的待退款资金金额。如果你喜欢视频，我们建议你观看我们对 Sense Finance 5 万美元赏金支付的[分析](https://www.youtube.com/watch?v=m7hDtIV_h_o)。

### **参考文章**

- [https://medium.com/immunefi/88mph-function-initialization-bug-fix-postmortem-c3a2282894d3](https://medium.com/immunefi/88mph-function-initialization-bug-fix-postmortem-c3a2282894d3)
- [https://medium.com/immunefi/mushrooms-finance-logic-error-bug-fix-postmortem-780122821621](https://medium.com/immunefi/mushrooms-finance-logic-error-bug-fix-postmortem-780122821621)
- [https://medium.com/immunefi/alchemix-access-control-bug-fix-debrief-a13d39b9f2e0](https://medium.com/immunefi/alchemix-access-control-bug-fix-debrief-a13d39b9f2e0)
- [https://medium.com/immunefi/openzeppelin-bug-fix-postmortem-66d8c89ed166](https://medium.com/immunefi/openzeppelin-bug-fix-postmortem-66d8c89ed166)
- [https://medium.com/immunefi/sense-finance-access-control-issue-bugfix-review-32e0c806b1a0](https://medium.com/immunefi/sense-finance-access-control-issue-bugfix-review-32e0c806b1a0)
- [https://medium.com/immunefi/enzyme-finance-missing-privilege-check-bugfix-review-ddb5e87b8058](https://medium.com/immunefi/enzyme-finance-missing-privilege-check-bugfix-review-ddb5e87b8058)

## V05: 重放攻击/签名延展性

### **概述**

密码学是所有智能合约功能的核心。协议中实现的加密原语通常基于链以无需许可的方式操作的相同原语。然而，它们有时可能会被错误地使用，导致操作执行的次数超过预期，从而导致财务损失或合约状态不正确。

### 描述

当攻击者重放有效交易或消息以欺骗智能合约多次执行某项操作时，就会发生重放攻击。基于 EVM 的链可以访问原语 ecrecover ，它允许智能合约验证某些数据是否已由恢复的地址验证和签名。然而，这个函数不实现任何类型的重放保护。
通常，重放保护是通过引入随机数 Nonce（使用过一次的数字）来实现的，该随机数在使用签名时递增，防止一旦更新随机数就再次使用原始签名。签名延展性（Signature malleability）是指可修改签名而不使其失效的能力，允许签名使用两次。当对数据进行编码或在类型之间进行转换时，可能会使用签名延展性，其中在检查签名时会忽略值的某些部分或位，但会整体使用它来防止重放攻击。

### 预防

为了防止重放攻击和签名延展性漏洞，开发人员应该实现基于随机数 nonce 的交易管理。 Nonce 可以确保每笔交易都是唯一的并防止重放攻击。此外，实施适当的签名验证检查（例如验证签名的完整性和真实性）可以帮助防止签名延展性攻击。合约设计还应包括防止重复意外操作的机制，例如一次性使用代币或唯一交易标识符。

### 例子

当时历史上支付最高的赏金，Polygon 的双花漏洞，处理的是 Polygon 的 WithdrawManager 中的一个错误，该错误验证了先前区块中销毁交易的包含性和唯一性。编码的方法 branchMask 允许将多个唯一分支掩码编码为相同的退出 ID。这种签名的延展性允许攻击者仅存入 10 万美元并重复使用签名，从而导致 2230 万美元的损失。

### 参考文章

- [https://medium.com/immunefi/polygon-double-spend-bug-fix-postmortem-2m-bounty-5a1db09db7f1](https://medium.com/immunefi/polygon-double-spend-bug-fix-postmortem-2m-bounty-5a1db09db7f1)
- [https://medium.com/immunefi/hack-analysis-nomad-bridge-august-2022-5aa63d53814a](https://medium.com/immunefi/hack-analysis-nomad-bridge-august-2022-5aa63d53814a)
- [https://medium.com/immunefi/hack-analysis-binance-bridge-october-2022-2876d39247c1](https://medium.com/immunefi/hack-analysis-binance-bridge-october-2022-2876d39247c1)

## V06: 舍入误差

### 概述

浮点运算和舍入误差处理不当可能会导致财务差异或合约逻辑被利用。精确处理数值运算，在适用的情况下使用定点算术，对于避免此类漏洞至关重要。通常，这些漏洞可能出现在无需许可的兑换协议中，其中非标准小数位数（decimal）值可能会带来不可预见的后果。

### 描述

当智能合约执行涉及浮点算术的计算并且无法考虑精度或舍入时，就会出现舍入错误。这些错误可能会导致财务差异、资金损失或合约中计算的奖励不正确。智能合约应使用定点算术或替代机制来准确处理小数计算，确保最小化或消除舍入误差。

### 预防

为了防止舍入错误，开发人员应使用定点算术或提供精确数值运算的库。定点算术使用整数值来表示小数，避免了与浮点算术相关的不精确性。此外，对数值运算（包括边界条件和极端情况）的彻底测试和验证可以帮助识别和解决潜在的舍入错误。

### 例子

值得注意的是，[DFX Finance](https://medium.com/immunefi/dfx-finance-rounding-error-bugfix-review-17ba5ffb4114) 修复了一个漏洞，该漏洞包括由于非标准小数位数（2 位）而导致 EURS 代币出现舍入错误。Assimilators 对于 DFX Finance 的自动做市商来说是必要的，因为所有资产都与 USDC 配对。 Assimilator V2 合约负责将所有金额转换为计价单位，或用于跨协议计算的基础值。当整数除法导致从用户转移零代币时，就会出现问题，尽管用户仍然收到代表他们在曲线池中的部分的曲线代币。

### 参考文章

- [https://medium.com/immunefi/moonbeam-astar-and-acala-library-truncation-bugfix-review-1m-payout-41a862877a5b](https://medium.com/immunefi/moonbeam-astar-and-acala-library-truncation-bugfix-review-1m-payout-41a862877a5b)
- [https://medium.com/immunefi/dfx-finance-rounding-error-bugfix-review-17ba5ffb4114](https://medium.com/immunefi/dfx-finance-rounding-error-bugfix-review-17ba5ffb4114)

## V07: 重入攻击

### 概述

重入攻击在以太坊中有着悠久的历史，是造成 The DAO Hack 的漏洞类别，DAO Hack 是 2016 年早期以太坊网络上最大的攻击之一。重入允许攻击者在上一次调用完成之前重复调用易受攻击的合约，从而导致意外的情况发生。状态变化和未经授权的资金转移。

### 描述

当合约允许在执行期间对其进行外部调用而没有正确管理状态更改和执行流程时，就会出现重入漏洞。重入攻击是允许攻击者在上一次调用完成之前重复调用易受攻击的合约，从而导致意外的状态更改和未经授权的资金转移。实施安全状态管理模式并应用互斥锁可以降低重入攻击的风险。一些可以帮助你识别合约中可能存在重入的工具包括 [Slither](https://github.com/crytic/slither)、[Mythril](https://github.com/ConsenSys/mythril) 和 [Pyrometer](https://github.com/nascentxyz/pyrometer)。你可以在这篇文章[《可重入终极指南》](https://medium.com/immunefi/the-ultimate-guide-to-reentrancy-19526f105ac)中阅读有关重入的更多信息。

### 预防

为了防止重入漏洞，开发人员应遵循安全状态管理模式，例如“检查-效果-交互”(CEI) 模式。此模式可确保在执行任何外部调用之前进行所有状态更改，从而防止重入攻击。此外，实现互斥锁或使用“[ReentrancyGuard](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/ReentrancyGuard.sol)”模式可以通过阻止重入调用来进一步防止重入。

### 例子

[Omni Protocol](https://medium.com/immunefi/hack-analysis-omni-protocol-july-2022-2d35091a0109) 遭遇黑客攻击，由于其以太坊智能合约遭到重入攻击，导致 140 万美元损失。易受攻击的代码使用了 ERC721 的 safeTransferFrom 方法，该方法调用实现 onERC721Received 接口的智能合约。此外部调用将执行权移交给接收者，并引入了重入漏洞。

### 参考文章

- [https://medium.com/immunefi/hack-analysis-omni-protocol-july-2022-2d35091a0109](https://medium.com/immunefi/hack-analysis-omni-protocol-july-2022-2d35091a0109)

## V08: 抢跑

### 概述

抢跑交易（Frontrunning）是一种攻击者利用观察到待处理交易与将其包含在区块之间的时间延迟的技术。通过在受害者的交易之前将自己的交易设置为更高的 Gas 价格，攻击者可以为了自己的利益而操纵某些合约交互的结果。抢跑交易是去中心化交易所、拍卖或任何涉及交易顺序的场景的一个问题。

### 描述

当攻击者通过先于其他人执行交易而获得优势时，尤其是当他们知道即将包含在区块中的待处理交易时，就会发生抢跑交易。在智能合约的背景下，在交易顺序影响结果的情况下，抢跑交易可能是有害的。例如，在去中心化交易所中，攻击者可以观察受害者旨在以特定价格购买特定代币的待处理交易。然后，他们可以快速提交自己的较高 Gas 价格的交易，以便在受害者的交易执行之前以较低的价格购买相同的代币。这使得攻击者可以通过牺牲受害者的利益来从价格差异中获益。抢跑交易可以由观察内存池的任何人执行，但也可以源自区块生产者本身。一些链具有可以降低风险的私有 RPC，但私有内存池中的验证者和区块生产者也可能有错误的信任假设。开发人员应该在智能合约层面减少潜在的抢跑交易机会，而不是依赖外部缓解措施，因为外部缓解措施部分依赖于信任或一致的激励措施来保护其协议。

### 预防

防止抢跑交易需要结合技术和设计考虑。一些预防措施包括使用秘密或提交披露方案、实施在交易确认之前对价格或出价等敏感信息保密的方案、链下订单匹配、使用允许用户将交易捆绑在一起的 flashbots 以及将它们直接提交给矿工，减少抢跑者的机会，并优化费用以减少被抢跑者出价超过的可能性。

### 例子

在各种 DeFi 协议中都观察到了抢跑交易攻击。 [RocketPool 和 Lido](https://medium.com/immunefi/rocketpool-lido-frontrunning-bug-fix-postmortem-e701f26d7971) 已获悉存在可能影响两者质押服务的漏洞。恶意节点运营商可以通过使用相同的 validator bls key 来使用先前准备的 deposit data 和所需的最低限度的 deposit value 抢先存款来窃取用户存款。

### 参考文章

- [https://medium.com/immunefi/rocketpool-lido-frontrunning-bug-fix-postmortem-e701f26d7971](https://medium.com/immunefi/rocketpool-lido-frontrunning-bug-fix-postmortem-e701f26d7971)

## V09: 未初始化的代理

### 概述

在没有正确初始化的情况下使用代理合约可能会引入漏洞，因为攻击者可以操纵未初始化的存储变量。实施安全代理模式并进行全面的初始化检查对于防止未经授权访问未初始化的合约状态至关重要。未初始化的代理错误已导致迄今为止最高的 1000 万美元赏金支出。

### 描述

未初始化的代理合约是指代理合约的状态变量在使用前未正确初始化的情况。这可能会产生安全漏洞，因为未初始化的存储变量可能包含敏感数据或控制关键合约行为。攻击者可以通过操纵未初始化的存储变量来利用这些漏洞，以获得未经授权的访问或执行意外的操作。为了减轻这种风险，确保代理合约在生产环境中使用之前正确初始化至关重要。

### 预防

为了防止未初始化的代理漏洞，开发人员应确保在部署和使用代理之前正确初始化代理合约中的所有存储变量。这包括初始化敏感数据、访问控制权限和任何其他关键状态变量。开发人员还应该在代理合约中实施全面的初始化检查，以验证所有必需的变量和依赖项是否已正确初始化。他们还应该实施监控工具来提供二级验证，确保初始化已正确发生。这可以通过构造函数或初始化函数来实现，这些函数或初始化函数在部署后通过自动化脚本或交易捆绑调用。

### 例子

[虫洞未初始化代理](https://medium.com/immunefi/wormhole-uninitialized-proxy-bugfix-review-90250c41a43a)错误报告是迄今为止历史上支付最高的赏金：向提交该报告的白帽黑客支付了 1000 万美元。当部署 UUPS 代理合约时，“构造函数”是实现中存在的常规 Solidity 函数。该实现提供了初始化所有者的 initialize() 函数。虫洞没有初始化其实现的实现合约，这将允许攻击者获得对实现合约的控制，并自毁合约，这将导致代理合约无法继续执行，因为它们指向的逻辑合约不再存在。

### 参考文章

- [https://blog.openzeppelin.com/the-transparent-proxy-pattern](https://blog.openzeppelin.com/the-transparent-proxy-pattern)
- [https://blog.openzeppelin.com/the-state-of-smart-contract-upgrades](https://blog.openzeppelin.com/the-state-of-smart-contract-upgrades)
- [https://medium.com/immunefi/harvest-finance-uninitialized-proxies-bug-fix-postmortem-ea5c0f7af96b](https://medium.com/immunefi/harvest-finance-uninitialized-proxies-bug-fix-postmortem-ea5c0f7af96b)
- [https://medium.com/immunefi/wormhole-uninitialized-proxy-bugfix-review-90250c41a43a](https://medium.com/immunefi/wormhole-uninitialized-proxy-bugfix-review-90250c41a43a)

## V10: 治理攻击

### 概述

治理攻击是指操纵或利用去中心化协议或智能合约系统中的治理机制。这些攻击旨在破坏治理系统的决策过程、投票系统或参数调整，使攻击者获得不当的控制权或从协议中获益。

### 描述

治理攻击可以采取多种形式，包括允许在没有法定人数的情况下执行提案、允许在没有任何投票步骤的情况下执行提案，或者直接操纵其他参与者的投票。这些攻击可能会损害协议的去中心化性质并导致权力集中，或者为攻击者带来经济利益。治理攻击在去中心化自治组织（DAO）中尤其重要，因为决策权分布在代币持有者之间。

### 预防

为了防止治理攻击，重要的是建立一个强大的、定义明确的和透明的治理框架，概述决策过程、投票机制和参与规则。实施安全、防篡改的投票系统，确保投票的完整性。这可能涉及使用加密技术、零知识证明或多重签名方案来增强安全性。确保代币的公平和去中心化分配，避免投票权集中在少数实体手中。考虑使用代币归属或锁定期等机制来阻止短期操纵行为。确保大多数治理代币不会分布在交易所之间，以便恶意行为者可以获得足够的代币来一致通过提案。

### 例子

治理攻击的一个著名例子是对 Beanstalk 的攻击，这是一种无需许可的 FIAT 稳定币协议。黑客提交了两份 Beanstalk 改进提案：BIP18 和 BIP19。第一个提案建议将资金全部转移给攻击者，第二个建议将价值 25 万美元的 $BEAN 代币发送到乌克兰的官方加密捐赠地址。攻击者从 Aave、Uniswap 和 SushiSwap 借出了超过 10 亿美元，以获得足够的投票权（至少 ⅔ 多数）来触发紧急治理执行。

### 参考文章

- [https://medium.com/immunefi/hack-analysis-beanstalk-governance-attack-april-2022-f42788fc821e](https://medium.com/immunefi/hack-analysis-beanstalk-governance-attack-april-2022-f42788fc821e)

## 结论

随着智能合约不断发展并获得广泛采用，开发人员和审计人员及时了解最新的漏洞和安全最佳实践至关重要。通过解决这十大智能合约漏洞，利益相关者可以增强其智能合约的安全状况，并为基于区块链的系统的整体信任和可靠性做出贡献。
