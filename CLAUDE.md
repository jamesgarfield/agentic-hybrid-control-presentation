# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands
- Build: `gulp build`
- Start development server: `gulp serve`
- Run tests: `gulp test`
- Run single test: `qunit 'test/test-file.html'`
- Run ESLint: `gulp eslint`

## Style Guidelines
- JavaScript: Follow ESLint rules in package.json (eq comparison, no-caller, etc.)
- Formatting: Use standard JS formatting with ES6 module syntax
- Imports: Place at top of file, use ES modules where possible
- Error handling: Use try/catch for runtime errors, handle promise rejections 
- Code organization: Follow module pattern in existing files
- Naming: camelCase for variables/functions, PascalCase for classes/constructors
- Plugin structure: Follow the pattern in /plugin directory with UMD and ESM exports
- SCSS: Follow nesting and variable patterns in existing theme files