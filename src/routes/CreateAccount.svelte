<script>
  import Header from "../components/Header.svelte";
  import Footer from "../components/Footer.svelte";
  import { signInWithPopup } from 'firebase/auth';
  import { auth, googleProvider, facebookProvider } from '../firebase.js';

  let src = "../public/backgroundImageRegister.svg";

  function handleFormSubmit() {
      console.log('Formulário enviado!');
  };

  async function signInWithGoogle() {
    try {
      const result = await signInWithPopup(auth, googleProvider);
      console.log('Google sign in successful:', result.user);
      // Redirect or handle success
    } catch (error) {
      console.error('Google sign in error:', error);
    }
  }

  async function signInWithFacebook() {
    try {
      const result = await signInWithPopup(auth, facebookProvider);
      console.log('Facebook sign in successful:', result.user);
      // Redirect or handle success
    } catch (error) {
      console.error('Facebook sign in error:', error);
    }
  }

  let routes = [
      ["/#/login", "Login"],
      ["/#/signup", "Sign Up"],
      ["/#/about", "About Us"],
      ["/#/help", "Help"],
  ];
</script>

<div class="w-full min-h-screen bg-color-0" style="background-image: url('{src}'); background-size: cover; background-position: center;">
    <Header className="sticky top-0" />

    <div class="flex items-center justify-center min-h-[80vh] px-[16px] sm:px-[32px] xl:px-0">
        <div class="w-full max-w-[400px] bg-[#051d26] p-8 rounded-lg shadow-lg border-2 border-[#2ec4b6]">
            <h2 class="text-2xl font-bold text-center text-white mb-6">Create Account</h2>

            <form on:submit|preventDefault={handleFormSubmit} class="space-y-4">
                <div>
                    <label for="email" class="block text-sm font-medium text-white">Email</label>
                    <input type="email" id="email" name="email" required
                           class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#2ec4b6] focus:border-[#2ec4b6] bg-white">
                </div>

                <div class="relative">
                    <label for="password" class="block text-sm font-medium text-white">Password</label>
                    <input type={showPassword ? 'text' : 'password'} id="password" name="password" required
                           class="mt-1 block w-full px-3 py-2 pr-10 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#2ec4b6] focus:border-[#2ec4b6] bg-white">
                    <button type="button" on:click={() => showPassword = !showPassword} class="absolute inset-y-0 right-0 pr-3 flex items-center text-sm leading-5 mt-1">
                        {showPassword ? 'Hide' : 'Show'}
                    </button>
                </div>

                <div>
                    <label for="confirmPassword" class="block text-sm font-medium text-white">Confirm Password</label>
                    <input type="password" id="confirmPassword" name="confirmPassword" required
                           class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#2ec4b6] focus:border-[#2ec4b6] bg-white">
                </div>

                <button type="submit" class="w-full bg-[#2ec4b6] text-white py-2 px-4 rounded-md hover:bg-[#1e9b8f] transition-colors">
                    Create Account
                </button>
            </form>

            <div class="mt-6">
                <div class="relative">
                    <div class="absolute inset-0 flex items-center">
                        <div class="w-full border-t border-gray-300"></div>
                    </div>
                    <div class="relative flex justify-center text-sm">
                        <span class="px-2 bg-[#051d26] text-white">or</span>
                    </div>
                </div>

                <div class="mt-6 grid grid-cols-1 gap-3">
                    <button on:click={signInWithGoogle} class="bg-[#051d26] border-2 border-[#2ec4b6] py-3 w-full flex justify-center items-center text-white transition-transform transform hover:scale-105 hover:bg-[#2ec4b6] rounded-md">
                        <img src="static/media/img/googleImage.svg" alt="Google" class="mr-2" />
                        Continue with Google
                    </button>
                    <button on:click={signInWithFacebook} class="bg-[#051d26] border-2 border-[#2ec4b6] py-3 mt-2 w-full flex justify-center items-center text-white transition-transform transform hover:scale-105 hover:bg-[#2ec4b6] rounded-md">
                        <img src="static/media/img/icons8-facebook-novo.svg" alt="Facebook" class="mr-2" />
                        Continue with Facebook
                    </button>
                </div>
            </div>

            <div class="mt-6 text-center">
                <p class="text-white">Already have an account? <a href="/#/login" class="text-[#2ec4b6] hover:text-[#1e9b8f]">Login</a></p>
            </div>
        </div>
    </div>

    <Footer />
</div>
