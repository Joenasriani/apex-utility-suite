# Apex Utility Suite

A browser-based collection of developer and everyday utilities, implemented in a single `index.html` file. React renders the interface; JavaScript handles data conversion, formatting, hashing, image tools, text processing, and other operations in the browser.

**Live page:** https://joenasriani.github.io/apex-utility-suite/

## Implemented tools

The source defines more than 50 tool entries across these groups:

- **Data conversion:** CSV, JSON, XML, TSV, and HTML table conversions. Excel (`.xls` and `.xlsx`) file import uses SheetJS to read the first worksheet and place CSV or JSON into the input editor.
- **Files:** Convert a selected file to a Base64 data URL or decode Base64 content for file download.
- **Developer tools:** Line-based text diff, regular expression tester, color explorer, timestamp utility, network speed test, and an .htaccess snippet generator.
- **Hashing and encoding:** SHA-1, SHA-256, SHA-512, MD5, Base64, and URL encoding/decoding. These tools do not constitute encryption or a complete security assessment.
- **Code formatting:** JSON, JavaScript, CSS, and HTML formatting with Prettier; simplified SQL formatting and Python indentation helpers.
- **Minification:** Basic JSON, JavaScript, and CSS minification. The JavaScript and CSS implementations use string replacements rather than full production minifier parsers.
- **Images:** Browser-based image resizing and favicon generation.
- **Network and validation:** Public IP lookup, a router-password reference tool, and email syntax validation.
- **Numbers and text:** Number-base conversion, basic unit/data-size conversions, keyword tools, word count, text reversal, text/hex conversion, HTML tag removal, and HTML escaping.

The interface includes tool search, category navigation, file upload, copy actions, and a light/dark theme toggle.

## Architecture and dependencies

There is no `package.json`, bundler configuration, or npm build script in this repository. The application is an HTML page with embedded React/JSX transformed in the browser by Babel.

The page loads its dependencies from third-party CDNs, including React 18, React DOM, Babel Standalone, Tailwind CSS, Lucide React, Prettier, CryptoJS, PapaParse, jsdiff, and SheetJS.

An internet connection is needed to load those external libraries when they are not already cached. Availability and behavior depend on the referenced CDN resources.

## Use

Open the [hosted page](https://joenasriani.github.io/apex-utility-suite/) or clone the repository:

```bash
git clone https://github.com/Joenasriani/apex-utility-suite.git
cd apex-utility-suite
```

For local use, serve the directory with a static web server, for example:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser. The HTML loads its external dependencies over the network.

There is no `npm install`, `npm run dev`, or `npm run build` step for the current repository.

## Data handling and limitations

Most formatting, conversion, hashing, and file operations are implemented in browser JavaScript. Uploaded text and spreadsheet files are read with browser file APIs. The inspected application source does not contain an upload endpoint for those files.

**This is not an offline or network-free application.** The page requests scripts and modules from external CDNs. Its public IP utility also calls `api.ipify.org`, which receives a network request when that feature is used. Do not interpret local processing as a guarantee that all activity or data remains on the device.

Some utilities are intentionally lightweight. Email validation checks syntax, not deliverability; simple formatting and minification are not substitutes for dedicated language parsers or build tools; and output from conversions should be checked before production use.

Features above are identified from the source code. No browser end-to-end tests, security audit, external privacy audit, or production reliability verification was performed for this README update.

Credit: Joe Nasr
