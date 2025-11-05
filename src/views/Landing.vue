<script setup lang="ts">
import { useAuthStore } from "@/stores/auth";
import { useRouter } from "vue-router";

defineOptions({ name: "LandingPage" });

const authStore = useAuthStore();
const router = useRouter();
const go = (tenant: "owner" | "trainer" | "admin") => {
  authStore.tenant = tenant;
  router.push({ name: "sign-in-tenant", params: { tenant } });
};
</script>

<style scoped>
.cursor-pointer {
  cursor: pointer;
}
</style>

<template>
  <div class="container py-10">
    <div class="text-center mb-8">
      <h1 class="mb-2">Welcome</h1>
      <p class="text-muted">Choose your tenant to continue</p>
    </div>

    <div class="row g-6 justify-content-center">
      <div class="col-12 col-md-4">
        <div class="card h-100 cursor-pointer" @click="go('owner')">
          <div
            class="card-body d-flex flex-column align-items-center justify-content-center py-10"
          >
            <div class="fs-2 fw-bold mb-2">Owner</div>
            <div class="text-muted">Sign in as Owner</div>
          </div>
        </div>
      </div>
      <div class="col-12 col-md-4">
        <div class="card h-100 cursor-pointer" @click="go('trainer')">
          <div
            class="card-body d-flex flex-column align-items-center justify-content-center py-10"
          >
            <div class="fs-2 fw-bold mb-2">Trainer</div>
            <div class="text-muted">Sign in as Trainer</div>
          </div>
        </div>
      </div>
      <div class="col-12 col-md-4">
        <div class="card h-100 cursor-pointer" @click="go('admin')">
          <div
            class="card-body d-flex flex-column align-items-center justify-content-center py-10"
          >
            <div class="fs-2 fw-bold mb-2">Admin</div>
            <div class="text-muted">Sign in as Admin</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
