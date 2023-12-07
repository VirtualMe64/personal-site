<script lang="ts">
    let y : number = 0;

    let yDefault = 1080;
    let width = 1920;
    let parallax = 1;

    const interpolate = (start : number, end : number, scroll: number, includeScroll: boolean) => {
        let pct : number = Math.max(0, Math.min(scroll / parallax, yDefault)) / yDefault;
        // spline to smooth out movement
        pct = pct == 1 ? 1 : (Math.log2(pct + 0.5) + 1) / (Math.log2(1.5) + 1);
        return start + (end - start) * pct + (includeScroll ? scroll : 0);
    }

    let yOffsetPct = 50;
    $: yOffsetPct = interpolate(50, 1, y, false);
    let xOffsetPct = 50;
    $: xOffsetPct = interpolate(50, 1, y, false);
    let translatePct = 50;
    $: translatePct = interpolate(50, 0, y, false);
    let fontRems = 8;
    $: fontRems = interpolate(width > 850 ? 8 : 3.5, 1.5, y, false);
    let paddingRems = 2;
    $: paddingRems = interpolate(2, 0.5, y, false);
    let borderWidth = 2;
    $: borderWidth = interpolate(4, 4, y, false);
    let innerPct = 100;
    $: innerPct = interpolate(100, 30, y, false);
    let textPct = 100;
    $: textPct = interpolate(100, 80, y, false);
    let fullText = true;
    $: fullText = (y / parallax < yDefault);
</script>

<div class="flex flex-col absolute overflow-clip w-min"
     style="transform: translate(-{translatePct}%,-{translatePct}%) translate(5px, {y}px);top:{yOffsetPct}%;left:{xOffsetPct}%">
    <div style="width: {fullText ? innerPct : 100}%; border-width: {borderWidth}px;"
         class="rounded-3xl border-black">
        <div class="overflow-clip" style="width: {fullText ? textPct : 100}%;">
            <h1 class="font-semibold p-4 text-black leading-tight"
                style="font-size:{fontRems}rem;padding:{paddingRems}rem">
                {#if fullText}
                Sammy<br>Taubman
                {:else}
                S<br>T
                {/if}
            </h1>
        </div>
    </div>
</div>

<svelte:window bind:scrollY={y} bind:innerHeight={yDefault} bind:innerWidth={width}/>