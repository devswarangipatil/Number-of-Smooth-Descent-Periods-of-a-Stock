# Number-of-Smooth-Descent-Periods-of-a-Stock

You are given an integer array prices representing the daily price history of a stock, where prices[i] is the stock price on the ith day.

A smooth descent period of a stock consists of one or more contiguous days such that the price on each day is lower than the price on the preceding day by exactly 1. The first day of the period is exempted from this rule.

Return the number of smooth descent periods.

class Solution:
    def getDescentPeriods(self, prices: List[int]) -> int:

        tally, ans = 1, 0
        triangle = lambda x: x * (x + 1)//2

        for p1, p2 in pairwise(prices):
            if p2 == p1 - 1:
                tally+= 1
            else:
                ans+= triangle(tally)
                tally = 1
                
        ans+= triangle(tally)

        return  ans
