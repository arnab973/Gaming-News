<script>
    let email = '';
    let password = '';

    function handleLogin() {
        // Handle login logic here
        console.log('Login:', email, password);
    }
</script>

<div class="w-full min-h-screen bg-color-0 flex items-center justify-center" style="background-image: url('/backgroundImageSign.svg'); background-size: cover; background-position: center;">
    <div class="bg-white dark:bg-[#001A24] p-8 rounded-lg shadow-lg max-w-md w-full">
        <h1 class="text-2xl font-bold text-center mb-6 text-color-title">Login</h1>
        <form on:submit|preventDefault={handleLogin}>
            <div class="mb-4">
                <label for="email" class="block text-sm font-medium text-color-body">Email</label>
                <input type="email" id="email" bind:value={email} class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#69D3C9] focus:border-[#69D3C9]" required>
            </div>
            <div class="mb-6">
                <label for="password" class="block text-sm font-medium text-color-body dark:text-white">Password</label>
                <input type="password" id="password" bind:value={password} class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#69D3C9] focus:border-[#69D3C9]" required>
            </div>
            <button type="submit" class="w-full bg-[#69D3C9] text-white py-2 px-4 rounded-md hover:bg-[#5AB8B2] transition-colors">Login</button>
        </form>
        {#if errorMessage}
            <p class="mt-4 text-center text-sm text-red-500">{errorMessage}</p>
        {/if}
        <p class="mt-4 text-center text-sm text-color-body">
            Don't have an account? <a href="/#/create-account" class="text-[#69D3C9] hover:underline">Sign up</a>
        </p>
    </div>
</div>
