<script>

    import {onMount} from "svelte";

    function getCountdown() {

        const difference =  new Date(new Date().getFullYear(), 6, 10).getTime() - new Date().getTime()

        const seconds =  String(Math.floor((difference / 1000) % 60)).padStart(2, "0");
        const minutes = String(Math.floor((difference / 1000 / 60) % 60)).padStart(2, "0");
        const hours = String(Math.floor((difference / (1000 * 60 * 60)) % 24)).padStart(2, "0");
        const days = Math.floor(difference / (1000 * 60 * 60 * 24));

        return `${days}:${hours}:${minutes}:${seconds}`;
    }

    let countdown = $state(getCountdown());

    onMount(()=>{
        setInterval(()=>{
            countdown = getCountdown()
        }, 100)
    })

</script>


<div class="-z-10 font-chiron-hei flex flex-col bg-black text-white items-center">
    <div class="flex flex-col w-full max-w-[100vw] sm:max-w-[900px] 2xl:max-w-[1200px]">
        <div class="flex flex-col relative">
            <picture>
                <source srcset="/fireworks.avif" type="image/avif">
                <source srcset="/fireworks.webp" type="image/webp">
                <img class="w-full object-cover sm:max-h-[25rem] 2xl:max-h-[32rem]" alt="Fireworks Exploding" src="/fireworks.jpg">
            </picture>
            <h1 class="absolute top-0 text-2xl sm:p-10 sm:text-5xl sm:text-shadow-neutral-800 w-full text-center -skew-x-6 text-shadow-lg font-black py-4">LOOK FOR THE <span class="text-yellow">BRIGHT YELLOW</span> SIGN!</h1>
        </div>
        <div class="relative flex flex-col p-5 sm:p-8 pt-7 gap-6 font-semibold sm:text-base sm:text-xl">

            {#if Number(countdown.split(":")[0]) < 18 && Number(countdown.split(":")[0]) >= 0 }
                <div class="flex flex-col justify-center items-center w-full text-3xl sm:text-5xl">
                    <h1 class="text-yellow uppercase font-black tracking-wide">Countdown</h1>
                    <h1 class=" font-black tracking-widest">{countdown}</h1>
                </div>
            {/if}
            <article class="desktop">
                <h2 class="pb-3 sm:py-10">
                    At Parker Fireworks in East Tennessee,
                    we’re your local destination for fireworks
                    during the 4th of July season. Whether you're
                    hosting a backyard cookout,
                    gathering with family, or just want to light up the skies,
                    we’ve got everything you need to make your celebration
                    <span class="text-[1.025rem] sm:text-xl text-[#FF0000] font-black tracking-wide uppercase">unforgettable.</span></h2>

                <h2 class="sm:pb-10">We carry a wide selection of high-quality fireworks
                    at prices that make it easy to stock up big on aerials,
                    artillery shells, fountains, sparklers, smoke bombs, and more.
                    As a locally owned and veteran founded business, we’re proud to serve the
                    <span class="font-black">Sevierville, Maryville, Newport & Morristown</span> communities with
                    honest advice and a real passion for fireworks.
                    Stop by and see why families across East Tennessee trust
                    Parker Fireworks to kick off their <span class="text-yellow font-black -skew-x-12 ">July 4<span class="text-sm">th</span></span> with a <span class="text-[#FF0000] font-black uppercase tracking-wide -skew-x-12">bang!</span>
                </h2>
            </article>
        </div>
    </div>
</div>

<style>
    @media (width >= 40rem) {
        .desktop {
            line-height: 1.75rem;
            font-size: 1.42rem;
        }
    }
</style>

