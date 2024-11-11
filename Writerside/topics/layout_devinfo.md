# Project organization

The file tree is:

```
ubair-website/
├── node_modules/
├── public/
│   ├── css/
│   │   ├── main.css
│   │   └── *.css
|   ├── data/
│   │   ├── test_liveobs.json
│   │   ├── test_wind_ts.json
│   │   ├── *.json
│   │   └── outlooks/
│   │       └── *.md
│   ├── images/
│   ├── js/
│   │   ├── forecast_data.js
│   │   └── map.js
│   └── partials/
│       └── *.html
├── server/
│   └── server.js
├── views/
│   │   ├── index.html
│   │   └── *.html
├── package.json
└── README.md
```

First, a descriptive overview:
* `node_modules/` contains all the dependencies of the project. Leave alone. From the command line in the root directory, run `npm install` to install all dependencies. (Then `npm start` to start the server.)
* `public/` contains all the files that are served to the user:
  - `css/` contains all the stylesheets. `main.css` is the main stylesheet.
  - `data/` contains all the data files. `test_liveobs.json` and `test_wind_ts.json` are test data files. These will be replaced will real json data files close to operations. The directory `outlooks/` contains all the outlooks that will be identical to the body text of _Ozone Alert_ emails.
  - `images/` contains images, icons, photos, etc.
  - `js/` contains all the JavaScript files. For instance, `map.js` dictates the map page, but also uses `mapUtils.js` from the same folder.
  - `partials/` contains all the "partial" HTML files that represent frequently used assets like sidebars, headers, and footers.
* `server/` contains the `server.js` main server file.
* `views/` contains all the HTML files that are rendered by the server; e.g., `index.html` is the main HTML file.
* `package.json` contains metadata about the project, dependencies, etc.
* `README.md` will be an intro documentation file but we should use this WriterSide/GitHub Pages site for more detailed documentation

### Example: editing position of USU log on the map page:
1. In `/views/map.html`, we have:

```html
<div class="usu-logo">
  <img src="/public/images/images-removebg-preview.png" alt="Logo">
</div>
```

We make sure the map page "sees" the style sheets and javascript with a snippet like this in the `<head>`:

```html
  <link rel="stylesheet" href="/public/css/map.css">
```

2. We see the "class", so we turn to CSS files in `/public/css/` and find the class in `map.css` with style settings specifically for the map page:

```css
.usu-logo img {
    transform: scale(0.5); /* Scales down the logo to 50% */
}
```

3. The javascript file `/public/js/map.js` is where the map is mostly controlled. We can find the usu-logo class:

```javascript
usuLogo.style.position = 'fixed';
usuLogo.style.top = '1%';
usuLogo.style.left = '10px'; // Adjust as needed for spacing from left
usuLogo.style.transform = 'translateY(0)'; // Remove centering
usuLogo.style.zIndex = '2';
```

We also make sure this is accessible by the html page with:

```html
<script type="module" src="/public/js/map.js"></script>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
```

where the second line also imports the leaflet map library.