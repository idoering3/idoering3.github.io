<script lang="ts">
	import './layout.css';
	import type { LayoutProps } from './$types';

	let { children }: LayoutProps = $props();
</script>

<!-- header -->
<div class="fixed z-10">
	<img class="h-14 mt-2 ml-6 select-none" draggable="false" src="/images/signature.png" alt="Ian Doering">
</div>

<!-- content -->
<div>
	{@render children()}
</div>