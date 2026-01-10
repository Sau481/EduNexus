# EduNexus 🎓

**Smart Collaborative Classroom & Notebook Platform**

EduNexus is a production-grade educational platform that combines classroom management, collaborative note-sharing, and AI-powered learning assistance. Built with modern web technologies, it provides teachers and students with seamless tools for knowledge sharing and interactive learning.

---

## ✨ Key Features

### 🏫 Classroom Management
- **Multi-Classroom Support**: Teachers can create and manage multiple classrooms
- **Easy Enrollment**: Students join classrooms via unique codes
- **Subject Organization**: Organize content by subjects and chapters
- **Role-Based Access**: Distinct permissions for teachers and students

### 📚 Collaborative Notes
- **Upload & Share**: Students and teachers can upload PDF/TXT notes
- **Approval Workflow**: Student notes require teacher approval before becoming public
- **Visibility Control**: Students see their own notes + approved public notes
- **Smart Organization**: Notes are organized by chapter for easy navigation

### 🤖 AI-Powered Notebook
- **RAG (Retrieval-Augmented Generation)**: AI responses grounded in uploaded course materials
- **Chapter-Scoped Queries**: AI searches only within the current chapter's approved notes
- **Intelligent Recommendations**: Get relevant learning resources based on your queries
- **Powered by Google Gemini**: Advanced language model for accurate responses

### 💬 Interactive Q&A
- **Student Questions**: Ask questions publicly or privately
- **Teacher Responses**: Teachers can answer and provide guidance
- **Subject Filtering**: Questions are organized by subject for easy management
- **Knowledge Repository**: Build a searchable database of common questions

### 📢 Announcements
- **Subject-Level Broadcasts**: Teachers can post announcements for entire subjects
- **Real-time Updates**: Students receive important updates immediately
- **Community Engagement**: Foster communication within the classroom

### 📊 Teacher Dashboard
- **Pending Approvals**: Review and approve student note submissions
- **Question Management**: Track and respond to student queries
- **Subject Assignment**: Manage which teachers have access to which subjects
- **Analytics**: Monitor classroom activity and engagement

---

## 🚀 Upcoming Features

We're constantly evolving EduNexus to deliver even more powerful learning experiences. Here's what's coming next:

### 📝 Integrated Quiz & Assessment System
Real-time evaluations to measure student understanding and track learning progress. Create custom quizzes, auto-graded assessments, and performance analytics.

### 🎴 AI-Based Flashcards & Concept Diagrams
Visual and interactive tools for faster learning. Automatically generate flashcards from course content and create visual concept maps to help students grasp complex topics.

### 🧠 Smarter AI with Improved RAG
More accurate, context-aware responses from chapter content. Enhanced retrieval algorithms and better context understanding for more precise AI assistance.

### 🏛️ Multi-Institution Support
Scalable platform for colleges, schools, and universities. Manage multiple institutions, departments, and courses from a single unified platform.

### 📰 Student Tech Blogs & Knowledge Sharing
Daily technology blogs where students share insights, tools, and trends with peers. Build a vibrant learning community beyond the classroom.

---

## 🏗️ Architecture

EduNexus follows a modern **full-stack architecture** with a clear separation between frontend and backend:

```
┌─────────────────────────────────────────────────────────────┐
│                         Frontend                             │
│   React + TypeScript + Vite + shadcn/ui + Tailwind         │
│                  (Firebase Authentication)                   │
└─────────────────────────────────────────────────────────────┘
                            ↕ REST API
┌─────────────────────────────────────────────────────────────┐
│                         Backend                              │
│              FastAPI + Python + Pydantic                     │
│                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   Firebase   │  │   Supabase   │  │    Qdrant    │     │
│  │ Auth (Token) │  │  Postgres +  │  │   Vector DB  │     │
│  │ Verification │  │   Storage    │  │  (RAG/Search)│     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│                                                              │
│  ┌──────────────────────────────────────────────────┐      │
│  │          Google Gemini AI                        │      │
│  │   (Embeddings + Text Generation)                 │      │
│  └──────────────────────────────────────────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

### Tech Stack

#### Frontend
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized production builds
- **UI Library**: shadcn/ui with Radix UI primitives
- **Styling**: Tailwind CSS
- **State Management**: TanStack Query for server state
- **Routing**: React Router DOM
- **Authentication**: Firebase Auth
- **Forms**: React Hook Form + Zod validation
- **Markdown Rendering**: react-markdown

#### Backend
- **Framework**: FastAPI (Python)
- **Authentication**: Firebase Admin SDK (token verification only)
- **Database**: Supabase Postgres
- **File Storage**: Supabase Storage
- **Vector Database**: Qdrant (for semantic search)
- **AI/LLM**: Google Generative AI (Gemini)
- **Document Processing**: pdfminer.six
- **Validation**: Pydantic v2

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ and npm
- **Python** 3.9+
- **Docker** (for Qdrant)
- **Firebase** project
- **Supabase** project
- **Google Gemini API** key

### Installation

#### 1. Clone the Repository

```bash
git clone <YOUR_GIT_URL>
cd EduNexus
```

#### 2. Backend Setup

```bash
cd backend

# Install Python dependencies
pip install -r requirements.txt

# Configure environment variables
# Copy .env.example to .env and fill in:
# - FIREBASE_CREDENTIALS_PATH
# - SUPABASE_URL, SUPABASE_KEY, SUPABASE_SERVICE_KEY
# - GEMINI_API_KEY
# - QDRANT_URL, QDRANT_API_KEY (optional)

# Setup Firebase
# 1. Create Firebase project at https://console.firebase.google.com
# 2. Download service account JSON
# 3. Save to firebase/secrets/firebase-admin.json

# Setup Supabase
# 1. Create project at https://supabase.com
# 2. Run migrations from supabase_migrations/migrations/
# 3. Create storage bucket named "notes"

# Run Qdrant (using Docker)
docker run -p 6333:6333 qdrant/qdrant

# Start backend server
uvicorn app.main:app --reload
```

Backend will run on `http://localhost:8000`

API documentation: `http://localhost:8000/docs`

#### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Configure environment variables
# Create .env.local with:
# - VITE_API_URL=http://localhost:8000
# - Firebase config (VITE_FIREBASE_API_KEY, etc.)

# Start development server
npm run dev
```

Frontend will run on `http://localhost:5173`

---

## 📖 Usage Guide

### For Teachers

1. **Create an Account**: Sign up with your email
2. **Create a Classroom**: Set up a new classroom with a unique name
3. **Add Subjects**: Organize your classroom by subjects (e.g., Math, Science)
4. **Create Chapters**: Break down subjects into chapters
5. **Upload Notes**: Share course materials (PDF/TXT) - auto-approved
6. **Approve Student Notes**: Review and approve student submissions
7. **Answer Questions**: Respond to student queries
8. **Post Announcements**: Keep students informed with subject-level updates

### For Students

1. **Create an Account**: Sign up with your email
2. **Join a Classroom**: Enter the classroom code provided by your teacher
3. **Upload Notes**: Share your study materials (requires teacher approval)
4. **Browse Notes**: Access approved notes from teachers and peers
5. **Ask Questions**: Get help from teachers on specific subjects
6. **Use AI Notebook**: Query the AI assistant for chapter-specific help
7. **View Announcements**: Stay updated with classroom news

---

## 🔐 Authentication & Security

- **Firebase Authentication**: Secure user authentication on frontend
- **Token Verification**: Backend verifies Firebase ID tokens
- **Role-Based Access Control**: Strict permission checks for all operations
- **Chapter-Scoped Data**: Users only access data from their enrolled classrooms
- **Student Privacy**: Students only see approved public notes + their own uploads

---

## 🧠 AI & RAG Pipeline

The AI Notebook uses Retrieval-Augmented Generation (RAG) to provide accurate, context-aware responses:

1. **Document Upload**: PDFs/TXT files are uploaded
2. **Text Extraction**: Content is extracted using pdfminer.six
3. **Teacher Approval**: Notes must be approved before entering the RAG pipeline
4. **Embedding Generation**: Approved notes are embedded using Google Gemini
5. **Vector Storage**: Embeddings stored in Qdrant vector database
6. **Query Processing**: Student queries trigger semantic search in Qdrant
7. **Context Retrieval**: Relevant note snippets are retrieved
8. **AI Response**: Gemini generates response using retrieved context
9. **Chapter Scoping**: Only searches notes from the current chapter

---

## 📁 Project Structure

```
EduNexus/
├── backend/
│   ├── app/
│   │   ├── core/              # Config, auth, permissions
│   │   ├── modules/           # Feature modules (auth, classroom, etc.)
│   │   │   ├── auth/
│   │   │   ├── classroom/
│   │   │   ├── subject/
│   │   │   ├── questions/
│   │   │   ├── teacher_access/
│   │   │   ├── dashboard/
│   │   │   └── chapter/
│   │   │       ├── notes/
│   │   │       ├── upload/
│   │   │       ├── notebook/
│   │   │       └── community/
│   │   ├── services/          # AI, RAG, Qdrant, document processing
│   │   ├── utils/             # Helper functions
│   │   └── main.py            # FastAPI application
│   ├── firebase/
│   │   └── secrets/           # Firebase credentials
│   ├── supabase_migrations/   # Database schema
│   ├── scripts/               # Utility scripts
│   ├── tests/                 # Test files
│   ├── requirements.txt
│   └── README.md
│
└── frontend/
    ├── src/
    │   ├── components/        # Reusable UI components
    │   │   ├── common/
    │   │   ├── layout/
    │   │   └── ui/            # shadcn/ui components
    │   ├── tasks/             # Feature-specific components
    │   │   ├── auth/
    │   │   ├── classroom/
    │   │   ├── subject/
    │   │   ├── chapter/
    │   │   ├── dashboard/
    │   │   └── teacher-access/
    │   ├── contexts/          # React contexts
    │   ├── hooks/             # Custom React hooks
    │   ├── lib/               # Utilities and API clients
    │   └── types/             # TypeScript type definitions
    ├── configs/               # Build and lint configs
    ├── package.json
    └── README.md
```

---

## 🧪 Development

### Backend Development

```bash
cd backend

# Run with auto-reload
uvicorn app.main:app --reload

# Access API docs
# http://localhost:8000/docs (Swagger UI)
# http://localhost:8000/redoc (ReDoc)
```

### Frontend Development

```bash
cd frontend

# Development server
npm run dev

# Type checking
npm run lint

# Build for production
npm run build

# Preview production build
npm run preview
```

### Adding New Features

#### Backend

1. Create module in `app/modules/`
2. Define Pydantic schemas
3. Implement service logic
4. Create routes with permission checks
5. Register router in `main.py`

#### Frontend

1. Add types in `src/types/`
2. Create API functions in `src/lib/api/`
3. Build components in `src/tasks/[feature]/`
4. Update routing in `src/App.tsx`

---

## 🚢 Deployment

### Backend Deployment

EduNexus backend can be deployed to:
- **Vercel** (serverless functions)
- **AWS Lambda** + API Gateway
- **Google Cloud Run**
- **Azure App Service**
- **Docker** (container-based hosting)

**Pre-deployment checklist:**
1. Setup production Supabase instance
2. Setup production Qdrant instance (Qdrant Cloud recommended)
3. Configure production environment variables
4. Run database migrations
5. Create Supabase storage bucket

### Frontend Deployment

The frontend is optimized for deployment to:
- **Vercel** (recommended)
- **Netlify**
- **AWS Amplify**
- **GitHub Pages**

```bash
cd frontend
npm run build
# Deploy the dist/ folder to your hosting platform
```

---

## 📊 Database Schema

Key tables in the Supabase Postgres database:

- **users**: User profiles (students & teachers)
- **classrooms**: Classroom definitions
- **classroom_members**: Student enrollments
- **subjects**: Subjects within classrooms
- **teacher_access**: Teacher-to-subject assignments
- **chapters**: Chapters within subjects
- **notes**: Uploaded notes with approval status
- **questions**: Student Q&A
- **announcements**: Subject-level announcements

For full schema details, see `backend/supabase_migrations/migrations/`

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License.

---

## 🙏 Acknowledgments

- **shadcn/ui** for the beautiful UI components
- **Firebase** for authentication services
- **Supabase** for the database and storage infrastructure
- **Google Gemini** for AI capabilities
- **Qdrant** for vector search functionality
- **FastAPI** for the robust backend framework

---

## 📧 Support

For questions or support, please open an issue on GitHub.

---

**Built with ❤️ for educators and learners everywhere**
