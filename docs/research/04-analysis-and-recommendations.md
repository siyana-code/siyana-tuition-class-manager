# 4. Analysis and Recommendations

## The original idea, checked against what we found

| Original point | What we found | Verdict |
|---|---|---|
| **What:** QR attendance, fee tracking, parent SMS, schedules | All four are standard in competing products | ✅ Right features, ⚠️ not different |
| **Stack:** Next.js, Supabase, SMS API | Not locked yet. See "What the stack must handle" below | Decide after validation |
| **Why:** tuition is huge and run in exercise books | Huge: yes. Exercise books: true for small teachers, less so for big ones, who already use systems | ✅ / ⚠️ |
| **How:** charge per class per month | Competitors charge per student (ClassFlow) or by student tiers (tuitionfee.lk, eduX) | ⚠️ Needs testing; see Pricing |
| **Selling point:** "your child arrived" SMS | Already offered by 5+ competitors | ❌ Not enough on its own |

## SWOT

**Strengths**
- Small team, so we can move fast and keep costs low
- Can be built mobile-first, offline-first and Sinhala/Tamil-first from day one, which is harder for older systems to retrofit
- No hardware to sell; any phone is the scanner

**Weaknesses**
- No brand, no customers, no testimonials yet. In this market, trust comes from word of mouth
- Competing against a free tier (ClassFlow) and an established leader (IT Signature)
- SMS costs eat into a low price

**Opportunities**
- LankaQR's zero fee for payments under Rs. 5,000 (from April 2026). We could make "parent pays by QR, card updates itself" simple
- Absence alerts, which parents care about more than arrival alerts
- Institutes that need clean money splitting between teachers and the institute
- Rural and outstation teachers, where use has nearly caught up with urban areas but sales teams rarely go

**Threats**
- Competitors can copy any single feature quickly
- Province rules on tuition could shrink or scare parts of the market
- Economic pressure makes teachers resist any new monthly cost
- PDPA breaches involving children's data would be very damaging

## Where we could win

Pick **one** clear focus for the first version. Three realistic options:

### Option A: "The fee collector" for individual teachers (recommended to test first)

A teacher with 50–500 students who now uses a notebook or class cards.

- Parent pays by **LankaQR**. The class card is marked paid automatically and the parent gets a receipt.
- At the door, the assistant scans the card. It shows **green (paid) or red (not paid)** instantly, even offline.
- Parents get **arrival or absence** messages.
- **Why it could win:** it saves real money and time at the door, and cuts lost fees. "We'll help you collect fees" is a stronger pitch than "we'll send SMS".

### Option B: "The institute back office"

An institute with 5–30 teachers.

- One front desk for all classes, a split of each fee into teacher share and institute share, a monthly settlement report per teacher.
- **Why it could win:** this is a messy, money-related problem. Institutes pay more, and one institute brings many teachers.
- **Why it's harder:** IT Signature is strong here, and sales are slower.

### Option C: "The parent trust" product

Built around safety: arrival, absence, departure and late-pickup alerts.

- **Why it could win:** parents of younger children (grade 6–11) care a lot about this.
- **Why it's harder:** parents don't pay, teachers do. Teachers have to see value for themselves.

**Recommendation:** start with **A** and design the data model so **B** can follow. Keep **C**'s absence alerts as a feature within A.

## Pricing

"Per class per month" is simple, but think it through:

- A teacher with **one huge class of 800 students** would pay the same as a teacher with **one class of 10**. SMS costs would be very different.
- Teachers already think in **students**, since they collect fees per student.

Suggested model to **test** in interviews, not decided:

| Plan | Who | Price idea |
|---|---|---|
| Free | Up to about 30 students, no SMS | Rs. 0, so a teacher can try it on one class |
| Teacher | Up to about 300 students | about Rs. 1,500–2,000/month |
| Institute | Many teachers | Per-teacher or per-student pricing, on quote |
| SMS | All plans | Prepaid **SMS credits** at cost plus a small margin, shown clearly |

Keep SMS **separate and visible**. That protects our margins and matches what teachers expect (tuitionfee.lk does the same).

## What the stack must handle

The stack is not locked. Whatever we choose must handle these needs, which come straight from the research:

1. **Offline door scanning** with a queue, then sync. A PWA with local storage or a native Android app.
2. **Fast QR scanning** on cheap Android phones' cameras.
3. **Sinhala, Tamil and English** throughout, including SMS templates.
4. **Swappable SMS and WhatsApp providers.** Prices change, so don't hard-wire one gateway.
5. **Payment provider integration**: LankaQR through a bank or acquirer, with card payments as backup.
6. **Strong separation between customers**: each teacher's or institute's data kept apart (multi-tenancy, for example row-level security).
7. **PDPA needs**: consent records, export and delete, audit logs and a known hosting region.
8. **Cheap to run** at low volume, because revenue per customer is small.

Next.js + Supabase can meet most of these, since Supabase row-level security suits point 6. Point 1 (offline scanning) and point 5 (LankaQR) are the parts to prototype before committing.

## Validation plan (before writing product code)

**Goal:** find out whether Option A is something teachers will pay for.

1. **Interview 15–20 teachers**: mix of mass-class, small-group, urban and outstation. Ask:
   - How do you collect fees today? How much do you lose to unpaid fees?
   - How long does the door check take? Who does it?
   - Have you tried a system before? Why did you stop or stay?
   - Would parents pay by QR? Do they already?
   - What would you pay per month?
2. **Interview 3–5 institute owners** about fee splitting and what they use now.
3. **Talk to 5–10 parents** about arrival and absence alerts: SMS or WhatsApp, and which language?
4. **Try competitors' free trials** (tuitionfee.lk, ClassFlow) and note what is slow or confusing.
5. **Ask a bank or acquirer** how a platform can offer LankaQR collection for many small merchants.
6. **Short legal check** on PDPA roles and children's consent.

**Signals to go ahead:**
- At least 5 teachers say they would pay about Rs. 1,500/month or more and agree to a pilot.
- At least 1 institute agrees to a pilot.
- A workable path to LankaQR collection.

**Signals to rethink:**
- Teachers are happy with free tools or WhatsApp plus a notebook.
- No practical way to offer LankaQR as a platform.

## Final verdict

**The idea suits Sri Lanka very well, and that is exactly why others are already doing it.** Building "QR attendance + arrival SMS" again would mean competing on price against free tools. Building **"the easiest way for a tuition teacher to collect fees and keep parents informed, in Sinhala and Tamil, even offline"**, with LankaQR at the centre, has a real chance. Validate that with teachers first.
