### Updated README.md: Dynamic Multi-Tool & Raw GitHub Content Loader

# Dynamic Multi-Tool & Raw GitHub Content Loader

## Overview
This repository contains two tools designed for dynamic and seamless content embedding:
1. **Dynamic Multi-Tool HTML**: A versatile dashboard capable of handling iframe embedding, GitHub content fetching, and custom HTML displays.
2. **Raw GitHub Content Loader HTML**: A standalone HTML file for dynamically loading raw GitHub content.

Both tools have a checksum feature for validation, which can be toggled on or off. Additionally, the `credentials.txt` file now supports comments for improved manageability.

---

## Dynamic Multi-Tool HTML

### Key Features
| **Feature**                     | **How It Works**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Login System**                | Requires users to authenticate using credentials stored in the `credentials.txt` file.           |
| **Iframe Embedding**            | Displays external URLs in an iframe.                                                            |
| **GitHub Content Fetching**     | Dynamically fetches and embeds raw HTML content from a GitHub URL.                              |
| **Custom HTML Display**         | Displays pre-defined custom HTML, allowing for easy manual customization.                       |
| **Checksum Validation**         | Ensures the file's integrity is verified before execution; can be toggled on/off.               |
| **Comments in `credentials.txt`** | Lines starting with `//` are ignored, allowing you to document and manage credentials.           |
| **Error Handling**              | Provides alerts for missing credentials, misconfigured display options, or fetch failures.      |

---

### Dynamic Multi-Tool: Side-by-Side Explanation

#### HTML Elements
| **HTML Section**                | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `<head>`                        | Includes CSS styling and JavaScript functions to control the functionality of the tool.         |
| `<div id="popup">...</div>`      | Houses the login form for user authentication.                                                  |
| `<div id="accessMessage">...</div>` | Displays a success message once login credentials are verified.                                 |
| `<div id="errorMessage">...</div>` | Displays an error message for incorrect login credentials.                                      |
| `<div id="fileErrorMessage">...</div>` | Displays an error message if the `credentials.txt` file cannot be fetched.                     |

#### JavaScript Functions
| **Function**                    | **What It Does**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| `verifyNameAndCode()`           | Reads and validates the username and password against the fetched `credentials.txt` file.         |
| `checksumValidation()`          | Ensures the integrity of the HTML file before loading content. Can be disabled if necessary.      |
| `handleEmbedOption()`           | Determines which display mode to activate (`iframe`, `github`, or `custom`) and loads it.        |
| `fetchGitHubContent(url)`       | Fetches and embeds raw HTML content from the provided GitHub URL.                                |

---

#### `credentials.txt` File
| **Format**                      | **Explanation**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| `username:password`             | Each line represents a username-password pair for login.                                         |
| `//`                            | Any line starting with `//` is treated as a comment and ignored during validation.               |

#### Example `credentials.txt`
```
// Admin credentials
admin:1234

// Test account credentials
testuser:password123

// Notes: The above credentials are for testing only.
```

---

## Raw GitHub Content Loader HTML

### Key Features
| **Feature**                     | **How It Works**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Dynamic Content Fetching**    | Automatically fetches and displays raw HTML content from a GitHub URL.                          |
| **Error Handling**              | Provides descriptive error messages for missing or invalid GitHub URLs.                         |
| **Live Updates**                | Always displays the latest version of the raw GitHub content without requiring manual updates.   |
| **Minimal Design**              | Designed with simplicity and clarity in mind for easy usage.                                     |

---

### Raw GitHub Content Loader: Side-by-Side Explanation

#### HTML Elements
| **HTML Section**                | **Purpose**                                                                                     |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| `<head>`                        | Includes the required JavaScript for fetching and displaying GitHub content.                   |
| `<body>`                        | Displays loading and error messages during the content-fetching process.                       |
| `<p id="loadingMessage">...</p>` | Shows a message indicating content is being loaded from GitHub.                                 |
| `<p id="errorMessage">...</p>`   | Displays errors dynamically if the content fetch fails.                                         |

---

### How the Tools Work Together
Both tools are designed to handle dynamic content embedding, but they serve slightly different purposes:
1. **Dynamic Multi-Tool HTML**: Ideal for integrating multiple content-display modes in one location.
2. **Raw GitHub Content Loader HTML**: Optimized for seamlessly pulling and displaying raw HTML content from GitHub repositories.

---

### Configuration Instructions

#### Sensitive URLs
Before using either HTML file, you must configure the following:
- **`credentialsUrl`**: URL for the `credentials.txt` file (required for the Multi-Tool HTML file).
- **`iframeUrl`**: URL for iframe embedding in the Multi-Tool HTML.
- **`gitHubEmbedUrl`**: URL for GitHub content embedding in the Multi-Tool HTML.
- **`gitHubRawUrl`**: URL for the content to be dynamically fetched in the Raw GitHub Content Loader HTML.

#### Checksum Validation
To enable or disable checksum validation:
- Locate the `enableChecksum` variable in the JavaScript of each HTML file.
- Set it to `true` to enable validation or `false` to disable it.

---

### Error Handling Summary

| **Error Scenario**              | **Resolution**                                                                                  |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Missing URL Configuration**   | Alerts user to set required variables (`credentialsUrl`, `iframeUrl`, etc.).                    |
| **Invalid Credentials**         | Prompts user to check and re-enter their username and password.                                  |
| **Failed Fetch Requests**       | Displays error messages if URLs are unreachable or content is unavailable.                      |
| **Unset Display Option**         | Alerts user to configure the `displayOption` variable properly.                                 |

---

### Final Notes
- These tools are designed to securely and dynamically embed content while maintaining flexibility and user control.
- Comments in the `credentials.txt` file make it easier to manage and document credentials without disrupting functionality.
- The tools are lightweight, well-documented, and easy to extend for additional functionality as needed.

---
