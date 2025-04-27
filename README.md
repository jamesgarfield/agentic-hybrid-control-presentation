# Agentic Patterns and Hybrid Mechanisms of Control Presentation

A reveal.js presentation on LLM agent control patterns and hybrid control mechanisms.

## Overview

This presentation covers various patterns and mechanisms for controlling LLM agents, including:

- Tools & Structured Responses
- ERRV (Extract-Review-Revise-Verify) Pattern
- Primordial Loop
- Oracles
- MemGPT Case Study
- State Machines

## Getting Started

### Prerequisites

- Node.js (>= 18.0.0)

### Installation

1. Clone this repository
2. Install dependencies:

```bash
npm install
```

### Running the Presentation

To start the presentation:

```bash
npm start
```

This will open the presentation in your default web browser at http://localhost:8000.

## Development

### Directory Structure

- `index.html` - Main presentation file
- `slides/main.md` - Slide content in markdown format
- `images/` - Diagrams and visualizations
- `css/custom.css` - Custom styling
- `reference/` - Background materials and notes

### Building for Distribution

To build a distributable version of the presentation:

```bash
npm run build
```

### Creating a Package

To create a ZIP package of the presentation:

```bash
gulp package
```

## Notes for Presenters

- Use the 'S' key to access the speaker notes view
- Use 'SPACE' to advance slides
- Use 'ESC' to see a slide overview

## Credits

Based on [reveal.js](https://revealjs.com/) by Hakim El Hattab.

---
<div align="center">
  MIT licensed | Copyright © 2011-2024 Hakim El Hattab, https://hakim.se
</div>
