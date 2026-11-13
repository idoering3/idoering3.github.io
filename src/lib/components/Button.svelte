<script lang='ts'>
    let { children, href } = $props();
</script>

<div class="mix-blend-difference flex items-center">
    <a
        class="relative inline-flex items-center justify-center px-2 py-2 leading-none text-white
            after:pointer-events-none after:absolute after:inset-x-2 after:bottom-1
            after:h-px after:origin-left after:scale-x-0 after:bg-current
            after:content-[''] motion-safe:after:transition-transform
            after:duration-200 after:ease-out
            hover:after:scale-x-100 focus-visible:after:scale-x-100"
        href={href}
    >
        {@render children?.()}
    </a>
</div>