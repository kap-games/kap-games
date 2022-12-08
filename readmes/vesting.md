# Vesting

The vesting contract is used by team members and private investors, both to lock and to vest their KAP allocations. Vesting agreements are set to begin at a specified timestamp (i.e. a cliff), after which linear vesting occurs over a specified time period. For example, linear vesting over 52 weeks means that 1 week after vesting starts the beneficiary will be able to collect 1/52 of their KAP allocation.

A beneficiary of a vesting agreement can choose to appoint a voting delegate. As the vesting contract balance associated with the beneficiary increases and decreases, the appointed delegate's voting weight will increase and decrease equivalently. The vesting contract balance associated with a beneficiary is the sum of all uncollected KAP promised to the beneficiary. In particular, the KAP contained in vesting agreements which will unlock in the future is counted towards current voting weight.

We use a two-step process for changing delegates. The fundamental issue we must prevent is a delegate-change wherein the new delegate and the old delegate both vote on the same proposal. When a beneficiary chooses to change their delegate, our implementation requires that the beneficiary first delegates to the zero address for an amount of time equal to the voting period.

The caller of `Vesting.createVestingAgreement` is the core team multisig. There is a technical danger of the team multisig "recycling" voting weight by rapidly creating short-term vesting agreements and voting on the same proposal with each of them. Of course, this is not a genuine security concern because the core team would have other more effective ways of damaging the project should they wish. As the Kapital DAO reaches maturity and the original founders begin to step down, it is expected that the DAO votes to remove the vesting contract as a valid source of voting weight, and replaces it with a more truely decentralized mechanism.