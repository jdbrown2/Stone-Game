# Stone-Game

We can make the game a little simpler by saying that Alex choosing a number will increase his score
and Lee choosing a number will decrease Alex's score. If Alex's score is positive, he has more stones than Lee and we return true.
Let's list the piles like this: `piles[i], piles[i+1], ..., piles[j-1], piles[j]` and call the highest possible score 
of the remaining piles `dp(i, j)`. Assuming we already know the answer to the inside of the problem, we just need to find the number that
maximizes Alex's score on his turn and minimizes Alex's score on Lee's turn because they both play optimally.
We can use a 2d array `dp[][]` to store the values of each optimal outcome given every possible choice of pile.

On each turn there are only two options of piles to take: `piles[i]` and `piles[j]`.  
If it's Alex's turn he wants the maximum between `piles[i] + dp(i+1, j)` and `piles[j] + dp(i, j-1)`.  
If it's Lee's turn he wants the minimum between `dp(i+1, j) - piles[i]` and `dp(i, j-1) - piles[j]`.
Either way, we store that value in the next slot in the 2d array `dp[i+1][j+1]` so we can reuse that value for calculating the optimal play when picking up the other piles.
