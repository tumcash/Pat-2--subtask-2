#include <iostream>
#include <map>
#include <string>

using namespace std;

// Morse code dictionary
map<char, string> morseCode = {
    {'A', ".-"}, {'B', "-..."}, {'C', "-.-."}, {'D', "-.."},
    {'E', "."},  {'F', "..-."}, {'G', "--."},  {'H', "...."},
    {'I', ".."}, {'J', ".---"}, {'K', "-.-"},  {'L', ".-.."},
    {'M', "--"}, {'N', "-."},   {'O', "---"},  {'P', ".--."},
    {'Q', "--.-"},{'R', ".-."}, {'S', "..."},  {'T', "-"},
    {'U', "..-"}, {'V', "...-"}, {'W', ".--"}, {'X', "-..-"},
    {'Y', "-.--"}, {'Z', "--.."},
    {'0', "-----"}, {'1', ".----"}, {'2', "..---"}, {'3', "...--"},
    {'4', "....-"}, {'5', "....."}, {'6', "-...."}, {'7', "--..."},
    {'8', "---.."}, {'9', "----."},
    {' ', " "} // Space between words
};

int main() {
    string message;
    cout << "Enter a short message in English (A-Z, 0-9, space): ";
    getline(cin, message);

    cout << "\nMorse Code:\n";

    for (char c : message) {
        c = toupper(c); // Convert to uppercase
        if (morseCode.find(c) != morseCode.end()) {
            string code = morseCode[c];
            for (char symbol : code) {
                if (symbol == '.') {
                    cout << static_cast<char>(46); // Dot
                } else if (symbol == '-') {
                    cout << static_cast<char>(45); // Dash
                } else if (symbol == ' ') {
                    cout << "   "; // Space between words
                }
            }
            cout << " "; // Space between letters
        } else {
            cout << "? "; // Unknown character
        }
    }

    cout << endl;
    return 0;
}
