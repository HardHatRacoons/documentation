# Frontend Code Documentation
Click on the file name that you would like documentation for.

---

## 📂 [`src/`](/application/codebase/main+App.md)

📄 [`main.jsx`](/application/codebase/main+App?id=file-mainjsx) - Entry point for the React application. Configures AWS Amplify, sets up routing, and provides context for user and theme management.

📄 [`App.jsx`](/application/codebase/main+App?id=file-appjsx) - Defines the main routing structure for the application using `react-router`.

---

## 📂 [`layouts/`](/application/codebase/layouts.md)

📄 [`RootLayout.jsx`](/application/codebase/layouts?id=_2-file-rootlayoutjsx) - Provides a basic layout wrapper for the entire application with consistent styling.

📄 [`FileLayout.jsx`](/application/codebase/layouts?id=_1-file-filelayoutjsx) - Manages layout and navigation for viewing individual files with tab navigation and AWS S3 integration.

---

## 📂 [`pages/`](/application/codebase/pages.md)

📄 [`Home.jsx`](/application/codebase/pages?id=_2-file-homejsx) - Dashboard for managing file uploads, deletions, and viewing annotated/unannotated files.

📄 [`LoginPage.jsx`](/application/codebase/pages?id=_3-file-loginpagejsx) - Provides a Google sign-in button to authenticate users.

📄 [`BPView.jsx`](/application/codebase/pages?id=_1-file-bpviewjsx) - Displays a PDF viewer alongside a control panel for annotated PDFs.

📄 [`TableView.jsx`](/application/codebase/pages?id=_6-file-tableviewjsx) - Displays tabular data using the `ag-Grid` library.

📄 [`MetricView.jsx`](/application/codebase/pages?id=_4-file-metricviewjsx) - Displays a grid of metric cards that users can pin or reorder.

📄 [`NoPage.jsx`](/application/codebase/pages?id=_5-file-nopagejsx) - Displays an error message for undefined routes and provides navigation back to the home page.

---

## 📂 [`components/`](/application/codebase/components.md)

📄 [`BPViewControlPanel.jsx`](/application/codebase/components?id=_1-file-bpviewcontrolpaneljsx) - Provides controls for downloading annotated, unannotated, and CSV versions of PDF files.

📄 [`Card.jsx`](/application/codebase/components?id=_2-file-cardjsx) - Represents a selectable card component that can be pinned or unpinned.

📄 [`GoogleSignOut.jsx`](/application/codebase/components?id=_3-file-googlesignoutjsx) - Handles user sign-out functionality.

📄 [`Paginator.jsx`](/application/codebase/components?id=_4-file-paginatorjsx) - Manages pagination for navigating through multiple pages of content.

📄 [`PDFViewer.jsx`](/application/codebase/components?id=_5-file-pdfviewerjsx) - Displays PDF files with support for pagination and annotation interaction.

📄 [`ProtectedRoute.jsx`](/application/codebase/components?id=_6-file-protectedroutejsx) - Protects routes by ensuring only authenticated users can access them.

📄 [`Tabs.jsx`](/application/codebase/components?id=_7-file-tabsjsx) - Provides tabbed navigation for switching between different views or sections.

📄 [`UserContext.jsx`](/application/codebase/components?id=_8-file-usercontextjsx) - Manages and provides user attribute context across the application.
