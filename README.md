# SIGN — ASL Alphabet Detector

A modern, responsive, and highly interactive web application that uses **MediaPipe Hands** to detect American Sign Language (ASL) fingerspelling (A–Z) in real-time right from your webcam.

Developed using Vanilla HTML, CSS (Space Grotesk & Righteous typography), and JavaScript with a custom geometric ASL classifier.

## 🚀 Features

- **Live Camera Feed**: Real-time webcam integration with mirroring and overlay support.
- **Skeleton Tracking**: Interactive skeleton rendering overlay using 21 MediaPipe hand landmarks.
- **ASL Geometric Classifier**: Uses key distance, curl, and angle calculations to classify the 26 letters of the ASL alphabet in real-time.
- **Word Builder**: Hold a sign for 0.8 seconds to dynamically build words. Includes controls to delete letters, insert spaces, clear, or copy the word to your clipboard.
- **Alphabet Grid Reference**: Dynamic reference grid showing visual emoji indicators and helpful tooltips/descriptions for each letter. Highlighted dynamically as you sign.
- **Discovered Progress**: Tracks letters discovered during the session with a visually premium progress indicator.
- **Live Stats**: Real-time trackers for detection count, accuracy percentage, and current word length.

## 🛠️ Getting Started

### Prerequisites

You only need **Node.js** installed on your system to run the local server.

### Installation

1. Install the required development dependencies (Vite):
   ```bash
   npm install
   ```

2. Start the local development server:
   ```bash
   npm run dev
   ```

3. Open the provided local URL in your web browser:
   ```text
   http://localhost:5173/
   ```

## 📂 Project Structure

- `index.html` - The main application file containing markup, responsive styling, and classification scripts.
- `package.json` - Development configuration for running and building the application with Vite.
- `README.md` - Setup instructions and feature documentation.

## 🧪 Geometric Classifier Architecture

The classification logic in `index.html` processes raw 3D coordinates from the MediaPipe landmarks:
1. **Normalization**: Landmark positions are normalized relative to the wrist (landmark 0) and scaled according to the hand size (distance from wrist to middle MCP joint).
2. **Feature Extraction**:
   - Calculates finger extension states based on tip-to-wrist vs PIP-to-wrist distances.
   - Calculates finger curl amounts normalized from 0 to 1.
   - Calculates pinch distances (e.g., thumb-index distance, index-middle spread).
   - Resolves finger angles (e.g., thumb spread, index tilt).
3. **Decision Tree**: Evaluates the mathematical relationships corresponding to the anatomical shape of each ASL letter.
