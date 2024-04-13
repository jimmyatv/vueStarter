<template>
  <div id="app">
    <MainHeader />
    <OurHero />
    <UsersList/>
    <PhonesList/>
    <WorkersList/>
  </div>
</template>

<script setup>
import { defineComponent } from 'vue';
import MainHeader from '@/components/MainHeader.vue';
import OurHero from '@/components/OurHero.vue';
import UsersList from '@/components/UsersList.vue'
import PhonesList from '@/components/PhonesList.vue'
import WorkersList from '@/components/WorkersList.vue'

defineComponent({
  components: {
    MainHeader,
    OurHero,
    UsersList,
    PhonesList,
    WorkersList
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
