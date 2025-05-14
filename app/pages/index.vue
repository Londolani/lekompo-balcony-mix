<script setup lang="ts">
import NavBar from '~/components/NavBar.vue'
import { ref, onMounted } from 'vue'

// Add animations with intersection observer
onMounted(() => {
  updateCountdown()
  setInterval(updateCountdown, 1000)
  
  // Add animation on scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fade-in')
        observer.unobserve(entry.target)
      }
    })
  }, { threshold: 0.1 })
  
  document.querySelectorAll('.animate-on-scroll').forEach(el => {
    observer.observe(el)
  })
})

const activeTab = ref(0)
const musicTab = ref(0)
const activeFaq = ref<number | null>(null)

// Countdown logic for Next Event: 25 May 2025 · Meropa Casino
const countdown = ref<{
  days: string | number;
  hours: string | number;
  minutes: string | number;
  seconds: string | number;
}>({ days: '--', hours: '--', minutes: '--', seconds: '--' })
const targetDate = new Date('2025-05-25T00:00:00')
function updateCountdown() {
  const now = Date.now()
  const diff = targetDate.getTime() - now
  if (diff <= 0) return
  countdown.value = {
    days: Math.floor(diff / (1000 * 60 * 60 * 24)),
    hours: Math.floor((diff / (1000 * 60 * 60)) % 24),
    minutes: Math.floor((diff / (1000 * 60)) % 60),
    seconds: Math.floor((diff / 1000) % 60)
  }
}

// For tabs navigation across the site
const sections = ['Artists', 'About', 'Vision', 'Mission', 'Past Events']
const activePage = ref('Artists')

// Artists data
const artists = [
  { name: 'Shebeshxt', photo:  'images/a1.jpg', topTrack: { name: 'Ambulance', embed: '3ma6tT5grA0NMud8I4oRmH' } }, 
  { name: 'Kharishma', photo: 'images/a2.jpeg', topTrack: { name: 'Chokeslem', embed: '5QUe8XDF5536t4H0aRdt01' } },
  { name: 'Naqua SA', photo: 'images/a3.jpeg', topTrack: { name: 'Sekoloto', embed: '4ZBGTuegA9imRSv755wQVe' } }
]
</script>

<template>
  <div class="bg-black text-white min-h-screen font-sans">
    <NavBar />

    <!-- Hero Section - Redesigned Background -->
    <section id="hero" class="min-h-screen flex flex-col justify-center container mx-auto px-4 text-center pt-20 pb-16 relative animate-on-scroll overflow-hidden">
      <!-- New creative background -->
      <div class="absolute top-0 left-0 right-0 bottom-0 bg-[radial-gradient(circle,rgba(80,20,20,0.2)_0%,rgba(0,0,0,1)_70%)]"></div>
      <div class="absolute -top-[400px] -left-[400px] w-[800px] h-[800px] rounded-full bg-red-900/10 blur-3xl"></div>
      <div class="absolute -bottom-[300px] -right-[300px] w-[600px] h-[600px] rounded-full bg-yellow-800/10 blur-3xl"></div>
      
      <!-- Content with higher z-index -->
      <div class="relative z-10">
        <h1 class="text-6xl md:text-7xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-red-500 to-yellow-400 mb-6">Lekompō Balcony Mix</h1>
        <img src="@/assets/images/logo.jpg" alt="" class="w-64 mx-auto mb-8 rounded-lg shadow-2xl transform hover:scale-105 transition-transform duration-500 ring-4 ring-red-600/50">
        <p class="text-2xl mb-2 text-gray-200 font-medium">Next Event: Lekompo Balcony mix 6</p>
        <p class="text-xl mb-2 text-gray-300">25 May 2025</p>
        <p class="text-xl mb-10 text-gray-300">Meropa Casino, Polokwane</p>
        
        <!-- Enhanced countdown -->
        <div class="flex justify-center space-x-6 mb-12">
          <div class="w-24 h-24 rounded-2xl bg-gradient-to-br from-red-900 to-red-600 flex flex-col justify-center items-center shadow-[0_0_25px_rgba(185,28,28,0.3)] transition-transform hover:scale-105 duration-300">
            <div class="text-4xl font-bold text-white">{{ countdown.days }}</div>
            <div class="text-xs uppercase tracking-wider text-gray-100">Days</div>
          </div>
          <div class="w-24 h-24 rounded-2xl bg-gradient-to-br from-red-900 to-red-600 flex flex-col justify-center items-center shadow-[0_0_25px_rgba(185,28,28,0.3)] transition-transform hover:scale-105 duration-300">
            <div class="text-4xl font-bold text-white">{{ countdown.hours }}</div>
            <div class="text-xs uppercase tracking-wider text-gray-100">Hours</div>
          </div>
          <div class="w-24 h-24 rounded-2xl bg-gradient-to-br from-red-900 to-red-600 flex flex-col justify-center items-center shadow-[0_0_25px_rgba(185,28,28,0.3)] transition-transform hover:scale-105 duration-300">
            <div class="text-4xl font-bold text-white">{{ countdown.minutes }}</div>
            <div class="text-xs uppercase tracking-wider text-gray-100">Mins</div>
          </div>
          <div class="w-24 h-24 rounded-2xl bg-gradient-to-br from-red-900 to-red-600 flex flex-col justify-center items-center shadow-[0_0_25px_rgba(185,28,28,0.3)] transition-transform hover:scale-105 duration-300 animate-pulse">
            <div class="text-4xl font-bold text-white">{{ countdown.seconds }}</div>
            <div class="text-xs uppercase tracking-wider text-gray-100">Secs</div>
          </div>
        </div>
        
        <!-- Enhanced buttons -->
        <div class="space-x-6">
          <a href="https://www.howler.co.za/events/lekompo-mix-6-with-shebeshxt-kharishma-naqua-adb1" class="px-8 py-4 bg-gradient-to-r from-yellow-500 to-yellow-700 text-white rounded-full hover:from-yellow-600 hover:to-yellow-800 transition-all duration-300 font-medium shadow-lg hover:shadow-yellow-500/30 transform hover:-translate-y-1" target="_blank">Get Tickets</a>
          <a href="#content" class="px-8 py-4 bg-gradient-to-r from-red-700 to-red-900 text-white rounded-full hover:from-red-800 hover:to-red-950 transition-all duration-300 font-medium shadow-lg hover:shadow-red-500/30 transform hover:-translate-y-1">Learn More</a>
        </div>
      </div>
    </section>

    

   <!-- Artists Section - Cleaner Background -->
   <section id="artists" class="py-32 relative overflow-hidden animate-on-scroll">
      <!-- Simplified background -->
      <div class="absolute inset-0 bg-gradient-to-b from-black to-black/90 z-0"></div>
      
      <div class="container mx-auto px-4 relative z-10">
        <h2 class="text-5xl md:text-6xl font-black text-center mb-20 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-red-500 to-yellow-400">Featured Artists</h2>
        
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-12">
          <div v-for="artist in artists" :key="artist.name" class="group bg-black/30 backdrop-blur-sm p-8 rounded-xl border border-red-900/20 hover:border-red-500/30 transition-all duration-300 shadow-lg hover:shadow-red-500/10">
            <div class="relative mb-8">
              <!-- Glow effect -->
              <div class="absolute inset-0 rounded-full bg-gradient-to-br from-red-500/40 to-yellow-500/40 blur-xl opacity-70 group-hover:opacity-100 transition-opacity duration-500 scale-110"></div>
              
              <!-- Image wrapper -->
              <div class="relative p-1  bg-gradient-to-br from-red-500 via-red-600 to-yellow-500">
                <img :src="artist.photo" :alt="artist.name" class="w-full aspect-square object-cover ">
              </div>
            </div>
            
            <h3 class="text-2xl font-bold mb-2 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">{{ artist.name }}</h3>
            <p class="text-gray-300 mb-4">Top Track: {{ artist.topTrack.name }}</p>
            <div class="rounded-xl p-0.5 bg-gradient-to-r from-red-600 to-yellow-600">
              <div class="bg-gray-900 rounded-lg p-1">
                <iframe :src="`https://open.spotify.com/embed/track/${artist.topTrack.embed}`" width="100%" height="80" frameborder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" class="rounded-lg"></iframe>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>


    <!-- About, Vision & Mission as Tabs -->
    <section id="about" class="py-24 relative animate-on-scroll">
      <div class="container mx-auto px-6">
        <!-- Tab navigation -->
        <div class="flex justify-center mb-12">
          <div class="inline-flex rounded-lg border border-red-900/30 backdrop-blur-sm p-1 bg-black/20">
            <button 
              v-for="(tab, index) in ['About', 'Vision', 'Mission']" 
              :key="tab" 
              @click="activeTab = index"
              :class="[
                'px-6 py-3 text-lg font-medium rounded-md transition-all duration-300',
                activeTab === index 
                  ? 'bg-gradient-to-r from-red-700 to-red-900 text-white shadow-lg' 
                  : 'text-gray-400 hover:text-white'
              ]"
            >
              {{ tab }}
            </button>
          </div>
        </div>
        
        <!-- Tab Content with Creative Design -->
        <div class="max-w-8xl mx-auto relative">
          <!-- Decorative elements -->
          <div class="absolute -top-10 -left-10 w-40 h-40 bg-red-600/10 rounded-full filter blur-3xl"></div>
          <div class="absolute -bottom-10 -right-10 w-40 h-40 bg-yellow-600/10 rounded-full filter blur-3xl"></div>
          
          <!-- Card content -->
          <div class="bg-gradient-to-br from-gray-900 to-black border border-red-900/20 rounded-2xl p-8 md:p-10 shadow-2xl relative overflow-hidden">
            <!-- Tab panels -->
            <div v-show="activeTab === 0" class="relative z-10">
              <h3 class="text-4xl font-bold mb-8 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">About</h3>
              <p class="text-gray-300 text-lg leading-relaxed">
                Lekompo is a music genre from Limpopo. Lekompo Chillas Mix hosts lekompo balcony mix as a movement that popularises the genre.
                The Lekompo Balcony Mix is a playlist event that seeks to promote the culture, the dress style, associated brands, the lekompo 
                music and the faces behind the whole lekompo culture. The events further seek to unite the lekompo community.
              </p>
            </div>
            
            <div v-show="activeTab === 1" class="relative z-10">
              <h3 class="text-4xl font-bold mb-8 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">Vision</h3>
              <div class="flex">
                <div class="text-red-500 text-5xl font-bold mr-6 opacity-20">"</div>
                <p class="text-gray-300 text-lg leading-relaxed">
                  Whereas Lekompo Music emanates from Limpopo, the vision is not to landlock it but to strengthen the genre to the greater parts 
                  of the world. In order to do same, we need not to confine lekompo to the tag of it being a genre—but a culture. 
                  The vision is therefore to popularise the movement without limits.
                </p>
              </div>
            </div>
            
            <div v-show="activeTab === 2" class="relative z-10">
              <h3 class="text-4xl font-bold mb-8 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">Mission</h3>
              <ul class="space-y-6">
                <li class="flex items-start space-x-4">
                  <div class="mt-1 flex-shrink-0 w-8 h-8 rounded-full bg-gradient-to-br from-red-600 to-yellow-600 flex items-center justify-center text-white font-bold">1</div>
                  <p class="text-gray-300 text-lg">To provide exceptional events that blend creativity, emotion, and authenticity in the sound of Lekompo.</p>
                </li>
                <li class="flex items-start space-x-4">
                  <div class="mt-1 flex-shrink-0 w-8 h-8 rounded-full bg-gradient-to-br from-red-600 to-yellow-600 flex items-center justify-center text-white font-bold">2</div>
                  <p class="text-gray-300 text-lg">To collaborate with brands by bringing their vision to life.</p>
                </li>
                <li class="flex items-start space-x-4">
                  <div class="mt-1 flex-shrink-0 w-8 h-8 rounded-full bg-gradient-to-br from-red-600 to-yellow-600 flex items-center justify-center text-white font-bold">3</div>
                  <p class="text-gray-300 text-lg">Creating meaningful and impactful visuals and music scenes.</p>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

     <!-- Past Events Section -->
     <section id="events" class="py-20 container mx-auto px-4 animate-on-scroll">
      <h2 class="text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500 text-center mb-12">Past Events</h2>
      
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div class="bg-black/30 backdrop-blur-sm rounded-xl overflow-hidden shadow-lg border border-red-900/20 hover:border-red-500/30 transition-all duration-300 group">
          <img src="https://www.howler.co.za/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBejBYQWc9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--59fdecb3110ab91f45aff7879bffecf042cf600a/4fbbc7f2-d40e-4d50-b44c-1925d29d417c.jpeg" alt="Lekompo Mix 5" class="w-full h-48 object-cover">
          <div class="p-6">
            <h3 class="text-xl font-bold mb-2 group-hover:text-red-400 transition-colors">Lekompo Mix 5</h3>
            <p class="text-gray-400 mb-2">27 April 2025</p>
            <p class="text-gray-300">Featuring Tribby, Zolly, wendy, smeezy and DJ Snani</p>
          </div>
        </div>
        
        <div class="bg-black/30 backdrop-blur-sm rounded-xl overflow-hidden shadow-lg border border-red-900/20 hover:border-red-500/30 transition-all duration-300 group">
          <img src="https://computicket-boxoffice-media.s3.af-south-1.amazonaws.com/media-library/43105/conversions/SAsQ0KJTA4Xrx2jIzeFNkji7gojycM-metaZWIzNjA1Y2YtMzU2Zi00NDZhLTkyM2EtMjEzNzRmMTNiNTgxLmpwZWc%3D--detail-webp.webp" alt="Lekompo Mix 4" class="w-full h-48 object-cover">
          <div class="p-6">
            <h3 class="text-xl font-bold mb-2 group-hover:text-red-400 transition-colors">Lekompo Mix 4</h3>
            <p class="text-gray-400 mb-2">08 March 2025</p>
            <p class="text-gray-300">Featuring Janesh, Abi , Janesh</p>
          </div>
        </div>
        
        <div class="bg-black/30 backdrop-blur-sm rounded-xl overflow-hidden shadow-lg border border-red-900/20 hover:border-red-500/30 transition-all duration-300 group">
          <img src="https://scontent-jnb2-1.xx.fbcdn.net/v/t39.30808-6/495545929_1241987921263654_6177376699809834848_n.jpg?_nc_cat=102&ccb=1-7&_nc_sid=833d8c&_nc_ohc=hb4rIy9DDVcQ7kNvwFiLdln&_nc_oc=AdnXPBxny28du9qKrAYX0ew6jvLGnGLNYdysbTnd4M_nilUJn14Ih39MGblKybwQDCs&_nc_zt=23&_nc_ht=scontent-jnb2-1.xx&_nc_gid=lnN-_4yDZ16ih43-WdxsaA&oh=00_AfLNPA39DAOJYV9EQbJRc5LblXDspW8nix15ki0nz_fqmA&oe=682A2C82" alt="Lekompo Mix 3" class="w-full h-48 object-cover">
          <div class="p-6">
            <h3 class="text-xl font-bold mb-2 group-hover:text-red-400 transition-colors">Lekompo Mix 3</h3>
            <p class="text-gray-400 mb-2">21 February 2025</p>
            <p class="text-gray-300">Featuring Ba Bethe and Mc Kay</p>
          </div>
        </div>
      </div>
    </section>

   
    
    <!-- Music Section -->
  <section id="music" class="py-24 relative animate-on-scroll">
    <div class="absolute inset-0 bg-gradient-to-b from-black to-black/90 z-0"></div>
    
    <div class="container mx-auto px-6 relative z-10">
      <h2 class="text-5xl md:text-6xl font-black text-center mb-16 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-red-500 to-yellow-400">Music</h2>
      
      <!-- Decorative elements -->
      <div class="absolute -top-10 right-20 w-40 h-40 bg-red-600/10 rounded-full filter blur-3xl"></div>
      <div class="absolute bottom-20 left-10 w-40 h-40 bg-yellow-600/10 rounded-full filter blur-3xl"></div>
      
      <!-- Main Content - Side by Side Containers with 1 embed each -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-6xl mx-auto">
        <!-- Spotify Container - Single Embed -->
        <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 hover:border-red-500/30 transition-all duration-300 shadow-lg p-6 overflow-hidden">
          <h3 class="text-2xl font-bold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">Spotify</h3>
          
          <div class="rounded-xl overflow-hidden p-0.5 bg-gradient-to-r from-red-600 to-yellow-600">
            <div class="bg-gray-900 rounded-lg p-1">
              <!-- Just one playlist embed -->
              <iframe src="https://open.spotify.com/embed/album/3MnpwtoFirZc0UdWSGtdpY" width="100%" height="380" frameborder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" class="rounded-lg"></iframe>
            </div>  
          </div>
        </div>
        
        <!-- YouTube Container - Single Embed -->
        <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 hover:border-red-500/30 transition-all duration-300 shadow-lg p-6 overflow-hidden">
          <h3 class="text-2xl font-bold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">YouTube</h3>
          
          <div class="rounded-xl overflow-hidden p-0.5 bg-gradient-to-r from-red-600 to-yellow-600">
            <div class="bg-gray-900 rounded-lg p-1">
              <!-- Just one video embed -->
              <iframe width="100%" height="380" src="https://www.youtube.com/embed/IDhRK9zXLs8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="rounded-lg"></iframe>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Hot New Releases - Made more prominent -->
      <div class="mt-20 bg-black/20 backdrop-blur-sm rounded-xl border border-red-900/20 p-8 max-w-6xl mx-auto">
        <h3 class="text-3xl font-bold text-center mb-10 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">Hot New Releases</h3>
        
        <div class="space-y-6">
          <!-- Release 1 -->
          <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 p-4 hover:border-red-500/30 transition-all duration-300">
            <div class="rounded-lg overflow-hidden">
              <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/3CLA4E7HOX6MBSjZG7hyhm?utm_source=generator" width="100%" height="152" frameBorder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
            </div>
          </div>
          
          <!-- Release 2 -->
          <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 p-4 hover:border-red-500/30 transition-all duration-300">
            <div class="rounded-lg overflow-hidden">
              <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/1PpA7U71A6sBFDDawDXtxf?utm_source=generator" width="100%" height="152" frameBorder="0"  allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
            </div>
          </div>
          
          <!-- Release 3 -->
          <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 p-4 hover:border-red-500/30 transition-all duration-300">
            <div class="rounded-lg overflow-hidden">
              <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/3bM6G6G4kcoeTAMdFDPKEB?utm_source=generator" width="100%" height="152" frameBorder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

    <section id="faq" class="py-24 relative animate-on-scroll">
      <div class="absolute inset-0 bg-gradient-to-b from-black to-black/90 z-0"></div>
      <div class="container mx-auto px-4 relative z-10">
        <h2 class="text-5xl md:text-6xl font-black text-center mb-20 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-red-500 to-yellow-400">FAQ</h2>
        
        <div class="max-w-4xl mx-auto space-y-6">
          <div v-for="(item, i) in [
            {q: 'What is Lekompo music?', a: 'Lekompo is a vibrant music genre from Limpopo that blends traditional sounds with modern production.'},
            {q: 'Are tickets refundable?', a: 'Tickets are non-refundable but can be transferred to another person up to 48 hours before the event.'},
            {q: 'What should I bring to the event?', a: 'Your ticket (digital or printed), ID, and good vibes! Food and drinks will be available for purchase.'},
            {q: 'Is there an age restriction?', a: 'Yes, this is an 18+ event. Valid ID will be required for entry.'}
          ]" :key="i" class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 hover:border-red-500/30 transition-all duration-300 shadow-lg overflow-hidden">
            <div @click="activeFaq = activeFaq === i ? null : i" 
                class="p-6 cursor-pointer flex justify-between items-center">
              <h3 class="text-lg font-medium text-white">{{ item.q }}</h3>
              <svg :class="[activeFaq === i ? 'rotate-180' : '', 'transition-transform duration-300']" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16" class="text-red-500">
                <path d="M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z"/>
              </svg>
            </div>
            <div v-show="activeFaq === i" class="px-6 pb-6 text-gray-300">
              {{ item.a }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="newsletter" class="py-32 relative animate-on-scroll">
      <div class="absolute inset-0 bg-gradient-to-b from-black to-black/90 z-0"></div>
      
      <!-- Decorative elements like other sections -->
      <div class="absolute -top-20 right-10 w-60 h-60 bg-red-600/10 rounded-full filter blur-3xl"></div>
      <div class="absolute -bottom-20 left-10 w-60 h-60 bg-yellow-600/10 rounded-full filter blur-3xl"></div>
      
      <div class="container mx-auto px-4 relative z-10">
        <h2 class="text-5xl md:text-6xl font-black text-center mb-20 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-red-500 to-yellow-400">Stay Updated</h2>
        
        <div class="max-w-4xl mx-auto bg-black/30 backdrop-blur-sm rounded-xl p-8 border border-red-900/20 hover:border-red-500/30 transition-all duration-300 shadow-lg">
          <p class="text-gray-300 text-center mb-8">Be the first to know about upcoming events, artist announcements, and ticket releases.</p>
          
          <form @submit.prevent="" class="flex flex-col sm:flex-row gap-4">
            <input 
              type="email" 
              placeholder="Your email address" 
              class="flex-1 bg-black/50 border border-gray-700 rounded-lg px-4 py-3 text-gray-200 focus:outline-none focus:border-red-500 transition-colors"
              required
            />
            <button 
              type="submit" 
              class="px-8 py-4 bg-gradient-to-r from-red-700 to-red-900 hover:from-red-800 hover:to-red-950 text-white rounded-full transition-all duration-300 font-medium shadow-lg hover:shadow-red-500/30 transform hover:-translate-y-1"
            >
              Subscribe
            </button>
          </form>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-20 relative overflow-hidden">
      <!-- Background gradient to match other sections -->
      <div class="absolute inset-0 bg-gradient-to-b from-black to-black/90 z-0"></div>
      
      <!-- Decorative elements like other sections -->
      <div class="absolute -top-20 right-10 w-60 h-60 bg-red-600/10 rounded-full filter blur-3xl"></div>
      <div class="absolute -bottom-20 left-10 w-60 h-60 bg-yellow-600/10 rounded-full filter blur-3xl"></div>

      <div class="container mx-auto px-4 relative z-10">
        <!-- Social Links with matching styling -->
        <div class="bg-black/30 backdrop-blur-sm rounded-xl border border-red-900/20 p-8 mb-12 max-w-4xl mx-auto">
          <h2 class="text-3xl font-bold text-center mb-8 text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-red-500">Follow Us</h2>
          <div class="flex justify-center space-x-8">
            <a href="https://www.youtube.com/@LekompoCultureMixSessions-g9o" target="_blank" rel="noopener noreferrer" class="transform hover:scale-110 transition-transform duration-300">
              <div class="w-12 h-12 rounded-full bg-gradient-to-br from-red-900 to-red-600 flex items-center justify-center shadow-lg">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 16 16" class="text-white">
                  <path d="M8.051 1.999h.089c.822.003 4.987.033 6.11.335a2.01 2.01 0 0 1 1.415 1.42c.101.38.172.883.22 1.402l.01.104.022.26.008.104c.065.914.073 1.77.074 1.957v.075c-.001.194-.01 1.108-.082 2.06l-.008.105-.009.104c-.05.572-.124 1.14-.235 1.558a2.007 2.007 0 0 1-1.415 1.42c-1.16.312-5.569.334-6.18.335h-.142c-.309 0-1.587-.006-2.927-.052l-.17-.006-.087-.004-.171-.007-.171-.007c-1.11-.049-2.167-.128-2.654-.26a2.007 2.007 0 0 1-1.415-1.419c-.111-.417-.185-.986-.235-1.558L.09 9.82l-.008-.104A31.4 31.4 0 0 1 0 7.68v-.123c.002-.215.01-.958.064-1.778l.007-.103.003-.052.008-.104.022-.26.01-.104c.048-.519.119-1.023.22-1.402a2.007 2.007 0 0 1 1.415-1.42c.487-.13 1.544-.21 2.654-.26l.17-.007.172-.006.086-.003.171-.007A99.788 99.788 0 0 1 7.858 2h.193zM6.4 5.209v4.818l4.157-2.408L6.4 5.209z"/>
                </svg>
              </div>
            </a>
            <a href="https://www.tiktok.com/@lekompoculturemix" target="_blank" rel="noopener noreferrer" class="transform hover:scale-110 transition-transform duration-300">
              <div class="w-12 h-12 rounded-full bg-gradient-to-br from-gray-900 to-gray-600 flex items-center justify-center shadow-lg">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="currentColor" viewBox="0 0 16 16" class="text-white">
                  <path d="M9 0h1.98c.144.715.54 1.617 1.235 2.512C12.895 3.389 13.797 4 15 4v2c-1.753 0-3.07-.814-4-1.829V11a5 5 0 1 1-5-5v2a3 3 0 1 0 3 3V0Z"/>
                </svg>
              </div>
            </a>
            <a href="https://www.instagram.com/lekompobalconymix/" target="_blank" rel="noopener noreferrer" class="transform hover:scale-110 transition-transform duration-300">
              <div class="w-12 h-12 rounded-full bg-gradient-to-br from-pink-800 to-pink-500 flex items-center justify-center shadow-lg">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="currentColor" viewBox="0 0 16 16" class="text-white">
                  <path d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.917 3.917 0 0 0-1.417.923A3.927 3.927 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.916 3.916 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.926 3.926 0 0 0-.923-1.417A3.911 3.911 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0h.003zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599.28.28.453.546.598.92.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.47 2.47 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.478 2.478 0 0 1-.92-.598 2.48 2.48 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233 0-2.136.008-2.388.046-3.231.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92.28-.28.546-.453.92-.598.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045v.002zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92zm-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217zm0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334z"/>
                </svg>
              </div>
            </a>
            <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="transform hover:scale-110 transition-transform duration-300">
              <div class="w-12 h-12 rounded-full bg-gradient-to-br from-blue-900 to-blue-600 flex items-center justify-center shadow-lg">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="currentColor" viewBox="0 0 16 16" class="text-white">
                  <path d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951z"/>
                </svg>
              </div>
            </a>
          </div>
        </div>

        <!-- Footer Content with gradient border -->
        <div class="rounded-xl p-0.5 bg-gradient-to-r from-red-900/50 to-yellow-900/50 max-w-xl mx-auto">
          <div class="bg-black/70 backdrop-blur-sm rounded-lg p-8 text-center">
            <div class="relative mb-6">
              <!-- Logo glow effect -->
              <div class="absolute inset-0 bg-red-500/30 rounded-full blur-lg"></div>
              <img src="@/assets/images/logo.jpg" alt="Lekompō Logo" class="relative w-20 h-20 object-cover rounded-full mx-auto mb-2 ring-2 ring-red-500/50">
            </div>
            <div class="text-lg font-medium text-transparent bg-clip-text bg-gradient-to-r from-yellow-200 to-red-300 mb-2">© 2025 Lekompō Mix</div>
            <div class="text-sm text-gray-400 mb-6">The Ultimate Balcony Mix Experience</div>
            
            <!-- Contact info -->
            <div class="flex justify-center space-x-8 text-sm text-gray-400">
              <a href="mailto:lekompochillasmix@gmail.com" class="hover:text-red-400 transition-colors">info@lekompo.com</a>
              <a href="tel:+27123456789" class="hover:text-red-400 transition-colors">+27 12 345 6789</a>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Animation keyframes */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-on-scroll {
  opacity: 0;
}

.animate-fade-in {
  animation: fadeIn 0.8s ease forwards;
}
</style>