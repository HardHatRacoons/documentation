# Pages Documentation

## 1. File: `BPView.jsx`

### Purpose
- Displays a PDF viewer alongside a control panel for annotated PDFs.

### Key Components
- **PDFViewer**: Renders the PDF document using the URL from context.
- **BPViewControlPanel**: Displays controls relevant to the PDF.
- **useOutletContext**: Retrieves context data (like PDF URLs, page number, and setter).

### Structure
- Selects the annotated PDF if available, otherwise falls back to the unannotated version.
- Layout uses Flexbox for a side-by-side view of the PDF and control panel.
- The container has styling for padding, border radius, color themes (light/dark), and spacing.
- Page number and navigation state are handled outside and passed into the viewer.

---

## 2. File: `Home.jsx`

### Purpose
- Serves as the dashboard for managing file uploads, deletions, and viewing annotated/unannotated files.

### Purpose
- Displays the main gallery page where users can upload, search, view, and delete blueprint files.

### Key Components
- **LoginNavbar**: Header with user and theme options.
- **FileList**: Lists uploaded files with thumbnails and delete buttons.
- **UploadModal**: Modal for uploading new PDFs.
- **DeleteConfirmationModal**: Modal to confirm file deletion.

### Structure
- Uses local state for modals, selected file, search query, and refresh triggers.
- Includes a search bar with clear functionality.
- Handles Amplify `remove` calls to delete associated files.
- Uses `useUser()` and `useOutletContext()` for user and theme context.

---

## 3. File: `LoginPage.jsx`

### Purpose
- Provides a login screen with Google authentication via AWS Amplify.

### Key Components
- **signInWithRedirect**: Starts the Google sign-in process.
- **signOut**: Logs out any existing user.
- **FcGoogle**: Google icon used in the login button.

### Structure
- Fullscreen layout with centered login card.
- Calls `signOut` if a user is already logged in before attempting a new login.
- Button styled with hover effects and icon + label combo.

---

## 4. File: `MetricView.jsx`

### Purpose
- Displays a dynamic dashboard of graphs representing metrics extracted from an annotated PDF.

### Key Components
- **Card**: Container for each graph with pinning functionality.
- **fetchJSONData**: Loads data from CSV and JSON sources.
- **graph()**: Generates visualizations for each metric.
- **useOutletContext**: Provides access to current PDF data.

### Structure
- Pinned graph layout is saved and restored via `localStorage`.
- Graphs re-render when data changes.
- Responsive grid using CSS and Framer Motion for animation.
- Uses unique graph options and types per card.

---

## 5. File: `NoPage.jsx`

### Purpose
- Renders a fallback page for unmatched routes.

### Key Components
- **useNavigate**: React Router hook to redirect to the homepage.

### Structure
- Minimal layout with text and a click-to-return prompt.
- Includes dark mode text styling.

---

## 6. File: `TableView.jsx`

### Purpose
- Shows raw PDF annotation data in an interactive data grid (AG Grid).

### Key Components
- **AgGridReact**: Renders the table using AG Grid.
- **fetchJSONData**: Fetches JSON-formatted CSV data.
- **useOutletContext**: Provides access to current PDF data.

### Structure
- Column definitions include filters, sorting, and custom formatting.
- Uses `useMemo` and `useEffect` to manage data and layout behavior.
- Responsive layout with dark mode support.
- Row selection and auto-sizing enabled.
