# SVMC
code First Duplicate
#include <iostream>
using namespace std;
int findFirstRepeating(int arr[], int n) {
    const int maxSize = n;
    int lastOccurrence[maxSize];

    for (int i = 0; i < maxSize; i++) {
        lastOccurrence[i] = -1;
    }

    int result = -1;
    int minIndex = maxSize;

    for (int i = 0; i < n; i++) {
        if (lastOccurrence[arr[i] - 1] != -1 && lastOccurrence[arr[i] - 1] < minIndex) {
            minIndex = lastOccurrence[arr[i] - 1];
            result = arr[i];
            break;
        } else {
            lastOccurrence[arr[i] - 1] = i;
        }
    }

    return result;
}

int main() {
    int numTestCases;
    cin >> numTestCases;

    for (int testCase = 1; testCase <= numTestCases; testCase++) {
        int n;
        cin >> n;
        int arr[n];

        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }

        int result = findFirstRepeating(arr, n);
        cout << "#" << testCase << " " << result << std::endl;
    }

    return 0;
}
