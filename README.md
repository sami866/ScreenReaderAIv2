# ScreenReaderV2 — UI Perception Prototype

## Overview
ScreenReaderV2 is an **Android Accessibility-based prototype** focused on **capturing and analyzing real-time UI structure changes**.  
The current stage aims to **observe, record, and reconstruct** Android user interface hierarchies and interaction events in a structured, inspectable format.

> ⚠️ This project is a research prototype and is not intended as a consumer application.

---

## Current Implementation

### 1. Accessibility Event Monitoring
The app uses a custom `AccessibilityService` to listen for system-wide UI events, including:

- Window state changes  
- Window content updates  
- Scroll events  
- View interaction events  

All raw accessibility events are timestamped and logged in an internal event store.

---

### 2. UI Snapshot Reconstruction
When a meaningful UI change occurs, the system:

- Traverses the active window’s accessibility node tree  
- Extracts properties for each node:
  - Class name
  - Text / content description
  - Screen bounds
  - Interactivity flags (clickable, scrollable, focusable, etc.)
- Builds a **snapshot of the UI hierarchy** at that moment

Snapshots allow inspection of **structural changes** and **screen context** over time.

---

### 3. Event-to-Structure Linking
Accessibility events are linked to their corresponding UI nodes and snapshots, creating a **temporal UI timeline** that records:

- what changed  
- when it changed  
- which UI elements were involved

---

### 4. Monitoring Interface
The project includes a monitoring activity that displays:

- Recorded UI snapshots  
- Detected UI changes  
- Recent raw accessibility events  

This interface is primarily for **debugging and analysis**.

---

## Technical Focus
Current technical focus areas:

- Accurate UI tree traversal  
- Stable node identification strategies  
- Separation of **raw events** and **UI structural snapshots**  
- Performance and memory management for continuous monitoring

---

## Next Step (Near-Term Plan)
The next immediate technical step is:

> **Implement snapshot comparison logic** to detect meaningful differences between consecutive UI states.

This will enable:

- Detection of added / removed nodes  
- Property changes tracking  
- Filtering redundant UI updates  

---

## Status
ScreenReaderV2 is in an **experimental research stage** and is intended for **learning, system exploration, and academic evaluation**. 
