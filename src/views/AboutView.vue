<template>

  <div class="space-y-16">

    <!-- ABOUT -->
    <section class="bg-[#0b0f1a] px-6 py-12 md:px-12 md:py-16 text-left text-gray-200 mx-3 rounded-3xl border border-[#1e293b]">

      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center">
          About Me
          <div class="ml-4 h-[2px] w-32 md:w-60 bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="flex flex-col md:flex-row gap-8 md:gap-12">

        <div class="flex justify-center md:justify-start">
          <img
            src="/img/me.jpg"
            class="w-40 h-40 object-cover rounded-full border-4 border-[#38bdf8]"
          />
        </div>

        <div class="md:w-7/12 text-base md:text-lg text-slate-300">

          <p class="mb-5">
            Hi! I'm
            <strong class="text-white">Abdelrhman Hesham</strong>,
            a final-year Computer Science student at
            <strong class="text-white">Menoufia University</strong>.
          </p>

          <p>
            I specialize in
            <span class="text-[#38bdf8]">Data Science</span>,
            machine learning, and extracting insights from data using
            <strong>Python</strong>, statistics, and modern analytics tools.
          </p>

          <div class="mt-6 flex gap-4 flex-wrap">

            <a
              href="/img/cv/Abdelrhman_Hesham_CV.pdf"
              download
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition"
            >
              Download CV
            </a>

            <a
              href="#certificates"
              class="border border-[#38bdf8] text-[#38bdf8] px-6 py-3 rounded-xl font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition"
            >
              My Certificates
            </a>

          </div>

        </div>

      </div>

    </section>


    <!-- WORKFLOW -->
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
          <p>Handle missing values and prepare the dataset.</p>
        </div>

        <div class="workflow-card">
          <h3>Data Analysis</h3>
          <p>Explore trends and patterns in the data.</p>
        </div>

        <div class="workflow-card">
          <h3>Machine Learning</h3>
          <p>Train predictive models using ML algorithms.</p>
        </div>

        <div class="workflow-card">
          <h3>Deployment</h3>
          <p>Deploy models or dashboards for real use.</p>
        </div>

      </div>

    </section>


    <!-- SKILLS -->
    <section class="px-6 md:px-12 text-gray-200 mx-3">

      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-8 flex items-center">
          Technical Toolkit
          <div class="ml-4 h-[2px] w-20 md:w-32 bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 md:grid-cols-4 gap-6 text-center">

        <div
          v-for="skill in skills"
          :key="skill.id"
          class="workflow-card flex flex-col items-center"
        >

          <img :src="skill.image" class="w-12 h-12 mb-3" />

          <h3 class="text-[#38bdf8] font-semibold text-lg">
            {{ skill.name }}
          </h3>

          <p class="text-slate-300 text-sm mt-1">
            {{ skill.level }}
          </p>

        </div>

      </div>

    </section>


    <!-- CERTIFICATES -->
    <section id="certificates" class="px-6 md:px-12 text-gray-200 mx-3 pb-10">

      <header>
        <div class="text-[#38bdf8] text-2xl md:text-3xl font-bold mb-10 flex items-center">
          Certificates
          <div class="ml-4 h-[2px] w-20 md:w-32 bg-[#1e293b]"></div>
        </div>
      </header>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

        <div
          v-for="cert in certificates"
          :key="cert.id"
          class="certificate-card"
        >

          <h3 class="text-lg font-bold text-white mb-2">
            {{ cert.title }}
          </h3>

          <p class="text-slate-400 text-sm mb-4">
            {{ cert.issuer }} ({{ cert.date }})
          </p>

          <a
            :href="cert.pdf"
            download
            class="inline-block border border-[#38bdf8] text-[#38bdf8] px-4 py-2 rounded-lg font-semibold hover:bg-[#38bdf8] hover:text-[#0b0f1a] transition"
          >
            Download Certificate
          </a>

        </div>

      </div>

    </section>

  </div>

</template>

<script>
export default {
  data() {
    return {

      skills: [
        {
          id: 1,
          name: "Python",
          image: "https://cdn-icons-png.flaticon.com/512/5968/5968350.png",
          level: "Advanced"
        },
        {
          id: 2,
          name: "SQL",
          image: "https://cdn-icons-png.flaticon.com/512/4248/4248443.png",
          level: "Intermediate"
        },
        {
          id: 3,
          name: "Pandas",
          image: "https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg",
          level: "Data Analysis Library"
        },
        {
          id: 4,
          name: "Scikit-Learn",
          image: "https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg",
          level: "Machine Learning Library"
        }
      ],

      certificates: [
        {
          id: 1,
          title: "Getting Started with Deep Learning",
          issuer: "NVIDIA",
          date: "August 2025",
          pdf: "/certificates/nvidia.pdf"
        },
        {
          id: 2,
          title: "Programming using Python (120 Hours)",
          issuer: "NTI & ITIDA",
          date: "July 2025",
          pdf: "/certificates/nti.pdf"
        },
        {
          id: 3,
          title: "CIB Summer Program - The Green Leap",
          issuer: "CIB & IFC",
          date: "July 2025",
          pdf: "/certificates/cib.pdf"
        },
        {
          id: 4,
          title: "Back-End Diploma (120 Hours)",
          issuer: "ARRAY Courses Center",
          date: "January 2025",
          pdf: "/certificates/array.pdf"
        }
      ]

    };
  }
};
</script>

<style scoped>

.workflow-card{
  background:#111827;
  border:1px solid #1e293b;
  border-radius:14px;
  padding:22px;
  transition:0.3s;
}

.workflow-card:hover{
  border-color:#38bdf8;
  transform:translateY(-6px);
}

.workflow-card h3{
  color:#38bdf8;
  font-weight:600;
  margin-bottom:8px;
}

.workflow-card p{
  color:#cbd5e1;
  font-size:14px;
}

.certificate-card{
  background:#111827;
  border:1px solid #1e293b;
  border-radius:16px;
  padding:22px;
  transition:0.3s;
}

.certificate-card:hover{
  border-color:#38bdf8;
  transform:translateY(-6px);
}

</style>