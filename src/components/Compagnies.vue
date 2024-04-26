<template>
  <div class="container">
    <div class="mb-3">
      <input
        type="text"
        v-model="searchTerm"
        placeholder="Rechercher une compagnie"
        class="form-control"
      />
    </div>
    <div
      v-for="company in filteredAndPaginatedCompanies.data"
      :key="company['Company Name']"
    >
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
        <li
          v-for="n in filteredAndPaginatedCompanies.totalPages"
          :key="n"
          class="page-item"
        >
          <a
            class="page-link"
            :class="{ active: currentPage === n }"
            @click="setPage(n)"
          >
            {{ n }}
          </a>
        </li>
        <li
          class="page-item"
          :class="{
            disabled: currentPage === filteredAndPaginatedCompanies.totalPages,
          }"
        >
          <a class="page-link" href="#" @click="nextPage">Next</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup lang="ts">
import type { ICompany } from "@/interfaces/company.interface";
import axios from "axios";
import { defineProps, ref, onMounted, computed } from "vue";

const companies = ref<ICompany[]>([]); // Initialize as an empty array
const searchTerm = ref(""); // Search term for filtering
const currentPage = ref(1); // Current page number (initially set to 1)
const itemsPerPage = 3; // Items to display per page

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

const filteredAndPaginatedCompanies = computed<{
  totalPages: number;
  data: ICompany[];
}>(() => {
  const filtered = companies.value.filter((company) =>
    company["Company Name"]
      .toLowerCase()
      .includes(searchTerm.value.toLowerCase())
  );

  if (filtered.length === 0) {
    return {
      totalPages: 0,
      data: [],
    };
  }

  const startIndex = (currentPage.value - 1) * itemsPerPage;
  const endIndex = startIndex + itemsPerPage;

  const totalPages = Math.ceil(filtered.length / itemsPerPage);
  const data = filtered.slice(startIndex, endIndex);
  return {
    totalPages,
    data,
  };
});

function prevPage() {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
}

function nextPage() {
  if (currentPage.value < filteredAndPaginatedCompanies.value.totalPages) {
    currentPage.value++;
  }
}

function setPage(pageNumber: number) {
  currentPage.value = pageNumber;
}
</script>

<style scoped></style>
