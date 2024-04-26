<template>
  <div class="container">
    <div class="mb-3">
      <input
        type="text"
        v-model="searchTerm"
        placeholder="Rechercher une compagnie"
        class="form-control"
        @keyup.enter="searchCompanies"
      />
    </div>
    <div
      class="card mb-3"
      v-for="companie in filteredCompanies"
      :key="companie['Company Name']"
    >
      <div class="d-flex align-items-center">
        <img :src="companie.Logo" class="rounded-circle" alt="Profil" />
        <div class="ps-3">
          <h6>{{ companie["Company Name"] }}</h6>
          <span class="text-muted small pt-2 ps-1">{{ companie.About }}</span>
        </div>
      </div>
      <div class="card-footer">
        <div class="row">
          <div class="col-6">Vue: {{ companie.vue }}</div>
          <div class="col-6">
            <button type="button" class="btn btn-primary">Voir</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from "axios";
import { defineProps, ref, onMounted, computed } from "vue";

const companies = ref([]); // Initialize as an empty array
const searchTerm = ref(""); // Search term for filtering

interface Company {
  "Company Name": string;
  Logo: string;
  About: string;
  vue: string;
}

onMounted(async () => {
  try {
    const response = await axios.get(
      "https://retoolapi.dev/Oal4aL/listing-company" // Replace with endpoint for all companies
    );
    companies.value = response.data;
  } catch (error) {
    console.error("Une erreur s'est produite:", error);
  }
});

const filteredCompanies = computed(() => {
  return companies.value.filter((company) =>
    company["Company Name"]
      .toLowerCase()
      .includes(searchTerm.value.toLowerCase())
  );
});

function searchCompanies() {
  if (searchTerm.value.length < 3) {
    console.warn("Search term must be at least 3 characters long.");
  }
}
</script>

<style scoped></style>
