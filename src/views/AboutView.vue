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
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition"
            >
              Download CV
            </a>
            <button
              @click="openPreview('/img/cv/Abdelrhman_Hesham_CV.pdf')"
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition"
            >
              Preview CV
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- CERTIFICATES GRID -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center gap-4">
          Certificates
          <div class="flex-1 h-[2px] bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6">
        <div
          v-for="cert in certificates"
          :key="cert.file"
          class="workflow-card flex flex-col justify-between p-6"
        >
          <div class="mb-4">
            <h3 class="text-lg font-semibold text-white mb-1">{{ cert.name }}</h3>
            <p class="text-slate-400 text-sm">{{ cert.issuer }} | {{ cert.date }}</p>
          </div>
          <div class="flex gap-2 mt-4">
            <a
              :href="`/img/certificates/${cert.file}`"
              download
              class="border border-[#38bdf8] text-[#38bdf8] px-3 py-2 rounded font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition text-sm text-center flex-1"
            >
              Download
            </a>
            <button
              @click="openPreview(`/img/certificates/${cert.file}`)"
              class="border border-[#38bdf8] text-[#38bdf8] px-3 py-2 rounded font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition text-sm text-center flex-1"
            >
              Preview
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- DATA SCIENCE WORKFLOW GRID -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-10 flex items-center">
          My Data Science Workflow
          <div class="ml-4 h-[2px] w-24 md:w-40 bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-5 gap-6 text-center">
        <div v-for="step in workflow" :key="step.title" class="workflow-card p-6">
          <h3 class="text-[#38bdf8] font-semibold text-lg mb-2">{{ step.title }}</h3>
          <p class="text-slate-300 text-sm">{{ step.description }}</p>
        </div>
      </div>
    </section>

    <!-- TECHNICAL TOOLKIT GRID -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">
      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center gap-4">
          Technical Toolkit
          <div class="flex-1 h-[2px] bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6 text-center">
        <div v-for="tool in toolkit" :key="tool.name" class="workflow-card flex flex-col items-center p-6">
          <img :src="tool.icon" class="w-12 h-12 mb-3" />
          <h3 class="text-[#38bdf8] font-semibold text-lg">{{ tool.name }}</h3>
          <p class="text-slate-300 text-sm mt-1">{{ tool.level }}</p>
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
      ],
      workflow: [
        { title: "Data Collection", description: "Gather datasets from APIs, databases, or scraping." },
        { title: "Data Cleaning", description: "Handle missing values and prepare datasets." },
        { title: "Data Analysis", description: "Explore trends and patterns." },
        { title: "Machine Learning", description: "Train predictive models." },
        { title: "Deployment", description: "Deploy models or dashboards." },
      ],
      toolkit: [
        { name: "Python", icon: "https://cdn-icons-png.flaticon.com/512/5968/5968350.png", level: "Advanced" },
        { name: "SQL", icon: "https://cdn-icons-png.flaticon.com/512/4248/4248443.png", level: "Intermediate" },
        { name: "Pandas", icon: "https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg", level: "Data Analysis Library" },
        { name: "Scikit-Learn", icon: "https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg", level: "Machine Learning Library" },
      ],
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