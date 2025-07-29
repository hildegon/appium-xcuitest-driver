# Installing and Using the XCUITest Driver

This fork of the appium-xcuitest-driver has been updated to be fully compatible with Appium 2.x.

## Installation

To install this driver for use with Appium, you have several options:

### Option 1: Install from local directory (Recommended for development)

```bash
# Clone or download this repository
git clone https://github.com/hildegon/appium-xcuitest-driver.git
cd appium-xcuitest-driver

# Install dependencies and build
npm install

# Install the driver in Appium
appium driver install /path/to/appium-xcuitest-driver --source=local
```

### Option 2: Install from tarball

```bash
# Build the package
npm pack

# Install the driver in Appium
appium driver install ./appium-xcuitest-driver-9.7.0.tgz --source=local
```

## Verification

After installation, you can verify the driver is properly installed:

```bash
# List installed drivers
appium driver list

# Start Appium server (driver will be automatically loaded)
appium server --port 4723
```

You should see output similar to:
```
✔ Listing available drivers
- xcuitest@9.7.0 [installed (linked from /path/to/appium-xcuitest-driver)]
```

## Usage

Once installed, you can use this driver in your Appium test scripts by specifying the automation name:

```javascript
const capabilities = {
  platformName: 'iOS',
  automationName: 'XCUITest',
  deviceName: 'iPhone Simulator',
  // ... other capabilities
};
```

## Changes Made

This fork includes the following updates to make it compatible with Appium 2.x:

1. **Added missing scripts**:
   - `tunnel-creation.mjs` - For tunnel creation functionality
   - `download-wda-sim.mjs` - For WebDriverAgent download functionality
   - `utils.js` - Utility functions used by the scripts

2. **Updated dependencies**:
   - Added `appium-ios-remotexpc` for remote XPC functionality
   - Added `@appium/strongbox` for secure storage
   - Added `@appium/support` for updated Appium support utilities

3. **Updated package.json**:
   - Added the new scripts to the `appium.scripts` configuration
   - Updated dependencies list

## Troubleshooting

If you encounter issues installing the driver:

1. Make sure you're using Appium 2.x (`npm list -g appium`)
2. Ensure all dependencies are installed (`npm install` in the driver directory)
3. Use the `--source=local` flag when installing
4. Check that the driver appears in `appium driver list`

## Development

To work on this driver:

```bash
# Install dependencies
npm install

# Build the TypeScript code
npm run build

# Run tests
npm test

# Run linting
npm run lint
```