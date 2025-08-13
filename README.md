# Chatty - Real-time Chat Application

A modern, full-stack real-time chat application built with React, Node.js, Socket.IO, and MongoDB. Features include user authentication, real-time messaging, image sharing, online status tracking, and multiple theme options.

## 🚀 Features

### Core Features
- **Real-time Messaging**: Instant message delivery using Socket.IO
- **User Authentication**: Secure signup/login with JWT tokens
- **Image Sharing**: Upload and share images in conversations
- **Online Status**: See who's online in real-time
- **Profile Management**: Update profile pictures and view account information
- **Theme Customization**: 32+ beautiful themes powered by DaisyUI
- **Responsive Design**: Works seamlessly on desktop and mobile devices

### Security Features
- **JWT Authentication**: Secure token-based authentication
- **Password Hashing**: Bcrypt for secure password storage
- **HTTP-only Cookies**: Secure token storage
- **CORS Protection**: Configured for secure cross-origin requests
- **Input Validation**: Server-side validation for all inputs

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **Socket.IO** - Real-time communication
- **MongoDB** - Database
- **Mongoose** - MongoDB object modeling
- **JWT** - Authentication tokens
- **Bcrypt.js** - Password hashing
- **Cloudinary** - Image storage and management
- **Cookie-parser** - Cookie handling
- **CORS** - Cross-origin resource sharing
- **Dotenv** - Environment variable management

### Frontend
- **React 18** - UI library
- **Vite** - Build tool and development server
- **React Router DOM** - Client-side routing
- **Zustand** - State management
- **Axios** - HTTP client
- **Socket.IO Client** - Real-time communication
- **Tailwind CSS** - Utility-first CSS framework
- **DaisyUI** - Tailwind CSS components
- **Lucide React** - Icon library
- **React Hot Toast** - Toast notifications

## 📁 Project Structure

```
chat-app/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   │   ├── auth.controller.js      # Authentication logic
│   │   │   └── message.controller.js   # Message handling logic
│   │   ├── lib/
│   │   │   ├── cloudinary.js          # Cloudinary configuration
│   │   │   ├── db.js                  # MongoDB connection
│   │   │   ├── socket.js              # Socket.IO setup
│   │   │   └── utils.js               # JWT utilities
│   │   ├── middleware/
│   │   │   └── auth.middleware.js     # Authentication middleware
│   │   ├── models/
│   │   │   ├── message.model.js       # Message schema
│   │   │   └── user.model.js          # User schema
│   │   ├── routes/
│   │   │   ├── auth.route.js          # Authentication routes
│   │   │   └── message.route.js       # Message routes
│   │   ├── seeds/
│   │   │   └── user.seed.js           # Database seeding
│   │   └── index.js                   # Server entry point
│   ├── package.json
│   └── package-lock.json
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── skeletons/
│   │   │   │   ├── MessageSkeleton.jsx
│   │   │   │   └── SidebarSkeleton.jsx
│   │   │   ├── AuthImagePattern.jsx   # Auth page decoration
│   │   │   ├── ChatContainer.jsx      # Main chat interface
│   │   │   ├── ChatHeader.jsx         # Chat header with user info
│   │   │   ├── MessageInput.jsx       # Message input component
│   │   │   ├── Navbar.jsx             # Navigation bar
│   │   │   ├── NoChatSelected.jsx     # Empty state component
│   │   │   └── Sidebar.jsx            # User list sidebar
│   │   ├── constants/
│   │   │   └── index.js               # Theme constants
│   │   ├── lib/
│   │   │   ├── axios.js               # Axios configuration
│   │   │   └── utils.js               # Utility functions
│   │   ├── pages/
│   │   │   ├── HomePage.jsx           # Main chat page
│   │   │   ├── LoginPage.jsx          # Login page
│   │   │   ├── ProfilePage.jsx        # User profile page
│   │   │   ├── SettingsPage.jsx       # Theme settings page
│   │   │   └── SignUpPage.jsx         # Registration page
│   │   ├── store/
│   │   │   ├── useAuthStore.js        # Authentication state
│   │   │   ├── useChatStore.js        # Chat state management
│   │   │   └── useThemeStore.js       # Theme state
│   │   ├── App.jsx                    # Main app component
│   │   ├── index.css                  # Global styles
│   │   └── main.jsx                   # React entry point
│   ├── public/
│   │   ├── avatar.png                 # Default avatar
│   │   ├── screenshot-for-readme.png  # App screenshot
│   │   └── vite.svg                   # Vite logo
│   ├── eslint.config.js               # ESLint configuration
│   ├── index.html                     # HTML template
│   ├── package.json
│   ├── package-lock.json
│   ├── postcss.config.js              # PostCSS configuration
│   ├── tailwind.config.js             # Tailwind configuration
│   └── vite.config.js                 # Vite configuration
├── .gitignore
└── package.json                       # Root package.json
```

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or cloud instance)
- Cloudinary account (for image uploads)

### Environment Variables

Create a `.env` file in the `backend` directory:

```env
PORT=5001
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
NODE_ENV=development
```

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd chat-app
   ```

2. **Install dependencies**
   ```bash
   # Install root dependencies
   npm install
   
   # Install backend dependencies
   cd backend
   npm install
   
   # Install frontend dependencies
   cd ../frontend
   npm install
   ```

3. **Seed the database (optional)**
   ```bash
   cd backend
   node src/seeds/user.seed.js
   ```

4. **Start the application**
   ```bash
   # From root directory - builds and starts backend
   npm run build
   npm start
   
   # Or run in development mode
   # Backend (from backend directory)
   npm run dev
   
   # Frontend (from frontend directory)
   npm run dev
   ```

## 📊 Database Schema

### User Model
```javascript
{
  email: String (required, unique),
  fullName: String (required),
  password: String (required, minlength: 6),
  profilePic: String (default: ""),
  createdAt: Date,
  updatedAt: Date
}
```

### Message Model
```javascript
{
  senderId: ObjectId (ref: User, required),
  receiverId: ObjectId (ref: User, required),
  text: String,
  image: String,
  createdAt: Date,
  updatedAt: Date
}
```

## 🔌 API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /signup` - User registration
- `POST /login` - User login
- `POST /logout` - User logout
- `PUT /update-profile` - Update user profile (protected)
- `GET /check` - Check authentication status (protected)

### Message Routes (`/api/messages`)
- `GET /users` - Get all users for sidebar (protected)
- `GET /:id` - Get messages with specific user (protected)
- `POST /send/:id` - Send message to specific user (protected)

## 🎨 Available Themes

The application supports 32+ themes through DaisyUI:
- light, dark, cupcake, bumblebee, emerald, corporate
- synthwave, retro, cyberpunk, valentine, halloween
- garden, forest, aqua, lofi, pastel, fantasy
- wireframe, black, luxury, dracula, cmyk, autumn
- business, acid, lemonade, night, coffee, winter
- dim, nord, sunset

## 🔄 Real-time Features

### Socket.IO Events
- **Connection Management**: Automatic connection/disconnection handling
- **Online Users**: Real-time online user tracking
- **Message Broadcasting**: Instant message delivery
- **User Status**: Online/offline status updates

### State Management
- **Zustand Stores**: Lightweight state management
  - `useAuthStore`: Authentication state and socket connection
  - `useChatStore`: Chat messages and user management
  - `useThemeStore`: Theme persistence and switching

## 🛡️ Security Implementation

### Authentication Flow
1. User registers/logs in with credentials
2. Server validates and creates JWT token
3. Token stored in HTTP-only cookie
4. Protected routes verify token via middleware
5. Socket connection authenticated with user ID

### Password Security
- Passwords hashed using bcrypt with salt rounds
- Minimum 6 character requirement
- Server-side validation for all inputs

### Image Upload Security
- Cloudinary integration for secure image storage
- Base64 image processing and validation
- File type restrictions for image uploads

## 🎯 Key Features Implementation

### Real-time Messaging
- Socket.IO for bidirectional communication
- Message persistence in MongoDB
- Real-time message delivery and status updates
- Image sharing with Cloudinary integration

### User Experience
- Responsive design with Tailwind CSS
- Loading states and skeleton components
- Toast notifications for user feedback
- Theme customization with live preview

### Performance Optimizations
- Vite for fast development and building
- Code splitting and lazy loading
- Optimized image handling
- Efficient state management with Zustand

## 🚀 Deployment

### Production Build
```bash
# Build frontend
npm run build

# Start production server
npm start
```

### Environment Configuration
- Set `NODE_ENV=production`
- Configure production MongoDB URI
- Set up Cloudinary for production
- Configure CORS for production domain

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📝 License

This project is licensed under the ISC License.

## 🔮 Future Enhancements

- Group chat functionality
- Message reactions and replies
- File sharing (documents, videos)
- Voice and video calling
- Message encryption
- Push notifications
- Mobile app development
- Advanced user roles and permissions

---

**Built with ❤️ using modern web technologies**