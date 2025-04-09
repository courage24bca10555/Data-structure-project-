#include <iostream>
#include <vector>
#include <string>
struct Student {
int rollNumber;
std::string name;
int age;
char grade;
};
void addStudent(std::vector<Student>& students) {
  Student newStudent;
    std::cout << "Enter Roll Number: ";
    std::cin >> newStudent.rollNumber;
    std::cin.ignore(); // To ignore the newline character left by std::cin
    std::cout << "Enter Name: ";
    std::getline(std::cin, newStudent.name);
    std::cout << "Enter Age: ";
    std::cin >> newStudent.age;
    std::cout << "Enter Grade: ";
    std::cin >> newStudent.grade;
    students.push_back(newStudent);
    std::cout << "Student added successfully.\n";
    }
void viewStudents(const std::vector<Student>& students) {
    if (students.empty()) {
        std::cout << "No records found.\n";
        return;
        }
    for (const auto& student : students) {
        std::cout << "Roll Number: " << student.rollNumber
<< ", Name: " << student.name
   << ", Age: " << student.age
 << ", Grade: " << student.grade << '\n';
}
}
void updateStudent(std::vector<Student>& students) {
    int rollNumber;
    std::cout << "Enter Roll Number of student to update: ";
    std::cin >> rollNumber;
    for (auto& student : students) {
        if (student.rollNumber == rollNumber) {
            std::cout << "Enter new Name: ";
            std::cin.ignore();
            std::getline(std::cin, student.name);
            std::cout << "Enter new Age: ";
            std::cin >> student.age;
            std::cout << "Enter new Grade: ";
            std::cin >> student.grade;
            std::cout << "Student record updated successfully.\n";
            return;
        }
    }
    std::cout << "Student with Roll Number " << rollNumber << " not found.\n";
}
void deleteStudent(std::vector<Student>& students) {
    int rollNumber;
    std::cout << "Enter Roll Number of student to delete: ";
    std::cin >> rollNumber;
    for (auto it = students.begin(); it != students.end(); ++it) {
        if (it->rollNumber == rollNumber) {
            students.erase(it);
            std::cout << "Student record deleted successfully.\n";
            return;
        }
    }
    std::cout << "Student with Roll Number " << rollNumber << " not found.\n";
}
int main() {
    std::vector<Student> students;
    int choice;
    do {
        std::cout << "\nStudent Record Management System\n";
        std::cout << "1. Add Student\n";
        std::cout << "2. View Students\n";
        std::cout << "3. Update Student\n";
        std::cout << "4. Delete Student\n";
        std::cout << "5. Exit\n";
        std::cout << "Enter your choice: ";
        std::cin >> choice;
        switch (choice) {
            case 1:
                addStudent(students);
                break;
            case 2:
                viewStudents(students);
                break;
            case 3:
                updateStudent(students);
                break;
            case 4:
                deleteStudent(students);
                break;
            case 5:
                std::cout << "Exiting the program.\n";
                break;
            default:
                std::cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 5);
    return 0;
}



