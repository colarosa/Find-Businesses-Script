# Google Places Business Search Script for Google Sheets

A Google Apps Script that fetches business listings from the Google Maps Places API based on user-specified search parameters (such as industry, location, type, and maximum results) and writes the results to a new worksheet in your Google Sheets workbook. The script dynamically expands the search radius until it meets the required number of unique results, filters out duplicate entries, and retrieves additional details like phone numbers via the Place Details API.

## Features

- **Dynamic Search Radius:** Automatically expands the search radius until a specified number of unique results is found or until a maximum radius limit is reached.
- **Duplicate Filtering:** Prevents duplicate entries by checking business addresses.
- **Detailed Business Information:** Fetches details such as business name, address, rating, and phone number (using an additional API call when needed).
- **New Worksheet for Each Query:** Creates a new worksheet for each search query, keeping your data organized.
- **Easy Customization:** Modify search parameters (industry, location, business type, max results) via the `main()` function.

## Requirements

- **Google Maps Places API Key:**  
  You must generate your own API key.  
  [Get your API Key here](https://developers.google.com/maps/documentation/places/web-service/get-api-key)
- A Google Sheets account.
- Basic knowledge of Google Apps Script.

## Setup

1. **Obtain an API Key:**  
   Generate your own Google Maps Places API key and replace the placeholder in the script:
   ```javascript
   // IMPORTANT: Replace 'XXXXX' with your own Google Maps Places API key.
   // If you don't have one yet, you can generate it here:
   // https://developers.google.com/maps/documentation/places/web-service/get-api-key
   const API_KEY = 'XXXXX';
