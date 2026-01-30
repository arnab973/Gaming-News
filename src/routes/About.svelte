<script>
    import Header from ".././components/Header.svelte";
    import MainAbout from "../components/about_page/MainAbout.svelte";
    import Footer from ".././components/Footer.svelte";
</script>

<div class="w-full min-h-screen bg-color-0" style="background-image: url('/backgroundImageSign.svg'); background-size: cover; background-position: center;">
    <Header className="sticky top-0" />
    <MainAbout />
    <hr class="lg:hidden max-w-[1024px] mx-[16px] md:mx-[32px] mt-16 border-t-2">
    <div class="flex items-center justify-center m-5 mt-16">
        <h1
        class="text-[#69D3C9] text-[36px] font-title-semibold block text-center"
        >
            Creator
        </h1>
    </div>
    <div class="max-w-[768px] mx-auto md:px-[32px] xl:px-0 text-center">
        <img src="/WhatsApp Image 2025-06-22 at 22.05.31_7a95192f.jpg" alt="Arnab Das" class="w-36 h-36 rounded-full mx-auto mb-4" />
        <h2 class="text-white text-2xl font-bold mb-4">Arnab Das</h2>
        <p class="text-white text-lg mb-6">Full Stack Web Developer</p>
        <div class="flex justify-center space-x-4">
            <a href="https://www.linkedin.com/in/arnabdas2003" target="_blank" class="text-[#69D3C9] hover:text-white">LinkedIn</a>
            <a href="https://www.facebook.com/share/1HVP3gHHFY/" target="_blank" class="text-[#69D3C9] hover:text-white">Facebook</a>
            <a href="https://www.instagram.com/creative_arnab?igsh=MWZmdmdvZTFvMGZ4Ng==" target="_blank" class="text-[#69D3C9] hover:text-white">Instagram</a>
            <a href="https://github.com/arnab973" target="_blank" class="text-[#69D3C9] hover:text-white">GitHub</a>
        </div>
    </div>
    <hr class="lg:hidden max-w-[1024px] mx-[16px] md:mx-[32px] mt-16 border-t-2">
    <div class="flex items-center justify-center mb-10 max-w-[1024px] mx-auto">
        <h2 class="block text-4xl text-color-title font-title-bold text-center my-28 px-[16px] md:px-[100px] py-16 dark:bg-[#001A24] bg-[#EEE] border-2 max-lg:border-x-0 border-[#69D3C9] dark:border-white lg:rounded-lg" style="background-image: url('/backgroundImageAbout.svg'); background-size: cover; background-position: center;">
            Success is not definitive, failure is not fatal: It is the courage to
            continue that counts.
        </h2>
    </div>
    <Footer />
</div>
