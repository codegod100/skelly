<script>
	import '../app.postcss';
	import { AppShell, AppBar, Modal, getModalStore, initializeStores } from '@skeletonlabs/skeleton';

	// Highlight JS
	import hljs from 'highlight.js';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	import Magic from '$lib/Magic.svelte';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
	initializeStores();
	const modalStore = getModalStore();
	const modal = {
		type: 'component',
		component: {
			ref: Magic,
			props: { modal: this }
		}
	};
</script>

<Modal />
<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase"><a href="/">Skeleton</a></strong>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://discord.gg/EXqV7W8MtY"
					target="_blank"
					rel="noreferrer"
				>
					Discord
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://twitter.com/SkeletonUI"
					target="_blank"
					rel="noreferrer"
				>
					Twitter
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://github.com/skeletonlabs/skeleton"
					target="_blank"
					rel="noreferrer"
				>
					GitHub
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Page Route Content -->
	<svelte:fragment slot="footer">
		<AppBar slotTrail="place-content-center">
			<div class="grid grid-cols-2 gap-5">
				<div class="col-span-1">
					<h1>Stuff</h1>
					<div>one</div>
					<div>two</div>
					<div>three</div>
				</div>
				<div class="col-span-1">
					<h1>Other stuff</h1>
					<div>four</div>
					<div>five</div>
					<div>six</div>
				</div>
			</div>

			<svelte:fragment slot="trail">
				<div>
					<button class="btn variant-filled" on:click={() => modalStore.trigger(modal)}
						>click me</button
					>
				</div>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<slot />
</AppShell>
