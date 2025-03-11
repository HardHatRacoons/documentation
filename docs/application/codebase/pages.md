# Pages Documentation

## 1. File: `BPView.jsx`

### Purpose
- Displays a PDF viewer alongside a control panel for annotated PDFs.

### Key Components
- **PDFViewer**: Renders the PDF document using the URL from context.
- **BPViewControlPanel**: Displays controls relevant to the PDF.
- **useOutletContext**: Retrieves context data (like PDF URLs).

### Structure
- Layout uses Flexbox for a side-by-side view of PDF and controls.
- The container has styling for borders, padding, and spacing.

---

## 2. File: `Home.jsx`

### Purpose
- Serves as the dashboard for managing file uploads, deletions, and viewing annotated/unannotated files.

### Key Components
- **LoginNavbar**: Displays a welcome message and sign-out option.
- **UploadModal**: Modal component for uploading PDF files.
- **DeleteConfirmationModal**: Confirms file deletion with a modal.
- **FileList**: Lists uploaded files with options to delete or view.
- **GoogleSignOut**: Handles user sign-out.

### Core Features
- Upload and delete PDF files in both "annotated" and "unannotated" folders.
- Uses AWS Amplify for file storage and management.
- UI built with Tailwind CSS for responsive design.
- Provides visual feedback during file uploads and deletions.

---

## 3. File: `LoginPage.jsx`

### Purpose
- Provides a Google sign-in button to authenticate users.

### Key Components
- **signInWithRedirect**: Initiates Google sign-in.
- **signOut**: Logs out existing users.
- **useUser**: Retrieves user context.

### Core Features
- Displays a centered login form with Google sign-in functionality.
- Button styling is consistent with app theme using Tailwind CSS.

---

## 4. File: `MetricView.jsx`

### Purpose
- Displays a grid of metric cards that users can pin or reorder.

### Key Components
- **Card**: Custom component to display metric information.
- **onPin**: Function to handle pinning/unpinning of metrics.

### Core Features
- Metrics can be pinned to appear first in the display.
- Grid layout for a consistent and organized appearance.
- Uses Tailwind CSS for styling and spacing.

---

## 5. File: `NoPage.jsx`

### Purpose
- Displays an error message when a user navigates to an undefined route.

### Key Components
- **useNavigate**: Provides navigation to other routes.

### Core Features
- Displays a message indicating the page does not exist.
- Includes a clickable text to navigate back to the home page.

---

## 6. File: `TableView.jsx`

### Purpose
- Displays data in a table format using the `ag-Grid` library.

### Key Components
- **AgGridReact**: React wrapper for the ag-Grid table.
- **rowData**: The data to be displayed in the table.
- **colDefs**: Defines the structure and behavior of table columns.
- **rowSelection**: Configuration for row selection (multi-row selection enabled).

### Core Features
- Displays a customizable and sortable table of data.
- Supports multi-row selection with pagination.
- Utilizes memoization for optimized performance.
- Conditional value formatting for specific columns.
