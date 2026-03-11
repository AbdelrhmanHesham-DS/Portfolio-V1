<template>
  <div class="max-w-7xl mx-auto flex flex-col relative">
    <nav
      :class="[
        'max-w-7xl px-5 md:fixed top-0 z-[98] w-screen transition-all duration-300',
        isScrolled 
          ? 'backdrop-blur-md bg-[#101010] bg-opacity-95 border-b border-[#2a2a2a] shadow-lg' 
          : 'backdrop-blur-md bg-[#101010] bg-opacity-90 border-b border-[#2a2a2a]'
      ]"
    >
      <div class="container mx-auto flex flex-wrap items-center justify-between py-4">
        <button @click="redirectToHome" class="flex items-center">
          <span class="text-xl font-bold text-red-500 tracking-tight hover:text-white transition">
            Eng.Abdelrhman(D3ff4ult);
          </span>
        </button>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex space-x-6 text-sm font-medium">
          <router-link to="/" class="text-gray-300 hover:text-white transition relative group">
            Home
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-red-500 transition-all duration-300 group-hover:w-full"></span>
          </router-link>
          <router-link to="/about" class="text-gray-300 hover:text-white transition relative group">
            About
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-red-500 transition-all duration-300 group-hover:w-full"></span>
          </router-link>
          <router-link to="/portfolio" class="text-gray-300 hover:text-white transition relative group">
            Projects
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-red-500 transition-all duration-300 group-hover:w-full"></span>
          </router-link>
          <router-link to="/contact" class="text-gray-300 hover:text-white transition relative group">
            Contact
            <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-red-500 transition-all duration-300 group-hover:w-full"></span>
          </router-link>
        </div>

        <!-- Mobile Menu Button -->
        <button
          @click="toggleMobileMenu"
          class="md:hidden p-2 rounded-lg text-gray-300 hover:text-white hover:bg-gray-800 transition-colors duration-300"
          aria-label="Toggle mobile menu"
        >
          <svg v-if="isMobileMenuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <div 
        :class="[
          'md:hidden transition-all duration-300 ease-in-out',
          isMobileMenuOpen 
            ? 'max-h-64 opacity-100' 
            : 'max-h-0 opacity-0 overflow-hidden'
        ]"
      >
        <div class="px-4 pt-2 pb-4 space-y-2 bg-[#101010] bg-opacity-95 border-t border-[#2a2a2a]">
          <router-link to="/" @click="closeMobileMenu" class="block px-4 py-3 text-gray-300 hover:text-white hover:bg-gray-800 rounded-lg transition-all duration-300">Home</router-link>
          <router-link to="/about" @click="closeMobileMenu" class="block px-4 py-3 text-gray-300 hover:text-white hover:bg-gray-800 rounded-lg transition-all duration-300">About</router-link>
          <router-link to="/portfolio" @click="closeMobileMenu" class="block px-4 py-3 text-gray-300 hover:text-white hover:bg-gray-800 rounded-lg transition-all duration-300">Projects</router-link>
          <router-link to="/contact" @click="closeMobileMenu" class="block px-4 py-3 text-gray-300 hover:text-white hover:bg-gray-800 rounded-lg transition-all duration-300">Contact</router-link>
        </div>
      </div>
    </nav>

    <!-- Mobile Menu Overlay -->
    <div v-if="isMobileMenuOpen" @click="closeMobileMenu" class="fixed inset-0 z-40 bg-black bg-opacity-50 md:hidden" />

    <div class="md:mt-[100px]">
      <router-view />
    </div>

    <footer class="bg-[#0f0f0f] border-t border-[#2c2c2c] text-gray-300 py-10 px-6">
      <div class="container mx-auto grid grid-cols-1 md:grid-cols-3 gap-8 text-sm">
        <div>
          <h2 class="text-lg font-semibold text-red-500 mb-3">Information</h2>
          <p>Back-end developer crafting modern sites</p>
        </div>
        <div>
          <h3 class="text-red-400 font-semibold mb-2">Quick Links</h3>
          <ul class="space-y-1">
            <li><router-link to="/" class="hover:text-white transition">Home</router-link></li>
            <li><router-link to="/about" class="hover:text-white transition">About</router-link></li>
            <li><router-link to="/portfolio" class="hover:text-white transition">Projects</router-link></li>
            <li><router-link to="/contact" class="hover:text-white transition">Contact</router-link></li>
          </ul>
        </div>
        <div>
          <h3 class="text-red-400 font-semibold mb-2">Contact Info</h3>
          <ul class="space-y-1">
            <li>Email: <a href="mailto:abdoh6112113@gmail.com" class="hover:text-white transition">abdoh6112113@gmail.com</a></li>
            <li>Phone: <a href="tel:+201149969986" class="hover:text-white transition">+20 114 996 9986</a></li>
            <li>Location: Giza, Egypt</li>
          </ul>
        </div>
      </div>
      <div class="flex justify-center gap-4 mt-8">
     <a href="https://www.linkedin.com/in/abdelrhman-hesham-395268335" target="_blank"
                class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1f1f1f] text-[#ff3b3b] hover:bg-[#2a2a2a] transition"
                aria-label="LinkedIn">
                <i class="fab fa-linkedin-in"></i>
              </a>
              <a href="https://snapchat.com/t/Hk3jmyAg" target="_blank"
                class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1f1f1f] text-[#ff3b3b] hover:bg-[#2a2a2a] transition"
                aria-label="Snapchat">
                <i class="fab fa-snapchat-ghost"></i>
              </a>
              <a href="https://www.facebook.com/abdo.hesham.52438" target="_blank"
                class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1f1f1f] text-[#ff3b3b] hover:bg-[#2a2a2a] transition"
                aria-label="Facebook">
                <i class="fab fa-facebook-f"></i>
              </a>
              <a href="https://www.instagram.com/abdo.h.28" target="_blank"
                class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1f1f1f] text-[#ff3b3b] hover:bg-[#2a2a2a] transition"
                aria-label="Instagram">
                <i class="fab fa-instagram"></i>
              </a>
              <a href="https://github.com/d3ff4ult" target="_blank"
                class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1f1f1f] text-[#ff3b3b] hover:bg-[#2a2a2a] transition"
                aria-label="GitHub">
                <i class="fab fa-github"></i>
              </a>
      </div>
      <div class="mt-6 text-center text-gray-500 text-xs">© {{ currentYear }} D3ff4ult. All rights reserved.</div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isMobileMenuOpen: false,
      isScrolled: false,
      currentYear: new Date().getFullYear()
    };
  },
  methods: {
    redirectToHome() {
      this.$router.push('/');
    },
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
    closeMobileMenu() {
      this.isMobileMenuOpen = false;
    },
    handleScroll() {
      this.isScrolled = window.scrollY > 20;
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  }
};
</script>

<style lang="css">
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

::-webkit-scrollbar {
  width: 5px;
  height: 5px;
}

::-webkit-scrollbar-track {
  background: hsla(0, 0%, 100%, 0);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb {
  background: #ffffff;
  border-radius: 5px;
}

::-webkit-scrollbar-button {
  width: 20px;
}

body {
  font-family: 'Poppins', sans-serif;
  background-color: #0b0b0b;
  color: #d1d1d1;
  font-size: 16px;
  line-height: 1.6;
  text-align: left;
  padding: 0;
  margin: 0;
}

nav a {
  font-size: 15px;
  transition: color 0.3s ease;
}

h1, h2, h3 {
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  color: #ffffff;
}

p {
  font-size: 14px;
  color: #bcbcbc;
}

nav a.router-link-exact-active {
  display: inline-flex;
  flex-direction: column;
  color: #ff03038a;
  transition: color 0.3s;
}

nav a.router-link-exact-active::after {
  display: inline-block;
  content: "";
  margin-top: 0.08em;
  width: 100%;
  height: 4px;
  border-radius: 2px;
  background-color: #ff03038a;
}

nav a.router-link-exact-active:hover {
  color: hsl(0, 0%, 100%);
}
</style>
