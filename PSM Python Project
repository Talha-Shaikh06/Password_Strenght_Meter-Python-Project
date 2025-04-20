import streamlit as st
import re

def check_strength(password):
    score = 0
    feedback = []

    # Length checks
    if len(password) >= 8:
        score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    if re.search(r"[a-z]", password) and re.search(r"[A-Z]", password):
        score += 1
    else:
        feedback.append("Use both uppercase and lowercase letters.")

    if re.search(r"\d", password):
        score += 1
    else:
        feedback.append("Add at least one number.")

    if re.search(r"[!@#$%^&*(),.?\":{}|<>]", password):
        score += 1
    else:
        feedback.append("Add special characters like !, @, #, etc.")

    if len(password) > 12:
        score += 1

    return score, feedback

def get_strength_label(score):
    if score <= 1:
        return "Very Weak", "red"
    elif score == 2:
        return "Weak", "orange"
    elif score == 3:
        return "Moderate", "yellow"
    elif score == 4:
        return "Strong", "lightgreen"
    else:
        return "Very Strong", "green"

# Streamlit UI
st.title("🔐 Password Strength Meter")

password = st.text_input("Enter your password", type="password")

if password:
    score, feedback = check_strength(password)
    strength, color = get_strength_label(score)
    st.markdown(f"**Strength:** <span style='color:{color}'>{strength}</span>", unsafe_allow_html=True)

    st.progress(score / 5)

    if feedback:
        st.markdown("**Suggestions:**")
        for item in feedback:
            st.markdown(f"- {item}")
