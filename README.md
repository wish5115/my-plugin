# My Plugin User Guide

## 📖 Introduction

My Plugin is a SiYuan Note plugin development template that provides a basic framework and common feature examples for plugin development.

**Plugin Name:**  My Plugin  
**Author:**  Wilson  
**Version:**  0.0.1  
**License:**  MIT  
**Minimum Required Version:**  SiYuan 3.0.12+

---

## ✨ Key Features

### 1. Command Palette

- **Hotkey:**  `⇧⌘O` (Shift + Command + O)
- **Function:**  Open custom dialog
- **Description:**  Quickly open the demo dialog via command palette or hotkey

### 2. Custom Dock Panel

- **Hotkey:**  `⌥⌘W` (Option + Command + W)
- **Position:**  Bottom Left
- **Features:**

  - Desktop: Embedded Baidu webpage iframe
  - Mobile: Display custom text
- **Size:**  Width 200px, height adaptive

### 3. Plugin Settings

- **Configuration:**  Readonly text
- **Description:**  Configure readonly text content in the settings panel, which will be saved to `config.json`

### 4. Style Customization

- **Example:**  Set note title input box color to blue
- **File:**  `index.css`

---

## 📦 Project Structure

```
my-plugin/
├── node_modules/           # Node modules, for IDE development hints
├── i18n/                   # Internationalization files
│   ├── en_US.json          # English
│   └── zh_CN.json          # Simplified Chinese
├── icon.png                # Plugin icon
├── preview.png             # Plugin preview image
├── index.js                # Plugin main logic
├── index.css               # Plugin styles
├── plugin.json             # Plugin configuration
├── build.sh                # Linux/macOS build script
├── build.bat               # Windows build script
├── LICENSE                 # Open source license
├── README.md               # English documentation
└── README-zh.md            # Chinese documentation
```

---

## 🚀 Quick Start

### Installation

#### Method 1: Install from Source

1. Clone or download this repository
2. Copy the `my-plugin` folder to SiYuan's plugin directory:

    - Windows: `{workspace}/data/plugins/`
    - macOS/Linux: `{workspace}/data/plugins/`
3. Restart SiYuan or refresh the plugin list in settings
4. Enable "My Plugin"

#### Method 2: Install from Package

1. Run the build script:

    ```
    # Linux/macOS
    bash build.sh

    # Windows
    build.bat
    ```
2. Extract the generated `package.zip` to the plugin directory
3. Restart SiYuan

---

## 🛠️ Development Guide

### Requirements

- Node.js (for development and debugging)
- SiYuan 3.0.12 or higher

### Core API Usage

#### 1. Plugin Lifecycle

```
module.exports = class MyPlugin extends Plugin {
    onload() {
        // Executed when plugin is loaded
    }
    
    onLayoutReady() {
        // Executed after page layout is ready
    }
    
    onunload() {
        // Executed when plugin is unloaded
    }
    
    uninstall() {
        // Executed when plugin is deleted
    }
}
```

#### 2. Adding Commands

```
this.addCommand({
    langKey: "showDialog",      // i18n key
    hotkey: "⇧⌘O",            // Hotkey
    callback: () => {
        this.showDialog();      // Callback function
    },
});
```

#### 3. Adding Dock Panel

```
this.addDock({
    config: {
        position: "LeftBottom", // Position
        size: {width: 200, height: 0},
        icon: "iconSaving",     // Icon
        title: "Custom Dock",   // Title
        hotkey: "⌥⌘W",         // Hotkey
    },
    init: (dock) => {
        // Initialize UI
    },
    // ... other callbacks
});
```

#### 4. Creating Dialogs

```
const dialog = new Dialog({
    title: "Title",
    content: "<div>Content</div>",
    width: "560px",
    height: "540px",
});
```

#### 5. Settings Panel

```
this.setting = new Setting({
    confirmCallback: () => {
        // Save configuration
        this.saveData(STORAGE_NAME, data);
    }
});

this.setting.addItem({
    title: "Setting Item Title",
    description: "Setting item description",
    createActionElement: () => {
        // Return form element
    },
});
```

### Data Persistence

```
// Save data
this.saveData(STORAGE_NAME, {key: "value"});

// Load data
const data = this.data[STORAGE_NAME];
```

### Internationalization (i18n)

Add language files in the `i18n/` directory:

```
{
  "showDialog": "Open Dialog"
}
```

---

## 📝 Build & Release

### Automatic Build

Running the build script automatically excludes the following files/directories:

- ​`.git/`
- ​`.gitignore`
- ​`.history/`
- ​`.idea/`
- ​`.DS_Store`
- ​`node_modules/`
- ​`build.sh`
- ​`build.bat`
- ​`.hotreload`

### Manual Build

Compress the following files into `package.zip`:

```
- i18n/
- icon.png
- preview.png
- index.js
- index.css
- plugin.json
- README.md
- README-zh.md
- LICENSE
```

---

## 🔧 Configuration

### plugin.json Fields

|Field|Description|
| -------| ------------------------------------------|
|​`name`|Unique plugin identifier (English)|
|​`author`|Author name|
|​`url`|Project homepage URL|
|​`version`|Plugin version number|
|​`minAppVersion`|Minimum supported SiYuan version|
|​`backends`|Backend supported platforms (`["all"]`for all)|
|​`frontends`|Frontend supported platforms (`["all"]`for all)|
|​`displayName`|Plugin display name (i18n supported)|
|​`description`|Plugin description (i18n supported)|
|​`readme`|Documentation file path (i18n supported)|
|​`funding`|Sponsorship links|

---

## 🐛 Debugging Tips

1. **View Logs**  
    Open SiYuan DevTools (`F12`) and check console logs
2. **Reload**  
    After modifying code, press `Ctrl+R` (Windows/Linux) or `⌘+R` (macOS) to reload in the devtools panel
3. **Breakpoint Debugging**  
    Use `debugger`​ statement in `index.js` or set breakpoints in DevTools

---

## 📄 License

This project is licensed under the **MIT** License.  
See the [LICENSE](https://cursor.com/cn/LICENSE) file for details.

---

## 🤝 Contributing

Issues and Pull Requests are welcome!

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📧 Contact

- **Project Homepage:**  [https://github.com/wish5115/my-plugin](https://github.com/wish5115/my-plugin)
- **Author:**  Wilson
- **Sponsor:**  [View QR Code](https://b3logfile.com/file/2025/06/image-fEA9BRv.png)

---

## 🙏 Acknowledgments

Thanks to the [SiYuan Note](https://github.com/siyuan-note/siyuan) team for providing an excellent plugin development framework!

---

**Enjoy using My Plugin!**  🎉
