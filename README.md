# React + TypeScript + Vite + Capacitor

This template provides a minimal setup to get **React** working in **Vite** with **HMR**, some **ESLint** rules, and **Capacitor** for native mobile app development.

## 🚀 Setup Instructions

### 1️⃣ Install Dependencies
Run the following command to install all required dependencies:

```sh
npm install
```

### 2️⃣ Run the Vite Development Server
To start the app in the browser:

```sh
npm run dev
```

---

## 🛠 ESLint Configuration

Currently, two official plugins are available for React with Vite:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh.
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh.

### 🔹 Expanding the ESLint Configuration
If you are developing a production application, we recommend updating the configuration to enable **type-aware lint rules**:

#### **1. Update `parserOptions`**
Modify your ESLint config:

```js
export default tseslint.config({
  languageOptions: {
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

#### **2. Strengthen TypeScript Rules**
Replace:

```js
tseslint.configs.recommended
```

With:

```js
tseslint.configs.recommendedTypeChecked
```

Or:

```js
tseslint.configs.strictTypeChecked
```

Optionally, add:

```js
...tseslint.configs.stylisticTypeChecked
```

#### **3. Add `eslint-plugin-react`**
Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react):

```sh
npm install eslint-plugin-react --save-dev
```

Then, update the ESLint configuration:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  settings: { react: { version: '18.3' } },
  plugins: {
    react,
  },
  rules: {
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```

---

## 📱 Running Capacitor for Android & iOS

### 1️⃣ Install Capacitor
If you haven't already installed Capacitor, run:

```sh
npm install @capacitor/core @capacitor/cli
```

### 2️⃣ Add Platforms
To enable native builds, add the platforms:

```sh
npx cap add android
npx cap add ios
```

### 3️⃣ Sync Project Files
Whenever you change something in your React project, sync Capacitor:

```sh
npx cap sync
```

or for a specific platform:

```sh
npx cap sync android
npx cap sync ios
```

---

## 🤖 Running on Android

### **1. Open in Android Studio**
```sh
npx cap open android
```
Then, click **Run ▶** inside Android Studio.

### **2. Run Directly on a Device**
If you have a connected Android device or emulator running:

```sh
npx cap run android
```

### **3. Generate a Signed APK**
To build a release APK:

```sh
cd android
./gradlew assembleRelease
```

The APK will be in:

```
android/app/build/outputs/apk/release/app-release.apk
```

---

## 🍏 Running on iOS

### **1. Open in Xcode**
```sh
npx cap open ios
```
Then, build and run the app using **Xcode**.

### **2. Run Directly on a Device**
If you have a connected iOS device:

```sh
npx cap run ios
```

### **3. Generate an IPA for App Store**
1. Open **Xcode**.
2. Select **Any iOS Device (arm64)**.
3. Go to **Product > Archive**.
4. Export the IPA from Xcode Organizer.

---

## 🎯 Additional Commands

### **Run a Clean Build**
If you experience issues, try cleaning and rebuilding:

```sh
npx cap sync
npx cap clean android
npx cap clean ios
```

### **Reinstall Dependencies**
```sh
rm -rf node_modules package-lock.json
npm install
npx cap sync
```

### **Debugging with Logs**
```sh
npx cap run android --target emulator --verbose
```

```sh
npx cap run ios --target emulator --verbose
```

---

This setup allows you to build and deploy your React + TypeScript + Vite + Capacitor app on both **Android** and **iOS** seamlessly. 🚀

