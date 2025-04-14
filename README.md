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
  
  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Montserrat:wght@400;500;600;700&display=swap" rel="stylesheet">
  
  <!-- Animate.css -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  
  <style id="app-style">
    :root {
      --primary-color: #6c63ff;
      --secondary-color: #4c46b6;
      --accent-color: #ff6584;
      --text-color: #333;
      --light-text: #777;
      --light-bg: #f8f9fa;
      --dark-bg: #2a2a3c;
      --success-color: #28a745;
      --border-radius: 12px;
      --card-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
      --transition: all 0.3s ease;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #f5f7fa 0%, #e4e8ff 100%);
      color: var(--text-color);
      min-height: 100vh;
      line-height: 1.6;
    }
    
    h1, h2, h3, h4, h5 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px;
    }
    
    .app-header {
      text-align: center;
      margin-bottom: 30px;
      padding-top: 30px;
    }
    
    .app-title {
      font-size: 2.5rem;
      margin-bottom: 10px;
      background: linear-gradient(45deg, var(--primary-color), var(--accent-color));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    
    .app-subtitle {
      font-size: 1.1rem;
      color: var(--light-text);
      max-width: 600px;
      margin: 0 auto;
    }
    
    .main-container {
      display: flex;
      flex-direction: column;
      gap: 30px;
    }
    
    @media (min-width: 992px) {
      .main-container {
        flex-direction: row;
      }
    }
    
    .input-section {
      background-color: white;
      border-radius: var(--border-radius);
      padding: 30px;
      box-shadow: var(--card-shadow);
      flex: 1;
    }
    
    .form-group {
      margin-bottom: 20px;
    }
    
    .form-label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
    }
    
    .form-control {
      width: 100%;
      padding: 12px 16px;
      border: 1px solid #ddd;
      border-radius: var(--border-radius);
      font-size: 16px;
      transition: var(--transition);
    }
    
    .form-control:focus {
      outline: none;
      border-color: var(--primary-color);
      box-shadow: 0 0 0 3px rgba(108, 99, 255, 0.2);
    }
    
    .form-select {
      appearance: none;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='%23777' viewBox='0 0 16 16'%3E%3Cpath d='M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z'/%3E%3C/svg%3E");
      background-repeat: no-repeat;
      background-position: right 12px center;
      background-size: 16px 12px;
    }
    
    .range-value {
      display: inline-block;
      margin-left: 10px;
      color: var(--primary-color);
      font-weight: 600;
    }
    
    .api-key-section {
      margin-top: 30px;
      padding-top: 20px;
      border-top: 1px dashed #ddd;
    }
    
    .btn {
      display: inline-block;
      padding: 12px 24px;
      background-color: var(--primary-color);
      color: white;
      border: none;
      border-radius: var(--border-radius);
      font-size: 16px;
      font-weight: 500;
      cursor: pointer;
      transition: var(--transition);
      text-align: center;
      text-decoration: none;
    }
    
    .btn:hover {
      background-color: var(--secondary-color);
      transform: translateY(-2px);
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    }
    
    .btn-primary {
      background-color: var(--primary-color);
      width: 100%;
      margin-top: 10px;
    }
    
    .btn-success {
      background-color: var(--success-color);
    }
    
    .results-section {
      background-color: white;
      border-radius: var(--border-radius);
      padding: 30px;
      box-shadow: var(--card-shadow);
      flex: 1;
      min-height: 300px;
      display: flex;
      flex-direction: column;
    }
    
    .results-title {
      margin-bottom: 20px;
      padding-bottom: 20px;
      border-bottom: 1px solid #eee;
    }
    
    .loading-container {
      display: none;
      flex: 1;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }
    
    .spinner {
      border: 4px solid rgba(0, 0, 0, 0.1);
      border-radius: 50%;
      border-top: 4px solid var(--primary-color);
      width: 50px;
      height: 50px;
      animation: spin 1s linear infinite;
      margin-bottom: 20px;
    }
    
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    
    .names-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 15px;
      flex: 1;
    }
    
    .name-item {
      padding: 15px;
      border-radius: var(--border-radius);
      background-color: var(--light-bg);
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: var(--transition);
    }
    
    .name-item:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
    }
    
    .name-text {
      font-weight: 600;
      font-size: 1.1rem;
    }
    
    .name-actions {
      display: flex;
      gap: 10px;
    }
    
    .action-btn {
      background: none;
      border: none;
      cursor: pointer;
      font-size: 1.2rem;
      color: var(--light-text);
      transition: var(--transition);
    }
    
    .action-btn:hover {
      color: var(--primary-color);
    }
    
    .saved-section {
      margin-top: 20px;
      border-top: 1px dashed #ddd;
      padding-top: 20px;
    }
    
    .saved-title {
      margin-bottom: 15px;
    }
    
    .saved-list {
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }
    
    .saved-item {
      background-color: var(--light-bg);
      border-radius: 50px;
      padding: 8px 16px;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    
    .saved-item .remove-saved {
      color: var(--accent-color);
      cursor: pointer;
      font-size: 0.8rem;
    }
    
    .no-results {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      color: var(--light-text);
      font-style: italic;
    }
    
    .results-placeholder {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: var(--light-text);
    }
    
    .placeholder-icon {
      font-size: 3rem;
      margin-bottom: 20px;
      color: #ddd;
    }
    
    .tooltip {
      position: relative;
      display: inline-block;
      margin-left: 5px;
      color: var(--light-text);
    }
    
    .tooltip .tooltiptext {
      visibility: hidden;
      width: 200px;
      background-color: var(--dark-bg);
      color: white;
      text-align: center;
      border-radius: 6px;
      padding: 10px;
      position: absolute;
      z-index: 1;
      bottom: 125%;
      left: 50%;
      transform: translateX(-50%);
      opacity: 0;
      transition: opacity 0.3s;
      font-size: 0.8rem;
      font-weight: normal;
    }
    
    .tooltip:hover .tooltiptext {
      visibility: visible;
      opacity: 1;
    }
    
    .api-status {
      display: inline-block;
      font-size: 0.8rem;
      padding: 3px 8px;
      border-radius: 50px;
      background-color: #f8d7da;
      color: #842029;
      margin-left: 10px;
    }
    
    .api-status.connected {
      background-color: #d1e7dd;
      color: #0f5132;
    }
    
    @media (max-width: 768px) {
      .app-title {
        font-size: 2rem;
      }
      
      .input-section, .results-section {
        padding: 20px;
      }
    }

    .toast {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: var(--success-color);
      color: white;
      padding: 15px 25px;
      border-radius: var(--border-radius);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
      transform: translateY(100px);
      opacity: 0;
      transition: all 0.3s ease;
      z-index: 1000;
    }
    
    .toast.show {
      transform: translateY(0);
      opacity: 1;
    }

    .empty-state {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 40px 20px;
      color: var(--light-text);
    }

    .empty-state-icon {
      font-size: 4rem;
      margin-bottom: 20px;
      color: #ddd;
    }

    .empty-state-text {
      max-width: 300px;
      margin-bottom: 20px;
    }
  </style>

  <style id="dark-mode-style">
    /* Dark mode CSS overrides */
    body.dark-mode {
      background: linear-gradient(135deg, #1c1c1c 0%, #2e2e2e 100%);
      color: #ddd;
      transition: background 0.3s ease, color 0.3s ease;
    }
    body.dark-mode .app-title {
      background: linear-gradient(45deg, #bb86fc, #03dac6);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    body.dark-mode .input-section,
    body.dark-mode .results-section {
      background-color: #333;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.5);
    }
    body.dark-mode .form-control {
      background-color: #444;
      border: 1px solid #555;
      color: #eee;
    }
    body.dark-mode .form-control:focus {
      border-color: #bb86fc;
      box-shadow: 0 0 0 3px rgba(187, 134, 252, 0.3);
    }
    body.dark-mode .results-placeholder,
    body.dark-mode .empty-state,
    body.dark-mode .empty-state-text {
      color: #ccc;
    }
    body.dark-mode .name-item {
      background-color: #444;
    }
    body.dark-mode .saved-item {
      background-color: #555;
    }
    /* Override CSS variable values if preferred */
    body.dark-mode {
      --primary-color: #bb86fc;
      --secondary-color: #3700b3;
      --accent-color: #03dac6;
      --text-color: #ddd;
      --light-text: #aaa;
      --light-bg: #333;
      --dark-bg: #121212;
    }
  </style>
</head>
<body>
  <div class="container">
    <header class="app-header">
      <h1 class="app-title">NeoName</h1>
      <p class="app-subtitle">Generate unique, memorable product names for your next big idea. Powered by advanced AI technology.</p>
      <!-- Dark mode toggle button added below -->
      <button id="darkModeToggle" class="btn" style="position:absolute; top:20px; right:20px;">
        <i class="fas fa-adjust"></i> Toggle Dark Mode
      </button>
    </header>
    
    <main class="main-container">
      <section class="input-section">
        <h2>Tell us about your product</h2>
        <p class="mb-4">Fill in the details below to help generate names that resonate with your vision.</p>
        
        <form id="nameGeneratorForm">
          <div class="form-group">
            <label for="industry" class="form-label">Industry Type</label>
            <select id="industry" class="form-control form-select">
              <option value="">Select an industry</option>
              <option value="technology">Technology</option>
              <option value="food">Food & Beverage</option>
              <option value="fashion">Fashion & Apparel</option>
              <option value="health">Health & Wellness</option>
              <option value="finance">Finance & Banking</option>
              <option value="entertainment">Entertainment</option>
              <option value="education">Education</option>
              <option value="travel">Travel & Hospitality</option>
              <option value="beauty">Beauty & Cosmetics</option>
              <option value="home">Home & Furniture</option>
              <option value="sports">Sports & Fitness</option>
              <option value="other">Other</option>
            </select>
          </div>
          
          <div class="form-group">
            <label for="category" class="form-label">Product Category</label>
            <input type="text" id="category" class="form-control" placeholder="e.g. Smartphone, Snack, Software">
          </div>
          
          <div class="form-group">
            <label for="adjectives" class="form-label">Key Adjectives</label>
            <input type="text" id="adjectives" class="form-control" placeholder="e.g. Innovative, Sustainable, Elegant">
          </div>
          
          <div class="form-group">
            <label for="audience" class="form-label">Target Audience</label>
            <input type="text" id="audience" class="form-control" placeholder="e.g. Young Professionals, Parents, Teenagers">
          </div>
          
          <div class="form-group">
            <label for="tone" class="form-label">Tone/Style</label>
            <select id="tone" class="form-control form-select">
              <option value="">Select a tone</option>
              <option value="professional">Professional</option>
              <option value="playful">Playful</option>
              <option value="luxury">Luxury</option>
              <option value="minimalist">Minimalist</option>
              <option value="technical">Technical</option>
              <option value="friendly">Friendly</option>
              <option value="futuristic">Futuristic</option>
              <option value="retro">Retro/Vintage</option>
              <option value="eco">Eco-friendly</option>
            </select>
          </div>
          
          <div class="form-group">
            <label for="keywords" class="form-label">Keywords</label>
            <input type="text" id="keywords" class="form-control" placeholder="e.g. speed, eco, smart">
          </div>
          
          <div class="form-group">
            <label for="length" class="form-label">Name Length Preference</label>
            <select id="length" class="form-control form-select">
              <option value="">Select length preference</option>
              <option value="short">Short (1-5 characters)</option>
              <option value="medium">Medium (6-10 characters)</option>
              <option value="long">Long (11+ characters)</option>
              <option value="any">Any length</option>
            </select>
          </div>
          
          <div class="form-group">
            <label for="nameType" class="form-label">Name Type</label>
            <select id="nameType" class="form-control form-select">
              <option value="">Select name type</option>
              <option value="real">Real words</option>
              <option value="coined">Coined/Made-up words</option>
              <option value="blended">Blended words</option>
              <option value="acronym">Acronyms</option>
              <option value="any">Any type</option>
            </select>
          </div>
          
          <div class="form-group">
            <label for="values" class="form-label">Brand Values</label>
            <input type="text" id="values" class="form-control" placeholder="e.g. Sustainability, Innovation, Trust">
          </div>
          
          <button type="submit" id="generateBtn" class="btn btn-primary">
            <i class="fas fa-magic"></i> Generate Names
          </button>
        </form>
      </section>
      
      <section class="results-section">
        <h2 class="results-title">Generated Product Names</h2>
        
        <div id="resultsPlaceholder" class="results-placeholder">
          <i class="fas fa-lightbulb placeholder-icon"></i>
          <p>Your generated names will appear here</p>
          <small>Fill in the form and click "Generate Names" to get started</small>
        </div>
        
        <div id="loadingContainer" class="loading-container">
          <div class="spinner"></div>
          <p>Generating creative names...</p>
        </div>
        
        <ul id="namesList" class="names-list" style="display: none;"></ul>
        
        <div id="savedSection" class="saved-section" style="display: none;">
          <h3 class="saved-title">Saved Names</h3>
          <ul id="savedList" class="saved-list"></ul>
        </div>
      </section>
    </main>
  </div>
  
  <div id="toast" class="toast">Name saved successfully!</div>

  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script id="app-script">
    $(document).ready(function() {
      // Dark mode toggle functionality
      $('#darkModeToggle').on('click', function() {
        $('body').toggleClass('dark-mode');
      });
      
      // Initialize variables
      let apiConnected = true;
      let savedNames = JSON.parse(localStorage.getItem('savedProductNames')) || [];
      
      // Update saved names display on load
      updateSavedNames();
      
      // Form submission
      $('#nameGeneratorForm').on('submit', function(e) {
        e.preventDefault();
        
        // Check if API is connected
        if (!apiConnected) {
          showToast('Please connect your API key first!');
          return;
        }
        
        // Hide results placeholder and show loading
        $('#resultsPlaceholder').hide();
        $('#namesList').hide();
        $('#loadingContainer').css('display', 'flex');
        
        // Collect form data and prepare API request payload for ProductNamesAPI
        const formData = {
          industryType: $('#industry').val(),                             // Map industry value
          productCategory: $('#category').val(),                            // Map category value
          keyAdjectives: $('#adjectives').val().split(',').map(item => item.trim()), // Split adjectives, assuming comma separated
          targetAudience: $('#audience').val(),                             // Map audience value
          toneStyle: $('#tone').val(),                                      // Map tone value
          keywords: $('#keywords').val().split(',').map(item => item.trim()), // Split keywords, assuming comma separated
          lengthPreferences: $('#length').val(),                            // Map length value
          nameType: $('#nameType').val(),                                   // Map name type value
          brandValues: $('#values').val().split(',').map(item => item.trim()) // Split brand values, assuming comma separated
        };

        // New: Call ProductNamesAPI Magic Loop using fetch
        fetch('https://magicloops.dev/api/loop/fbf30e79-8f9b-40f2-b9ea-67500cf4620f/run', {
          method: 'POST',
          body: JSON.stringify(formData)
        })
        .then(response => response.json())
        .then(data => {
          // Hide loading and show results
          $('#loadingContainer').hide();
          $('#namesList').show();
          $('#namesList').empty();
          
          // Iterate over the generated names and build the UI list items
          if (data.generatedNames && data.generatedNames.length) {
            data.generatedNames.forEach(name => {
              $('#namesList').append(`
                <li class="name-item">
                  <span class="name-text">${name}</span>
                  <div class="name-actions">
                    <button class="action-btn copy-name" title="Copy Name"><i class="fas fa-copy"></i></button>
                    <button class="action-btn save-name" title="Save Name"><i class="fas fa-save"></i></button>
                  </div>
                </li>
              `);
            });
          } else {
            // If no generated names, show an empty state
            $('#namesList').html(`
              <div class="empty-state">
                <i class="fas fa-code empty-state-icon"></i>
                <p class="empty-state-text">No names were generated. Please try different inputs.</p>
              </div>
            `);
          }
          // Show saved section if we have saved names
          if (savedNames.length > 0) {
            $('#savedSection').show();
          }
        })
        .catch(error => {
          console.error('Error generating names:', error);
          showToast('An error occurred during name generation.');
          $('#loadingContainer').hide();
          $('#resultsPlaceholder').show();
        });
      });
      
      // Handle saving names (event delegation for dynamic elements)
      $(document).on('click', '.save-name', function() {
        const nameItem = $(this).closest('.name-item');
        const name = nameItem.find('.name-text').text();
        
        // Add to saved names if not already saved
        if (!savedNames.includes(name)) {
          savedNames.push(name);
          localStorage.setItem('savedProductNames', JSON.stringify(savedNames));
          updateSavedNames();
          showToast('Name saved!');
        } else {
          showToast('This name is already saved');
        }
      });
      
      // Handle removing saved names
      $(document).on('click', '.remove-saved', function() {
        const name = $(this).data('name');
        savedNames = savedNames.filter(item => item !== name);
        localStorage.setItem('savedProductNames', JSON.stringify(savedNames));
        updateSavedNames();
        showToast('Name removed');
      });
      
      // Copy name to clipboard
      $(document).on('click', '.copy-name', function() {
        const name = $(this).closest('.name-item').find('.name-text').text();
        navigator.clipboard.writeText(name)
          .then(() => {
            showToast('Copied to clipboard!');
          })
          .catch(err => {
            console.error('Failed to copy: ', err);
            showToast('Failed to copy');
          });
      });
      
      // Helper function to update saved names list
      function updateSavedNames() {
        const savedList = $('#savedList');
        savedList.empty();
        
        if (savedNames.length > 0) {
          $('#savedSection').show();
          savedNames.forEach(name => {
            savedList.append(`
              <li class="saved-item">
                <span>${name}</span>
                <i class="fas fa-times remove-saved" data-name="${name}"></i>
              </li>
            `);
          });
        } else {
          $('#savedSection').hide();
        }
      }
      
      // Helper function to show toast messages
      function showToast(message) {
        $('#toast').text(message).addClass('show');
        setTimeout(() => {
          $('#toast').removeClass('show');
        }, 3000);
      }
    });
  </script>
</body>
</html>
