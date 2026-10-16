<script>
	import ScrollVideo from "#lib/misc/ScrollVideo.svelte";


    let scrollY = $state(0);
</script>

<svelte:window bind:scrollY={scrollY} />

<div class="">
    <div 
        class="hero-video"
        style:transform={`translateY(${scrollY * 0.2}px)`}
    >
        <ScrollVideo src="/videos/hero.mp4" startScroll={0} endScroll={650} smoothing={0.22} />
    </div>

    <div class="hero pt-8 px-16 pb-24">
        <div class="z-10">
            <h2 class="intro">
                Aerospace engineer by major, <br> Software engineer by job, <br> Designer by heart.
            </h2>
        </div>
        <div class="motion-safe:animate-text-intro">
            <h1 class="name">
                Ian Doering
            </h1>
        </div>
    </div>
</div>

<div class="h-[1500px]">
    <p>testing {scrollY}</p>
</div>

<style>
    .hero {
        box-sizing: border-box;
        min-height: 100svh;

        display: grid;
        grid-template-columns: auto minmax(0, 1fr);
        align-items: end;
        gap: 3rem;
    }

    .hero-video {
        position: absolute;
        right: 0rem;

        min-height: 25rem;
        max-height: 68svh;
        width: 80%;
        aspect-ratio: 21 / 9;
        object-fit: cover;
        display: block;
        z-index: 0;
    }

    .intro {
        justify-self: end;
        padding-bottom: 0.2rem;
        margin: 0;
    }

    .name {
        justify-self: end;
        text-align: right;
        margin: 0;
        line-height: 1;
        transform: translateY(0.09em);
    }
</style>