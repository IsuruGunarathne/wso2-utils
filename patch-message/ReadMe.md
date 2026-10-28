# Patch Message Instructions

## Patch Message Bookmarklet Setup

Use this guide to trigger your `patch-message` extraction script directly from your browser's address bar using a simple keyboard shortcut.

---

## 1. The Javascript Code

Copy the `patch-message.bookmarklet.txt` snippet to use as your search engine URL:

### Auto-updating loader (alternative)

Instead of the full snippet, you can use this short loader. It downloads `patch-message.js` from this repo's `main` branch every time it runs, so changes pushed to `main` reach you without updating the browser:

```
javascript:(()=>{fetch('https://raw.githubusercontent.com/IsuruGunarathne/wso2-utils/main/patch-message/patch-message.js',{cache:'no-store',referrerPolicy:'no-referrer'}).then(r=>{if(!r.ok)throw new Error('HTTP '+r.status);return r.text()}).then(src=>new Function(src)()).catch(e=>console.error('Patch message loader failed:',e))})();void 0;
```

* Whatever is on `main` runs inside your logged-in UMT session, so only point the loader at a repo where you trust everyone who can push.
* GitHub caches the file for up to 5 minutes, so a change can take that long to show up.
* GitHub has to be reachable. If it isn't, the console shows `Patch message loader failed`.
* The script is downloaded before it runs, so copying always needs a click on the page (see How to Use).

## 2. Setup Instructions (Chrome / Edge)

1. Open your browser settings and navigate to:
   * **Chrome:** `chrome://settings/searchEngines`
   * **Edge:** `edge://settings/searchEngines`
2. Scroll down to the **Site search** section and click **Add**.
3. Fill out the fields as follows:
   * **Name:** `Patch Message`
   * **Shortcut:** `pm` *(or your preferred short trigger)*
   * **URL:** Paste the content of `patch-message.bookmarklet.txt` (or the loader above) into it.
4. Click **Save**.

---

## 3. How to Use

When you are on the UMT view update page:

1. Press **`Cmd + L`** (Mac) or **`Ctrl + L`** (Windows) to highlight the address bar.
2. Type **`pm`** and press **`Enter`**.
3. The Update description is logged in the browser console. Chrome usually doesn't allow copying from the address bar, so click anywhere on the page to copy it to your clipboard. The console shows `Copied to clipboard.` once it has been copied.
  e.g 
  ```
  U2: 19763
Internal Issue: <issue link>
Public Issue: https://github.com/wso2/api-manager/issues/<issue-no>
Deliverables:
Modified:
  - repository/components/plugins/org.wso2.carbon.apimgt.impl_9.27.188.jar
Most Likely ETA: 2026-09-24
Staging build status: SUCCESS
Manual Testing: PENDING
Applicable components: AIO, ACP, TM, UGW
  ```
