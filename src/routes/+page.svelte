
<div class="hero">
    <h2 class="intro">
        Aerospace engineer by major, <br> Software engineer by job, <br> Designer by heart.
    </h2>
    <h1 class="name">
        Ian Doering
    </h1>
</div>

<style>
    .hero {
        box-sizing: border-box;
        min-height: 100svh;
        padding: 2rem 4rem 4rem;

        display: grid;
        grid-template-columns: auto minmax(0, 1fr);
        align-items: end;
        gap: 3rem;
    }

    .intro {
        justify-self: start;
        padding-bottom: 1.65rem;
        margin: 0;
    }

    .name {
        justify-self: end;
        text-align: right;
        margin: 0;
        font-size: clamp(6rem, 12vw, 20rem);
        line-height: 1;
    }
</style>