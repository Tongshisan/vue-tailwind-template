<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header Section -->
    <header class="sticky top-0 z-50 bg-white shadow-sm">
      <div
        class="container mx-auto px-4 py-3 flex items-center justify-between"
      >
        <div class="flex items-center">
          <div class="text-2xl font-bold text-blue-600">
            <i class="fas fa-mountain mr-2"></i>
            <span>PeakSkier</span>
          </div>
          <nav class="hidden md:flex ml-10">
            <ul class="flex space-x-6">
              <li>
                <a
                  href="#"
                  class="text-gray-800 hover:text-blue-600 font-medium cursor-pointer"
                  >Home</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-800 hover:text-blue-600 font-medium cursor-pointer"
                  >Destinations</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-800 hover:text-blue-600 font-medium cursor-pointer"
                  >Equipment</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-800 hover:text-blue-600 font-medium cursor-pointer"
                  >Training</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-800 hover:text-blue-600 font-medium cursor-pointer"
                  >Community</a
                >
              </li>
            </ul>
          </nav>
        </div>
        <div class="flex items-center space-x-4">
          <div class="relative hidden md:block">
            <input
              type="text"
              placeholder="Search..."
              class="pl-10 pr-4 py-2 border-none rounded-full bg-gray-100 focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
            />
            <i
              class="fas fa-search absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400"
            ></i>
          </div>
          <button
            class="bg-blue-600 text-white px-4 py-2 rounded-full hover:bg-blue-700 transition duration-300 !rounded-button whitespace-nowrap cursor-pointer"
          >
            Book a Trip
          </button>
          <div class="cursor-pointer">
            <i class="fas fa-user-circle text-2xl text-gray-700"></i>
          </div>
          <button class="md:hidden text-gray-700">
            <i class="fas fa-bars text-xl"></i>
          </button>
        </div>
      </div>
    </header>
    <!-- Hero Section -->
    <section class="relative h-[600px] overflow-hidden">
      <div
        class="absolute inset-0 bg-gradient-to-r from-blue-900/80 to-transparent z-10"
      ></div>
      <img
        src="https://zyp.readdy.ai/api/search-image?query=Breathtaking%20panoramic%20view%20of%20snow-covered%20mountain%20peaks%20with%20pristine%20ski%20slopes%2C%20dramatic%20blue%20sky%20with%20wispy%20clouds%2C%20golden%20sunlight%20casting%20long%20shadows%20across%20untouched%20powder%20snow%2C%20majestic%20pine%20trees%20dusted%20with%20snow%2C%20professional%20skier%20in%20distance%2C%20cinematic%20landscape%20photography&width=1440&height=600&seq=hero1&orientation=landscape"
        alt="Ski mountain landscape"
        class="absolute inset-0 w-full h-full object-cover object-top"
      />
      <div
        class="container mx-auto px-4 h-full flex items-center relative z-20"
      >
        <div class="max-w-2xl text-white">
          <h1 class="text-5xl md:text-6xl font-bold mb-4">
            Experience the Thrill of the Slopes
          </h1>
          <p class="text-xl mb-8">
            Discover the world's most breathtaking ski destinations and create
            unforgettable memories on fresh powder snow.
          </p>
          <div class="flex flex-wrap gap-4">
            <button
              class="bg-blue-600 text-white px-6 py-3 rounded-full hover:bg-blue-700 transition duration-300 !rounded-button whitespace-nowrap cursor-pointer"
            >
              Explore Destinations
            </button>
            <button
              class="bg-white text-blue-900 px-6 py-3 rounded-full hover:bg-gray-100 transition duration-300 !rounded-button whitespace-nowrap cursor-pointer"
            >
              Get Started
            </button>
          </div>
        </div>
      </div>
      <div
        class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-20 animate-bounce"
      >
        <i class="fas fa-chevron-down text-white text-2xl"></i>
      </div>
    </section>
    <!-- Featured Destinations -->
    <section class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">
            Featured Destinations
          </h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Explore our handpicked selection of the world's most exceptional ski
            resorts, each offering unique experiences for every skill level.
          </p>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="(destination, index) in destinations"
            :key="index"
            class="bg-white rounded-xl shadow-lg overflow-hidden transition-transform duration-300 hover:shadow-xl hover:-translate-y-1 cursor-pointer"
          >
            <div class="h-64 overflow-hidden">
              <img
                :src="destination.image"
                :alt="destination.name"
                class="w-full h-full object-cover object-top transition-transform duration-500 hover:scale-105"
              />
            </div>
            <div class="p-6">
              <div class="flex justify-between items-center mb-3">
                <h3 class="text-xl font-bold">{{ destination.name }}</h3>
                <div
                  :class="`px-3 py-1 rounded-full text-xs font-medium ${destination.difficultyColor}`"
                >
                  {{ destination.difficulty }}
                </div>
              </div>
              <p class="text-gray-600 mb-4">{{ destination.description }}</p>
              <button
                class="text-blue-600 font-medium flex items-center hover:text-blue-800 !rounded-button whitespace-nowrap cursor-pointer"
              >
                Learn More <i class="fas fa-arrow-right ml-2"></i>
              </button>
            </div>
          </div>
        </div>
        <div class="text-center mt-12">
          <button
            class="border border-blue-600 text-blue-600 px-6 py-3 rounded-full hover:bg-blue-50 transition duration-300 !rounded-button whitespace-nowrap cursor-pointer"
          >
            View All Destinations
          </button>
        </div>
      </div>
    </section>
    <!-- Latest Conditions -->
    <section class="py-16 bg-gray-50">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Latest Conditions</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Stay updated with real-time snow reports and weather conditions at
            top ski resorts around the world.
          </p>
        </div>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
          <div class="bg-white rounded-xl shadow-lg overflow-hidden">
            <div class="p-6">
              <h3 class="text-xl font-bold mb-4">Current Weather</h3>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div
                  v-for="(resort, index) in resortWeather"
                  :key="index"
                  class="flex items-center p-4 bg-gray-50 rounded-lg"
                >
                  <div class="text-4xl text-blue-500 mr-4">
                    <i :class="resort.icon"></i>
                  </div>
                  <div>
                    <h4 class="font-bold">{{ resort.name }}</h4>
                    <div class="text-gray-600">{{ resort.temperature }}</div>
                    <div class="text-sm text-gray-500">
                      {{ resort.condition }}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="bg-white rounded-xl shadow-lg overflow-hidden">
            <div class="p-6">
              <h3 class="text-xl font-bold mb-4">Snow Reports</h3>
              <div class="space-y-4">
                <div
                  v-for="(report, index) in snowReports"
                  :key="index"
                  class="flex justify-between items-center p-4 bg-gray-50 rounded-lg"
                >
                  <div>
                    <h4 class="font-bold">{{ report.resort }}</h4>
                    <div class="text-sm text-gray-500">
                      Updated: {{ report.updated }}
                    </div>
                  </div>
                  <div class="text-right">
                    <div class="font-bold text-blue-600">
                      {{ report.depth }}
                    </div>
                    <div class="text-sm text-gray-600">
                      {{ report.trails }} trails open
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-12 bg-white rounded-xl shadow-lg overflow-hidden">
          <div class="p-6">
            <h3 class="text-xl font-bold mb-4">Resort Map</h3>
            <div
              class="h-[400px] bg-gray-100 rounded-lg relative overflow-hidden"
            >
              <div ref="mapContainer" class="w-full h-full"></div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Equipment Guide -->
    <section class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Equipment Guide</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Find the perfect gear for your next adventure with our curated
            selection of top-rated ski and snowboard equipment.
          </p>
        </div>
        <div class="mb-8 flex justify-center">
          <div class="inline-flex bg-gray-100 p-1 rounded-full">
            <button
              v-for="(category, index) in equipmentCategories"
              :key="index"
              @click="activeCategory = category"
              :class="`px-4 py-2 rounded-full text-sm font-medium transition-colors duration-200 ${
                activeCategory === category
                  ? 'bg-white shadow-sm'
                  : 'text-gray-600 hover:text-gray-900'
              } !rounded-button whitespace-nowrap cursor-pointer`"
            >
              {{ category }}
            </button>
          </div>
        </div>
        <div class="relative">
          <swiper
            :modules="swiperModules"
            :slides-per-view="1"
            :space-between="20"
            :pagination="{ clickable: true }"
            :breakpoints="{
              '640': {
                slidesPerView: 2,
                spaceBetween: 20,
              },
              '768': {
                slidesPerView: 3,
                spaceBetween: 30,
              },
              '1024': {
                slidesPerView: 4,
                spaceBetween: 30,
              },
            }"
            class="equipment-swiper"
          >
            <swiper-slide
              v-for="(item, index) in filteredEquipment"
              :key="index"
            >
              <div class="bg-white rounded-xl shadow-md overflow-hidden h-full">
                <div class="h-48 overflow-hidden">
                  <img
                    :src="item.image"
                    :alt="item.name"
                    class="w-full h-full object-cover object-top"
                  />
                </div>
                <div class="p-4">
                  <div class="text-sm text-gray-500 mb-1">{{ item.brand }}</div>
                  <h3 class="font-bold mb-2">{{ item.name }}</h3>
                  <div class="flex items-center mb-2">
                    <div class="text-yellow-400 flex">
                      <i
                        v-for="n in 5"
                        :key="n"
                        :class="`fas fa-star ${
                          n <= item.rating ? '' : 'text-gray-300'
                        }`"
                      ></i>
                    </div>
                    <span class="text-sm text-gray-500 ml-2"
                      >({{ item.reviews }})</span
                    >
                  </div>
                  <div class="text-gray-800 font-medium mb-3">
                    {{ item.price }}
                  </div>
                  <button
                    class="text-blue-600 font-medium flex items-center hover:text-blue-800 !rounded-button whitespace-nowrap cursor-pointer"
                  >
                    Shop Now <i class="fas fa-arrow-right ml-2"></i>
                  </button>
                </div>
              </div>
            </swiper-slide>
          </swiper>
        </div>
      </div>
    </section>
    <!-- Community Section -->
    <section class="py-16 bg-gray-50">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">
            Join Our Community
          </h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Connect with fellow ski enthusiasts, share your adventures, and get
            inspired by amazing stories from slopes around the world.
          </p>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
          <div
            v-for="(post, index) in communityPosts"
            :key="index"
            class="relative group overflow-hidden rounded-lg cursor-pointer"
          >
            <img
              :src="post.image"
              :alt="post.username"
              class="w-full h-64 object-cover object-top transition-transform duration-500 group-hover:scale-110"
            />
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-4"
            >
              <div class="text-white">
                <div class="flex items-center mb-2">
                  <div class="w-8 h-8 rounded-full overflow-hidden mr-2">
                    <img
                      :src="post.userAvatar"
                      :alt="post.username"
                      class="w-full h-full object-cover"
                    />
                  </div>
                  <span class="font-medium">{{ post.username }}</span>
                </div>
                <p class="text-sm">{{ post.caption }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-12 text-center">
          <button
            class="bg-blue-600 text-white px-6 py-3 rounded-full hover:bg-blue-700 transition duration-300 !rounded-button whitespace-nowrap cursor-pointer"
          >
            Join Community
          </button>
          <div class="mt-8 flex justify-center space-x-6">
            <a
              href="#"
              class="text-gray-600 hover:text-blue-600 transition-colors duration-200 cursor-pointer"
            >
              <i class="fab fa-instagram text-2xl"></i>
            </a>
            <a
              href="#"
              class="text-gray-600 hover:text-blue-600 transition-colors duration-200 cursor-pointer"
            >
              <i class="fab fa-facebook text-2xl"></i>
            </a>
            <a
              href="#"
              class="text-gray-600 hover:text-blue-600 transition-colors duration-200 cursor-pointer"
            >
              <i class="fab fa-twitter text-2xl"></i>
            </a>
            <a
              href="#"
              class="text-gray-600 hover:text-blue-600 transition-colors duration-200 cursor-pointer"
            >
              <i class="fab fa-youtube text-2xl"></i>
            </a>
          </div>
        </div>
      </div>
    </section>
    <!-- Newsletter Signup -->
    <section class="py-16 bg-blue-600">
      <div class="container mx-auto px-4">
        <div class="max-w-3xl mx-auto text-center text-white">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Stay Updated</h2>
          <p class="mb-8">
            Subscribe to our newsletter and be the first to know about fresh
            powder alerts, exclusive deals, and insider tips for your next ski
            adventure.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 max-w-md mx-auto">
            <input
              type="email"
              placeholder="Your email address"
              class="flex-grow px-4 py-3 rounded-full text-gray-800 border-none focus:outline-none focus:ring-2 focus:ring-blue-300"
            />
            <button
              class="bg-white text-blue-600 px-6 py-3 rounded-full hover:bg-gray-100 transition duration-300 whitespace-nowrap !rounded-button cursor-pointer"
            >
              Subscribe
            </button>
          </div>
          <p class="text-sm mt-4 text-blue-200">
            By subscribing, you agree to our
            <a href="#" class="underline hover:text-white cursor-pointer"
              >Privacy Policy</a
            >.
          </p>
        </div>
      </div>
    </section>
    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div>
            <div class="text-2xl font-bold mb-4">
              <i class="fas fa-mountain mr-2"></i>
              <span>PeakSkier</span>
            </div>
            <p class="text-gray-400 mb-4">
              Your ultimate guide to the world of skiing and snowboarding
              adventures.
            </p>
            <div class="flex space-x-4">
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
              >
                <i class="fab fa-facebook-f"></i>
              </a>
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
              >
                <i class="fab fa-twitter"></i>
              </a>
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
              >
                <i class="fab fa-instagram"></i>
              </a>
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
              >
                <i class="fab fa-youtube"></i>
              </a>
            </div>
          </div>
          <div>
            <h3 class="text-lg font-bold mb-4">Quick Links</h3>
            <ul class="space-y-2">
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Home</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Destinations</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Equipment</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Training</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Community</a
                >
              </li>
            </ul>
          </div>
          <div>
            <h3 class="text-lg font-bold mb-4">Resources</h3>
            <ul class="space-y-2">
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Blog</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Ski Schools</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Safety Guide</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >Equipment Reviews</a
                >
              </li>
              <li>
                <a
                  href="#"
                  class="text-gray-400 hover:text-white transition-colors duration-200 cursor-pointer"
                  >FAQs</a
                >
              </li>
            </ul>
          </div>
          <div>
            <h3 class="text-lg font-bold mb-4">Contact Us</h3>
            <ul class="space-y-2">
              <li class="flex items-start">
                <i class="fas fa-map-marker-alt mt-1 mr-3 text-gray-400"></i>
                <span class="text-gray-400"
                  >123 Powder Lane, Alpine Heights, CO 80425</span
                >
              </li>
              <li class="flex items-center">
                <i class="fas fa-phone mr-3 text-gray-400"></i>
                <span class="text-gray-400">+1 (800) SKI-PEAK</span>
              </li>
              <li class="flex items-center">
                <i class="fas fa-envelope mr-3 text-gray-400"></i>
                <span class="text-gray-400">info@peakskier.com</span>
              </li>
            </ul>
            <div class="mt-4 flex items-center space-x-3">
              <div class="text-gray-400">
                <i class="fab fa-cc-visa text-xl"></i>
              </div>
              <div class="text-gray-400">
                <i class="fab fa-cc-mastercard text-xl"></i>
              </div>
              <div class="text-gray-400">
                <i class="fab fa-cc-amex text-xl"></i>
              </div>
              <div class="text-gray-400">
                <i class="fab fa-cc-paypal text-xl"></i>
              </div>
            </div>
          </div>
        </div>
        <div
          class="border-t border-gray-800 mt-10 pt-6 flex flex-col md:flex-row justify-between items-center"
        >
          <p class="text-gray-400 text-sm mb-4 md:mb-0">
            © 2025 PeakSkier. All rights reserved.
          </p>
          <div class="flex space-x-6">
            <a
              href="#"
              class="text-gray-400 hover:text-white text-sm transition-colors duration-200 cursor-pointer"
              >Terms of Service</a
            >
            <a
              href="#"
              class="text-gray-400 hover:text-white text-sm transition-colors duration-200 cursor-pointer"
              >Privacy Policy</a
            >
            <a
              href="#"
              class="text-gray-400 hover:text-white text-sm transition-colors duration-200 cursor-pointer"
              >Cookie Policy</a
            >
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>
<script lang="ts" setup>
import { ref, onMounted, computed } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination, Autoplay } from "swiper/modules";
import * as echarts from "echarts";
const swiperModules = [Pagination, Autoplay];
const mapContainer = ref<HTMLElement | null>(null);
const activeCategory = ref("All Gear");
// Featured Destinations
const destinations = [
  {
    name: "Whistler Blackcomb, Canada",
    difficulty: "Advanced",
    difficultyColor: "bg-red-100 text-red-800",
    description:
      "North America's largest ski resort offering breathtaking views, diverse terrain, and world-class amenities for all skill levels.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Whistler%20Blackcomb%20ski%20resort%20in%20Canada%20with%20snow-covered%20mountains%2C%20aerial%20view%20of%20ski%20slopes%2C%20gondolas%2C%20and%20lodges%20nestled%20in%20valley%2C%20pristine%20snow%20conditions%2C%20blue%20sky%20with%20scattered%20clouds%2C%20majestic%20mountain%20peaks%20in%20background%2C%20professional%20landscape%20photography&width=600&height=400&seq=dest1&orientation=landscape",
  },
  {
    name: "Chamonix, France",
    difficulty: "Expert",
    difficultyColor: "bg-purple-100 text-purple-800",
    description:
      "Home to the majestic Mont Blanc, offering legendary off-piste terrain, steep descents, and authentic Alpine charm.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Chamonix%20ski%20resort%20in%20France%20with%20Mont%20Blanc%20in%20background%2C%20dramatic%20alpine%20landscape%20with%20steep%20slopes%2C%20charming%20European%20mountain%20village%20with%20traditional%20architecture%2C%20cable%20cars%20ascending%20mountains%2C%20pristine%20powder%20snow%20conditions%2C%20blue%20sky%20with%20dramatic%20clouds&width=600&height=400&seq=dest2&orientation=landscape",
  },
  {
    name: "Niseko, Japan",
    difficulty: "Intermediate",
    difficultyColor: "bg-blue-100 text-blue-800",
    description:
      "Famous for its legendary powder snow, stunning views of Mt. Yotei, and unique Japanese cultural experience.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Niseko%20ski%20resort%20in%20Japan%20with%20Mount%20Yotei%20in%20background%2C%20deep%20powder%20snow%20conditions%2C%20Japanese%20style%20wooden%20buildings%20with%20snow-covered%20roofs%2C%20snow-laden%20trees%2C%20misty%20atmospheric%20conditions%2C%20skiers%20enjoying%20powder%20snow%2C%20dramatic%20winter%20landscape%20photography&width=600&height=400&seq=dest3&orientation=landscape",
  },
  {
    name: "Aspen Snowmass, USA",
    difficulty: "All Levels",
    difficultyColor: "bg-green-100 text-green-800",
    description:
      "Four mountains of world-class terrain combined with luxury amenities and a vibrant après-ski scene.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Aspen%20Snowmass%20ski%20resort%20in%20Colorado%20with%20luxury%20mountain%20lodges%2C%20pristine%20groomed%20ski%20runs%2C%20aspen%20trees%20with%20golden%20leaves%2C%20dramatic%20Rocky%20Mountain%20peaks%2C%20blue%20sky%20backdrop%2C%20gondolas%20and%20chairlifts%2C%20upscale%20ski%20village%20with%20shops%20and%20restaurants%2C%20professional%20landscape%20photography&width=600&height=400&seq=dest4&orientation=landscape",
  },
  {
    name: "Zermatt, Switzerland",
    difficulty: "Intermediate",
    difficultyColor: "bg-blue-100 text-blue-800",
    description:
      "Ski in the shadow of the iconic Matterhorn with glacier skiing, charming car-free village, and Swiss precision.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Zermatt%20ski%20resort%20in%20Switzerland%20with%20iconic%20Matterhorn%20peak%20in%20background%2C%20Swiss%20alpine%20village%20with%20traditional%20chalets%2C%20snow-covered%20landscape%2C%20cable%20cars%20and%20ski%20lifts%2C%20pristine%20ski%20slopes%2C%20dramatic%20mountain%20scenery%2C%20blue%20sky%20with%20wispy%20clouds%2C%20professional%20landscape%20photography&width=600&height=400&seq=dest5&orientation=landscape",
  },
  {
    name: "Queenstown, New Zealand",
    difficulty: "All Levels",
    difficultyColor: "bg-green-100 text-green-800",
    description:
      "Southern Hemisphere's adventure capital with stunning alpine scenery, reliable snow, and vibrant nightlife.",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Queenstown%20New%20Zealand%20ski%20resort%20with%20dramatic%20Southern%20Alps%20mountains%2C%20Lake%20Wakatipu%20in%20foreground%2C%20snow-covered%20peaks%2C%20adventure%20town%20nestled%20in%20valley%2C%20ski%20slopes%20with%20chairlifts%2C%20dramatic%20clouds%2C%20pristine%20snow%20conditions%2C%20adventure%20sports%20atmosphere%2C%20professional%20landscape%20photography&width=600&height=400&seq=dest6&orientation=landscape",
  },
];
// Resort Weather Data
const resortWeather = [
  {
    name: "Whistler Blackcomb",
    temperature: "-2°C / 28°F",
    condition: "Light Snow",
    icon: "fas fa-snowflake",
  },
  {
    name: "Aspen Snowmass",
    temperature: "-5°C / 23°F",
    condition: "Sunny",
    icon: "fas fa-sun",
  },
  {
    name: "Chamonix",
    temperature: "-8°C / 17°F",
    condition: "Partly Cloudy",
    icon: "fas fa-cloud-sun",
  },
  {
    name: "Zermatt",
    temperature: "-4°C / 25°F",
    condition: "Clear",
    icon: "fas fa-sun",
  },
];
// Snow Reports
const snowReports = [
  {
    resort: "Whistler Blackcomb",
    depth: "210 cm / 83 in",
    trails: "200/200",
    updated: "April 17, 2025",
  },
  {
    resort: "Aspen Snowmass",
    depth: "175 cm / 69 in",
    trails: "320/330",
    updated: "April 17, 2025",
  },
  {
    resort: "Chamonix",
    depth: "240 cm / 94 in",
    trails: "90/100",
    updated: "April 17, 2025",
  },
  {
    resort: "Zermatt",
    depth: "195 cm / 77 in",
    trails: "145/145",
    updated: "April 17, 2025",
  },
];
// Equipment Categories
const equipmentCategories = [
  "All Gear",
  "Skis",
  "Boots",
  "Clothing",
  "Accessories",
];
// Equipment Data
const equipment = [
  {
    category: "Skis",
    name: "Alpine Pro X2",
    brand: "Rossignol",
    price: "$599 - $799",
    rating: 5,
    reviews: 128,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20alpine%20skis%20on%20pristine%20white%20snow%20background%2C%20high-end%20modern%20ski%20design%20with%20vibrant%20colors%2C%20detailed%20bindings%20and%20edges%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20ski%20technology%20and%20craftsmanship&width=400&height=300&seq=eq1&orientation=landscape",
  },
  {
    category: "Skis",
    name: "Freeride Master",
    brand: "Atomic",
    price: "$649 - $849",
    rating: 4,
    reviews: 94,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20freeride%20skis%20on%20pristine%20white%20snow%20background%2C%20wide%20powder%20skis%20with%20modern%20design%20and%20vibrant%20graphics%2C%20detailed%20bindings%20and%20edges%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20ski%20technology%20and%20craftsmanship&width=400&height=300&seq=eq2&orientation=landscape",
  },
  {
    category: "Boots",
    name: "Alpine Performance",
    brand: "Salomon",
    price: "$399 - $599",
    rating: 5,
    reviews: 76,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20ski%20boots%20on%20pristine%20white%20background%2C%20high-performance%20alpine%20ski%20boots%20with%20detailed%20buckles%20and%20adjustments%2C%20modern%20design%20with%20vibrant%20accents%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20boot%20technology%20and%20craftsmanship&width=400&height=300&seq=eq3&orientation=landscape",
  },
  {
    category: "Clothing",
    name: "Pro Shell Jacket",
    brand: "The North Face",
    price: "$349 - $499",
    rating: 4,
    reviews: 112,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20ski%20jacket%20on%20pristine%20white%20background%2C%20high-performance%20waterproof%20shell%20with%20modern%20design%20and%20vibrant%20colors%2C%20detailed%20zippers%20and%20pockets%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20jacket%20technology%20and%20craftsmanship&width=400&height=300&seq=eq4&orientation=landscape",
  },
  {
    category: "Clothing",
    name: "Insulated Ski Pants",
    brand: "Arc'teryx",
    price: "$299 - $449",
    rating: 5,
    reviews: 89,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20ski%20pants%20on%20pristine%20white%20background%2C%20high-performance%20insulated%20pants%20with%20modern%20design%20and%20vibrant%20colors%2C%20detailed%20pockets%20and%20ventilation%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20pants%20technology%20and%20craftsmanship&width=400&height=300&seq=eq5&orientation=landscape",
  },
  {
    category: "Accessories",
    name: "Pro Vision Goggles",
    brand: "Smith",
    price: "$179 - $249",
    rating: 4,
    reviews: 145,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20ski%20goggles%20on%20pristine%20white%20background%2C%20high-performance%20goggles%20with%20interchangeable%20lenses%20and%20modern%20frame%20design%2C%20vibrant%20lens%20colors%20with%20anti-fog%20technology%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20goggle%20technology%20and%20craftsmanship&width=400&height=300&seq=eq6&orientation=landscape",
  },
  {
    category: "Accessories",
    name: "Carbon Fiber Poles",
    brand: "Black Diamond",
    price: "$129 - $179",
    rating: 5,
    reviews: 67,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20ski%20poles%20on%20pristine%20white%20background%2C%20lightweight%20carbon%20fiber%20poles%20with%20ergonomic%20grips%20and%20adjustable%20straps%2C%20modern%20design%20with%20vibrant%20accents%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20pole%20technology%20and%20craftsmanship&width=400&height=300&seq=eq7&orientation=landscape",
  },
  {
    category: "Boots",
    name: "Freestyle Tech",
    brand: "Dalbello",
    price: "$349 - $499",
    rating: 4,
    reviews: 58,
    image:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20freestyle%20ski%20boots%20on%20pristine%20white%20background%2C%20high-performance%20park%20and%20pipe%20boots%20with%20flex%20adjustment%2C%20modern%20design%20with%20vibrant%20colors%2C%20clean%20product%20photography%20with%20soft%20shadows%2C%20minimalist%20background%20to%20highlight%20the%20boot%20technology%20and%20craftsmanship&width=400&height=300&seq=eq8&orientation=landscape",
  },
];
// Filter equipment based on active category
const filteredEquipment = computed(() => {
  if (activeCategory.value === "All Gear") {
    return equipment;
  }
  return equipment.filter((item) => item.category === activeCategory.value);
});
// Community Posts
const communityPosts = [
  {
    username: "powder_chaser",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20male%20skier%20with%20helmet%20and%20goggles%2C%20snowy%20mountain%20background%2C%20warm%20lighting%2C%20candid%20expression%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar1&orientation=squarish",
    caption:
      "Found the perfect powder stash at Whistler today! #powderday #skiing",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Skier%20carving%20through%20deep%20powder%20snow%20with%20snow%20spray%2C%20dramatic%20mountain%20backdrop%2C%20blue%20sky%2C%20action%20sports%20photography%2C%20dynamic%20angle%20capturing%20the%20thrill%20of%20powder%20skiing%2C%20professional%20ski%20photography%20with%20perfect%20lighting&width=400&height=400&seq=comm1&orientation=squarish",
  },
  {
    username: "mountain_girl",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20female%20skier%20with%20beanie%20hat%20and%20sunglasses%2C%20snowy%20mountain%20background%2C%20warm%20lighting%2C%20candid%20smile%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar2&orientation=squarish",
    caption: "Summit views that make the climb worth it! #alpineskiing #views",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Panoramic%20mountain%20summit%20view%20from%20skier%20perspective%2C%20vast%20snow-covered%20peaks%2C%20dramatic%20clouds%2C%20alpine%20landscape%2C%20golden%20hour%20lighting%2C%20sense%20of%20achievement%20and%20solitude%2C%20professional%20landscape%20photography&width=400&height=400&seq=comm2&orientation=squarish",
  },
  {
    username: "ski_instructor",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20ski%20instructor%20with%20professional%20attire%2C%20snowy%20mountain%20background%2C%20warm%20lighting%2C%20friendly%20smile%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar3&orientation=squarish",
    caption: "Teaching the next generation of shredders! #skischool #kids",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Ski%20instructor%20teaching%20children%20in%20colorful%20ski%20outfits%2C%20gentle%20learning%20slope%2C%20playful%20atmosphere%2C%20kids%20in%20ski%20school%20formation%2C%20patient%20instruction%2C%20blue%20sky%20day%2C%20professional%20photography%20capturing%20learning%20moments&width=400&height=400&seq=comm3&orientation=squarish",
  },
  {
    username: "freestyle_king",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20male%20freestyle%20skier%20with%20stylish%20hat%20and%20sunglasses%2C%20terrain%20park%20background%2C%20warm%20lighting%2C%20confident%20expression%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar4&orientation=squarish",
    caption: "Stomped my first 720 today! #freestyleskiing #terrainpark",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Freestyle%20skier%20performing%20aerial%20trick%20in%20terrain%20park%2C%20mid-rotation%20720%20spin%2C%20perfect%20form%20against%20blue%20sky%2C%20snow-covered%20jump%2C%20action%20sports%20photography%20freezing%20the%20moment%20of%20peak%20action%2C%20professional%20ski%20photography&width=400&height=400&seq=comm4&orientation=squarish",
  },
  {
    username: "backcountry_explorer",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20backcountry%20skier%20with%20avalanche%20safety%20equipment%2C%20remote%20mountain%20background%2C%20warm%20lighting%2C%20determined%20expression%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar5&orientation=squarish",
    caption: "Earned our turns in the backcountry today. #skitouring #nolifts",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Backcountry%20skiers%20skinning%20up%20remote%20mountain%20slope%2C%20untouched%20powder%20snow%2C%20vast%20wilderness%2C%20no%20ski%20lifts%20in%20sight%2C%20ski%20touring%20equipment%2C%20sense%20of%20adventure%20and%20solitude%2C%20professional%20adventure%20photography&width=400&height=400&seq=comm5&orientation=squarish",
  },
  {
    username: "apres_ski_lover",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20relaxed%20skier%20with%20stylish%20apr%C3%A8s-ski%20attire%2C%20mountain%20lodge%20background%2C%20warm%20lighting%2C%20joyful%20expression%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar6&orientation=squarish",
    caption: "The perfect way to end a day on the slopes! #apresski #fireplace",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Cozy%20mountain%20lodge%20interior%20with%20roaring%20fireplace%2C%20skiers%20relaxing%20with%20drinks%20after%20day%20on%20slopes%2C%20rustic%20wooden%20decor%2C%20warm%20ambient%20lighting%2C%20ski%20equipment%20nearby%2C%20atmosphere%20of%20relaxation%20and%20celebration%2C%20professional%20lifestyle%20photography&width=400&height=400&seq=comm6&orientation=squarish",
  },
  {
    username: "snow_chaser",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20an%20adventurous%20skier%20with%20helmet%20and%20face%20protection%2C%20extreme%20mountain%20background%2C%20dramatic%20lighting%2C%20intense%20expression%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20headshot&width=100&height=100&seq=avatar7&orientation=squarish",
    caption: "First tracks on a bluebird powder day! #freshpowder #earlybird",
    image:
      "https://zyp.readdy.ai/api/search-image?query=First%20tracks%20in%20pristine%20powder%20snow%2C%20early%20morning%20light%20with%20long%20shadows%2C%20untouched%20snow%20surface%20with%20perfect%20ski%20lines%2C%20bluebird%20sky%2C%20sense%20of%20solitude%20and%20freshness%2C%20professional%20ski%20photography%20capturing%20the%20perfect%20morning&width=400&height=400&seq=comm7&orientation=squarish",
  },
  {
    username: "ski_family",
    userAvatar:
      "https://zyp.readdy.ai/api/search-image?query=Professional%20portrait%20photo%20of%20a%20family%20of%20skiers%20with%20matching%20outfits%2C%20resort%20background%2C%20warm%20lighting%2C%20happy%20expressions%2C%20outdoor%20adventure%20photography%20style%2C%20high%20resolution%20group%20headshot&width=100&height=100&seq=avatar8&orientation=squarish",
    caption:
      "Three generations hitting the slopes together! #familyski #memories",
    image:
      "https://zyp.readdy.ai/api/search-image?query=Multi-generational%20family%20skiing%20together%20on%20groomed%20slope%2C%20grandparents%20with%20parents%20and%20children%2C%20matching%20ski%20outfits%2C%20joyful%20interaction%2C%20blue%20sky%20day%20at%20ski%20resort%2C%20professional%20family%20photography%20capturing%20shared%20experience&width=400&height=400&seq=comm8&orientation=squarish",
  },
];
onMounted(() => {
  // Initialize map chart
  if (mapContainer.value) {
    const mapChart = echarts.init(mapContainer.value);
    const option = {
      animation: false,
      title: {
        text: "崇礼滑雪场分布",
        left: "center",
        textStyle: {
          color: "#333",
        },
      },
      tooltip: {
        trigger: "item",
        formatter: "{b}: {c} (雪深厘米)",
      },
      visualMap: {
        min: 50,
        max: 200,
        text: ["高", "低"],
        realtime: false,
        calculable: true,
        inRange: {
          color: ["#313695", "#4575b4", "#74add1", "#abd9e9", "#e0f3f8"],
        },
      },
      geo: {
        map: "china",
        roam: true,
        center: [115.282, 40.975], // 崇礼区域坐标
        zoom: 8,
        emphasis: {
          itemStyle: {
            areaColor: "#f4f4f4",
            borderColor: "#404a59",
          },
        },
      },
      series: [
        {
          name: "雪深",
          type: "scatter",
          coordinateSystem: "geo",
          symbolSize: function (val) {
            return val[2] / 10;
          },
          itemStyle: {
            color: "#4575b4",
          },
          emphasis: {
            label: {
              show: true,
              formatter: "{b}",
            },
          },
          data: [
            { name: "万龙滑雪场", value: [115.404, 40.96, 180] },
            { name: "云顶滑雪场", value: [115.468, 40.957, 165] },
            { name: "太舞滑雪场", value: [115.389, 40.912, 170] },
            { name: "富龙滑雪场", value: [115.282, 40.975, 155] },
            { name: "长城岭滑雪场", value: [115.322, 40.932, 160] },
            { name: "多乐美地滑雪场", value: [115.435, 40.942, 175] },
            { name: "冰雪小镇", value: [115.412, 40.967, 150] },
          ],
        },
      ],
    };
    mapChart.setOption(option);
    window.addEventListener("resize", () => {
      mapChart.resize();
    });
  }
});
</script>
<style scoped>
.swiper {
  padding-bottom: 50px;
}
.swiper :deep(.swiper-pagination) {
  bottom: 0;
}
.swiper :deep(.swiper-pagination-bullet) {
  width: 10px;
  height: 10px;
  background: #ccc;
  opacity: 1;
}
.swiper :deep(.swiper-pagination-bullet-active) {
  background: #3b82f6;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
