<script lang="ts">
    export let showLogo : boolean;

    const buttons = {
        "About": "/about",
        "Projects": "/projects",
        "Skills": "/skills"
    }
</script>

<div class="sticky top-0 w-full h-[100px] bg-red-700 flex flex-row items-center justify-center">
    {#if showLogo}
        <div class="absolute top-[5%] left-[1%]">
            <div class="border-[4px] border-black w-min rounded-3xl">
                <a href="https://www.linkedin.com/in/sammytaubman/" target="_blank">
                    <h1 class="font-semibold p-[0.5rem] text-black leading-tight text-[1.5rem]"> S<br>T </h1>
                </a>
            </div>
        </div>
    {/if}
    {#each Object.entries(buttons) as [label, href]}
        <a class="m-2 md:m-6 hover:font-bold text-xl" href={href}>{label}</a>
    {/each}
</div>

