# Quiz CLI

An interactive command-line quiz game for learning JavaScript/Node fundamentals.

[![Node.js >= 18](https://img.shields.io/badge/node-%3E%3D18.0.0-339933?logo=node.js)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](#license)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![Branch](https://img.shields.io/badge/branch-main-blue)

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Data Format](#data-format)
- [Configuration Notes](#configuration-notes)
- [Scripts](#scripts)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

---

## Overview

Quiz CLI is a lightweight interactive quiz game that runs in your terminal. It focuses on JavaScript and Node.js fundamentals and is implemented with modern ES Modules on Node.js without external dependencies.

- Problem it solves: Provides a quick, distraction-free way to practice and reinforce core JavaScript/Node concepts directly from the terminal.
- Target users: Learners, bootcamp students, and developers who want to refresh their knowledge of JS/Node.
- Core value proposition: Simple, fast, and portable—no setup beyond Node.js; colorized output and intuitive numeric input.

Architecture overview (as implemented):
- Entry point `index.js` (with a CLI shebang) orchestrates the game flow.
- Questions are loaded from `data/questions.json`.
- Interactive input is handled via Node’s `readline`.
- Colors and styles are centralized in `src/colors.js`.
- Quiz logic is in `src/quiz.js`; input helpers are in `src/input.js`.
- Uses only Node.js built-ins: `fs/promises`, `url`, `path`, and `readline`.

---

## Features

- Core gameplay
  - Category selection on start.
  - Choose the number of questions (All, 3, or 5 if available).
  - Multiple-choice questions; answer by entering the option number.
  - Quiz loop asking one question at a time.
  - Final results summary and prompt to play again.

- User experience
  - Colorized terminal output via ANSI codes.
  - Clear prompts and simple numeric controls.

- Data-driven
  - Questions organized by categories in a single JSON file.
  - Each question includes text, options, correct answer index, and optional explanation.

- Developer-friendly
  - ES Modules; clean separation of concerns (colors, input, quiz).
  - No external dependencies; relies only on Node built-ins.
  - Node’s built-in test runner wired (no tests present in the repository).

---

## Project Structure

```
test-app/
├─ index.js
├─ package.json
├─ data/
│  └─ questions.json
└─ src/
   ├─ colors.js
   ├─ input.js
   └─ quiz.js
```

- `index.js`  
  CLI entry point. Displays a banner, loads questions, prompts for category/quantity, runs the quiz, and handles replay.

- `package.json`  
  Package metadata for `quiz-cli`, Node engine requirement (>= 18.0.0), scripts (`start`, `test`), and license declaration (MIT). No dependencies.

- `data/questions.json`  
  Data source containing categories and questions. See [Data Format](#data-format) for structure and extension guidelines.

- `src/colors.js`  
  Utility functions/constants for ANSI color codes and styling terminal output.

- `src/input.js`  
  Readline-based input helpers to prompt users and validate numeric selections.

- `src/quiz.js`  
  Core quiz logic: iterates questions, checks answers, tracks score, and displays results.

---

## Prerequisites

- Node.js >= 18.0.0
- A terminal (macOS, Linux, or Windows)
- Git (optional, for cloning)

No external dependencies are required.

---

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/Sshchornyi/test-app.git
   cd test-app
   ```

2. Run the application:
   - Using npm:
     ```bash
     npm start
     ```
   - Using Node directly:
     ```bash
     node index.js
     ```

Notes:
- `index.js` includes a CLI shebang; on Unix-like systems you could also run:
  ```bash
  chmod +x index.js
  ./index.js
  ```
  This is optional; running via `npm start` or `node index.js` works everywhere.

3. No installation step is needed; there are no dependencies.

4. Environment configuration:
   - None required. No `.env` file is used.

5. Running tests:
   - The repository includes a `test` script wired to Node’s built-in test runner:
     ```bash
     npm test
     ```
   - No test files are present in the repo at this time, so the command runs without executing tests.

6. Docker:
   - There is no Dockerfile in this repository.

---

## Usage

- Start the app and follow on-screen prompts.
- When prompted to choose a category, use the numeric selection to pick one.
- Select how many questions you want (All, 3, or 5 if available).
- For each question, type the number of the correct option and press Enter.
- Press Enter to continue between questions when prompted.
- After completing the quiz, review your results and choose whether to play again.

Tips:
- Terminal colors enhance readability; most modern terminals are supported.
- If colors look off, verify your terminal supports ANSI escape codes.

---

## Data Format

Data lives in `data/questions.json` and follows this schema:

```jsonc
{
  "categories": {
    "<categoryId>": {
      "name": "Category Display Name",
      "questions": [
        {
          "question": "Question text",
          "options": ["Option A", "Option B", "Option C", "Option D"],
          "answer": 0, // index of the correct option
          "explanation": "Optional explanation shown after answering"
        }
      ]
    }
  }
}
```

Adding or editing content:
- Add a new category by introducing a new key under `categories` with a `name` and a `questions` array.
- Each question requires:
  - `question` (string): The question text.
  - `options` (string[]): Array of choices displayed in order.
  - `answer` (number): Zero-based index of the correct option in `options`.
  - `explanation` (string): Short rationale shown after answering.
- Keep option arrays consistent in length (e.g., 4 options) for a uniform experience.
- Validate JSON after editing (e.g., `node -e "JSON.parse(require('fs').readFileSync('data/questions.json'))"`).

---

## Configuration Notes

- Module system: ES Modules (`"type": "module"` in `package.json`).
- Entry point: `index.js` includes a POSIX shebang. There is no `bin` field in `package.json`; prefer running via `npm start` or `node index.js`.
- Compatibility: Requires Node.js >= 18.0.0; uses built-in modules only (`fs/promises`, `url`, `path`, `readline`).

---

## Scripts

- `npm start` — Launches the quiz: `node index.js`.
- `npm test` — Runs Node’s built-in test runner (no tests currently in the repo).

---

## Development

- `src/colors.js` — Centralized ANSI color helpers for consistent styling.
- `src/input.js` — Readline utilities for prompts, selections, confirmations, and pause.
- `src/quiz.js` — Quiz class encapsulating state, question flow, scoring, feedback, and results.

Recommended enhancements:
- Add a `bin` entry in `package.json` to install/run globally as `quiz-cli`.
- Expand question banks and categories.
- Add tests using `node:test` for input modules and quiz logic.
- Add a LICENSE file (MIT) to match the package.json declaration.

---

## Contributing

Contributions are welcome!
- Fork the repo and create a feature branch.
- Keep PRs focused and include a clear description.
- Run `npm test` (when tests are added) and ensure JSON is valid.

---

## License

MIT License. The license is declared in `package.json`. A dedicated `LICENSE` file is not present in the repository.

---

## Acknowledgements

- Inspired by countless CLI tools and learning resources in the JavaScript community.
- ANSI color codes reference: https://en.wikipedia.org/wiki/ANSI_escape_code