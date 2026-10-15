# Sofara Admin Panel

This repository contains the standalone article dashboard. The Firebase web configuration in `firebase-config.js` is client configuration, not a service-account key. Never add a Firebase service-account private key or a GitHub token to this repository.

## Hosting

Enable GitHub Pages for this repository from **Settings → Pages** and select the `main` branch with the root folder. The dashboard can then be opened at:

`https://nexorastudiodevv-ctrl.github.io/sofara-admin-panel/`

Add `nexorastudiodevv-ctrl.github.io` to Firebase Authentication's authorized domains. Keep Firebase Authentication enabled and grant the admin user the `admin: true` custom claim. Firestore rules must restrict article writes to that admin claim.

## Article publishing

When an article is saved with status `published`, the public website reads it directly from Firestore: published articles appear in the homepage and blog list, and their article page loads by slug. Firestore rules must allow public reads only for published articles.

The dashboard also requests a GitHub Actions run to generate static article pages and update the sitemap for search engines. If that optional static-page update cannot start, the article is still live through Firebase; the workflow retries automatically every 15 minutes. Do not place a GitHub token or Firebase service-account private key in this dashboard. Keep those credentials only in the publishing service's environment.

## Affiliate links

In an article, optionally enter an HTTPS partner URL, a short description, a button label, and choose whether the promotion appears at the beginning, middle, or end. The generated article adds a commission disclosure automatically. Add only partner links relevant to the article and follow the partner program's terms.
