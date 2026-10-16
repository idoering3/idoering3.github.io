<script lang="ts">
	import './layout.css';
	import type { LayoutProps } from './$types';
	import Header from '#lib/components/Header.svelte';

	let { children }: LayoutProps = $props();
</script>

<!-- header -->
<Header />

<!-- content -->
<div>
	{@render children()}
</div>