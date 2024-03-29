# Luhn-Algorithm-in-C-
Creating a Luhn algorithm to validate a credit card
#include <iostream>
using namespace std;
int main() {

    long long credit_info, credit; // long var used because of high data value as credit card numbers have more than 10 digits
    int length = 0, counter, remaind, sum = 0;

    cout << "Enter a number ";
    cin >> credit_info;
    // find length
    credit = credit_info; // restore credit value for further use
    do {
        length++;
        credit_info = credit_info / 10;
    } while (credit_info > 0); // Get's the length of integer

    for (int i = 0; i < length; i++) {
        remaind = credit % 10;
        credit = credit / 10;       // extracts every digit from the input

        if (i % 2 == 1 && i != 0) {  // Checks the digit on every second place
            remaind = remaind * 2;
        }
        if (remaind > 9) {
            counter = remaind % 10;
            remaind = remaind / 10;
            sum = sum + remaind + counter; // adding individual integers if split
        }
        else {
            sum = sum + remaind; // adding the individual integers
        }
        cout << "___________________________________________" << '\n';

    }

    if (sum % 10 != 0) { // Checkts if the sum of all is equal to 10
        cout << " number is not valid" << '\n';
        cout << "___________________________________________" << '\n';
    }
    else {
        cout << "it is valid" << '\n';
        cout << "___________________________________________" << '\n';
    }

    return 0;
    }
