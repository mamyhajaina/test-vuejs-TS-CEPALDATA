<script setup lang="ts">
// defineProps<{
//   msg: string
// }>()
</script>

<template>

      <section class="section register min-vh-100 d-flex flex-column align-items-center justify-content-center py-4">
        <div class="container">
          <div class="row justify-content-center">
            <div class="col-lg-6">
              <div class="card mb-3 h-100 back-blue p-5">
                <div class="d-flex py-4 mb-5">
                  <a href="index.html" class="logo d-flex align-items-center w-auto">
                    <img src="/src/assets/img/logo.png" alt="">
                  </a>
                </div>

                <div class="float-left mt-5">
                  <div class="credits text-white">
                    <p class="text-white">
                        Ut in ea error laudantium quas omnis officia. Sit sed praesentium voluptas. Corrupti inventore consequatur nisi necessitatibus modi consequuntur soluta id. Enim autem est esse natus assumenda. Non sunt dignissimos officiis expedita. Consequatur sint repellendus voluptas.
                    Quidem sit est nulla ullam. Suscipit debitis ullam iusto dolorem animi dolorem numquam. Enim fuga ipsum dolor nulla quia ut.
                    </p>
                    John Doe
                  </div>
                </div>
              </div>
            </div>
            <div class="col-lg-6 col-md-6 d-flex flex-column align-items-center justify-content-center">

              <div class="mb-3">

                <div class="card-body">

                  <div class="pt-4 pb-2">
                    <h5 class="card-title text-center pb-0 fs-4">Welcome Back</h5>
                  </div>

                  <form class="row g-3 needs-validation" novalidate>

                    <div class="col-12">
                      <div class="form-floating mb-3">
                        <input type="email" class="form-control" id="floatingInput">
                        <label for="floatingInput">Email</label>
                      </div>
                    </div>

                    <div class="col-12">
                      <div class="form-floating mb-3">
                        <input type="email" class="form-control" id="PassWord">
                        <label for="floatingInput">PassWord</label>
                      </div>
                    </div>

                    <div class="col-12">
                      <button class="btn btn-primary w-100 btn-lg" type="submit">Login</button>
                    </div>

                    <div class="col-12 mt-4">
                      <div class="line-with-text">
                        <div class="line"></div>
                        <div class="text mx-3">Or</div>
                        <div class="line"></div>
                      </div>
                    </div>

                    <div class="col-12 mt-5">
                      <button type="button" class="btn btn-outline-secondary w-100 btn-lg">Log With Google</button>
                    </div>

                    <div class="col-12">
                      <button type="button" class="btn btn-outline-secondary w-100 btn-lg">Log With Facebook</button>
                    </div>
                  </form>

                </div>
              </div>

            </div>
          </div>
        </div>

      </section>
</template>

<style scoped>
.line-with-text {
  display: flex;
  align-items: center;
  text-align: center;
}
.line {
  flex-grow: 1;
  border-bottom: 1px solid black;
}
.back-blue {
  background-color: #4d81f5;
}
</style>
