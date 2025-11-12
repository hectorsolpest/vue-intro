<script setup>
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobList from '@/components/JobList.vue'
</script>

<template>
  <hero title="Become a Vue Dev" subtitle="Find a job !!!"/>
  <home-cards/>
  <job-list :limit="3" :show-button="true"/>
</template>
