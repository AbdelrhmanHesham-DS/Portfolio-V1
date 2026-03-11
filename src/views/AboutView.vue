<template>
  <div class="bg-[#1a1a1a] px-5 py-10 md:px-12 md:py-16 text-left text-gray-200 mx-3 mb-5 rounded-3xl border border-[#2e2e2e]">
    <article>
      <!-- About Section -->
      <header>
        <div class="text-[#ff3b3b] text-2xl md:text-3xl font-bold mb-6 flex items-center">
          About Me
          <div class="ml-4 h-[2px] w-32 md:w-60 bg-[#444]"></div>
        </div>
      </header>

      <section class="flex flex-col md:flex-row gap-6 md:gap-12">
        <div class="flex justify-center md:justify-start">
          <img
            src="/img/me.jpg"
            alt="My Avatar"
            class="w-32 h-32 sm:w-40 sm:h-40 md:w-48 md:h-48 lg:w-56 lg:h-56 object-cover rounded-full border-4 border-[#ff3b3b] shadow-lg transition-all duration-300 hover:scale-105"
          />
        </div>

        <div class="md:w-7/12 text-base md:text-lg leading-relaxed">
          <p class="mb-5">
            Hi everyone! My name is <strong class="text-white">Abdelrhman Hesham</strong>. I'm a student at Menofia
            University (MU), studying in the Faculty of Computer and Information, Computer Science Department.
          </p>
          <p>
            My job is to build your project to be functional and user-friendly yet still attractive. I provide a
            personal touch to your project and ensure that it catches attention and is easy to use.
            My goal is to convey your message and identity in the most creative way. You can contact me through my
            social media accounts.
          </p>
        </div>
      </section>
    </article>
  </div>

  <div class="px-5 py-10 md:px-12 md:py-16 text-left text-gray-200 mx-3">
    <article>
      <!-- Skills Section -->
      <header>
        <div class="text-[#ff3b3b] text-2xl md:text-3xl font-bold mb-6 flex items-center">
          Skills
          <div class="ml-4 h-[2px] w-20 md:w-32 bg-[#444]"></div>
        </div>
      </header>

      <div>
        <ul class="flex space-x-4 text-sm md:text-base font-medium mb-6">
          <li>
            <button
              class="px-4 py-2 rounded-md transition duration-300"
              :class="{
                'text-[#ff3b3b] bg-[#1a1a1a] border border-[#ff3b3b]': activeTab === 1,
                'text-gray-400 hover:text-[#ff3b3b] hover:bg-[#2a2a2a]': activeTab !== 1
              }"
              @click="activeTab = 1"
            >
              Skills
            </button>
          </li>
          <li>
            <button
              class="px-4 py-2 rounded-md transition duration-300"
              :class="{
                'text-[#ff3b3b] bg-[#1a1a1a] border border-[#ff3b3b]': activeTab === 2,
                'text-gray-400 hover:text-[#ff3b3b] hover:bg-[#2a2a2a]': activeTab !== 2
              }"
              @click="activeTab = 2"
            >
              Tools
            </button>
          </li>
        </ul>
      </div>

      <div v-show="activeTab === 1">
        <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-6">
          <div v-for="item in d3ff4ult" :key="item.id" class="bg-[#1f1f1f] border border-[#ff3b3b] rounded-md p-4 flex items-center space-x-4 hover:bg-[#2a2a2a] transition">
            <img :src="item.imageUrl" alt="Skill" class="w-12 h-12 object-contain" />
            <div>
              <div class="text-white font-semibold">{{ item.name }}</div>
              <div class="text-xs text-[#ff3b3b]">{{ item.status }}</div>
            </div>
          </div>
        </div>
      </div>

      <div v-show="activeTab === 2">
        <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-6">
          <div v-for="item in tools" :key="item.id" class="bg-[#1f1f1f] border border-[#ff3b3b] rounded-md p-4 flex items-center space-x-4 hover:bg-[#2a2a2a] transition">
            <img :src="item.imageUrl" alt="Tool" class="w-12 h-12 object-contain" />
            <div>
              <div class="text-white font-semibold">{{ item.name }}</div>
              <div class="text-xs text-[#ff3b3b]">{{ item.status }}</div>
            </div>
          </div>
        </div>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 1,
      d3ff4ult: [
        { id: 1, name: 'HTML', imageUrl: 'https://cdn-icons-png.flaticon.com/512/1051/1051277.png', status: 'Intermediate' },
        { id: 2, name: 'CSS', imageUrl: 'https://cdn-icons-png.flaticon.com/512/732/732190.png', status: 'Beginner' },
        { id: 3, name: 'PHP', imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-php-2038871-1720084.png', status: 'Intermediate' },
        { id: 4, name: 'Laravel', imageUrl: 'https://cdn.worldvectorlogo.com/logos/laravel-2.svg', status: 'Intermediate' }
      ],
      tools: [
        { id: 1, name: 'Git', imageUrl: 'https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png', status: 'Version Control' },
        { id: 2, name: 'GitHub', imageUrl: 'https://cdn-icons-png.flaticon.com/512/25/25231.png', status: 'Git Hosting' },
        { id: 3, name: 'NPM', imageUrl: 'https://cdn.iconscout.com/icon/free/png-256/free-npm-3-1175132.png', status: 'Package Manager' },
        { id: 4, name: 'MySQL', imageUrl: 'https://cdn-icons-png.flaticon.com/512/5968/5968313.png', status: 'Database' }
      ]
    };
  }
};
</script>

<style scoped>
body {
  font-family: 'Poppins', sans-serif;
  background-color: #121212;
  color: #e0e0e0;
  line-height: 1.75;
}
</style>
