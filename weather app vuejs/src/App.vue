<script setup>
import { ref } from 'vue'
import SearchInput from './components/icons/SearchInput.vue';
import WeatherCard from './components/icons/WeatherCard.vue';

const places = ref([])

const addPlace = (data) => {
  places.value.push(data)
}

const deletePlace = (name) => {
  console.log(name)
}
</script>
<template>
  <main>
    <!-- Date -->
    <div class="text-center mb-6">
      {{ 
        new Date().toLocaleDateString('en-us', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        })
      }}

      <!--Search-->
      <div>
        <SearchInput @place-data="addPlace"/>
      </div>
      <!-- Card -->
       <div class="grid grid-cols-2 gap-4">
        <div v-for="(place, idx) in places" :key="idx">
          <WeatherCard :place="place" @delete-place="deletePlace"/>
        </div>
      </div>
    </div>
  </main>
</template>