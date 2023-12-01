#include <stdio.h>
#include <limits.h>

// Function to find the minimum of two values
int min(int a, int b) {
    return (a < b) ? a : b;
}

// Function to construct optimal BST and calculate minimum cost
int optimalBST(int keys[], int freq[], int n) {
    // Create a 2D table to store subproblem solutions
    int dp[n][n];

    // Initialize the table
    for (int i = 0; i < n; i++) {
        dp[i][i] = freq[i];
    }

    // Fill the table diagonally based on the subproblem size
    for (int len = 2; len <= n; len++) {
        for (int i = 0; i <= n - len + 1; i++) {
            int j = i + len - 1;
            dp[i][j] = INT_MAX;

            // Try all keys as the root and find the minimum cost
            for (int r = i; r <= j; r++) {
                int c = ((r > i) ? dp[i][r - 1] : 0) +
                        ((r < j) ? dp[r + 1][j] : 0) +
                        freq[r];

                dp[i][j] = min(dp[i][j], c);
            }
        }
    }

    return dp[0][n - 1];
}

int main() {
    int n;

    // Input the number of elements
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int keys[n];
    int freq[n];

    // Input keys
    printf("Enter the keys:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &keys[i]);
    }

    // Input frequencies
    printf("Enter the frequencies:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &freq[i]);
    }

    // Calculate and print the minimum cost of optimal BST
    int minCost = optimalBST(keys, freq, n);
    printf("Minimum cost of optimal BST: %d\n", minCost);

    return 0;
}
