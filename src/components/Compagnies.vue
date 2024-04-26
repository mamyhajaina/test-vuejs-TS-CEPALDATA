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

  <nav aria-label="...">
    <ul class="pagination">
      <li class="page-item disabled">
        <a class="page-link" href="#" tabindex="-1" aria-disabled="true">Previous</a>
      </li>
      <li class="page-item"><a class="page-link" href="#">1</a></li>
      <li class="page-item active" aria-current="page">
        <a class="page-link" href="#">2</a>
      </li>
      <li class="page-item"><a class="page-link" href="#">3</a></li>
      <li class="page-item">
        <a class="page-link" href="#">Next</a>
      </li>
    </ul>
  </nav>
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
