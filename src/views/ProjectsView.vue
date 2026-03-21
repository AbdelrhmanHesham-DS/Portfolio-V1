<template>
  <div class="px-5 py-5 md:px-12 md:py-10 text-left mx-3">
    <article>
      <header>
        <div class="text-2xl font-bold text-[#38bdf8] mb-10 fadein-bot flex items-center justify-center flex-col">
          <h4>Past Project Experience</h4>
          <h4 class="text-base font-normal text-slate-400">
            Explore the projects I've worked on so far
          </h4>
        </div>
      </header>

      <section>
        <div class="grid grid-cols-1 gap-6 pb-32 md:grid-cols-3 xl:grid-cols-3 fade-zoom-in items-stretch">
          
          <div v-for="item in items" :key="item.id" class="flex">
            <div
              class="item-card flex flex-col items-center gap-3 rounded-xl bg-[#111827] border border-[#1e293b] text-slate-300 px-5 py-5 transition-all duration-300 hover:border-[#38bdf8] w-full h-full">

              <div class="w-full">
                <img
                  :src="item.imageUrl"
                  alt="Project Image"
                  loading="lazy"
                  class="rounded-xl w-full shadow-lg aspect-video object-cover"
                />
              </div>

              <div class="w-full flex flex-col flex-1 gap-2 items-center text-sm md:text-base mt-3">
                
                <div class="font-semibold text-[#38bdf8] w-full text-center">
                  {{ item.name }}
                </div>

                <div class="w-full text-left text-sm text-slate-400 flex-1">
                  {{ item.status }}
                </div>

                <div class="w-full mt-auto">
                  <div class="text-left text-xs text-[#38bdf8] mb-3">
                    {{ item.d3ff4ult }}
                  </div>

                  <div class="flex justify-end gap-3 pt-3 border-t border-slate-800">
                    <a
                      v-if="item.github !== 'null'"
                      :href="item.github"
                      target="_blank"
                      rel="noreferrer"
                      title="View GitHub repository"
                      class="text-slate-400 hover:text-[#38bdf8] transition-colors"
                    >
                      <svg xmlns="http://www.w3.org/2000/svg" stroke="currentColor" fill="none" stroke-width="2"
                        viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="18" width="18">
                        <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61
                          c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77
                          A5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38
                          13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07
                          0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42
                          3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22">
                        </path>
                      </svg>
                    </a>

                    <a
                      v-if="item.demo !== 'null'"
                      :href="item.demo"
                      target="_blank"
                      rel="noreferrer"
                      title="View finished project"
                      class="text-slate-400 hover:text-[#38bdf8] transition-colors"
                    >
                      <svg xmlns="http://www.w3.org/2000/svg" stroke="currentColor" fill="none" stroke-width="2"
                        viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="18" width="18">
                        <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6" />
                        <polyline points="15 3 21 3 21 9" />
                        <line x1="10" y1="14" x2="21" y2="3" />
                      </svg>
                    </a>
                  </div>
                </div>

              </div>
            </div>
          </div>

        </div>
      </section>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          id: 1,
          name: 'Personal Portfolio',
          imageUrl: '/img/projects/mysite.jpg',
          status: 'A modern portfolio where I showcase my skills, projects, and learning journey in Data Science.',
          d3ff4ult: 'Vue.js, Tailwind CSS',
          github: 'https://github.com/d3ff4ult/Portfolio-V1.git',
          demo: 'https://portfolio-v1-cj9u.vercel.app/',
        },
        {
          id: 2,
          name: 'Chatbot Project',
          imageUrl: '/img/projects/cohere.jpg',
          status: 'A chatbot application that can answer questions and interact intelligently with users.',
          d3ff4ult: 'Python',
          github: 'https://github.com/AbdelrhmanHesham-DS/Chatbot',
          demo: 'null',
        },
        {
          id: 3,
          name: 'RAG Chatbot',
          imageUrl: '/img/projects/rag.jpg',
          status: 'A Retrieval-Augmented Generation (RAG) chatbot that leverages documents for intelligent responses.',
          d3ff4ult: 'Python',
          github: 'https://github.com/AbdelrhmanHesham-DS/Rag-chatbot',
          demo: 'null',
        },
      ],
    };
  },
};
</script>

<style scoped>
.item-card {
  /* Added backface-visibility to keep text sharp during scale transitions */
  backface-visibility: hidden;
}

.item-card:hover {
  transform: translateY(-8px);
}

.fade-zoom-in {
  animation: fadeZoomIn 0.9s ease-in-out;
}

@keyframes fadeZoomIn {
  0% {
    opacity: 0;
    transform: scale(0.85);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
</style>