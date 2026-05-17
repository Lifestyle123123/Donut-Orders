# DonutOrder


A professional Minecraft plugin that enables players to create and manage item orders with a beautifully designed GUI system. Perfect for survival servers looking to streamline item trading and marketplace functionality.


---

## 📋 Features

- **📦 Order Management System**: Players can create custom item orders with specific quantities and prices
- **💰 Economy Integration**: Seamless integration with Vault for secure economy transactions
- **🎨 Beautiful GUI**: Professionally designed inventory menus with color-coded elements
- **🔍 Advanced Search & Filter**: Search for specific items and filter orders by multiple criteria
- **📊 Smart Sorting**: Sort orders by most paid, most delivered, recently listed, or money per item
- **✅ Confirmation System**: Safe delivery confirmations to prevent accidental transactions
- **🔔 Sound Effects**: Custom sound effects for enhanced user experience
- **🛡️ Folia Support**: Full compatibility with Folia for multi-threaded server performance
- **🌍 Localization**: Full multi-language support (en.yml, tr.yml) with configurable defaults
- **⚙️ Highly Configurable**: Extensive configuration options for customization

---

## 🚀 Installation

1. **Download** the latest `DonutOrder-2.1.1.jar` from the releases
2. **Install Dependencies**: Ensure you have [Vault](https://www.spigotmc.org/resources/vault.34315/) installed
3. **Place** the JAR file in your server's `plugins` folder
4. **Restart** your server
5. **Configure** the plugin by editing `plugins/DonutOrder/config.yml`

---

## 📖 Usage

### Commands

| Command | Aliases | Description | Permission |
|---------|---------|-------------|------------|
| `/orders` | `/order` | Open the orders menu | None |
| `/donutorder reload` | `/dorder`, `/dorders` | Reload the plugin configuration | `donutorder.admin` |

### Permissions

- `donutorder.admin` - Access to admin commands (default: op)

---

## 🎮 How to Use

### For Players

1. **Creating an Order**:
   - Run `/orders` to open the main menu
   - Click "Your Orders" and then "New Order"
   - Select the item you want to order
   - Set the amount and price per item
   - Confirm your order

2. **Delivering Items**:
   - Browse orders in the main menu
   - Click on an order to deliver items
   - Place the items you want to deliver in the GUI
   - Confirm the delivery to receive payment

3. **Managing Your Orders**:
   - View your active orders in "Your Orders"
   - Click on your order to collect delivered items
   - Cancel orders if needed

### For Administrators

- Configure disabled items in `config.yml`
- Customize GUI layouts, colors, and messages
- Adjust sound effects for different actions
- Set up search and filter options

---

## ⚙️ Configuration

The plugin offers extensive configuration options:

- **Disabled Items**: Prevent certain items from being ordered (e.g., spawners)
- **Custom Messages**: Personalize all player-facing messages
- **GUI Customization**: Modify menu titles, item names, lore, and slots
- **Sound Effects**: Configure sounds for clicks, confirmations, and notifications
- **Sort Names**: Customize sorting option names
- **Sign Input**: Configure sign-based input for searches and amounts

For detailed configuration, see the `config.yml` file.

---

## 🛠️ Technical Details

### Dependencies

- **Paper API**: 1.21-R0.1-SNAPSHOT
- **Vault API**: 1.7
- **Java**: 21

### Build

This plugin is built with Maven. To compile from source:

```bash
mvn clean package
```

The compiled JAR will be located in the `target` directory.

---

## 🔧 Development

### Project Structure

```
DonutOrder/
├── src/main/java/me/clanify/donutOrder/
│   ├── cmd/          # Command handlers
│   ├── gui/          # GUI menu implementations
│   ├── store/        # Data managers and storage
│   ├── catalog/      # Item catalog system
│   ├── data/         # Data models and types
│   ├── input/        # Chat and sign input handlers
│   └── util/         # Utility classes
├── src/main/resources/
│   └── plugin.yml    # Plugin metadata
├── config.yml        # Configuration file
└── pom.xml          # Maven build configuration
```


---

## 📊 Changelog

### Version 2.2.0
- **Security & Stability Overhaul (Major Update)**:
  - **Transaction Atomicity**: Fixed critical "item loss" exploit in delivery menus (Bedrock & Java).
  - **Data Integrity**: Implemented `AtomicFileUtil` to prevent data corruption on server crashes.
  - **Audit Logging**: Added `audit.log` to track all Order creations, cancellations, and deliveries.
  - **Menu Manager**: Centralized GUI handling; safe closure on reload/disable.
  - **Concurrency**: Reinforced thread safety for Folia support.

### Version 2.1.1
- **Security Audit & Hardening**:
  - **Transaction Atomicity**: Strict "Validate -> Payout -> Commit" flow to prevent "Money glitch" or "Item loss".
  - **Input Safety**: Fixed potential memory leaks and async errors in `ChatInputManager` (Thread-safe maps).
  - **Lifecycle Management**: Improved `onDisable` cleanup; open plugin GUIs are now force-closed on reload/stop.
  - **Codebase Cleanup**: Removed legacy checks and verified strict lock ordering.

### Version 2.1.0
- **Localization**:
  - Moved ALL hardcoded messages to `lang/en.yml` and `lang/tr.yml`.
  - Added `default-language` setting in `config.yml`.
  - Localized GUI Titles (e.g., "{player}'s Order" adapts to language).
- **Security & Exploits**:
  - **Fail-Safe Mode**: New global try-catch system prevents item theft if a GUI crashes.
  - **Reload Safety**: Automatically closes all order menus on plugin reload/disable.
  - **Blocked Items**: Added default blocking for Bedrock, Spawners, Command Blocks, etc.
  - **UUID Locking**: Fixed race conditions where multiple players could claim the same order.
- **GUI Improvements**:
  - "Item Selection" menu now uses Vanilla item names (Client-side language).
  - "Order List" menus use consistent localized headers.

### Version 2.0.0
- **Folia Support**: Full compatibility with Folia 1.21.11+
- **Security Hardening**:
  - Patched "Ghost Item" and duplication exploits.
  - Added Drag Protection to all menus.
  - Implemented Sign Input timeouts.
  - Added strict Economy limits (Max Order Size/Price).
- **Refactoring**:
  - Global scheduler implementation.
  - Enhanced config system.

### Version 1.1.3
- Current stable release
- Full Folia support
- Enhanced GUI system
- Improved order management
- Bug fixes and performance improvements

---

<div align="center">
  <strong>Made with ❤️ by siberanka</strong>
</div>
