
# Dynamic Post Page with OG Image Generation

## Overview

This application allows users to create a dynamic post page using React. The app generates an Open Graph (OG) image based on the post content and uploads it to Firebase Storage. The generated image includes the post's title, content snippet, and an optional image, and it is used to enhance social media previews.

## Features

1. **Dynamic Post Page**: Users can enter a title, content, and an optional image to generate a post.
2. **OG Image Generation**: Generates a 1200x630 pixels OG image that visually represents the post content.
3. **Firebase Integration**: Uploads the generated OG image to Firebase Storage and provides a shareable URL.

## Technology Stack

- **Frontend**: React
- **Backend**: Firebase
- **Image Processing**: `html-to-image` library for generating images from HTML
- **Storage**: Firebase Storage

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-repo/ogImageGenerator.git
cd ogImageGenerator
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up Firebase

1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Create a new project or use an existing one.
3. Navigate to **Storage** and get your bucket name (e.g., `your-project-id.appspot.com`).
4. Go to **Project Settings** and find your Firebase configuration.

### 4. Configure Firebase

Create a `src/firebase.js` file and add the following code, replacing the placeholders with your Firebase configuration:

```javascript
import { initializeApp } from 'firebase/app';
import { getStorage } from 'firebase/storage';

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID",
};

const app = initializeApp(firebaseConfig);
const storage = getStorage(app);

export { storage };
```

## Application Structure

- **`src/App.js`**: Main application component that includes the PostPage and generates the OG image.
- **`src/components/PostPage.js`**: Component for creating a post with title, content, and image.
- **`src/components/MetaTags.js`**: Component for setting meta tags for the OG image.
- **`src/utils/generateOgImage.js`**: Utility function to generate the OG image from HTML.
- **`src/utils/uploadToFirebase.js`**: Utility function to upload the generated image to Firebase Storage.
- **`src/firebase.js`**: Firebase configuration and initialization.

## Functions

### `generateOgImage()`

Generates an image from the post content and returns a base64 data URL.

### `uploadToFirebase(base64Image)`

Uploads the base64 image to Firebase Storage and returns the public URL of the uploaded image.

### `MetaTags({ imageUrl })`

Sets the meta tags for the page, including the OG image URL.

## Error Handling

### Common Errors

- **403 Forbidden**: Check Firebase Storage rules and CORS configuration.
- **Command Not Found**: Ensure `gcloud` is installed and properly configured in your PATH.

## Contribution

To contribute to this project, please fork the repository and create a pull request with your changes. For any issues or feature requests, please open an issue on the GitHub repository.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to adjust the documentation according to your project's specific needs and details.
