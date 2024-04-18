<script setup>
import { ref } from "vue";
import navbar from "./components/navbar.vue";
import gallery from "./components/gallery.vue";
import cart from "./components/cart.vue";

const toggleCart = ref(false);

const addCart = ref("");

function handleData(data) {
  addCart.value = data;
}
</script>

<template>
  <header class="mb-6 relative">
    <div class="flex justify-between items-center">
      <div class="flex lg:flex-row-reverse items-center">
        <navbar />
        <img
          alt="logo"
          class="logo dark:bg-[var(--orange)] rounded p-1 ms-2 lg:ms-0 lg:me-2 cursor-pointer"
          src="/images/logo.svg"
        />
      </div>
      <div class="flex items-end">
        <div class="cart-button relative">
          <div
            v-if="addCart"
            class="absolute -right-2 text-xs -mt-2 bg-[var(--orange)] rounded-full h-4 w-5 font-bold text-center text-white"
          >
            {{ addCart }}
          </div>
          <button @click="toggleCart = !toggleCart">
            <img src="/images/icon-cart.svg" class="" alt="icon_cart" />
          </button>
        </div>
        <img
          src="/images/image-avatar.png"
          class="h-8 ms-6 rounded-full hover:ring-2 ring-[var(--orange)] cursor-pointer"
          alt="avatar"
        />
      </div>
    </div>
    <cart :quantity="addCart" v-if="toggleCart">
      <button @click="addCart = false">
        <img src="/images/icon-delete.svg" alt="icon_delete" />
      </button>
    </cart>
  </header>
  <div
    class="divider hidden lg:block h-px bg-[var(--color-border)] mb-6 lg:mb-20"
  ></div>

  <main>
    <div>
      <gallery @add-cart="handleData" />
    </div>
  </main>
</template>

<style scoped></style>
