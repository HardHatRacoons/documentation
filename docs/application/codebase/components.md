# ReactJS Components Documentation

## 1. File: `BPViewControlPanel.jsx`

### Purpose
Displays a collapsible side panel with download options for blueprint files: the annotated PDF, associated CSV data, and original unannotated PDF.

### Key Components
- **Download Buttons**: Links to annotated and original files.
- **Mobile Toggle Button**: Collapses/expands the panel on small screens.
- **Spinner Icon**: Shown when the annotated PDF is still processing.

### Structure
- On mobile: hidden by default, toggled via a button.
- On desktop: always visible.
- Uses Tailwind for layout, transitions, and dark mode styling.

---

## 2. File: `Card.jsx`

### Purpose
Renders a stylized card container that can be pinned or unpinned via an icon.

### Key Components
- **Pin Button**: Toggles a visual pinned state.
- **Children Rendering**: Any content can be placed inside the card.

### Structure
- Flexbox layout with top padding for the pin button and bottom space for content.
- Supports dark and light themes via utility classes.

---

## 3. File: `FileList.jsx`

### Purpose
Displays a responsive grid of user-uploaded files, including thumbnails and delete actions. Supports search filtering and file preview navigation.

### Key Components
- **AWS Amplify Storage**: Lists, fetches metadata, and loads thumbnail previews.
- **Local Caching**: Stores fetched file info in `localStorage`.
- **Delete Button**: Opens delete confirmation modal.
- **Search Query**: Filters results based on user input.

### Structure
- Fetches files from S3 using `list`, `getProperties`, and `getUrl`.
- Dynamically filters and sorts files by name.
- Displays placeholder images when thumbnails aren't available.

---

## 4. File: `GoogleSignOut.jsx`

### Purpose
Renders a sign-out button that logs out users from Google OAuth via AWS Amplify.

### Key Components
- **signOut** from `aws-amplify/auth`: Triggers logout.
- **IoMdExit**: Exit icon next to the label.

### Structure
- Styled button with icon and text.
- Uses `onClick` async handler for graceful sign-out.

---

## 5. File: `Grapher.js`

### Purpose
Generates various types of graphs (bar, histogram, pie, text-based) using D3.js to visualize data from PDF annotations.

### Key Components
- **graph()**: Dispatcher that routes to the appropriate chart generator.
- **generateBarGraph()**: Creates a D3 bar chart with configurable options.
- **generateHistogram()**: Creates a histogram with customizable bins.
- **generatePieGraph()**: Renders a pie chart grouped by categories.
- **generateText()**: Displays numeric summaries like totals and averages.

### Structure
- Each graph function accepts a container, dataset, and options.
- Color and styling are adjusted based on the active theme.
- Tooltips and axis labels enhance interactivity and readability.

---

## 6. File: `JsonFetch.js`

### Purpose
Handles loading and caching of CSV annotation data. Converts CSV to JSON if necessary, then uploads the JSON to S3 and uses it going forward.

### Key Components
- **fetchJSONData()**: Main function that attempts to load a JSON file from S3. If not found, falls back to CSV.
- **fetchCsvData()**: Helper that fetches and parses CSV data, then uploads the result as JSON.

### Structure
- Uses D3.js for parsing.
- Uploads parsed JSON to `jsonPath` for future efficiency.
- Integrates with AWS Amplify Storage via `getUrl` and `uploadData`.

---

## 7 File: `LoginNavbar.jsx`

### Purpose
Renders the top navigation bar, displaying a greeting, theme toggle, and sign-out functionality.

### Key Components
- **User Greeting**: Displays user name from `userAttributes`.
- **Theme Toggle**: Switches between light and dark modes.
- **GoogleSignOut**: Button to log the user out.

### Structure
- Uses iconography to indicate current theme.
- Controlled via `themeController` prop containing `[theme, setTheme]`.
- Responsive and styled using Tailwind CSS.

---

## 8. File: `Paginator.jsx`

### Purpose
Provides pagination controls for navigating between pages, such as in a PDF viewer.

### Key Components
- **Previous / Next Buttons**: Navigates to the previous or next page within bounds.
- **Page Input**: Allows direct page number input and updates on valid change.

### Structure
- Maintains local page state and triggers `onChange` callback when changed.
- Prevents overflow or underflow of page numbers.
- Uses icons for intuitive navigation and inline styling with Tailwind.

---

## 9. File: `PDFViewer.jsx`

### Purpose
Renders a PDF file inside a canvas element with responsive scaling and pagination.

### Key Components
- **Paginator**: Component used to switch between pages.
- **ResizeObserver**: Detects and responds to container resizing.
- **pdf.js**: Handles PDF rendering and scale calculations.

### Structure
- Uses `useEffect` to fetch and render the appropriate page on change.
- Calculates a dynamic scale to fit the viewer container.
- Prepared for annotation interaction via `calculateCollision` (not yet implemented).

---

## 10. File `ProtectedRoute.jsx`

### Purpose
Wraps protected routes to ensure only authenticated users can access them.

### Key Components
- **getCurrentUser**: Verifies whether a user is logged in via AWS Amplify.
- **Navigate**: Redirects unauthenticated users to the login page.

### Structure
- Displays "Loading..." while authentication status is being checked.
- Uses a boolean state (`isAuthenticated`) to control route access.

---

## 11. File `Tabs.jsx`

### Purpose
Renders a horizontal tab interface for switching between different views or panels.

### Key Components
- **Tab Titles**: Rendered dynamically from an array.
- **onChange / setActiveTab**: Triggered when a tab is selected.

### Structure
- Uses `reduce()` to determine the longest word for layout consistency.
- Highlights active tab and supports additional styling via `className` prop.
- Styled with Tailwind and responsive to dark mode.

---

## 12. File `Toggle.jsx`

### Purpose
Displays a simple toggle switch (e.g., for theme toggling) with animated movement.

### Key Components
- **onChange**: Callback triggered when the toggle is flipped.
- **initialValue**: Initial toggle state provided via props.

### Structure
- Uses `useState` to control local toggle state.
- Smooth transitions and accessibility handled through ARIA and Tailwind classes.

## 13. File `UserContext.jsx`

### Purpose
Provides authenticated user attributes across the app using React Context.

### Key Components
- **UserProvider**: Fetches user attributes using Amplify and shares them via context.
- **useUser()**: Custom hook to access the current user's attributes.

### Structure
- Fetches user attributes on mount using `fetchUserAttributes`.
- Handles absence of user without throwing errors.
- Wraps children components with context access.
