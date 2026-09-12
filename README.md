# 🏥 MediCare — AI-Assisted Healthcare Management System

> **An integrated healthcare management platform that connects patients, doctors, and administrators while providing AI-assisted preliminary symptom analysis using Machine Learning.**

MediCare is a full-stack healthcare management system designed to simplify healthcare-related activities through a single digital platform. The system provides separate interfaces for **Patients, Doctors, and Administrators**, along with an **AI Health module** for preliminary symptom-pattern analysis.

The AI module processes symptoms entered in natural language using **exact matching, synonym matching, and fuzzy matching**, and then uses a **Random Forest classifier** to identify possible disease patterns and provide related health information and precautions.

> ⚠️ **Medical Disclaimer:** The AI Health module is intended for educational and preliminary informational purposes only. It is not a medical diagnosis system and should not replace consultation with a qualified healthcare professional.

---

## ✨ Key Features

### 👤 Patient Portal

* User registration and authentication
* Browse available doctors
* View doctor profiles and details
* Browse healthcare services
* Book doctor appointments
* Book healthcare-service appointments
* Online payment using Stripe
* Cash payment option
* Appointment confirmation
* AI-assisted symptom analysis
* View preliminary health information and precautions

### 👨‍⚕️ Doctor Portal

* Secure doctor authentication
* Doctor dashboard
* View appointments
* Manage appointment status
* Reschedule appointments
* Manage doctor profile
* Manage availability

### 🛠️ Admin Portal

* Admin authentication
* Admin dashboard
* Add doctors
* Update doctor information
* Delete doctors
* Manage healthcare services
* View appointments
* Monitor system statistics

### 🤖 AI Health Module

The AI Health module allows users to enter symptoms using natural language.

The processing pipeline includes:

```text
User Symptom Input
        ↓
Text Processing
        ↓
Symptom Recognition
        ↓
Exact Matching
        +
Synonym Matching
        +
Fuzzy Matching
        ↓
Feature Representation
        ↓
Random Forest Classifier
        ↓
Disease Pattern Prediction
        ↓
Health Information & Precautions
```

The system is designed to handle variations in the way users describe symptoms, including synonyms and minor spelling differences.

---

# 🏗️ System Architecture

```text
                         ┌─────────────────────┐
                         │        USERS        │
                         └──────────┬──────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
              ▼                     ▼                     ▼
       ┌─────────────┐       ┌─────────────┐       ┌─────────────┐
       │   PATIENT   │       │   DOCTOR    │       │    ADMIN    │
       │   PORTAL    │       │   PORTAL    │       │  DASHBOARD  │
       └──────┬──────┘       └──────┬──────┘       └──────┬──────┘
              │                     │                     │
              └─────────────────────┼─────────────────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Node.js + Express   │
                         │      Backend        │
                         │      REST APIs      │
                         └──────────┬──────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
              ▼                     ▼                     ▼
        ┌───────────┐         ┌───────────┐        ┌────────────┐
        │  MongoDB  │         │  Stripe   │        │ Cloudinary │
        │  Database │         │  Payment  │        │   Images   │
        └───────────┘         └───────────┘        └────────────┘


                         AI HEALTH MODULE
                                │
                                ▼
                       ┌─────────────────┐
                       │   Python API    │
                       │ Flask + Waitress│
                       └────────┬────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │ Symptom Matching│
                       │                 │
                       │ Exact           │
                       │ Synonym         │
                       │ Fuzzy           │
                       └────────┬────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │ Feature         │
                       │ Processing      │
                       └────────┬────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │ Random Forest   │
                       │   Classifier    │
                       └────────┬────────┘
                                │
                                ▼
                       ┌─────────────────┐
                       │ Prediction      │
                       │ & Health Info   │
                       └─────────────────┘
```

---

# 🔄 Application Workflow

## Patient Workflow

```text
Patient
   ↓
Login / Registration
   ↓
Browse Doctors or Services
   ↓
Select Doctor / Service
   ↓
Choose Appointment
   ↓
Payment
   ↓
Appointment Confirmation
```

## Doctor Workflow

```text
Doctor
   ↓
Login
   ↓
Doctor Dashboard
   ↓
View Appointments
   ↓
Accept / Update / Reschedule
   ↓
Manage Availability
```

## Admin Workflow

```text
Admin
   ↓
Login
   ↓
Admin Dashboard
   ↓
Manage Doctors
   ↓
Manage Services
   ↓
Manage Appointments
   ↓
View Statistics
```

## AI Health Workflow

```text
Patient enters symptoms
          ↓
Natural-language processing
          ↓
Symptom extraction
          ↓
Exact / Synonym / Fuzzy matching
          ↓
Feature representation
          ↓
Random Forest model
          ↓
Possible disease pattern
          ↓
Description + Precautions
```

---

# 🧠 AI/ML Methodology

The AI component is implemented as a separate Python-based service.

### 1. User Input

The patient enters symptoms in natural language.

Example:

```text
"I have high temperature, headache and dizziness."
```

### 2. Symptom Recognition

The system identifies relevant symptoms from the input.

It supports:

* Exact symptom matching
* Synonym matching
* Fuzzy matching

For example:

```text
"high temperature" → fever
"dizzy"            → dizziness
```

### 3. Feature Representation

Recognized symptoms are converted into a format that can be processed by the machine-learning model.

### 4. Random Forest Classification

The processed symptom features are passed to a **Random Forest classifier**.

Random Forest combines predictions from multiple decision trees to produce a classification result.

### 5. Result

The system returns information such as:

* Recognized symptoms
* Possible disease pattern
* Model confidence information
* Condition description
* Precautions

---

# 🛠️ Technology Stack

## Frontend

* React
* Vite
* Axios
* HTML
* CSS
* JavaScript

## Backend

* Node.js
* Express.js
* REST APIs

## Database

* MongoDB

## Authentication

* Clerk
* JWT

## Payment

* Stripe

## Media Management

* Cloudinary

## AI / Machine Learning

* Python
* Flask
* Waitress
* scikit-learn
* pandas
* NumPy
* Random Forest

---

# 📁 Project Structure

```text
MediCare/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── admin/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── backend/
│   ├── ai_health/
│   │   ├── dataset/
│   │   ├── model/
│   │   ├── Python files
│   │   └── ...
│   │
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── server files
│   └── package.json
│
└── README.md
```

> The exact folder/file names may vary with the current version of the repository.

---

# 🔐 Security & Authentication

MediCare uses authentication mechanisms for different user roles.

### Patient/Admin

Authentication is handled using **Clerk**.

### Doctor

The doctor portal uses **JWT-based authentication**.

Role-based access helps ensure that users can access functionality appropriate to their role.

```text
Patient → Patient Features

Doctor → Doctor Features

Admin → Administrative Features
```

---

# 💳 Payment System

MediCare supports online appointment payments through **Stripe** as well as a cash payment option.

### Online Payment Flow

```text
Patient
   ↓
Select Appointment
   ↓
Select Online Payment
   ↓
Stripe Checkout
   ↓
Payment
   ↓
Confirmation
```

---

# ☁️ Image Management

**Cloudinary** is used for cloud-based image/media management, such as doctor profile images.

```text
Image Upload
     ↓
Cloudinary
     ↓
Image URL
     ↓
Application
```

---

# 🎯 Problem Statement

Healthcare services can be fragmented across different platforms, making it difficult for patients to search for doctors, manage appointments, access healthcare services, and obtain preliminary information about symptoms.

Additionally, patients often describe symptoms using different words, synonyms, or spelling variations. A simple keyword-based system may fail to recognize these variations.

Therefore, there is a need for an integrated healthcare platform that combines healthcare management with intelligent preliminary symptom analysis.

---

# 💡 Proposed Solution

MediCare provides a unified platform for patients, doctors, and administrators.

The system combines:

```text
Healthcare Management
        +
Doctor & Service Discovery
        +
Appointment Management
        +
Payment Processing
        +
AI-Assisted Symptom Analysis
```

The AI module improves symptom recognition by combining exact, synonym, and fuzzy matching with a Random Forest classification model.

---

# 🌍 Social Relevance

MediCare aims to improve the accessibility and convenience of digital healthcare services by:

* Simplifying doctor discovery
* Making appointment booking easier
* Providing centralized healthcare-service management
* Supporting doctors in appointment management
* Providing preliminary symptom-pattern information
* Reducing dependence on fragmented healthcare workflows

The AI component is designed as a **supportive and educational tool**, not as a replacement for medical professionals.

---

# 📊 Results & Evaluation

The AI model should be evaluated using standard machine-learning metrics such as:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

Example evaluation format:

| Model         | Accuracy | Precision | Recall | F1-Score |
| ------------- | -------: | --------: | -----: | -------: |
| Random Forest |      XX% |       XX% |    XX% |      XX% |

> **Important:** Replace `XX%` with the actual values obtained from your test dataset. Do not publish estimated or fabricated results.

---

# 📌 Advantages

* Unified healthcare management platform
* Separate Patient, Doctor and Admin portals
* Online appointment booking
* Online payment support
* Doctor availability management
* Centralized administration
* Natural-language symptom processing
* Exact, synonym and fuzzy symptom matching
* Machine-learning-based symptom-pattern classification
* Modular architecture with a separate AI service

---

# ⚠️ Limitations

* AI predictions depend on the quality and coverage of the training dataset.
* Natural-language symptom descriptions can be ambiguous.
* Fuzzy matching can sometimes incorrectly map user input.
* The model may not generalize to all real-world patient populations.
* The AI module is not clinically validated.
* The system should not be used as a replacement for professional medical diagnosis.

---

# 🚀 Future Scope

Future improvements may include:

### AI & NLP

* Transformer-based NLP models
* BERT / ClinicalBERT
* Sentence Transformers
* Multilingual symptom understanding
* Voice-based symptom input
* Explainable AI
* Improved uncertainty estimation

### Healthcare Features

* Electronic health records
* Prescription management
* Medical report management
* Laboratory report integration
* Telemedicine
* Doctor feedback on AI predictions

### Research

* Larger and more diverse datasets
* Comparison with additional ML algorithms
* Cross-validation
* Bias and fairness evaluation
* Clinical expert evaluation
* Real-world validation

---

# 🧪 Research Contribution

The research direction of MediCare focuses on integrating:

```text
Natural-Language Symptom Processing
                +
Symptom Matching
                +
Machine Learning
                +
Healthcare Management
```

Potential research questions include:

1. How effectively can natural-language symptom matching identify predefined symptoms?
2. How accurately can Random Forest classify disease patterns from recognized symptoms?
3. Does synonym and fuzzy matching improve symptom recognition compared with exact matching?
4. How can AI-assisted healthcare systems provide useful preliminary information while maintaining appropriate medical limitations?

---

# 👥 Team Contributions

| Team Member | Contribution                  |
| ----------- | ----------------------------- |
| Member 1    | Frontend Development          |
| Member 2    | Backend & REST APIs           |
| Member 3    | AI/ML & Symptom Analysis      |
| Member 4    | Admin/Doctor Module & Testing |

> Replace the above roles with your team's actual contributions.

---

# 🖥️ Screenshots

Add screenshots of the main modules here.

### Home Page

```text
Add screenshot here
```

### Patient Dashboard

```text
Add screenshot here
```

### Doctor Dashboard

```text
Add screenshot here
```

### Admin Dashboard

```text
Add screenshot here
```

### AI Health

```text
Add screenshot here
```

---

# ⚙️ Installation & Setup

## Prerequisites

Make sure you have installed:

* Node.js
* npm
* Python 3.x
* MongoDB / MongoDB Atlas
* Git

---

## 1. Clone the Repository

```bash
git clone https://github.com/rohityadav8286/Medicare.git

cd Medicare
```

---

## 2. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

---

## 3. Admin Setup

Open another terminal:

```bash
cd admin
npm install
npm run dev
```

---

## 4. Backend Setup

Open another terminal:

```bash
cd backend
npm install
npm run server
```

> Use the actual backend start command defined in your `package.json` if it differs.

---

## 5. AI Health Setup

Open another terminal:

```bash
cd backend/ai_health

pip install -r requirements.txt
```

Then start the Python AI service using the command specified by the project configuration.

---

# 🔑 Environment Variables

Create the required `.env` files and add your own credentials.

Typical configuration may include:

```env
MONGODB_URI=your_mongodb_connection_string

CLERK_SECRET_KEY=your_clerk_secret

STRIPE_SECRET_KEY=your_stripe_secret

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

For the AI service, add any required model/API configuration according to the project's Python configuration.

> **Never commit real API keys, passwords, database credentials, or secret tokens to GitHub.**

---

# 🧑‍💻 Development Workflow

```text
Frontend
   ↓
Axios / HTTP Request
   ↓
Node.js + Express REST API
   ↓
Business Logic
   ↓
MongoDB / External Services
   ↓
Response
   ↓
Frontend
```

AI workflow:

```text
Frontend
   ↓
AI API Request
   ↓
Python Flask Service
   ↓
Symptom Processing
   ↓
Random Forest
   ↓
Prediction
   ↓
Frontend
```

---

# 📚 Technologies & Concepts Demonstrated

This project demonstrates practical knowledge of:

* Full-stack web development
* React
* REST APIs
* Node.js
* Express.js
* MongoDB
* Authentication & Authorization
* JWT
* API integration
* Payment integration
* Cloud media management
* Python
* Machine Learning
* Random Forest
* Natural-language processing
* Fuzzy matching
* Symptom classification
* Modular service architecture

---

# 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Commit your changes
5. Push the branch
6. Open a Pull Request

---

# 📄 Research Paper

A research paper is being prepared based on the AI-assisted healthcare management and symptom-pattern analysis component of MediCare.

### Proposed Research Title

**"An AI-Assisted Healthcare Management Platform for Natural-Language Symptom Pattern Analysis and Appointment Scheduling"**

---

# ⚠️ Disclaimer

MediCare is an academic/project prototype.

The AI Health feature provides preliminary and educational information based on the implemented machine-learning model. It does **not** provide a medical diagnosis and should not be used for emergency decisions or as a substitute for consultation with a qualified healthcare professional.

---

# 👨‍💻 Authors

**MediCare Project Team**

B.Tech — Computer Science & Engineering

---

# ⭐ Support

If you find this project useful, consider giving the repository a ⭐ star.

**GitHub Repository:**
https://github.com/rohityadav8286/Medicare
