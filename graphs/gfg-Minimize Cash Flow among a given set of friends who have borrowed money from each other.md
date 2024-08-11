# [Minimize Cash Flow among a given set of friends who have borrowed money from each other](https://www.geeksforgeeks.org/minimize-cash-flow-among-given-set-friends-borrowed-money/)

![](https://badgen.net/badge/Level/Hard/red)

Given a number of friends who have to give or take some amount of money from one another. Design an algorithm by which the total cash flow among all the friends is minimized. 

### Approach Used :

-   Create a vector called ‘amount’ and store cash value each person will receive.
-   Create two priority_queues one for max_heap and another for min_heap purpose. maxQ will have only positive value. minQ will have only negative value.
-   Iterate over amount vector and insert index and its value in the queues. Zero amount will be ignored. Positive amount (credit) will go to maxQ. Negative amount (debit) will go to minQ
-   Iterate over the queues until empty and fetch max credit and min debit. If sum of both equals zero, then just print the result, else print result as mentioned and push remaining credit or debit back to the required queue.

### Code (C++)

```cpp
#include <iostream>
#include <queue>

using namespace std;

// Comparator that will be used to make priority_queue
// containing pair of integers maxHeap Comparison is based
// on second entry in the pair which represents cash
// credit/debit
struct AscCmp {
    bool operator()(const pair<int, int>& p1,
                    const pair<int, int>& p2)
    {
        return p1.second < p2.second;
    }
};

// Comparator that will be used to make priority_queue
// containing pair of integers minHeap Comparison is based
// on second entry in the pair which represents cash
// credit/debit
struct DscCmp {
    bool operator()(const pair<int, int>& p1,
                    const pair<int, int>& p2)
    {
        return p1.second > p2.second;
    }
};

class Solution {
private:
    // Below priority queues will be used as min_heap (minQ)
    // and max_heap (maxQ) First entry in the pair will be
    // person id Second entry in the pair will be cash
    // debit/credit for the same person
    priority_queue<pair<int, int>, vector<pair<int, int> >,
                   DscCmp>
        minQ;
    priority_queue<pair<int, int>, vector<pair<int, int> >,
                   AscCmp>
        maxQ;

    // This function will fill in minQ and maxQ in such a
    // way that maxQ will have only positive value. minQ
    // will have only negative value amount is taken as
    // input. amount[i] => cash credit/debit to/from person
    // i amount[i] == 0 will be ignored as no credit/debit
    // is left.
    void constructMinMaxQ(const vector<int>& amount)
    {
        for (int i = 0; i < amount.size(); ++i) {
            if (amount[i] == 0)
                continue;
            if (amount[i] > 0) {
                maxQ.emplace(i, amount[i]);
            }
            else {
                minQ.emplace(i, amount[i]);
            }
        }
    }

    // This function will iterate over minQ and maxQ until
    // empty. It will fetch max credit and min debit. If sum
    // of both is not equal to zero, then push remaining
    // credit or debit back to the required queue. At the
    // end of the loop, print result
    void solveTransaction()
    {
        while (!minQ.empty() && !maxQ.empty()) {
            pair<int, int> maxCreditEntry = maxQ.top();
            maxQ.pop();

            pair<int, int> maxDebitEntry = minQ.top();
            minQ.pop();

            // Get the remaining transaction value by adding
            // credit and debit cash
            int transaction_val = maxCreditEntry.second
                                  + maxDebitEntry.second;

            int debtor = maxDebitEntry.first,
                creditor = maxCreditEntry.first,
                owed_amount = 0;

            if (transaction_val == 0) {
                // credit and debit cash for this person is
                // cancelled out
                owed_amount = maxCreditEntry.second;
            }
            else if (transaction_val < 0) {
                // transaction_val is the debit cash which
                // is remaining, so push to the queue for
                // further processing
                owed_amount = maxCreditEntry.second;
                minQ.emplace(maxDebitEntry.first,
                             transaction_val);
            }
            else {
                // transaction_val is the credit cash which
                // is remaining, so push to the queue for
                // further processing
                owed_amount = -(maxDebitEntry.second);
                maxQ.emplace(maxCreditEntry.first,
                             transaction_val);
            }

            // Print result
            cout << "Person " << debtor << " pays "
                 << owed_amount << " to Person " << creditor
                 << endl;
        }
    }

public:
    void minCashFlow(const vector<vector<int> >& graph)
    {
        int n = graph.size();

        // Calculate the cash to be credited/debited to/from
        // each person and store in vector amount
        vector<int> amount(n, 0);
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                int diff = graph[j][i] - graph[i][j];
                amount[i] += diff;
            }
        }

        // Fill in both queues minQ and maxQ using amount
        // vector
        constructMinMaxQ(amount);

        // Solve the transaction using minQ, maxQ and amount
        // vector
        solveTransaction();
    }
};

int main()
{
    // Test case 1
    vector<vector<int> > graph = {
        { 0, 1000, 2000 },
        { 0, 0, 5000 },
        { 0, 0, 0 },
    };

    cout << "Solution 1 : " << endl;
    Solution S;
    S.minCashFlow(graph);

    // Test case 2
    vector<vector<int> > graph2 = { { 2, 63, 0, 85, 49 },
                                    { 0, 76, 0, 0, 27 },
                                    { 0, 0, 0, 17, 0 },
                                    { 73, 32, 50, 6, 71 },
                                    { 0, 86, 0, 0, 10 }

    };

    cout << "Solution 2 : " << endl;
    Solution S2;
    S2.minCashFlow(graph2);
    return 0;
}

```

### Time Complexity:
- **O(nlogn):** where N is the number of persons. Iterate over each person in O(N) and insert new value in Q in O(logN).

### Space Complexity:
- **O(n):** for storing interemediate results.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>