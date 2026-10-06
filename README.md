# Sarah Multistore - Native Flutter Mobile App

**Sarah Multistore** is a production-ready, native mobile e-commerce application developed in **Flutter & Dart** with **Firebase backend services**, designed for Saddam's perfume and multi-product retail shop.

---

## 📱 Application Overview

- **App Name:** Sarah Multistore
- **Owner:** Saddam
- **Platform:** Native Android (Primary, package `com.sarahmultistore.app`) with iOS future-readiness
- **Design System:** Material 3 with luxury perfume styling (Deep Burgundy `#6A1428` & Amber Gold `#C59B27`)
- **Backend Services:** Firebase Authentication, Cloud Firestore, Firebase Storage, Firebase Cloud Messaging
- **State Management:** Provider Architecture (`ChangeNotifierProvider`)

---

## 📁 Complete Project Structure

```
c:\Users\DELL\OneDrive\Documents\flutter\
│
├── pubspec.yaml                 # Dependencies and asset declarations
├── firestore.rules              # Production Firestore security rules
├── storage.rules                # Production Firebase Storage security rules
├── firebase.json                # Firebase configuration & deploy manifest
├── firestore.indexes.json       # Composite query index definitions
│
├── android/
│   ├── build.gradle             # Android root Gradle configuration
│   ├── settings.gradle          # Plugin & module loader
│   ├── gradle.properties        # Memory and AndroidX flags
│   └── app/
│       ├── build.gradle         # App-level Gradle (namespace: com.sarahmultistore.app)
│       ├── google-services.json.example
│       └── src/main/
│           ├── AndroidManifest.xml # Permissions (Internet, Camera, Notifications)
│           ├── kotlin/com/sarahmultistore/app/MainActivity.kt
│           └── res/             # Launchers, themes, and string resources
│
├── ios/
│   └── Runner/Info.plist        # iOS bundle configuration & camera/photo permissions
│
├── assets/
│   ├── images/logo.png          # High-resolution store branding logo
│   └── icons/app_icon.png       # App launcher icon
│
└── lib/
    ├── main.dart                # App entry point with safe Firebase bootstrap
    ├── firebase_options.dart    # FlutterFire credentials configuration
    │
    ├── app/
    │   ├── app.dart             # Root MultiProvider wrapper & MaterialApp
    │   ├── routes.dart          # Centralized named route generator
    │   └── theme.dart           # Material 3 Luxury Perfume theme
    │
    ├── models/
    │   ├── user_model.dart      # User profile with 'customer' / 'admin' roles
    │   ├── category_model.dart  # Dynamic category model
    │   ├── variant_model.dart   # Value, Unit, Price, Stock per variant
    │   ├── product_model.dart   # Product document with embedded variant list
    │   ├── cart_item_model.dart # Shopping cart state model
    │   ├── order_model.dart     # Order snapshot structure with order sequence
    │   └── shop_settings_model.dart # Shop name, Saddam owner info, WhatsApp
    │
    ├── services/
    │   ├── auth_service.dart    # Firebase Auth & Firestore role sync
    │   ├── product_service.dart # Realtime Firestore product stream & CRUD
    │   ├── category_service.dart# Category streaming & admin management
    │   ├── order_service.dart   # Atomic Firestore transactions for stock validation
    │   ├── storage_service.dart # Phone gallery picker & Firebase Storage upload
    │   ├── notification_service.dart # FCM & local notification triggers
    │   ├── settings_service.dart# Shop info realtime sync
    │   └── sample_data_service.dart # Sample perfumes seeder
    │
    ├── providers/
    │   ├── auth_provider.dart   # Authentication state management
    │   ├── product_provider.dart# Product catalog, sorting, and search filters
    │   ├── category_provider.dart # Category state
    │   ├── cart_provider.dart   # Shopping cart management
    │   ├── order_provider.dart  # Order placement & admin order tracking
    │   └── settings_provider.dart # Shop settings provider
    │
    ├── screens/
    │   ├── splash/splash_screen.dart # Animated branding splash screen
    │   ├── auth/
    │   │   ├── login_screen.dart     # Customer & Admin login
    │   │   └── register_screen.dart  # Customer account creation
    │   ├── customer/
    │   │   └── customer_main_nav.dart # 5-tab bottom navigation
    │   ├── home/home_screen.dart     # Hero banner, categories, featured & latest
    │   ├── categories/categories_screen.dart # All categories grid
    │   ├── products/product_list_screen.dart # Search, price & stock filtering
    │   ├── product_details/product_details_screen.dart # Multi-ML dynamic pricing
    │   ├── cart/cart_screen.dart     # Working shopping cart with item controls
    │   ├── checkout/checkout_screen.dart # Delivery details & COD order placement
    │   ├── orders/
    │   │   ├── my_orders_screen.dart # Customer order history
    │   │   └── order_details_screen.dart # Order timeline & item snapshots
    │   ├── profile/profile_screen.dart # Profile and owner admin portal access
    │   └── admin/
    │       ├── admin_dashboard_screen.dart # Sales stats, metrics & quick actions
    │       ├── admin_products_screen.dart  # Catalog inventory management
    │       ├── add_edit_product_screen.dart# Dynamic multi-variant product creator
    │       ├── admin_orders_screen.dart    # Status filter tabs (NEW, PREPARING...)
    │       ├── admin_order_details_screen.dart # Customer contact & status changer
    │       ├── admin_categories_screen.dart# Category CRUD
    │       └── admin_settings_screen.dart  # Store info & sample data seeder
    │
    ├── widgets/
    │   ├── product_card.dart    # Product grid item with image caching
    │   ├── category_card.dart   # Category pill/card
    │   ├── cart_item_tile.dart  # Cart quantity increment/decrement tile
    │   ├── order_card.dart      # Order receipt summary card
    │   ├── variant_selector.dart# Multi-ML selector chips with price display
    │   ├── status_badge.dart    # Color-coded order status badge
    │   ├── order_timeline.dart  # Visual order progress stepper
    │   ├── custom_button.dart   # Reusable button with loading indicators
    │   ├── custom_text_field.dart # Form text inputs
    │   └── app_drawer.dart      # Navigation drawer with admin shortcut
    │
    └── utils/
        ├── constants.dart       # AppConstants & AppColors
        ├── currency_formatter.dart # Indian Rupee (₹) number formatting
        └── validators.dart      # Input validation utilities
```

---

## 🛠️ Step-by-Step Setup Instructions

### 1. Install Flutter SDK (if not already installed)
1. Download the Flutter SDK for Windows from [flutter.dev](https://flutter.dev/docs/get-started/install/windows).
2. Extract the zip to `C:\src\flutter`.
3. Add `C:\src\flutter\bin` to your Windows System Environment Variables `PATH`.
4. Open PowerShell and run:
   ```powershell
   flutter doctor
   ```

### 2. Configure Firebase Project
1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Create a new project named **Sarah Multistore** (or `sarah-multistore`).
3. Under **Authentication**, click **Get Started** and enable **Email/Password**.
4. Under **Firestore Database**, click **Create Database** (Start in Production mode or test mode).
5. Under **Storage**, click **Get Started** and create your default storage bucket.
6. Under **Project Settings (Gear icon) > General > Your Apps**:
   - Click the **Android** icon.
   - Enter Android package name: `com.sarahmultistore.app`
   - Enter App nickname: `Sarah Multistore`
   - Click **Register App**.
   - Download `google-services.json`.
   - Place this file in `android/app/google-services.json`.

### 3. Deploy Firebase Security Rules
Open a terminal in the project directory:
```powershell
firebase login
firebase use --add <your-project-id>
firebase deploy --only firestore:rules,storage:rules
```

---

## 🚀 How to Run the App

1. Fetch all dependencies:
   ```powershell
   flutter pub get
   ```

2. Connect an Android phone via USB (with USB Debugging enabled) or launch an Android emulator.

3. Run the application:
   ```powershell
   flutter run
   ```

---

## 👑 Creating Saddam's Admin Account

1. Open the app on your phone.
2. Tap the menu icon in the top left > tap **Sign In / Register** > tap **Register Now**.
3. Register Saddam's account:
   - **Name:** Saddam
   - **Email:** saddam@sarahmultistore.com (or your preferred email)
   - **Password:** (Choose a secure password)
   - **Phone:** (Your mobile number)
4. Promote this account to `admin` in Cloud Firestore:
   - Go to **Firebase Console > Firestore Database > `users` collection**.
   - Find the document corresponding to Saddam's UID.
   - Change the `role` field value from `"customer"` to `"admin"`.
5. Re-open or sign in to the app with Saddam's email.
6. The **Owner Admin Panel** will automatically unlock in the drawer and profile screen, granting full access to Dashboard, Inventory, Orders, Categories, and Shop Settings.

---

## 📦 How to Add Products with Multiple ML / Size Variants

1. In the Admin Panel, navigate to **Manage Products** or tap **+ Add Product**.
2. Fill in:
   - **Product Name:** e.g., `Wild Stone Perfume`
   - **Category:** Select `Perfumes`
   - **Description:** e.g., `Premium woody and musky fragrance.`
   - **Product Image:** Tap **Pick from Gallery** to upload from your phone camera/gallery directly to Firebase Storage.
3. Under **Size & ML Variants**:
   - Variant #1: Size `30`, Unit `ml`, Price `150`, Stock `10`
   - Variant #2: Size `50`, Unit `ml`, Price `220`, Stock `8`
   - Variant #3: Size `100`, Unit `ml`, Price `380`, Stock `5`
   - Tap **+ ADD VARIANT** if you want to add more sizes or units (e.g., `200 ml`, `50 g`, `1 piece`).
4. Tap **SAVE PRODUCT**.
5. When a customer views this product, selecting `30 ml`, `50 ml`, or `100 ml` will automatically update the displayed price and check variant stock in real time!

---

## 🏗️ How to Build Android APK and App Bundle (AAB)

### Build Release APK:
Run in your project directory:
```powershell
flutter build apk --release
```
The generated APK file will be located at:
`build\app\outputs\flutter-apk\app-release.apk`

### Build Release App Bundle (for Google Play Store):
```powershell
flutter build appbundle --release
```
The generated AAB file will be located at:
`build\app\outputs\bundle\release\app-release.aab`

---

## 📲 How to Install the APK on Android Phone

1. Copy `app-release.apk` to your Android phone via USB cable, Google Drive, or WhatsApp.
2. On your phone, tap the file in your File Manager or Downloads.
3. If prompted with *"Install unknown apps"*, allow permission for your File Manager or Chrome.
4. Tap **Install**.
5. **Sarah Multistore** will be installed as a native Android app with the official app icon and title.
