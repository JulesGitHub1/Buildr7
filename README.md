# ColorSwipe

A mobile-optimized web app that lets users swipe on color swatches in a TikTok-like format. Users can swipe up to like colors and swipe down to dislike colors. The app learns from these preferences and shows more colors similar to those liked and less similar to those disliked.

## Features

- 150 unique color swatches generated using HSL color space
- Swipe up to like, swipe down to dislike
- First 5 colors are completely random
- Subsequent colors are selected based on user preferences
- "Finalize" button to select your favorite color
- Heart emoji animation when finalizing
- Unique color ID displayed for the final selection
- Selected color IDs are sent to a Google Sheet for tracking

## Setup Instructions

### 1. Local Setup

Simply open the `index.html` file in a web browser to use the app locally.

### 2. Google Sheet Integration

To enable saving color selections to a Google Sheet:

1. **Deploy the Google Apps Script:**
   - Go to [Google Apps Script](https://script.google.com/) and create a new project
   - Copy the code from `google-apps-script.txt` into the script editor
   - The spreadsheet ID is already set to the provided sheet: `1A5ejlCsK3U4VR-3GbkRNVH8GLZYsISryFxmNG94NMWs`
   - Deploy as a web app:
     - Click "Deploy" > "New deployment"
     - Select type: "Web app"
     - Set "Execute as" to "Me"
     - Set "Who has access" to "Anyone"
     - Click "Deploy"
     - Copy the web app URL

2. **Update the Configuration:**
   - Open `js/config.js`
   - Replace the `GOOGLE_SCRIPT_URL` value with your deployed script URL

## How It Works

1. **Color Generation:**
   - The app generates 150 unique colors using HSL color space for better distribution
   - Each color has a unique ID number between 1000-9999

2. **Swipe Mechanism:**
   - Swipe up to like a color (👍)
   - Swipe down to dislike a color (👎)
   - The first 5 colors are completely random

3. **Color Selection Algorithm:**
   - After the first 5 colors, the app uses your likes and dislikes to select new colors
   - Colors more similar to your likes and less similar to your dislikes are prioritized
   - Similarity is calculated using a weighted HSL distance formula

4. **Finalization:**
   - Click the "Finalize" button to select your current color
   - A heart animation plays
   - The color's unique ID is displayed
   - The color ID is sent to the Google Sheet for tracking

5. **Google Sheet Integration:**
   - When you finalize a color, its ID is sent to the Google Sheet
   - The sheet records the color ID and a timestamp

## Technical Implementation

- Pure HTML, CSS, and JavaScript (no frameworks required)
- Mobile-optimized with responsive design
- Touch-friendly swipe gestures with visual feedback
- Google Apps Script for Google Sheet integration

## Files

- `index.html` - Main HTML structure
- `styles.css` - CSS styling
- `js/colors.js` - Color generation and similarity calculations
- `js/swipe.js` - Touch interaction handling
- `js/config.js` - Configuration settings (Google Script URL)
- `js/app.js` - Main application logic
- `google-apps-script.txt` - Google Apps Script code for sheet integration

## Browser Compatibility

The app works on modern browsers and is optimized for mobile devices. For desktop testing, mouse interactions simulate touch events.
