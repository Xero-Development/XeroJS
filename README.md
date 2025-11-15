# **XeroJS – Official Client SDK for .xo Extensions**

![License](https://img.shields.io/badge/License-XODL-blue.svg)
![Node](https://img.shields.io/badge/Node.js-18%2B-green.svg)
![Status](https://img.shields.io/badge/Build-Stable-brightgreen.svg)
![Platform](https://img.shields.io/badge/Platform-Discord%20Client-lightgrey.svg)
![Framework](https://img.shields.io/badge/Framework-Xero-blue.svg)

XeroJS is the scripting engine behind the Xero ecosystem.
It powers `.xo` files, extensions, UI modules, and advanced client hooks for **XeroCord**.

---

# **📘 Table of Contents**

1. [Overview](#overview)
2. [Key Features](#key-features)
3. [Project Structure](#project-structure)
4. [Installation](#installation)
5. [XO Script Basics](#xo-script-basics)
6. [JavaScript API Usage](#javascript-api-usage)
7. [Core Modules](#core-modules)
8. [Events](#events)
9. [UI API](#ui-api)
10. [Security Model](#security-model)
11. [Development Workflow](#development-workflow)
12. [License](#license)
13. [Support](#support)

---

# **1. Overview**

**XeroJS** is a modular, sandboxed client SDK that loads and executes `.xo` scripts inside XeroCord.
It enables developers to extend the Discord client with **custom UI**, **hooks**, **events**, and **runtime injections**—without altering the core client.

---

# **2. Key Features**

✔ Complete `.xo` file parsing & execution
✔ Secure sandbox with limited JS functions
✔ Binding layer to XeroCord client
✔ Event-driven runtime (ready, message, UI, system)
✔ Custom UI generation (panels, buttons, toggles, etc.)
✔ Plugin isolation & error protection
✔ Developer-friendly API surface
✔ Fast load times with lazy execution

---

---

# **3. Installation**

### **From Source**

```sh
git clone https://github.com/xero-project/XeroJS.git
cd XeroJS
npm install
```

### **Run SDK**

```sh
node xero.js
```

---

# **4. XO Script Basics**

`.xo` files use a simple controlled scripting language.

### **Example:**

```xo
event onReady {
  log("XeroJS Loaded!");
}

ui.addButton {
  label: "Ping",
  onClick: {
    log("Pong!");
  }
}
```

---

# **5. JavaScript API Usage**

```js
const Xero = require("./xero");

const script = Xero.parse("./plugins/example.xo");
script.run();
```

---

# **6. Core Modules**

### **🔹 Parser**

* Tokenizes `.xo` syntax
* Builds AST
* Validates unsafe calls

### **🔹 Runtime**

* Manages execution state
* Handles internal events
* Manages memory lifecycle

### **🔹 UI Layer**

* Adds panels & widgets to XeroCord
* Supports buttons, groups, inputs, toggles

### **🔹 Sandbox**

* Removes dangerous JS globals
* Implements safe eval
* Rate-limits heavy operations

---

# **7. Events**

Common `.xo` events:

| Event         | Description                         |
| ------------- | ----------------------------------- |
| `onReady`     | Fires when XeroJS finishes loading  |
| `onMessage`   | Triggers when a message is received |
| `onClick`     | Fires from UI events                |
| `onPanelOpen` | When UI panel is opened             |
| `onInject`    | When client injection completes     |

---

# **8. UI API**

### **Panels**

```xo
ui.addPanel {
  name: "My Tools",
  content: "<h2>Tools Loaded</h2>"
}
```

### **Buttons**

```xo
ui.addButton {
  label: "Click Me",
  onClick: {
    log("Clicked!");
  }
}
```

### **Toggles**

```xo
ui.addToggle {
  label: "Enable Mode",
  state: false,
  onToggle: {
    log("Toggled!");
  }
}
```

---

# **9. Security Model**

XeroJS enforces:

* No direct Node.js module access
* No `require()` usage inside `.xo` files
* Restricted global objects
* Sandboxed runtime with error isolation
* Rate-limited async operations
* Explicit whitelisted FS operations

This ensures that plugins **cannot harm the client** or perform system-level actions.

---

# **10. Development Workflow**

### **1. Write your XO script**

Create a file in:

```
/XeroCord/plugins/
```

### **2. Test via CLI**

```sh
node xero.js test ./plugins/example.xo
```

### **3. Load into XeroCord**

XeroCord automatically loads all `.xo` scripts on launch.

---

# **11. License**

Licensed under the **Xero Open Development License (XODL)**.
Free for personal & open development use.

---

# **12. Support**

📌 Discord: [https://discord.gg/7am95PkR](https://discord.gg/7am95PkR)
📌 Docs (In Progress): Coming soon

---
