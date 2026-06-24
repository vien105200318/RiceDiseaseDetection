# Rice Disease Detection & AI Treatment Assistant Mobile App

A smart, production-ready mobile application that empowers farmers to diagnose rice diseases instantly via smartphone cameras. The system utilizes a hybrid AI architecture: a **Computer Vision model** detects the disease from leaf images, and a **Large Language Model (LLM)** generates personalized treatment plans, prevention steps, and pesticide prescriptions.

---

## 🚀 Key Features

- **Instant Diagnosis:** Take a photo or upload an image of a rice leaf directly from the field.
- **Smart Image Cropping:** Built-in cropping tool allows farmers to focus precisely on infected leaf areas for maximum AI accuracy.
- **Multimodal AI Insights:** Combines Vision AI predictions with an LLM-driven "Digital Agronomist" to provide comprehensive, readable medical prescriptions for crops.
- **Interactive Dashboard:** Beautiful UI featuring fluid loading states, markdown rendering for AI advice, and percentage indicators for model confidence.

---

## 🏗️ System Architecture & Data Flow

The project follows a modern **End-to-End Multimodal AI Application** architecture:

```text
[Flutter App] ──(Upload Image via Dio)──> [FastAPI Backend]
                                                 │
                                        ┌────────┴────────┐
                                        ▼                 ▼
                                 [Vision AI]         [LLM API]
                            (Detects Disease & %)  (Generates Treatment)
                                        └────────┬────────┘
                                                 ▼
[Flutter App] <──(Render Markdown UI)─── [Clean JSON Response]
```

1. **Presentation Layer (Mobile):** User captures an image. Flutter handles local state management and transmits the file asynchronously.
2. **Analysis Layer (Backend):** The server processes the image through a specialized Computer Vision model to identify the disease label (e.g., Blast, Bacterial Blight) and confidence metrics.
3. **Reasoning Layer (LLM):** The backend injects the detected label into a domain-specific prompt engineering pipeline, prompting the LLM to return actionable, structured agricultural advice in Vietnamese.

---

## 📱 Mobile App Architecture (Flutter)

The mobile client is engineered using **Clean Architecture** principles coupled with the **BLoC (Business Logic Component) Pattern** to ensure strict separation of concerns, testability, and scalability.

```text
lib/
├── data/                  # Data Layer: API services (Dio) & Data Models (JSON parsing)
├── domain/                # Domain Layer: Core Business Entities & Repository Interfaces
└── presentation/          # UI Layer: BLoC State Management, Screens, and Widgets
```

### State Management Lifecycle (`RiceDetectBloc`):
- `RiceDetectInitial`: Waiting for user interaction (Camera/Gallery selection).
- `RiceDetectLoading`: Asynchronous API upload in progress; triggers dynamic loading indicators.
- `RiceDetectSuccess`: Successfully parses JSON and populates the UI with percentage charts and markdown text.
- `RiceDetectFailure`: Catches network/server errors gracefully with "Retry" mechanisms.

---

## 🛠️ Tech Stack & Dependencies

### Mobile Client (Flutter & Dart)
- **State Management:** `flutter_bloc` (Event-driven architecture)
- **Networking:** `dio` (Robust HTTP client for multipart file uploads)
- **Media Handling:** `image_picker` & `image_cropper`
- **UI & Visualization:** `flutter_markdown` (Renders rich-text LLM outputs) & `percent_indicator`

### Backend & AI Infrastructure
- **Framework:** Python / FastAPI (Optimized for low-latency asynchronous routing)
- **Vision AI Core:** Deep Learning-based Computer Vision Architecture
- **Language Intelligence:** LLM APIs integrated via Server-Side Prompt Engineering

---

## 📸 Screen Previews & Demo

| Home Screen | Analyzing State | AI Expert Prescription |
| :---: | :---: | :---: |
| *[Place your Home screenshot here]* | *[Place your Loading screenshot here]* | *[Place your Result screenshot here]* |

> 📺 **Watch the Full Mobile Walkthrough Video:** [Link to your Youtube/Drive Video Demo]

---

## ⚙️ Setup & Installation

### Prerequisites
- Flutter SDK (Latest Stable Version)
- Android Studio / VS Code
- A running instance of the Python Backend Server

### Mobile Installation Steps
1. Clone this repository:
   ```bash
   git clone https://github.com
   cd rice-disease-app
   ```
2. Install dependencies:
   ```bash
   flutter pub get
   ```
3. Configure the API Endpoint:
   Open `lib/data/datasources/api_client.dart` and update the `baseUrl` to match your Python server's local IP address.
4. Run the application:
   ```bash
   flutter run
   ```

---

## 👨‍💻 Developer Profile

- **Developer:** Vien Nguyen
- **Core Focus:** Fullstack Development & Applied Artificial Intelligence Systems
- **Contact:** attackervien1@gmail.com | 0796716811
