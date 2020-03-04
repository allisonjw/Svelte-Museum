<script>
	import { createEventDispatcher, onDestroy } from 'svelte';
    import { fade } from 'svelte/transition';
	const dispatch = createEventDispatcher();
    const close = () => dispatch('close');

	let modal;

	const handle_keydown = e => {
		if (e.key === 'Escape') {
			close();
			return;
		}

		if (e.key === 'Tab') {
			const nodes = modal.querySelectorAll('*');
			const tabbable = Array.from(nodes).filter(n => n.tabIndex >= 0);

			let index = tabbable.indexOf(document.activeElement);
			if (index === -1 && e.shiftKey) index = 0;

			index += tabbable.length + (e.shiftKey ? -1 : 1);
			index %= tabbable.length;

			tabbable[index].focus();
			e.preventDefault();
		}
	};

	const previously_focused = typeof document !== 'undefined' && document.activeElement;

	if (previously_focused) {
		onDestroy(() => {
			previously_focused.focus();
		});
	}
</script>

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.3);
	}
	.modal {
		position: absolute;
		left: 50%;
		top: 71%;
		width: calc(100vw - 4em);
		max-width: 40em;
		max-height: calc(100vh - 4em);
		overflow: auto;
		transform: translate(-50%,-50%);
		padding: 1em;
		border-radius: 0.2em;
        background: white;
        z-index: 2;
	}
	button {
        display: block;
        background-color: #109e6c;
        width: 30%;
        font-size: 1.2em;
	}
</style>

<svelte:window on:keydown={handle_keydown}/>

<div class="modal-background" on:click={close}></div>
<div class="modal" bind:this={modal} transition:fade= {{ y: 125, duration: 500 }}>
    <hr>
      <slot></slot>
    <hr>
    <button on:click={close}>close</button>
</div>
