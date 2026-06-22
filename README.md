# Hi, I'm Radoslav! 👋
### QA Automation Engineer & Software Developer 🚀

I am a detail-oriented Quality Assurance and Software Engineering student at Software University (SoftUni), passionate about building efficient applications and ensuring their flawless performance through automation.

- 🛠️ **What I'm currently working on:** Enhancing web applications and building automation frameworks.
- 📚 **Tech Stack I use:** JavaScript, TypeScript, C#, HTML5, CSS3, Git, GitHub Pages.
- 🎯 **Future Goals:** Mastering Advanced QA Automation (Playwright, Selenium) and CI/CD integration.

## 2. Executed Test Cases

| ID | Test Description | Expected Result | Initial Status | Final Status |
| :--- | :--- | :--- | :---: | :---: |
| **TC-01** | Validation of base destinations (Start: Kardzhali center).[cite: 1] | Distance must match Google Maps (e.g., Burgas: 245 km).[cite: 1] | 🔴 MISMATCH[cite: 1] | 🟢 SUCCESS[cite: 1] |
| **TC-02** | Browser GPS module test (satellite/air signal).[cite: 1] | Successful extraction of exact coordinates (Lat/Lng) via Geolocation API.[cite: 1] | 🟢 SUCCESS[cite: 1] | 🟢 SUCCESS[cite: 1] |
| **TC-03** | Integration test under a 46 km deviation from the center.[cite: 1] | Recalculate route directly to destination without using Kardzhali as a mask.[cite: 1] | 🔴 WRONG KM[cite: 1] | 🟢 FIXED[cite: 1] |
| **TC-04** | Mathematical model test (Road Coefficient: 1.28).[cite: 1] | Transformation of straight-line coordinates into real road curves.[cite: 1] | 🟢 SUCCESS[cite: 1] | 🟢 SUCCESS[cite: 1] |
| **TC-05** | Boundary Value Analysis (Speed limits).[cite: 1] | Activation of a `warning-box` exactly when exceeding limits per Traffic Law.[cite: 1] | 🟢 SUCCESS[cite: 1] | 🟢 SUCCESS[cite: 1] |
