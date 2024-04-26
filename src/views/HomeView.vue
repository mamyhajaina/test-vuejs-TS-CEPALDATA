<template>
  <section class="section">
    <div class="row align-items-top">
      <div class="col-lg-3">
      </div>

      <div class="col-lg-6">
        <div class="pagetitle">
          <nav>
            <ol class="breadcrumb">
              <li class="breadcrumb-item"><a href="index.html">Home</a></li>
              <li class="breadcrumb-item">Components</li>
              <li class="breadcrumb-item active">Cards</li>
            </ol>
          </nav>
        </div><!-- End Page Title -->
        
        <Compagnies></Compagnies>
      </div>

      <div class="col-lg-3">

        
        <!-- Special title treatmen -->
        <div class="card text-center">
          <div class="card-header">
            <ul class="nav nav-pills card-header-pills">
              <li class="nav-item">
                <a class="nav-link active" href="#">Active</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Link</a>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
              </li>
            </ul>
          </div>
          <div class="card-body">
            <h5 class="card-title">Special title treatment</h5>
            <p class="card-text">With supporting text below as a natural lead-in to additional content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
          </div>
        </div><!-- End Special title treatmen -->

      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
import Compagnies from '../components/Compagnies.vue'
</script>

<style>

</style>
