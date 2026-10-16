<script lang='ts'>
    let { children, href } = $props();
</script>

<div class="mix-blend-difference flex items-center">
    <a
        class="inline-flex items-center justify-center text-white p-2 leading-none"
        href={href}
    >
        {@render children?.()}
    </a>
</div>