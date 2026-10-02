# Food Ordering & Delivery Platform (WeFlutter)

A comprehensive, full-stack food ordering solution built with **Flutter** and **Firebase**. Developed as the final graduation project for the **WE Information Technology Internship Program**.

This repository contains a full-featured Customer and Driver mobile application (`sushi`), along with a dedicated Web Admin Dashboard (`dashboard`).

![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=for-the-badge&logo=Firebase&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)

---

## Project Structure

This monorepo contains two primary components:

1. **`sushi/` (Mobile App)**: The cross-platform mobile client for both Customers and Delivery Drivers.
2. **`dashboard/` (Web App)**: The responsive Web Admin panel for restaurant managers to oversee menu, orders, and logistics.

---

## Features

### Customer Application
- **Multi-Method Authentication**: Email/Password, Google, Facebook, and Biometric authentication.
- **Menu & Ordering**: Dynamic browsing of restaurants, categories, and items with cart and checkout workflows.
- **Favorites**: Local and cloud synchronization of favorite dishes.
- **Real-Time Tracking**: Live delivery status updates and location tracking via Google Maps.
- **Localization & Theming**: Full Arabic (RTL) & English (LTR) localization with Light/Dark mode support.

### Driver Application
- **Driver Portal**: Dedicated interface for drivers to receive, accept, and manage delivery orders.
- **GPS Navigation**: Live routing and location tracking powered by `geolocator` and Google Maps.
- **Earnings & History**: Real-time tracking of completed deliveries and operational earnings.

### Admin Dashboard (Web)
- **Analytics Overview**: Visual reporting of sales, orders, and revenue trends with `fl_chart`.
- **Catalog Management**: Full CRUD operations for restaurants, branches, categories, and items.
- **Fleet & User Management**: Driver onboarding, status verification, and customer management.
- **Promotions**: Creation and distribution of promotional banners and discount codes.

---

## Tech Stack & Architecture

### Frontend (Flutter)
- **State Management**: BLoC / Cubit (`flutter_bloc`) for predictable, reactive state transitions across 20+ application states.
- **Navigation**: Clean Flutter Navigator routing.
- **Maps & Geolocation**: `google_maps_flutter`, `geolocator`, `geocoding`.
- **UI/UX**: Custom Material 3 design system, responsive layouts, `cached_network_image`.

### Backend (Firebase)
- **Authentication**: `firebase_auth` (Email, Social, Biometrics).
- **Database**: Cloud Firestore (real-time collections for users, orders, inventory, notifications).
- **Storage**: Cloud Storage for secure asset and media uploads.

---

## Getting Started

### Prerequisites
- Flutter SDK (^3.10.0 or higher)
- Dart SDK
- Android Studio / VS Code
- Configured Firebase project

### 1. Mobile App Setup (`sushi`)
```bash
cd sushi
flutter pub get
flutter run
```
*Note: Add your own `google-services.json` (Android) and `GoogleService-Info.plist` (iOS).*

### 2. Admin Dashboard Setup (`dashboard`)
```bash
cd dashboard
flutter pub get
flutter run -d chrome
```

---

## State Management Architecture (BLoC)

The mobile application utilizes a feature-first architecture driven by modular Cubits:
- `auth_cubit`: Manages user authentication, profile data, and session states.
- `cart_cubit`: Handles cart management, discount calculations, and checkout.
- `menu_cubit`: Real-time caching and fetching of restaurant items and categories.
- `orders_cubit`: Stream-based listening to live order status transitions.
- `settings_cubit`: Persistent theme and language preferences via `shared_preferences`.

---

## License

This project is licensed under the [MIT License](LICENSE).
