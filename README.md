def get_ordinal(x):
    if x == 1:
        return "st"
    elif x == 2:
        return "nd"
    elif x == 3:
        return "rd"
    else:
        return "th"
def gpa(score):
    score = float(score)
    if score >= 90:
        return 4.3
    elif score >= 85:
        return 4.0
    elif score >= 80:
        return 3.7
    elif score >= 77:
        return 3.3
    elif score >= 70:
        return 2.7
    elif score >= 67:
        return 2.3
    elif score >= 63:
        return 2.0
    elif score >= 60:
        return 1.7
    else:
        return 0.0

def main():
    score = 0
    credit = 0
    total_score = 0
    total_credit = 0
    total_gpa = 0
    subject = 1
    transcript = []
    print("If you want to stop, please enter -1 in your score.")
    while True:
        suffix = get_ordinal(subject)
        print(f"The {subject}{suffix} subject")
        score = input("Enter your score: ")
        if score == '-1':
            break
        credit = input("Enter your credit: ")
        gpa_point = gpa(score)
        total_score += float(score) * float(credit)
        total_credit += float(credit)
        total_gpa += float(gpa_point) * float(credit)
        record = f"Subject{subject}:Score{score},Credit{credit}->GPA{gpa_point}"
        transcript.append(record)
        real_gpa = total_gpa/total_credit
        subject += 1

    if total_credit > 0:
        real_score = total_score / total_credit
        print("----------------------------------------")
        print(f"Your credit is {total_credit:.2f} credit.")
        print(f"Your score is {real_score}.")
        print(f"Your subject number is {subject-1}")
        print(f"Your gpa number is {real_gpa}")
        print("----------------成績單-------------------")
        for line in transcript:
            print(line)
        print("---------------------------------------")
    else:
        print("No score is entered.")
main()
