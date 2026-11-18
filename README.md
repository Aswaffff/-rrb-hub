# RRB Hub — Official Study Material Website (GitHub Pages Ready)

This repository contains the complete, production-ready frontend for **RRB Hub** (Malayalam, English, and Hindi RRB examination study material PDFs at `₹151` each), connected to your existing Supabase project (`https://dujgqwzxxmpdsikhkhbk.supabase.co`) and Razorpay Live Checkout.

---

## 1. Repository Root Structure (GitHub Pages)

All files are placed directly at the repository root so GitHub Pages serves `index.html` immediately without needing a build server:

| File / Folder | Required on GitHub Pages? | Description |
| :--- | :--- | :--- |
| `index.html` | **Yes (Required)** | Main website entry point at the repository root (`/`). Contains all HTML, CSS, JavaScript, and your publishable `VITE_SUPABASE_ANON_KEY`. |
| `404.html` | **Yes (Recommended)** | Fallback entry point so visitors opening direct sub-links never see a GitHub 404 error. |
| `favicon.svg` | **Yes (Required)** | Custom red-and-white RRB Hub open-book and railway-track browser tab icon. |
| `assets/hero-locomotive.jpg` | **Yes (Required)** | High-resolution Indian electric locomotive image used in the Hero banner and 3D product book covers. |
| `.nojekyll` | **Yes (Required)** | Tells GitHub Pages to serve all static assets directly without running Jekyll processing. |
| `.gitignore` | Optional | Prevents accidental commits of local `.env` files or OS metadata files. |
| `.env.example` | Reference only | Template showing publishable frontend keys vs. server-only Supabase Edge Function secrets. |
| `supabase/` | Reference only | Contains your reference Edge Function TypeScript files (`create-razorpay-order`, `payment-status`, `admin-orders`, `razorpay-webhook`) and non-destructive SQL schema check. |

---

## 2. How to Publish on GitHub Pages (Step-by-Step)

### Step 1: Create a New GitHub Repository
1. Log in to [GitHub](https://github.com/) and click the **`+`** icon in the top-right corner → **New repository**.
2. Enter a repository name (for example, `rrb-hub`).
3. Choose **Public** (required for free GitHub Pages hosting on a free GitHub account).
4. Click **Create repository**.

### Step 2: Upload the Website Files to the Repository Root
1. Unzip `rrb-hub-github-pages.zip` on your phone or computer.
2. In your new GitHub repository, click **uploading an existing file** (or **Add file → Upload files**).
3. Select and drag the extracted files (`index.html`, `404.html`, `favicon.svg`, `.nojekyll`, `README.md`, and the `assets/` folder containing `hero-locomotive.jpg`) directly into the upload box so that **`index.html` is at the top level of the repository** (not buried inside a subfolder).
4. Type `"Initial RRB Hub website release"` in the commit message box and click **Commit changes**.

### Step 3: Enable GitHub Pages
1. Inside your GitHub repository, click **Settings** (top menu bar).
2. In the left sidebar, click **Pages** (under "Code and automation").
3. Under **Build and deployment**:
   * **Source:** Select **Deploy from a branch**.
   * **Branch:** Select **`main`** (or `master`) and folder **`/ (root)`**, then click **Save**.
4. Wait 1 to 2 minutes and refresh the **Settings → Pages** screen. GitHub will display your live website URL at the top:
   `https://<your-github-username>.github.io/<repository-name>/`

---

## 3. How to Update the Website or Set Your Razorpay Key ID Later

To update your publishable Razorpay Key ID (`VITE_RAZORPAY_KEY_ID`) directly on GitHub:
1. Open `index.html` in your GitHub repository and click the **Pencil icon (Edit this file)**.
2. Near the top of `index.html` (around Line 12), locate `window.__RRB_HUB_ENV__`:
   ```javascript
   window.__RRB_HUB_ENV__ = window.__RRB_HUB_ENV__ || {
     VITE_SUPABASE_URL: "https://dujgqwzxxmpdsikhkhbk.supabase.co",
     VITE_SUPABASE_ANON_KEY: "sb_publishable_feb6_kXW2mlweliMCv73Rg_6NdCVwIe",
     VITE_SUPABASE_PUBLISHABLE_KEY: "sb_publishable_feb6_kXW2mlweliMCv73Rg_6NdCVwIe",
     VITE_RAZORPAY_KEY_ID: "YOUR_RAZORPAY_KEY_ID_HERE"
   };
   ```
3. Replace `"YOUR_RAZORPAY_KEY_ID_HERE"` with your publishable Razorpay Key ID (`rzp_live_...` or `rzp_test_...`) and click **Commit changes**. *(Never put any secret key such as `RAZORPAY_KEY_SECRET` or `SUPABASE_SERVICE_ROLE_KEY` in `index.html`).*
