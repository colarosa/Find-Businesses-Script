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
The script searches for the following categories of activities (change to whatever you like):
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

### 3. New Worksheet Creation
- Each execution creates a **new worksheet** named using the search parameters and a timestamp  
  (e.g., `"swimming lessons"`).
- This ensures that different queries output to separate sheets and do not overwrite previous results.

### 4. Logs
- Use the **Execution Logs** in the Apps Script Editor to track:
  - The number of businesses found.
  - Any errors encountered during execution.

## Running the Script
To run the script:
1. Open the Apps Script editor in Google Sheets.
2. Run the `main()` function to search for all categories in Toronto (default location).
3. The results will be saved into a Google Sheet.

## Customization
### Change Search Location
Modify the `main()` function to use a different city:
```js
function main() {
  CATEGORIES.forEach(category => getBusinesses(category, 'New York'));
}
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

