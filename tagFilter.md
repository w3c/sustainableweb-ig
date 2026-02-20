# ReSpec Tag and Filter

- **Version:** 0.3.4
- **Creator:** Alexander Dawson

## Features

- It supports ReSpec generation mode, HTML Exports, PR Preview, and Echidna.
- Uses CSS and Vanilla JavaScript with no dependencies (lightweight).
- It works offline, progressively enhances, and is low maintenance.
- Works across desktop and handheld browsers (good compatibility).
- It supports query strings based on tag names (and `id` where duplication exists).

## HTML

The below attributes are **required** to be included within `<section>` elements:

**Note:**
- Attribute `name` and `value` must match JavaScript case sensitivty to function.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```html
<section class="notoc" data-materials="medium" data-energy="medium" data-water="medium" data-emissions="medium" data-standard="AFNOR" data-considerations="Accessibility" data-categories="Compatibility, Ideation, KPIs, Patterns, Reporting, Research, Social Equity, UI, Usability">
	<h4 id="identify-and-define">Success Criterion: Identify and define <span class="external"><a class="urls" href="https://w3c.github.io/sustainableweb-wsg/resources.html#UX02-1">Resources</a></span></h4>
	<p>Primary and secondary target visitors are identified, and their needs are defined through quantitative or qualitative research, testing, or analytics, ensuring your visitors and affected communities remain a close part of the research and testing process.</p>
</section>
```

## CSS

The below must be included within the `<head>` element:

**Note:**
- Show Filter Categories must be customized based on the HTML you have above.
- Show Filtered Content must be customized based on the HTML you have above.
   - It has a primary section to ensure the parent container is made visible.
   - It has a secondary section for the `class` that needs to be made visible.
   - It finally ensures our additional information `<details>` element is always visible.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```css
/* Role-based Labeling & Filter System: https://github.com/w3c/sustainableweb-wsg/issues/14 */
legend { font-weight: bold; width: fit-content; }
.switch form { display: flex; margin-bottom: 1.5em; margin-top: 1.5em; }
.switch label { box-sizing: border-box; border: medium solid var(--toclink-visited-text); display: flex; padding: 0.5em; justify-content: center; }
.switch label:has(input:checked) { background-color: #d9d9d9; color: #000000; font-weight: bold; }
.switch label:has(input:focus:checked) { outline: 4px solid var(--toclink-underline); }
.switch label:first-child { border-right: 0; border-top-left-radius: 15px; border-bottom-left-radius: 15px; min-width: 100px; }
.switch label:last-child { border-left: 0; border-top-right-radius: 15px; border-bottom-right-radius: 15px; min-width: 100px; }
.filter h2 { position: static !important; }
.filter input { margin-bottom: 0.75em; margin-top: 0.75em; }
.filter label { margin-right: 0.5em; white-space: nowrap; }
.standards label, .considerations label, .categories label { flex-basis: 50%; margin-right: 0; }
.filter fieldset { border: medium solid #d9d9d9; display: flex; flex-wrap: wrap; margin-bottom: 1em; }
.filter fieldset:has(:checked) ~ .c .reset { border-color: var(--toclink-visited-text); color: var(--toclink-text); }
.filter .c, .switch { max-width: fit-content; margin-left: auto; margin-right: auto; }
.filter .c .reset { background-color: var(--tocsidebar-bg); border: medium solid #d9d9d9; border-radius: 15px; color: #d9d9d9; font-size: 1em; font-weight: bold; margin-bottom: 2em; padding: 1.2em 3em; }
/* Hide All Non-SC Related Content Upon Filter Activation */
.hidden, .switch input, .switch:has(#contents:checked) ~ .filter, .switch:has(#filters:checked) ~ #table-of-contents, .switch:has(#filters:checked) ~ .toc, body:has(#filter :checked) #abstract, body:has(#filter :checked) #sotd, #toc:has(.filter :checked) ~ #introduction, #toc:has(.filter :checked) ~ #considerations, #toc:has(.filter :checked) ~ #acknowledgments, #toc:has(.filter :checked) ~ #changelog, #toc:has(.filter :checked) ~ section > p ~ section, #toc:has(.filter :checked) ~ section > p, #toc:has(.filter :checked) ~ section > ul, #toc:has(.filter :checked) ~ section > .summary, #toc:has(.filter :checked) ~ section > p ~ section > section
{ clip: rect(0,0,0,0) !important; content-visibility: hidden; height: 1px; overflow: hidden; position: absolute; width: 1px; }
/* Show Filtered Content */
#toc:has(.filter :checked) ~ section section:has(.mh), #toc:has(.filter :checked) ~ section section:has(.mm), #toc:has(.filter :checked) ~ section section:has(.ml),
#toc:has(.filter :checked) ~ section section:has(.eh), #toc:has(.filter :checked) ~ section section:has(.em), #toc:has(.filter :checked) ~ section section:has(.el),
#toc:has(.filter :checked) ~ section section:has(.wh), #toc:has(.filter :checked) ~ section section:has(.wm), #toc:has(.filter :checked) ~ section section:has(.wl),
#toc:has(.filter :checked) ~ section section:has(.ch), #toc:has(.filter :checked) ~ section section:has(.cm), #toc:has(.filter :checked) ~ section section:has(.cl),
#toc:has(.filter :checked) ~ section section:has(.afnor), #toc:has(.filter :checked) ~ section section:has(.aws), #toc:has(.filter :checked) ~ section section:has(.azure), #toc:has(.filter :checked) ~ section section:has(.gpf), #toc:has(.filter :checked) ~ section section:has(.gr491), #toc:has(.filter :checked) ~ section section:has(.greenit), #toc:has(.filter :checked) ~ section section:has(.opquast), #toc:has(.filter :checked) ~ section section:has(.sdgs), #toc:has(.filter :checked) ~ section section:has(.ca), #toc:has(.filter :checked) ~ section section:has(.cp), #toc:has(.filter :checked) ~ section section:has(.cs), #toc:has(.filter :checked) ~ section section:has(.ai), #toc:has(.filter :checked) ~ section section:has(.assets), #toc:has(.filter :checked) ~ section section:has(.compatibility), #toc:has(.filter :checked) ~ section section:has(.content), #toc:has(.filter :checked) ~ section section:has(.css), #toc:has(.filter :checked) ~ section section:has(.e-waste), #toc:has(.filter :checked) ~ section section:has(.education), #toc:has(.filter :checked) ~ section section:has(.governance), #toc:has(.filter :checked) ~ section section:has(.hardware), #toc:has(.filter :checked) ~ section section:has(.html), #toc:has(.filter :checked) ~ section section:has(.ideation), #toc:has(.filter :checked) ~ section section:has(.javascript), #toc:has(.filter :checked) ~ section section:has(.kpis), #toc:has(.filter :checked) ~ section section:has(.marketing), #toc:has(.filter :checked) ~ section section:has(.networking), #toc:has(.filter :checked) ~ section section:has(.patterns), #toc:has(.filter :checked) ~ section section:has(.performance), #toc:has(.filter :checked) ~ section section:has(.report), #toc:has(.filter :checked) ~ section section:has(.research), #toc:has(.filter :checked) ~ section section:has(.equity), #toc:has(.filter :checked) ~ section section:has(.software), #toc:has(.filter :checked) ~ section section:has(.strategy), #toc:has(.filter :checked) ~ section section:has(.ui), #toc:has(.filter :checked) ~ section section:has(.usability),
.mh, .mm, .ml, .eh, .em, .el, .wh, .wm, .wl, .ch, .cm, .cl, .afnor, .aws, .azure, .gpf, .gr491, .greenit, .opquast, .sdgs, .ca, .cp, .cs, .ai, .assets, .compatibility, .content, .css, .e-waste, .education, .governance, .hardware, .html, .ideation, .javascript, .kpis, .marketing, .networking, .patterns, .performance, .report, .research, .equity, .software, .strategy, .ui, .usability,
.mh ~ section:last-child, .mm ~ section:last-child, .ml ~ section:last-child, .eh ~ section:last-child, .em ~ section:last-child, .el ~ section:last-child, .wh ~ section:last-child, .wm ~ section:last-child, .wl ~ section:last-child, .ch ~ section:last-child, .cm ~ section:last-child, .cl ~ section:last-child , .afnor ~ section:last-child, .aws ~ section:last-child, .azure ~ section:last-child, .gpf ~ section:last-child, .gr491 ~ section:last-child, .greenit ~ section:last-child, .opquast ~ section:last-child, .sdgs ~ section:last-child, .ca ~ section:last-child, .cp ~ section:last-child, .cs ~ section:last-child, .ai ~ section:last-child, .assets ~ section:last-child, .compatibility ~ section:last-child, .content ~ section:last-child, .css ~ section:last-child, .e-waste ~ section:last-child, .education ~ section:last-child, .governance ~ section:last-child, .hardware ~ section:last-child, .html ~ section:last-child, .ideation ~ section:last-child, .javascript ~ section:last-child, .kpis ~ section:last-child, .marketing ~ section:last-child, .networking ~ section:last-child, .patterns ~ section:last-child, .performance ~ section:last-child, .report ~ section:last-child, .research ~ section:last-child, .equity ~ section:last-child, .software ~ section:last-child, .strategy ~ section:last-child, .ui ~ section:last-child, .usability ~ section:last-child
{ clip: auto; content-visibility: visible !important; height: auto !important; overflow: unset !important; position: static !important; width: auto !important; }
@media print { .switch { display: none; } }
@media (scripting: none) { .switch, .filter { display: none; } }
```

## JavaScript

The below must be included within the `<head>` element:

**Note:**
- `option-inline` categories must match CSS "Show Filter Categories".
- `id` must match assigned CSS class names and JavaScript case sensitivity to function.
- Attribute `value` must match JavaScript case sensitivty to function.
- `filterNote` must match assigned CSS class names and HTML attributes to function.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```javascript
<script>
	window.addEventListener("click", (event) => { addFilter(); updateQueryString(); });
	window.addEventListener("load", function() { queryFilter(); });
	function addFilter() {
		window.addEventListener('change', filterData); filterData(); }
	function htmlInsert() {
		let toc = document.querySelector('#toc');
		let newItems = `
		<section id="switch" class="switch">
			<form>
				<label for="contents"><input type="radio" id="contents" name="switcher" checked>Contents</label>
				<label for="filters"><input type="radio" id="filters" name="switcher">Filters</label>
			</form>
		</section>`;
		toc.insertAdjacentHTML('afterbegin', newItems);
		let newItems2 = `
		<section id="filter" class="filter">
			<h2 class="introductory">Content Filters</h2>
			<form>
				<fieldset class="materials">
					<legend><a href="#reporting">Materials</a></legend>
					<label for="mh"><input type="checkbox" id="mh" name="materials">High</label>
					<label for="mm"><input type="checkbox" id="mm" name="materials">Medium</label>
					<label for="ml"><input type="checkbox" id="ml" name="materials">Low</label>
				</fieldset>
				<fieldset class="energy">
					<legend><a href="#reporting">Energy</a></legend>
					<label for="eh"><input type="checkbox" id="eh" name="energy">High</label>
					<label for="em"><input type="checkbox" id="em" name="energy">Medium</label>
					<label for="el"><input type="checkbox" id="el" name="energy">Low</label>
				</fieldset>
				<fieldset class="water">
					<legend><a href="#reporting">Water</a></legend>
					<label for="wh"><input type="checkbox" id="wh" name="water">High</label>
					<label for="wm"><input type="checkbox" id="wm" name="water">Medium</label>
					<label for="wl"><input type="checkbox" id="wl" name="water">Low</label>
				</fieldset>
				<fieldset class="emissions">
					<legend><a href="#reporting">Emissions</a></legend>
					<label for="ch"><input type="checkbox" id="ch" name="emissions">High</label>
					<label for="cm"><input type="checkbox" id="cm" name="emissions">Medium</label>
					<label for="cl"><input type="checkbox" id="cl" name="emissions">Low</label>
				</fieldset>
				<fieldset class="standards">
					<legend><a href="#relationships">Standards</a></legend>
					<label for="afnor"><input type="checkbox" id="afnor" name="standard">AFNOR</label>
					<label for="aws"><input type="checkbox" id="aws" name="standard"><abbr title="Amazon Web Services">AWS</abbr> <abbr title="Well-Architected Framework">WAF</abbr></label>
					<label for="azure"><input type="checkbox" id="azure" name="standard"><abbr title="Microsoft Azure">Azure</abbr> WAF</label>
					<label for="gpf"><input type="checkbox" id="gpf" name="standard"><abbr title="General Policy Framework for the Ecodesign of Digital Services">GPF</abbr></label>
					<label for="gr491"><input type="checkbox" id="gr491" name="standard">GR491</label>
					<label for="greenit"><input type="checkbox" id="greenit" name="standard">GreenIT</label>
					<label for="opquast"><input type="checkbox" id="opquast" name="standard">OpQuast</label>
					<label for="sdgs"><input type="checkbox" id="sdgs" name="standard"><abbr title="United Nations">UN</abbr> SDGs</label>
				</fieldset>
				<fieldset class="considerations">
					<legend><a href="#considerations">Considerations</a></legend>
					<label for="ca"><input type="checkbox" id="ca" name="considerations">Accessibility</label>
					<label for="cp"><input type="checkbox" id="cp" name="considerations">Privacy</label>
					<label for="cs"><input type="checkbox" id="cs" name="considerations">Security</label>
				</fieldset>
				<fieldset class="categories">
					<legend>Categories</legend>
					<label for="ai"><input type="checkbox" id="ai" name="category">AI</label>
					<label for="assets"><input type="checkbox" id="assets" name="category">Assets</label>
					<label for="compatibility"><input type="checkbox" id="compatibility" name="category">Compatibility</label>
					<label for="content"><input type="checkbox" id="content" name="category">Content</label>
					<label for="css"><input type="checkbox" id="css" name="category">CSS</label>
					<label for="e-waste"><input type="checkbox" id="e-waste" name="category">E-Waste</label>
					<label for="education"><input type="checkbox" id="education" name="category">Education</label>
					<label for="governance"><input type="checkbox" id="governance" name="category">Governance</label>
					<label for="hardware"><input type="checkbox" id="hardware" name="category">Hardware</label>
					<label for="html"><input type="checkbox" id="html" name="category">HTML</label>
					<label for="ideation"><input type="checkbox" id="ideation" name="category">Ideation</label>
					<label for="javascript"><input type="checkbox" id="javascript" name="category">JavaScript</label>
					<label for="kpis"><input type="checkbox" id="kpis" name="category">KPIs</label>
					<label for="marketing"><input type="checkbox" id="marketing" name="category">Marketing</label>
					<label for="networking"><input type="checkbox" id="networking" name="category">Networking</label>
					<label for="patterns"><input type="checkbox" id="patterns" name="category">Patterns</label>
					<label for="performance"><input type="checkbox" id="performance" name="category">Performance</label>
					<label for="report"><input type="checkbox" id="report" name="category">Reporting</label>
					<label for="research"><input type="checkbox" id="research" name="category">Research</label>
					<label for="equity"><input type="checkbox" id="equity" name="category">Social Equity</label>
					<label for="software"><input type="checkbox" id="software" name="category">Software</label>
					<label for="strategy"><input type="checkbox" id="strategy" name="category">Strategy</label>
					<label for="ui"><input type="checkbox" id="ui" name="category">UI</label>
					<label for="usability"><input type="checkbox" id="usability" name="category">Usability</label>
				</fieldset>
				<div class="c">
					<input class="reset" type="reset" value="Reset the filters">
				</div>
			</form>
		</section>`;
		toc.insertAdjacentHTML('beforeend', newItems2); }
	function autoScroll() {
		document.addEventListener('click', event => {
		if (event.target.matches('.filter input')) {
			document.getElementById('user-experience-design').scrollIntoView({ behavior: 'smooth', block: 'start' });
			const inputs = document.querySelectorAll('.filter input');
			const noneChecked = ![...inputs].some(input => input.checked);
			if (noneChecked) { window.scrollTo({ top: 0, behavior: 'smooth' }); } } }); }
	function filterData() {
		filterNote('mh', '[data-materials="high"]');
		filterNote('mm', '[data-materials="medium"]');
		filterNote('ml', '[data-materials="low"]');
		filterNote('eh', '[data-energy="high"]');
		filterNote('em', '[data-energy="medium"]');
		filterNote('el', '[data-energy="low"]');
		filterNote('wh', '[data-water="high"]');
		filterNote('wm', '[data-water="medium"]');
		filterNote('wl', '[data-water="low"]');
		filterNote('ch', '[data-emissions="high"]');
		filterNote('cm', '[data-emissions="medium"]');
		filterNote('cl', '[data-emissions="low"]');
		filterNote('afnor', '[data-standard*="AFNOR"]');
		filterNote('aws', '[data-standard*="AWS WAF"]');
		filterNote('azure', '[data-standard*="Azure WAF"]');
		filterNote('gpf', '[data-standard*="GPF"]');
		filterNote('gr491', '[data-standard*="GR491"]');
		filterNote('greenit', '[data-standard*="GreenIT"]');
		filterNote('opquast', '[data-standard*="OpQuast"]');
		filterNote('sdgs', '[data-standard*="SDGs"]');
		filterNote('ca', '[data-considerations*="Accessibility"]');
		filterNote('cp', '[data-considerations*="Privacy"]');
		filterNote('cs', '[data-considerations*="Security"]');
		filterNote('ai', '[data-categories*="AI"]');
		filterNote('assets', '[data-categories*="Assets"]');
		filterNote('compatibility', '[data-categories*="Compatibility"]');
		filterNote('content', '[data-categories*="Content"]');
		filterNote('css', '[data-categories*="CSS"]');
		filterNote('e-waste', '[data-categories*="E-Waste"]');
		filterNote('education', '[data-categories*="Education"]');
		filterNote('governance', '[data-categories*="Governance"]');
		filterNote('hardware', '[data-categories*="Hardware"]');
		filterNote('html', '[data-categories*="HTML"]');
		filterNote('ideation', '[data-categories*="Ideation"]');
		filterNote('javascript', '[data-categories*="JavaScript"]');
		filterNote('kpis', '[data-categories*="KPIs"]');
		filterNote('marketing', '[data-categories*="Marketing"]');
		filterNote('networking', '[data-categories*="Networking"]');
		filterNote('patterns', '[data-categories*="Patterns"]');
		filterNote('performance', '[data-categories*="Performance"]');
		filterNote('report', '[data-categories*="Reporting"]');
		filterNote('research', '[data-categories*="Research"]');
		filterNote('equity', '[data-categories*="Social Equity"]');
		filterNote('software', '[data-categories*="Software"]');
		filterNote('strategy', '[data-categories*="Strategy"]');
		filterNote('ui', '[data-categories*="UI"]');
		filterNote('usability', '[data-categories*="Usability"]');

		// Updates TOC based on filters
		const toc = document.querySelector('#toc > .toc');
		if (toc) { toc.querySelectorAll('a').forEach(link => {
			link.parentElement.classList.remove('hidden');
			link.classList.remove('hidden'); }); }
		document.querySelectorAll('body > section > section').forEach(section => {
		let style = window.getComputedStyle(section);
		if (style.position === 'absolute') {
			const toc = document.querySelector('#toc > .toc');
			if (toc) {
			toc.querySelectorAll('a').forEach(link => {
				const str = link.href;
				const result = str.split('#')[1];
				if (section.id === result || result === "abstract" || result === "sotd" || result === "considerations" || result === "acknowledgments" || result === "changelog") {
					link.classList.add('hidden'); } else if (
				result === "introduction") {
					link.parentElement.classList.add('hidden'); } }); } } });
		document.querySelectorAll('a').forEach(a => {
			if (a.classList.contains('hidden')) {
				a.setAttribute('tabindex', '-1'); } else { a.removeAttribute('tabindex');
			} }); }
	function filterNote(name, attr) {
		let countTotal = " (" + document.querySelectorAll(attr).length + ")";
		if (document.getElementById(name).parentElement.innerHTML.includes(countTotal)) { } else {
			document.getElementById(name).parentElement.innerHTML += countTotal; }
		if (document.getElementById(name).checked == true) {
			document.querySelectorAll(attr).forEach(function (elem) {
				elem.classList.add(name); }); } else {
			document.querySelectorAll(attr).forEach(function (elem) {
				elem.classList.remove(name); }); }
		return(name + attr); }
	function getQueryValue(input) {
		let labelText = input.parentElement.textContent.trim().toLowerCase().toLowerCase().replace(/\s+/g, '-').replace(/\(.*?\)/g, '').replace(/-$/, '');
		if (["high", "medium", "low"].includes(labelText)) {
			return `${input.id}-${labelText}`;
		} else { return `${labelText}`; } }
	function updateQueryString() {
		autoScroll();
		const params = new URLSearchParams(window.location.search);
		params.delete('filter');
		document.querySelectorAll('.filter input:checked').forEach(input => params.append('filter', getQueryValue(input)));
		const query = params.toString();
		const hash = window.location.hash;
		let newUrl = window.location.pathname;
		if (window.location.search || query) { newUrl += '?' + query; }
		history.replaceState(null, '', newUrl += hash); }
	function queryFilter() {
		// Query String Filtering onLoad
		const filters = document.querySelectorAll('.filter');
		if (!filters.length) return;
		document.querySelectorAll('.filter input').forEach(input => {
			input.addEventListener('change', updateQueryString); });
		document.querySelectorAll('form').forEach(form => {
			form.addEventListener('reset', () => setTimeout(updateQueryString, 0)); });
		const queryParams = window.location.search.substring(1).toLowerCase().split('&').filter(Boolean);
		document.querySelectorAll('.filter label').forEach(label => {
			const input = label.querySelector('input');
			if (!input || !input.id) return;
			const rawText = Array.from(label.childNodes).filter(node => node.nodeType === Node.TEXT_NODE).map(node => node.textContent).join(' ').trim().toLowerCase();
			let text = rawText.replace(/\s+/g, '-').replace(/\(.*?\)/g, '').replace(/-$/, '');
			let result = ["high", "medium", "low"].includes(text)
				? `${input.id}-${text}`
				: text;
			result = `filter=${result}`;
			input.checked = queryParams.includes(result); });
		if (typeof filterData === 'function') { filterData(); } }
</script>
```

The below must be included in the `respecConfig` section:

```javascript
var respecConfig = {
	postProcess: [htmlInsert, addFilter, queryFilter] }
```