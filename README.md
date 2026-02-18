# Quiz CLI 🎯 — Interactive command‑line quiz game in Node.js

[![Node.js >= 18](https://img.shields.io/badge/Node.js-%E2%89%A518.0.0-green?logo=node.js)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository (test-app; package name: quiz-cli) is a simple, interactive CLI quiz that demonstrates modern Node.js ES Modules, asynchronous I/O, filesystem access, readline-based user input, and a small OOP design. Questions are loaded from JSON and organized by category.

## Features

- Core
  - Interactive command-line quiz with prompts and selections
  - Multiple categories loaded from JSON data (e.g., javascript, nodejs, general)
  - Choose how many questions to play (all/3/5 depending on availability)
  - Results summary at the end, with review and explanations for incorrect answers
  - Replay option to start another round
- Implementation
  - Node.js ES Modules (import/export)
  - Async/await flow and clean control over user input
  - Zero external dependencies (built-in Node.js modules only)
  - Simple OOP via a Quiz class (shuffling, progress tracking, question loop)
- UX
  - Colored output using ANSI escape codes
  - Clear instructions and graceful error handling

## Requirements

- Node.js >= 18.0.0
- A terminal that supports interactive input (readline) and ANSI colors (for best experience)
