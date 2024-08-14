# Task-4 
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class ToDoList {
private:
    vector<string> tasks;

public:
    void addTask(const string &task) {
        tasks.push_back(task);
        cout << "Task added successfully!" << endl;
    }

    void deleteTask(int index) {
        if (index < 1 || index > tasks.size()) {
            cout << "Invalid task number!" << endl;
        } else {
            tasks.erase(tasks.begin() + (index - 1));
            cout << "Task deleted successfully!" << endl;
        }
    }

    void viewTasks() const {
        if (tasks.empty()) {
            cout << "No tasks to show!" << endl;
        } else {
            cout << "To-Do List:" << endl;
            for (int i = 0; i < tasks.size(); i++) {
                cout << i + 1 << ". " << tasks[i] << endl;
            }
        }
    }
};

void displayMenu() {
    cout << "\n--- To-Do List Menu ---\n";
    cout << "1. Add Task\n";
    cout << "2. Delete Task\n";
    cout << "3. View Tasks\n";
    cout << "4. Exit\n";
    cout << "Choose an option: ";
}

int main() {
    ToDoList todoList;
    int choice;

    do {
        displayMenu();
        cin >> choice;
        cin.ignore(); // to clear the newline character from the buffer

        switch (choice) {
            case 1: {
                cout << "Enter the task description: ";
                string task;
                getline(cin, task);
                todoList.addTask(task);
                break;
            }
            case 2: {
                cout << "Enter the task number to delete: ";
                int taskNumber;
                cin >> taskNumber;
                todoList.deleteTask(taskNumber);
                break;
            }
            case 3: {
                todoList.viewTasks();
                break;
            }
            case 4: {
                cout << "Exiting program. Goodbye!" << endl;
                break;
            }
            default: {
                cout << "Invalid option! Please choose again." << endl;
                break;
            }
        }
    } while (choice != 4);

    return 0;
}
