<script lang="ts">
	import { onMount } from "svelte";

    interface Props {
        src: string;
        startScroll?: number;
        endScroll?: number;
        smoothing?: number;
    }

    let {
        src,
        startScroll = 0,
        endScroll = 1500,
        smoothing = 0.12
    }: Props = $props();

    let video = $state<HTMLVideoElement>();
    let scrollY = $state(0);
    let duration = $state(0);

    let progress = $derived(
        endScroll > startScroll
            ? Math.max(
                0,
                Math.min(
                    1,
                    (scrollY - startScroll) / (endScroll - startScroll)
                )
            )
            : 0
    );

    onMount(() => {
        let frame: number;
        let displayedTime = 0;
        let previousTime: number | undefined;

        function animate(now: number) {
            const elapsed = previousTime === undefined
                ? 1000 / 60
                : Math.min(now - previousTime, 100);

            previousTime = now;

            if (video && Number.isFinite(duration) && duration > 0) {
                const targetTime = progress * duration;

                // Adjust for different monitor refresh rates.
                const strength = Math.max(0.001, Math.min(1, smoothing));
                const amount = 1 - Math.pow(
                    1 - strength,
                    elapsed / (1000 / 60)
                );

                displayedTime += (targetTime - displayedTime) * amount;

                if (Math.abs(targetTime - displayedTime) < 0.01) {
                    displayedTime = targetTime;
                }

                // Let the browser finish its current seek first.
                if (
                    !video.seeking &&
                    Math.abs(video.currentTime - displayedTime) > 0.01
                ) {
                    video.currentTime = displayedTime;
                }
            }

            frame = requestAnimationFrame(animate);
        }

        frame = requestAnimationFrame(animate);

        return () => cancelAnimationFrame(frame);
    });
</script>

<svelte:window bind:scrollY />

<div class="overflow-hidden w-full h-full">
    <video
        bind:this={video}
        bind:duration
        {src}
        muted
        playsinline
        preload="auto"
    ></video>
</div>

<style>
    video {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
</style>