//Zhicheng Wang
#include <iostream>
using namespace std;

// Define a Rational class
class Rational {
private:
    int numerator;     // numerator
    int denominator;   // denominator

public:
    // Constructor with two parameters
    Rational(int n, int d) : numerator(n), denominator(d) {
        if (denominator == 0) {
            throw runtime_error("Denominator cannot be zero");
        }
    }

    // Conversion function: convert Rational → double
    operator double() const {
        cout << "[DEBUG] operator double() called for Rational("
             << numerator << "/" << denominator << ")\n";
        return static_cast<double>(numerator) / static_cast<double>(denominator);
    }

    // Optional: a helper display function
    void show() const {
        cout << numerator << " / " << denominator;
    }
};

int main() {
    Rational r1(1, 4);      // Represents 1/4 = 0.25

    cout << ">>> Expression: r1 + 4" << endl;
    double result1 = r1 + 4;    // r1 → double (calls operator double()), then 4 → 4.0
    cout << "Result = " << result1 << endl << endl;

    cout << ">>> Expression: 4 + r1" << endl;
    double result2 = 4 + r1;    // r1 → double, same rule reversed
    cout << "Result = " << result2 << endl << endl;

    cout << ">>> Expression: r1 + 5.1" << endl;
    double result3 = r1 + 5.1;  // r1 → double, then double + double
    cout << "Result = " << result3 << endl << endl;

    cout << ">>> Expression: r1 + r1 (two Rational objects)" << endl;
    // double result4 = r1 + r1; //  would cause compile error
    cout << "(This would fail because there is no operator+ for two Rational objects.)" << endl;

    return 0;
}

