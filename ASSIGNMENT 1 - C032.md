# Assignment 1 - C032
#!/bin/bash

# ============================================
# GEMINI AI CHATBOT - GITHUB SETUP SCRIPT
# Author: Avaneesh Thakur
# Roll Number: C032
# ============================================

echo "=========================================="
echo "   GEMINI AI CHATBOT - GITHUB SETUP"
echo "=========================================="

# STEP 1: CONFIGURATION
REPO_URL="YOUR_GITHUB_REPOSITORY_URL"
PROJECT_FOLDER="GeminiAIChatbot"
SCREENSHOT_SOURCE="/mnt/data/SCREEEN SHOT GEMINI CHATBOT.png"

# STEP 2: CLONE THE REPOSITORY
echo ""
echo "Cloning GitHub repository..."

git clone "$REPO_URL" "$PROJECT_FOLDER"

if [ $? -ne 0 ]; then
    echo "Error: Failed to clone the repository."
    exit 1
fi

cd "$PROJECT_FOLDER" || exit 1

echo "Repository cloned successfully."

# STEP 3: CREATE SCREENSHOTS FOLDER
echo ""
echo "Creating screenshots folder..."

mkdir -p screenshots

# STEP 4: COPY THE SCREENSHOT
echo ""
echo "Adding application screenshot..."

if [ -f "$SCREENSHOT_SOURCE" ]; then
    cp "$SCREENSHOT_SOURCE" "screenshots/gemini-chatbot.png"
    echo "Screenshot added successfully."
else
    echo "WARNING: Screenshot not found at:"
    echo "$SCREENSHOT_SOURCE"
    echo ""
    echo "Please manually copy your screenshot to:"
    echo "$(pwd)/screenshots/gemini-chatbot.png"
fi

# STEP 5: CREATE README FILE
echo ""
echo "Creating README.md..."

cat > README.md <<'EOF'
# Gemini AI Chatbot – Android Application

<p align="center">
  <img src="screenshots/gemini-chatbot.png"
       alt="Gemini AI Chatbot Application"
       width="300">
</p>

<p align="center">
  <b>An AI-powered Android chatbot built using Kotlin, Jetpack Compose, and Google Gemini AI.</b>
</p>

---

## Mobile Application Development Lab – Assignment 1

**Name:** Avaneesh Thakur

**Roll Number:** C032

**Program:** B.Tech Computer Science

**University:** SVKM's NMIMS University, School of Technology Management & Engineering

---

## About the Project

Gemini AI Chatbot is a modern Android application that allows users to interact with Google's Gemini AI through an intuitive and responsive chat interface.

The application enables users to send text prompts, receive AI-generated responses, and interact with the chatbot using voice input.

It also includes local chat history storage, allowing users to access previous conversations even after restarting the application.

This project demonstrates the practical implementation of modern Android development concepts, including declarative UI design, AI integration, state management, local data persistence, voice recognition, responsive layouts, and secure API configuration.

---

## Key Features

### 1. AI-Powered Chat

- Integration with Google Gemini AI.
- Text-based interaction with the chatbot.
- Conversational display of user and AI messages.
- Loading indicators and error handling.

### 2. Modern User Interface

- Developed using Jetpack Compose.
- Material 3 design components.
- Separate chat bubbles for user and AI messages.
- LazyColumn for displaying conversations.
- Automatic scrolling to the latest message.

### 3. Voice Input

- Voice-to-text functionality using RecognizerIntent.
- Allows users to speak their prompts.
- Voice interaction integrated into the chat interface.

### 4. Persistent Chat History

- Local chat storage using Room Database.
- Conversations remain available after restarting the application.
- Asynchronous database operations using Kotlin Coroutines.

### 5. User Preferences

- Preferences DataStore for storing application settings.
- Support for dark mode preferences.
- Configurable automatic scrolling behavior.

### 6. Theme Support

- Light and dark theme support.
- System theme compatibility.
- Consistent Material 3 styling.

### 7. Responsive Layout

- Adaptable interface for different Android screen sizes.
- Support for portrait and landscape orientations.
- Flexible layout for smartphones and larger displays.

### 8. API Key Protection

- API key configuration through local.properties.
- Encryption using AES-256-GCM.
- Encryption key protection through Android Keystore.
- Avoids intentionally logging or displaying sensitive credentials.

> For production deployment, a secure backend proxy is recommended to keep API credentials away from the client application.

---

## Technology Stack

| Technology | Purpose |
|---|---|
| Kotlin | Android application development |
| Jetpack Compose | Declarative user interface |
| Material 3 | UI components and theming |
| Google Gemini AI | AI-generated responses |
| Room Database | Local chat history storage |
| Preferences DataStore | User preferences |
| Android Keystore | Cryptographic key protection |
| AES-256-GCM | Data encryption |
| StateFlow | Reactive state management |
| Kotlin Coroutines | Asynchronous operations |
| RecognizerIntent | Voice-to-text input |
| JUnit | Unit testing |
| Compose UI Testing | Interface testing |

---

## Application Architecture

The application follows an MVVM-inspired architecture that separates the user interface, application logic, and data management.

### Presentation Layer

The presentation layer is built using Jetpack Compose.

Responsibilities include:

- Displaying messages.
- Accepting user input.
- Handling voice interactions.
- Showing loading and error states.
- Managing themes and responsive layouts.

### ViewModel Layer

The ChatViewModel manages the chatbot's UI state and coordinates communication between the interface and the data layer.

StateFlow is used to expose state changes to the Compose UI.

### Repository Layer

The repository provides a connection between the ViewModel and the data sources.

It manages:

- Communication with Gemini AI.
- Chat history operations.
- Data retrieval and storage.

### Data Layer

The data layer manages the application's data sources, including:

- Gemini AI integration.
- Room Database.
- Preferences DataStore.
- Secure API key management.

---

## Application Workflow

```text
User Input
    |
    v
Jetpack Compose UI
    |
    v
ChatViewModel
    |
    v
Repository
    |
    +----> Room Database
    |
    v
Gemini AI Service
    |
    v
AI-Generated Response
    |
    v
ChatViewModel Updates State
    |
    v
Jetpack Compose UI
    |
    v
Save Conversation

![Gemini AI Chatbot](image.png)
