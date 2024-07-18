import java.util.*;

class Solution {
    public int maxProfit(int[] prices) {
        int n = prices.length;
        long[][] dp = new long[n + 1][2];
        dp[n][0] = 0;
        dp[n][1] = 0;
  
        for (int ind = n - 1; ind >= 0; ind--) {
            for (int flg = 0; flg <= 1; flg++) {
                long ans = 0;

                if (flg == 1) {
                    long take = -prices[ind] + dp[ind + 1][0];
                    long ntake = dp[ind + 1][1];
                    ans = Math.max(take, ntake);
                } else {
                    long take = prices[ind] + dp[ind + 1][1];
                    long ntake = dp[ind + 1][0];
                    ans = Math.max(take, ntake);
                }
                dp[ind][flg] = ans;
            }
        }
        return (int) dp[0][1];
    }
}
