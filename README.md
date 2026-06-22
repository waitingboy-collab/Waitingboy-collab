# Hi, I'm Radoslav! 👋
### QA Automation Engineer & Software Developer 🚀

I am a detail-oriented Quality Assurance and Software Engineering student at Software University (SoftUni), passionate about building efficient applications and ensuring their flawless performance through automation.

- 🛠️ **What I'm currently working on:** Enhancing web applications and building automation frameworks.
- 📚 **Tech Stack I use:** JavaScript, TypeScript, C#, HTML5, CSS3, Git, GitHub Pages.
- 🎯 **Future Goals:** Mastering Advanced QA Automation (Playwright, Selenium) and CI/CD integration.
# BG-RouteMaster Pro | QA Documentation & Methodology

### [cite_start]GPS Localization & Road Route Validation Report [cite: 2]

---

## [cite_start]1. Test Process Summary & Root Cause Analysis [cite: 3]

[cite_start]During the development and integration of the geo-localization module in **BG-RouteMaster Pro**, a critical logical defect (Bug) was identified[cite: 4]. [cite_start]The software miscalculated total distances when compared to real-world commercial navigation systems (such as Google Maps)[cite: 4].

* [cite_start]**Root Cause:** The initial software model relied on a static delta-calculation based on the assumption that the user always starts from a fixed zero point (Kardzhali)[cite: 5]. [cite_start]When tested from a real-world position 46 km away from Kardzhali, the software calculated a straight-line ("as the crow flies") distance relative to the city center, instead of the actual road distance to the final destination[cite: 6].
* [cite_start]**Resolution:** Implemented a dynamic algorithm based on the **Haversine formula** integrated with a **Road Curvature Coefficient (1.28)** specifically optimized for the Bulgarian road network[cite: 7].

---

## [cite_start]2. Executed Test Cases [cite: 8]

| ID | Test Description | Expected Result | Initial Status | Final Status |
| :--- | :--- | :--- | :---: | :---: |
| **TC-01** | [cite_start]Validation of base destinations (Start: Kardzhali center)[cite: 9]. | [cite_start]Distance must match Google Maps (e.g., Burgas: 245 km)[cite: 9]. | [cite_start]🔴 MISMATCH [cite: 9] | [cite_start]🟢 SUCCESS [cite: 9] |
| **TC-02** | [cite_start]Browser GPS module test (satellite/air signal)[cite: 9]. | [cite_start]Successful extraction of exact coordinates (Lat/Lng) via Geolocation API[cite: 9]. | [cite_start]🟢 SUCCESS [cite: 9] | [cite_start]🟢 SUCCESS [cite: 9] |
| **TC-03** | [cite_start]Integration test under a 46 km deviation from the center[cite: 9]. | [cite_start]Recalculate route directly to destination without using Kardzhali as a mask[cite: 9]. | [cite_start]🔴 WRONG KM [cite: 9] | [cite_start]🟢 FIXED [cite: 9] |
| **TC-04** | [cite_start]Mathematical model test (Road Coefficient: 1.28)[cite: 9]. | [cite_start]Transformation of straight-line coordinates into real road curves[cite: 9]. | [cite_start]🟢 SUCCESS [cite: 9] | [cite_start]🟢 SUCCESS [cite: 9] |
| **TC-05** | [cite_start]Boundary Value Analysis (Speed limits)[cite: 9]. | [cite_start]Activation of a `warning-box` exactly when exceeding limits per Traffic Law[cite: 9]. | [cite_start]🟢 SUCCESS [cite: 9] | [cite_start]🟢 SUCCESS [cite: 9] |

---

## [cite_start]3. QA Methodology & Applied Testing Techniques [cite: 12, 13]

[cite_start]To ensure complete coverage and quality of the routing algorithm, the following software testing methods were applied[cite: 13]:

### [cite_start]A. Black-Box Testing [cite: 14]
[cite_start]Testing performed entirely from the user's perspective without internal code modifications during execution[cite: 15].
* [cite_start]**Equivalence Partitioning:** Divided destinations into distinct regional groups (e.g., Southern Black Sea Coast, Northern Bulgaria) to validate correct UI clustering inside the `<optgroup>` elements[cite: 16].
* [cite_start]**Boundary Value Analysis (BVA):** Evaluated speed input fields exactly at the legal thresholds (e.g., 90 km/h and 91 km/h) to verify proper triggering of traffic warning notifications[cite: 17].

### [cite_start]B. Integration Testing [cite: 18]
[cite_start]Validated the seamless data flow and communication between two isolated components[cite: 19]:
* [cite_start]The hardware/browser-based GPS sensor (`navigator.geolocation`)[cite: 19].
* [cite_start]The internal JavaScript database (`bgRoutes Database`)[cite: 19].
* [cite_start]*Goal:* To confirm that incoming latitude/longitude coordinates successfully dynamically update the `value` attributes of DOM elements in real-time[cite: 20].

### [cite_start]C. Regression Testing [cite: 21]
[cite_start]Executed the entire core test suite after modifying the formula to fix the 46 km deviation bug[cite: 22]. [cite_start]This ensured that the new mathematical triangulation did not break existing features, such as arrival time estimation (`addMinutesToTime`) and fuel cost calculations[cite: 23].

---

## 🔍 4. How to Verify This Project (Manual Testing)

Since this project focuses on precision and calculations, I have performed thorough Manual Testing based on Black-Box techniques to ensure its stability. You can replicate the verification by following these steps:

1.  **Open the Live Application:** Click the production link in the "About" section of this repository.
2.  **Happy Path Testing (TC-01):** Select a standard destination, enter average fuel consumption, and verify that the calculated kilometers and total cost match real-world navigation data.
3.  **Boundary Value Verification (TC-05):** Input a speed value exactly at the highway limit ($140\text{ km/h}$) and then at $141\text{ km/h}$. Verify that the `warning-box` triggers correctly on the UI.
4.  **Integration Check:** Open your browser's Developer Tools (`F12` -> Console), allow location access, and verify that the Geolocation API successfully populates the coordinate fields without errors.

---

## [cite_start]5. Conclusion & QA Assessment [cite: 24]

[cite_start]Following the final testing iteration and the architectural shift of the GPS calculator from "offset-based" to "direct terrestrial triangulation", the application meets accuracy standards[cite: 25]. [cite_start]The system is stable, free of hardcoded values, and fully ready for deployment to the **Production** environment[cite: 26].
