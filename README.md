# password-complexity-checker-by-PYTHON

This script evaluates a password based on several criteria such as length, the presence of uppercase and lowercase letters, numbers, and special characters. It assigns a score based on these criteria and provides feedback on the strength of the password.

```

import re

def password_complexity_checker(password):
    # Criteria for checking password complexity
    length_criteria = len(password) >= 8
    uppercase_criteria = re.search(r'[A-Z]', password) is not None
    lowercase_criteria = re.search(r'[a-z]', password) is not None
    digit_criteria = re.search(r'[0-9]', password) is not None
    special_char_criteria = re.search(r'[\W_]', password) is not None

    # Calculate the complexity score
    score = sum([length_criteria, uppercase_criteria, lowercase_criteria, digit_criteria, special_char_criteria])

    # Provide feedback based on the score
    if score == 5:
        complexity = "Very Strong"
    elif score == 4:
        complexity = "Strong"
    elif score == 3:
        complexity = "Moderate"
    else:
        complexity = "Weak"

    feedback = []
    if not length_criteria:
        feedback.append("Password should be at least 8 characters long.")
    if not uppercase_criteria:
        feedback.append("Password should contain at least one uppercase letter.")
    if not lowercase_criteria:
        feedback.append("Password should contain at least one lowercase letter.")
    if not digit_criteria:
        feedback.append("Password should contain at least one digit.")
    if not special_char_criteria:
        feedback.append("Password should contain at least one special character.")

    return complexity, feedback

# Example usage
password = input("Enter a password to check its complexity: ")
complexity, feedback = password_complexity_checker(password)

print(f"Password Complexity: {complexity}")
if feedback:
    print("Feedback:")
    for item in feedback:
        print(f"- {item}")

```

