<template>
  <div class="font-sans">
    <!-- Header -->
    <header class="fixed top-0 w-full bg-white shadow-md z-50">
      <nav class="max-w-7xl mx-auto flex items-center justify-between p-4">
        <div class="text-2xl font-bold text-red-700">Lekompō Mix</div>
        <ul class="hidden md:flex space-x-6 text-gray-700">
          <li><a href="#about" class="hover:text-red-700">About</a></li>
          <li><a href="#lineup" class="hover:text-red-700">Line-Up</a></li>
          <li><a href="#gallery" class="hover:text-red-700">Gallery</a></li>
          <li><a href="#tickets" class="hover:text-red-700">Tickets</a></li>
          <li><a href="#contact" class="hover:text-red-700">Contact</a></li>
        </ul>
      </nav>
    </header>

    <!-- Hero Section -->
    <section
      id="hero"
      class="h-screen bg-cover bg-center"
      style="background-image: url('https://images.unsplash.com/photo-1508970436-b46233be0f0e?auto=format&fit=crop&w=1600&q=80')"
    >
      <div class="bg-black bg-opacity-50 h-full flex flex-col justify-center items-center text-center px-4">
        <h1 class="text-5xl md:text-7xl font-extrabold text-white uppercase">
          Lekompō Balcony Mix
        </h1>
        <p class="mt-4 text-lg md:text-2xl text-yellow-300">
          Fri 21 Feb · Phela Bush Adventure
        </p>
        <button
          class="mt-6 px-8 py-3 bg-red-700 text-white font-semibold rounded-md hover:bg-red-800 transition"
        >
          Buy Tickets
        </button>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-20 bg-gray-50">
      <div class="max-w-4xl mx-auto text-center px-4">
        <h2 class="text-3xl font-bold text-red-700">About Lekompō</h2>
        <p class="mt-4 text-gray-700">
          Lekompō is more than music—it’s a cultural movement from Limpopo.
          Chillas Mix brings the community together with beats, creativity, and authenticity.
        </p>
      </div>
    </section>

    <!-- Line-Up Section -->
    <section id="lineup" class="py-20">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-red-700 text-center">Line-Up & Schedule</h2>
        <div class="mt-8 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          <!-- Example Artist Card -->
          <div class="bg-white shadow rounded-lg overflow-hidden">
            <img
              src="https://images.unsplash.com/photo-1512726731325-2dfc598b0b3e?auto=format&fit=crop&w=800&q=80"
              alt="DJ on turntable"
              class="w-full h-48 object-cover"
            >
            <div class="p-4">
              <h3 class="font-semibold text-lg">Featured DJ</h3>
              <p class="text-sm text-gray-600 mt-1">2:00 PM</p>
            </div>
          </div>
          <!-- repeat for more artists -->
        </div>
      </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="py-20 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-red-700 text-center">Gallery</h2>
        <div class="mt-8 grid grid-cols-2 md:grid-cols-4 gap-4">
          <div
            class="h-40 bg-cover bg-center"
            style="background-image: url('https://images.unsplash.com/photo-1525909002-6d1d1c0f74d0?auto=format&fit=crop&w=400&q=80')"
          ></div>
          <div
            class="h-40 bg-cover bg-center"
            style="background-image: url('https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=400&q=80')"
          ></div>
          <!-- more if you like -->
        </div>
      </div>
    </section>

    <!-- Tickets Section -->
    <section id="tickets" class="py-20">
      <div class="max-w-4xl mx-auto text-center px-4">
        <h2 class="text-3xl font-bold text-red-700">Tickets & Info</h2>
        <p class="mt-4 text-gray-700">R350 (includes food & mocktails)</p>
        <a
          href="https://www.computicket.co.za"
          target="_blank"
          class="mt-6 inline-block px-6 py-3 bg-yellow-400 text-gray-900 font-semibold rounded-md hover:bg-yellow-500 transition"
        >
          Buy on Computicket
        </a>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 bg-gray-50">
      <div class="max-w-4xl mx-auto text-center px-4">
        <h2 class="text-3xl font-bold text-red-700">Contact & Social</h2>
        <p class="mt-4 text-gray-700">
          Email: event@lekompochillasmix.co.za
        </p>
        <div class="mt-4 flex justify-center space-x-4">
          <a href="#" class="text-gray-700 hover:text-red-700">Instagram</a>
          <a href="#" class="text-gray-700 hover:text-red-700">TikTok</a>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-6 bg-white shadow-inner">
      <div class="max-w-7xl mx-auto text-center text-gray-600">
        © 2025 Lekompō Chillas Mix
      </div>
    </footer>
  </div>
</template>

<script setup>
// no local images needed!
</script>