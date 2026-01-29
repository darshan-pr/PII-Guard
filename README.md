# PII-Guard: A Robust PII Detection and Masking System

<p align="center">
  <img src="https://placehold.co/600x300/1e293b/ffffff?text=PII-Guard&font=inter" alt="PII-Guard Project Banner">
</p>

<p align="center">
    <a href="#"><img src="https://img.shields.io/badge/Python-3.9+-blue.svg" alt="Python Version"></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
    <a href="#"><img src="https://img.shields.io/badge/Hugging%20Face-Transformers-yellow.svg" alt="Hugging Face Transformers"></a>
    <a href="#"><img src="https://img.shields.io/badge/Build-Passing-brightgreen.svg" alt="Build Status"></a>
</p>

> PII-Guard is a high-performance Python library designed for the detection and redaction of Personally Identifiable Information (PII) in unstructured text. It utilizes a fine-tuned transformer model to provide context-aware identification of sensitive data, ensuring robust privacy protection before data is processed by third-party services or stored in databases.

---

## Abstract

In modern data pipelines, particularly those involving Large Language Models (LLMs), ensuring the confidentiality of user data is paramount. PII-Guard addresses this challenge by providing a reliable, model-based solution for identifying and masking a wide range of sensitive entities. By replacing PII with secure placeholders, it allows for safe data handling and processing, with a seamless mechanism to restore the original information when required.

---

##  Key Features

-   **Advanced NER-Based Detection:** Employs a fine-tuned Named Entity Recognition (NER) model to accurately identify entities like `PERSON`, `EMAIL`, `PHONE`, and `LOCATION` with contextual understanding, minimizing false positives.
-   **Systematic Masking & Unmasking:** Implements a reversible process where detected PII is replaced with classified placeholders (e.g., `[EMAIL_1]`). The original data is stored in a secure map, enabling precise restoration in the final output.
-   **High Performance:** Built upon the `distilbert-base-cased` architecture, offering an optimal balance between accuracy and computational efficiency.
-   **Extensible Architecture:** The model can be further fine-tuned on custom datasets to recognize domain-specific or novel PII types.
-   **Formal Logging:** Includes capabilities for logging detected PII types and counts for audit and compliance purposes.

---

## Core Workflow

The system operates on a straightforward, three-stage data sanitization workflow:

1.  **PII Identification and Masking:** The input text is processed by the fine-tuned NER model. Each identified PII entity is replaced by a unique placeholder, and the original value is stored in a corresponding PII map.
2.  **Sanitized Data Processing:** The resulting text, now sanitized and free of sensitive information, is safely processed by downstream applications, such as an external LLM API.
3.  **Data Restoration:** The response from the external service, which may contain placeholders, is unmasked using the PII map to restore the original data, ensuring the final output is complete and coherent.

---

## 🤖 SECURE AI CHATBOT WITH PII PROTECTION

Your sensitive information will be automatically protected!
Type 'exit' or 'quit' to end the conversation.
---
You: hey man, can u pls fix this up for me? gotta send it to the client.  ok so tell Jen P. at Megacorp that the files r sent. she can reach me at alexj_designs@proton.me or just call my cell 555-867-5309 if theres a problem. my ip when i sent it was 192.168.1.10 if their IT asks.  also she needs my w9 info, the ssn is 987.65.4321 but tell her not to email that around lol. just use it for the paperwork. her office is the one on 123 Main St, Anytown.  my full name is Alex Johnson btw. thx!! Make this into formal way.

🔍 Detecting sensitive information... ✓ Found 8 PII entities
🔒 Masking sensitive information... ✓ Data protected

📝 Masked version sent to AI:
   "hey man, can u pls fix this up for me? gotta send it to the client.  ok so tell [PERSON_2] at Megacorp that the files r sent. she can reach me at [EMAIL_ADDRESS_1] or just call my cell [PHONE_NUMBER_1] if theres a problem. my ip when i sent it was [IP_ADDRESS_1] if their IT asks.  also she needs my [LOCATION_3] info, the ssn is 987.65.4321 but tell her not to email that around lol. just use it for the paperwork. her office is the one on 123 [LOCATION_2], [LOCATION_1].  my full name is [PERSON_1] btw. thx!! Make this into formal way."

🤔 AI is thinking... ✓ Response generated

📄 AI Response (Masked):
   "Of course! Here is a more formal and professional version of your message, ready to send to your client.

**A quick but important note:** I have not included the Social Security Number in the email below. It is highly insecure to send sensitive information like an SSN via email. Instead, the message prompts them to contact you for a secure way to provide it, which protects both you and the client.

***

**Subject: Confirmation of File Delivery**

Dear [PERSON_2],

I am writing to confirm that the requested files have been sent to you.

Please let me know if you encounter any issues. You can reach me by replying to this email at [EMAIL_ADDRESS_1] or by calling my cell phone at [PHONE_NUMBER_1].

For your IT department's reference, the files were sent from the IP address: [IP_ADDRESS_1].

I understand you also require my [LOCATION_3] information and Social Security Number for the paperwork. My location is: [LOCATION_3]. For security purposes, I would prefer to provide my SSN through a more secure channel. Please let me know the best way to do so, or feel free to call me at your convenience to receive it.

Thank you.

Best regards,

[PERSON_1]
[EMAIL_ADDRESS_1]
[PHONE_NUMBER_1]"

🔓 Restoring your information... ✓ Complete

🤖 AI (Final Response):
   Of course! Here is a more formal and professional version of your message, ready to send to your client.

**A quick but important note:** I have not included the Social Security Number in the email below. It is highly insecure to send sensitive information like an SSN via email. Instead, the message prompts them to contact you for a secure way to provide it, which protects both you and the client.

***

**Subject: Confirmation of File Delivery**

Dear Jen P.,

I am writing to confirm that the requested files have been sent to you.

Please let me know if you encounter any issues. You can reach me by replying to this email at alexj_designs@proton.me or by calling my cell phone at 555-867-5309.

For your IT department's reference, the files were sent from the IP address: 192.168.1.10.

I understand you also require my w9 information and Social Security Number for the paperwork. My location is: w9. For security purposes, I would prefer to provide my SSN through a more secure channel. Please let me know the best way to do so, or feel free to call me at your convenience to receive it.

Thank you.

Best regards,

Alex Johnson
alexj_designs@proton.me
555-867-5309


## Getting Started

### Prerequisites
- Python 3.9+
- Pip and a virtual environment manager

### Installation

Clone the repository and install the required dependencies.

```bash
# Clone the repository
git clone [https://github.com/your-username/PII-Guard.git](https://github.com/your-username/PII-Guard.git)
cd PII-Guard

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
