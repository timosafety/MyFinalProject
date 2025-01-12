# MyFinalProject
#This is made to made the input of scores and make life stressfree for eduactors in computing and ease their grading system.

def get_scores(subject):
    """Function to get test and exam scores for a subject."""
    while True:
        try:
            test_score = float(input(f"Enter the Test score for {subject} (max 40%): "))
            if test_score < 0 or test_score > 40:
                print("Test score must be between 0 and 40.")
                continue
            exam_score = float(input(f"Enter the Examination score for {subject} (max 60%): "))
            if exam_score < 0 or exam_score > 60:
                print("Examination score must be between 0 and 60.")
                continue
            total_score = test_score + exam_score
            return test_score, exam_score, total_score
        except ValueError:
            print("Invalid input. Please enter numeric values.")


def calculate_grade(total_score):
    """Function to calculate the grade based on total score."""
    if 70 <= total_score <= 100:
        return 'A'
    elif 60 <= total_score < 70:
        return 'B'
    elif 50 <= total_score < 60:
        return 'C'
    elif 45 <= total_score < 50:
        return 'D'
    elif 40 <= total_score < 45:
        return 'E'
    else:
        return 'F'


def main():
    subjects = ["Mathematics", "English", "Science", "History", "Geography"]

    # Initialize lists to store scores
    test_scores = []
    exam_scores = []
    total_scores = []
    grades = []

    print("School Result Sheet")
    print("====================")

    # Get student information
    student_name = input("Enter the name of the student: ")
    student_class = input("Enter the class of the student: ")

    # Loop through each subject to get scores
    for subject in subjects:
        test, exam, total = get_scores(subject)
        test_scores.append(test)
        exam_scores.append(exam)
        total_scores.append(total)
        grades.append(calculate_grade(total))

    # Display the result sheet
    print("====================================")
    print(f"Student Name: {student_name}")
    print(f"Class: {student_class}")
    print("====================================")

    print("\nResult Sheet")
    print("====================================")
    print(f"{'Subject':<15}{'Test Score':<15}{'Exam Score':<15}{'Total Score':<15}{'Grade':<15}")
    print("====================================")

    for i, subject in enumerate(subjects):
        print(f"{subject:<15}{test_scores[i]:<15}{exam_scores[i]:<15}{total_scores[i]:<15}{grades[i]:<15}")




if __name__ == "__main__":
    main()
