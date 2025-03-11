# main and App.jsx

## Overview
This ReactJS application is structured to use AWS Amplify for backend services, React Router for routing, and Context API for state management. It includes protected routes and a context for theme management.

---

## File: `main.jsx`

### Purpose
This file is the entry point of the React application. It configures AWS Amplify, sets up routing, and provides context for user and theme management.

### Key Imports
- Amplify from `aws-amplify`: Configures AWS backend.  
- BrowserRouter from `react-router`: Enables client-side routing.  
- UserProvider from `./components/UserContext`: Provides user state context.  
- App from `./App`: Main application component.  
- ThemeContext from `react`: Provides a theme context (light/dark).  

### Amplify Configuration
Initializes AWS Amplify with configurations from `amplify_outputs.json`.
```javascript
Amplify.configure(outputs);
```

### Context and Rendering
```javascript
createRoot(document.getElementById('root')).render(
    <ThemeContext.Provider value="dark">
        <UserProvider>
            <BrowserRouter>
                <App />
            </BrowserRouter>
        </UserProvider>
    </ThemeContext.Provider>,
);
```

- Wraps the entire app with `ThemeContext` and `UserProvider` for global state management.  
- BrowserRouter enables client-side routing.  
- The App component is rendered as the root of the application.

---

## File: `App.jsx`

### Purpose
Defines the main routing structure for the application using `react-router`.

### Routes Structure

- **Root Layout (`/`)**  
  - **Home Page (`/`)**  
    - Protected route that renders the `Home` component.  
  - **Login Page (`/login`)**  
    - Public route for user login, rendering the `LoginPage` component.  
  - **File Layout (`/file/:id`)**  
    - Protected route with nested routes for viewing specific file data.  
    - **Blueprint View (`/file/:id/blueprint`)**  
    - **Table View (`/file/:id/table`)**  
    - **Metrics View (`/file/:id/metrics`)**  
  - **No Page (`*`)**  
    - Catches all undefined routes and renders the `NoPage` component.  

### Sample Code
```javascript
<Routes>
    <Route path="/" element={<RootLayout />}>
        <Route
            index
            element={
                <ProtectedRoute>
                    <Home />
                </ProtectedRoute>
            }
        />
        <Route path="login" element={<LoginPage />} />
        <Route
            path="file/:id"
            element={
                <ProtectedRoute>
                    <FileLayout />
                </ProtectedRoute>
            }
        >
            <Route path="blueprint" element={<BPView />} />
            <Route path="table" element={<TableView />} />
            <Route path="metrics" element={<MetricView />} />
        </Route>
        <Route path="*" element={<NoPage />} />
    </Route>
</Routes>
```

### ProtectedRoute
- Ensures that certain routes are accessible only to authenticated users.

### Nested Routes
- The `/file/:id` path has nested routes that render specific views depending on the URL.

---

## Contexts

- **ThemeContext**: Manages the current theme of the application (default is set to `dark`).  
- **UserProvider**: Provides the user context throughout the application for authentication and state management.  

---

## Amplify

- Configured using the `amplify_outputs.json` file.  
- Can be extended for services like authentication, storage, and API integration.

---

## Styling

- Imports global styles from `./index.css`.

---

## Notes

- Uncomment the `ConsoleLogger` import and related code in `main.jsx` for debugging Amplify issues.  
- Ensure that the `amplify_outputs.json` file is correctly configured for your AWS resources.

---