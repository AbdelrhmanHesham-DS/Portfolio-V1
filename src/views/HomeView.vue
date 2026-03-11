<template>
  <main
    class="mt-10 md:mt-1 flex flex-col-reverse gap-8 items-center md:flex-row md:gap-16 md:justify-center min-h-[65vh] md:min-h-[80vh] bg-[#0b0f1a]"
  >
    <div class="space-y-4 text-center md:text-left px-10">
      <p class="text-[#38bdf8] font-medium text-base md:text-lg tracking-widest uppercase fade-in-from-left">
        Hello World, I'm
      </p>

      <h1 class="text-4xl font-bold md:text-6xl text-white fadein-up">
        Abdelrhman Hesham
      </h1>

      <div class="py-2">
        <h1
          class="typewrite text-xl md:text-3xl font-semibold text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-[#38bdf8] fadein-up"
          ref="typewriter"
        >
          <span class="wrap">{{ txt }}</span>
        </h1>
      </div>

      <p class="text-slate-400 text-base md:text-lg max-w-lg fade-in-from-left leading-relaxed">
        Aspiring <span class="text-[#38bdf8] font-semibold">Data Scientist</span> dedicated to uncovering 
        meaningful insights from complex data. <span class="wave">📊</span>
      </p>

      <div class="pt-4 fadein-up">
        <router-link 
          to="/Projects" 
          class="px-6 py-3 rounded-full border border-[#38bdf8] text-[#38bdf8] hover:bg-[#38bdf8] hover:text-white transition-all duration-300 font-medium"
        >
          Explore My Projects
        </router-link>
      </div>
    </div>

    <div class="flex justify-center md:justify-start fadein-right">
      <div class="relative group">
        <div class="absolute -inset-1 bg-[#38bdf8] rounded-full blur opacity-25 group-hover:opacity-50 transition duration-1000"></div>
        <img 
          src="/img/me.jpg" 
          alt="Abdelrhman Hesham"
          class="relative w-40 h-40 sm:w-48 sm:h-48 md:w-56 md:h-56 lg:w-64 lg:h-64 object-cover rounded-full border-2 border-[#38bdf8] shadow-2xl transition-all duration-500 hover:scale-105"
        />
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      // Updated these to be Data Science focused
      toRotate: ["Data Scientist", "Machine Learning Specialist", "Python Developer", "Final Year Student"],
      period: 2000,
      txt: '',
      loopNum: 0,
      isDeleting: false,
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.tick();
    });
  },
  methods: {
    tick() {
      let typewriter = this.$refs.typewriter;
      if (!typewriter) return;

      let i = this.loopNum % this.toRotate.length;
      let fullTxt = this.toRotate[i];

      this.txt = this.isDeleting
        ? fullTxt.substring(0, this.txt.length - 1)
        : fullTxt.substring(0, this.txt.length + 1);

      typewriter.innerHTML = `<span class="wrap">${this.txt}</span>`;

      let that = this;
      let delta = 150 - Math.random() * 100; // Slightly faster typing
      if (this.isDeleting) delta /= 2;

      if (!this.isDeleting && this.txt === fullTxt) {
        delta = this.period;
        this.isDeleting = true;
      } else if (this.isDeleting && this.txt === '') {
        this.isDeleting = false;
        this.loopNum++;
        delta = 500;
      }

      setTimeout(() => that.tick(), delta);
    },
  }
}
</script>

<style scoped>
/* Scoped to keep it clean */
.typewrite > .wrap {
  border-right: 0.08em solid #38bdf8; /* Blue cursor */
}

.wave {
  animation-name: wave-animation;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
  display: inline-block;
}

@keyframes wave-animation {
  0%, 60%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(14deg); }
  20%, 40% { transform: rotate(-8deg); }
  50% { transform: rotate(10deg); }
}

/* Reusing your great animations */
.fadein-up {
  opacity: 0;
  animation: fadeInUp 0.8s ease-out forwards;
}

@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.fade-in-from-left {
  opacity: 0;
  animation: fadeInLeft 0.8s ease-out forwards;
}

@keyframes fadeInLeft {
  0% { opacity: 0; transform: translateX(-30px); }
  100% { opacity: 1; transform: translateX(0); }
}

.fadein-right {
  opacity: 0;
  animation: fadeInRight 0.8s ease-out forwards;
}

@keyframes fadeInRight {
  0% { opacity: 0; transform: translateX(30px); }
  100% { opacity: 1; transform: translateX(0); }
}
</style>