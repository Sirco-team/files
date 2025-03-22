# Dynamic Multi-Tool Dashboard

## Overview
The Dynamic Multi-Tool Dashboard is a flexible and powerful web-based tool that supports multiple functionalities:
1. **Login System**: User authentication using either embedded credentials or an external `credentials.txt` file.
2. **Dynamic Content Display**: Choose between:
   - Embedding content using an iframe.
   - Dynamically fetching raw HTML from a GitHub URL.
   - Displaying custom HTML defined within the tool.
3. **Robust Error Handling**: Provides clear feedback for missing configurations, invalid credentials, and user input errors.
4. **Checksum Validation**: Ensures the integrity of the HTML file before executing. This feature can be toggled on or off for flexibility.

---

## Features

| **Feature**                     | **How It Works**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Login System**                | Requires users to log in using a valid `username:password` combination stored in credentials.    |
| **Embedded vs. External Credentials** | Supports embedded credentials within the HTML or dynamic fetching of an external `credentials.txt` file.|
| **Iframe Embedding**            | Displays external content in an iframe, using a configured URL.                                 |
| **GitHub Content Fetching**     | Dynamically retrieves raw HTML from a GitHub URL and renders it on the page.                    |
| **Custom HTML**                 | Displays pre-defined HTML content for custom use cases.                                         |
| **Error Handling**              | Provides detailed error messages for incorrect login, empty fields, or missing configurations.  |
| **Checksum Validation**         | Validates the integrity of the HTML file before execution. Can be enabled or disabled.          |

---

## Configuration Instructions

### 1. Credentials Type
The type of credentials used can be configured with the `useEmbeddedCredentials` variable:
- **Set to `"true"`**: Use embedded credentials stored in the `embeddedCredentials` object.
- **Set to `"false"`**: Use an external `credentials.txt` file fetched from the URL specified in `credentialsUrl`.

Example Configuration:
```javascript
const credentialsUrl = "https://example.com/credentials.txt"; // URL for external credentials
let useEmbeddedCredentials = "false"; // Use external credentials
```
```javascript
const credentialsUrl = ""; // No URL needed for embedded credentials
let useEmbeddedCredentials = "true"; // Use embedded credentials

const embeddedCredentials = {
    "admin": "1234",
    "user": "password123"
};
```

---

### 2. Display Modes
Set the `displayOption` variable to define how the content will be displayed after login:
- **"iframe"**: Embed external content using an iframe.
- **"github"**: Fetch and render raw HTML from a GitHub URL.
- **"custom"**: Display custom HTML defined in `customHtmlContent`.

Example Configuration:
```javascript
let displayOption = "iframe"; // Embed iframe content
```

---

### 3. Checksum Validation
The `enableChecksum` variable controls whether checksum validation is applied:
- **Set to `true`**: Enables checksum validation to ensure HTML file integrity.
- **Set to `false`**: Disables checksum validation.

Example Configuration:
```javascript
const enableChecksum = true;
```

---

## credentials.txt File
The `credentials.txt` file stores `username:password` pairs for external credential validation. Lines starting with `//` are treated as comments and ignored.

### Example credentials.txt
```
// Admin credentials
admin:1234

// User credentials
user:password123

// Notes: Add credentials below this line.
```

---

## Error Handling

| **Error Type**                  | **Description**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| Missing `useEmbeddedCredentials`| Displays an error if this variable is not explicitly set to `"true"` or `"false"`.             |
| Missing Credentials File        | Alerts the user if the `credentials.txt` file is not found or cannot be fetched.               |
| Incorrect Login                 | Displays a clear "Access Denied" message for invalid credentials.                              |
| Empty Fields                    | Prompts the user to fill in both the username and password fields.                             |
| Missing `displayOption`         | Alerts the user if no display mode is configured.                                              |
| Missing URL                     | Displays an error if the `iframeUrl` or `gitHubEmbedUrl` is not configured.                    |

---

## Side-by-Side Explanation

### HTML Elements

| **HTML Section**                | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `<head>`                        | Includes all necessary CSS styles and JavaScript functions for the dashboard.                  |
| `<div id="popup">...</div>`      | Houses the login form for user authentication.                                                  |
| `<div id="accessMessage">...</div>` | Displays a success message once login credentials are validated.                                |
| `<div id="errorMessage">...</div>` | Shows an error message for invalid login attempts.                                              |
| `<div id="fileErrorMessage">...</div>` | Displays an error message if the `credentials.txt` file is missing or inaccessible.            |

---

### JavaScript Functions

| **Function**                    | **What It Does**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| `verifyNameAndCode()`           | Validates the entered username and password against the configured credentials.                 |
| `validateCredentials()`         | Checks user input against embedded or external credentials and grants/denies access.           |
| `showAccessGranted()`           | Displays the success message and triggers the content-loading process.                         |
| `checksumValidation()`          | Verifies the integrity of the HTML file and proceeds to load content.                          |
| `handleEmbedOption()`           | Determines which display mode to activate and loads the appropriate content.                   |
| `fetchGitHubContent()`          | Dynamically fetches and renders raw HTML content from a GitHub URL.                            |
| `showMessage()`                 | Displays error or success messages dynamically.                                                |

---

### CSS

| **CSS Rule**                    | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `iframe { ... }`                | Styles the iframe for full-page embedding of external content.                                 |
| `#popup { ... }`                | Centers the login form with a fullscreen modal overlay.                                        |
| `input, button { ... }`         | Adds consistent styling to input fields and buttons.                                           |
| `#accessMessage, #errorMessage, ...` | Styles all dynamic messages, such as success, error, and empty field alerts.                  |

---

## Example Usage
1. Set `useEmbeddedCredentials` to `"true"` or `"false"`.
2. Configure the `credentialsUrl` or `embeddedCredentials` based on your choice.
3. Set the `displayOption` to `"iframe"`, `"github"`, or `"custom"`.
4. Optionally, toggle `enableChecksum` to enable or disable checksum validation.
5. Deploy and use the tool for dynamic content loading after successful user authentication.

---
