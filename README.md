# 🍣 WeFlutter Project - Sushi Ordering System & Admin Dashboard

Welcome to the **WeFlutter Project**, a comprehensive, full-stack food ordering solution built with **Flutter** and **Firebase**. This repository contains a fully-featured Customer and Driver mobile application (`sushi`), along with a powerful Web Admin Dashboard (`dashboard`).

![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=for-the-badge&logo=Firebase&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)

---

## 📱 Project Structure

This repository is a monorepo containing two main projects:

1. **`sushi/` (Mobile App)**: The main application for both Customers and Delivery Drivers.
2. **`dashboard/` (Web App)**: The Admin panel used by restaurant managers to control the entire system.

---

## ✨ Features

### 🛒 Customer App (`sushi`)
- **Authentication**: Email/Password, Google, and Facebook Sign-In, plus Biometric Auth.
- **Menu & Ordering**: Browse restaurants, categories, and items. Add to cart and place orders.
- **Favorites**: Save favorite meals for quick access.
- **Real-time Tracking**: Live order status updates and tracking using Google Maps.
- **Localization & Theming**: Supports English 🇬🇧 & Arabic 🇪🇬, and Light/Dark modes 🌓.

### 🛵 Driver App (`sushi`)
- **Driver Portal**: Dedicated UI for drivers to accept and manage incoming delivery requests.
- **Location Tracking**: Uses Geolocator and Google Maps to find customers.
- **Finances**: Track earnings and completed orders.

### 💻 Admin Dashboard (`dashboard`)
- **Analytics Overview**: View sales, revenue, and order statistics with beautiful charts (`fl_chart`).
- **Menu Management**: Add, edit, or delete restaurants, branches, categories, and items.
- **User & Driver Management**: Manage customer accounts and approve/track delivery drivers.
- **Offers**: Create and manage promotional banners and discounts.

---

## 🛠️ Tech Stack & Architecture

### Frontend (Flutter)
- **State Management**: BLoC / Cubit (`flutter_bloc`) for predictable state transitions.
- **Routing**: Standard Flutter Navigator.
- **Maps**: `google_maps_flutter`, `geolocator`, `geocoding`.
- **UI/UX**: Custom Material 3 themes, `cupertino_icons`, `cached_network_image`.

### Backend (Firebase)
- **Authentication**: `firebase_auth` (Email, Google, Facebook).
- **Database**: `cloud_firestore` (NoSQL database for users, orders, items, etc.).
- **Storage**: `firebase_storage` (For profile pictures, food images, and banners).

---

## 🚀 Getting Started

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) (^3.10.0 or higher)
- Android Studio / VS Code
- A Firebase Project linked to both apps.

### 1️⃣ Setup the Mobile App (`sushi`)
```bash
cd sushi
flutter pub get
flutter run
```
*Note: Make sure to configure your own `google-services.json` (Android) and `GoogleService-Info.plist` (iOS).*

### 2️⃣ Setup the Admin Dashboard (`dashboard`)
```bash
cd dashboard
flutter pub get
flutter run -d chrome
```

---

## 📂 Architecture overview (BLoC)

The mobile app follows a clean, feature-first folder structure using Cubits:
- `auth_cubit`: Manages user sessions and login states.
- `cart_cubit`: Handles cart operations (add/remove items, calculate totals).
- `menu_cubit`: Fetches and caches categories and food items from Firestore.
- `orders_cubit`: Listens to real-time order updates.
- `settings_cubit`: Manages Theme (Dark/Light) and Language (En/Ar) preferences via `shared_preferences`.

---

## 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/AhmedAbeed/WeFlutter-Project/issues).

## 📝 License
This project is open-source and available under the [MIT License](LICENSE).
