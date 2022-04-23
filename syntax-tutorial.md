# Syntax tutorial per file

## manifest.json
File contains all configuration info: essential for Chrome to recognize project as extension.

`"manfiest_version": 2` Manifest ver. 1 was deprecated in Chrome 18. Developers should currently specify manifest_version 2 or 3

`"name": "Extension name"` a name for the extension

`"version": "0.0.1"` developer-specified Chrome store version of the extension, e.g., update 0.0.2, etc.

`"content_scripts": [ { ... } ]` array of all content scripts of application (e.g., js files to listen to, paths)

- `“matches”: [ “<all_urls>” ]` all URL's that extension should be functional on
- `"js": [ "Content.js" ]` what js file should be run (entry point) for extension

## Content.js
Code that serves as logic for extension // see comments

### More possibilites
```javascript
if (window.location.hostname === "www.youtube.com") {
    alert("You are on YouTube");
} // provide alert hostname is YouTube
```

Can organize better: convert into a switch case
```javascript
switch (window.location.hostname) {
    case "www.youtube.com":
        // can replace entire webpage with HTML component: e.g., button
        document.body.innerHTML = "<button> Click This </button>"
        break;
    case "www.tiktok.com":
        // can entire page with separate HTML page.
        documment.body.innerHTML = generateHTML("TikTok");
        break;
    case "www.netflix.com":
        alert("You are on Netflix");
        break;
}
```

## Running and testing extension
Chrome > top right puzzle icon, “Extensions” > “Manage extensions” > top right, “Developer mode”, turn ON > top left, “Load unpacked” > choose project folder containing extension

- extension will apear in Extensions page
- click refresh icon on extension to reload from disk