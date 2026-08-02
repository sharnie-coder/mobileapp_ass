# System Requirements Specifications

## 1. Functional Requirements (FR)

Functional requirements define the core capabilities, operations, and services that the **Campus Virtual Queue Management Mobile Application** must provide to users.

| Requirement ID | Module / Feature | Description | Priority |
| :--- | :--- | :--- | :--- |
| **FR-01** | Service Selection | The app shall allow users to view available campus service points (Academic Registry, Finance Office, Student Health Clinic, Accommodation Office) along with their live operating status (Open, Closed, On Break). | High (Must Have) |
| **FR-02** | Virtual Ticket Issuance | The app shall allow users to select a service and generate a digital queue ticket containing a unique ticket ID (e.g., `#FIN-104`), issue timestamp, and service point details. | High (Must Have) |
| **FR-03** | Real-Time Queue Tracking | The app shall display dynamic real-time updates of the user's current queue position (e.g., *"3 people ahead of you"*) and estimated wait time in minutes. | High (Must Have) |
| **FR-04** | Push Notifications | The app shall send automated push notifications when key threshold events occur (e.g., when 5 people remain, when 2 people remain, and when it is the user's turn to proceed to a counter). | High (Must Have) |
| **FR-05** | Queue Delay / Snooze | The app shall provide a "Snooze / Delay 10 Mins" feature, allowing users to temporarily shift their position back in the queue if delayed (limited to 1 snooze per ticket). | Medium (Should Have) |
| **FR-06** | Voluntary Queue Exit | The app shall allow users to cancel their active ticket and exit the queue at any point prior to being called. | High (Must Have) |
| **FR-07** | Counter Navigation / Guidance | The app shall display target counter details (e.g., *"Proceed to Desk 4, Ground Floor Room 102"*) upon being called. | Medium (Should Have) |
| **FR-08** | Service Completion & Feedback | The app shall prompt users upon service completion to rate their experience (1–5 stars) and optionally submit brief feedback. | Low (Nice to Have) |
| **FR-09** | Queue History | The app shall maintain a historical log of past queue tickets and completed service visits for student record-keeping. | Low (Nice to Have) |

---

## 2. Mobile Usability & HCI Requirements (UR)

Mobile usability requirements are non-functional constraints aligned with Nielsen’s Usability Heuristics and standard Mobile UX guidelines to ensure the app is intuitive, efficient, and accessible on smartphones.

### UR-01: Visibility of System Status
* **Requirement:** The app must continuously communicate queue updates to the user.
* **HCI Rule:** Live counters, active progress bars, and status badges (e.g., *Active*, *Paused*, *Served*) must refresh dynamically without requiring full manual screen reloads.

### UR-02: Touch-Friendly Targets & Thumb Zone Optimization
* **Requirement:** All interactive elements must be optimized for one-handed smartphone touch interaction.
* **HCI Rule:** Primary buttons (e.g., *Join Queue*, *Leave Queue*) must have a minimum touch target area of **44 × 44 pt (48 × 48 px)** with at least 8px padding between adjacent buttons to prevent accidental taps. Key actions must be situated in the bottom half of the screen.

### UR-03: Real-Time Feedback & System Response
* **Requirement:** The interface must provide immediate visual and haptic feedback for every user action.
* **HCI Rule:** Button taps must display immediate visual states (pressed color shift) within **100ms**. Critical alerts (such as *Your Turn!*) must trigger simultaneous audio and vibration feedback.

### UR-04: Error Prevention & User Control
* **Requirement:** The system must protect users from accidental destructive actions.
* **HCI Rule:** Pressing "Leave Queue" or "Cancel Ticket" must trigger a confirmation dialog modal (e.g., *"Are you sure you want to leave? You will lose position #3"*). Users must also be able to navigate back cleanly without breaking ticket status.

### UR-05: Consistency and Standards
* **Requirement:** The visual design must adhere to recognizable mobile UI conventions.
* **HCI Rule:** Use standardized mobile navigation patterns (e.g., persistent bottom tab navigation bar, standard back arrows top-left, recognizable icons for settings, notifications, and profile).

### UR-06: Minimalist & High-Contrast Design
* **Requirement:** Information must be easily readable in outdoor campus conditions (bright sunlight) while walking.
* **HCI Rule:** High-contrast text elements (contrast ratio of at least 4.5:1), large typography for ticket numbers (minimum 24pt bold), and zero clutter on primary task screens.
### UR-07: Mobile Accessibility & Inclusivity (WCAG 2.1 AA)
* **Requirement:** The app must be fully usable by students with visual or motor impairments.
* **HCI Rule:** All visual controls must support system screen readers (TalkBack on Android, VoiceOver on iOS). Color alone must never be used to convey status (e.g., pair red/green indicator badges with text labels like "Open" or "Closed").

---

## 3. Mapping HCI Principles to Requirements

| HCI Principle | Requirement Mapping | Design Implementation |
| :--- | :--- | :--- |
| **Visibility of Status** | FR-03, UR-01 | Big live counter showing position and estimated wait time. |
| **Error Prevention** | UR-04 | Modal dialog before ticket cancellation. |
| **Flexibility & Efficiency** | FR-05 | "Snooze Queue" action button for delayed students. |
| **Aesthetics & Minimalism** | UR-06 | Clean card layout for service selection; large touch buttons. |
| **Feedback** | FR-04, UR-03 | Push alerts, sound, and haptics when called to counter. |
---

## 4. Non-Functional Technical Requirements (NFR)

| ID | Category | Requirement Description | Target Metric |
| :--- | :--- | :--- | :--- |
| **NFR-01** | Performance | App must update live queue positions seamlessly. | Latency under 2.0s over 3G/4G/5G |
| **NFR-02** | Security | Student IDs and authentication tokens must be encrypted in transit and at rest. | HTTPS / TLS 1.3 Encryption |
| **NFR-03** | Availability | Virtual queue system must maintain high uptime during peak enrollment weeks. | 99.5% Operational Uptime |
| **NFR-04** | Battery & Data | Background push notifications must minimize battery and mobile data usage. | < 5MB data usage per session |