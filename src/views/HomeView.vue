<template>
  <section class="section">
    <div class="row align-items-top">
      <div class="col-lg-3">
      </div>

      <div class="col-lg-6">
        <div class="form-floating mb-3">
          <input type="text" class="form-control" id="floatingInput" placeholder="text">
          <label for="floatingInput">Search</label>
        </div>
        <div class="pagetitle">
          <nav>
            <ol class="breadcrumb">
              <li class="breadcrumb-item"><a href="index.html">Home</a></li>
              <li class="breadcrumb-item">List</li>
              <li class="breadcrumb-item active">Compagnies</li>
            </ol>
          </nav>
        </div><!-- End Page Title -->
        
        <Compagnies></Compagnies>
      </div>

      <div class="col-lg-3">

      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
import Compagnies from '../components/Compagnies.vue'
import Header from '../components/Header.vue'
</script>

<style>

</style>
