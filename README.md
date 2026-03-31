# Match-3 Deceptive UX Experiment

## Overview

This project is a self-contained, browser-based Match-3 game designed for a psychological UX experiment. The study investigates how cognitive age (functional cognitive processing capacity) serves as a predictor of a player's receptiveness to manipulation through deceptive design patterns (often called "dark patterns") in video games, compared to natural (chronological) age.

The game acts as the testing environment, contrasting standard "flow-state" gameplay with sudden, high-pressure manipulative prompts. By measuring player behavior and reaction times during these prompts, researchers can gather objective telemetry on susceptibility to digital persuasion.

## How to Run

Because this is a single-file application with embedded CSS and JavaScript, no server or build process is required.

1. Download or clone this repository.
2. Locate the `experiment-game.html` file.
3. Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, Edge).
4. Open your browser's Developer Console (usually `F12` or `Ctrl+Shift+J` / `Cmd+Option+J`) to view the real-time telemetry logs during gameplay.

## Gameplay Mechanics

- The core game is a standard Match-3 grid.
- Players click two adjacent gems to swap them.
- Matching 3 or more identical gems removes them, adds to the score, and drops new gems from the top.
- The player is given a strict limit of 5 moves.
- Once the move counter reaches 0, the deceptive design sequence is triggered.

## The Deceptive Design Patterns (Dark Patterns)

Deceptive design patterns are UI/UX choices carefully crafted to trick users into doing things they might not otherwise do, such as spending premium currency or giving up personal data. This experiment utilizes three specific patterns deployed simultaneously to test a player's cognitive inhibition and susceptibility to heuristic (impulsive) processing.

### 1. The Near-Miss Effect

**What it is:**  
A cognitive bias heavily exploited in gambling and mobile gaming. A "near-miss" is a failure that looks incredibly close to a massive success.

**How it works here:**  
When the player runs out of moves, the game halts and presents a modal claiming:  
"You have a MEGA COMBO waiting!"  
Even if this isn't mathematically true on the board, the sudden interruption simulates the feeling that the player was just one move away from a massive victory, triggering a dopamine response that makes them want to continue playing to "close the loop."

### 2. False Urgency

**What it is:**  
Artificial time constraints placed on a decision to induce stress and force the user to act quickly rather than think critically.

**How it works here:**  
The manipulative modal features a large, rapidly ticking countdown timer starting at 10 seconds. As the timer drops below 3 seconds, it flashes red. This induces cognitive load and panic, bypassing the player's systematic processing and forcing them to rely on heuristic, impulsive decision-making.

### 3. Confirmshaming & Visual Interference

**What it is:**  
Manipulating the visual hierarchy and the wording (microcopy) of choices to make the "decline" option feel shameful, confusing, or difficult to interact with.

**How it works here:**  

- **The Desired Action:** The button to spend premium currency is massive, brightly colored, heavily animated (bouncing), and uses enthusiastic language.  
- **The Decline Action:** The button to close the prompt is tiny, low‑contrast, unstyled, and uses self‑deprecating language: "No thanks, I prefer to give up and lose all my hard-earned progress."  

This forces the user to actively agree with a negative statement about themselves to escape the modal.

## Telemetry & Data Collection

The game tracks objective behavioral data to supplement subjective scales (like NASA‑TLX or PENS) administered outside the game.

When the deceptive modal is triggered, the game logs a JSON object to the browser console containing:

- `subject_id`: An automatically generated ID for the session.
- `pattern_type`: The specific dark patterns being tested.
- `decision_latency_ms`: The exact time (in milliseconds) it took for the user to make a choice under pressure. Lower latency often correlates with higher impulsivity and lower cognitive inhibition.
- `choice_made`: Whether the user succumbed (`succumbed_to_pattern_bought_moves`), resisted (`resisted_pattern_declined`), or let the timer run out (`timeout`).
