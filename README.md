# Blog App

A full-stack MERN blog application with separate backend and frontend projects. The app supports user and author roles, authentication, article creation, editing, soft delete/restore, article comments, and image upload via Cloudinary.

## Project Structure

- `blog backend/` - Express + MongoDB backend
- `blog frontend/` - React + Vite frontend

## Features

- Role-based authentication for `USER`, `AUTHOR`, and `ADMIN`
- User registration and login
- Author registration and profile creation with profile image upload
- Create, edit, delete, and restore articles for authors
- Browse and read active articles for users
- View article details with author info and comments
- Post comments on articles as authenticated users
- Protected routes in React using role-based access control
- Backend cookie-based auth for secure session handling
- Cloudinary image upload support for profile images

## Backend

### Technologies

- Node.js
- Express
- MongoDB / Mongoose
- JSON Web Tokens
- bcryptjs
- dotenv
- multer
- Cloudinary
- cookie-parser
- nodemon

### Start Backend

1. Open `blog backend/`
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file with at least:

```env
DB_URL=<your-mongodb-connection-string>
FRONTEND_URL=http://localhost:5173
PORT=4000
NODE_ENV=development
```

4. Run the backend:

```bash
npm run dev
```

The server listens on `http://localhost:4000` by default.

### Backend API Routes

- `POST /common-api/login` - login and set auth cookie
- `GET /common-api/logout` - clear auth cookie
- `GET /common-api/check-auth` - verify current user session
- `POST /user-api/users` - register a new user
- `GET /user-api/articles` - list active articles for users
- `GET /user-api/article/:id` - get article details
- `POST /user-api/comment/:articleId` - add comment to an article
- `POST /author-api/users` - register a new author
- `GET /author-api/articles/:authorId` - list author articles
- `POST /author-api/article` - create a new article
- `GET /author-api/article/:id` - get author article
- `PUT /author-api/article/:id` - update an article
- `DELETE /author-api/article/:id` - soft delete an article
- `PUT /author-api/article/:id/restore` - restore a deleted article

## Frontend

### Technologies

- React
- Vite
- React Router
- Zustand
- Axios
- React Hook Form
- React Hot Toast
- Tailwind CSS

### Start Frontend

1. Open `blog frontend/`
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file with:

```env
VITE_API_BASE_URL=https://blog-application-qlfs.onrender.com
```

4. Run the frontend:

```bash
npm run dev
```

The app runs by default on `https://blog-application-gb7e.vercel.app/`.

## Available Pages

- `/` - Home page with article listings for users
- `/register` - Registration page for users/authors
- `/login` - Login page
- `/user-profile` - User dashboard (protected)
- `/author-profile` - Author dashboard (protected)
- `/author-profile/articles` - Author articles list
- `/author-profile/write-article` - Create new article
- `/article/:id` - Article detail page
- `/edit-article/:id` - Edit article page (author only)

## Notes

- The frontend uses a centralized `apiClient` for API calls with `axios` and cookies enabled.
- `ProtectedRoute` enforces authentication and role-based access before allowing route access.
- The backend uses an Express middleware to allow cross-origin requests from allowed frontend origins.

## License

This project is provided as-is for learning and development purposes.
