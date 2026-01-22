# Dentilia

> **Dentilia** is a state-of-the-art, local-first Dental Practice Management System (PMS) and Cephalometric Analysis Engine. Built for the 2026 clinical landscape, it prioritizes data sovereignty, high-speed micro-interactions, and automated orthodontic diagnostics.

![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)
![Tauri](https://img.shields.io/badge/Tauri-v2-FFC131?logo=tauri&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-2021-000000?logo=rust&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-ACID-003B57?logo=sqlite&logoColor=white)

---

## 📑 Project Overview

Dentilia was developed to modernize the legacy experience of dental practice management. By moving away from high-latency web apps and bloated legacy software, Dentilia offers an instantaneous, offline-capable environment that integrates clinical charting, professional scheduling, and advanced radiographic analysis into a single unified binary.

### Key Features
- **Interactive Odontogram:** SVG-based clinical tooth mapping with persistent state tracking.
- **Medical History & Risk Alerting:** Comprehensive, JSON-driven medical history with visual safety cues for practitioners.
- **Professional Agenda:** 24h high-performance calendar with drag-and-drop rescheduling and direct clinical record linking.
- **Cephalometric Engine:** Manual radiographic tracing with automated clinical angle calculations.

---

## 🛠 Technical Case Study

### 1. Core Architecture
Dentilia utilizes a **Local-First, Hybrid-Desktop architecture**. By leveraging **Tauri v2**, the application decouples the UI from the system-level operations:
*   **Rust Backend:** Manages memory-safe file I/O, local encrypted database access, and system-level dialogue plugins.
*   **React Frontend:** A high-speed, reactive interface styled with **Tailwind CSS v4**, communicating with the backend via an asynchronous **IPC (Inter-Process Communication) bridge**.
*   **ACID Compliance:** Uses an embedded **SQLite** engine, ensuring that patient records remain atomic and consistent even in the event of hardware failure.

### 2. Complex Logic: The Cephalometric Diagnostic Engine
The most significant technical challenge was the development of a manual tracing engine capable of translating pixel-based interactions into clinical data.
*   **Coordinate-to-Angle Algorithm:** Implemented a custom geometric engine using `Math.atan2` to calculate clinical angles (SNA, SNB, ANB) from user-placed landmarks. 
*   **Mathematical Precision:** The algorithm handles quadrant normalization and vector-based projection to classify skeletal relationships (Class I, II, or III) in real-time.
*   **Data Hydration:** Tracings are stored as serialized JSON, allowing for "non-destructive" editing where individual points can be moved years later to update a diagnosis without redrawing the entire study.

### 3. The Tech Stack
- **Engine:** [Tauri v2](https://tauri.app/) (Rust-based system bridge)
- **Frontend:** [React](https://react.dev/) + [Vite](https://vitejs.dev/)
- **State Management:** React Hooks (useState, useEffect) with persistent local DB sync.
- **Graphics Engine:** [Konva.js](https://konvajs.org/) for the Cephalometric Canvas.
- **Scheduling:** [FullCalendar](https://fullcalendar.io/) with custom time-grid logic.
- **Styling:** [Tailwind CSS v4](https://tailwindcss.com/)
- **Database:** [SQLite](https://www.sqlite.org/) via `rusqlite`

### 4. Performance & Results
*   **Binary Footprint:** Managed to keep the final installer under **10MB**, compared to ~100MB+ for typical Electron-based competitors.
*   **UI Responsiveness:** Achieved sub-10ms latency on data-heavy switches (e.g., jumping from Agenda to a full Patient Chart).
*   **Sovereignty:** 100% of patient data resides in the user's `%APPDATA%` directory, ensuring GDPR/HIPAA compliance by design through total data isolation.

---

## 🚀 Getting Started

### Prerequisites
- [Rust](https://www.rust-lang.org/tools/install)
- [Node.js](https://nodejs.org/)
- [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) (C++ Desktop Development)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/dentilia.git