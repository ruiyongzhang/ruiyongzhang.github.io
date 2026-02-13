---
layout: post
title: "Scotland Yard: Digitalizing a Classic Board Game with Advanced Java OOP"
date: 2021-05-15
categories: [Project, Software Engineering]
tags: [Java, Object-Oriented Programming, Design Patterns, Game Logic]
---

## The Hunt for Mr. X: Implementing Scotland Yard in Java

![Scotland Yard Game Board](/assets/img/SY/ScotlandYard.jp2)

### 🕵️‍♂️ Project Overview
**Scotland Yard** is a famous board game where a team of detectives hunts down a fugitive named "Mr. X" through the streets of London. 

In this project for the **Object-Oriented Programming (COMS10017)** unit at the University of Bristol, I was tasked with implementing the complete game logic (The Model) within a pre-existing software framework. The goal was not just to make the game work, but to strictly adhere to **OOP principles** and utilize industry-standard **Design Patterns**.

<!-- > [View Project Repository](https://github.com/你的用户名/仓库名) (Check strict visibility settings due to academic integrity) -->

>[View Player Instructions](/assets//img/SY/26646%20anl%202050897_2.pdf)

---

### 🧩 The Challenge: From Board Rules to Code
The complexity of Scotland Yard lies in its asymmetric gameplay:
* **Mr. X** moves secretly, recording his moves in a travel log (sometimes hiding the transport type).
* **Detectives** move openly, and their used tickets are handed over to Mr. X.
* **Double Moves:** Mr. X can move twice in a single turn using special cards.

My role was to implement the "Brain" of the game—the `GameState`—which validates moves, updates player locations, and manages the game flow without breaking encapsulation.

---

### 🛠 Technical Deep Dive: Design Patterns
To handle the complex state transitions, I implemented several key design patterns:

#### 1. The Factory Pattern
I utilized the **Factory Pattern** (`MyGameStateFactory`) to handle the creation of game instances. This decoupled the game setup logic from the actual game execution, allowing for flexible initialization of different game scenarios (e.g., varying numbers of detectives or starting positions).

#### 2. The Visitor Pattern (Crucial for Move Handling)
One of the biggest technical hurdles was distinguishing between a `SingleMove` (normal turn) and a `DoubleMove` (Mr. X special ability).
* **Problem:** Avoiding messy `instanceof` checks or long `if-else` chains when processing a move.
* **Solution:** I implemented a **Visitor Pattern**. This allowed the `GameState` to "visit" the move object. The move itself would then tell the system whether it was a single or double action, enabling polymorphic handling of game logic for updating player locations and ticket counts.

#### 3. The Observer Pattern
To ensure the User Interface (GUI) stayed in sync with the internal data, I implemented the **Observer Pattern**. The Game Model acts as the *Subject*, notifying all registered *Observers* (the UI components) whenever a `MOVE_MADE` or `GAME_OVER` event occurs.

---

### ⚙️ Core Logic Implementation: The `advance()` Method
The heart of the project was the `advance()` method, which calculates the next state of the game. It had to atomically handle four parallel updates:
1.  **Location Updates:** Moving players across the graph based on the ticket used (Taxi, Bus, Underground).
2.  **Ticket Transfer:** Implementing the specific rule where *“When a detective moves, the ticket used is given to Mr. X.”*
3.  **Travel Log Management:** If Mr. X moves, the system must update the log. Crucially, if he uses a **Black Ticket**, the log must obscure the transport mode to maintain secrecy.
4.  **Rotation Management:** Determining whose turn it is next, or checking if the game has ended (Detectives win if they land on Mr. X; Mr. X wins if rounds run out).

---

### 🧱 Data Structures & Immutability
To ensure thread safety and prevent accidental side effects, I relied heavily on **Immutable Data Structures** (using Google Guava libraries or Java's standard immutable sets).
* **`ImmutableSet`**: Used for holding the list of players and winning configurations.
* **`Optional<Integer>`**: Used for Mr. X’s location, as his position is effectively "null" (unknown) to the detectives for most of the game.

---

### 🚀 Reflection
This project was a rigorous exercise in translating abstract rules into concrete, type-safe Java code. It moved beyond simple scripting to true architectural design, teaching me the importance of:
* **Encapsulation:** Keeping the internal state of Mr. X private.
* **Polymorphism:** Handling different move types elegantly