# Old Portfolio

Developer: Sidali DJEGHBAL

This is a static, responsive personal portfolio website built with HTML, CSS, and JavaScript. It showcases About, Resume, Portfolio, and Contact sections using animated lightbox-style panels, a preloader, category filtering, sliders, and a dark theme.

## Overview

- Single-page entry in `index.html` with four modal/lightbox sections: `#about`, `#resume`, `#portfolio`, and `#contact`.
- Responsive navbar and animated overlay for opening/closing panels.
- Portfolio grid with category filters and image lightbox.
- Testimonials slider, skills progress bars, and a contact form (AJAX).
- Dark color scheme with customizable accent colors.

## Tech Stack & Libraries

- HTML5, CSS3, JavaScript
- Bootstrap 4 (`css/bootstrap-custom.css`, `js/bootstrap.bundle.min.js`)
- jQuery (`js/jquery.min.js`)
- Tiny Slider (`js/tiny-slider.js`) for testimonials/carousels
- Isotope + ImagesLoaded (`js/isotope.pkgd.min.js`, `js/imagesloaded.pkgd.min.js`) for portfolio layout/filtering
- Lity (`js/lity.min.js`) for image/video lightboxes
- AnimatedModal (`js/animatedModal.js`) for section animations
- Simplebar (`js/simplebar.min.js`) for custom scrollbars inside lightboxes
- Ionicons (loaded via CDN)
- Optional: jQuery.mb.YTPlayer (CSS referenced; see Notes)

## Project Structure

```
old-portfolio/
├── css/
│   ├── bootstrap-custom.css
│   ├── colors/
│   │   └── main-darkgreen.css
│   ├── lity.min.css
│   ├── main.css
│   ├── simplebar.min.css
│   └── tiny-slider.css
├── img/
│   ├── favicons/
│   │   └── apple-touch-icon.png
│   ├── home-tab.svg
│   ├── home.svg
│   ├── info-img.png
│   ├── item-1.jpg
│   ├── item-2.png
│   ├── item-3.png
│   ├── item-4.png
│   ├── item-5.png
│   ├── item-6.png
│   ├── logo.png
│   └── logo.svg
├── js/
│   ├── animatedModal.js
│   ├── bootstrap.bundle.min.js
│   ├── imagesloaded.pkgd.min.js
│   ├── isotope.pkgd.min.js
│   ├── jquery.min.js
│   ├── lity.min.js
│   ├── main.js
│   ├── simplebar.min.js
│   └── tiny-slider.js
├── well-known/
│   └── discord
└── index.html
```

## How It Works

- Entry point: `index.html` loads styles and scripts, defines the navbar and the four lightbox sections.
- Scripts are included at the bottom of `index.html` in this order:
  1. `js/jquery.min.js`
  2. `js/bootstrap.bundle.min.js`
  3. `js/imagesloaded.pkgd.min.js`
  4. `js/isotope.pkgd.min.js`
  5. `js/animatedModal.js`
  6. `js/tiny-slider.js`
  7. `js/lity.min.js`
  8. `js/simplebar.min.js`
  9. `js/main.js`
  10. Ionicons CDN

- `js/main.js` initializes:
  - AnimatedModal for the `#about`, `#resume`, `#portfolio`, `#contact` sections.
  - Lity for `[data-lightbox]` links in portfolio items.
  - Tiny Slider for testimonials in `#about .testimonials-section .my-slider`.
  - Isotope with ImagesLoaded for the portfolio grid and category filters.
  - Skills progress bars in `#resume .skills-section`.
  - Preloader fade-out on window load.
  - Viewport height CSS variable `--vh` to handle mobile 100vh issues.
  - AJAX submission for the contact form.

## Getting Started

### Quick Preview

- Open `index.html` in any modern browser.

### Optional: Run a local server

- Node.js: `npx serve` or `npx http-server` in the project root.
- Python 3: `python -m http.server` and visit `http://localhost:8000/`.

## Customization

### Content

- `index.html`
  - Navbar links correspond to the lightbox IDs: `#about`, `#resume`, `#portfolio`, `#contact`.
  - Update the About section text, social links, and CV link.
  - Update Resume items (Experience/Skills) markup and skill percentages.
  - Portfolio items: change thumbnail images under `img/` and external links.
  - Contact info and form placeholders under the Contact section.

### Styling

- Global styles: `css/main.css` (minified) and `css/bootstrap-custom.css`.
- Color scheme: `css/colors/main-darkgreen.css` controls accent colors (e.g., `.resume-section .resume-item`, `.skills-section .progress-bar`, `.portfolio-section` filters, etc.).
  - To change accent color, edit the hex values in `main-darkgreen.css`.
  - The active scheme is linked via `<link id="color-scheme" href="css/colors/main-darkgreen.css">` in `index.html`.

### Scripts

- `js/main.js` is minified/obfuscated and orchestrates plugin initialization and UI behaviors. If you plan to extend behaviors, consider replacing it with a readable version or documenting changes carefully.
- Maintain the script inclusion order shown above to avoid dependency issues.

## Contact Form Backend

- The form posts to `php/contact.php` and expects a plain text response of `Success` on success.
- This repository does not include the backend. You must add your own server-side endpoint.

Example minimal PHP handler (for reference only):

```php
<?php
// php/contact.php
header('Content-Type: text/plain');
if ($_SERVER['REQUEST_METHOD'] !== 'POST') { echo 'Error'; exit; }

$name = $_POST['name'] ?? '';
$email = $_POST['email'] ?? '';
$subject = $_POST['subject'] ?? '';
$message = $_POST['message'] ?? '';

// TODO: validate and send email or store message
if ($name && $email && $subject && $message) {
  echo 'Success';
} else {
  echo 'Error';
}
```

## Notes & Known Issues

- `index.html` references `css/jquery.mb.YTPlayer.min.css` for a potential video hero variant (`#homeVideo`).
  - The CSS file is not present in `css/` and there is no corresponding JS included. If you intend to use the video variant, add the YTPlayer assets and initialization, or remove the reference if unused.
- The contact form requires a backend endpoint; without it, submissions will fail and log an error to the browser console.
- `css/main.css` is minified; making large style changes may be easier in `bootstrap-custom.css` and `css/colors/main-darkgreen.css`.
- Keep `well-known/discord` for domain or service verification if needed.

## Deployment

- Static hosting options: GitHub Pages, Netlify, Vercel, or any static host.
- Ensure asset paths remain relative (they are currently local-relative).

## Credits

- Bootstrap: https://getbootstrap.com/
- jQuery: https://jquery.com/
- Tiny Slider: https://github.com/ganlanyuan/tiny-slider
- Isotope: https://isotope.metafizzy.co/
- ImagesLoaded: https://imagesloaded.desandro.com/
- Lity: https://sorgalla.com/lity/
- Simplebar: https://grsmto.github.io/simplebar/
- AnimatedModal: https://github.com/joaopereirawd/animatedModal.js
- Ionicons: https://ionic.io/ionicons
- (Optional) jQuery.mb.YTPlayer: https://pupunzi.open-lab.com/mb-jquery-components/jquery-mb-video/

## Author

- Sidali DJEGHBAL — https://sidali.tech/

## License

- No explicit license is provided in this repository.