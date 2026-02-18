# c-18Feb

#create a student class with attributes : name , roll no. and marks 
add member functions to input and display student details 
create atleast 3 objects and display their data 
write a c++ code

**output**
<img width="834" height="849" alt="image" src="https://github.com/user-attachments/assets/677807f0-d36c-4c3b-9eb3-3b8ff1d2b439" />
<img width="620" height="448" alt="image" src="https://github.com/user-attachments/assets/49a5d9a5-5319-4fbc-9418-8804068b2c58" />


<img width="498" height="803" alt="image" src="https://github.com/user-attachments/assets/8b618733-53f9-43c1-b59f-bd1e98316de4" />


#question 2
create  a bank account class . Initialize account number and balance using a constructor . Display a message when the destructor is called . Create objects inside a function to observe destructor behaviour

<img width="823" height="817" alt="image" src="https://github.com/user-attachments/assets/2bc71115-4f0d-4838-882a-987cb1fd66e0" />

<img width="746" height="442" alt="image" src="https://github.com/user-attachments/assets/768b442f-0cf0-4d21-90e9-2bf89dc5184d" />

#question 3
Create an Employee class. 

Make salary private.

Provide getter and setter functions.

Add validation: salary cannot be negative.

<img width="841" height="812" alt="image" src="https://github.com/user-attachments/assets/907a7557-5e98-410a-a19d-e51cd280dfb7" />
<img width="729" height="406" alt="image" src="https://github.com/user-attachments/assets/3a2695db-1aba-4632-ad97-74477559f66f" />
**output**
<img width="519" height="278" alt="image" src="https://github.com/user-attachments/assets/c1ac6977-59af-4bee-8d4d-e711c45ae949" />

#question 4
Create a class Calculator

Overload a function add() for:

int

double

three parameters


<img width="626" height="823" alt="image" src="https://github.com/user-attachments/assets/2df798e7-c606-4e39-9c8e-c866b8340607" />
**output**
<img width="369" height="216" alt="image" src="https://github.com/user-attachments/assets/9d7f97fd-f30d-489b-a3b5-a3b53c33c7ac" />

#question 5
Create a struct Subject { string name; int marks; }.
Create a class Student with:

private: int roll; string name; Subject* subjects; int n;

constructor allocates dynamic memory for n subjects

member functions: input(), display(), total(), grade()

Store N students using pointer to object array, find topper, and free all memory properly.

**code**
<img width="756" height="813" alt="image" src="https://github.com/user-attachments/assets/49814493-cc34-47e1-b714-7209af37f3ed" />
<img width="786" height="810" alt="image" src="https://github.com/user-attachments/assets/98864d72-49e9-4869-97f7-3038a1839fa8" />
<img width="866" height="810" alt="image" src="https://github.com/user-attachments/assets/e3695ff5-6ff3-4336-b5ab-5aa96dce1257" />

**output**
<img width="499" height="818" alt="image" src="https://github.com/user-attachments/assets/6032dcde-d8c9-4abe-b379-d1e37ae9b26b" />

#question 6
Create a struct Node containing:

Patient data (id, name, severity)

Node* next

Create a class PatientQueue implementing:

enqueue (based on severity priority)

dequeue

display
Use dynamic memory (new/delete) and demonstrate queue operations.

#code
<img width="667" height="826" alt="image" src="https://github.com/user-attachments/assets/eca2b26a-04ff-4c2c-9682-6924dddb4462" />
<img width="846" height="819" alt="image" src="https://github.com/user-attachments/assets/9bdb7721-f9cd-425a-b495-cf1d4a5bdc9e" />
<img width="841" height="812" alt="image" src="https://github.com/user-attachments/assets/92b07110-2f22-47c2-a92b-134aa678ee33" />
<img width="763" height="538" alt="image" src="https://github.com/user-attachments/assets/6f9ed63e-5730-4869-8c96-8f45948a5d24" />

**output**
<img width="751" height="568" alt="image" src="https://github.com/user-attachments/assets/ab41f2d3-f8df-4065-96bc-b0224e3313e6" />

#question 7
Create a struct BookNode:

int id; string title; string author; bool issued;

BookNode* next

Create a class Library with:

BookNode* head

addBook(), issueBook(id), returnBook(id), searchBook(title), displayAll()

Use pointers to traverse linked list and manage memory safely.


**output**
#include <iostream>
#include <string>
using namespace std;

// Structure for Book Node
struct BookNode {
    int id;
    string title;
    string author;
    bool issued;
    BookNode* next;
};

class Library {
private:
    BookNode* head;

public:
    // Constructor
    Library() {
        head = nullptr;
    }

    // Destructor (free memory safely)
    ~Library() {
        BookNode* temp;
        while (head != nullptr) {
            temp = head;
            head = head->next;
            delete temp;
        }
        cout << "All book records deleted. Memory freed.\n";
    }

    // Add new book
    void addBook(int id, string title, string author) {
        BookNode* newBook = new BookNode;
        newBook->id = id;
        newBook->title = title;
        newBook->author = author;
        newBook->issued = false;
        newBook->next = nullptr;

        if (head == nullptr) {
            head = newBook;
        } else {
            BookNode* temp = head;
            while (temp->next != nullptr) {
                temp = temp->next;
            }
            temp->next = newBook;
        }

        cout << "Book added successfully.\n";
    }

    // Issue book by ID
    void issueBook(int id) {
        BookNode* temp = head;

        while (temp != nullptr) {
            if (temp->id == id) {
                if (!temp->issued) {
                    temp->issued = true;
                    cout << "Book issued successfully.\n";
                } else {
                    cout << "Book already issued.\n";
                }
                return;
            }
            temp = temp->next;
        }

        cout << "Book not found.\n";
    }

    // Return book by ID
    void returnBook(int id) {
        BookNode* temp = head;

        while (temp != nullptr) {
            if (temp->id == id) {
                if (temp->issued) {
                    temp->issued = false;
                    cout << "Book returned successfully.\n";
                } else {
                    cout << "Book was not issued.\n";
                }
                return;
            }
            temp = temp->next;
        }

        cout << "Book not found.\n";
    }

    // Search book by title
    void searchBook(string title) {
        BookNode* temp = head;

        while (temp != nullptr) {
            if (temp->title == title) {
                cout << "\nBook Found:\n";
                cout << "ID: " << temp->id
                     << "\nTitle: " << temp->title
                     << "\nAuthor: " << temp->author
                     << "\nStatus: "
                     << (temp->issued ? "Issued" : "Available")
                     << endl;
                return;
            }
            temp = temp->next;
        }

        cout << "Book not found.\n";
    }

    // Display all books
    void displayAll() {
        if (head == nullptr) {
            cout << "Library is empty.\n";
            return;
        }

        BookNode* temp = head;
        cout << "\nLibrary Books:\n";

        while (temp != nullptr) {
            cout << "ID: " << temp->id
                 << ", Title: " << temp->title
                 << ", Author: " << temp->author
                 << ", Status: "
                 << (temp->issued ? "Issued" : "Available")
                 << endl;

            temp = temp->next;
        }
    }
};

int main() {
    Library lib;

    // Adding books
    lib.addBook(1, "C++ Basics", "Bjarne Stroustrup");
    lib.addBook(2, "Data Structures", "Mark Allen Weiss");
    lib.addBook(3, "Algorithms", "CLRS");

    lib.displayAll();

    cout << "\nIssuing Book ID 2...\n";
    lib.issueBook(2);

    cout << "\nSearching for 'Algorithms'...\n";
    lib.searchBook("Algorithms");

    cout << "\nReturning Book ID 2...\n";
    lib.returnBook(2);

    lib.displayAll();

    return 0;
}

<img width="798" height="753" alt="image" src="https://github.com/user-attachments/assets/f7f59029-9cff-4278-879b-07fd144b21d1" />

#question 8
Create a struct Transaction:

string type; double amount; string date; Transaction* next

Create a class BankAccount:

private: accountNo, holderName, balance, Transaction* historyHead

deposit(), withdraw(), showHistory(), showBalance()

Store multiple accounts using BankAccount* array pointer and search account by number.

**output**
#include <iostream>
#include <string>
using namespace std;

// Transaction node
struct Transaction {
    string type;      // "Deposit" or "Withdraw"
    double amount;
    string date;
    Transaction* next;
};

class BankAccount {
private:
    int accountNo;
    string holderName;
    double balance;
    Transaction* historyHead;

public:
    // Constructor
    BankAccount(int accNo, string name, double bal = 0) {
        accountNo = accNo;
        holderName = name;
        balance = bal;
        historyHead = nullptr;
    }

    // Destructor
    ~BankAccount() {
        // Free transaction history
        Transaction* temp;
        while (historyHead != nullptr) {
            temp = historyHead;
            historyHead = historyHead->next;
            delete temp;
        }
    }

    // Deposit function
    void deposit(double amt, string date) {
        if (amt <= 0) {
            cout << "Deposit amount must be positive.\n";
            return;
        }

        balance += amt;

        // Record transaction
        Transaction* t = new Transaction;
        t->type = "Deposit";
        t->amount = amt;
        t->date = date;
        t->next = historyHead;
        historyHead = t;

        cout << "Deposit successful.\n";
    }

    // Withdraw function
    void withdraw(double amt, string date) {
        if (amt <= 0) {
            cout << "Withdrawal amount must be positive.\n";
            return;
        }
        if (amt > balance) {
            cout << "Insufficient balance.\n";
            return;
        }

        balance -= amt;

        // Record transaction
        Transaction* t = new Transaction;
        t->type = "Withdraw";
        t->amount = amt;
        t->date = date;
        t->next = historyHead;
        historyHead = t;

        cout << "Withdrawal successful.\n";
    }

    // Show current balance
    void showBalance() {
        cout << "Account No: " << accountNo
             << ", Holder: " << holderName
             << ", Balance: " << balance << endl;
    }

    // Show transaction history
    void showHistory() {
        if (historyHead == nullptr) {
            cout << "No transactions yet.\n";
            return;
        }

        cout << "\nTransaction History for Account " << accountNo << ":\n";
        Transaction* temp = historyHead;
        while (temp != nullptr) {
            cout << temp->date << " | " << temp->type
                 << " | Amount: " << temp->amount << endl;
            temp = temp->next;
        }
    }

    // Getter for account number
    int getAccountNo() {
        return accountNo;
    }
};

int main() {
    int N;
    cout << "Enter number of accounts: ";
    cin >> N;
    cin.ignore();

    // Array of pointers to BankAccount objects
    BankAccount** accounts = new BankAccount*[N];

    // Input account details
    for (int i = 0; i < N; i++) {
        int accNo;
        string name;
        cout << "\nEnter details for account " << i + 1 << ":\n";
        cout << "Account No: ";
        cin >> accNo;
        cin.ignore();
        cout << "Holder Name: ";
        getline(cin, name);

        accounts[i] = new BankAccount(accNo, name);
    }

    // Example operations
    accounts[0]->deposit(1000, "2026-02-18");
    accounts[0]->withdraw(500, "2026-02-19");
    accounts[1]->deposit(2000, "2026-02-20");

    cout << "\nAll account balances:\n";
    for (int i = 0; i < N; i++) {
        accounts[i]->showBalance();
    }

    // Search for an account by number
    int searchAcc;
    cout << "\nEnter account number to search: ";
    cin >> searchAcc;

    BankAccount* found = nullptr;
    for (int i = 0; i < N; i++) {
        if (accounts[i]->getAccountNo() == searchAcc) {
            found = accounts[i];
            break;
        }
    }

    if (found) {
        cout << "Account found:\n";
        found->showBalance();
        found->showHistory();
    } else {
        cout << "Account not found.\n";
    }

    // Free memory
    for (int i = 0; i < N; i++) {
        delete accounts[i];
    }
    delete[] accounts;

    return 0;
}

**out**
<img width="603" height="795" alt="image" src="https://github.com/user-attachments/assets/fd47b8ae-43bd-4d87-b25e-8abf7d37e48c" />

#question 9
reate a struct Course:

courseCode, courseName, credits

Create a class Student:

roll, name

Course* registeredCourses (dynamic)

registerCourses(), dropCourse(code), showCourses(), totalCredits()

Store multiple students using pointers and print list of students registered in a given course.


**code**
#include <iostream>
#include <string>
using namespace std;

// Course structure
struct Course {
    string courseCode;
    string courseName;
    int credits;
};

// Student class
class Student {
private:
    int roll;
    string name;
    Course* registeredCourses;  // Dynamic array
    int numCourses;

public:
    // Constructor
    Student(int r, string n) {
        roll = r;
        name = n;
        registeredCourses = nullptr;
        numCourses = 0;
    }

    // Destructor
    ~Student() {
        delete[] registeredCourses;
    }

    // Register a course
    void registerCourse(Course c) {
        Course* temp = new Course[numCourses + 1];

        // Copy old courses
        for (int i = 0; i < numCourses; i++)
            temp[i] = registeredCourses[i];

        // Add new course
        temp[numCourses] = c;
        numCourses++;

        // Free old array and update pointer
        delete[] registeredCourses;
        registeredCourses = temp;

        cout << "Course " << c.courseCode << " registered for " << name << endl;
    }

    // Drop a course by code
    void dropCourse(string code) {
        int index = -1;
        for (int i = 0; i < numCourses; i++) {
            if (registeredCourses[i].courseCode == code) {
                index = i;
                break;
            }
        }

        if (index == -1) {
            cout << "Course not found.\n";
            return;
        }

        Course* temp = new Course[numCourses - 1];
        for (int i = 0, j = 0; i < numCourses; i++) {
            if (i != index)
                temp[j++] = registeredCourses[i];
        }

        numCourses--;
        delete[] registeredCourses;
        registeredCourses = temp;

        cout << "Course " << code << " dropped for " << name << endl;
    }

    // Show registered courses
    void showCourses() {
        cout << "\nStudent: " << name << " | Roll: " << roll << "\nCourses:\n";
        for (int i = 0; i < numCourses; i++) {
            cout << registeredCourses[i].courseCode << " - "
                 << registeredCourses[i].courseName
                 << " (" << registeredCourses[i].credits << " credits)\n";
        }
        if (numCourses == 0) cout << "No courses registered.\n";
    }

    // Total credits
    int totalCredits() {
        int total = 0;
        for (int i = 0; i < numCourses; i++)
            total += registeredCourses[i].credits;
        return total;
    }

    // Getter for roll
    int getRoll() { return roll; }

    // Getter for name
    string getName() { return name; }

    // Check if registered in a course
    bool isRegisteredIn(string code) {
        for (int i = 0; i < numCourses; i++) {
            if (registeredCourses[i].courseCode == code)
                return true;
        }
        return false;
    }
};

int main() {
    int numStudents = 3;
    Student** students = new Student*[numStudents];

    // Create some students
    students[0] = new Student(101, "Alice");
    students[1] = new Student(102, "Bob");
    students[2] = new Student(103, "Charlie");

    // Create some courses
    Course c1 = {"CS101", "Data Structures", 4};
    Course c2 = {"CS102", "Algorithms", 3};
    Course c3 = {"CS103", "Databases", 3};

    // Register courses
    students[0]->registerCourse(c1);
    students[0]->registerCourse(c2);

    students[1]->registerCourse(c1);
    students[1]->registerCourse(c3);

    students[2]->registerCourse(c2);

    // Display student courses
    for (int i = 0; i < numStudents; i++) {
        students[i]->showCourses();
        cout << "Total Credits: " << students[i]->totalCredits() << endl;
    }

    // Print list of students registered in CS101
    string searchCourse = "CS101";
    cout << "\nStudents registered in " << searchCourse << ":\n";
    for (int i = 0; i < numStudents; i++) {
        if (students[i]->isRegisteredIn(searchCourse))
            cout << students[i]->getName() << " (Roll: " << students[i]->getRoll() << ")\n";
    }

    // Drop a course for Alice
    students[0]->dropCourse("CS102");

    students[0]->showCourses();

    // Free memory
    for (int i = 0; i < numStudents; i++)
        delete students[i];
    delete[] students;

    return 0;
}

<img width="752" height="810" alt="image" src="https://github.com/user-attachments/assets/937c6e4c-4b6e-407e-93db-0e785818894a" />

#question 10
Create a struct DirNode:

string name; bool isFile;

DirNode* child; DirNode* sibling;

Create a class DirectoryTree:

createFolder(path), createFile(path)

list(path)

deleteNode(path)
Implement using pointers (tree navigation) and free memory in destructor.


**code**
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
using namespace std;

// Directory Node
struct DirNode {
    string name;
    bool isFile;
    DirNode* child;    // First child (folder or file)
    DirNode* sibling;  // Next sibling
};

// Directory Tree class
class DirectoryTree {
private:
    DirNode* root;

    // Helper: split path by '/'
    vector<string> splitPath(const string& path) {
        vector<string> parts;
        stringstream ss(path);
        string item;
        while (getline(ss, item, '/')) {
            if (!item.empty()) parts.push_back(item);
        }
        return parts;
    }

    // Helper: find or create folder recursively
    DirNode* findChild(DirNode* parent, const string& name, bool create = false, bool isFile = false) {
        DirNode* prev = nullptr;
        DirNode* temp = parent->child;

        while (temp != nullptr) {
            if (temp->name == name) return temp;
            prev = temp;
            temp = temp->sibling;
        }

        if (create) {
            DirNode* newNode = new DirNode{name, isFile, nullptr, nullptr};
            if (prev == nullptr) parent->child = newNode;
            else prev->sibling = newNode;
            return newNode;
        }

        return nullptr;
    }

    // Helper: navigate to node by path
    DirNode* navigate(const vector<string>& parts) {
        DirNode* curr = root;
        for (auto& p : parts) {
            curr = findChild(curr, p);
            if (!curr) return nullptr;
        }
        return curr;
    }

    // Helper: recursive list
    void listRecursive(DirNode* node, string prefix) {
        if (!node) return;
        cout << prefix << (node->isFile ? "[FILE] " : "[DIR] ") << node->name << endl;
        listRecursive(node->child, prefix + "    ");
        listRecursive(node->sibling, prefix);
    }

    // Helper: delete node recursively
    void deleteNodeRecursive(DirNode* node) {
        if (!node) return;
        deleteNodeRecursive(node->child);
        deleteNodeRecursive(node->sibling);
        delete node;
    }

public:
    // Constructor
    DirectoryTree() {
        root = new DirNode{"/", false, nullptr, nullptr};
    }

    // Destructor
    ~DirectoryTree() {
        deleteNodeRecursive(root);
    }

    // Create folder
    void createFolder(const string& path) {
        auto parts = splitPath(path);
        DirNode* curr = root;

        for (size_t i = 0; i < parts.size(); i++) {
            bool isLast = (i == parts.size() - 1);
            curr = findChild(curr, parts[i], true, false); // folder
        }

        cout << "Folder created: " << path << endl;
    }

    // Create file
    void createFile(const string& path) {
        auto parts = splitPath(path);
        if (parts.empty()) return;

        string fileName = parts.back();
        parts.pop_back();

        DirNode* curr = root;
        for (auto& p : parts) {
            curr = findChild(curr, p, true, false); // intermediate folders
        }

        findChild(curr, fileName, true, true); // create file
        cout << "File created: " << path << endl;
    }

    // List contents of a folder
    void list(const string& path = "/") {
        auto parts = splitPath(path);
        DirNode* node = navigate(parts);
        if (!node) {
            cout << "Path not found: " << path << endl;
            return;
        }

        listRecursive(node->child, ""); // list children only
    }

    // Delete folder or file
    void deleteNode(const string& path) {
        auto parts = splitPath(path);
        if (parts.empty()) {
            cout << "Cannot delete root\n";
            return;
        }

        DirNode* parent = root;
        for (size_t i = 0; i < parts.size() - 1; i++) {
            parent = findChild(parent, parts[i]);
            if (!parent) {
                cout << "Path not found\n";
                return;
            }
        }

        DirNode* prev = nullptr;
        DirNode* curr = parent->child;

        while (curr != nullptr) {
            if (curr->name == parts.back()) break;
            prev = curr;
            curr = curr->sibling;
        }

        if (!curr) {
            cout << "Node not found\n";
            return;
        }

        // Unlink node from list
        if (prev == nullptr) parent->child = curr->sibling;
        else prev->sibling = curr->sibling;

        deleteNodeRecursive(curr);
        cout << "Deleted: " << path << endl;
    }
};

int main() {
    DirectoryTree dt;

    dt.createFolder("/home/user/docs");
    dt.createFolder("/home/user/images");
    dt.createFile("/home/user/docs/file1.txt");
    dt.createFile("/home/user/docs/file2.txt");
    dt.createFile("/home/user/images/pic1.png");

    cout << "\nListing /home/user:\n";
    dt.list("/home/user");

    dt.deleteNode("/home/user/docs/file1.txt");

    cout << "\nAfter deleting file1.txt:\n";
    dt.list("/home/user");

    return 0;
}

<img width="514" height="514" alt="image" src="https://github.com/user-attachments/assets/21da0bb3-2d6f-4bc9-adc4-782957e8def3" />
