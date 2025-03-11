# ReactJS Components Documentation

## 1. File: `BPViewControlPanel.jsx`

### Purpose
- Provides a control panel for downloading annotated, unannotated, and CSV versions of PDF files.

### Key Components
- **LuDownload, BsFiletypePdf, BsFiletypeCsv**: Icons representing the download options.
- **Download Links**: 
  - Annotated PDF.
  - Annotated CSV data.
  - Original unannotated PDF.

### Core Features
- Displays download options for PDF and CSV files.
- Styled with Tailwind CSS for a consistent look.
- Hover effects to improve user interaction.

---

## 2. File: `Card.jsx`

### Purpose
- Represents a selectable card component that can be pinned or unpinned.

### Key Components
- **TbPin, TbPinFilled**: Icons to indicate pinned and unpinned states.
- **onChange**: Function to propagate the pinning status to the parent component.

### Core Features
- Cards toggle between pinned and unpinned states upon clicking.
- Visual feedback is provided through icons.
- Flexible design to accommodate dynamic content through `children`.

---

## 3. File: `GoogleSignOut.jsx`

### Purpose
- Handles user sign-out functionality.

### Key Components
- **signOut**: Function from AWS Amplify to sign out the user.
- **IoMdExit**: Icon indicating the sign-out action.

### Core Features
- Provides a button to log out users.
- Displays success and error messages in the console.
- Styled for intuitive user interaction.

---

## 4. File: `Paginator.jsx`

### Purpose
- Manages pagination for navigating through multiple pages of content.

### Key Components
- **FaAngleLeft, FaAngleRight**: Icons for previous and next page buttons.
- **Input Field**: Allows manual entry of the page number.

### Core Features
- Users can navigate pages using buttons or by manually entering a page number.
- Prevents invalid page numbers from being set.
- Invokes the `onChange` callback when the page number is updated.

---

## 5. File: `PDFViewer.jsx`

### Purpose
- Displays PDF files with support for pagination and annotation interaction.

### Key Components
- **Paginator**: Integrated for navigating between PDF pages.
- **pdfjs**: Library for rendering PDF content.

### Core Features
- Dynamically loads and renders PDF pages based on user interaction.
- Handles mouse tracking for potential annotation interactions.
- Rescales content on container resize events.
- Utilizes a debounced resize observer for optimized performance.

---

## 6. File `ProtectedRoute.jsx`

### Purpose
- Protects routes by ensuring only authenticated users can access them.

### Key Components
- **getCurrentUser**: Checks if a user is authenticated.
- **Navigate**: Redirects unauthorized users to the login page.

### Core Features
- Displays a loading message while authentication status is determined.
- Redirects unauthenticated users to the login page.
- Renders the desired component for authenticated users.

---

## 7. File `Tabs.jsx`

### Purpose
- Provides tabbed navigation for switching between different views or sections.

### Key Components
- **onChange**: Callback triggered when a tab is selected.
- **Dynamic Styling**: Highlights the active tab.

### Core Features
- Dynamically generates tabs based on the provided list.
- Applies styles to indicate the active tab.
- Supports flexible customization via props.

---

## 8. File `UserContext.jsx`

### Purpose
- Manages and provides user attribute context across the application.

### Key Components
- **UserContext**: React context for sharing user data.
- **UserProvider**: Wraps the application and fetches user attributes.
- **useUser**: Custom hook to access user context.

### Core Features
- Fetches and maintains user attributes using AWS Amplify.
- Makes user data available to the entire component tree.
- Provides a simple hook (`useUser`) for accessing user information.
