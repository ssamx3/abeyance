<script lang="ts">
    //imports --
    import {gsap} from 'gsap';
    import {SplitText} from "gsap/SplitText";
    import {onMount, onDestroy} from 'svelte';
    import VanillaTilt from "vanilla-tilt";

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
        VanillaTilt.init(document.querySelector(".box"), {
            max: 10,
            speed: 400,
            glare: true,
            "max-glare": 0.2,
            easing: "cubic-bezier(.03,.98,.52,.99)",
            transition: true
        })
    })


    function handleMouseEnter(selector: string) {
        if (hoverTimelines[selector]) {
            hoverTimelines[selector].kill();
        }


        // Create a new timeline for smooth animations
        hoverTimelines[selector] = gsap.timeline();

        hoverTimelines[selector].to(selector, {
            duration: 0.5,
            y: -10,
            rotate: 0,
            scaleX: 0.9,
            ease: "elastic",
            filter: "blur(1px)"
        });

        hoverTimelines[selector].to(selector, {
                duration: 0.5,
                y: 0,
                scaleX: 1,
                rotate: 0,
                ease: "elastic.inout",
                filter: "blur(0px)"
            }, 0.1
        )
    }


</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');

    :global(html, body) {
        margin: 0;
        padding: 0;
        height: 100%;
        width: 100%;
        overflow-x: hidden;
    }


    .WaveTitle {
        color: #ffffff;
        font-size: clamp(28px, 6vw, 75px);
        font-family: "VT323", monospace;
        font-weight: 400;
        letter-spacing: 0.8vw;
        font-optical-sizing: auto;
        padding: 0;
        margin: 0;
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
        background: rgb(10, 10, 10);
        background: radial-gradient(circle, rgb(92, 73, 99) 0%, rgba(10, 10, 10, 1) 100%);
    }

    .box {

        border-color: rgba(255, 255, 255, 0.3);
        border-style: solid;

        border-width: clamp(2px, 0.5vw, 15px);
        backdrop-filter: blur(50px);
        padding: clamp(20px, 10vw, 500px);
        border-radius: 25px;

    }

    .Link1 {
        font-family: "VT323", monospace;
        color: white;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }

    .Link2 {
        font-family: "VT323", monospace;
        color: white;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }

    .Link3 {
        font-family: "VT323", monospace;
        color: white;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }

    .Link4 {
        font-family: "VT323", monospace;
        color: white;
        font-weight: 100;
        font-size: clamp(16px, 2vw, 25px);
    }

    .LinkBox {
        align-items: center;
        display: flex;
        flex-direction: row;
    }

    #app {
        height: 100%;
        width: 100%;
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
            <a href="https://blog.abeyance.space"
               class="Link1"
               on:mouseenter={() => handleMouseEnter(".Link1")}

            >
                blog</a>

            <p class="Link4"> &nbsp;//&nbsp; </p>

            <a href="https://blog.abeyance.space/blog/tag/projects" class="Link2"
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

