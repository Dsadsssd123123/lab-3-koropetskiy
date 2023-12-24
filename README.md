#include <iostream>
#include <vector>
#include <algorithm>

void calculateArrayOperations(std::vector<double>& arr) {
    
    int countGreaterThan3 = std::count_if(arr.begin(), arr.end(), [](double x) { return x > 3; });
    std::cout << "Кількість елементів масиву більших за 3: " << countGreaterThan3 << std::endl;

    
    auto maxElement = std::max_element(arr.begin(), arr.end(), [](double x, double y) {
        return std::abs(x) < std::abs(y);
    });

    if (maxElement != arr.end()) {
        
        double productAfterMax = 1.0;
        auto it = std::find(maxElement, arr.end(), *maxElement);
        if (it != arr.end()) {
            for (++it; it != arr.end(); ++it) {
                productAfterMax *= *it;
            }
        }
        std::cout << "Добуток елементів після максимального за модулем елементу: " << productAfterMax << std::endl;
    }

    
    std::sort(arr.begin(), arr.end(), [](double x, double y) {
        return (x >= 0 && y >= 0) ? false : (x >= 0);
    });
}

int main() {
    std::vector<double> array = { -2, 4, -6, 8, 0, -1, 3, 5, -7 };

    calculateArrayOperations(array);

    std::cout << "Масив після операцій: ";
    for (const auto& element : array) {
        std::cout << element << " ";
    }
    std::cout << std::endl;

    return 0;
}
