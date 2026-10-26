# Calorix

Calorix is a calorie and nutrition tracking mobile application built with React Native and Expo. The application allows users to browse foods, search and filter food items, track daily calorie and macronutrient intake, create custom foods, save favourite foods, and calculate a personalised daily calorie goal based on their profile and activity level.

---

## Features

### Dashboard

The Dashboard provides an overview of the user's nutrition for the current day.

It displays:

- Total calories consumed
- Daily calorie goal
- Remaining calories
- Protein intake
- Carbohydrate intake
- Fat intake
- Foods logged during the day
- Food intake grouped by category

The Dashboard updates based on the foods recorded in the daily log.

### Food Library

The Food Library provides access to the application's built-in food database.

Users can:

- Browse available foods
- Search for foods
- Filter foods by category
- Sort food items
- View food details
- Add foods to their daily log
- Favourite foods
- Manage custom foods

Food information includes:

- Food name
- Category
- Portion size
- Calories
- Protein
- Carbohydrates
- Fat

### Food Categories

Foods are organised into the following categories:

- Breakfast
- Lunch
- Dinner
- Snack
- Drink
- Custom

### Food Search

Users can search the food library by food name to quickly find a particular food.

### Food Sorting

The Food Library provides sorting options including:

- Name A–Z
- Name Z–A
- Calories ascending
- Calories descending

### Food Pagination

Food items are displayed using pagination, allowing users to move between pages of food results rather than displaying the entire food database at once.

### Food Details

The Food Detail screen displays the nutritional information for a selected food.

Users can also:

- Adjust the number of servings
- Add the food to the daily log
- Add or remove the food from favourites
- Delete custom foods

### Serving Adjustment

Users can select the number of servings before adding a food to the daily log.

Serving amounts can be adjusted in increments of 0.5. Nutritional values are adjusted according to the selected serving amount.

### Daily Log

The Daily Log displays foods recorded for the current day.

Each logged food can include:

- Food name
- Number of servings
- Portion size
- Calories
- Protein
- Carbohydrates
- Fat
- Logged time

Users can remove individual foods from the daily log.

### Favourites

Users can save frequently used foods as favourites.

Favourite foods are available from the Favourites tab so they can be accessed and logged more quickly.

### Custom Foods

Users can create their own food entries using the Add Food screen.

A custom food can contain:

- Food name
- Portion size
- Category
- Calories
- Protein
- Carbohydrates
- Fat

Custom foods are saved locally and appear in the Food Library.

Users can also delete custom foods when they are no longer needed.

### Automatic Calorie Calculation

When creating a custom food, Calorix can calculate an estimated calorie value from the macronutrients.

The calculation is based on:

```text
Protein × 4
Carbohydrates × 4
Fat × 9
```

### Profile

The Profile screen allows users to enter personal information used for calorie calculations.

The profile includes information such as:

- Gender
- Age
- Height
- Weight
- Activity level
- Weight goal

### BMR Calculation

Calorix calculates Basal Metabolic Rate (BMR) using the Mifflin-St Jeor equation.

For males:

```text
BMR = (10 × weight) + (6.25 × height) − (5 × age) + 5
```

For females:

```text
BMR = (10 × weight) + (6.25 × height) − (5 × age) − 161
```

Where weight is measured in kilograms and height in centimetres.

### Activity Levels

Users can select an activity level when calculating their daily calorie requirements.

Available activity levels include:

- Sedentary
- Lightly Active
- Moderately Active
- Very Active
- Extra Active

### Weight Goals

Users can select a weight goal from the Profile screen:

- Lose Weight
- Maintain
- Gain Muscle

The selected goal is used when calculating the personalised daily calorie target.

### Personalised Calorie Goal

Calorix can calculate a recommended daily calorie goal based on:

- BMR
- Activity level
- Weight goal

The calculated goal can then be saved and used by the Dashboard.

### Splash Screen

The application includes a splash screen that appears when the application starts, with a Get Started action before entering the main application.

---

## Tech Stack

| Technology | Purpose |
|------------|---------|
| Expo SDK 54 | Application development and tooling |
| React Native 0.81.5 | Mobile application framework |
| React 19.1.0 | User interface |
| React Navigation | Application navigation |
| Bottom Tab Navigator | Main application navigation |
| Stack Navigator | Nested screen navigation |
| AsyncStorage | Local application data storage |
| Expo Vector Icons | Icons |
| React Native Gesture Handler | Gesture handling |
| React Native Screens | Navigation screen management |
| React Native Safe Area Context | Safe-area support |
| Expo Status Bar | Status bar configuration |
| JavaScript | Programming language |

---

## Project Structure

```text
calorix/
│
├── App.js
├── index.js
├── app.json
├── package.json
│
├── assets/
│   ├── adaptive-icon.png
│   ├── favicon.png
│   ├── icon.png
│   ├── splash-icon.png
│   └── snack-icon.png
│
├── components/
│   └── AssetExample.js
│
├── data/
│   └── foods.js
│
├── screens/
│   ├── Splash.js
│   ├── Dashboard.js
│   ├── FoodLibrary.js
│   ├── FoodDetail.js
│   ├── AddFood.js
│   ├── LogDay.js
│   ├── Favourites.js
│   └── Profile.js
│
└── utils/
    └── storage.js
```

---

## Navigation

Calorix uses React Navigation with bottom tabs and stack navigation.

### Main Navigation

The main application contains five bottom tabs:

```text
Dashboard
Library
My Log
Favourites
Profile
```

### Library Navigation

The Library tab uses stack navigation:

```text
Food Library
     │
     ├── Food Detail
     │
     └── Add Food
```

---

## Local Data Storage

Calorix is a local-only application.

There is currently no:

- Backend server
- Online database
- User account system
- Login system
- Cloud synchronisation

Application data is stored on the device using:

```text
@react-native-async-storage/async-storage
```

The main local storage keys used by the application are:

| Storage Key | Purpose |
|-------------|---------|
| `calorix_log` | Stores daily food logs |
| `calorix_favs` | Stores favourite food IDs |
| `calorix_custom` | Stores custom food entries |
| `calorix_goal` | Stores the daily calorie goal |
| `calorix_profile` | Stores profile information |

Because the application uses local storage, data belongs to the local application/device rather than an online account.

---

## Default Calorie Goal

The application starts with a default daily calorie goal of:

```text
2200 kcal
```

The user can change this goal through the Profile screen.

A personalised calorie goal can also be calculated using the user's profile, activity level, and selected weight goal.

---

## Food Data

The built-in food database is stored in:

```text
data/foods.js
```

Food records contain nutritional information such as:

- Name
- Category
- Portion
- Calories
- Protein
- Carbohydrates
- Fat

The application also allows users to create additional custom food records.

---

## Nutrition Calculations

### Calories from Macronutrients

Calorix can estimate calories from macronutrient values using:

```text
Calories =
    (Protein × 4)
  + (Carbohydrates × 4)
  + (Fat × 9)
```

### BMR

The application uses the Mifflin-St Jeor equation to calculate BMR.

Male:

```text
BMR = (10 × weight) + (6.25 × height) − (5 × age) + 5
```

Female:

```text
BMR = (10 × weight) + (6.25 × height) − (5 × age) − 161
```

### Daily Calorie Requirement

The BMR is adjusted according to the selected activity level. The selected weight goal is then applied to calculate the user's recommended daily calorie target.

---

## Getting Started

### Prerequisites

Before running Calorix, make sure you have:

- [Node.js](https://nodejs.org/) installed
- npm installed
- Expo development tools
- Expo Go installed on a physical device if you want to test on a phone
- An Android or iOS simulator if testing through an emulator

Node.js LTS is recommended.

### Installation

Clone or download the project and open the project directory:

```bash
cd calorix
```

Install the project dependencies:

```bash
npm install
```

Start the Expo development server:

```bash
npm start
```

Expo will start the development server and provide options for running the application.

---

## Running the Application

### Physical Android or iOS Device

Install Expo Go on your device.

Start the development server:

```bash
npm start
```

Then scan the QR code displayed by Expo.

### Android

```bash
npm run android
```

### iOS

```bash
npm run ios
```

### Web

```bash
npm run web
```

---

## Available NPM Scripts

```bash
npm start
npm run android
npm run ios
npm run web
```

| Command | Description |
|---------|-------------|
| `npm start` | Start the Expo development server |
| `npm run android` | Start and open the Android application |
| `npm run ios` | Start and open the iOS application |
| `npm run web` | Start and open the web version |

---

## Application Workflow

A typical user workflow is:

```text
Launch Calorix
      │
      ▼
Splash Screen
      │
      ▼
Dashboard
      │
      ├── View daily calorie progress
      │
      ├── Browse Food Library
      │       │
      │       ├── Search food
      │       ├── Filter category
      │       ├── Sort foods
      │       └── View Food Details
      │
      ├── Add food to Daily Log
      │
      ├── View Favourites
      │
      └── Manage Profile
              │
              ├── Personal information
              ├── Activity level
              ├── Weight goal
              └── Daily calorie goal
```

---

## Daily Food Tracking

The application allows users to track foods consumed throughout the day.

The general process is:

1. Open the Food Library.
2. Search or browse for a food.
3. Open the Food Detail screen.
4. Select the desired serving amount.
5. Add the food to the Daily Log.
6. View the updated nutrition totals on the Dashboard.

The Dashboard calculates the day's totals based on the foods recorded in the local daily log.

---

## Custom Food Workflow

Users can create a custom food when a food is not already available in the built-in library.

The process is:

1. Open the Food Library.
2. Open the Add Food screen.
3. Enter the food information.
4. Enter nutritional values.
5. Optionally calculate calories automatically from the macronutrients.
6. Save the food.
7. The custom food becomes available in the Food Library.

Custom foods are stored locally using AsyncStorage.

---

## Profile Workflow

Users can enter their personal information through the Profile screen.

The profile information is used to calculate a personalised calorie target.

The process is:

1. Enter gender.
2. Enter age.
3. Enter height.
4. Enter weight.
5. Select an activity level.
6. Select a weight goal.
7. Calculate the recommended calorie target.
8. Save the calorie goal.

The saved goal is then used by the Dashboard.

---

## Data Persistence

Data remains available after the application is closed and reopened because Calorix stores application data using AsyncStorage.

The stored information includes:

- Daily food logs
- Favourite foods
- Custom foods
- Profile information
- Daily calorie goal

The application does not currently synchronise this data with an online account or server.

---

## Limitations

The current version of Calorix has the following limitations:

- Data is stored locally on the device.
- There is no user authentication system.
- There is no backend server.
- There is no cloud database.
- Data is not synchronised between multiple devices.
- Built-in nutritional information depends on the food data provided in `data/foods.js`.
- Custom food nutritional information depends on the values entered by the user.
- Calorie recommendations are estimates based on the information entered by the user.

---

## Future Improvements

Possible future improvements include:

- User accounts and authentication
- Cloud database synchronisation
- Backup and restore
- Cross-device data synchronisation
- Larger food database
- Barcode scanning
- Meal planning
- Weekly and monthly nutrition reports
- Progress charts
- Weight tracking
- Water intake tracking
- More detailed nutrition information
- Improved food recommendations
- Notifications and reminders

---

## Privacy

Calorix currently stores application data locally using AsyncStorage.

No online account or backend database is required to use the core application.

Users should be aware that deleting application data or uninstalling the application may remove locally stored information.

---

## Disclaimer

Calorix is a calorie and nutrition tracking application intended for general informational and educational purposes.

Calorie calculations and nutritional information are estimates and should not be considered medical advice.

Individual calorie requirements can vary depending on many factors. Users with medical or dietary concerns should consult an appropriately qualified healthcare professional or registered dietitian.

---

## Project Information

**Project Name:** Calorix

**Platform:** React Native / Expo

**Expo SDK:** 54

**React Native:** 0.81.5

**Storage:** AsyncStorage

**Application Type:** Local calorie and nutrition tracking application

---

## Author

Hein Pyae Sone Phyo — https://github.com/HeinPyaeSonePhyo

---

## License

This project is intended for educational and project-development purposes.
