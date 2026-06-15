# Lovable build prompt — GLP-1 Macro Coach

Paste everything in the code block below into Lovable as your first prompt.
It recreates the app we built, so Lovable starts from our work instead of scratch.

---

```
Build a personal health web app called "GLP-1 Macro Coach" — a mobile-first nutrition
tracker for someone on a GLP-1 medication (tirzepatide), focused on preserving muscle and
hair during weight loss. It is for my own personal use.

DESIGN
Dark, modern, app-like, mobile-first. Deep navy background (#0f1226), card surfaces,
purple-to-blue gradient accents (#6e8efb -> #a777e3), green for success/targets met
(#38d39f). Rounded cards, clean and friendly. Should feel great added to an iPhone home screen.

ACCOUNTS & SYNC
Add user sign-in with Google and store each user's data in the cloud so it syncs across all
my devices in real time. Keep each user's data private to them.

FEATURE 1 — MACRO CALCULATOR
Inputs: sex; age; height (toggle imperial ft/in or metric cm); current weight (lb or kg);
activity level (Sedentary 1.2, Light 1.375, Moderate 1.55, Active 1.725, Very active 1.9);
goal (Maintain = 0, Gentle loss -250 cal, Steady loss -500, Faster loss -750); medication
(Tirzepatide, Semaglutide, Other, None); weeks since starting.
Math:
- BMR (Mifflin-St Jeor) = 10*kg + 6.25*cm - 5*age + (men: +5, women: -161)
- TDEE = BMR * activity factor
- Calorie target = TDEE - goal deficit, with a safety floor (min 1500 men / 1200 women);
  if the floor is hit, show a gentle warning.
- Protein = 1.6 g per kg body weight (protein-forward to protect muscle and hair)
- Fat = 25% of calories
- Carbs = the remainder. If protein + fat exceed the target, trim protein but keep ~10%
  of calories as carbs, and show a note.
Output: a big calories-per-day number; protein/carbs/fat cards (grams + % of calories);
a "protein per meal" hint (protein / 4); and journey-aware tips that change by medication
and weeks (early weeks: build protein-first habits; mid: don't skip meals, use protein-dense
snacks; later: watch micronutrients, consider a multivitamin). NOTE: I microdose tirzepatide
at a steady 2.5mg, so tips should NOT assume the dose keeps climbing.

FEATURE 2 — DAILY VITAMIN & SUPPLEMENT TRACKER
A daily checklist of MY items (below). For each item show: a "taken" checkbox; a box to log
the amount I actually took today; and a live "% of target" measured against the LOW end of
the target range (100% is the goal; color green at >=100%, amber 50-99%, grey if blank).
Show an "X of N at 100% today" counter. Resets daily; saved and synced.
Items (Name | Target | Note):
- Total Protein | 100-115 g | Hair is protein - top lever
- Water | 80-100 oz | Extra important on a GLP-1
- Vitamin D3 | 2,000-4,000 IU | Monitor labs
- B12 | 25-500 mcg | Check supplement label
- Folate | 400-800 mcg DFE | From prenatal
- Iron | 18 mg | Ferritin matters for hair
- Magnesium | 300-400 mg | Glycinate; sleep & constipation
- Zinc | 10-15 mg | Potential gap
- Selenium | 55-100 mcg | Potential gap
- Iodine | 150 mcg | From prenatal
- Choline | 425-550 mg | Mostly from food
- Omega-3 EPA/DHA | 500-1,000 mg | Check fish oil label
- Pumpkin Seed Oil | 1,000-2,000 mg | Hair support
- Saw Palmetto | 160-320 mg | Hair support

FEATURE 3 — WEIGHT JOURNEY
Log weight by date; show a line chart over time plus Start / Latest / Change stats. Show my
current dose as "2.5mg microdose". One entry per day; saved and synced.

FEATURE 4 — SOURCES SECTION
A "Why these numbers? (Sources)" section citing: Mifflin-St Jeor 1990 (Am J Clin Nutr);
Morton et al. 2018 protein meta-analysis (~1.6 g/kg, Br J Sports Med); ISSN Protein & Exercise
position stand; American Society for Nutrition "Nutritional Priorities to Support GLP-1
Therapy for Obesity"; Guo & Katta "Diet and hair loss" review.

FEATURE 5 — DISCLAIMER
A clear "This is not medical advice" note: educational only, not a substitute for my doctor,
pharmacist, or dietitian; confirm what I actually need with bloodwork.
```

---

## Tips for using Lovable
- Start a **new project** and paste the block above as the first message.
- Build in **small steps** after that: e.g. "now improve the vitamin tracker spacing,"
  "add a weekly protein average to the journey." One change per message works best.
- When you connect Google sign-in, Lovable will walk you through its backend (Supabase) —
  similar idea to the Firebase setup we did.
- Keep this repo (`landerlunar/sandbox`) as your working backup.
