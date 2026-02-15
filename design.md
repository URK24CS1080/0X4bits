# System Design – Community Information Assistant

## Architecture Overview
The system is a web-based AI assistant using Google Gemini API
to deliver category-specific civic and public service information.

## High-Level Architecture

User Interface (Web App)
        ↓
Frontend Interaction Logic
        ↓
Backend API (Node.js)
        ↓
Google Gemini API
        ↓
Formatted Response
        ↓
User (Text / Voice)

## Core Components

### 1. Frontend (Web App)
- Responsive, mobile-first design
- Clear section-based layout:
  - Header and introduction
  - Language selection
  - User category selection
  - Assistant interaction area
  - Quick topic shortcuts

### 2. User Category Engine
- Users select one category:
  Student, Farmer, Job Seeker, Senior Citizen, Woman, Business Owner
- Category is stored in session state
- All responses adapt based on selected category

### 3. AI Engine (Gemini API)

Responsibilities:
- Intent detection
- Answer generation
- Recommendation logic
- Language adaptation

Prompt Strategy:
- Simple language
- Step-by-step explanations
- Category-aware responses
- Voice-friendly phrasing

### 4. Backend Service
- Single API endpoint:
  `/api/ask`
- Sends to Gemini:
  - User query
  - Selected category
  - Selected language
- Returns structured response to frontend

## Interaction Flow

1. User selects language
2. User selects category
3. User asks a question (text or voice)
4. Input normalized into text
5. Context sent to Gemini API
6. Gemini generates response
7. Response formatted for:
   - Text display
   - Voice output (if enabled)
8. Response shown to user

## Voice & Low-Bandwidth Design

### Voice Interaction
- Speech-to-Text → Gemini → Text-to-Speech
- Optional voice mode
- Clear and slow phrasing for accessibility

### Low-Bandwidth Optimization
- Short responses
- Bullet points
- Minimal UI animations
- No heavy media dependencies

## Messaging Integration (Planned)
- WhatsApp and SMS-based access
- Short, concise answers
- Same Gemini-powered backend

## Accessibility Considerations
- High contrast UI
- Large touch targets
- Reduced motion support
- Voice-first option for low literacy users

## Safety and Ethics
- No personal data collection
- Session-based context only
- Neutral and inclusive responses
- Informational assistance only

## Future Enhancements
- Regional language expansion
- Offline FAQ caching
- Voice reminders (conceptual)
- Localized scheme databases

## Deployment Plan
- Web app hosted on free cloud platforms
- Scalable backend
- Easy updates to schemes and content
