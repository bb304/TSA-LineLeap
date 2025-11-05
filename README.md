✈️ ##LineLeap##

This is a React Native (Expo) application designed to optimize airport security foot traffic. It allows passengers to pre-book a time slot for their TSA security check, reducing queue times and improving the overall airport experience.

The app segments passengers into selectable time slots, which allows people to wait less at the airport while still enabling them to arrive earlier if they wish to visit shops. This system generates a unique QR code for each booking, which is then scanned by TSA personnel for validation and entry during the selected time period.

✨ Key Features

Passenger Time Slots: Travelers can select a specific time slot to go through security, based on their flight.

Reduced Wait Times: Helps passengers plan their airport arrival and avoid long, unpredictable queues.

Optimized Foot Traffic: Smooths out passenger flow, reducing congestion at security checkpoints while still encouraging traffic for airport retailers.

QR Code Generation: Generates a unique QR code for each booked time slot.

TSA Validation: Includes a simple validation screen (/validate) to check if a passenger's QR code is valid for the current time.

Admin Panel: A secure section (/tsaLogin and /tsa) for TSA personnel to manage flight details, including passenger counts, security windows (start/end times), and the number of available slots.

Real-time Backend: Uses Firebase Firestore to manage flight data and slot availability in real-time.

⚙️ How It Works

For Passengers

Find Flight: The user finds their upcoming flight in the app.

Select Slot: They are presented with available time slots for security, based on capacity managed by the TSA admin.

Book & Get QR Code: Upon selecting a slot, the app reserves their spot and generates a unique QR code.

Scan at TSA: The passenger arrives at the TSA checkpoint during their selected time, scans their QR code, and proceeds to security.

For TSA Admins

Login: TSA staff log in through a dedicated login screen (/tsaLogin).

Manage Flights: Staff can add new flights, specifying the flight number, date, total passenger count, and the time window for security screening.

Set Slot Capacity: The system automatically divides the passenger load across the available time slots.

Validate Passengers: At the checkpoint, TSA staff use a scanner (or the validate screen) to verify passengers' QR codes and ensure they are arriving within their booked time.

🚀 Tech Stack

Framework: React Native (Expo)

Navigation: Expo Router (file-based)

Backend: Firebase (Firestore)

QR Codes: react-native-qrcode-svg

Language: TypeScript

🏁 Getting Started

1. Prerequisites

Node.js (LTS version recommended)

Expo Go app on your iOS or Android device (for testing)

A Firebase project.

2. Installation

Clone the repository:

git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name


Install dependencies:

npm install


3. Firebase Setup

This app requires a Firebase project to function.

Go to the Firebase Console and create a new project.

Add a "Web" app to your project.

Copy the firebaseConfig object given to you.

Create a new file in the root of this project named firebaseConfig.js.

Paste your config into the file, like so:

// File: firebaseConfig.js
import { initializeApp } from "firebase/app";
import { getFirestore } in 'firebase/firestore';
import { getAuth } from 'firebase/auth';

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
const auth = getAuth(app);
export { db, auth };


In the Firebase Console, go to Firestore Database and create a new database. Start in test mode (or set up security rules to allow reads/writes).

Go to Authentication and enable the Email/Password sign-in method (or any other method you prefer for user/TSA login).

4. Run the App

Start the development server:

npx expo start


Scan the QR code from the terminal with the Expo Go app on your phone.
