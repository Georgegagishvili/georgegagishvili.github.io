# Asset Links for Android App Verification

This repository hosts the `assetlinks.json` file required for Android App Links verification. It's designed to be deployed on GitHub Pages to provide a publicly accessible endpoint for your Android app's digital asset links.

## 📱 What is this?

Android App Links allow your Android app to handle URLs from your domain. The `assetlinks.json` file is a JSON document that declares the relationship between your website and your Android app, enabling deep linking functionality.

## 🚀 Quick Setup

### 1. Fork or Clone this Repository

```bash
git clone https://github.com/[your-username]/assetlinks.git
cd assetlinks
```

### 2. Customize the assetlinks.json

Edit `.well-known/assetlinks.json` with your app's information:

```json
[
  {
    "relation": ["delegate_permission/common.handle_all_urls"],
    "target": {
      "namespace": "android_app",
      "package_name": "com.yourcompany.yourapp",
      "sha256_cert_fingerprints": ["YOUR:SHA256:FINGERPRINT:HERE"]
    }
  }
]
```

### 3. Enable GitHub Pages

1. Go to your repository settings on GitHub
2. Scroll down to "Pages" section
3. Under "Source", select "Deploy from a branch"
4. Choose the main branch (or master)
5. Click "Save"

### 4. Access Your Asset Links

Once deployed, your asset links will be available at:

```
https://[your-username].github.io/assetlinks/.well-known/assetlinks.json
```

## 🔧 Configuration

### Current Configuration

This repository is currently configured for:

- **Package Name**: `com.noxtton.msquare`
- **Permission**: `delegate_permission/common.handle_all_urls`
- **SHA256 Fingerprints**: Configured for your app's signing certificates

### How to Get SHA256 Fingerprints

1. **For Debug builds**:

   ```bash
   keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
   ```

2. **For Release builds**:
   ```bash
   keytool -list -v -keystore your-release-key.keystore -alias your-key-alias
   ```

## 📋 File Structure

```
assetlinks/
├── index.html              # Landing page
├── README.md              # This file
└── .well-known/
    └── assetlinks.json    # Asset links configuration
```

## 🔍 Testing

You can test if your asset links are working by:

1. Visiting the GitHub Pages URL
2. Using Google's Asset Links Generator: https://developers.google.com/digital-asset-links/tools/generator
3. Testing with your Android app's deep linking functionality

## 🛠️ Troubleshooting

### If assetlinks.json returns 404

If you're getting a 404 error when accessing `/.well-known/assetlinks.json`, try these solutions:

1. **Wait for deployment**: GitHub Pages can take a few minutes to deploy changes
2. **Check the `.nojekyll` file**: This file disables Jekyll processing and ensures all files are served
3. **Verify the URL**: Make sure you're using the correct GitHub Pages URL format:
   ```
   https://[your-username].github.io/assetlinks/.well-known/assetlinks.json
   ```
4. **Check repository settings**: Ensure GitHub Pages is enabled and pointing to the correct branch

### Alternative Solution

If the `.well-known` directory still doesn't work, you can also place the `assetlinks.json` file in the root directory and access it at:

```
https://[your-username].github.io/assetlinks/assetlinks.json
```

## 📚 Resources

- [Android App Links Documentation](https://developer.android.com/training/app-links)
- [Digital Asset Links Specification](https://developers.google.com/digital-asset-links/v1/getting-started)
- [Asset Links Generator](https://developers.google.com/digital-asset-links/tools/generator)

## 🤝 Contributing

Feel free to fork this repository and customize it for your own Android app. The structure is designed to be simple and easily deployable on GitHub Pages.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
