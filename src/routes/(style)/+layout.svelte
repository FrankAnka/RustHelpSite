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


<div class="navbar bg-base-100 shadow-sm">
	<div class="flex-1">

	<a class="btn btn-ghost text-xl" href="{base}/">Home</a>
	<a class="btn btn-ghost text-xl" href="{base}/Items">Items</a>
	<a class="btn btn-ghost text-xl" href="{base}/Guides">Monuments</a>
	</div>
	
</div>


<main>
	
</main>


<slot />
<style>
main{
	display: flex;
	flex-direction: row;
	width: 100vw;
	height: 180vh;
	background-color: #0f0e14;

}



</style>

