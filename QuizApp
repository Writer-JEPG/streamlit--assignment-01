
import streamlit as st

# --------------------------------------------------
# PAGE CONFIGURATION
# --------------------------------------------------
st.set_page_config(
    page_title="Python Quiz App",
    page_icon="🧠",
    layout="centered"
)

# --------------------------------------------------
# TITLE AND INTRODUCTION
# --------------------------------------------------
st.title("🧠 Python Knowledge Quiz")
st.subheader("Test your knowledge of Python programming!")

st.markdown("""
### Welcome to the Quiz!

Answer the following **five questions** and test your Python knowledge.

**Instructions:**
- Select one answer for each question.
- Answer all five questions.
- Click the Submit button to see your final score.
- Each correct answer gives you 1 point.
""")

st.info("You have 5 questions. The maximum score is 5 points.")

st.markdown("---")

# --------------------------------------------------
# QUIZ QUESTIONS
# --------------------------------------------------

questions = [
    {
        "question": "1. Which keyword is used to define a function in Python?",
        "options": ["function", "def", "define", "fun"],
        "answer": "def"
    },
    {
        "question": "2. Which data type is used to store True or False?",
        "options": ["String", "Integer", "Boolean", "Float"],
        "answer": "Boolean"
    },
    {
        "question": "3. Which symbol is used for comments in Python?",
        "options": ["//", "#", "/* */", "--"],
        "answer": "#"
    },
    {
        "question": "4. Which function displays output in Python?",
        "options": ["input()", "print()", "display()", "show()"],
        "answer": "print()"
    },
    {
        "question": "5. Which of the following is a Python list?",
        "options": [
            "(1, 2, 3)",
            "{1, 2, 3}",
            "[1, 2, 3]",
            "<1, 2, 3>"
        ],
        "answer": "[1, 2, 3]"
    }
]

# --------------------------------------------------
# USER INFORMATION WIDGET
# --------------------------------------------------

name = st.text_input("Enter your name:")

level = st.selectbox(
    "Select your Python experience:",
    ["Beginner", "Intermediate", "Advanced"]
)

st.markdown("---")
st.markdown("### Answer the Questions")

# --------------------------------------------------
# RADIO BUTTONS
# --------------------------------------------------

user_answers = []

for i, q in enumerate(questions):

    st.write(f"**{q['question']}**")

    answer = st.radio(
        "Choose your answer:",
        q["options"],
        index=None,
        key=f"question_{i}"
    )

    user_answers.append(answer)

st.markdown("---")

# --------------------------------------------------
# ADDITIONAL WIDGETS
# --------------------------------------------------

confidence = st.slider(
    "How confident are you about your answers?",
    min_value=0,
    max_value=100,
    value=50,
    format="%d%%"
)

feedback = st.text_area(
    "Do you have any comments about this quiz?"
)

# --------------------------------------------------
# SUBMIT BUTTON AND SCORE CALCULATION
# --------------------------------------------------

if st.button("Submit Quiz", type="primary"):

    if not name.strip():
        st.error("Please enter your name before submitting.")

    elif None in user_answers:
        st.warning("Please answer all five questions before submitting.")

    else:
        score = 0

        for i, q in enumerate(questions):
            if user_answers[i] == q["answer"]:
                score += 1

        st.markdown("---")
        st.header("Quiz Results")

        st.write(f"**Participant:** {name}")
        st.write(f"**Experience level:** {level}")
        st.write(f"**Confidence level:** {confidence}%")

        st.metric(
            label="Your Final Score",
            value=f"{score}/5"
        )

        # RESULT MESSAGES
        if score == 5:
            st.success(
                f"Excellent, {name}! Perfect score! "
                "You answered all questions correctly."
            )

        elif score >= 3:
            st.warning(
                f"Good job, {name}! You passed the quiz "
                f"with {score} out of 5 correct answers."
            )

        else:
            st.error(
                f"Keep practicing, {name}! "
                f"You scored {score} out of 5. "
                "Review your Python fundamentals and try again."
            )

        # DISPLAY ANSWER REVIEW
        st.subheader("Answer Review")

        for i, q in enumerate(questions):

            if user_answers[i] == q["answer"]:
                st.write(f"✅ Question {i+1}: Correct")
            else:
                st.write(
                    f"❌ Question {i+1}: "
                    f"Your answer: {user_answers[i]} | "
                    f"Correct answer: {q['answer']}"
                )

        if feedback.strip():
            st.info(f"Your feedback: {feedback}")
