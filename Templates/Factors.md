```c++
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

vector<int> getFactors(int n) {
    vector<int> factors;
    
    for (int i = 1; i <= sqrt(n); ++i) {
        if (n % i == 0) {
            factors.push_back(i);
            if (i != n / i) { // Avoid duplicates like 4*4 = 16
                factors.push_back(n / i);
            }
        }
    }

    return factors;
}




```


