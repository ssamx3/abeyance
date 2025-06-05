<script lang="ts">
    //imports --
    import { gsap } from 'gsap';
    import { SplitText } from "gsap/SplitText";
    import { onMount, onDestroy } from 'svelte';
    gsap.registerPlugin(SplitText);
    //imports
    onMount(() => {
    gsap.from(".box", {
        scale: 0,
        ease: "back.inOut",
        filter: "blur(20px)",
        duration: 1,
        opacity: 0
        }
    )
        SplitText.create(".WaveTitle", {
            type: "words, chars",
            onSplit(self) {

                gsap.from(self.chars, {
                    duration: 2,
                    y: 75,
                    scale: 0.0,
                    opacity: 0,
                    rotate: 25,
                    autoAlpha: 0,
                    stagger: 0.05,
                    ease: "elastic",
                    color: "#000000",
                    fontWeight: "thin",
                    filter: "blur(15px)"
                });
            }
        });
    })



</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
    .WaveTitle {
        color: #ffffff;
        font-size: 6vw;
        font-family: "VT323", monospace;
        font-weight: 400;
        letter-spacing: 0.8vw;
        font-optical-sizing: auto;
        padding: 0;
    }

    main {
        font-family: sans-serif;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        width: 100vw;
        margin: 0;
    }

    .box {
        #background-color: #2e2e2e;
        border-color: #2e2e2e;
        border-width: 10px;
        border-style: dashed;
        padding: 8vw;
        border-radius: 10px;
    }

    .Link {
        font-family: "VT323", monospace;
        font-weight: 100;
        font-size: 2vw;
    }
    .linkbox {
        align-items: center;
        display: flex;
        flex-direction: row;
    }
</style>

<main>
    <div class="box">
        <h2 class="WaveTitle">abeyance</h2>
        <div class="linkbox">
            <a href="https://www.google.com" class="Link">blog</a>
            <p class="Link"> &nbsp;//&nbsp; </p>
            <a href="https://www.x.com" class="Link">projects</a>
            <p class="Link"> &nbsp;//&nbsp; </p>
            <a href="https://www.github.com/ssamx3" class="Link">github</a>
        </div>
    </div>



</main>

