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
    <div v-for="company in paginatedCompanies" :key="company['Company Name']">
      <div class="card mb-3">
        <div class="d-flex align-items-center">
          <img :src="company.Logo" class="rounded-circle" alt="Profil" />
          <div class="ps-3">
            <h6>{{ company["Company Name"] }}</h6>
            <span class="text-muted small pt-2 ps-1">{{ company.About }}</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="row">
            <div class="col-6">Vue: {{ company.vue }}</div>
            <div class="col-6">
              <button type="button" class="btn btn-primary">Voir</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav aria-label="...">
      <ul class="pagination">
        <li class="page-item" :class="{ disabled: currentPage === 1 }">
          <a class="page-link" href="#" @click="prevPage">Previous</a>
        </li>
        <li v-for="n in totalPages" :key="n" class="page-item">
          <a
            class="page-link"
            :class="{ active: currentPage === n }"
            @click="setPage(n)"
          >
            {{ n }}
          </a>
        </li>
        <li class="page-item" :class="{ disabled: currentPage === totalPages }">
          <a class="page-link" href="#" @click="nextPage">Next</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup lang="ts">
import axios from "axios";
import { defineProps, ref, onMounted, computed } from "vue";

const companies = ref([]); // Initialize as an empty array
const searchTerm = ref(""); // Search term for filtering
const currentPage = ref(1); // Current page number (initially set to 1)
const itemsPerPage = 3; // Items to display per page

interface Company {
  "Company Name": string;
  Logo: string;
  About: string;
  vue: string;
}

onMounted(async () => {
  try {
    const response = await axios.get(
      "https://retoolapi.dev/Oal4aL/listing-company"
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

const totalPages = computed(() =>
  Math.ceil(filteredCompanies.value.length / itemsPerPage)
);

const paginatedCompanies = computed(() => {
  if (filteredCompanies.value.length === 0) {
    return [];
  }

  const startIndex = (currentPage.value - 1) * itemsPerPage;
  const endIndex = startIndex + itemsPerPage;
  return filteredCompanies.value.slice(startIndex, endIndex);
});

const isSearching = computed(() => searchTerm.value.length > 0);

function searchCompanies() {
  if (searchTerm.value.length < 3) {
    console.warn("Search term must be at least 3 characters long.");
  }
  currentPage.value = 1;
}

function prevPage() {
  if (currentPage.value > 1 && !isSearching.value) {
    currentPage.value--;
  }
}

function nextPage() {
  if (currentPage.value < totalPages.value && !isSearching.value) {
    currentPage.value++;
  }
}

function setPage(pageNumber: number) {
  if (!isSearching.value) {
    currentPage.value = pageNumber;
  }
}
</script>

<style scoped></style>
