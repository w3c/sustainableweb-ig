# ReSpec Multipage

- **Version:** 0.3.5
- **Creator:** Alexander Dawson

> [!IMPORTANT]

The Sustainable Web IG has dropped this feature in favor of our [filtering system](https://w3c.github.io/sustainableweb-ig/tagFilter.html) so we won't be continuing to develop it, that being said, it is fully developed and stable so others can continue to utilize it within ReSpec.

## Features

- It supports ReSpec generation mode, HTML Exports, and PR Preview (inc dark mode).
- Uses Vanilla JavaScript with no dependencies (lightweight).
- Progressively enhances (no JavaScript it'll just show the full-document version).
- Uses anchor fragments (it can work offline) and is low maintenance.
- If no fragment exists or an invalid fragment is used it'll point to the first page.
- If the fragment exists it'll show the correct page and jump to the section.
- Supports printing that page (or the full document if in that mode).
- Works across desktop and handheld browsers (good compatibility).

## HTML

The below is **required** to be included, and customized for every page so the buttons work:

```html
<ol class="pageButtons">
	<li><a class="previousPage" href="">Previous page<br>None</a></li>
	<li><a class="fullDocument" href="#full-document">Full document</a></li>
	<li><a class="nextPage" href="">Next page<br>None</a></li>
</ol>
```

## CSS

The below must be included within the `<head>` element:

```css
@media print { body:not(.full-document) #toc { display: none !important; } }
@media (scripting: enabled) {
	.hide { content-visibility: hidden; display: inherit !important; height: 1px; left: -1000px; overflow: hidden; position: absolute; top: -1px; width: 1px; }
	.show { content-visibility: visible; height: auto; left: auto; overflow: unset; position: static; top: auto; width: auto; } }
.pageButtons { margin-top: 2em; padding-left: 0; }
.pageButtons, .pageButtons li, .pageButtons tbody { display: flex; flex: 1; gap: 10px; }
.pageButtons a { align-items: center; border: medium solid #d9d9d9; background-color: var(--tocsidebar-bg); display: flex; font-weight: bold; flex: 1; padding: 0.5em 1em; }
.previousPage { justify-content: left; } .fullDocument { justify-content: center; } .nextPage { justify-content: right; text-align: right; }
@media (scripting: none) {
	.pageButtons { display: none;}
	.hide { display: block !important; height: auto; left: auto; overflow: unset; position: static; top: auto; width: auto; } }
```

## JavaScript

The below must be included within the `<head>` element:

```javascript
<script>
function addMultipage() {
	window.addEventListener('hashchange', onHashChange);
	onHashChange(); }
window.addEventListener("load", (event) => {
	addMultipage(); });
function hashSection(hash) {
	// Grabs the ID's from every element requested
	let arrayGrab = Array.from(document.querySelectorAll(hash));
	let mapID = arrayGrab.map(el => el.getAttribute('id'));
	let filtered = mapID.filter(function (el) { return el != null; });
	return filtered; }
function onHashChange() {
	// Gets the current anchor reference & main locations
	let current = window.location.hash.substring(1);
	let sections = hashSection('body > section');
	// Assign your document sections here (to search for IDs)
	let introduction = hashSection('#introduction *');
	let ux = hashSection('#user-experience-design *');
	let webdev = hashSection('#web-development *');
	let infra = hashSection('#hosting-infrastructure-and-systems *');
	let biz = hashSection('#business-strategy-and-product-management *');
	let considerations = hashSection('#considerations section');
	let glossary = hashSection('#glossary *');
	let credits = hashSection('#acknowledgments section');
	let changelog = hashSection('#changelog section');
	let refs = hashSection('#references *');
	let all = sections.concat(sections, introduction, ux, webdev, infra, biz, considerations, glossary, credits, changelog, refs);
	// Ensures the TOC is only shown to printers when the initial page is loaded
	if (document.body.classList.contains('full-document')) {
		document.body.classList.remove('full-document'); }
	// If current hash or full-document matches, visibility is assured & buttons appear
	// Otherwise content and buttons disappear until requested for that section
	if (current) {
		for (const value of sections) {
			for (const value of sections) {
				// This makes the content visible
				if ( value != current ) {
					document.getElementById(value).classList.remove('show');
					document.getElementById(value).classList.add('hide'); } else {
					document.getElementById(value).classList.remove('hide');
					document.getElementById(value).classList.add('show'); }}
			if (current == "abstract" || current == "sotd") { header(); }
			// Adds buttons to references as ReSpec auto-generated this section
			for (const value of refs) {
				if ( value != current && document.getElementById('references').querySelector('.pageButtons') == null ) {
					document.getElementById('references').innerHTML = document.getElementById('references').innerHTML + `<ol class="pageButtons">
						<li><a class="previousPage" href="#changelog">Previous page<br>Changelog</a></li>
						<li><a class="fullDocument" href="#full-document">Full document</a></li>
						<li></li>
					</ol>`; } }
			// This ensures the buttons don't appear for full-document mode
			// It also shows the TOC to printers on the initial page
			if (current == "full-document") {
				document.body.classList.add("full-document");
				for (const value of sections) {
					document.getElementById(value).classList.remove('hide');
					document.getElementById(value).classList.add('show'); }
					document.querySelectorAll('.pageButtons').forEach(e => e.classList.remove('show'));
					document.querySelectorAll('.pageButtons').forEach(e => e.classList.add('hide'));
					window.scrollTo(0, 0); } else {
					document.querySelectorAll('.pageButtons').forEach(e => e.classList.remove('hide'));
					document.querySelectorAll('.pageButtons').forEach(e => e.classList.add('show')); }
			// If no hash is visible, show at least something on the screen
			let check = false;
			for (const value of all) {
				if (current == value && check == false ) { check = true; } }
			if (check == false) { header(); } }
		// Assign your headings here to do the above for more than just the main sections
		heading(introduction,"introduction");
		heading(ux,"user-experience-design");
		heading(webdev,"web-development");
		heading(infra,"hosting-infrastructure-and-systems");
		heading(biz,"business-strategy-and-product-management");
		heading(considerations,"considerations");
		heading(glossary,"glossary");
		heading(credits,"acknowledgments");
		heading(changelog,"changelog");
		heading(refs,"references"); } else {
		for (const value of sections) {
			document.getElementById(value).classList.remove('show');
			document.getElementById(value).classList.add('hide'); }
		header(); }
		// Scrolls to the correct section of the page once its rendered it
		for (const value of all) {
			if (window.location.hash && window.location.hash !="#full-document" && value == current){
				document.getElementById(window.location.hash.substring(1)).scrollIntoView(); } } }
function heading(hash, string) {
	// This function examines headings for things needing to be hidden or made visible
	// It also ensures jump-to-location works as expected with content being shuffled
	let current = window.location.hash.substring(1);
	let sections = hashSection('body > section');
	if (hash.includes(current)) {
		for (const value of sections) {
			if (value == string) {
				document.getElementById(value).classList.remove('hide');
				document.getElementById(value).classList.add('show'); } else {
				document.getElementById(value).classList.remove('show');
				document.getElementById(value).classList.add('hide'); } } }
	location.hash = "#" + current; }
	// This ensures the abstract and sotd content exists if no fragment is visible
function header() {
	document.getElementById("abstract").classList.remove('hide');
	document.getElementById("sotd").classList.remove('hide');
	document.getElementById("abstract").classList.add('show');
	document.getElementById("sotd").classList.add('show');
	buttons("sotd"); window.scrollTo(0, 0);
	if (window.location.hash != "#full-document") {
		document.querySelectorAll('.pageButtons').forEach(e => e.classList.remove('hide'));
		document.querySelectorAll('.pageButtons').forEach(e => e.classList.add('show')); } }
function buttons(id) {
	// Adds the buttons where they are required
	var d = document.querySelector('#' + id + ' ol');
	d.parentNode.appendChild(d); }
</script>
```
**Note:** Code comments can be removed and section names should be configured to match your specification TOC.

The below must be included in the `respecConfig` section:

```javascript
var respecConfig = {
	lint: { "local-refs-exist": false, },
	postProcess: [addMultipage] }
```