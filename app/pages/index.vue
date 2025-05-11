<script setup lang="ts">
import NavBar from '~/components/NavBar.vue'
import { ref, onMounted } from 'vue'

// Notification modal state
const notify = ref(false)

// Countdown logic for Next Event: 25 May 2025 · Meropa Casino
const countdown = ref({ days: '--', hours: '--', minutes: '--', seconds: '--' })
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
onMounted(() => {
  updateCountdown()
  setInterval(updateCountdown, 1000)
})

// Past events data
const pastEvents = Array.from({ length: 6 }, (_, i) => ({
  id: i + 1,
  title: `Balcony Mix ${i + 1}`,
  date: new Date(2024, i + 1, 5).toLocaleDateString(),
  img: `https://picsum.photos/seed/event${i+1}/400/300`
}))

// Artists data
const artists = [
  { name: 'Shebeshxt', photo: 'https://picsum.photos/seed/artist1/200/200', topTrack: { name: 'Ambulance', embed: '3ma6tT5grA0NMud8I4oRmH' } },
  { name: 'Kharishma', photo: 'https://picsum.photos/seed/artist2/200/200', topTrack: { name: 'Chokeslem', embed: '5QUe8XDF5536t4H0aRdt01' } },
  { name: 'Naqua SA', photo: 'https://picsum.photos/seed/artist3/200/200', topTrack: { name: 'Sekoloto', embed: '21PFvrdji50onYneSMkHWjA' } }
]
</script>

<template>
  <div class="bg-black text-white min-h-screen font-sans">
    <NavBar />

    <!-- Hero / Countdown -->
    <section id="hero" class="container mx-auto px-4 text-center">
      <h1 class="text-5xl font-bold text-yellow-400 mb-4">Lekompō Balcony Mix</h1>
      <img src="@/assets/images/logo.jpg" alt="" class="w-120 mx-auto mb-6 rounded-lg shadow-lg">
      <p class="text-xl mb-2 text-gray-300">Next Event: Lekompo Balcony mix 6</p>
      <p class="text-lg mb-2 text-gray-500">25 May 2025</p>
      <p class="text-lg mb-6 text-gray-500">Meropa Casino, Polokwane</p>
      <div class="flex justify-center space-x-6 text-2xl text-green-400 mb-6">
        <div><div>{{ countdown.days }}</div><div class="text-sm">Days</div></div>
        <div><div>{{ countdown.hours }}</div><div class="text-sm">Hours</div></div>
        <div><div>{{ countdown.minutes }}</div><div class="text-sm">Mins</div></div>
        <div><div>{{ countdown.seconds }}</div><div class="text-sm">Secs</div></div>
      </div>
      <div class="space-x-4">
        <a href="#https://www.howler.co.za/events/lekompo-mix-6-with-shebeshxt-kharishma-naqua-adb1" class="px-6 py-2 border border-yellow-400 text-yellow-600 rounded hover:bg-yellow-400 hover:text-white transition">Tickets</a>
        <a href="#artists" class="px-6 py-2 border border-red-600 text-red-600 rounded hover:bg-red-600 hover:text-white transition">Featured Artists</a>
      </div>
    </section>

    <!-- Artists -->
    <section id="artists" class="py-20 container mx-auto px-4">
      <h2 class="text-3xl font-semibold text-yellow-400 text-center mb-8">Featured Artists</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="artist in artists" :key="artist.name" class="bg-gray-800 rounded-lg p-6 text-center">
          <img :src="artist.photo" :alt="artist.name" class="mx-auto w-32 h-32 rounded-full object-cover mb-4">
          <h3 class="text-xl font-semibold text-red-400 mb-1">{{ artist.name }}</h3>
          <p class="text-gray-300 mb-2">Top Track: {{ artist.topTrack.name }}</p>
          <iframe :src="`https://open.spotify.com/embed/track/${artist.topTrack.embed}`" width="100%" height="80" frameborder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>
    </section>

    <!-- About, Vission & Mission  -->
    <section id="about" class="py-20 bg-gray-900">
      <div class="container mx-auto px-4 text-center">
        <h2 class="text-3xl font-semibold text-yellow-400 mb-4">About</h2>
        <p class="text-gray-300 max-w-2xl mx-auto">
          Lekompo is a music genre from Limpopo. Lekompo Chillas Mix hosts lekompo balcony mix as a movement that popularises the genre.
          The Lekompo Balcony Mix is a playlist event that seeks to promote the culture, the dress style, associated brands, the lekompo 
          music and the faces behind the whole lekompo culture.The events further seek to unite the lekompo community.
        </p>
      </div>
    </section>

    <section id="about" class=" bg-gray-900"> 
      <div class="container mx-auto py-4 px-4 text-center">
        <h2 class="text-3xl font-semibold text-yellow-400 mb-4">Vision</h2>
        <p class="text-gray-300 max-w-2xl mx-auto">
          Whereas Lekompo Music emanates from Limpopo, the vision is not to landlock it but to strengthen the genre to the greater parts 
          of the world. In order to do same, we need not to confine lekompo to the tag of it being a genre-but a culture. 
          The vision is therefore to popularise the movement without limits.
        </p>
      </div>
    </section>

    <section id="about" class=" bg-gray-900"> 
      <div class="container mx-auto py-4 px-4 text-center">
        <h2 class="text-3xl font-semibold text-yellow-400 mb-4">Mission</h2>
        <p class="text-gray-300 max-w-2xl mx-auto">
          * To provide exceptional events that blend creativity, emotion, and authenticity in the sound of Lekompo <br>
          * To collaborate with brands by bringing their vision to life. <br>
          * Creating meaningful and impactful visuals and music scenes.
        </p>
      </div>
    </section>

    <!-- Past Events -->
    <section id="events" class="py-20 container mx-auto px-4">
      <h2 class="text-3xl font-semibold text-yellow-400 text-center mb-8">Past Events</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="e in pastEvents" :key="e.id" class="bg-gray-800 rounded-lg overflow-hidden shadow">
          <img :src="e.img" :alt="e.title" class="w-full h-40 object-cover">
          <div class="p-4">
            <h4 class="font-semibold text-lg text-red-400">{{ e.title }}</h4>
            <p class="text-gray-300 text-sm mt-1">Date: {{ e.date }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats -->
    <section id="stats" class="py-20 bg-gray-900 text-center">
      <div class="container mx-auto px-4 grid grid-cols-2 md:grid-cols-3 gap-6">
        <div><div class="text-4xl font-bold text-red-400">6</div><div class="text-gray-300">Events Hosted</div></div>  
        <div><div class="text-4xl font-bold text-red-400">25+</div><div class="text-gray-300">Tracks Released</div></div>
        <div><div class="text-4xl font-bold text-red-400">3</div><div class="text-gray-300">DJs Featured</div></div>
      </div>
    </section>

    <!-- Music -->
    <section id="music" class="py-20 bg-gray-900 text-center">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-semibold text-yellow-400 mb-8">Music</h2>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
          <div class="bg-gray-800 rounded-lg p-6">
            <h3 class="text-2xl font-semibold text-red-400 mb-4">Lekompo Balcony Mix on Spotify</h3>
            <iframe src="https://open.spotify.com/embed/album/3MnpwtoFirZc0UdWSGtdpY" width="100%" height="380" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
          </div>
          <div class="bg-gray-800 rounded-lg p-6">
            <h3 class="text-2xl font-semibold text-red-400 mb-4">New Release: Balcony Mix 5</h3>
            <iframe width="100%" height="315" src="https://www.youtube.com/embed/OLAK5uy_muru5HnyGZPMaitqqcO8krx2lF0E5oZ0E" frameborder="0" allow="autoplay; encrypted-media; fullscreen; picture-in-picture" allowfullscreen></iframe>
          </div>
        </div>
      </div>
    </section>

    <!-- Gallery -->
    <section id="gallery" class="py-20 container mx-auto px-4">
      <h2 class="text-3xl font-semibold text-yellow-400 text-center mb-8">Gallery</h2>
      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="n in 8" :key="n" class="h-40 bg-cover bg-center rounded-lg" :style="{ backgroundImage: `url(https://picsum.photos/seed/gallery${n}/400/400)` }"></div>
      </div>
    </section>

    <!--FAQ -->
    <section id="faq" class="py-20 container mx-auto px-4 text-center">
      <h2 class="text-3xl font-semibold text-yellow-400 mb-8">Frequently Asked Questions</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <details class="bg-gray-800 p-4 rounded-lg text-left"><summary class="font-semibold text-white cursor-pointer">Who can attend?</summary><p class="mt-2 text-gray-300">18+ only.</p></details>
        <details class="bg-gray-800 p-4 rounded-lg text-left"><summary class="font-semibold text-white cursor-pointer">Parking?</summary><p class="mt-2 text-gray-300">Free onsite parking.</p></details>
        <details class="bg-gray-800 p-4 rounded-lg text-left md:col-span-2"><summary class="font-semibold text-white cursor-pointer">Dress code?</summary><p class="mt-2 text-gray-300">All black attire.</p></details>
      </div>
    </section>

    <!-- Newsletter -->
    <section id="newsletter" class="py-20 bg-gray-900 text-center">
      <div class="container mx-auto px-4">
        <div class="bg-gray-800 rounded-lg p-6 max-w-md mx-auto">
          <h2 class="text-2xl font-semibold text-yellow-400 mb-4">Join Our Newsletter</h2>
          <p class="text-gray-300 mb-4">Stay updated on upcoming mixes and special releases.</p>
          <form class="space-y-4">
            <input type="text" placeholder="Your Name" class="w-full px-4 py-2 rounded-md bg-gray-700 border border-gray-600 text-white" />
            <input type="email" placeholder="Email Address" class="w-full px-4 py-2 rounded-md bg-gray-700 border border-gray-600 text-white" />
            <button type="submit" class="w-full px-4 py-2 bg-green-600 rounded hover:bg-green-700 transition text-white">Subscribe</button>
          </form>
        </div>
      </div>
    </section>

    <!-- Social -->
    <section id="social" class="py-20 container mx-auto px-4 text-center">
      <h2 class="text-3xl font-semibold text-yellow-400 mb-6">Follow Us</h2>
      <div class="flex justify-center space-x-4 mt-4">
        <a href="https://youtube.com" target="_blank" rel="noopener noreferrer" class="text-red-600 hover:text-red-400 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" viewBox="0 0 16 16">
            <path d="M8.051 1.999h.089c.822.003 4.987.033 6.11.335a2.01 2.01 0 0 1 1.415 1.42c.101.38.172.883.22 1.402l.01.104.022.26.008.104c.065.914.073 1.77.074 1.957v.075c-.001.194-.01 1.108-.082 2.06l-.008.105-.009.104c-.05.572-.124 1.14-.235 1.558a2.007 2.007 0 0 1-1.415 1.42c-1.16.312-5.569.334-6.18.335h-.142c-.309 0-1.587-.006-2.927-.052l-.17-.006-.087-.004-.171-.007-.171-.007c-1.11-.049-2.167-.128-2.654-.26a2.007 2.007 0 0 1-1.415-1.419c-.111-.417-.185-.986-.235-1.558L.09 9.82l-.008-.104A31.4 31.4 0 0 1 0 7.68v-.123c.002-.215.01-.958.064-1.778l.007-.103.003-.052.008-.104.022-.26.01-.104c.048-.519.119-1.023.22-1.402a2.007 2.007 0 0 1 1.415-1.42c.487-.13 1.544-.21 2.654-.26l.17-.007.172-.006.086-.003.171-.007A99.788 99.788 0 0 1 7.858 2h.193zM6.4 5.209v4.818l4.157-2.408L6.4 5.209z"/>
          </svg>
        </a>
        <a href="https://tiktok.com" target="_blank" rel="noopener noreferrer" class="text-gray-200 hover:text-gray-400 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" fill="currentColor" viewBox="0 0 16 16">
            <path d="M9 0h1.98c.144.715.54 1.617 1.235 2.512C12.895 3.389 13.797 4 15 4v2c-1.753 0-3.07-.814-4-1.829V11a5 5 0 1 1-5-5v2a3 3 0 1 0 3 3V0Z"/>
          </svg>
        </a>
        <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" class="text-pink-600 hover:text-pink-400 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" fill="currentColor" viewBox="0 0 16 16">
            <path d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.917 3.917 0 0 0-1.417.923A3.927 3.927 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.916 3.916 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.926 3.926 0 0 0-.923-1.417A3.911 3.911 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0h.003zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599.28.28.453.546.598.92.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.47 2.47 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.478 2.478 0 0 1-.92-.598 2.48 2.48 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233 0-2.136.008-2.388.046-3.231.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92.28-.28.546-.453.92-.598.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045v.002zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92zm-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217zm0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334z"/>
          </svg>
        </a>
        <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="text-blue-600 hover:text-blue-400 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" fill="currentColor" viewBox="0 0 16 16">
            <path d="M16 8.049c0-4.446-3.582-8.05-8-8.05C3.58 0-.002 3.603-.002 8.05c0 4.017 2.926 7.347 6.75 7.951v-5.625h-2.03V8.05H6.75V6.275c0-2.017 1.195-3.131 3.022-3.131.876 0 1.791.157 1.791.157v1.98h-1.009c-.993 0-1.303.621-1.303 1.258v1.51h2.218l-.354 2.326H9.25V16c3.824-.604 6.75-3.934 6.75-7.951z"/>
          </svg>
        </a>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-6 text-center bg-gray-800 text-gray-500">
      © 2025 Lekompō Mix
    </footer>
  </div>
</template>

<style scoped>
.container {
  max-width: 1024px;
}
</style>
