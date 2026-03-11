<template>
  <section id="Contact" class="py-20 bg-[#0b0f1a] text-gray-200">
    <div class="container mx-auto px-4 md:px-6">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-5xl font-bold mb-4 text-white">
          Let's Decipher <span class="text-[#38bdf8]">Data Together</span>
        </h2>
        <p class="text-slate-400 max-w-2xl mx-auto text-lg">
          Whether you have a data-driven question or a complex project that needs insights, 
          I'm ready to collaborate. Drop a message below.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-start">
        
        <div class="bg-[#111827] p-8 rounded-2xl border border-[#1e293b] shadow-xl">
          <h3 class="text-xl font-semibold mb-8 text-[#38bdf8]">Contact Information</h3>
          
          <div class="space-y-8">
            <div class="flex items-center gap-5 group">
              <div class="p-4 bg-[#1e293b] rounded-xl text-[#38bdf8] group-hover:bg-[#38bdf8] group-hover:text-white transition-all">
                <Mail :size="24" />
              </div>
              <div>
                <h4 class="text-sm text-slate-500 font-medium uppercase tracking-wider">Email</h4>
                <a href="mailto:abdelrhman.hesham2093@gmail.com" class="text-lg hover:text-[#38bdf8] transition-colors">
                  abdelrhman.hesham2093@gmail.com
                </a>
              </div>
            </div>

            <div class="flex items-center gap-5 group">
              <div class="p-4 bg-[#1e293b] rounded-xl text-[#38bdf8] group-hover:bg-[#38bdf8] group-hover:text-white transition-all">
                <Phone :size="24" />
              </div>
              <div>
                <h4 class="text-sm text-slate-500 font-medium uppercase tracking-wider">Phone</h4>
                <a href="tel:+201066016826" class="text-lg hover:text-[#38bdf8] transition-colors">
                  +20 106 601 6826
                </a>
              </div>
            </div>

            <div class="flex items-center gap-5 group">
              <div class="p-4 bg-[#1e293b] rounded-xl text-[#38bdf8] group-hover:bg-[#38bdf8] group-hover:text-white transition-all">
                <MapPin :size="24" />
              </div>
              <div>
                <h4 class="text-sm text-slate-500 font-medium uppercase tracking-wider">Location</h4>
                <p class="text-lg">Giza, Egypt</p>
              </div>
            </div>
          </div>

          <div class="mt-12 pt-8 border-t border-[#1e293b]">
            <h3 class="text-sm font-semibold mb-6 text-slate-500 uppercase tracking-widest">Connect with me</h3>
            <div class="flex gap-4">
              <a v-for="link in socialLinks" :key="link.label" :href="link.url" target="_blank"
                class="w-11 h-11 flex items-center justify-center rounded-lg bg-[#1e293b] text-[#38bdf8] hover:bg-[#38bdf8] hover:text-white transition-all"
                :aria-label="link.label">
                <i :class="link.icon"></i>
              </a>
            </div>
          </div>
        </div>

        <div class="bg-[#111827] p-8 rounded-2xl border border-[#1e293b] shadow-xl">
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div class="grid grid-cols-1 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium mb-2 text-slate-300">Your Name</label>
                <input type="text" id="name" required
                  class="w-full px-4 py-3 bg-[#0b0f1a] text-white border border-[#1e293b] rounded-xl focus:border-[#38bdf8] focus:ring-1 focus:ring-[#38bdf8] outline-none transition-all placeholder:text-slate-600"
                  placeholder="John Doe" />
              </div>
              <div>
                <label for="email" class="block text-sm font-medium mb-2 text-slate-300">Your Email</label>
                <input type="email" id="email" required
                  class="w-full px-4 py-3 bg-[#0b0f1a] text-white border border-[#1e293b] rounded-xl focus:border-[#38bdf8] focus:ring-1 focus:ring-[#38bdf8] outline-none transition-all placeholder:text-slate-600"
                  placeholder="john@example.com" />
              </div>
            </div>

            <div>
              <label for="subject" class="block text-sm font-medium mb-2 text-slate-300">Project Type</label>
              <input type="text" id="subject" required
                class="w-full px-4 py-3 bg-[#0b0f1a] text-white border border-[#1e293b] rounded-xl focus:border-[#38bdf8] focus:ring-1 focus:ring-[#38bdf8] outline-none transition-all placeholder:text-slate-600"
                placeholder="Data Analysis / ML Model" />
            </div>

            <div>
              <label for="message" class="block text-sm font-medium mb-2 text-slate-300">Message</label>
              <textarea id="message" required rows="4"
                class="w-full px-4 py-3 bg-[#0b0f1a] text-white border border-[#1e293b] rounded-xl focus:border-[#38bdf8] focus:ring-1 focus:ring-[#38bdf8] outline-none transition-all placeholder:text-slate-600"
                placeholder="Briefly describe your goals..."></textarea>
            </div>

            <button type="submit"
              class="w-full py-4 rounded-xl bg-[#38bdf8] hover:bg-[#0ea5e9] text-[#0b0f1a] font-bold text-lg shadow-lg shadow-blue-500/20 transition-all flex items-center justify-center gap-2 group">
              Send Message
              <Send :size="20" class="group-hover:translate-x-1 group-hover:-translate-y-1 transition-transform" />
            </button>
          </form>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { Send, Mail, Phone, MapPin } from 'lucide-vue-next'
import { useRouter } from 'vue-router'

const router = useRouter()

const socialLinks = [
  { label: 'LinkedIn', url: 'https://www.linkedin.com/in/abdelrhman-hesham-ds/', icon: 'fab fa-linkedin-in' },
  { label: 'GitHub', url: 'https://github.com/AbdelrhmanHesham-DS', icon: 'fab fa-github' },
  { label: 'Instagram', url: 'https://www.instagram.com/abdo.h.28', icon: 'fab fa-instagram' },
  { label: 'Facebook', url: 'https://www.facebook.com/abdo.hesham.52438', icon: 'fab fa-facebook-f' }
]

function handleSubmit() {
  alert('Thank you! Your message has been sent successfully.')
  router.push('/')
}
</script>