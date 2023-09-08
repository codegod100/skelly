<script>
	export let modal, parent;
	import { AppShell, AppBar, Modal, getModalStore, initializeStores } from '@skeletonlabs/skeleton';
</script>

<div class="card w-modal p-4 shadow-xl text-center variant-filled">
	<a href="/foo" on:click={() => parent.currentModal.close()}>secret page <slot /></a>
</div>
