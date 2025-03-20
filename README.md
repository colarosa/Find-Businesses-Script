# Find Bussiness: Get data in bulk script

## Overview
This project is a Google Apps Script that leverages the Google Maps Places API to aggregate kids' activity listings. It fetches business details for various categories of activities for children and organizes them into a Google Sheet.

## Features
- Retrieves activity listings using Google Maps Places API
- Extracts business details such as phone, website, logo, hours, and categorization
- Categorizes activities by age group
- Identifies businesses offering online options
- Writes results to a Google Sheet for easy access

## Prerequisites
### Required API Key
To use this script, you must have a Google Maps Places API key.
1. Generate an API key from Google: [Get API Key](https://developers.google.com/maps/documentation/places/web-service/get-api-key)
2. Replace `XXXXX` in the script with your actual API key:
   ```js
   const API_KEY = 'XXXXX';
   ```

### Google Apps Script Setup
1. Open Google Sheets.
2. Go to `Extensions > Apps Script`.
3. Copy and paste the script into the editor.
4. Save the script.

## Categories Tracked
The script searches for the following categories of activities (change these to what ever you want):
- Karate classes
- Daycares
- Coding clubs
- Chess clubs
- Language clubs
- Gymnastics
- Music lessons
- Dance schools
- Art classes
- Swimming lessons
- Summer camps
- Science clubs
- Math tutoring

## How It Works
### 1. Fetching Business Details
- Uses Google Places API to retrieve business information.
- Extracts details such as phone number, website, hours, and category.

### 2. Categorization
- Determines the suitable age range for each activity based on keywords.
- Checks if the business offers online classes.

### 3. Writing to Google Sheets
- Creates a new sheet for each category.
- Stores details including business name, address, rating, phone, website, and more.

## Running the Script
To run the script:
1. Open the Apps Script editor in Google Sheets.
2. Run the `main()` function to search for all categories in Toronto (default location).
3. The results will be saved into a Google Sheet.

## Customization
### Change Search Location
Modify the `main()` function to use a different city:
```js
main('New York');
```

### Adjust Search Radius
Update the `getBusinesses` function to modify the `currentRadius` and `maxSearchRadius` variables:
```js
let currentRadius = 15000;
const maxSearchRadius = 60000;
```

## Error Handling
- The script logs errors if API requests fail.
- If a business lacks details, default values such as 'N/A' are used.

## License
This project is open-source and free to use.

## Acknowledgments
Built using Google Apps Script and Google Maps Places API to simplify the search for kids' activities.

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

### 1. Obtain an API Key

Generate your own Google Maps Places API key and replace the placeholder in the script:

```javascript
// IMPORTANT: Replace 'XXXXX' with your own Google Maps Places API key.
// If you don't have one yet, you can generate it here:
// https://developers.google.com/maps/documentation/places/web-service/get-api-key
const API_KEY = 'XXXXX';
```

### 2. Add the Script to Your Google Sheets

Follow these steps to install the script:

1. Open your **Google Sheets** document.
2. Click on **Extensions > Apps Script**.
3. Delete any existing code in the script editor.
4. Copy and paste the script into the script editor.
5. Click **Save** (Ctrl + S or Cmd + S).
6. Click **Run** to execute the script.

## Usage

### 1. Running the Script

Modify the `main()` function with your desired search parameters and run the script.

Example:


### 2. New Worksheet Creation

- Each execution creates a **new worksheet** named using the search parameters and a timestamp  
  (e.g., `"swimming lessons"`).
- This ensures that different queries output to separate sheets and do not overwrite previous results.

### 3. Logs

- Use the **Execution Logs** in the Apps Script Editor to track:
  - The number of businesses found.
  - Any errors encountered during execution.

## Customization

### 1. Search Parameters

Modify the `getBusinesses()` function call inside the `main()` function to adjust the search query.

- **Parameters:**
  - **Industry (string):** The type of business to search for.
  - **Location (string):** The geographic location for the search.
  - **Type (optional, string):** A specific Google Places API business type.
  - **Max Results (optional, number):** The maximum number of results to return.

Example:

```javascript
getBusinesses('yoga classes', 'New York', 'gym', 50);
```

### 2. Radius Settings

Adjust how the search radius expands in the script:

- **Starting radius:** `10,000` meters (10 km).
- **Increment:** `10,000` meters (10 km).
- **Maximum radius:** `50,000` meters (50 km).

Modify these values inside the script if needed.

### 3. Additional Data

The script fetches:

- Business name
- Address
- Rating
- Phone number (via a secondary API call if missing)

Extend the script to fetch additional data from the Google Places API if required.

## License

This project is licensed under the **MIT License**.  
Feel free to use and modify it to fit your needs.

## Contributing

If you’d like to contribute improvements or report issues, please **submit a pull request** or **open an issue** on GitHub.

