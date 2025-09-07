<script setup>
import { onMounted, reactive } from 'vue'
import JobCard from '@/components/JobCard.vue'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
import axios from 'axios'

//state es igual a ref, se usa para reactividad pero solo para objetos
//ref permite objetos y tipos primitivos, se puede hacer de ambas formas
const state = reactive({
  jobs:[],
  isLoading: true,
})
defineProps({
  limit:{
    type:Number
  },
  showButton:{
    type:Boolean,
    default:false
  }
})

onMounted(async () =>{
  try {
    const response = await axios.get('http://localhost:5000/jobs')
    state.jobs = response.data
  }
  catch (e) {
    console.log(e)
  }
  finally {
    state.isLoading = false
  }
})

</script>

<template>
  <section class="bg-green-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
        Browse Jobs
      </h2>
      <div v-if="state.isLoading" class="text-center text-gray-500 py-6">
        <pulse-loader/>
      </div>
      <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <job-card v-for="job in state.jobs.slice(0,limit || state.jobs.lenght)" :key="job.id" :job="job"/>
      </div>
    </div>
  </section>

  <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
    <RouterLink
      to="/jobs"
      class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
    >View All Jobs</RouterLink
    >
  </section>
</template>

<style scoped>

</style>
