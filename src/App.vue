<script setup>
import Navbar from '@/components/Navbar.vue'
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobList from '@/components/JobList.vue'
</script>

<template>
  <navbar/>
  <hero title="Become a Vue Dev motherfucker" subtitle="Find a fucking job !!!"/>
  <home-cards/>
  <job-list :limit="3" :show-button="false"/>
</template>

<style scoped>

</style>
