📱 Experiment No. 3
Convert React App into Progressive Web App (PWA)
🎯 Objective
To convert an existing React application into a Progressive Web App (PWA) with offline capabilities using service workers, enabling installability and caching.

🧠 Overview
A Progressive Web App (PWA) is a web application that provides a native app-like experience. It works offline, loads faster, and can be installed on a user’s device.

⚙️ Technologies Used
React.js

Service Workers

Web App Manifest

Workbox (optional for advanced caching)

📌 Steps Performed
🔹 Step 1: Add manifest.json
Created a manifest.json file in the public folder.

Included:

App name

Icons

Theme color

Background color

Linked it in index.html.

✅ Result: App becomes installable in browser.

🔹 Step 2: Register Service Worker
Enabled service worker in React (serviceWorkerRegistration.js).

Cached static assets:

HTML

CSS

JavaScript

// serviceWorkerRegistration.js
serviceWorker.register();
✅ Result: App loads even when offline.

🔹 Step 3: Implement Runtime Caching
Used custom service worker / Workbox.

Cached API responses dynamically.

Example:

self.addEventListener('fetch', (event) => {
  if (event.request.url.includes('/api')) {
    event.respondWith(
      caches.open('api-cache').then(cache => {
        return fetch(event.request).then(response => {
          cache.put(event.request, response.clone());
          return response;
        }).catch(() => cache.match(event.request));
      })
    );
  }
});
✅ Result: API data available even without internet.

📊 Features Achieved
✅ Offline support

✅ Faster loading with caching

✅ Installable web app

✅ Improved performance

🧪 Testing
Turn off internet and reload app

Verify cached content loads

Check install option in browser

📷 Output
App runs offline successfully

Install prompt appears in browser

🚀 Conclusion
The React application was successfully converted into a Progressive Web App, improving performance, reliability, and user experience with offline capabilities.
