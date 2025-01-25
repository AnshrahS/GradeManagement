Introduction:
The student management system is an integrated solution for managing student information, storing data and generating relevant files. This program demonstrates structured programing and dynamic memory allocation functionalities in the systems. This student program manages data over different sections and subjects. It enables data entry, modification and retrieval of data.This management system has adapted its features from flex.

Thought Process:
  This program initially was designed to handle a single subject entry with only a single file generation and basic usage of pointers(to point to arrays).It focused on basic marks entry ,gpa calculation and saving data.However, as we progressed with the course we added:
    1.	Multiple subjects.
    2.	File generation
    3.	Error handling for inputs
    4.	Access according to user
    5.	Use of DMA(pointers)
Features:
Teacher Interface:
    1.	Enter, view, and modify marks and attendance.
    2.	Add remarks and generate detailed class reports.
    3.	Identify students with the highest GPA.
Student Interface:
    1.	View marks, attendance, and report cards.
    2.	Understand marks weightage for each subject.
Parent Interface:
    1.	Access GPA, attendance, and performance summary for their child.
Reports:
    1.	Generate textual and class-specific reports.
Dynamic Allocation:
    1.	The system dynamically adjusts based on the number of students and sections.
Description of Modules:
    1. Main Menu Module
Purpose:
Serves as the entry point  directs users (teachers, students, and parents) to their respective interfaces.
Functionality:
•	Displays the primary navigation options:
    1.	Teacher Menu
    2.	Student Menu
    3.	Parent Menu
    4.	Exit
    •	Accepts user input to select the appropriate menu.
    •	Includes input validation to ensure valid choices.
    •	Calls corresponding functions based on the selected option.
Module Name:
•	void showMainMenu(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS)
Guides users to the respective modules or exits the application.
________________________________________
2. Teacher Menu Module
Purpose:
Allows teachers to manage (add data, modify data and view data)student data, including marks, attendance, and reports.
Functionality:
•	Provides the following options for teachers:
1.	Enter marks and attendance for students.
2.	Modify marks or attendance records.
3.	View marks, attendance, and GPA details for individual students or sections.
4.	Generate reports for specific classes or sections.
5.	Add remarks for students.
6.	View the highest GPA within a section or across all sections.
•	Implement error handling to manage invalid inputs, ensuring data accuracy.
Module Name:
•	void teacherMenu(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS)
•	void enterMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void enterAttendance(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void modifyMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void viewHighestGPA(Student ***students, int section, int NUM_STUDENTS, int subIndex)
________________________________________
3. Student Menu Module
Purpose:
Allows students to access their academic performance details, including marks, GPA, and attendance.
Functionality:
•	Provides the following options for students:
1.	View individual marks for midterm, classwork, and final exams.
2.	View attendance records for specific subjects.
3.	Generate a detailed report card displaying subject-wise GPA and attendance.
4.	Understand the weightage of each assessment component (midterm, classwork, final exam) toward their final grade.
•	Ensures secure access by prompting students to input their section and student index.
Module Name:
•	void studentMenu(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS)
•	void generateReportCard(Student ***students, int section, int studentIndex)
•	void viewMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void viewAttendance(Student ***students, int section, int NUM_STUDENTS, int subIndex)
________________________________________
4. Parent Menu Module
Purpose:
Provides parents with access to their child's academic performance data.
Functionality:
•	Offers options to view:
1.	Marks and attendance of their child.
2.	GPA and performance summary.
3.	A complete academic report, including remarks from teachers.
•	Simplifies navigation for parents with a concise and user-friendly interface.
Module Name:
•	void parentMenu(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS)
•	void viewMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void viewAttendance(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void generateReportCard(Student ***students, int section, int studentIndex)
________________________________________
5. GPA and Report Management Module
Purpose:
Handle GPA calculation, identifies high achievers, and generates detailed reports.
Functionality:
•	Calculates GPA for each student using the pre-defined formula: 
•	(We have pre-defined the formulae as per FAST curriculum)
GPA=0.3×Midterm Marks+0.2×Classwork Marks+0.5×Final Exam MarksGPA=0.3×Midterm Marks+0.2×Classwork Marks+0.5×Final Exam Marks.
•	Identifies the highest GPA in a section and across all sections. Similar to award distribution ceremony at FAST
•	Generate textual reports for individual students and entire classes. Enables the teacher to have an idea about the section they teach at a glance.

Module Name:
•	void viewHighestGPA(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void viewHighestGPAAllSections(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS, int subIndex)
•	void generateTextReport(Student ***students, int section, int studentIndex)
•	void generateClassfile(Student ***students, int section, int NUM_STUDENTS, int subIndex)
________________________________________
6. Data Input and Modification Module
Purpose:
Allows teachers to input and update student data such as marks, attendance, and remarks.
Functionality:
•	Enables entering marks for all or specific students.
•	Updates attendance records and ensures inputs are within valid ranges (e.g., 0–100% does a validation to check if the input is correct or not).
•	Adds remarks to student profiles for specific subjects(acts as a private comment to student).
•	Modifies existing data with a error-checking mechanism.
Module Name:
•	void enterMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void modifyMarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void enterAttendance(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void modifyAttendance(Student ***students, int section, int NUM_STUDENTS, int subIndex)
•	void enterRemarks(Student ***students, int section, int NUM_STUDENTS, int subIndex)
________________________________________
7. Cleanup and Memory Management Module
Purpose:
Ensures efficient use of resources by properly deallocating dynamically allocated memory or else if we do not free the memory it will cause performance issues.
Functionality:
•	Frees memory allocated for students, sections, and GPA arrays.
•	Prevents memory leaks by ensuring all pointers are properly deallocated before exiting the program.
Module Name:
•	void cleanup(Student ***students, int NUM_SECTIONS, int NUM_STUDENTS)
________________________________________
8. File Handling Module
Purpose:
Facilitates persistence of data and generation of archival reports.Acts as report cards given to kids to have an idea about their progress. 
Functionality:
•	Writes detailed performance reports for individual students or entire classes to text files.
•	Ensures proper file handling with error checking during read/write operations(checks whether the files is NULL).
Module Name:
•	void generateTextReport(Student ***students, int section, int studentIndex)
•	void generateClassfile(Student ***students, int section, int NUM_STUDENTS, int subIndex)

Error Handling:
1. Main Menu Module
•	Invalid Menu Option Handling:
Ensures the user enters a valid choice between 1–4 in the main menu.
•	Input Type Validation:
Handles non-integer inputs by clearing the input buffer if scanf fails.

________________________________________
2. Teacher Menu Module
•	Invalid Section Number Handling:
Ensures the user enters a valid section number within the range (1–NUM_SECTIONS).
•	Invalid Subject ID Handling:
Ensures the entered subject ID is within the range (0–NUM_SUBJECTS - 1).
•	Invalid Menu Option Handling:
Ensures the user selects valid choices for teacher-specific operations.
________________________________________
3. Student Menu Module
•	Invalid Section Number Handling:
Validates that the section number is within the range (1–NUM_SECTIONS).
•	Invalid Student Index Handling:
Ensures the student index is within the range (0–NUM_STUDENTS - 1).
•	Invalid Subject ID Handling:
Checks that the subject ID is between (0 and NUM_SUBJECTS – 1).
•	Invalid Menu Option Handling:
Validates user inputs for student-specific menu options.
4. Parent Menu Module
•	Invalid Section Number Handling:
Ensures the section number entered is valid (1–NUM_SECTIONS).
•	Invalid Student Index Handling:
Ensures the student index falls within the valid range (0–NUM_STUDENTS - 1).
•	Invalid Subject ID Handling:
Validates the subject ID against the range (0–NUM_SUBJECTS - 1).
•	Invalid Menu Option Handling:
Handles invalid inputs for parent-specific operations.
5. Marks and Attendance Module
•	Marks Range Validation:
Ensures midterm, classwork, and final exam marks are within the range (0–100).
•	Attendance Range Validation:
Validates that attendance is a percentage between 0 and 100.
•	Invalid Student Index Handling:
Ensures the student index is within bounds (0–NUM_STUDENTS - 1).
•	Invalid Input for Bulk Data Entry:
Ensures marks and attendance files are correctly formatted.
6. GPA and Report Management Module
•	File Opening Error Handling:
Checks if files open before reading or writing.
•	Invalid Subject ID Handling:
Validates the subject ID for GPA calculations and report generation.
________________________________________
7. Cleanup and Memory Management Module
•	Memory Allocation Error Handling:
Verifies that all calls to malloc succeed and exits if allocation fails.
8. General Validation
•	Default Case Handling in Switch Statements:
Catches invalid menu options for all menus.
•	Input Buffer Clearance:
Handles leftover characters or invalid inputs during scanf.
Conclusion:
The Student Management System, which was originally a simple single-subject GPA tracker, has now become a complex, multi-functional system that can efficiently handle all academic data for multiple subjects, sections, and users (teachers, students, and parents). The system ensures high-level performance of processing the student's grades, attendance, and reports and the usage of the dynamic allocation memory methods and user-defined structures for data. 
