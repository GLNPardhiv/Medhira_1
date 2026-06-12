//Medhira//

A web application that records doctor-patient consultations and automatically generates medical summaries using AI-powered transcription and analysis.

## 

This application helps healthcare professionals by automating the medical documentation process. Doctors can record their patient consultations, and the system automatically transcribes the audio and generates structured medical summaries that can be saved to Google Drive.

Problem it solves: Reduces time spent on medical documentation and ensures consistent, structured patient records.

# ✨ Features

- Audio Recording Record consultations directly in the browser
- File Upload: Upload existing audio files (MP3, WAV, M4A, WebM)
- AI Transcription: Automatic speech-to-text using OpenAI Whisper
- Medical Summary Generation: AI-powered structured medical summaries
- Google Drive Integration: Save summaries directly to Google Drive
- Consultation History: View and manage all past consultations
- User Authentication: Secure login and registration system
- Real-time Status Updates: Live progress tracking during processing

# 🛠️ Technologies Used

#Frontend
- React - User interface framework
- Vite - Build tool and development server
- CSS3 - Styling with custom variables
- Lucide React - Icons
- React Router - Navigation

### Backend
- Node.js - Runtime environment
- Express.js - Web framework
- MongoDB - Database
- Mongoose - MongoDB object modeling
- JWT - Authentication
- Multer - File upload handling
- OpenAI API - AI services

### External APIs
- OpenAI Whisper - Audio transcription
- OpenAI GPT-4- Medical summary generation
- Google Drive API - Cloud storage

## 📁 Project Structure

```
patient-doctor-summarizer/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/
│   │   │   │   ├── ErrorBoundary.jsx
│   │   │   │   ├── Navbar.jsx
│   │   │   │   └── ProtectedRoute.jsx
│   │   │   └── dashboard/
│   │   │       ├── AudioRecorder.jsx
│   │   │       ├── HistoryTable.jsx
│   │   │       ├── SummaryEditor.jsx
│   │   │       └── TranscriptViewer.jsx
│   │   ├── hooks/
│   │   │   ├── useAuth.jsx
│   │   │   └── useConsultations.jsx
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── HistoryPage.jsx
│   │   │   ├── LandingPage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── SettingsPage.jsx
│   │   │   └── SignUpPage.jsx
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   └── googleDrive.js
│   │   └── styles/
│   │       ├── auth.css
│   │       ├── dashboard.css
│   │       ├── global.css
│   │       ├── landing.css
│   │       └── settings.css
│   ├── package.json
│   └── vite.config.js
└── backend/
    ├── controllers/
    │   ├── audioController.js
    │   ├── authController.js
    │   └── consultationController.js
    ├── middleware/
    │   ├── auth.js
    │   └── upload.js
    ├── models/
    │   ├── Consultation.js
    │   └── User.js
    ├── routes/
    │   ├── audio.js
    │   ├── auth.js
    │   └── consultations.js
    ├── services/
    │   ├── openaiService.js
    │   └── googleDriveService.js
    ├── uploads/
    ├── package.json
    └── server.js
```

## 🚀 Installation & Setup

### Prerequisites
- Node.js (version 18 or higher)
- MongoDB (local installation or MongoDB Atlas account)
- OpenAI API account
- Google Cloud account (for Drive integration)

### Step 1: Clone the Repository
```bash
git clone https://github.com/24CSB0B35/Medhira.git
cd Test_Demo
```

### Step 2: Backend Setup
```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create environment file
cp .env.example .env
```

**Configure backend environment variables in `backend/.env`:**
```env
PORT=5002
MONGODB_URI=mongodb://localhost:27017/medhira_db
JWT_SECRET=your_super_secure_jwt_secret_here
OPENAI_API_KEY=sk-your-openai-api-key-here
GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:5002/api/auth/google/callback
```

### Step 3: Frontend Setup
```bash
# Navigate to frontend directory
cd ../frontend

# Install dependencies
npm install

# Create environment file
cp .env.example .env
```

**Configure frontend environment variables in `frontend/.env`:**
```env
VITE_API_BASE_URL=http://localhost:5002
VITE_GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
```

### Step 4: Start MongoDB
```bash
# If using local MongoDB
mongod

# Or use MongoDB Atlas (cloud) - update MONGODB_URI in .env
```

### Step 5: Run the Application
```bash
# Terminal 1 - Start backend server
cd backend
npm run dev

# Terminal 2 - Start frontend development server
cd frontend
npm run dev
```

**Application URLs:**
- Frontend: http://localhost:3000
- Backend API: http://localhost:5002

## 📖 How to Use

### For Healthcare Professionals

#### 1. Create an Account
- Open http://localhost:3000
- Click "Sign Up" and create your account
- Login with your credentials

#### 2. Record a Consultation
- Go to Dashboard
- Click "Start Recording" to record live audio
- Or click "Upload Audio" to use existing audio files
- Stop recording when finished

#### 3. Review AI-Generated Content
- View the transcribed conversation in Transcript Viewer
- Review the medical summary in Summary Editor
- Edit any fields as needed

#### 4. Save Your Work
- Connect Google Drive in Settings
- Click "Save to Google Drive" to store as PDF
- Or "Download as Text" for local storage

#### 5. Manage Consultations
- View all past consultations in History page
- Search and filter patient records
- Delete old consultations if needed

## 🔧 API Configuration

### OpenAI API Setup
1. Go to [OpenAI Platform](https://platform.openai.com/)
2. Create account and generate API key
3. Add key to `backend/.env` as `OPENAI_API_KEY`

### Google Drive API Setup
1. Visit [Google Cloud Console](https://console.cloud.google.com/)
2. Create new project
3. Enable "Google Drive API"
4. Create OAuth 2.0 credentials
5. Add authorized origins: `http://localhost:3000`
6. Copy credentials to both `.env` files



## 🐛 Troubleshooting

### Common Issues

**MongoDB Connection Issues**
```bash
# Check if MongoDB is running
brew services list | grep mongodb

# Start MongoDB if not running
brew services start mongodb-community
```

**Audio Recording Not Working**
- Ensure microphone permissions are granted in browser
- Use HTTPS in production (required for microphone access)

**Google Drive Authentication Failed**
- Verify OAuth credentials in Google Cloud Console
- Check authorized JavaScript origins and redirect URIs

**OpenAI API Errors**
- Verify API key is correct and has credits
- Check API usage limits on OpenAI dashboard

### Development Tips
- The app automatically uses mock data when APIs are unavailable
- Check browser console for detailed error messages
- Use the network tab to monitor API requests

## 🔒 Security Features

- JWT token-based authentication
- Protected API routes
- Secure file upload handling
- Patient data encryption
- Google OAuth 2.0 for secure Drive access



## 🔗 Links

- **GitHub Repository**: https://github.com/24CSB0B35/Medhira


# Medhira
