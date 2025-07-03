# A82-Array-Intersection
#include <stdio.h>
#include <stdlib.h>

int compare(const void *a, const void *b) {
    return (*(int*)a - *(int*)b);  // For sorting in ascending order
}

int main() {
    int N, M;

    // Input the lengths of the arrays
    scanf("%d %d", &N, &M);

    int nums1[N], nums2[M];
    
    // Input the elements of the first array
    for (int i = 0; i < N; i++) {
        scanf("%d", &nums1[i]);
    }
    
    // Input the elements of the second array
    for (int i = 0; i < M; i++) {
        scanf("%d", &nums2[i]);
    }

    // Step 1: Convert both arrays to sets using hash tables or sorted arrays.
    int hash1[1001] = {0}; // As the elements range from 0 to 1000
    int hash2[1001] = {0}; // Hash table for second array

    // Mark the elements in the first array
    for (int i = 0; i < N; i++) {
        hash1[nums1[i]] = 1;
    }

    // Mark the elements in the second array
    for (int i = 0; i < M; i++) {
        hash2[nums2[i]] = 1;
    }

    // Step 2: Find the intersection (common elements)
    int intersection[1001];
    int idx = 0;

    // Iterate through all possible numbers from 0 to 1000
    for (int i = 0; i <= 1000; i++) {
        if (hash1[i] && hash2[i]) {
            intersection[idx++] = i;
        }
    }

    // Step 3: Sort the result array (although, it's already sorted in ascending order)
    qsort(intersection, idx, sizeof(int), compare);

    // Step 4: Output the intersection
    for (int i = 0; i < idx; i++) {
        printf("%d ", intersection[i]);
    }
    printf("\n");

    return 0;
}
