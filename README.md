# AI-Credit-Card-Data-Harvester

```markdown
# 💳 AI Credit Card Data Harvester (n8n + Gemini)

This project automates the extraction of structured credit card details from two trusted sources:  
- 🧾 Official MITC/KFS PDF documents  
- 🌐 Bank product web pages

It uses Google Gemini (LLM) for intelligent data extraction, and n8n to orchestrate the workflow end-to-end.

---

## 📦 Features

✅ Upload a PDF and enter a product URL via a user form  
✅ Extract 29 standardized credit card fields (Joining Fee, Rewards, Eligibility, etc.)  
✅ Merge and prioritize data using custom logic (PDF > HTML > fallback)  
✅ Apply basic unit tests (e.g., verify Joining Fee)  
✅ Convert results to CSV and email them with a responsive HTML template  
✅ Full error handling and alerts via email if anything goes wrong  

---

## ⚙️ Tech Stack

| Tool       | Purpose                              |
|------------|--------------------------------------|
| **n8n**    | No-code automation workflow          |
| **Google Gemini API** | AI-powered field extraction (LangChain LLM agent) |
| **HTML + SMTP** | Sending visually appealing emails |
| **Error Trigger (n8n)** | Email-based error alert system |

---

## 📸 Workflow Overview

1. **📝 Form Trigger**  
   Collects user input (Name, Email, Product Page URL, PDF).

2. **📄 Extract PDF Text**  
   Extracts raw text from the uploaded MITC/KFS file.

3. **🌐 Fetch Product Page**  
   Uses headers to mimic a browser and retrieve HTML content.

4. **🧠 LLM Extraction (Gemini)**  
   Two AI agents extract 29 fields from both PDF and Webpage.

5. **🔀 Merge Logic**  
   Custom merging prioritizes PDF > HTML > default ("Not mentioned").

6. **✅ JSON Processing & Unit Test**  
   Validates specific fields (e.g., Joining Fee) and parses clean output.

7. **📁 CSV Conversion & 📧 Email Delivery**  
   Converts structured JSON to CSV and sends to the user with a friendly HTML email.

8. **🚨 Error Handling Workflow**  
   Separate `ErrorTrigger` sends admin alerts if any failure occurs during execution.

---

## 📂 Folder Structure (Recommended)

```

├── workflows/
│   ├── AI\_Credit\_Card\_Data\_Harvester.json
│   └── Error\_Handling\_For\_Credit\_Card\_Data\_Harvester.json
├── assets/
│   └── screenshots/
├── README.md
└── .env (for API keys, SMTP)

```

---

## 🚀 How to Use

1. **Import both JSON files** into n8n:
   - `AI Credit Card Data Harvester`
   - `Error Handling For Credit_Card_Data_Harvester`

2. Set up required credentials:
   - Google Gemini (Palm) API Key
   - SMTP email service for notifications

3. Deploy your webhook or host your n8n on a secure endpoint.

4. Open the form and test with:
   - Any credit card's public product page
   - A valid MITC/KFS PDF

---

## 🔒 Note on URLs

⚠️ Some bank websites (like HDFC, ICICI) may block bot access.  
If a **403 Forbidden** error occurs:
- Try a different credit card URL
- Wait and retry
- Use a page from a different bank if needed

---

## ✨ Future Enhancements

- Add a confidence scoring mechanism
- Introduce semantic reconciliation logic for contradicting values
- Build a frontend UI for manual field correction and approval

---

## 🧠 Built By

**Dhawan Nama**  
AI Developer | RPA Specialist | Automation Enthusiast  
📧 namadhawan@gmail.com

---

## 📃 License

This project is MIT Licensed.
```

---

