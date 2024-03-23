<template>
  <div id="app">
    <MainHeader />
    <OurHero />
  </div>
</template>

<script setup>
import MainHeader from '@/components/MainHeader.vue';
import OurHero from '@/components/OurHero.vue';
import { defineComponent } from 'vue';

defineComponent({
  components: {
    MainHeader,
    OurHero
  }
})
</script>

<style>
* {
  margin: 0;
  padding: 0; 
  box-sizing: border-box;
}
</style>
