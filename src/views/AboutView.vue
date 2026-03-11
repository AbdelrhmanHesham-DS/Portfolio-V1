<template>
  <div class="bg-[#0b0f1a] px-5 py-10 md:px-12 md:py-16 text-left text-gray-200 mx-3 mb-5 rounded-3xl border border-[#1e293b]">
    <header>
      <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-6 flex items-center">
        About Me
        <div class="ml-4 h-[2px] w-32 md:w-60 bg-[#1e293b]"></div>
      </div>
    </header>

    <section class="flex flex-col md:flex-row gap-6 md:gap-12">
      <div class="flex justify-center md:justify-start">
        <img src="/img/me.jpg" class="w-40 h-40 object-cover rounded-full border-4 border-[#38bdf8]">
      </div>
      <div class="md:w-7/12 text-base md:text-lg text-slate-300">
        <p class="mb-5">
          Hi! I'm <strong class="text-white">Abdelrhman Hesham</strong>, a final-year Computer Science student at <strong class="text-white">Menoufia University</strong>.
        </p>
        <p>
          I specialize in <span class="text-[#38bdf8]">Data Science</span>, machine learning, and extracting insights from data using <strong>Python</strong>, statistics, and modern analytics tools.
        </p>
        <div class="mt-6">
          <a href="/img/cv/Abdelrhman_Hesham_CV.pdf" download class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition">
            Download CV
          </a>
          <div class="mt-6">
          <a href="/img/Certificates" download class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition">
            MyCertificates
          </a>
        </div>
      </div>
    </section>
  </div>

  <div class="px-5 py-12 md:px-12 text-gray-200 mx-3">
    <header>
      <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-10 flex items-center">
        My Data Science Workflow
        <div class="ml-4 h-[2px] w-24 md:w-40 bg-[#1e293b]"></div>
      </div>
    </header>
    

[Image of data science lifecycle]

    <div class="grid grid-cols-1 md:grid-cols-5 gap-6 text-center">
      <div class="workflow-card"><h3>Data Collection</h3><p>Gather datasets from APIs, databases, or scraping.</p></div>
      <div class="workflow-card"><h3>Data Cleaning</h3><p>Handle missing values and prepare the dataset.</p></div>
      <div class="workflow-card"><h3>Data Analysis</h3><p>Explore trends and patterns in the data.</p></div>
      <div class="workflow-card"><h3>Machine Learning</h3><p>Train predictive models using ML algorithms.</p></div>
      <div class="workflow-card"><h3>Deployment</h3><p>Deploy models or dashboards for real use.</p></div>
    </div>
  </div>

  <div class="px-5 py-10 md:px-12 md:py-16 text-left text-gray-200 mx-3">
    <header>
      <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-6 flex items-center">
        Technical Toolkit
        <div class="ml-4 h-[2px] w-20 md:w-32 bg-[#1e293b]"></div>
      </div>
    </header>
    <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
      <div v-for="skill in skills" :key="skill.id" class="bg-[#111827] border border-[#1e293b] rounded-xl p-4 flex items-center space-x-4 hover:border-[#38bdf8] transition">
        <img :src="skill.image" class="w-10 h-10">
        <div>
          <div class="text-white font-semibold">{{ skill.name }}</div>
          <div class="text-xs text-[#38bdf8]">{{ skill.level }}</div>
        </div>
      </div>
    </div>
  </div>

  <div class="px-5 py-10 md:px-12 text-gray-200 mx-3">
    <header>
      <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-10 flex items-center">
        Certificates
        <div class="ml-4 h-[2px] w-20 md:w-32 bg-[#1e293b]"></div>
      </div>
    </header>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div v-for="cert in certificates" :key="cert.id" class="bg-[#111827] border border-[#1e293b] p-4 rounded-2xl hover:border-[#38bdf8] transition">
        <img :src="cert.image" class="w-full h-40 object-cover rounded-lg mb-4">
        <h3 class="text-lg font-bold text-white">{{ cert.title }}</h3>
        <p class="text-slate-400 text-sm">{{ cert.issuer }} ({{ cert.date }})</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      skills: [
        { id: 1, name: "Python", image: "https://cdn-icons-png.flaticon.com/512/5968/5968350.png", level: "Advanced" },
        { id: 2, name: "SQL", image: "https://cdn-icons-png.flaticon.com/512/4248/4248443.png", level: "Intermediate" },
        { id: 3, name: "Pandas", image: "https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg", level: "Library" },
        { id: 4, name: "Scikit-Learn", image: "https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg", level: "ML Library" }
      ],
    };
  }
};
</script>

<style scoped>
.workflow-card { background: #111827; border: 1px solid #1e293b; border-radius: 12px; padding: 20px; transition: .3s; }
.workflow-card:hover { border-color: #38bdf8; transform: scale(1.05); }
.workflow-card h3 { color: #38bdf8; font-weight: 600; margin-bottom: 8px; }
.workflow-card p { color: #cbd5e1; font-size: 14px; }
</style>