# ReSpec Tag and Filter

- **Version:** 0.1.4
- **Creator:** Alexander Dawson

## Features

- It supports ReSpec generation mode, HTML Exports, and PR Preview.
- Uses CSS and Vanilla JavaScript with no dependencies (lightweight).
- It works offline, progressively enhances, and is low maintenance.
- Compatible with the [ReSpec multiPage plugin](multipage.md) (available in this repo).
- Works across desktop and handheld browsers (good compatibility).

## HTML

The below is **required** to be included directly below the `<body>` tags:

**Note:**
- `option-inline` categories must match CSS "Show Filter Categories".
- `id` must match assigned CSS class names and JavaScript case sensitivity to function.
- Attribute `value` must match JavaScript case sensitivty to function.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```html
<div class="filter summary"> <!-- Filter Tool -->
	<details>
		<summary>Filter the available WSG Success Criteria upon certain settings</summary>
		<form>
			<div class="option-inline">
				<label for="test"><input type="radio" id="test" name="option" value="Testable" checked>Testable</label>
				<label for="rating"><input type="radio" id="rating" name="option" value="Ratings">Ratings</label>
				<label for="planet"><input type="radio" id="planet" name="option" value="Planetary">Planetary</label>
				<label for="standards"><input type="radio" id="standards" name="option" value="Standards">Standards</label>
				<label for="consideration"><input type="radio" id="consideration" name="option" value="considerations">Considerations</label>
				<label for="categories"><input type="radio" id="categories" name="option" value="categories">Categories</label>
			</div>
			<div class="wrapper">
				<fieldset class="testable">
					<legend><a href="#success-criteria">Testable</a></legend>
					<label for="mt"><input type="checkbox" id="mt" name="test" value="Machine-testable">Machine-testable</label>
					<label for="ht"><input type="checkbox" id="ht" name="test" value="Human-testable">Human-testable</label>
				</fieldset>
				<fieldset class="impact">
					<legend><a href="#impact">Impact</a></legend>
					<label for="ih"><input type="checkbox" id="ih" name="impact" value="High">High</label>
					<label for="im"><input type="checkbox" id="im" name="impact" value="Medium">Medium</label>
					<label for="il"><input type="checkbox" id="il" name="impact" value="Low">Low</label>
				</fieldset>
				<fieldset class="effort">
					<legend><a href="#effort">Effort</a></legend>
					<label for="ih2"><input type="checkbox" id="ih2" name="effort" value="High">High</label>
					<label for="im2"><input type="checkbox" id="im2" name="effort" value="Medium">Medium</label>
					<label for="il2"><input type="checkbox" id="il2" name="effort" value="Low">Low</label>
				</fieldset>
				<fieldset class="materials">
					<legend><a href="#reporting">Materials</a></legend>
					<label for="mh"><input type="checkbox" id="mh" name="materials" value="High">High</label>
					<label for="mm"><input type="checkbox" id="mm" name="materials" value="Medium">Medium</label>
					<label for="ml"><input type="checkbox" id="ml" name="materials" value="Low">Low</label>
				</fieldset>
				<fieldset class="energy">
					<legend><a href="#reporting">Energy</a></legend>
					<label for="eh"><input type="checkbox" id="eh" name="energy" value="High">High</label>
					<label for="em"><input type="checkbox" id="em" name="energy" value="Medium">Medium</label>
					<label for="el"><input type="checkbox" id="el" name="energy" value="Low">Low</label>
				</fieldset>
				<fieldset class="water">
					<legend><a href="#reporting">Water</a></legend>
					<label for="wh"><input type="checkbox" id="wh" name="water" value="High">High</label>
					<label for="wm"><input type="checkbox" id="wm" name="water" value="Medium">Medium</label>
					<label for="wl"><input type="checkbox" id="wl" name="water" value="Low">Low</label>
				</fieldset>
				<fieldset class="emissions">
					<legend><a href="#reporting">Emissions</a></legend>
					<label for="ch"><input type="checkbox" id="ch" name="emissions" value="High">High</label>
					<label for="cm"><input type="checkbox" id="cm" name="emissions" value="Medium">Medium</label>
					<label for="cl"><input type="checkbox" id="cl" name="emissions" value="Low">Low</label>
				</fieldset>
				<fieldset class="standards">
					<legend><a href="#relationships">Standards</a></legend>
					<label for="afnor"><input type="checkbox" id="afnor" name="standard" value="Human-testable">AFNOR</label>
					<label for="aws"><input type="checkbox" id="aws" name="standard" value="Human-testable"><abbr title="Amazon Web Services">AWS</abbr> <abbr title="Well-Architected Framework">WAF</abbr></label>
					<label for="azure"><input type="checkbox" id="azure" name="standard" value="Human-testable"><abbr title="Microsoft Azure">Azure</abbr> WAF</label>
					<label for="gpf"><input type="checkbox" id="gpf" name="standard" value="Human-testable"><abbr title="General Policy Framework for the Ecodesign of Digital Services">GPF</abbr></label>
					<label for="gr491"><input type="checkbox" id="gr491" name="standard" value="Human-testable">GR491</label>
					<label for="greenit"><input type="checkbox" id="greenit" name="standard" value="Human-testable">GreenIT</label>
					<label for="opquast"><input type="checkbox" id="opquast" name="standard" value="Human-testable">OpQuast</label>
					<label for="sdgs"><input type="checkbox" id="sdgs" name="standard" value="Human-testable"><abbr title="United Nations">UN</abbr> SDGs</label>
				</fieldset>
				<fieldset class="considerations">
					<legend><a href="#considerations">Considerations</a></legend>
					<label for="ca"><input type="checkbox" id="ca" name="considerations" value="High">Accessibility</label>
					<label for="cp"><input type="checkbox" id="cp" name="considerations" value="Medium">Privacy</label>
					<label for="cs"><input type="checkbox" id="cs" name="considerations" value="Low">Security</label>
				</fieldset>
				<fieldset class="categories">
					<legend>Categories</legend>
					<label for="assets"><input type="checkbox" id="assets" name="category" value="High">Assets</label>
					<label for="compatibility"><input type="checkbox" id="compatibility" name="category" value="High">Compatibility</label>
					<label for="content"><input type="checkbox" id="content" name="category" value="High">Content</label>
					<label for="css"><input type="checkbox" id="css" name="category" value="High">CSS</label>
					<label for="e-waste"><input type="checkbox" id="e-waste" name="category" value="High">E-Waste</label>
					<label for="education"><input type="checkbox" id="education" name="category" value="High">Education</label>
					<label for="governance"><input type="checkbox" id="governance" name="category" value="High">Governance</label>
					<label for="hardware"><input type="checkbox" id="hardware" name="category" value="High">Hardware</label>
					<label for="html"><input type="checkbox" id="html" name="category" value="High">HTML</label>
					<label for="ideation"><input type="checkbox" id="ideation" name="category" value="High">Ideation</label>
					<label for="javascript"><input type="checkbox" id="javascript" name="category" value="High">JavaScript</label>
					<label for="kpis"><input type="checkbox" id="kpis" name="category" value="High">KPIs</label>
					<label for="marketing"><input type="checkbox" id="marketing" name="category" value="High">Marketing</label>
					<label for="networking"><input type="checkbox" id="networking" name="category" value="High">Networking</label>
					<label for="patterns"><input type="checkbox" id="patterns" name="category" value="High">Patterns</label>
					<label for="performance"><input type="checkbox" id="performance" name="category" value="High">Performance</label>
					<label for="report"><input type="checkbox" id="report" name="category" value="High">Reporting</label>
					<label for="research"><input type="checkbox" id="research" name="category" value="High">Research</label>
					<label for="equity"><input type="checkbox" id="equity" name="category" value="High">Social Equity</label>
					<label for="software"><input type="checkbox" id="software" name="category" value="High">Software</label>
					<label for="strategy"><input type="checkbox" id="strategy" name="category" value="High">Strategy</label>
					<label for="ui"><input type="checkbox" id="ui" name="category" value="High">UI</label>
					<label for="usability"><input type="checkbox" id="usability" name="category" value="High">Usability</label>
				</fieldset>
			</div>
		</form>
	</details>
</div>
```

The below HTML attributes **required** to be included directly within your Success Criteria:

**Note:**
- Attribute `name` and `value` must match JavaScript case sensitivty to function.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```html
<section class="notoc" data-testable="machine" data-impact="medium" data-effort="high" data-materials="medium" data-energy="medium" data-water="medium" data-emissions="medium" data-standard="AFNOR" data-considerations="Accessibility" data-categories="Compatibility, Ideation, KPIs, Patterns, Reporting, Research, Social Equity, UI, Usability">
	<h4 id="identify-and-define">Success Criterion: Identify and define <span class="external"><a class ="machine" href="https://w3c.github.io/sustainableweb-wsg/star.html#UX02-1">Machine-testable</a> <span class="hide">/</span> <a class="urls" href="https://w3c.github.io/sustainableweb-wsg/resources.html#UX02-1">Resources</a></span></h4>
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
.filter details { scroll-margin-top: 25px; }
.filter details form { content-visibility: hidden; } .filter details[open] form { content-visibility: visible; }
legend { font-weight: bold; width: fit-content; }
.wrapper { display: flex; flex-wrap: wrap; }
.testable, .impact, .effort, .materials, .energy, .water, .emissions { min-width: 300px; }
.categories, .considerations, .standards, .testable { flex-basis: 100%; }
.impact, .effort, .materials, .energy, .water, .emissions { flex-basis: calc(50% - 32px); }
.wrapper > fieldset, .option-inline { margin-top: 1em; }
.wrapper label { margin-right: 0.5em; white-space: nowrap; }
@media screen and (max-width: 860px) {
	.wrapper fieldset, .option-inline { display: flex; flex-basis: 100%; flex-wrap: wrap; } }
@media screen and (max-width: 700px) {
	.option-inline { display: flex; flex-direction: column; min-width: unset; }
	.wrapper label { margin-right: 0; } }
@media screen and (max-width: 550px) {
	.wrapper fieldset { display: flex; flex-direction: column; min-width: unset; } }
.filter, .option-inline div:has(#test:checked),
/* Hide All Non-SC Related Content Upon Filter Activation */
.filter:has(details[open]) ~ #abstract, .filter:has(details[open]) ~ #sotd, .filter:has(details[open]) ~ #introduction, .filter:has(details[open]) ~ section > p ~ section, .filter:has(details[open]) ~ section > p ~ section > section, .filter:has(details[open]) ~ #acknowledgments, .filter:has(details[open]) ~ section > div, .filter:has(details[open]) ~ section > p, .filter:has(details[open]) ~ section ul, .wrapper fieldset
{ content-visibility: hidden; height: 1px; left: -1000px; overflow: hidden; position: absolute; top: -1px; width: 1px; }
/* Show Filter Basics */
.full-document .filter, .filter:has(details[open]) ~ #glossary > div, .filter:has(details[open]) ~ #glossary > p,
/* Show Filter Categories */
.option-inline:has(#test:checked) ~ .wrapper .testable, .option-inline:has(#rating:checked) ~ .wrapper .impact, .option-inline:has(#rating:checked) ~ .wrapper .effort, .option-inline:has(#planet:checked) ~ .wrapper .materials, .option-inline:has(#planet:checked) ~ .wrapper .energy, .option-inline:has(#planet:checked) ~ .wrapper .water, .option-inline:has(#planet:checked) ~ .wrapper .emissions, .option-inline:has(#standards:checked) ~ .wrapper .standards, .option-inline:has(#consideration:checked) ~ .wrapper .considerations, .option-inline:has(#categories:checked) ~ .wrapper .categories,
/* Show Filtered Content */
.filter:has(details[open]) ~ section section:has(.mt), .filter:has(details[open]) ~ section section:has(.ht),
.filter:has(details[open]) ~ section section:has(.ih), .filter:has(details[open]) ~ section section:has(.im), .filter:has(details[open]) ~ section section:has(.il),
.filter:has(details[open]) ~ section section:has(.ih2), .filter:has(details[open]) ~ section section:has(.im2), .filter:has(details[open]) ~ section section:has(.il2),
.filter:has(details[open]) ~ section section:has(.mh), .filter:has(details[open]) ~ section section:has(.mm), .filter:has(details[open]) ~ section section:has(.ml),
.filter:has(details[open]) ~ section section:has(.eh), .filter:has(details[open]) ~ section section:has(.em), .filter:has(details[open]) ~ section section:has(.el),
.filter:has(details[open]) ~ section section:has(.wh), .filter:has(details[open]) ~ section section:has(.wm), .filter:has(details[open]) ~ section section:has(.wl),
.filter:has(details[open]) ~ section section:has(.ch), .filter:has(details[open]) ~ section section:has(.cm), .filter:has(details[open]) ~ section section:has(.cl),
.filter:has(details[open]) ~ section section:has(.afnor), .filter:has(details[open]) ~ section section:has(.aws), .filter:has(details[open]) ~ section section:has(.azure), .filter:has(details[open]) ~ section section:has(.gpf), .filter:has(details[open]) ~ section section:has(.gr491), .filter:has(details[open]) ~ section section:has(.greenit), .filter:has(details[open]) ~ section section:has(.opquast), .filter:has(details[open]) ~ section section:has(.sdgs), .filter:has(details[open]) ~ section section:has(.ca), .filter:has(details[open]) ~ section section:has(.cp), .filter:has(details[open]) ~ section section:has(.cs), .filter:has(details[open]) ~ section section:has(.assets), .filter:has(details[open]) ~ section section:has(.compatibility), .filter:has(details[open]) ~ section section:has(.content), .filter:has(details[open]) ~ section section:has(.css), .filter:has(details[open]) ~ section section:has(.e-waste), .filter:has(details[open]) ~ section section:has(.education), .filter:has(details[open]) ~ section section:has(.governance), .filter:has(details[open]) ~ section section:has(.hardware), .filter:has(details[open]) ~ section section:has(.html), .filter:has(details[open]) ~ section section:has(.ideation), .filter:has(details[open]) ~ section section:has(.javascript), .filter:has(details[open]) ~ section section:has(.kpis), .filter:has(details[open]) ~ section section:has(.marketing), .filter:has(details[open]) ~ section section:has(.networking), .filter:has(details[open]) ~ section section:has(.patterns), .filter:has(details[open]) ~ section section:has(.performance), .filter:has(details[open]) ~ section section:has(.report), .filter:has(details[open]) ~ section section:has(.research), .filter:has(details[open]) ~ section section:has(.equity), .filter:has(details[open]) ~ section section:has(.software), .filter:has(details[open]) ~ section section:has(.strategy), .filter:has(details[open]) ~ section section:has(.ui), .filter:has(details[open]) ~ section section:has(.usability),
.summary ul, .mt, .ht, .ih, .im, .il, .ih2, .im2, .il2, .mh, .mm, .ml, .eh, .em, .el, .wh, .wm, .wl, .ch, .cm, .cl, .afnor, .aws, .azure, .gpf, .gr491, .greenit, .opquast, .sdgs, .ca, .cp, .cs, .assets, .compatibility, .content, .css, .e-waste, .education, .governance, .hardware, .html, .ideation, .javascript, .kpis, .marketing, .networking, .patterns, .performance, .report, .research, .equity, .software, .strategy, .ui, .usability,
.mt ~ section:last-child, .ht ~ section:last-child, .ih ~ section:last-child, .im ~ section:last-child, .il ~ section:last-child, .ih2 ~ section:last-child, .im2 ~ section:last-child, .il2 ~ section:last-child, .mh ~ section:last-child, .mm ~ section:last-child, .ml ~ section:last-child, .eh ~ section:last-child, .em ~ section:last-child, .el ~ section:last-child, .wh ~ section:last-child, .wm ~ section:last-child, .wl ~ section:last-child, .ch ~ section:last-child, .cm ~ section:last-child, .cl ~ section:last-child , .afnor ~ section:last-child, .aws ~ section:last-child, .azure ~ section:last-child, .gpf ~ section:last-child, .gr491 ~ section:last-child, .greenit ~ section:last-child, .opquast ~ section:last-child, .sdgs ~ section:last-child, .ca ~ section:last-child, .cp ~ section:last-child, .cs ~ section:last-child, .assets ~ section:last-child, .compatibility ~ section:last-child, .content ~ section:last-child, .css ~ section:last-child, .e-waste ~ section:last-child, .education ~ section:last-child, .governance ~ section:last-child, .hardware ~ section:last-child, .html ~ section:last-child, .ideation ~ section:last-child, .javascript ~ section:last-child, .kpis ~ section:last-child, .marketing ~ section:last-child, .networking ~ section:last-child, .patterns ~ section:last-child, .performance ~ section:last-child, .report ~ section:last-child, .research ~ section:last-child, .equity ~ section:last-child, .software ~ section:last-child, .strategy ~ section:last-child, .ui ~ section:last-child, .usability ~ section:last-child
{ content-visibility: visible !important; height: auto !important; left: auto !important; overflow: unset !important; position: static !important; top: auto !important; width: auto !important; }
@media (scripting: none) { .filter { display: none; } }
```

## JavaScript

The below must be included within the `<head>` element:

**Note:**
- `filterNote` must match assigned CSS class names and HTML attributes to function.
- The below are what W3C WSG utilizes, feel free to customize as appropriate.

```javascript
<script>
function addFilter() {
	window.addEventListener('change', filterData);
	window.addEventListener('hashchange', filterStyles); filterData();
	let details = document.querySelectorAll('.filter details')[0];
	details.addEventListener("toggle", function() {
		if (details.hasAttribute('open')) { details.scrollIntoView(); } }) }
window.addEventListener("load", (event) => {
	addFilter(); });
function filterData() {
	filterNote('mt', '[data-testable="machine"]');
	filterNote('ht', '[data-testable="human"]');
	filterNote('ih', '[data-impact="high"]');
	filterNote('im', '[data-impact="medium"]');
	filterNote('il', '[data-impact="low"]');
	filterNote('ih2', '[data-effort="high"]');
	filterNote('im2', '[data-effort="medium"]');
	filterNote('il2', '[data-effort="low"]');
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
	filterNote('usability', '[data-categories*="Usability"]');}
function filterStyles() {
	if (window.location.hash != "#full-document") {
		document.querySelectorAll('.summary')[0].setAttribute('inert','');
		document.querySelectorAll('.filter details').forEach(e => e.removeAttribute('open')); } else {
			document.querySelectorAll('.summary')[0].removeAttribute('inert'); } }
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
</script>
```

The below must be included in the `respecConfig` section:

```javascript
var respecConfig = {
	postProcess: [addFilter] }
```