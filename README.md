# Scoreeboard

A modern, lightweight scoreboard application built with Vue 3 and Vite. This project allows users to manage player setups and control scores dynamically through a clean web interface.

## 🚀 Features

- **Player Management**: Setup and manage player profiles using the `PlayerSetup.vue` component.
- **Dynamic Score Control**: Increment or decrement scores in real-time with the `ScoreControl.vue` component.
- **Reactive Logic**: Built using Vue 3's Composition API for efficient state management and reactivity.
- **Fast Development**: Optimized development environment using Vite and Sass.

## 📂 Project Structure

The project follows a standard Vue.js directory layout:

```
Scoreeboard/
├── src/
│   ├── components/
│   │   ├── PlayerSetup.vue     # Player configuration logic
│   │   └── ScoreControl.vue    # Score adjustment interface
│   ├── assets/
│   │   ├── main.scss           # Global styles
│   │   └── image.png           # Static assets
│   ├── App.vue                 # Main application entry point
│   └── main.js                 # Vue application initialization
├── public/                     # Static files (favicon, etc.)
└── vite.config.js              # Vite configuration
```

## 🛠️ Tech Stack

- **Framework**: Vue.js 3.5+
- **Build Tool**: Vite 8.0+
- **Styling**: Sass
- **Editor**: VS Code with Volar

## 📥 Installation

Clone the repository:

```
git clone https://github.com/your-username/Scoreeboard.git
cd Scoreeboard
```

Install dependencies:  
This project requires Node.js ^20.19.0 or >=22.12.0.

```
npm install
```

Run in development mode:

```
npm run dev
```

Build for production:

```
npm run build
```

## ⚙️ Configuration

The project includes a `jsconfig.json` for easy path aliasing, allowing you to use `@/` to reference the `src` directory. It also features pre-configured VS Code settings for file nesting (e.g., nesting tsconfig files) to keep your workspace clean.
