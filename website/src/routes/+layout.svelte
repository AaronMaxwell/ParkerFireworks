<script>
	import '../app.css';
    import {onMount} from "svelte";
    import {onNavigate} from "$app/navigation";
	
	let { children } = $props();

    let loaded = $state(false)
    let mobile = $state(false)

    let menu = $state(false)

    onMount(() => {
        mobile = screen.width < screen.height

        loaded = true
    })

    onNavigate(()=> {
        menu = false
    })
</script>


{#if loaded}
<nav class="flex relative flex-row sticky top-0 bg-yellow items-center justify-between z-10 drop-shadow-md drop-shadow-black p-2 px-0">
    <a href="/" class="flex z-20 flex-col select-none text-xl tracking-wider uppercase font-black px-3.5 sm:text-2xl text-center">
        <h1 class="text-blue pr-2">Parker</h1>
        <h1 class="text-red">Fireworks</h1>
    </a>

    {#if mobile}

        <button onclick={() => menu=!menu} class="flex flex-col px-12 justify-between w-7 h-5 cursor-pointer relative p-1 rounded-md">
            <div class="hamburger-line w-5 h-0.5 bg-gray-800 rounded-full transition-all duration-300 ease-in-out"></div>
            <div class="hamburger-line w-5 h-0.5 bg-gray-800 rounded-full transition-all duration-300 ease-in-out"></div>
            <div class="hamburger-line w-5 h-0.5 bg-gray-800 rounded-full transition-all duration-300 ease-in-out"></div>
        </button>


        <!-- Menu -->
        {#if menu}

            <nav class="absolute z-30 top-0 right-0 h-full w-[85%] bg-blue-700 text-white shadow-lg">
                <div class="bg-[#050505] drop-shadow-2xl h-[100vh] p-4">
                    <button onclick={() => menu=!menu} class="absolute top-0 right-0 p-6 px-8 text-white text-3xl font-bold focus:outline-none rounded-full p-2 hover:bg-blue-600 transition duration-200 cursor-pointer">
                        &times;
                    </button>
                    <ul class="space-y-4 text-xl">
                        <li>
                            <a href="/firework-stores" class="font-normal font-chiron-hei-hk block p-3 rounded-md hover:bg-blue-600 transition duration-200">Firework Stores</a>
                        </li>
                    </ul>
                </div>
            </nav>
        {/if}

    {:else }
        <div class="flex flex-row flex-grow justify-center items-center sm:justify-start sm:px-12 lg:px-[22rem] sm:text-xl sm:absolute font-black tracking-wider text-neutral-950 w-full">
            <a href="/firework-stores" class=" sm:p-4 hover:underline underline-offset-4 uppercase">Firework Stores</a>
        </div>
    {/if}
</nav>

<div class="flex flex-col min-h-[80vh] overflow-x-hidden">
    {@render children()}

    <div class="flex flex-col flex-grow"></div>

    <footer class="flex flex-col bg-neutral-800 items-center">
        <div class="flex text-neutral-50 flex-col p-4">
            <h1 class="font-semibold self-center">Contact Us</h1>
            <a class="self-center" href="tel:+12345678910">+1 (234)-5678-910</a>
            <h2>618 Maryville Hwy, Seymour, TN 37865</h2>
        </div>
    </footer>
</div>
{/if}