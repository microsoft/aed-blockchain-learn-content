# Use best practices for smart contracts

The DAO Hack
2016 the Decentralized Autonomous Organization (DAO) was hacked and lost around 70 million dollars. A hacker found a loophole in the smart contract, which sent out the amount and then updated the balance. Having a look at the Check-Effect-Interaction below, what happened in the DAO Hack case was that the interact part could be looped several times and the effect happened after this.


What would have prevented this / Some best Practices:

Check-Effect-Interaction Pattern
Make sure to run all your code internally before calling external functions. 
An example is a withdrawal from an account by following these steps:
Check: First check the specified amount is available in the account.
Effect: Subtract the amount specified from the account.
Interact: The amount can be withdrawn 
In the DAO hack, the contract had a flaw where the withdraw request passes a check (does user have enough balance => true) and then executed the withdraw transaction by sending the requested balance to the attacking contract, but the attacker used a fallback function to call the withdraw function again (aka the re-entrancy attack) before their balance has been decremented / finished. Therefore rapidly and recursively draining the main DAO contract. (Essentially they did Check - Interact - Effect).
 
Having a Circuit Breaker: 
Now that the immutability of smart contracts is hopefully second nature to you… what do we do? 
We can plan for failures! 
It’s as simple as setting up a kill switch in our smart contract. If we cannot reverse damage we can at least prevent further damage by turning off our contract. 

Here is a simple implementation of the kill switch we can use in `MyFirstContract2`

… 
function kill() { if (msg.sender == owner) selfdestruct(owner); }
…
You could use the existing modifier for this kill function as well instead of doing the if statement
A Bug Bounty Program:
This is typically a later stage strategy to improve contract security. 
After you have extensively written and tested your contract on a testnet you could reward developers for finding any vulnerabilities on your testnet deployed contract. You could set a per vulnerability reward or a reward that scales with the amount of loss in your testnet contract. 
Remember to make the bounty worthwhile for other blockchain devs. 
For more information about known security flaws… feel free to review https://swcregistry.io/
What about upgrades? 
Smart contracts cannot be changed but could be “upgraded” via a proxy contract that delegates to an implementation contract (which you could change… i.e. delegate to v1 vs v2 of the implementation contract). This is a topic of active debate and research since there exists a trade off between being able to upgrade a contract and the complexity and risk with making a contract upgradable.
 
 
 
 
Some general principles and gotchas to keep in mind for security:
Be Very Paranoid / Assume you will make mistakes: to not assume this is simply arrogant, plus the cost of assuming this and being wrong is much less than the cost of not assuming this and being wrong (in the first case, maybe you wrote more tests, spent more money on the bounty program, spent time writing a redirect / kill switch function etc… in the latter case, you could lose millions of your or other people’s dollars and damage the reputation / adoption of this community)
Do not trust external calls or external contracts: it’s better to have a “safelist” and assume anything not on the list is not to be trusted
Be careful with timestamps, randomness, gas on ethereum: these  may act slightly differently than in your usual context and can be manipulated / gamed
Reuse code where possible.
KISS (keep it simple). Complexity hides bugs.
