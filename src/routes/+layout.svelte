<script lang="ts">
	import './layout.css';
	import type { LayoutProps } from './$types';
	import Lenis from 'lenis';
	import 'lenis/dist/lenis.css';
	import { onMount } from 'svelte';
	import Header from '#lib/components/Header.svelte';

	onMount(() => {
		const lenis = new Lenis({
		autoRaf: true,
		smoothWheel: true,
		lerp: 0.16,
		anchors: true
		});

		return () => lenis.destroy();
	});

	let { children }: LayoutProps = $props();
</script>

<!-- header -->
<Header />

<!-- content -->
<div>
	{@render children()}
</div>