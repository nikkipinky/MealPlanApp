# Meal Planner Application

## Overview
The Meal Planner Application allows users to create personalized meal plans by searching and adding meals from the Spoonacular API. Users can register, authenticate, and manage their weekly meal plans through a user-friendly interface. This full-stack application is built using:

- **Backend**: Node.js with Express.js
- **Database**: MongoDB with Mongoose.js
- **Frontend**: Svelte.js

The application interacts with the Spoonacular API to provide meal search functionality and supports user authentication via JSON Web Tokens (JWT).

---

## Features

- **User Authentication**:
  - User registration and login.
  - JWT-based authentication and authorization.

- **Meal Search & Planning**:
  - Search for meals using the Spoonacular API.
  - Filter meals based on dietary preferences (e.g., Keto, Vegan, Gluten-Free).
  - Create and manage weekly meal plans (up to 3 meals per week).

- **User Management**:
  - Store user profiles with dietary preferences.
  - Secure password handling using bcrypt.

- **Responsive Frontend**:
  - Intuitive Svelte.js-based UI for easy navigation.
  - Display meal images, dietary labels, and more.

---

## Technologies Used

### Backend:
- Node.js
- Express.js
- MongoDB with Mongoose
- JSON Web Tokens (JWT)
- Bcrypt for password hashing

### Frontend:
- Svelte.js
- CSS (with Tailwind for styling)

### External API:
- Spoonacular API (for meal search and dietary filters)

---

## Data Models

### User Model
```javascript
{
  _id: ObjectId,          // Unique identifier for each user
  username: String,       // Unique, case-insensitive username
  password: String,       // Hashed password
  preferences: [String]   // Array of dietary preferences (e.g., Keto, Vegan)
}
```

### Meal Plan Model
```javascript
{
  _id: ObjectId,          // Unique identifier for each meal plan
  user_id: ObjectId,      // Reference to the user's _id
  week: Number,           // Week number for the meal plan
  meals: [
    {
      meal_id: Number,    // Unique ID from the Spoonacular API
      name: String,       // Meal name
      diets: [String],    // Dietary labels (e.g., Vegan, Gluten-Free)
      image: String       // Image URL from the Spoonacular API
    }
  ]
}
```

---

## Setup and Installation

### Prerequisites
- Node.js (v18+ recommended)
- MongoDB (running locally or via a cloud provider)

### Clone the Repository
```bash
git clone https://github.com/yourusername/meal-planner-app.git
cd meal-planner-app
```

### Backend Setup
1. Navigate to the `server` folder:
```bash
cd server
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file and add:
```
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
SPOONACULAR_API_KEY=your_spoonacular_api_key
```

4. Start the backend server:
```bash
npm start
```

### Frontend Setup
1. Navigate to the `client` folder:
```bash
cd client
```

2. Install dependencies:
```bash
npm install
```

3. Start the frontend development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`.

---

## API Endpoints

### Authentication
- `POST /api/auth/register`: Register a new user.
- `POST /api/auth/login`: Authenticate a user and return a JWT.

### Users
- `GET /api/users/profile`: Get the authenticated user's profile.

### Meal Plans
- `POST /api/mealplans`: Create a new meal plan.
- `GET /api/mealplans`: Retrieve all meal plans for the authenticated user.
- `GET /api/mealplans/:id`: Retrieve a specific meal plan.
- `DELETE /api/mealplans/:id`: Delete a meal plan.

### Spoonacular Integration
- `GET /api/meals/search?query=<keyword>&diet=<diet>`: Search for meals using Spoonacular API.

---

## Interaction with Spoonacular API

The application integrates with the Spoonacular API for meal search and dietary filtering. Users can search for recipes by keywords and apply filters based on dietary preferences.

- [Spoonacular API Documentation](https://spoonacular.com/food-api)

Example API call to search for meals:
```bash
GET https://api.spoonacular.com/recipes/complexSearch?query=pasta&diet=vegan&apiKey=YOUR_API_KEY
```

---


## Acknowledgments

- Spoonacular API for providing meal data.
- Node.js, Express.js, MongoDB, and Svelte.js communities for their excellent frameworks.
