RESTAURANT POS — PWA INSTALL FILES

1. Put manifest.json, sw.js and the icons folder in the SAME folder as your existing index.html.
2. In index.html, inside <head>, add:
   <link rel="manifest" href="manifest.json">
   <meta name="theme-color" content="#17243b">
3. Just before </body> in index.html, add:
   <script>
   if ("serviceWorker" in navigator) {
     window.addEventListener("load", () => {
       navigator.serviceWorker.register("./sw.js")
         .catch(error => console.error("Offline setup failed:", error));
     });
   }
   </script>
4. Upload the complete folder to an HTTPS host, such as GitHub Pages.
5. Open the HTTPS website in Chrome on Android. Use Chrome menu (⋮) > Install app
   or Add to Home screen.

IMPORTANT:
- A PWA is an installable web app, not an APK file.
- The site must be served over HTTPS (or localhost) for installation/service workers.
- Test the app online once before going offline.
- This starter service worker caches the app shell. Browser localStorage data remains
  on that device/browser and is not synced to other devices.
