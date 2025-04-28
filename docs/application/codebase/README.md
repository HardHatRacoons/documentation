# Frontend Code Documentation
Click on the file name that you would like documentation for.

---

## 📂 [`src/`](/application/codebase/main+App.md)

📄 [`App.jsx`](/application/codebase/main+App?id=file-appjsx) - Defines the main routing structure for the application using `react-router`.

📄 [`main.jsx`](/application/codebase/main+App?id=file-mainjsx) - Entry point for the React application. Configures AWS Amplify, sets up routing, and provides context for user and theme management.

---

## 📂 [`layouts/`](/application/codebase/layouts.md)

📄 [`FileLayout.jsx`](/application/codebase/layouts?id=_1-file-filelayoutjsx) - Manages layout and navigation for viewing individual files with tab navigation and AWS S3 integration.

📄 [`RootLayout.jsx`](/application/codebase/layouts?id=_2-file-rootlayoutjsx) - Provides a basic layout wrapper for the entire application with consistent styling.

---

## 📂 [`pages/`](/application/codebase/pages.md)

📄 [`BPView.jsx`](/application/codebase/pages?id=_1-file-bpviewjsx) - Displays a PDF viewer alongside a control panel for annotated PDFs.

📄 [`Home.jsx`](/application/codebase/pages?id=_2-file-homejsx) - Dashboard for managing file uploads, deletions, and viewing annotated/unannotated files.

📄 [`LoginPage.jsx`](/application/codebase/pages?id=_3-file-loginpagejsx) - Provides a Google sign-in button to authenticate users.

📄 [`MetricView.jsx`](/application/codebase/pages?id=_4-file-metricviewjsx) - Displays a grid of metric cards that users can pin or reorder.

📄 [`NoPage.jsx`](/application/codebase/pages?id=_5-file-nopagejsx) - Displays an error message for undefined routes and provides navigation back to the home page.

📄 [`TableView.jsx`](/application/codebase/pages?id=_6-file-tableviewjsx) - Displays tabular data using the `ag-Grid` library.

---

## 📂 [`components/`](/application/codebase/components.md)

📄 [`BPViewControlPanel.jsx`](/application/codebase/components?id=_1-file-bpviewcontrolpaneljsx) - Provides controls for downloading annotated, unannotated, and CSV versions of PDF files.

📄 [`Card.jsx`](/application/codebase/components?id=_2-file-cardjsx) - Represents a selectable card component that can be pinned or unpinned.

📄 [`FileList.jsx`](/application/codebase/components?id=_3-file-filelistjsx) - Displays a responsive grid of user-uploaded files, including thumbnails and delete actions.

📄 [`GoogleSignOut.jsx`](/application/codebase/components?id=_4-file-googlesignoutjsx) - Handles user sign-out functionality.

📄 [`Grapher.js`](/application/codebase/components?id=_5-file-grapherjs) - Generates various types of graphs (bar, histogram, pie, text-based) using D3.js to visualize data from PDF annotations.

📄 [`JsonFetch.js`](/application/codebase/components?id=_6-file-jsonfetchjs) - Handles loading and caching of CSV annotation data.

📄 [`LoginNavbar.jsx`](/application/codebase/components?id=_7-file-loginnavbarjsx) - Renders the top navigation bar

📄 [`Paginator.jsx`](/application/codebase/components?id=_8-file-paginatorjsx) - Manages pagination for navigating through multiple pages of content.

📄 [`PDFViewer.jsx`](/application/codebase/components?id=_9-file-pdfviewerjsx) - Displays PDF files with support for pagination and annotation interaction.

📄 [`ProtectedRoute.jsx`](/application/codebase/components?id=_10-file-protectedroutejsx) - Protects routes by ensuring only authenticated users can access them.

📄 [`Tabs.jsx`](/application/codebase/components?id=_11-file-tabsjsx) - Provides tabbed navigation for switching between different views or sections.

📄 [`Toggle.jsx`](/application/codebase/components?id=_12-file-togglejsx) - Displays a simple toggle switch with animated movement.

📄 [`UserContext.jsx`](/application/codebase/components?id=_13-file-usercontextjsx) - Manages and provides user attribute context across the application.

## 📂 [`components/modals`](/application/codebase/modals.md)

📄 [`UploadModal.jsx`](/application/codebase/modals?id=file-uploadmodaljsx) - Modal that allows users to upload PDF files.

📄 [`DeleteConfirmationModal.jsx`](/application/codebase/modals?id=file-deleteconfirmationmodaljsx) - Prompts the user to confirm deletion of a selected file
