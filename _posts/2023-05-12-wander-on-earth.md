---
layout: post
title: "Wander on Earth: A Multi-User 3D Environmental Restoration Game"
date: 2023-05-12
categories: [Project, Game Dev]
tags: [Unity, C#, Maya, Multiplayer, URP]
---

# Wander on Earth: Restoring Our Planet in 3D

![Project Banner](/assets/img/gameProject/game_banner.png)

### 🌍 Project Overview
**Wandering on Earth** is a high-fidelity 3D simulation game developed in **Unity**. The core concept revolves around environmental restoration—players work to revive different parts of the Earth, including various terrains and ecosystems, within a limited time.

> [Watch the Demonstration Video](https://youtu.be/Ar-UdNnshRE)  
> [Explore Source Code on GitHub](https://github.com/hanbin-zhang/WanderingOnEarth)

---

### 🚀 Key Technical Highlights

Developing a project of this scale within a PC lab environment presented several "hardcore" engineering hurdles:

#### 1. Real-time Network Physics & Lag Compensation
Synchronizing physics-based interactions for **up to 20 players** is a notorious challenge in game development. 
* **The Problem:** Network latency (lag) would normally cause objects to "jitter" or appear in different positions for different players.
* **Our Solution:** We implemented a custom **Lag Compensation Algorithm**. By predicting movement and interpolating states across the network, we ensured that tree planting and object interactions felt instantaneous and consistent for every participant.

#### 2. High-Fidelity Rendering vs. Performance Optimization
We aimed for a "vivid, complicated, and beautiful" world, which is computationally expensive.
* **The Problem:** Maintaining high resolutions and stable frame rates across different hardware in the university's PC labs.
* **Our Solution:** * Leveraged the **Universal Render Pipeline (URP)** with customized **Shader Lab** scripts to optimize light and shadow calculation. Integrated a **Nanite-like rendering logic** (high-poly detail management) to reduce the GPU's computing pressure without sacrificing visual detail.

#### 3. Bespoke Asset & Animation Pipeline
Unlike many student projects that use stock assets, we built a complex pipeline from scratch.
* **The Challenge:** Creating 30+ unique 3D models (animals, plants, terrain) that were fully interactive.
* **Our Solution:** We used **Maya and Blender** for skeletal rigging. Each model was equipped with a custom-coded skeleton and animation controller, allowing for realistic AI behaviors (e.g., animals returning once the "Environmental Impact Assessment" score improved).

#### 4. Adaptive Interdisciplinary Audio System
Working with **5 students from the Department of Music**, we tackled the challenge of "Environmental Storytelling through Sound."
* **Dynamic Background Music (BGM):** We created unique soundtracks for each scene.
* **Stage-Based Audio Evolution:** The music evolves as players successfully restore the environment. For example, as air quality improves and plants grow, the soundscape shifts from desolate tones to vibrant, melodic compositions.
* **Enhanced Immersion:** This synergy between visual feedback and adaptive audio significantly deepened the emotional impact and player engagement.

---

### 🎨 Design & Gameplay
In this world, players start by planting trees to improve air quality and soil environment. As the "Environmental Impact Assessment" score improves:
1.  **Ecosystem Rebirth:** Animals return to the habitat.
2.  **Human Integration:** Normal daily life resumes for human NPCs.
3.  **Collaborative Goals:** Players must collaborate and coordinate asynchrony or synchronously to achieve global restoration.

---

### 🛠 Tech Stack
* **Engine:** Unity 2021.3 (URP)
* **Languages/Scripts:** C#, Shader Lab
* **Networking:** Photon (PUN 2)
* **Modeling/Art:** Maya, Blender, Photoshop, Affinity Designer 2
* **Version Control:** Git / Unity Version Control

---

### 📈 Development Journey
This project was a rigorous engineering exercise involving over **90 team meetings** and managing **200+ tasks**. Our goal was to push the limits of PC laboratory hardware, creating a multi-machine experience that balances visual fidelity with high performance.

---
*Looking for a demo? You can build the game directly from the [GitHub repository](https://github.com/hanbin-zhang/WanderingOnEarth) or check out the project report for full architectural details.*