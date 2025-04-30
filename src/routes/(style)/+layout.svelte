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
	  <a class="btn btn-ghost text-xl">daisyUI</a>
	</div>
	<div class="flex-none">
	  <button class="btn btn-square btn-ghost">
		<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block h-5 w-5 stroke-current"> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z"></path> </svg>
	  </button>
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


</style>

