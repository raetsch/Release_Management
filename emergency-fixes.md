an emergency fix is a special case of a found bug after release. it requires urgent attention and fixing. That is, why new developed code should not find its way into the main branch before release. 
the emergency fix often requires a small change and is therefore easy and fast to test, which is absolutely important. with further new code in the main branch, the team has to check for dependencies and so on. this will slow down a fix, which could lead to really big problems.
after the fix is brought into the network, it can be merged into the dev code and it can be reacted on the code change.
so, in order to release an emergency fix:
- fix it
- test it in testnet (if it is possible to reproduce the problem there)
- test in live-network
- release it
- merge the code to dev-branch
