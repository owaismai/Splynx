# Custom Login Page Title & Favicon for Splynx Partner Portal

This repository contains a modified version of the `login.twig` file used in the Splynx Partner Portal.
The customization changes the **page title** and **favicon** only when the user visits the login page at:

```
https://portal.partner2.com/portal/login
```

All other pages remain unchanged.

---

## Features

* Custom **page title**: Displays your company name (e.g. `Partner2 Portal`) instead of the default Splynx title.
* Custom **favicon**: Displays your company favicon (`favicon.ico`) instead of the default Splynx icon.
* Affects **only** the login page URL, leaving all other Splynx pages with their default settings.

---

## Prerequisites

* A running **Splynx instance** (tested with `views/portal/login.twig`).
* SSH or file manager access to your server where Splynx is installed.
* Your company favicon uploaded to a **public URL**.

---

## Step 1: Upload your favicon

Upload your custom favicon (`favicon.ico`) to a **publicly accessible location** on your website, for example:

```
https://partner2.com/favicon.ico
```

This file will be used on the login page.

---

## Step 2: Backup original file

Always make a backup before modifying Splynx files:

```bash
cd /var/www/splynx/views/portal/
cp login.twig login.twig.bak
```

---

## Step 3: Replace the `login.twig` file

Copy the modified `login.twig` from this repository into:

```
/var/www/splynx/views/portal/login.twig
```

This file contains:

* JavaScript logic to detect when the URL is `/portal/login`.
* Custom code to replace the title and favicon only on that page.

---

## Step 4: Edit the code with your details

Inside the modified `login.twig`, look for this section:

```javascript
var targetUrl = 'https://portal.partner2.com/portal/login';
var faviconUrl = 'https://partner2.com/favicon.ico';
```

Update:

* `targetUrl` → Replace with your portal login URL.
* `faviconUrl` → Replace with the public link to your favicon.

Example for **Partner2**:

```javascript
var targetUrl = 'https://portal.partner2.com/portal/login';
var faviconUrl = 'https://partner2.com/favicon.ico';
```

---

## Step 5: Clear browser cache

After saving changes:

* Reload your portal in an **incognito/private window**, or
* Clear your browser cache to see the new favicon and title.

---

## Example Result

When visiting:

```
https://portal.partner2.com/portal/login
```

The page will show:

* Title: **Partner2 Portal**
* Favicon of partner2

When visiting any other Splynx page (e.g. `/portal/main`), the default Splynx title and favicon remain.

---

## Notes

* Updates to Splynx may overwrite `login.twig`. If this happens, re-apply your modified file.
* Make sure your favicon is **.ico format** for maximum browser compatibility.
* Works with `http` and `https` URLs, but ensure you use the **exact URL string** for matching.

---

## License

This customization is provided as-is under the MIT License. You may use, modify, and distribute it freely.

