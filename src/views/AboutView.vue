<template>
  <div class="space-y-16">

    <!-- ABOUT ME -->
    <section class="bg-[#0b0f1a] px-6 py-12 md:px-12 md:py-16 text-left text-gray-200 mx-3 rounded-3xl border border-[#1e293b]">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center">
          About Me
          <div class="ml-4 h-[2px] w-32 md:w-60 bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="flex flex-col md:flex-row gap-8 md:gap-12">
        <div class="flex justify-center md:justify-start">
          <img src="/img/me.jpg" class="w-40 h-40 object-cover rounded-full border-4 border-[#38bdf8]" />
        </div>

        <div class="md:w-7/12 text-base md:text-lg text-slate-300">
          <p class="mb-5">
            Hi! I'm <strong class="text-white">Abdelrhman Hesham</strong>, a final-year Computer Science student at <strong class="text-white">Menoufia University</strong>.
          </p>
          <p>
            I specialize in <span class="text-[#38bdf8]">Data Science</span>, machine learning, and extracting insights from data using <strong>Python</strong>.
          </p>

          <div class="mt-6 flex gap-4 flex-wrap">
            <a
              href="/img/cv/Abdelrhman_Hesham_CV.pdf"
              download
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition flex items-center gap-2"
            >
              <span>Download CV</span>
              <img src="https://cdn-icons-png.flaticon.com/512/337/337946.png" class="w-5 h-5" />
            </a>
            <button
              @click="openPreview('/img/cv/Abdelrhman_Hesham_CV.pdf')"
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition flex items-center gap-2"
            >
              <span>Preview CV</span>
              <img src="https://cdn-icons-png.flaticon.com/512/337/337946.png" class="w-5 h-5" />
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- CERTIFICATES SECTION -->
    <section class="bg-[#0b0f1a] px-6 py-12 md:px-12 md:py-16 text-gray-200 mx-3 rounded-3xl border border-[#1e293b]">
      <header class="mb-8">
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold flex items-center gap-4">
          Certificates
          <div class="flex-1 h-[2px] bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <div
          v-for="cert in certificates"
          :key="cert.file"
          class="bg-[#111827] rounded-2xl p-6 border border-[#1e293b] flex flex-col justify-between"
        >
          <div class="mb-4">
            <h3 class="text-xl font-bold text-white mb-2">{{ cert.name }}</h3>
            <p class="text-slate-400">{{ cert.issuer }} | {{ cert.date }}</p>
          </div>
          <div class="flex gap-4 flex-wrap mt-4">
            <a
              :href="`/img/cer/${cert.file}`"
              download
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition flex items-center gap-2"
            >
              <span>Download</span>
              <img src="https://cdn-icons-png.flaticon.com/512/337/337946.png" class="w-5 h-5" />
            </a>
            <button
              @click="openPreview(`/img/cer/${cert.file}`)"
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition flex items-center gap-2"
            >
              <span>Preview</span>
              <img src="https://cdn-icons-png.flaticon.com/512/337/337946.png" class="w-5 h-5" />
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- DATA SCIENCE WORKFLOW -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-10 flex items-center">
          My Data Science Workflow
          <div class="ml-4 h-[2px] w-24 md:w-40 bg-[#1e293b]"></div>
        </div>
      </header>
      <div class="grid grid-cols-1 md:grid-cols-5 gap-6 text-center">
        <div class="workflow-card">
          <h3>Data Collection</h3>
          <p>Gather datasets from APIs, databases, or scraping.</p>
        </div>
        <div class="workflow-card">
          <h3>Data Cleaning</h3>
          <p>Handle missing values and prepare datasets.</p>
        </div>
        <div class="workflow-card">
          <h3>Data Analysis</h3>
          <p>Explore trends and patterns.</p>
        </div>
        <div class="workflow-card">
          <h3>Machine Learning</h3>
          <p>Train predictive models.</p>
        </div>
        <div class="workflow-card">
          <h3>Deployment</h3>
          <p>Deploy models or dashboards.</p>
        </div>
      </div>
    </section>

    <!-- TECHNICAL TOOLKIT -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center gap-4">
          Technical Toolkit
          <div class="flex-1 h-[2px] bg-[#1e293b]"></div>
        </div>
      </header>
      <div class="grid grid-cols-1 md:grid-cols-4 gap-6 text-center">
        <div class="workflow-card flex flex-col items-center">
          <img src="https://cdn-icons-png.flaticon.com/512/5968/5968350.png" class="w-12 h-12 mb-3" />
          <h3 class="text-[#38bdf8] font-semibold text-lg">Python</h3>
          <p class="text-slate-300 text-sm mt-1">Advanced</p>
        </div>
        <div class="workflow-card flex flex-col items-center">
          <img src="https://cdn-icons-png.flaticon.com/512/4248/4248443.png" class="w-12 h-12 mb-3" />
          <h3 class="text-[#38bdf8] font-semibold text-lg">SQL</h3>
          <p class="text-slate-300 text-sm mt-1">Intermediate</p>
        </div>
        <div class="workflow-card flex flex-col items-center">
          <img src="https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg" class="w-12 h-12 mb-3" />
          <h3 class="text-[#38bdf8] font-semibold text-lg">Pandas</h3>
          <p class="text-slate-300 text-sm mt-1">Data Analysis Library</p>
        </div>
        <div class="workflow-card flex flex-col items-center">
          <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" class="w-12 h-12 mb-3" />
          <h3 class="text-[#38bdf8] font-semibold text-lg">Scikit-Learn</h3>
          <p class="text-slate-300 text-sm mt-1">Machine Learning Library</p>
        </div>
      </div>
    </section>

    <!-- PREVIEW MODAL -->
    <div v-if="previewFile" class="fixed inset-0 bg-black/80 flex items-center justify-center z-50 p-4">
      <div class="bg-[#0b0f1a] w-full max-w-5xl h-[90vh] rounded-xl border border-[#1e293b] relative overflow-hidden">
        <button
          @click="previewFile=null"
          class="absolute top-4 right-6 text-white text-2xl hover:text-[#38bdf8] transition z-10"
        >
          ✕
        </button>
        <iframe :src="previewFile" class="w-full h-full rounded-xl"></iframe>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      previewFile: null,
      certificates: [
        { name: "Getting Started with Deep Learning", issuer: "NVIDIA", date: "August 2025", file: "nvidia.pdf" },
        { name: "Programming using Python (120 Hours)", issuer: "NTI & ITIDA", date: "July 2025", file: "nti.pdf" },
        { name: "CIB Summer Program - The Green Leap", issuer: "CIB & IFC", date: "July 2025", file: "cib.pdf" },
        { name: "Back-End Diploma (120 Hours)", issuer: "ARRAY Courses Center", date: "January 2025", file: "array.pdf" },
      ]
    }
  },
  methods: {
    openPreview(file) {
      this.previewFile = file;
    }
  }
}
</script>

<style scoped>
.workflow-card {
  background: #111827;
  border: 1px solid #1e293b;
  border-radius: 14px;
  padding: 22px;
  transition: 0.3s;
}
.workflow-card:hover {
  border-color: #38bdf8;
  transform: translateY(-6px);
}
.workflow-card h3 {
  color: #38bdf8;
  font-weight: 600;
  margin-bottom: 8px;
}
.workflow-card p {
  color: #cbd5e1;
  font-size: 14px;
}
</style>