# WooBlocks Theme Flavors

This repository contains three flavors of the WooBlocks WordPress FSE theme, each leveraging a different CSS framework for styling. Choose the flavor that best suits your project's needs:

- **Skeleton**: Lightweight and minimal.
- **Tailwind**: Utility-first and highly customizable.
- **Bootstrap**: Classic responsive framework.

---

## **Getting Started**

### **1. Cloning the Repository**
Clone the repository and navigate to the folder of the theme flavor you wish to use:
```bash
git clone https://github.com/wooblocks-fse-base-theme.git
cd WooBlocks-Tailwind  # or WooBlocks-Skeleton / WooBlocks-Bootstrap
```

### **2. Installing Dependencies**
Each theme has its own dependencies managed via `npm`. Navigate to the theme directory and run:
```bash
npm install
```

---

## **Development Workflow**

### **1. Working with SASS (Skeleton and Bootstrap)**
Both the Skeleton and Bootstrap themes use SASS for styling. To compile SASS into CSS, use:
```bash
npm run build:css   # Compile SASS to production-ready CSS
npm run watch:css   # Watch for changes and recompile automatically
```

#### **SASS Directory Structure**
- `scss/`: Contains all SASS files.
  - `base.scss`: Core styles.
  - `utilities/`: Variables and mixins.
  - `components/`: Theme-specific components.

---

### **2. Working with Tailwind CSS**
The Tailwind theme uses a utility-first approach. Tailwind generates CSS based on your project's content.

#### **Commands**
```bash
npm run build:css   # Generate production-ready CSS
npm run watch:css   # Watch for changes and rebuild CSS automatically
```

#### **Customizing Tailwind**
Edit the `tailwind.config.js` file to extend or override default styles:
```javascript
module.exports = {
  content: ['./**/*.html', './inc/**/*.php', './blocks/**/*.js'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

---

### **3. Integrated Block Development**

All three themes support custom block development using WordPress's block editor (Gutenberg). The `blocks/` folder is where you can define and manage custom blocks.

#### **Creating a New Block**
1. Navigate to the `blocks/` directory of the theme.
2. Use the official WordPress Create Block tool to scaffold a new block:
   ```bash
   npx @wordpress/create-block my-custom-block
   ```
3. This generates a new folder with the necessary files:
   ```
   blocks/
   ├── my-custom-block/
   │   ├── block.json      # Block metadata
   │   ├── edit.js         # Block editor logic
   │   ├── save.js         # Block frontend rendering
   │   ├── style.css       # Frontend styles
   │   ├── editor.css      # Editor styles
   ```

#### **Building and Watching Blocks**
Use the following commands for block development:
```bash
npm run start   # Watch and build blocks in development mode
npm run build   # Build blocks for production
```

#### **Registering a Block**
To make a block available in WordPress, ensure the block's `block.json` is registered in `functions.php`:
```php
function enqueue_block_assets() {
    register_block_type(__DIR__ . '/blocks/my-custom-block/block.json');
}
add_action('init', 'enqueue_block_assets');
```

---

## **Folder Structure**

Each theme flavor follows the same structure:
```
WooBlocks-[Flavor]/
├── block-templates/          # FSE templates
├── block-template-parts/     # FSE template parts
├── blocks/                   # Custom Gutenberg blocks
├── scss/                     # SASS files (Skeleton and Bootstrap)
├── src/                      # Tailwind source files (Tailwind)
├── css/                      # Compiled CSS files
├── inc/                      # PHP functions
├── js/                       # JavaScript files
├── build/                    # Production-ready assets
├── functions.php             # Main theme functions
├── theme.json                # Global styles
├── README.md                 # Documentation
```

---

## **Contributing**

### **Guidelines**
1. Fork the repository.
2. Create a branch for your feature:
   ```bash
   git checkout -b feature/my-feature
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add my feature"
   ```
4. Push your branch and open a pull request.

### **Testing Changes**
- Use tools like [Query Monitor](https://wordpress.org/plugins/query-monitor/) and [Debug Bar](https://wordpress.org/plugins/debug-bar/) for debugging.
- Test performance using [Google PageSpeed Insights](https://pagespeed.web.dev/) or [GTmetrix](https://gtmetrix.com/).

---

## **License**

This project is licensed under the MIT License. Feel free to modify and use it in your projects.

---

Let me know if you need further customization for the README or any additional details!
