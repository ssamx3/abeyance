<script lang="ts">
    //imports --
    import { gsap } from 'gsap';
    import { SplitText } from "gsap/SplitText";
    import { onMount, onDestroy } from 'svelte';
    gsap.registerPlugin(SplitText);

    let hoverTimelines: { [key: string]: gsap.core.Timeline } = {};


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



    function handleMouseEnter(selector: string) {
        if (hoverTimelines[selector]) {
            hoverTimelines[selector].kill();
        }


        // Create a new timeline for smooth animations
        hoverTimelines[selector] = gsap.timeline();

        hoverTimelines[selector].to(selector,{
            duration: 0.5,
                scale: 1.2,
                rotate: 2,
                ease: "elastic",
            filter:  "blur(1px)"
        });

        hoverTimelines[selector].to(selector, {
            duration: 0.5,
            scale: 1,
            rotate: 0,
            ease: "elastic.inout",
            filter: "blur(0px)"
        }, 0.1
        )
    }

    /* function handleMouseLeave(selector: string) {
        if (hoverTimelines[selector]) {
            hoverTimelines[selector].kill();
        }

        hoverTimelines[selector] = gsap.timeline();

        hoverTimelines[selector].to(selector, {
            duration: 0.3,
            scale: 1,
            rotate: 0,
            ease: "power2.out",
            filter: "blur(0px)"
        });
    } */


</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');
    .WaveTitle {
        color: #ffffff;
        font-size: clamp(28px, 6vw, 75px);
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

        border-color: #2e2e2e;
        border-width: clamp(2px, 1vw, 15px);
        border-style: dashed;
        padding: clamp(30px, 10vw, 100px);
        border-radius: 10px;
    }

    .Link1 {
        font-family: "VT323", monospace;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }
    .Link2 {
        font-family: "VT323", monospace;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }
    .Link3 {
        font-family: "VT323", monospace;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }
    .Link4 {
        font-family: "VT323", monospace;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }
    .LinkBox {
        align-items: center;
        display: flex;
        flex-direction: row;
    }
</style>

<main>
    <div class="box">
        <h1 class="WaveTitle"
            on:mouseenter={() => handleMouseEnter(".WaveTitle")}

        >
            ssamx3
        </h1>

        <div class="LinkBox">
            <a href="https://www.google.com"
               class="Link1"
               on:mouseenter={() => handleMouseEnter(".Link1")}

            >
                blog</a>

            <p class="Link4"> &nbsp;//&nbsp; </p>

            <a href="https://www.x.com" class="Link2"
               on:mouseenter={() => handleMouseEnter(".Link2")}

            >
                projects</a>

            <p class="Link4"> &nbsp;//&nbsp; </p>
            <a href="https://www.github.com/ssamx3 "
               class="Link3"
               on:mouseenter={() => handleMouseEnter(".Link3")}

            >
                github</a>
        </div>
    </div>



</main>

