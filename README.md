# ViLearnX-Task2
    class Student:
      def __init__(self, name):
        self.name = name
        self.grades = {}
    
    def add_grade(self, subject, grade):
        if subject in self.grades:
            self.grades[subject].append(grade)
        else:
            self.grades[subject] = [grade]

    def calculate_average(self):
        total = 0
        count = 0
        for subject in self.grades:
            subject_average = sum(self.grades[subject]) / len(self.grades[subject])
            total += subject_average
            count += 1
        return total / count if count > 0 else 0
    
    def get_letter_grade(self, average):
        if average >= 90:
            return 'A'
        elif average >= 80:
            return 'B'
        elif average >= 70:
            return 'C'
        elif average >= 60:
            return 'D'
        else:
            return 'F'
    
    def display_report(self):
        print(f"\nReport for {self.name}:")
        for subject in self.grades:
            subject_average = sum(self.grades[subject]) / len(self.grades[subject])
            letter_grade = self.get_letter_grade(subject_average)
            print(f"{subject}: Average = {subject_average:.2f}, Letter Grade = {letter_grade}")
        overall_average = self.calculate_average()
        overall_letter = self.get_letter_grade(overall_average)
        print(f"\nOverall Average: {overall_average:.2f}")
        print(f"Overall Letter Grade: {overall_letter}\n")


    def main():
        print("Welcome to the Student Grade Management System")
        student_name = input("Enter the student's name: ")
         student = Student(student_name)

    while True:
        print("\nMenu:")
        print("1. Add grade")
        print("2. Display report")
        print("3. Exit")
        choice = input("Choose an option: ")

        if choice == '1':
            subject = input("Enter the subject: ")
            grade = float(input("Enter the grade: "))
            student.add_grade(subject, grade)
        elif choice == '2':
            student.display_report()
        elif choice == '3':
            print("Exiting the program. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

    if __name__ == "__main__":
        main()
