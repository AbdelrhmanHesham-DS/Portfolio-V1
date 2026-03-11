<template>
  <div class="min-h-screen flex flex-col bg-[#0b0f1a]">

    <!-- NAVBAR -->
    <nav
      :class="[
        'fixed top-0 z-[98] w-full transition-all duration-300',
        isScrolled
          ? 'backdrop-blur-md bg-[#0b0f1a]/95 border-b border-[#1e293b] shadow-lg'
          : 'backdrop-blur-md bg-[#0b0f1a]/90 border-b border-[#1e293b]'
      ]"
    >

      <div class="max-w-7xl mx-auto px-5 flex items-center justify-between py-4">

        <!-- Logo -->
        <button @click="redirectToHome">
          <span class="text-xl font-bold text-[#38bdf8] hover:text-white transition">
            Abdelrhman Hesham
          </span>
        </button>

        <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-6 text-sm font-medium">
          <router-link to="/" class="nav-link">Home</router-link>
          <router-link to="/about" class="nav-link">About</router-link>
          <router-link to="/projects" class="nav-link">Projects</router-link>
          <router-link to="/contact" class="nav-link">Contact</router-link>
        </div>

        <!-- Mobile Button -->
        <button
          @click="toggleMobileMenu"
          class="md:hidden p-2 rounded-lg text-gray-300 hover:text-white hover:bg-slate-800 transition"
        >

          <!-- Close -->
          <svg v-if="isMobileMenuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M6 18L18 6M6 6l12 12"/>
          </svg>

          <!-- Menu -->
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"/>
          </svg>

        </button>

      </div>

      <!-- Mobile Menu -->
      <div
        :class="[
          'md:hidden transition-all duration-300',
          isMobileMenuOpen
            ? 'max-h-80 opacity-100'
            : 'max-h-0 opacity-0 overflow-hidden'
        ]"
      >
        <div class="px-4 pt-2 pb-4 space-y-2 bg-[#0b0f1a] border-t border-[#1e293b]">
          <router-link to="/" @click="closeMobileMenu" class="mobile-nav-link">Home</router-link>
          <router-link to="/about" @click="closeMobileMenu" class="mobile-nav-link">About</router-link>
          <router-link to="/projects" @click="closeMobileMenu" class="mobile-nav-link">Projects</router-link>
          <router-link to="/contact" @click="closeMobileMenu" class="mobile-nav-link">Contact</router-link>
        </div>
      </div>

    </nav>


    <!-- Overlay -->
    <div
      v-if="isMobileMenuOpen"
      @click="closeMobileMenu"
      class="fixed inset-0 z-40 bg-black bg-opacity-50 md:hidden"
    ></div>


    <!-- MAIN CONTENT -->
    <main class="flex-1 pt-[100px]">

      <div class="max-w-7xl mx-auto px-5">
        <router-view/>
      </div>

    </main>


    <!-- FOOTER -->
    <footer class="bg-[#0b0f1a] border-t border-[#1e293b] text-gray-300 py-10 px-6">

      <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-8 text-sm">

        <!-- Info -->
        <div>
          <h2 class="text-lg font-semibold text-[#38bdf8] mb-3">Information</h2>
          <p>
            Data Scientist crafting modern insights through data analysis
            and machine learning.
          </p>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-[#38bdf8] font-semibold mb-2">Quick Links</h3>
          <ul class="space-y-1">
            <li><router-link to="/" class="hover:text-white">Home</router-link></li>
            <li><router-link to="/about" class="hover:text-white">About</router-link></li>
            <li><router-link to="/projects" class="hover:text-white">Projects</router-link></li>
          </ul>
        </div>

        <!-- Contact -->
        <div>
          <h3 class="text-[#38bdf8] font-semibold mb-2">Contact Info</h3>
          <ul class="space-y-1">
            <li>Email: <a href="mailto:abdelrhman.hesham2093@gmail.com">abdelrhman.hesham2093@gmail.com</a></li>
            <li>Phone: <a href="tel:+201066016826">+20 106 601 6826</a></li>
            <li>Location: Giza, Egypt</li>
          </ul>
        </div>

      </div>


      <!-- Social -->
      <div class="flex justify-center gap-4 mt-8">

        <a
          v-for="social in socialLinks"
          :key="social.label"
          :href="social.url"
          target="_blank"
          class="w-10 h-10 flex items-center justify-center rounded-full bg-[#1e293b] text-[#38bdf8] hover:bg-[#38bdf8] hover:text-white transition"
        >
          <i :class="social.icon"></i>
        </a>

      </div>


      <!-- Copyright -->
      <div class="mt-6 text-center text-gray-500 text-xs">
        © {{ currentYear }} Abdelrhman Hesham — All rights reserved.
      </div>

    </footer>

  </div>
</template>


<script>
export default {

  data() {
    return {

      isMobileMenuOpen: false,
      isScrolled: false,
      currentYear: new Date().getFullYear(),

      socialLinks: [
        { label: "LinkedIn", url: "https://www.linkedin.com/in/abdelrhman-hesham-ds", icon: "fab fa-linkedin-in" },
        { label: "GitHub", url: "https://github.com/d3ff4ult", icon: "fab fa-github" },
        { label: "Instagram", url: "https://www.instagram.com/abdo.h.28", icon: "fab fa-instagram" },
        { label: "Facebook", url: "https://www.facebook.com/abdo.hesham.52438", icon: "fab fa-facebook-f" }
      ]

    }
  },


  methods: {

    redirectToHome() {
      this.$router.push("/")
    },

    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen
    },

    closeMobileMenu() {
      this.isMobileMenuOpen = false
    },

    handleScroll() {
      this.isScrolled = window.scrollY > 20
    }

  },


  mounted() {
    window.addEventListener("scroll", this.handleScroll)
  },


  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll)
  }

}
</script>


<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

body{
  font-family:'Poppins',sans-serif;
  background:#0b0f1a;
  color:#cbd5e1;
  margin:0;
}


/* Scrollbar */

::-webkit-scrollbar{
  width:6px;
}

::-webkit-scrollbar-track{
  background:#0b0f1a;
}

::-webkit-scrollbar-thumb{
  background:#38bdf8;
  border-radius:10px;
}


/* Navigation */

.nav-link{
  @apply text-gray-400 hover:text-[#38bdf8] transition relative;
}

.nav-link::after{
  content:'';
  @apply absolute bottom-[-4px] left-0 w-0 h-0.5 bg-[#38bdf8] transition-all duration-300;
}

.nav-link.router-link-exact-active{
  @apply text-[#38bdf8];
}

.nav-link.router-link-exact-active::after{
  @apply w-full;
}

.mobile-nav-link{
  @apply block px-4 py-3 text-gray-300 hover:text-[#38bdf8] hover:bg-slate-800 rounded-lg transition;
}

h1,h2,h3{
  color:#f8fafc;
}

</style>