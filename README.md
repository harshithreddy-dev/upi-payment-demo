# UPI Payment Demo 💸

**A real-world UPI Payment Flow Simulation built with deep link integration**

🔗 Live: [upipaymentdemo.vercel.app](https://upipaymentdemo.vercel.app)
📂 Repo: [github.com/harshithreddy-dev/upi-payment-demo](https://github.com/harshithreddy-dev/upi-payment-demo)

---

## 🚀 Overview

This project demonstrates how **UPI payments** can be initiated through **deep link intents**, replicating the real-world behavior of apps like GPay, Paytm, and PhonePe.
It was built as an internship assignment to explore how frontend-only apps can trigger native payment flows securely.

---

## 💡 Features

* ⚙️ **Dynamic UPI Link Generation** – Builds `upi://pay?...` links dynamically with all parameters
* 🏦 **Vendor Display** – Shows the correct merchant name & UPI ID before redirection
* 💸 **Instant Deep Link Redirection** – Opens UPI apps directly for payment
* 🔐 **PIN Entry Simulation** – Lets users go all the way to the PIN step in the UPI app
* 📱 **Responsive UI** – Works seamlessly across mobile & web

---

## 🧠 Tech Stack

* **Frontend:** HTML, CSS, JavaScript (Vanilla)
* **Deployment:** Vercel
* **Integration Tested:** Paytm, GPay, PhonePe via deep link intent
* **Additional Testing:** Cashfree payment gateway (for validation of backend approach)

---

## ⚙️ Setup & Usage

1. Clone the repo

   ```bash
   git clone https://github.com/harshithreddy-dev/upi-payment-demo.git
   cd upi-payment-demo
   ```
2. Run locally

   ```bash
   npm install
   npm run dev
   ```
3. Enter amount → click **Pay Now** → select a UPI app → follow the on-screen steps.

---

## 🧩 Flow

1. User inputs amount and name
2. App dynamically generates a deep link using the UPI format:

   ```
   upi://pay?pa=merchant@upi&pn=MerchantName&am=amount&tn=Note&cu=INR
   ```
3. The system launches the installed UPI app
4. The app correctly fetches merchant info and prompts for PIN
5. After PIN entry, some apps block the transaction (explained below 👇)

---

## ⚠️ Key Issue Faced — “MC Code” Block

This project works **95% perfectly**, but real UPI apps reject final payment confirmation because of **missing Merchant Category Code (MC Code)**.

**What happens:**

* Payment app opens successfully
* Merchant name & details appear correctly
* UPI PIN screen appears
* After entering PIN → Payment fails with *“Security reasons / MC Code missing”*

**Why:**

* UPI platforms (GPay, Paytm, PhonePe) now **require verified merchant registration** for real payments.
* The **MC Code** is part of the merchant verification process with NPCI or banks.
* Without it, payments are sandboxed or blocked at the final step.

**Attempts made:**

* Modified UPI parameters (`pa`, `pn`, `tn`, `cu`, `am`)
* Tried with multiple UPI apps
* Tested different VPAs and VPA domains
* Integrated with **Cashfree Payment Gateway**, which worked end-to-end
* But since the **assignment required deep-link based flow**, backend-based fix wasn’t permitted.

✅ **Result:** Functional demo covering **complete UI + UPI redirection + merchant validation flow**, with real-world insights on **UPI security restrictions**.

---

## 🧱 Commit Summary

* **Initial Build** – UI + deep link generator setup
* **UPI Flow Added** – Implemented core payment intent logic
* **Merchant Info Handling** – Dynamically fetched and displayed
* **Error Handling & Alerts** – For invalid or failed payment attempts
* **Final Tweaks** – Responsive layout, small design fixes

---

## 💭 Learnings

* How deep links interact with native UPI apps
* Why real payments require merchant validation & MC codes
* Hands-on with Cashfree SDK and backend verification for comparison
* Strong understanding of **UPI parameter structure** and **security layers**

---

## 🧩 Future Improvements

* ✅ Integrate a verified merchant backend for full payment success
* 📊 Add success/failure transaction dashboard
* 🔁 Test with sandbox UPI APIs for more realistic simulations
* 🧩 Add QR-based dynamic payment link generation

---

## 👤 Built By

**Harshith Reddy**
Student | Content Creator | Developer building things that actually work.
🌍 [GitHub](https://github.com/harshithreddy-dev)

---

## 📜 License

MIT License – Free to learn, fork, and experiment.

---
