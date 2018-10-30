Bismuth Maximum Supply after Hypernodes-Hardfork
=======

When Hypernodes where introduced, the Team decided to reduce Maximum Supply. When Bismuth-Mainnet started, the formula for rewards was this:
```python
if db_block_height <= 10000000:
    mining_reward = 15 - (quantize_eight(block_height_new) / quantize_eight(1000000))  # one zero less
else:
    mining_reward = 0
```

So the maximum coins, given out to miners will be **99999990 BIS**
Additionally, there is a dev reward, used for feeding the devlopers, but also pay for external developments, feasible exchange listing fees and so on. This reward is payed every 10th block and the amount is the mining_reward of this block.
To make it "easier" to understand, here is the line of code:
```python
if int(block_height_new) % 10 == 0:
    if transaction == block_transactions[-1]:  # put at the end
        execute_param(c, "INSERT INTO transactions VALUES (?,?,?,?,?,?,?,?,?,?,?,?)",
        ("0", str(time_now), "Development Reward", str(genesis_conf), str(**mining_reward**), "0", "0", "0", "0", "0", "0", str(block_height_new)))
    commit(conn)
```
In bold you can see the dev-reward is the same as the actual block:

Adding this up, the maximum supply of Bismuth was:
**109999980 BIS**

For better visibility, here is a picture:
![Oups, where is the plot?](/graphics/BIS_inf_red.png)

##Past Hardfork on block 854660##

Ok, no we go for the red line after the hn-hardfork. Here is the actual code for the mining_reward:
```python
if db_block_height <= 10000000:
    mining_reward = 15 - (quantize_eight(block_height_new) / quantize_eight(1000000 **/ 2)) - Decimal("0.8")**
    if mining_reward < 0:
        mining_reward = 0
else:
    mining_reward = 0
```

In bold, you can see the changed parts. 

What does this mean?
The reduction per Block got times 2 higher. Also 0.8 BIS per Block are collected as hypernode-rewards. They are paid weekly, so they are not part of the reduction.
The hardfork for hypernodes happened at block **854660**. So, until the hardfork, there were around **13700117 BIS** (with dev-rewards).
Now adding up with the new formula:
Pre fork: **13700117 BIS**
Post fork: **41701617 BIS**
Sum: **55401734 BIS**

There is a bigLITTE thing now at the end:

The hn rewards are actually paid infinitely. Means, after 10.000.000 blocks, the miners rewards are set to 0 (and so are dev rewards), only fees are paid. On every 10th block, the hn rewards still get paid (8 BIS). This is not meant to be the final decision, in fact it was really never discussed, how we handle hypernode rewards after block 10.000.000. So you can expect a change here in the future.