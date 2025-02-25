# TASK-1-SUBTASK-3
#include <iostream>
#include <string>
#include <cmath>

using namespace std;

// Function to convert decimal to binary
string decimalToBinary(int decimal) {
    string binary = "";
    
    // Handle case for 0
    if (decimal == 0) {
        return "0";
    }
    
    while (decimal > 0) {
        binary = to_string(decimal % 2) + binary;
        decimal /= 2;
    }
    
    return binary;
}

// Function to convert binary to decimal
int binaryToDecimal(string binary) {
    int decimal = 0;
    int power = 0;
    
    // Traverse the string in reverse
    for (int i = binary.length() - 1; i >= 0; i--) {
        if (binary[i] == '1') {
            decimal += pow(2, power);
        }
        power++;
    }
    
    return decimal;
}

int main() {
    int choice;
    string binary;
    int decimal;
    
    cout << "Welcome to the Decimal-Binary Converter!" << endl;
    cout << "Please choose an option:" << endl;
    cout << "1. Convert Decimal to Binary" << endl;
    cout << "2. Convert Binary to Decimal" << endl;
    cout << "3. Exit" << endl;
    
    while (true) {
        cout << "Enter your choice: ";
        cin >> choice;
        
        if (choice == 1) {
            cout << "Enter a decimal number: ";
            cin >> decimal;
            cout << "Binary representation: " << decimalToBinary(decimal) << endl;
        }
        else if (choice == 2) {
            cout << "Enter a binary number: ";
            cin >> binary;
            
            // Ensure the binary number is valid (contains only 1's and 0's)
            bool isValid = true;
            for (char c : binary) {
                if (c != '0' && c != '1') {
                    isValid = false;
                    break;
                }
            }
            
            if (isValid) {
                cout << "Decimal representation: " << binaryToDecimal(binary) << endl;
            } else {
                cout << "Invalid binary number!" << endl;
            }
        }
        else if (choice == 3) {
            cout << "Exiting program. Goodbye!" << endl;
            break;
        }
        else {
            cout << "Invalid choice. Please try again." << endl;
        }
    }
    
    return 0;
}
