<script lang="ts">
    import Hero from "../components/Hero.svelte"
</script>

<Hero />

<div class="w-full h-[100vh] landing-bg" />
<div class="h-[200vh] bg-white" />

<style>
    .landing-bg {
        background-color:hsla(217,66%,28%,1);
        background-image:
        radial-gradient(at 94% 9%, hsla(217,57%,52%,1) 0px, transparent 50%),
        radial-gradient(at 95% 100%, hsla(184,58%,30%,1) 0px, transparent 50%),
        radial-gradient(at 0% 0%, hsla(187,95%,33%,1) 0px, transparent 50%);
    }
</style>