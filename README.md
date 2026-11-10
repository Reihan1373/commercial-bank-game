# Commercial Bank Challenge — Reihan1373

Three-group classroom mortgage lending simulation (G1–G3) with seven borrowers, instructor-controlled outcome reveals, and profit/loss leaderboard.

## This package prevents the Firebase key being committed to GitHub source

The repository `config.js` contains ONLY placeholders. During publishing, GitHub Actions reads the `FIREBASE_WEB_CONFIG` Actions repository secret and creates the public client-side `config.js` inside the deployed website. This avoids putting the Firebase key into commits (and therefore avoids the same `config.js` source secret-scanning alert). **The Firebase web API key will still be visible in the public website**, as Firebase intends. This is not a private credential; use API restrictions, Firestore rules and instructor authentication. Never upload instructor outcome JSON, instructor password, service-account keys, or join codes.

## Setup (new Firebase project: commercial-bank-reihan-2026)

1. Enable Email/Password + Anonymous in Firebase Authentication; create the instructor user and Firestore `admins/{uid}` document with `role: "instructor"`.
2. Create the Firestore database and publish the provided `firestore.rules` (you may already have done this).
3. In GitHub repo Settings > Secrets and variables > Actions > New repository secret, create `FIREBASE_WEB_CONFIG` with the JSON config for your new Firebase web app. Example JSON structure:
   `{"apiKey":"...","authDomain":"...","projectId":"commercial-bank-reihan-2026","storageBucket":"...","messagingSenderId":"...","appId":"..."}`
4. Upload these website files at repository ROOT, preserving `.github/workflows/deploy.yml` path. Do NOT upload a private instructor outcome file.
5. GitHub Settings > Pages > Build and deployment: select `GitHub Actions` as Source. GitHub Actions > `Deploy Commercial Bank Game` > `Run workflow` if necessary.
6. Firebase Authentication > Settings > Authorized domains: add `reihan1373.github.io` if not already there.
7. Test https://reihan1373.github.io/commercial-bank-game/ and https://reihan1373.github.io/commercial-bank-game/admin.html in separate browser profiles.
8. Instructor signs in and loads `Commercial_Bank_Instructor_Secret_Outcomes_Reihan1373.json` from local computer, then clicks Initialize/reset to create join codes.

## Game rules

- $1,000B starting cash per bank; 7 loans totaling $1,250B; minimum 3 approvals
- Decisions: Reject / Approve & Hold / Approve & Sell
- Three groups G1, G2, G3 each have one group leader
- Instructor reveals all seven outcomes and opens profit/loss scoreboard
- Amounts, rates, LTV, DSCR, interest months and recovery amounts are *classroom simulation assumptions*, not reported corporate loan losses.

## Safety

Do not put `Commercial_Bank_Instructor_Secret_Outcomes_Reihan1373.json` into the repo, even temporarily. A public GitHub repository preserves commit history. Avoid using the instructor and student portals in the same browser profile. Test all three group sign-ins and result calculations before grading.
