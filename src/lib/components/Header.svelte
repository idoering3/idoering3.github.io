<script>
	import Button from "./Button.svelte";

</script>
<div class="fixed z-10 flex align-middle justify-between w-full">
    <!-- my signature -->
    <a href="" class="signature relative">
        <img class=" mix-blend-difference h-14 mt-1 ml-6 select-none" draggable="false" src="/images/signature.png" alt="Ian Doering">
        <svg
            class="pointer-events-none absolute -bottom-1 left-[12%] h-8 w-[88%]"
            viewBox="0 0 120 20"
            preserveAspectRatio="none"
            aria-hidden="true"
        >
            <path
                d="M8 14 Q65 7 118 5"
                pathLength="1"
                fill="none"
                stroke="currentColor"
                stroke-width="0.7"
                stroke-linecap="round"
            />
        </svg>
    </a>
    
    <div class="flex align-middle justify-center pr-24">
        <Button href="/">
            Work
        </Button>
        <Button href="">
            About
        </Button>
        <Button href="">
            Contact
        </Button>
    </div>
</div>

<style>
    .signature path {
        stroke-dasharray: 1;
        stroke-dashoffset: 1;
    }

    .signature:hover path,
    .signature:focus-visible path {
        stroke-dashoffset: 0;
    }

    @media (prefers-reduced-motion: no-preference) {
        .signature path {
            transition: stroke-dashoffset 220ms ease-out;
        }
    }
</style>