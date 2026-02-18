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

## Quick Start

1. Clone the repository:
   ```bash
   git clone https://github.com/Sshchornyi/test-app.git
   cd test-app
   ```
2. Install (optional): there are no external dependencies, so `npm install` is not required.
3. Run the app:
   - Using npm script:
     ```bash
     npm start
     ```
   - Or directly with Node:
     ```bash
     node index.js
     ```

Note: This project is not published to npm; there is no npx distribution.

## How to Play

1. Start the app:
   ```bash
   npm start
   ```
2. Follow the prompts:
   - Select a quiz category from the list (e.g., javascript, nodejs, general).
   - Choose the number of questions (options depend on data availability).
   - Read each question and enter the number of your chosen answer, then press Enter.
3. After the last question:
   - View your score summary.
   - Review incorrect answers with explanations.
4. Decide whether to play again when prompted.

## Scripts

- `start`: Run the quiz CLI
  ```bash
  npm start
  ```
- `test`: Execute Node’s built-in test runner
  ```bash
  npm test
  ```
  Note: There are currently no formal test files in the repository; this command will run with Node’s test runner but does not execute project-specific tests.

## Project Structure

```
test-app/
├─ index.js                # CLI entrypoint that orchestrates the quiz flow
├─ package.json            # Package metadata, engines (Node >= 18), scripts
├─ data/
│  └─ questions.json       # Quiz data: categories and questions
├─ src/
│  ├─ colors.js            # ANSI color helpers for styled terminal output
│  ├─ input.js             # Readline utilities: prompt, select, confirm, pressEnter
│  └─ quiz.js              # Quiz class: shuffling, question loop, progress, results
```

### Key Files

- `index.js`: Shows banner, loads data, handles category/length selection, runs the quiz, displays results, offers replay, and exits gracefully.
- `src/colors.js`: Provides small helpers to colorize text in the terminal using ANSI codes.
- `src/input.js`: Encapsulates user interaction via Node’s readline (prompting, selection lists, yes/no confirmations).
- `src/quiz.js`: Implements the quiz mechanics (shuffle questions, ask/validate answers, track correct/incorrect, review explanations).
- `data/questions.json`: The source of quiz content, organized by categories.

## Data Format

Questions are defined in `data/questions.json`. High-level schema:

- `categories`: an object where each key is a category name.
- Each category maps to an array of question objects:
  - `question`: string prompt
  - `options`: array of possible answers (strings)
  - `answer`: number index of the correct option
  - `explanation`: string shown when reviewing incorrect answers

Example (minimal):
```json
{
  "categories": {
    "javascript": [
      {
        "question": "Which array method returns a new array with elements that pass a test?",
        "options": ["map", "filter", "reduce"],
        "answer": 1,
        "explanation": "filter creates a new array with elements that satisfy the provided condition."
      }
    ]
  }
}
```

## Development Notes

- ES Modules: The project uses import/export and the "type": "module" workflow with Node >= 18.
- No external dependencies: All functionality relies on Node’s built-in modules (e.g., readline, fs).
- Extending questions/categories:
  - Add a new category key under categories in data/questions.json.
  - Provide an array of question objects matching the schema above.
- Extending colors:
  - Add new helper functions to src/colors.js that wrap strings with ANSI codes.
- Extending input:
  - Add additional prompt utilities in src/input.js for new interaction patterns (e.g., multi-select) using readline.

## Troubleshooting

- Node version errors:
  - Ensure Node.js >= 18.0.0. Older versions may fail due to ES Modules and APIs used.
- Terminal color issues:
  - Colored output relies on ANSI escape codes. If your terminal does not support ANSI colors, text may appear unstyled.
- Running from the project root:
  - Make sure you run npm start or node index.js from the repository root so paths to data/questions.json resolve correctly.

## Contributing

Contributions are welcome!

- Fork the repository
- Create a feature branch
- Make your changes and verify the CLI runs locally
- Open a pull request with a clear description and, if applicable, sample data updates

Please open an issue first for significant changes to discuss what you’d like to improve.

## License

MIT License. See https://opensource.org/licenses/MIT for details.
