# Layout Documentation

## 1. File: `FileLayout.jsx`

### Purpose
- Manages the layout and navigation for viewing and interacting with individual files.
- Provides tab-based navigation for different file views like blueprint, table, and metrics.

### Key Components
- **Tabs**: Renders navigation tabs for switching between views (blueprint, table, metrics).
- **MdArrowBack**: Provides a button to navigate back to the home page.
- **useOutletContext**: Passes the PDF information context to child components.
- **useParams**: Retrieves parameters from the URL (such as the file ID).
- **getUrl** and **getProperties** from `aws-amplify/storage`: Fetch URLs and metadata for PDF and CSV files stored in AWS.

### Core Features
- **Tab Navigation**: Allows users to switch between different file views using tabs.
- **AWS S3 Integration**:  
  - Fetches URLs for annotated and unannotated PDFs, and associated CSV files.  
  - Validates the existence of files in the storage.
- **Dynamic Page Titles**: Displays the file name dynamically based on AWS metadata.
- **Conditional Rendering**:  
  - Displays a loading state while fetching data.  
  - Handles invalid file states gracefully by displaying error messages.
- **Navigation Logic**:  
  - Automatically redirects to the first tab (blueprint) if no specific tab is specified.  
  - Allows users to navigate back to the home page with a back button.

---

## 2. File: `RootLayout.jsx`

### Purpose
- Provides a basic layout wrapper for the entire application.
- Ensures consistent layout and styling across the application.

### Key Components
- **Outlet**: Used to render child routes dynamically.
- **Authenticator**: Although not used explicitly here, this layout can integrate authentication for protected routes.

### Core Features
- **Consistent Layout**: Ensures all pages maintain a consistent background and full-screen height.
- **Theme Initialization**:  
  - Initializes the theme based on localStorage or system preference.  
  - Saves updated theme value to localStorage when changed.
- **Outlet Integration**: Dynamically renders nested child components based on routing.  
  - Passes `[theme, setTheme]` context down to allow child components to react to theme changes.