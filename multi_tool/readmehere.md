### README.md: Dynamic Multi-Tool & Raw GitHub Content Loader

# Dynamic Multi-Tool & Raw GitHub Content Loader

## Overview
This repository contains two powerful tools:
1. **Dynamic Multi-Tool HTML**: A versatile dashboard for iframe embedding, GitHub content fetching, and displaying custom HTML.
2. **Raw GitHub Content Loader HTML**: A standalone tool for dynamically loading raw GitHub content and displaying it.

Both HTML files include robust error handling and validation mechanisms. Additionally, a checksum feature is included to verify the integrity of the HTML files, which can be toggled off for flexibility.

---

## Dynamic Multi-Tool HTML

### Key Features
| **Feature**                     | **How It Works**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Login System**                | Requires users to enter valid credentials (username/password) stored in a `credentials.txt` file.|
| **Iframe Mode**                 | Embeds an external URL using an iframe for displaying content.                                   |
| **GitHub Mode**                 | Dynamically fetches and embeds raw HTML content from a GitHub URL.                              |
| **Custom HTML Mode**            | Displays pre-defined custom HTML content tailored for user requirements.                        |
| **Checksum Validation**         | Validates the HTML file's integrity before executing content-loading operations.                |
| **Error Handling**              | Alerts users to missing credentials, unset URLs, or invalid configuration options.              |

---

### Dynamic Multi-Tool: Side-by-Side Explanation

#### HTML Elements
| **HTML Section**                | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `<head>`                        | Includes CSS styling and JavaScript functions for functionality.                               |
| `<div id="popup">...</div>`      | Contains the login form for user authentication.                                               |
| `<div id="accessMessage">...</div>` | Displays a success message after a successful login.                                          |
| `<div id="errorMessage">...</div>` | Displays an error message for failed login attempts.                                           |
| `<div id="fileErrorMessage">...</div>` | Displays an error if the `credentials.txt` file cannot be fetched.                           |

---

#### CSS
| **CSS Rule**                    | **Explanation**                                                                                 |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `iframe { ... }`                | Defines full-page embedding for iframe content.                                                |
| `#popup { ... }`                | Styles the login form for centered, full-page display.                                          |
| `input, button { ... }`         | Styles input fields and buttons with padding, margins, and consistent font sizes.              |
| `textarea { ... }`              | Adds styling for the `textarea` used in custom HTML input.                                     |

---

#### JavaScript Functions
| **Function**                    | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `verifyNameAndCode()`           | Validates user credentials against the fetched `credentials.txt` file.                         |
| `handleEmbedOption()`           | Determines the mode (iframe, GitHub, or custom) and loads corresponding content.               |
| `fetchGitHubContent()`          | Fetches and displays content from a specified GitHub URL.                                      |
| `checksumValidation()`          | Runs a checksum to ensure the integrity of the HTML file. Can be toggled on/off.               |

---

## Raw GitHub Content Loader HTML

### Key Features
| **Feature**                     | **How It Works**                                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Dynamic Content Fetching**    | Automatically fetches and displays raw HTML content from a GitHub URL.                         |
| **Error Handling**              | Displays specific error messages for missing URLs or failed fetch requests.                     |
| **Live Updates**                | Always loads the latest version of the GitHub raw content hosted at the specified URL.          |
| **Minimal Design**              | Optimized for simplicity and ease of use.                                                      |

---

### Raw GitHub Content Loader: Side-by-Side Explanation

#### HTML Elements
| **HTML Section**                | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `<head>`                        | Includes JavaScript for fetching and displaying GitHub content.                                |
| `<body>`                        | Displays loading and error messages dynamically during content fetching.                       |
| `<p id="loadingMessage">...</p>` | Informs the user that content is being loaded.                                                  |
| `<p id="errorMessage">...</p>`   | Displays any errors encountered during the fetch process.                                       |

---

#### CSS
| **CSS Rule**                    | **Explanation**                                                                                 |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `body { ... }`                  | Centers content on the page and defines universal font and background color settings.           |
| `#loadingMessage { ... }`       | Styles the loading message with blue text for emphasis.                                         |
| `#errorMessage { ... }`         | Styles error messages with red text for visibility.                                             |

---

#### JavaScript Functions
| **Function**                    | **Purpose**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| `loadFromGitHub(url)`           | Fetches and loads raw HTML content from the specified GitHub URL.                              |
| `displayError(message)`         | Displays error messages dynamically during failed fetch attempts.                              |

---

## Configuration Instructions

### Sensitive URLs
Before deploying these files, configure the following variables:
- **`credentialsUrl`**: URL for the `credentials.txt` file.
- **`iframeUrl`**: URL for iframe embedding.
- **`gitHubEmbedUrl`**: URL for GitHub raw content embedding.

### Checksum Validation
To enable or disable checksum:
- Find the `enableChecksum` variable and set it to `true` or `false`.
- When enabled (`true`), ensures the HTML file’s integrity is validated before execution.

---

### Error Handling Summary

| **Error Scenario**              | **Message**                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------|
| Missing URL                      | Alerts user to configure the required URL(s).                                                 |
| Invalid Credentials              | Displays an error message for incorrect username/password.                                    |
| Failed Fetch Requests            | Alerts user to check the specified URL or their network connection.                          |
| Unset `displayOption`            | Prompts user to manually configure the display mode (iframe, GitHub, or custom).             |
