# NeoName - Product Name Generator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://www.javascript.com/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)

**NeoName** is a web application designed to help you generate unique and memorable product names for your next big idea. Leveraging advanced AI technology, NeoName takes your input about your product and provides a list of creative and relevant name suggestions.

## Table of Contents

- [Features](#features)
- [How It Works](#how-it-works)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Intelligent Name Generation:** Utilizes AI to create relevant and creative product name suggestions based on your input.
- **Customizable Input:** Specify industry, product category, key adjectives, target audience, tone, keywords, desired name length, and name type.
- **Save Favorite Names:** Easily save generated names you like for later consideration.
- **Copy to Clipboard:** Quickly copy generated names to your clipboard.
- **Dark Mode:** Offers a dark mode for comfortable viewing in low-light environments.
- **Responsive Design:** Works seamlessly on various devices, from desktops to mobile phones.
- **Real-time Feedback:** Provides loading indicators and toast notifications for a smooth user experience.

## How It Works

NeoName uses a backend API (in this case, powered by [Magic Loops](https://magicloops.dev/)) to process the information you provide through the intuitive form. When you submit your product details, the application sends a request to the API, which then uses sophisticated algorithms to generate a list of potential product names that align with your criteria. The generated names are then displayed in the results section, where you can save or copy them.

## Getting Started

To use NeoName, simply open the `index.html` file in your web browser. No installation or setup is required.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>NeoName - Product Name Generator</title>
    </head>
<body>
    <script src="[https://code.jquery.com/jquery-3.6.0.min.js](https://code.jquery.com/jquery-3.6.0.min.js)"></script>
    <script id="app-script">
        // ... (your JavaScript code) ...
    </script>
</body>
</html>
