# 🎓 Campus Jugaad: The Hyper-Local Campus Marketplace

**"Summon a Hero. Delegate your chaos."**

### ◆ Problem Statement
University campuses are isolated economies with inefficient "favor" systems. Students struggle to find help for small tasks like- 
a professor urgently needs a specific medicine but cannot leave the department because of back-to-back labs, a student needs a cycle for 1 hour, printing, food delivery, laundry pickup and many more.  
Right now, students randomly message WhatsApp groups, call friends, or run across campus in the middle of a busy schedule. There is no organized system to request help, no way to find someone available immediately, and no trusted way to pay for such small tasks.
While others have free time but no way to monetize it. Existing platforms cannot enter hostels or classrooms.

### ◆ Proposed Solution
**Campus Jugaad** is a closed-loop, secure marketplace designed exclusively for university campuses. It transforms the informal economy into a tech-driven system where students can outsource tasks to verified peers ("Heroes") safely.

##  Key Features
Ankur 

###  The Gamified Experience
* **Gamified Quest System:** Tasks aren't just chores; they are *"Quests"* with specific bounties, deadlines, and urgency levels (Low/Medium/Urgent).
* **Real-Time Hero Feed:** A real-time marketplace where students can find and accept quests based on location and reward to become the campus *"Hero"*.
* **Smart Quest Search & Sorting:** Heros don't just scroll blindly. They can **Filter** by **"Urgent"** to help fast or by **"High Pay"** to maximize their earnings or can sort by like **"Newest First"**. Heros can also manually search by typing for a specific task or location.
* **Legendary Dashboard:** Users track their journey with total earnings, completion stats, and a level-based XP system.
* **Rating System:** After the task is done, the Task Master rates the Hero out of 5 stars. This helps trustworthy *Heros* build a strong profile. In the future, this "Trust Score" will let Task Masters pick the best person for the job instead of just the first one.

###  Security & Architecture
* **Closed-Campus Authentication:** Integration with university emails (e.g., `@nitdgp.ac.in`) to ensure 100% verified college member access.(Note: Disabled for Hackathon Demo to allow external judges).
* **Secure OTP Handshake:** We don't rely on trust. When a Hero arrives, the Task Master gives them a secret 4-digit Code. The Hero *must* enter this code to unlock the payment.
* **Zero-Fraud Escrow Wallet:** Payments are deducted *before* the task goes live, guaranteeing the Hero gets paid. Funds are held in a secure `Escrow State` within the database and released only when the task provider (*"Task Master"*) shares the secret OTP.
* **Auto-Refund Escrow:** If a task is not accepted by anyone or a Hero accepts it but vanishes (doesn't complete it by the deadline), the smart contract **automatically refunds** the money to the Task Master. No admin needed.
* **In-App Hero Chat:** A private communication channel for Task Masters and Heroes to negotiate details without sharing personal phone numbers.

###  Design & Accessibility
* **Mobile-First Design:** Fully responsive layout optimized for on-the-go campus use between classes.
* **Glassmorphic UI:** A modern, sleek interface featuring fluid animations and full Dark/Light mode support.

*Note on Scope: For this hackathon, we focused exclusively on the Core Marketplace Logic. Secondary modules like User Profile, Settings, and Help Centre are currently static UI placeholders.*

## Demo Video
Demo video link: [🌐https://www.youtube.com/watch?v=1uiUTcwBCmg](https://www.youtube.com/watch?v=1uiUTcwBCmg)

##  Feasibility & Impact
* **Market Size:** ~5,000 students per average technical campus.
* **Economic Impact:** projected **₹50,000+** monthly transaction volume in pilot phase.
* **Time Saving:** Average student saves **~3 hours/week** by outsourcing logistics.

## Tech Stack

### Client (Frontend)
* **Library:** React.js
* **Build Tool:** Vite
* **Styling:** Tailwind CSS (Glassmorphism)

### Server (Backend)
* **Language:** TypeScript
* **Runtime:** Node.js
* **Framework:** Express.js

### Database
* **Database:** MongoDB (NoSQL)
* **ODM (Object Data Modeling):** Mongoose
* **Storage:** MongoDB Atlas (Cloud)

##  Limitations & Constraints

### 1. Financial Compliance (Regulatory)
* **No Real Banking API:** Currently, the "Wallet" uses a closed-loop virtual currency system. We have not integrated a real Payment Gateway (like Razorpay/Stripe) due to **KYC (Know Your Customer)** and legal requirements for handling real money between peers.
* **Cash-Out Logic:** Students cannot currently withdraw their virtual earnings to a bank account; this feature requires banking partnerships planned for phase 3 (the final production version).

### 2. Operational Logic
* **Binary Dispute Resolution:** The system currently assumes that if the OTP is shared, the task is successfully completed. We lack a **"Conflict Resolution Center"** for edge cases (e.g., "The Hero brought the wrong food item").
* **Open-Access Sandbox (Verification):** While the Sign-Up UI *advises* users to enter an institutional email (showing `student@college.edu` as a placeholder), the backend validation is currently **permissive**. (We allow `@gmail.com` signups also) So that judges and hackathon testers can easily access the platform without needing a fake university ID.(No verification is there in the backend).
* **Button Sensitivity:** Currently, we haven't added "Debouncing" (a delay to stop rapid clicks). So, if a user spams the "Post" button, it might create duplicate tasks. This will be fixed in the production version.

## Features for Round 2

### 1. Advanced Marketplace Engine
* **Dynamic Bidding Wars:** Moving beyond fixed prices. "Heroes" can bid higher or lower based on difficulty (e.g., "I'll print it for ₹40, but I need ₹10 extra for rain"). Task Masters can then select the best candidate based on price and rating.
### 2. Upgrade for Community Justice
* **Dispute Resolution Center:** A dedicated dashboard where users can upload proof (photos/chats) in case of a conflict. A "Jury System" (admins) will have access to review and resolve these edge cases.
### 3. Scaling & Performance
* **Preventing Double Posts:** Sometimes, if the internet is slow, a user might click the "Post" button twice. We will add **"Idempotency Keys"** (unique IDs) so the server knows to ignore the second click and create only one task.
* **Handling Simultaneous Clicks:** If two Heroes click "Accept" at the exact same millisecond, there is a risk of a **Race Condition**. We will implement better database locking to ensure only the first request wins, while the second user gets a polite "Quest already taken" message.


---
*For detailed architecture and diagrams, see [TECHNICAL_ARCHITECTURE.md](./TECHNICAL_ARCHITECTURE.md)*
