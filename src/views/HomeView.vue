<script setup>
import Hero from '@/components/HeroComp.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobListings from '@/components/JobListings.vue'
</script>

<template>
  <Hero title="Pratik's First Vue Project" />
  <HomeCards />
  <JobListings :limit="3" :showButton="true" />
</template>
