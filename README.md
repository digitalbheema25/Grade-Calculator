# Grade-Calculator
This program calculates grades for multiple students
# Student Grade Calculator
# Name: Sindhu g e
# Description: This program calculates grades for multiple students,
# provides comments, stores results, and shows statistics.

students = []

# Function to calculate grade and comment
def calculate_grade(mark):
    if mark >= 90:
        return "A", "Excellent performance"
    elif mark >= 75:
        return "B", "Very good job"
    elif mark >= 60:
        return "C", "Good effort"
    elif mark >= 40:
        return "D", "Needs improvement"
    else:
        return "F", "Fail - Work harder"

# Input number of students with validation
while True:
    try:
        total_students = int(input("Enter number of students: "))
        if total_students > 0:
            break
        else:
            print("Number must be greater than zero.")
    except ValueError:
        print("Invalid input! Please enter a number.")

# Collect student data
for i in range(total_students):
    print(f"\nStudent {i + 1}")

    name = input("Enter student name: ")

    while True:
        try:
            mark = float(input("Enter marks (0 - 100): "))
            if 0 <= mark <= 100:
                break
            else:
                print("Marks must be between 0 and 100.")
        except ValueError:
            print("Invalid input! Enter numeric marks.")

    grade, comment = calculate_grade(mark)

    students.append({
        "name": name,
        "marks": mark,
        "grade": grade,
        "comment": comment
    })

# Statistics
marks_list = [s["marks"] for s in students]
average = sum(marks_list) / len(marks_list)
highest = max(marks_list)
lowest = min(marks_list)

# Display results in formatted table
print("\n--- Student Grade Report ---")
print("{:<15} {:<10} {:<10} {:<25}".format("Name", "Marks", "Grade", "Comment"))
print("-" * 60)

for s in students:
    print("{:<15} {:<10} {:<10} {:<25}".format(
        s["name"], s["marks"], s["grade"], s["comment"]
    ))

print("\n--- Statistics ---")
print(f"Average Marks: {average:.2f}")
print(f"Highest Marks: {highest}")
print(f"Lowest Marks : {lowest}")
