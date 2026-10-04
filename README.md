# Food Ordering & Delivery Platform (WeFlutter)

A comprehensive, full-stack food ordering solution built with **Flutter** and **Firebase**. Developed as the final graduation project for the **WE Information Technology Internship Program**.

This repository contains a full-featured Customer and Driver mobile application (`sushi`), along with a dedicated Web Admin Dashboard (`dashboard`).

![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=for-the-badge&logo=Firebase&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![Architecture: BLoC / Cubit](https://img.shields.io/badge/Architecture-BLoC%2FCubit-42A5F5.svg?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)

---

## App Showcase

<div align="center">
  <img src="docs/assets/app_showcase.png" alt="Food Ordering & Delivery Platform Mobile Showcase" width="100%" />
</div>

<p align="center">
  <sub>End-to-end mobile user journey featuring Role Selection, Interactive Menu, Real-Time Cart Calculation, Live GPS Order Tracking, Promotional Offers, and Driver Dispatch Dashboard.</sub>
</p>

---

## System Architecture

The platform operates as a unified multi-role ecosystem where Customer, Driver, and Admin applications synchronize in real time through a consolidated Firebase backend.

```mermaid
graph TD
    subgraph Clients ["Client Applications (Flutter)"]
        CUST["Customer Mobile App<br/>(Browsing, Ordering, Cart, Live Tracking)"]
        DRIV["Driver Mobile App<br/>(Order Dispatch, GPS Routing, Earnings)"]
        DASH["Admin Web Dashboard<br/>(Analytics, Menu Management, Fleet Verification)"]
    end

    subgraph Backend ["Backend & Cloud Infrastructure (Firebase)"]
        AUTH["Firebase Authentication<br/>(Email/Password, Google, Facebook, Biometrics)"]
        STORE["Cloud Firestore (Real-Time NoSQL)<br/>(Users, Orders, Restaurants, Live GPS Coordinates)"]
        STORAGE["Firebase Cloud Storage<br/>(Food Images, Menus, KYC Verification Documents)"]
    end

    CUST -->|"Authenticates"| AUTH
    DRIV -->|"Authenticates"| AUTH
    DASH -->|"Admin Auth"| AUTH

    CUST -->|"Places Orders & Listens to Status"| STORE
    DRIV -->|"Accepts Orders & Streams GPS Location"| STORE
    DASH -->|"CRUD Menu, Dispatches, Audits Analytics"| STORE

    CUST -->|"Fetches Assets"| STORAGE
    DASH -->|"Uploads Banners & Dish Photos"| STORAGE
```

---

## State Management Architecture (BLoC / Cubit)

The mobile codebase follows a feature-first pattern with isolated Cubits governing distinct UI and business states across 20+ synchronized application states.

```mermaid
graph LR
    subgraph UI ["Presentation Layer"]
        Screen["Screen / Widget"]
    end

    subgraph Logic ["Cubit State Management"]
        AuthCubit["AuthCubit"]
        CartCubit["CartCubit"]
        OrderCubit["OrdersCubit (Stream)"]
        MenuCubit["MenuCubit"]
    end

    subgraph Services ["Data & Services"]
        Firestore["Cloud Firestore Streams"]
        LocalStorage["Shared Preferences (Cache)"]
    end

    Screen -->|"Invokes Intent"| Logic
    OrderCubit <-->|"Real-Time Listener"| Firestore
    MenuCubit -->|"Reads / Caches"| Firestore
    MenuCubit -->|"Local Preferences"| LocalStorage
    Logic -->|"Emits State"| Screen
```

---

## Engineering Highlights

- **Unified Multi-Interface Monorepo**: Engineered 3 distinct interfaces (Customer, Driver, and Admin) sharing centralized models and Firebase rules within a structured monorepo.
- **Real-Time GPS Tracking**: Implemented live map delivery tracking using `google_maps_flutter` and `geolocator`, reducing customer order status friction with sub-second position updates.
- **Zero-Inconsistency State Control**: Managed 20+ application states with BLoC/Cubit, eliminating state race conditions between background order updates and foreground views.
- **Enterprise Authentication**: Secured access through a 4-method authentication pipeline supporting Email/Password, Google, Facebook, and Biometric fingerprint verification.

---

## Project Structure

```
WeFlutter-Project/
├── sushi/                      # Mobile Application (Customer & Driver roles)
│   └── lib/
│       ├── cubits/             # Feature-based BLoC Cubits (Auth, Cart, Menu, Orders)
│       ├── models/             # Data models for meals, restaurants, orders, drivers
│       ├── screens/            # Customer screens, driver screens, checkout, tracking
│       ├── services/           # Firebase services, geolocation, notifications
│       └── widgets/            # Reusable UI cards, custom navigation, dialogs
│
└── dashboard/                  # Responsive Web Admin Dashboard (Flutter Web)
    └── lib/
        ├── models/             # Business metrics and analytics models
        ├── screens/            # Overview, Menu Management, Order Dispatch, Drivers
        └── widgets/            # Analytic charts (fl_chart), stat cards, tables
```

---

## Tech Stack & Dependencies

| Layer | Technologies | Purpose |
|:---|:---|:---|
| **Mobile Client** | Flutter 3.10+, Dart | Cross-platform Customer & Driver applications |
| **Web Dashboard** | Flutter Web | Responsive desktop administrative portal |
| **State Management** | `flutter_bloc` | Predictable state flow across screens |
| **Mapping & Location**| `google_maps_flutter`, `geolocator` | Real-time map rendering & route coordinates |
| **Authentication** | `firebase_auth` | Multi-provider OAuth & biometrics |
| **Cloud Database** | `cloud_firestore` | Real-time order sync and event subscriptions |
| **Cloud Storage** | `firebase_storage` | High-res food imagery and banner assets |
| **Data Visualization**| `fl_chart` | Interactive sales and revenue charts |

---

## Getting Started

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) (^3.10.0 or higher)
- Dart SDK
- Android Studio / VS Code
- A configured Firebase project with Authentication, Firestore, and Storage enabled.

### 1. Run Mobile App (`sushi`)
```bash
cd sushi
flutter pub get
flutter run
```
*Note: Ensure `google-services.json` (Android) and `GoogleService-Info.plist` (iOS) are placed in their respective platform directories.*

### 2. Run Admin Dashboard (`dashboard`)
```bash
cd dashboard
flutter pub get
flutter run -d chrome
```

---

## License

This project is open-source and available under the [MIT License](LICENSE).
