# 📚 BookNest

A modern full-stack e-commerce bookstore application built with the MERN stack (MongoDB, Express.js, React, Node.js). BookNest provides a seamless shopping experience for book lovers with features like user authentication, shopping cart, and real-time inventory management.

![BookNest Dashboard](images/dashboard.png)

## ✨ Features

- 🔐 **User Authentication** - Secure login and registration using Firebase Authentication
- 📖 **Browse Books** - Explore a curated collection of books with detailed information
- 🛒 **Shopping Cart** - Add books to cart and manage quantities
- 💳 **Checkout System** - Secure checkout process with order management
- 🔍 **Book Details** - View comprehensive information about each book
- 📱 **Responsive Design** - Beautiful UI built with React and Tailwind CSS
- 🔄 **Real-time Updates** - State management with Redux Toolkit
- 📊 **Admin Features** - Manage book inventory (add, edit, delete books)
- 🌟 **Trending Books** - Showcase popular and recommended titles
- 📰 **News Section** - Stay updated with book-related news

![Authentication](images/auth.png)

## 🚀 Tech Stack

### Frontend

- **React 19** - Modern UI library
- **Vite** - Fast build tool and dev server
- **Redux Toolkit** - State management with RTK Query for API calls
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Firebase** - Authentication service
- **Swiper** - Modern carousel/slider
- **SweetAlert2** - Beautiful alerts
- **React Hook Form** - Form validation

### Backend

- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variable management

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **MongoDB** (local installation or MongoDB Atlas account)
- **Firebase** account (for authentication)

## 🛠️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/JasonAlva/BookNest.git
cd BookNest
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file
# Add the following variables:
```

Create a `.env` file in the `backend` directory:

```env
# MongoDB Connection
DB_URL=mongodb+srv://username:password@cluster.mongodb.net/booknest
# Or for local MongoDB:
# DB_URL=mongodb://localhost:27017/booknest

# Server Port
PORT=5000
```

**MongoDB Atlas Setup:**

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster (free tier available)
3. Create a database user
4. Get your connection string from "Connect" → "Connect your application"
5. Replace `<username>`, `<password>`, and database name in the connection string

### 3. Frontend Setup

```bash
# Navigate to frontend directory
cd ../frontend

# Install dependencies
npm install

# Create .env file
```

Create a `.env` file in the `frontend` directory:

```env
# Firebase Configuration
VITE_APIKEY=your-firebase-api-key
VITE_Auth_Domain=your-project-id.firebaseapp.com
VITE_PROJECT_ID=your-project-id
VITE_STORAGE_BUCKET=your-project-id.appspot.com
VITE_MESSAGING_SENDERID=your-messaging-sender-id
VITE_APP_ID=your-app-id
```

**Firebase Setup:**

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project
3. Enable Authentication → Email/Password sign-in method
4. Go to Project Settings → General → Your apps
5. Add a web app and copy the configuration values
6. Paste the values into your `.env` file

### 4. Running the Application

You'll need **two terminal windows**:

**Terminal 1 - Start Backend Server:**

```bash
cd backend
npm run start:dev
```

The backend will run on `http://localhost:5000`

**Terminal 2 - Start Frontend Development Server:**

```bash
cd frontend
npm run dev
```

The frontend will run on `http://localhost:5173`

Visit `http://localhost:5173` in your browser to see the application!

## 📁 Project Structure

```
BookNest/
├── backend/
│   ├── src/
│   │   ├── books/
│   │   │   ├── book.Controller.js    # Book CRUD operations
│   │   │   ├── book.route.js         # Book API routes
│   │   │   └── bookModel.js          # Book schema
│   │   └── orders/
│   │       └── order.model.js        # Order schema
│   ├── index.js                      # Server entry point
│   ├── package.json
│   └── .env                          # Environment variables
│
├── frontend/
│   ├── src/
│   │   ├── components/               # Reusable components
│   │   │   ├── NavBar.jsx
│   │   │   ├── Footer.jsx
│   │   │   ├── Login.jsx
│   │   │   └── Register.jsx
│   │   ├── pages/                    # Page components
│   │   │   ├── home/
│   │   │   │   ├── Home.jsx
│   │   │   │   ├── Banner.jsx
│   │   │   │   ├── TopSellers.jsx
│   │   │   │   └── Recommendation.jsx
│   │   │   └── Books/
│   │   │       ├── BookCard.jsx
│   │   │       ├── SingleBook.jsx
│   │   │       ├── CartPage.jsx
│   │   │       └── Checkout.jsx
│   │   ├── redux/                    # State management
│   │   │   ├── store.js
│   │   │   └── features/
│   │   │       ├── Books/bookApi.js
│   │   │       └── cart/cartSlice.js
│   │   ├── routers/                  # Routing configuration
│   │   │   ├── router.jsx
│   │   │   └── PrivateRoute.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx       # Authentication context
│   │   ├── firebase/
│   │   │   └── firebase.config.js    # Firebase setup
│   │   └── utils/
│   │       ├── baseURL.js            # API base URL
│   │       └── getImgUrl.js          # Image helper
│   ├── public/
│   │   └── books.json                # Sample book data
│   ├── package.json
│   └── .env                          # Environment variables
│
└── images/                           # Screenshots for README
```

## 🔌 API Endpoints

### Books

| Method | Endpoint                 | Description       |
| ------ | ------------------------ | ----------------- |
| GET    | `/api/books/`            | Get all books     |
| GET    | `/api/books/:id`         | Get book by ID    |
| POST   | `/api/books/create-book` | Create a new book |
| PUT    | `/api/books/edit/:id`    | Update book by ID |
| DELETE | `/api/books/:id`         | Delete book by ID |

### Example API Request

```javascript
// Get all books
fetch("http://localhost:5000/api/books/")
  .then((response) => response.json())
  .then((data) => console.log(data));

// Create a new book
fetch("http://localhost:5000/api/books/create-book", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "The Great Gatsby",
    description: "A classic American novel",
    category: "Fiction",
    trending: true,
    coverImage: "https://example.com/image.jpg",
    oldPrice: 20,
    newPrice: 15,
  }),
});
```

## 🎨 Usage Examples

### Adding a Book to Cart

```jsx
import { useDispatch } from "react-redux";
import { addToCart } from "./redux/features/cart/cartSlice";

function BookCard({ book }) {
  const dispatch = useDispatch();

  const handleAddToCart = () => {
    dispatch(addToCart(book));
  };

  return <button onClick={handleAddToCart}>Add to Cart</button>;
}
```

### Protected Routes

```jsx
import PrivateRoute from "./routers/PrivateRoute";

<Route
  path="/checkout"
  element={
    <PrivateRoute>
      <Checkout />
    </PrivateRoute>
  }
/>;
```

## 🐛 Troubleshooting

### MongoDB Connection Issues

**Problem:** `MongooseError: The 'uri' parameter to 'openUri()' must be a string`

**Solution:** Make sure your `.env` file exists in the backend directory and contains a valid `DB_URL`.

**Problem:** `MongoServerError: bad auth : authentication failed`

**Solution:**

- Verify your MongoDB Atlas username and password are correct
- Check that the database user has proper permissions
- URL-encode special characters in your password (e.g., `@` → `%40`)

### Firebase Authentication Issues

**Problem:** `Firebase: Error (auth/invalid-api-key)`

**Solution:**

- Ensure your `.env` file exists in the frontend directory
- Verify all Firebase configuration values are correct
- Restart the Vite dev server after changing `.env` files

### Port Already in Use

**Problem:** `Error: listen EADDRINUSE: address already in use :::5000`

**Solution:**

- Kill the process using the port or change the `PORT` in backend `.env`
- On Windows: `netstat -ano | findstr :5000` then `taskkill /PID <PID> /F`

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please ensure your code follows the existing style and includes appropriate tests.

## 📝 Available Scripts

### Backend

```bash
npm start          # Start production server
npm run start:dev  # Start development server with nodemon
```

### Frontend

```bash
npm run dev        # Start development server
npm run build      # Build for production
npm run preview    # Preview production build
npm run lint       # Run ESLint
```

## 📄 License

This project is licensed under the ISC License.

## 👥 Author

**Jason Alva**

- GitHub: [@JasonAlva](https://github.com/JasonAlva)

## 🙏 Acknowledgments

- Firebase for authentication services
- MongoDB Atlas for database hosting
- Tailwind CSS for the beautiful UI components
- The MERN stack community for excellent documentation

## 📞 Support

If you have any questions or run into issues:

1. Check the [Troubleshooting](#-troubleshooting) section above
2. Search existing [GitHub Issues](https://github.com/JasonAlva/BookNest/issues)
3. Create a new issue with detailed information about your problem

---

Made with ❤️ by Jason Alva
