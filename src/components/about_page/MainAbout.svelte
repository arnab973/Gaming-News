<script>
    let aboutText = "About Us\n\nHi, I’m Arnab Das, the creator of this website.\n\nI’m a passionate gamer and a tech enthusiast who loves exploring the gaming world beyond just playing.\n\nThis platform is dedicated to bringing you latest gaming news, updates, esports highlights, and honest insights — all in one place.\n\n It  is built for gamers who want to stay updated, informed, and ahead of the game.\n\nNo fake rumors, no clickbait — just real gaming news, delivered with passion.\n\nStay connected. Stay updated.\n\nGame On 🎯"
</script>

<div class="w-full max-w-[1280px] mx-auto py-16 px-4">
    <div class="bg-gradient-to-br from-[#001B28] to-[#002A3A] rounded-2xl shadow-2xl overflow-hidden">
        <div class="p-8 md:p-12">
            <div class="flex flex-col lg:flex-row items-center gap-8">
                <div class="flex-1">
                    <h1 class="text-[#69D3C9] text-4xl md:text-5xl font-bold mb-6 text-center lg:text-left">About Us</h1>
                    <div class="text-white text-lg leading-relaxed space-y-4">
                        {#each aboutText.split('\n\n') as paragraph}
                            <p>{paragraph}</p>
                        {/each}
                    </div>
                </div>
                
                <div class="flex-shrink-0">
                    <div class="bg-[#69D3C9] bg-opacity-10 p-6 rounded-full">
                        <img src="logoImage.svg" alt="Logo" class="w-32 h-32 md:w-40 md:h-40" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
