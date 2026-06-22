# Hi, I'm Radoslav! 👋
### QA Automation Engineer & Software Developer 🚀

I am a detail-oriented Quality Assurance and Software Engineering student at Software University (SoftUni), passionate about building efficient applications and ensuring their flawless performance through automation.

- 🛠️ **What I'm currently working on:** Enhancing web applications and building automation frameworks.
- 📚 **Tech Stack I use:** JavaScript, TypeScript, C#, HTML5, CSS3, Git, GitHub Pages.
- 🎯 **Future Goals:** Mastering Advanced QA Automation (Playwright, Selenium) and CI/CD integration.
--------------------------------------------------------------------------------------------------------
# BG-RouteMaster Pro | QA Documentation & Methodology
### GPS Localization & Road Route Validation Report

---

## 1. Test Process Summary & Root Cause Analysis

During the development and integration of the geo-localization module in **BG-RouteMaster Pro**, a critical logical defect (Bug) was identified. The software miscalculated total distances when compared to real-world commercial navigation systems (such as Google Maps).

* **Root Cause:** The initial software model relied on a static delta-calculation based on the assumption that the user always starts from a fixed zero point (Kardzhali). When tested from a real-world position 46 km away from Kardzhali, the software calculated a straight-line ("as the crow flies") distance relative to the city center, instead of the actual road distance to the final destination.
* **Resolution:** Implemented a dynamic algorithm based on the **Haversine formula** integrated with a **Road Curvature Coefficient (1.28)** specifically optimized for the Bulgarian road network.

---

## 2. Executed Test Cases

| ID | Test Description | Expected Result | Initial Status | Final Status |
| :--- | :--- | :--- | :---: | :---: |
| **TC-01** | Validation of base destinations (Start: Kardzhali center). | Distance must match Google Maps (e.g., Burgas: 245 km). | 🔴 MISMATCH | 🟢 SUCCESS |
| **TC-02** | Browser GPS module test (satellite/air signal). | Successful extraction of exact coordinates (Lat/Lng) via Geolocation API. | 🟢 SUCCESS | 🟢 SUCCESS |
| **TC-03** | Integration test under a 46 km deviation from the center. | Recalculate route directly to destination without using Kardzhali as a mask. | 🔴 WRONG KM | 🟢 FIXED |
| **TC-04** | Mathematical model test (Road Coefficient: 1.28). | Transformation of straight-line coordinates into real road curves. | 🟢 SUCCESS | 🟢 SUCCESS |
| **TC-05** | Boundary Value Analysis (Speed limits). | Activation of a `warning-box` exactly when exceeding limits per Traffic Law. | 🟢 SUCCESS | 🟢 SUCCESS |

---

## 3. QA Methodology & Applied Testing Techniques

To ensure complete coverage and quality of the routing algorithm, the following software testing methods were applied:

### A. Black-Box Testing
Testing performed entirely from the user's perspective without internal code modifications during execution.
* **Equivalence Partitioning:** Divided destinations into distinct regional groups (e.g., Southern Black Sea Coast, Northern Bulgaria) to validate correct UI clustering inside the `<optgroup>` elements.
* **Boundary Value Analysis (BVA):** Evaluated speed input fields exactly at the legal thresholds (e.g., 90 km/h and 91 km/h) to verify proper triggering of traffic warning notifications.

### B. Integration Testing
Validated the seamless data flow and communication between two isolated components:
* The hardware/browser-based GPS sensor (`navigator.geolocation`).
* The internal JavaScript database (`bgRoutes Database`).
* *Goal:* To confirm that incoming latitude/longitude coordinates successfully dynamically update the `value` attributes of DOM elements in real-time.

### C. Regression Testing
Executed the entire core test suite after modifying the formula to fix the 46 km deviation bug. This ensured that the new mathematical triangulation did not break existing features, such as arrival time estimation (`addMinutesToTime`) and fuel cost calculations.

---

## 🔍 4. How to Verify This Project (Manual Testing)

Since this project focuses on precision and calculations, I have performed thorough Manual Testing based on Black-Box techniques to ensure its stability. You can replicate the verification by following these steps:

1.  **Open the Live Application:** Click the production link in the "About" section of this repository.
2.  **Happy Path Testing (TC-01):** Select a standard destination, enter average fuel consumption, and verify that the calculated kilometers and total cost match real-world navigation data.
3.  **Boundary Value Verification (TC-05):** Input a speed value exactly at the highway limit ($140\text{ km/h}$) and then at $141\text{ km/h}$. Verify that the `warning-box` triggers correctly on the UI.
4.  **Integration Check:** Open your browser's Developer Tools (`F12` -> Console), allow location access, and verify that the Geolocation API successfully populates the coordinate fields without errors.

---

## 5. Conclusion & QA Assessment

Following the final testing iteration and the architectural shift of the GPS calculator from "offset-based" to "direct terrestrial triangulation", the application meets accuracy standards. The system is stable, free of hardcoded values, and fully ready for deployment to the **Production** environment.
