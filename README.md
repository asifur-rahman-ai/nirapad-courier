# Nirapad Courier (নিরাপদ কুরিয়ার)

A demo website and admin dashboard for a parcel courier service covering all 64 districts of Bangladesh. The interface is fully in Bangla and lives in a single HTML file.

**Live demo:** https://asifur-rahman-ai.github.io/nirapad-courier/

> ⚠️ This is a demo. There is no server or database; all data is stored in your browser's `localStorage`. The hotline number and office address are placeholders.

---

## Features

### Public website

- **Parcel tracking:** enter a tracking ID to see a five-step timeline with timestamps: Booked → Picked up → Reached hub → Out for delivery → Delivered.
- **Services:** home delivery, cash on delivery, e-commerce merchant service, express delivery, document delivery and SMS updates.
- **Charge calculator:** pick the districts, weight and COD amount to get the delivery charge instantly.
- **Coverage:** all 64 districts listed under the 8 divisions.
- **Parcel booking form:** sender, receiver and parcel details with validation (11-digit Bangladeshi mobile numbers). A successful booking returns a new tracking ID.
- **Contact form** and a hamburger menu on mobile.

### Admin dashboard

- KPI cards: total parcels, in progress, delivered, total revenue, COD collected
- Search by ID, name or mobile number, and filter by status
- Move each parcel to the next step or cancel it, with timestamps recorded
- One-click reset to the demo data

---

## Delivery charges

| Route | Charge | Delivery time |
|---|---|---|
| Within the same district | ৳60 | 24 hours |
| Within the same division | ৳100 | 24–48 hours |
| Anywhere in Bangladesh | ৳130 | 48–72 hours |

- ৳20 extra per kg after the first 1 kg (weight is rounded up to the next whole kg)
- COD charge: 1% of the COD amount

Example: Dhaka to Chattogram, 1 kg, COD ৳1,500 → ৳130 + ৳15 = **৳145**

To change the rates, edit the `fee()` function in `index.html`.

---

## Try the demo

**Tracking:** enter one of these IDs on the home page

| ID | Route | Status |
|---|---|---|
| `NPC-1001` | Dhaka → Chattogram | Out for delivery |
| `NPC-1002` | Chattogram → Sylhet | Reached hub |
| `NPC-1003` | Chattogram → Chattogram | Delivered |

**Admin login:** click "অ্যাডমিন" (Admin) in the menu

- Username: `admin`
- Password: `admin123`

**End-to-end flow:**

1. Fill in the parcel booking form and confirm. You get a new ID such as `NPC-1004`.
2. Log in as admin. The new parcel appears at the top of the table.
3. Click "পরের ধাপ" (Next step) to advance its status.
4. Log out and track the same ID. The timeline shows the update.

---

## Tech

- A single `index.html`: HTML, CSS and vanilla JavaScript
- No framework, no build step, no backend
- Font: [Hind Siliguri](https://fonts.google.com/specimen/Hind+Siliguri) via Google Fonts
- Icons: [Tabler Icons](https://tabler.io/icons) via CDN
- Storage: parcels in `localStorage` (`npc_parcels`), admin session in `sessionStorage`
- Numbers and currency displayed in Bangla digits
- Responsive on mobile

---

## Run locally

```bash
git clone https://github.com/asifur-rahman-ai/nirapad-courier.git
cd nirapad-courier
```

Then open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy on GitHub Pages

1. Push `index.html` (and `logo.png`) to the `main` branch.
2. Go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, then `main` and `/ (root)`.
4. The site goes live at `https://asifur-rahman-ai.github.io/nirapad-courier/`.

---

## Project structure

```
nirapad-courier/
├── index.html   # website + admin (markup, styles, script)
├── logo.png     # logo (falls back to a green "N" badge if missing)
└── README.md
```

---

## Before going live

- [ ] Replace the hotline number (`০৯৬XX-XXXXXX`) and head office address
- [ ] Add `logo.png`
- [ ] Add a real backend and database so data is shared across devices
- [ ] Move admin login to the server. The current login is for the demo only; the password is in the page source, so anyone can see it.
- [ ] Send booking and contact form data to the server (the contact form currently only shows a confirmation)
- [ ] Integrate SMS updates and bKash / Nagad payments

---

## Author

Built by [Md. Asifur Rahman](https://github.com/asifur-rahman-ai).

© 2026 Nirapad Courier. All rights reserved.
