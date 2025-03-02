# CodeAlpha_Task-2
#include<iostream>
#include<fstream>
#include<string>
using namespace std;

void registerUser() {
	
    string username, password;
    cout << "Enter Username: ";
    cin >> username;
    cout << "Enter Password: ";
    cin >> password;

    ofstream file((username + ".txt").c_str()); // Fixed line 12 error by converting string to const char*
    if (file.is_open()) {
        file << username << endl;
        file << password << endl;
        file.close();
        cout << "Registration Successful!" << endl;
    } else {
        cout << "Error in creating file!" << endl;
    }
}

bool loginUser() {
    string username, password, uname, pass;
    cout << "Enter Username: ";
    cin >> username;
    cout << "Enter Password: ";
    cin >> password;

    ifstream file((username + ".txt").c_str()); // Fixed file opening by converting string to const char*
    if (file.is_open()) {
        getline(file, uname);
        getline(file, pass);
        file.close();

        if (username == uname && password == pass) {
            cout << "Login Successful!" << endl;
            return true;
        } else {
            cout << "Invalid Username or Password!" << endl;
            return false;
        }
    } else {
        cout << "User not found!" << endl;
        return false;
    }
}

int main() {
    int choice;
    while (true) {
        cout << "\n1. Register" << endl;
        cout << "2. Login" << endl;
        cout << "3. Exit" << endl;
        cout << "Enter Your Choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            registerUser();
            break;
        case 2:
            loginUser();
            break;
        case 3:
            cout << "Exiting..." << endl;
            return 0;
        default:
            cout << "Invalid Choice! Please try again." << endl;
        }
}
}
