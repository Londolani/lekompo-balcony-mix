<template>
  <div class="bg-gray-900 text-white font-sans scroll-smooth">
    <NavBar />

    <!-- Hero / Countdown -->
    <section id="hero" class="h-screen flex flex-col justify-center items-center bg-cover bg-center" style="background-image:url('https://source.unsplash.com/1600x900/?concert,night')">
      <div class="bg-black bg-opacity-60 p-8 rounded-lg text-center">
        <h1 class="text-5xl md:text-7xl font-extrabold mb-4">Lekompō Balcony Mix</h1>
        <p class="text-xl mb-6">Next Event: 10 Jun 2025 · Howler</p>
        <div class="text-lg mb-4">Starts In</div>
        <div class="flex justify-center space-x-6 text-2xl">
          <div class="text-yellow-400">
            <span>{{countdown.days}}</span>
            <div class="text-sm">Days</div>
          </div>
          <div class="text-yellow-400">
            <span>{{countdown.hours}}</span>
            <div class="text-sm">Hours</div>
          </div>
          <div class="text-yellow-400">
            <span>{{countdown.minutes}}</span>
            <div class="text-sm">Mins</div>
          </div>
          <div class="text-yellow-400">
            <span>{{countdown.seconds}}</span>
            <div class="text-sm">Secs</div>
          </div>
        </div>
        <div class="mt-8 space-x-4">
          <a href="#events" class="px-6 py-3 bg-red-700 rounded-md hover:bg-red-800 transition">Events</a>
          <a href="#music" class="px-6 py-3 bg-yellow-400 text-gray-900 rounded-md hover:bg-yellow-500 transition">Music</a>
        </div>
      </div>
    </section>

    <!-- Events -->
    <section id="events" class="py-20">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-4xl font-bold text-yellow-400 text-center mb-8">Events</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="n in 6" :key="n" class="bg-gray-800 rounded-lg overflow-hidden shadow-lg">
            <img :src="`https://source.unsplash.com/800x600/?festival,night&sig=${n}`" alt="Past Event" class="w-full h-48 object-cover">
            <div class="p-4">
              <h3 class="font-semibold text-xl">Balcony Mix {{n}}</h3>
              <p class="text-gray-400 mt-1">Date: {{ new Date(2024, n, 5).toLocaleDateString() }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About & Mission -->
    <section id="about" class="py-20 bg-gray-800">
      <div class="max-w-4xl mx-auto px-4 text-center">
        <h2 class="text-3xl font-bold text-yellow-400 mb-4">About & Mission</h2>
        <p class="text-gray-300 mb-6">
          Lekompō Balcony Mix elevates Limpopo's unique rhythms—celebrating culture, creativity, and community under the open sky.
        </p>
      </div>
    </section>

    <!-- Artists -->
    <section id="artists" class="py-20">
      <div class="max-w-4xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-yellow-400 text-center mb-8">Featured Artists</h2>
        <div class="space-y-8">
          <div v-for="artist in artists" :key="artist.name" class="bg-gray-800 rounded-lg shadow-lg p-6 flex flex-col md:flex-row items-center">
            <img :src="artist.photo" alt="artist.name" class="w-32 h-32 rounded-full object-cover mr-6 mb-4 md:mb-0">
            <div>
              <h3 class="text-2xl font-semibold">{{ artist.name }}</h3>
              <p class="text-gray-300">Top Track: {{ artist.topTrack.name }}</p>
              <div class="mt-4">
                <iframe :src="`https://open.spotify.com/embed/track/${artist.topTrack.id}`" width="300" height="80" frameborder="0" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Music -->
    <section id="music" class="py-20 bg-gray-800 text-center">
      <div class="max-w-4xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-yellow-400 mb-6">Music</h2>
        <!-- Spotify Mix -->
        <div class="bg-gray-900 rounded-lg p-6 mb-8 shadow-lg inline-block">
          <h3 class="text-2xl font-semibold mb-4">Listen: Lekompo Balcony Mix on Spotify</h3>
          <iframe src="https://open.spotify.com/embed/album/3MnpwtoFirZc0UdWSGtdpY" width="100%" height="380" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
        </div>
        <!-- YouTube Release -->
        <div>
          <h3 class="text-2xl font-semibold mb-4">New Release: Balcony Mix 5</h3>
          <iframe width="560" height="315" src="https://www.youtube.com/embed/OLAK5uy_muru5HnyGZPMaitqqcO8krx2lF0E5oZ0E" frameborder="0" allow="autoplay; encrypted-media; fullscreen; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>
    </section>

    <!-- Gallery -->
    <section id="gallery" class="py-20">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-yellow-400 text-center mb-8">Gallery</h2>
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4">
          <div v-for="i in 8" :key="i" class="h-40 bg-cover bg-center rounded-lg shadow-lg" :style="{ backgroundImage: `url(https://source.unsplash.com/400x400/?concert,lights&sig=${i})` }"></div>
        </div>
      </div>
    </section>

    <!-- Stats -->
    <section id="stats" class="py-20 bg-gray-800 text-center">
      <div class="max-w-4xl mx-auto px-4 grid grid-cols-2 md:grid-cols-3 gap-6">
        <div><p class="text-4xl font-bold text-yellow-400">6</p><p class="text-gray-300">Events Hosted</p></div>
        <div><p class="text-4xl font-bold text-yellow-400">25+</p><p class="text-gray-300">Tracks Released</p></div>
        <div><p class="text-4xl font-bold text-yellow-400">3</p><p class="text-gray-300">DJs Featured</p></div>
      </div>
    </section>

    <!-- Tickets & FAQ -->
    <section id="tickets" class="py-20 text-center">
      <div class="max-w-4xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-yellow-400 mb-6">Tickets & FAQ</h2>
        <p class="text-lg text-gray-300 mb-4">R350 includes food & mocktails</p>
        <a href="https://www.howler.co.za/events/lekompo-mix-6-with-shebeshxt-kharishma-naqua-adb1" target="_blank" class="px-6 py-3 bg-red-700 rounded-md hover:bg-red-800 transition inline-block mb-6">Buy Tickets</a>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <details class="bg-gray-800 p-4 rounded-lg"><summary class="font-semibold">Who can attend?</summary><p class="mt-2 text-gray-300">18+ only.</p></details>
          <details class="bg-gray-800 p-4 rounded-lg"><summary class="font-semibold">Parking?</summary><p class="mt-2 text-gray-300">Free onsite parking.</p></details>
          <details class="bg-gray-800 p-4 rounded-lg col-span-full"><summary class="font-semibold">Dress code?</summary><p class="mt-2 text-gray-300">All black attire.</p></details>
        </div>
      </div>
    </section>

    <!-- Newsletter -->
    <section id="newsletter" class="py-20 bg-gray-800 text-center">
      <div class="max-w-md mx-auto px-4 bg-gray-700 rounded-lg shadow-lg p-8">
        <h2 class="text-2xl font-bold text-yellow-400 mb-4">Join Our Newsletter</h2>
        <p class="text-gray-300 mb-4">Stay updated on upcoming mixes and special releases.</p>
        <form class="space-y-4">
          <input type="text" placeholder="Your Name" class="w-full px-4 py-2 rounded-md bg-gray-900 border border-gray-600 text-white">
          <input type="email" placeholder="Email Address" class="w-full px-4 py-2 rounded-md bg-gray-900 border border-gray-600 text-white">
          <button type="submit" class="w-full py-2 bg-red-700 rounded-md hover:bg-red-800 transition">Subscribe</button>
        </form>
      </div>
    </section>

    <!-- Social -->
    <section id="social" class="py-20 text-center">
      <h2 class="text-3xl font-bold text-yellow-400 mb-6">Follow Us</h2>
      <div class="flex justify-center space-x-6 text-3xl">
        <a href="https://youtube.com" target="_blank" class="text-red-700 hover:text-yellow-400"><i class="ri-youtube-fill"></i></a>
        <a href="https://tiktok.com" target="_blank" class="text-red-700 hover:text-yellow-400"><i class="ri-tiktok-fill"></i></a>
        <a href="https://instagram.com" target="_blank" class="text-red-700 hover:text-yellow-400"><i class="ri-instagram-fill"></i></a>
        <a href="https://facebook.com" target="_blank" class="text-red-700 hover:text-yellow-400"><i class="ri-facebook-fill"></i></a>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-6 text-center bg-gray-800 text-gray-500">
      © 2025 Lekompō Mix
    </footer>
  </div>
</template>

<script setup>
import NavBar from '~/components/NavBar.vue'
import { ref, onMounted } from 'vue'

// Countdown logic
const countdown = ref({ days: '--', hours: '--', minutes: '--', seconds: '--' })
const targetDate = new Date('2025-06-10T00:00:00')
function updateCountdown() {
  const now = new Date()
  const diff = targetDate - now
  if (diff <= 0) return
  const days = Math.floor(diff / (1000 * 60 * 60 * 24))
  const hours = Math.floor((diff / (1000 * 60 * 60)) % 24)
  const minutes = Math.floor((diff / (1000 * 60)) % 60)
  const seconds = Math.floor((diff / 1000) % 60)
  countdown.value = { days, hours, minutes, seconds }
}

onMounted(() => {
  updateCountdown()
  setInterval(updateCountdown, 1000)
})

const artists = [
  { name: 'Shebeshxt', photo: 'https://source.unsplash.com/200x200/?dj', topTrack: { name: 'Ambulance', id: '3ma6tT5grA0NMud8I4oRmH' } },
  { name: 'Kharishma', photo: 'https://source.unsplash.com/200x200/?singer', topTrack: { name: 'Chokeslem', id: '5QUe8XDF5536t4H0aRdt01' } },
  { name: 'Naqua SA', photo: 'https://source.unsplash.com/200x200/?artist', topTrack: { name: 'Sekoloto', id: '21PFvrdji50onYneSMkHWjA' } }
]
</script>

<style>
/* Global overrides or additional styles */
</style>
