def get_personal_info():
    name = input("Enter your name: ")
    age = int(input("Enter your age: "))
    gender = input("Enter your gender: ")
    blood_group = input("Enter your blood group: ")
    symptoms = input("Describe your symptoms: ")
    return name, age, gender, blood_group, symptoms

def recommend_treatment(symptoms):
    medicine_dict = {
        "fever": "Acetaminophen",
        "cough": "Cough syrup",
        "shortness of breath": "Emergency medical attention required",
        "headache": "Rest in a quiet and dark room, drink plenty of water, consider taking over-the-counter pain relievers like acetaminophen"
    }
    
    recommended_medicines = []
    treatment_recommendation = []
    
    for symptom in symptoms.split(','):
        if symptom.strip() in medicine_dict:
            recommended_medicines.append(medicine_dict[symptom.strip()])
            if symptom.strip() == "shortness of breath":
                treatment_recommendation.append("Seek immediate medical help for further evaluation.")
    
    if not recommended_medicines:
        return "No specific medicine recommendation. Please consult a healthcare professional."
    else:
        output = f"Medicines: {', '.join(recommended_medicines)}"
        if treatment_recommendation:
            output += f"\nTreatment Recommendation: {', '.join(treatment_recommendation)}"
        return output

# Main Program
name, age, gender, blood_group, symptoms = get_personal_info()
treatment_info = recommend_treatment(symptoms)
print(f"Hello {name}, based on your symptoms, here are the recommended medicines and treatment recommendation:\n{treatment_info}")
