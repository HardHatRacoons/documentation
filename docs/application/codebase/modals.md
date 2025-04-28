# Modals Documentation

## File: `UploadModal.jsx`

### Purpose
Displays a modal that allows users to upload PDF files. The modal handles file processing, converts the first page of the PDF into an image using `pdf.js`, uploads both the image and file to AWS S3, and then sends a processing request to an API endpoint.

### Key Components
- **FileUploader** from `@aws-amplify/ui-react-storage`: UI component for handling file uploads.
- **convertPdfToImage()**: Converts the first page of the uploaded PDF to a PNG image blob.
- **processFile()**: Handles hashing, conversion, and upload logic.
- **AWS Amplify**: Used for uploading data to S3 (`uploadData`).
- **useNavigate**: Redirects user to file view after successful upload.

### Structure
- Generates a SHA-1 hash of the file to use as a unique key.
- Converts PDF to image and uploads both to S3.
- Posts metadata to an API endpoint for further processing.
- After upload, binds click handlers to file name elements to allow navigation to the file view.
- Modal visibility controlled by the `isOpen` prop.
- Uses dark overlay and centered modal UI for consistent UX.

### Example Usage
```jsx
<UploadModal
    userAttributes={user}
    isOpen={isUploadOpen}
    onClose={() => setUploadOpen(false)}
/>
```

## File: `DeleteConfirmationModal.jsx`

### Purpose
Renders a modal that prompts the user to confirm deletion of a selected file. It displays a confirmation message and provides Cancel/Delete buttons.

### Key Components
- **Modal Layout**: Centered confirmation box with darkened background overlay.
- **Confirm Button**: Triggers `onConfirm` callback to perform deletion.
- **Cancel Button**: Triggers `onClose` callback to dismiss modal.

### Structure
- Simple conditional render: returns `null` if `isOpen` is `false`.
- Displays file name in confirmation text.
- Includes ARIA labels for accessibility on buttons.
- Buttons are styled with hover effects and color-coded for clarity (e.g., red for delete).

### Example Usage
```jsx
<DeleteConfirmationModal
    isOpen={isDeleteModalOpen}
    onClose={() => setIsDeleteModalOpen(false)}
    onConfirm={handleDelete}
    fileName={selectedFile?.fileName}
/>
```