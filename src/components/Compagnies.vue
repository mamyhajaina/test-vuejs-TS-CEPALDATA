<template>
  <section class="section dashboard">
    <div class="card" v-for="companie in companies">
      <div class="d-flex align-items-center">
        <img :src="companie.Logo" class="rounded-circle" alt="Profile">
        <div class="ps-3">
          <h6>{{ companie['Company Name'] }}</h6>
          <span class="text-muted small pt-2 ps-1">{{ companie.About }}</span>
    
        </div>
      </div>
      <div class="card-footer">
        <div class="row">
          <div class="col-6">
            Vue: {{ companie.vue }}
          </div>
          <div class="col-6">
            <button type="button" class="btn btn-primary">Voir</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import axios from 'axios';
import { defineProps, ref, onMounted } from 'vue';

const companies = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get('https://retoolapi.dev/Oal4aL/listing-company');
    companies.value = response.data;
    console.log('response.data',response.data);
  } catch (error) {
    console.error('Une erreur s\'est produite:', error);
  }
});
</script>


<style scoped>
</style>
