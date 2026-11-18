# -OOPS-EXP.6
C++ program to implement single and multilevel inheritance for a university management scenario ( person -- student -- graduation student )

#include <iostream>
#include <string>
using namespace std;

class Person {
protected:
    string name;
    int age;

public:
    void getPerson() {
        cout << "Enter Name: ";
        cin >> ws; // clear input buffer
        getline(cin, name);
        cout << "Enter Age: ";
        cin >> age;
    }
    void displayPerson() {
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
    }
};

class Student : public Person {
protected:
    int roll;
    string course;

public:
    void getStudent() {
        getPerson();
        cout << "Enter Roll Number: ";
        cin >> roll;
        cout << "Enter Course: ";
        cin >> ws;
        getline(cin, course);
    }
    void displayStudent() {
        displayPerson();
        cout << "Roll Number: " << roll << endl;
        cout << "Course: " << course << endl;
    }
};
// Derived Class 2 (Multilevel Inheritance: Person -> Student -> GraduateStudent)
class GraduateStudent : public Student {
private:
    string researchTopic;

public:
    void getGraduate() {
        getStudent(); // Calls Student input which calls Person input
        cout << "Enter Research Topic: ";
        cin >> ws;
        getline(cin, researchTopic);
    }
    void displayGraduate() {
        displayStudent(); // Calls Student display which calls Person display
        cout << "Research Topic: " << researchTopic << endl;
    }
};

int main() {
    int choice;
    cout << "=== University Management System ===" << endl;
    cout << "1. Regular Student (Single Inheritance Demo)" << endl;
    cout << "2. Graduate Student (Multilevel Inheritance Demo)" << endl;
    cout << "Enter your choice (1 or 2): ";
    cin >> choice;

    if (choice == 1) {
        Student s;
        cout << "\n--- Enter Student Details ---\n";
        s.getStudent();
        cout << "\n--- Student Details ---\n";
        s.displayStudent();
    } 
    else if (choice == 2) {
        GraduateStudent g;
        cout << "\n--- Enter Graduate Student Details ---\n";
        g.getGraduate();
        cout << "\n--- Graduate Student Details ---\n";
        g.displayGraduate();
    } 
    else {
        cout << "Invalid choice!" << endl;
    }
    return 0;
}
