# 3. The Sri Lankan Context

This file covers the local facts that will shape the product: SMS, WhatsApp, payments, the law, language and devices.

## SMS

### Cost

| Provider | Price per SMS (LKR) | Notes |
|---|---|---|
| SMSGo | 0.54 | Taxes included, no setup fee |
| Text.lk | 0.64–0.84 | Cheaper with bigger top-ups |
| SriLankaBulkSMS | 0.60–0.75 | |
| Dialog (direct) | about 0.50 | Business API needs a negotiated contract |
| tuitionfee.lk (competitor) | about 0.45 | What they say they pass on to teachers |

A Sinhala or Tamil SMS uses Unicode, so each SMS holds only about 70 characters instead of 160. **A Sinhala message can cost two or three times as much as the same message in English.** Keep messages short or use English and numbers.

### What it costs a teacher

Example: 200 students, one class a week, so about 4–5 classes a month.

| Message type | SMS per month | At Rs. 0.60 |
|---|---|---|
| Arrival only | about 900 | about Rs. 540 |
| Arrival + absence | about 900 (one or the other per class) | about Rs. 540 |
| + fee reminder + receipt | +400 | +Rs. 240 |
| **Total** | **about 1,300** | **about Rs. 780** |

That is a large share of a Rs. 2,000 subscription. **SMS cost must be either passed on clearly or tightly controlled.** Never hide it inside a flat price we can't afford.

### Sender ID ("mask")

- Business SMS must come from a **registered sender ID**: 3–11 letters, such as `SIYANA` or `MATHSGURU`.
- Registration needs a **Business Registration (BR) certificate** and takes about 3–7 working days per operator. A company can have only about 5 masks.
- **Promotional** SMS has stricter rules: consent, opt-out and sending only between 8 am and 8 pm. Attendance and receipts are **transactional**, which is easier, but we must not mix in adverts.

**What this means:** most individual teachers can't get their own mask. We would send from **one platform mask** (for example `SIYANA`) with the teacher's name in the message. A mask per teacher could be a paid extra for institutes.

## WhatsApp

- WhatsApp has about **15 million users** in Sri Lanka. It is how teachers already talk to students and parents.
- Through the official WhatsApp Business API, a **utility** message such as "arrived" or "receipt" costs about **US$0.002–0.0023** each to a Sri Lankan number in late 2026. That is roughly **Rs. 0.60–0.70**, about the same as SMS.
- WhatsApp is **not cheaper**, but it supports images (receipts, cards), two-way chat and no Unicode penalty.
- SMS still reaches every phone, including the basic phones many parents and grandparents use.

**What this means:** support **both**. Let the parent choose. SMS stays the reliable default.

## Payments

- **LankaQR** is the national QR payment standard. Since **6 April 2026** there is **no merchant fee on payments up to Rs. 5,000**. Above Rs. 5,000 the fee is capped at 1.0% for local apps.
- Most monthly class fees are **under Rs. 5,000**, so a parent can pay a class fee by LankaQR **at no cost to the teacher**.
- Card gateways like **PayHere** cost 2.69–3.90% per transaction, or 1.5% for LankaQR through PayHere. That is much more expensive, so cards are for parents abroad or as a backup.
- Today most fees are paid in **cash at the door** or by bank transfer with a photo of the slip.

**What this means:** "pay by LankaQR, your class card updates automatically" is one of the strongest features we could offer. It saves the teacher's assistant from counting cash and checking slips. **Open question:** how can a small software company get a LankaQR merchant setup that links payments to a specific student? This needs talks with a bank or acquirer.

## Law: Personal Data Protection Act No. 9 of 2022 (PDPA)

- **Fully in force since 18 March 2025.** It is enforced by the Data Protection Authority of Sri Lanka.
- Most students are **under 16**, and processing their data needs **a parent's consent**.
- We will store names, phone numbers, photos, school and attendance history. Attendance is effectively **location data about children**, which is sensitive.

**What this means for the product:**

- Collect **only what is needed**. Do we need the school name? A photo?
- Record **parent consent** at registration, with a simple paper or digital form the teacher can use.
- Clear roles: the teacher or institute is the **controller**. We are the **processor**. We need a data processing agreement in our terms.
- Let parents **see, correct and delete** their child's data.
- Keep data **secure** and decide **where it is hosted**. Cross-border transfer rules apply, so check this before choosing a cloud region.
- Delete data when a student leaves, after a set period.

**Get a short legal review before launch.** It is cheap compared with the risk.

## Rules on tuition itself

- **Western Province, December 2024:** a circular banned government teachers from giving paid tuition to students of their own school. After objections, the Governor **suspended** it. It could come back, and other provinces could copy it.
- **Sundays and Poya days:** several provinces have tried to stop tuition on Sunday mornings so children can attend religious school. Most attempts stalled or were not enforced.

**What this means:** these rules don't block the product, but:

- Some teachers may be **nervous about records** that show who they teach. Data stays private to the teacher; we never publish it.
- The **schedule** feature should handle Poya days and holidays, and local rules if they come in.

## Language

- Sinhala is the first language of most users, Tamil of a large minority, and many teachers use English for technical words.
- The interface should be **Sinhala, Tamil and English from day one**, not English with translation added later.
- SMS templates should come in each language, with the Unicode cost noted above.

## Devices and connectivity

- Smartphones are very common, but many are **cheap Android phones** with little storage and older Android versions.
- About **40% of people were still offline** in 2025. Mobile data in big halls can be **slow or overloaded** when hundreds of students arrive at once.
- Power cuts were common in 2022 and can still happen.

**What this means:**

- The **door scanner** must work **offline** and sync later. It must be fast with a queue of 300 students.
- The app should run well on a **Rs. 30,000-class Android phone**.
- Parents need **no app**. They get an SMS or WhatsApp message. An app or portal is optional.
