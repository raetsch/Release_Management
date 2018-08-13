# Running code in testnet

After the code is published to the dev-repo, it is first installed in a test environment.
For cryptocurrencies or -platforms it is typically a testnet, very similar to the live network. It could also be a closed lab environment, but as most development groups are lacking ressources, it will be a small testnet.
The nature of a testnet is very often an unstable, changing structure, which has advantages and disadvantages. For example one advantage is the fluctuation of nodes, this is sometimes good to see the behaviour of the code, when the live network gets unstable. a disadvantage is, that you sometimes have to repeat tests because somebody just interfered your running testcase.

In this stage, testers should repeat all testcases the developer alreasy wrote down. This environment is different, the used platform to test is different, we are closer to an end-to-end situation and here, first unexpected influences get visible.
Additionally, a tester should also think about other testcases (and also write them down) and he should try to break the function!
At the end of the tests, both, developer and testers should decide, which testcases must be done on every following release, to guarantee that the new release did not break the function.
The decision has to be documented so that the testcases can be done by something else next time.

After this decision, the code is ready to enter the live-network

[live-network evaluation phase](livenet-eval.md)