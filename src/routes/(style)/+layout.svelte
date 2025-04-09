<script>
	import '../../app.postcss';
	import {base} from '$app/paths';
	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';

	hljs.registerLanguage('xml', xml); // for HTML
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>

<nav class="navbar">
	<a href="{base}/">Home</a>
	<a href="{base}/Items">Items</a>
	<a href="{base}/Building">Building</a>
	<a href="{base}/Guides">Guides</a>
	<a href="{base}/devblog">Devblog</a>

</nav>
<input class="search" type="text" placeholder="Search">
<main>
	
</main>


<slot />
<style>
main{
	display: flex;
	flex-direction: row;
	width: 100vw;
	height: 100vh;
	background-color: #0f0e14;
}
.navbar{
	display:grid;
	position: fixed;
	top: 0;	
	justify-content: space-around;
	grid-template-columns: 1fr 4fr,4fr,4fr;
	grid-row: 1fr;
	grid-auto-flow: column;
	background-color: #1f1c2b;
	color: rgb(135, 58, 0);
	padding: 10px;
	width: 50%;
	border-bottom: #717171 2px solid;
	border-right: #717171 2px solid;
	border-bottom-right-radius: 10px;
	
}
.search{
	position: fixed;
	top: 0;
	right: 0;
	width: 25%;
	padding: 10px;
	border: none;
	background-color: #1f1c2b;
	color : rgb(135, 58, 0);
	border-bottom: #717171 2px solid;
	border-left: #717171 2px solid;
	border-bottom-left-radius: 10px;
}

</style>

