# ⚡ Infosys Springboard 7.0 - Milestone 2: FranchiseOps AI & Advanced Security

## Overview

This repository contains the Milestone 2 deliverable for the Infosys Springboard Internship. It builds upon the secure User Authentication Portal from Milestone 1 by transforming it into an Enterprise Multi-Agent Franchise Intelligence System. It introduces three autonomous Machine Learning agents, a Generative AI Copilot, and three advanced security hardening layers.

## Features Implemented

*   **Advanced Security Enhancements:** Introduces progressive account lockouts (escalating time penalties for failed logins), OTP resend rate-limiting (cooldowns to prevent spam), and a real-time 🔴/🟡/🟢 password strength checker.
*   **Three Autonomous ML Agents:** Features predictive models for Workforce Attrition, Outlet Clustering & Revenue Simulation, and Inventory & Weather Demand forecasting. Each agent evaluates 5+ algorithms to select a champion model.
*   **Generative AI Copilot:** Utilizes a 4-bit quantized LLM (Qwen2.5-3B-Instruct) to synthesize the agents' numerical outputs into executive action plans and structured JSON data.
*   **Live Weather Integration:** Localized weather lookups for 6 seeded Indian retail cities to impact inventory forecasting.
*   **System Administration:** A fully functional Admin Dashboard to add users, delete users, manually unlock accounts, and view ML Model Card training metrics.
*   **Database Management:** Uses SQLite3 to store user credentials, employing bcrypt for secure password hashing.

## Tech Stack

*   **Frontend/UI:** Streamlit
*   **Backend & Security:** SQLite3, PyJWT, bcrypt
*   **Networking & Email:** Pyngrok, Gmail SMTP
*   **Machine Learning:** scikit-learn (Logistic, Random Forest, Gradient Boosting, etc.), KMeans, joblib, pandas
*   **Generative AI:** HuggingFace Transformers, Qwen2.5-3B-Instruct, bitsandbytes (4-bit quantization)

## How to Run in Google Colab

1. Upload the `FranchiseOps_AI_Milestone2.ipynb` file to Google Colab.
2. Go to **Runtime → Change runtime type** and select **T4 GPU**.
3. Add the following keys to your Colab Secrets tab (enable Notebook Access):
   * `JWT_SECRET_KEY`: Any secure random string.
   * `NGROK_AUTHTOKEN`: Your personal ngrok auth token.
   * `EMAIL_ID`: The sender Gmail address.
   * `EMAIL_PASSWORD`: The 16-character Gmail App Password.
   * `ADMIN_EMAIL_ID`: Email to bootstrap the Admin account.
   * `ADMIN_PASSWORD`: Password for the Admin account.
   * `HF_TOKEN`: Your HuggingFace access token for the LLM.
   * `KAGGLE_USERNAME` & `KAGGLE_KEY`: (Optional) To train Agent 1 on real dataset.
4. Run all cells.
5. Click the generated Ngrok public URL to launch the portal.

## Screenshots

*   **Home page**
    
    (Drag and drop your home_page image right here!)

*   **AI Copilot (prompt + response)**
    
    (Drag and drop your ai_copilot image right here!)

*   **ML Pricing Calculator (input + predicted cost)**
    
    (Drag and drop your ml_pricing image right here!)

*   **Admin Panel → ML Model Card tab (R²/RMSE and all agent metrics)**
    
    (Drag and drop your model_card image right here!)

*   **Admin Panel → Add / Delete / Unlock user actions**
    
    (Drag and drop your admin_users image right here!)

*   **A triggered lockout message**
    
    (Drag and drop your lockout image right here!)

*   **An OTP cooldown message**
    
    (Drag and drop your otp_cooldown image right here!)
