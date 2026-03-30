# AI-Powered Web App Builder

An innovative full-stack web application that leverages Google's Gemini AI to generate code and help users build web applications visually. Users can authenticate, create projects, and use an interactive code editor powered by AI to generate HTML, CSS, and JavaScript code with a live preview.

## Features

- **User Authentication**: Secure sign-up and login with JWT-based authentication
- **Project Management**: Create, view, and manage multiple web app projects
- **AI Code Generation**: Generate code using Google's Gemini AI with customizable prompts
- **Live Code Editor**: Interactive code editor with syntax highlighting
- **Live Preview**: Real-time preview of HTML, CSS, and JavaScript changes
- **Project Dashboard**: View all user projects with quick access to editors
- **Protected Routes**: Authentication-based access control for private pages
- **Responsive Design**: Mobile-friendly user interface

## Tech Stack

### Frontend
- **React 19** - UI library
- **Vite** - Build tool and dev server
- **React Router 7** - Client-side routing
- **Axios** - HTTP client
- **CSS** - Styling

### Backend
- **Node.js** - Runtime environment
- **Express 5** - Web framework
- **MongoDB** - Database (via Mongoose ODM)
- **Google Generative AI** - AI code generation
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **CORS** - Cross-origin resource sharing

## Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or cloud instance via MongoDB Atlas)
- Google Gemini API key
- npm or yarn package manager

## Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd ai_powered_web_app_builder
```

### 2. Install Server Dependencies
```bash
cd server
npm install
```

### 3. Install Client Dependencies
```bash
cd ../client
npm install
```

## Environment Variables

### Server (.env in `/server` directory)
Create a `.env` file in the server directory with the following variables:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ai-web-builder
# OR for MongoDB Atlas:
# MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/ai-web-builder

GEMINI_API_KEY=your-google-gemini-api-key
JWT_SECRET=your-jwt-secret-key
CLIENT_URL=http://localhost:5173
```

### Client (.env in `/client` directory - Optional)
Create a `.env` file in the client directory:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

## Running the Application

### Development Mode

#### Terminal 1 - Start the Backend Server
```bash
cd server
npm run dev
```
The server will start on `http://localhost:5000`

#### Terminal 2 - Start the Frontend Development Server
```bash
cd client
npm run dev
```
The client will be available at `http://localhost:5173`

### Production Build

#### Build Frontend
```bash
cd client
npm run build
npm run preview
```

#### Start Server
```bash
cd server
npm start
```

## Project Structure

```
ai_powered_web_app_builder/
├── client/                          # React frontend
│   ├── src/
│   │   ├── components/             # Reusable React components
│   │   │   ├── ChatInput.jsx       # User input for chat/prompts
│   │   │   ├── ChatMessage.jsx     # Display chat messages
│   │   │   ├── CodeEditor.jsx      # Code editor component
│   │   │   ├── FeatureCard.jsx     # Feature showcase cards
│   │   │   ├── LivePreview.jsx     # Real-time code preview
│   │   │   ├── Navbar.jsx          # Navigation bar
│   │   │   ├── ProjectCard.jsx     # Project list cards
│   │   │   └── ProtectedRoute.jsx  # Auth-protected routes
│   │   ├── context/                # React Context for state
│   │   │   ├── AuthContext.jsx     # Authentication state
│   │   │   └── ToastContext.jsx    # Toast notifications
│   │   ├── pages/                  # Page components
│   │   │   ├── LandingPage.jsx     # Landing/home page
│   │   │   ├── LoginPage.jsx       # Login page
│   │   │   ├── DashboardPage.jsx   # User dashboard
│   │   │   └── BuilderPage.jsx     # Code builder interface
│   │   ├── services/               # API service modules
│   │   │   ├── api.js              # Axios instance config
│   │   │   ├── authService.js      # Auth API calls
│   │   │   ├── generationService.js# AI generation API calls
│   │   │   └── projectService.js   # Project API calls
│   │   ├── styles/                 # CSS files
│   │   ├── App.jsx                 # Main app component
│   │   └── main.jsx                # React entry point
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
└── server/                          # Express backend
    ├── src/
    │   ├── config/                 # Configuration files
    │   │   ├── db.config.js        # MongoDB connection
    │   │   └── gemini.config.js    # Gemini API setup
    │   ├── constants/
    │   │   └── prompts.js          # AI prompt templates
    │   ├── controllers/            # Route handlers
    │   │   ├── auth.controller.js  # Auth logic
    │   │   ├── generation.controller.js # AI generation logic
    │   │   └── project.controller.js  # Project CRUD logic
    │   ├── middleware/
    │   │   ├── auth.middleware.js  # JWT verification
    │   │   └── error.middleware.js # Error handling
    │   ├── models/                 # MongoDB schemas
    │   │   ├── User.model.js       # User schema
    │   │   └── Project.model.js    # Project schema
    │   ├── routes/                 # API routes
    │   │   ├── auth.routes.js      # Auth endpoints
    │   │   ├── generation.routes.js# Generation endpoints
    │   │   ├── project.routes.js   # Project endpoints
    │   │   └── index.js            # Route aggregator
    │   ├── services/               # Business logic
    │   │   ├── auth.service.js     # Auth service
    │   │   ├── gemini.service.js   # Gemini API wrapper
    │   │   ├── generation.service.js# Code generation logic
    │   │   └── project.service.js  # Project operations
    │   ├── utils/                  # Utility functions
    │   │   ├── code.utils.js       # Code utilities
    │   │   └── jwt.utils.js        # JWT utilities
    │   └── app.js                  # Express app config
    ├── server.js                   # Entry point
    └── package.json
```

## API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /register` - Register a new user
- `POST /login` - Login user
- `POST /logout` - Logout user
- `GET /me` - Get current user info

### Project Routes (`/api/projects`)
- `GET /` - Get all user projects
- `POST /` - Create a new project
- `GET /:id` - Get project details
- `PUT /:id` - Update project
- `DELETE /:id` - Delete project

### Generation Routes (`/api/generate`)
- `POST /code` - Generate code using Gemini AI
- `POST /enhance` - Enhance existing code

## Usage Guide

### Getting Started
1. Navigate to the landing page and click "Get Started"
2. Sign up with your email and password
3. Log in to access your dashboard

### Creating a Project
1. Click "Create New Project" on the dashboard
2. Enter a project name and click "Create"
3. You'll be redirected to the builder interface

### Using the Code Builder
1. Enter your requirements or prompt in the chat input
2. Click "Generate" to let Gemini AI generate code
3. Review the generated HTML, CSS, and JavaScript
4. Edit the code directly in the code editor
5. See changes in real-time in the live preview panel

### Saving Changes
1. Projects are automatically saved
2. Access your projects anytime from the dashboard

## Key Technologies Explained

### Google Gemini AI
The application uses Google's Gemini API to generate responsive, modern web code based on user prompts. The AI understands user requirements and produces clean, production-ready code.

### JWT Authentication
Secure token-based authentication ensures only authorized users can access their projects and generate code.

### MongoDB
Projects and user data are stored in MongoDB, providing flexible document storage and easy scalability.

### Live Preview
The live preview component uses an iframe to safely render and display HTML, CSS, and JavaScript changes in real-time.

## Common Issues & Troubleshooting

### "Cannot connect to MongoDB"
- Ensure MongoDB is running locally or your MongoDB Atlas connection string is correct
- Check that `MONGODB_URI` is set correctly in `.env`

### "Gemini API Key Error"
- Verify your `GEMINI_API_KEY` is valid and active
- Check that the API key has sufficient quota

### CORS Errors
- Ensure `CLIENT_URL` in server `.env` matches your frontend URL
- Verify the client is making requests to the correct API base URL

### Port Already in Use
- Change the `PORT` in server `.env` to an available port
- Or kill the process using the port

## Future Enhancements

- Export projects as downloadable files
- Collaboration features for team projects
- Code version history and rollback
- Additional AI models support
- Template library
- Community showcase

## License

ISC

## Support

For issues or questions, please open an issue in the repository or contact the development team.

---

**Built with ❤️ using React, Express, MongoDB, and Google Gemini AI**
