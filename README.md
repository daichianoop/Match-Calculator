
# ❤️ Love Calculator - Web-Based Game

## Overview

The **Love Calculator** is a web-based application that calculates the compatibility percentage between two people based on their names. The calculation ensures variability while maintaining a **fun and engaging** experience. A **leaderboard** is maintained using **localStorage** to track past calculations dynamically.

This project is fully **responsive**, ensuring smooth functionality on **mobile, tablet, and desktop**.

---

## Features

✅ **Dynamic Love Calculation Algorithm** (Ensures values between **60-100**)  
✅ **Leaderboard (Stored in LocalStorage)**  
✅ **Elegant & Crazy UI**  
✅ **Fully Responsive Design**  
✅ **Leaderboard Modal for Real-Time Updates**  

---

## How It Works

1. **User enters two names** (their name and their partner's name).
2. The system **calculates a percentage** based on a **custom algorithm**:
   - **First entry:** ~95% (Between 93-97)
   - **Second entry:** ~89% (Between 87-91)
   - **All subsequent entries:** **Calculated dynamically** with values between **60-100**
3. The **result is displayed** immediately.
4. The **leaderboard updates in real-time** and is stored in **localStorage**.

---

## Project Files

This project consists of a **single file** (`index.html`), containing **HTML, CSS, and JavaScript** for ease of deployment.

---

## Code Breakdown

### 1️⃣ HTML Structure

- **Form for Name Input**
- **Display Area for Match Percentage**
- **Leaderboard Button & Modal**

```html
<div class="container">
    <h1>Love Calculator</h1>
    <form id="loveForm">
        <input type="text" id="name1" placeholder="Your Name" required>
        <input type="text" id="name2" placeholder="Partner's Name" required>
        <button type="submit">Calculate</button>
    </form>
    <div id="result"></div>
    <button id="leaderboardBtn">Leaderboards</button>
</div>


---

2️⃣ CSS (Styling & Responsiveness)

Gradient Background:

background: linear-gradient(135deg, #ff4081, #ff80ab);

Card-like container:

box-shadow: 0 4px 15px rgba(0,0,0,0.2);

Modal Popup for Leaderboard

Responsive Design for Mobile & Tablets


@media (max-width: 600px) {
    h1 { font-size: 1.75rem; }
    input { font-size: 0.9rem; }
    button { font-size: 0.9rem; padding: 0.5rem 1rem; }
}


---

3️⃣ JavaScript (Core Functionality)

Handles Love Percentage Calculation

Ensures Results Always Stay Between 60-100

Stores & Updates Leaderboard in LocalStorage

Manages Modal Popups for Leaderboard


🚀 Love Percentage Calculation Algorithm

function calculateLove(name1, name2) {
    calcCount++;
    let percentage;
    if (calcCount === 1) {
        percentage = Math.floor(Math.random() * 5) + 93; // 93-97
    } else if (calcCount === 2) {
        percentage = Math.floor(Math.random() * 5) + 87; // 87-91
    } else {
        let combined = (name1 + name2).toLowerCase().replace(/\s/g, '');
        let sum = 0;
        for (let i = 0; i < combined.length; i++) {
            sum += combined.charCodeAt(i) * (i + 1);
        }
        let weightedFactor = (sum % 41) + 60;
        let fluctuation = Math.floor(Math.random() * 6) - 3;
        percentage = Math.min(100, Math.max(60, weightedFactor + fluctuation));
    }
    return percentage;
}

🔹 Why this algorithm?

The first two results are predictable for an engaging start.

The subsequent results vary dynamically while ensuring a minimum of 60%.

The calculation uses ASCII character values and positions to generate unique scores.



---

🔥 Storing & Updating the Leaderboard

function saveResult(name1, name2, percentage) {
    let data = JSON.parse(localStorage.getItem('loveLeaderboard')) || [];
    data.push({ name1, name2, percentage });
    localStorage.setItem('loveLeaderboard', JSON.stringify(data));
    updateLeaderboardUI();
}

Stores all match results in localStorage.

Ensures leaderboard is dynamically updated every time a new match is calculated.



---

🎯 Leaderboard Modal Handling

leaderboardBtn.addEventListener('click', function() {
    updateLeaderboardUI();
    leaderboardModal.style.display = 'block';
});

closeModal.addEventListener('click', function() {
    leaderboardModal.style.display = 'none';
});

window.addEventListener('click', function(event) {
    if (event.target === leaderboardModal) {
        leaderboardModal.style.display = 'none';
    }
});

Clicking the leaderboard button opens the modal.

Clicking the close button or outside the modal closes it.



---

Usage Instructions

1. Open index.html in a browser.


2. Enter your name and your partner’s name.


3. Click "Calculate" to get the match percentage.


4. Click "Leaderboards" to view saved results.




---

Future Enhancements

🚀 User Authentication: Login to save results for individual users.
🎨 Animated UI: Add playful animations when showing match results.
💬 Social Sharing: Share match results directly to social media.


---

Final Thoughts

This Love Calculator combines mathematical logic, UI design, and localStorage to provide a fun, engaging experience. The algorithm ensures fairness, and the leaderboard adds competitiveness to the game.

Enjoy testing your love compatibility with this elegant and crazy web-based game! ❤️

---

### **How to Use This README.md**
- Save this file as `README.md` in your project directory.
- It provides structured documentation for your **Love Calculator** project.
- It includes **setup instructions, algorithm explanation, and future enhancements**.

Let me know if you need any refinements! 🚀
