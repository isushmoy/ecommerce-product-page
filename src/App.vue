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
      <div class="flex items-center">
        <div class="cart-button relative me-3">
          <div
            v-if="addCart"
            class="absolute -right-2 text-xs  bg-[var(--orange)] rounded-full h-4 w-5 font-bold text-center text-white"
          >
            {{ addCart }}
          </div>
          <button @click="toggleCart = !toggleCart" class="mt-2" >
            <svg width="22" height="20" class="fill-[#69707D] hover:fill-black dark:hover:fill-white" xmlns="http://www.w3.org/2000/svg"><path d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z" fill-rule="nonzero"/></svg>
          </button>
        </div>
        <img
          src="/images/image-avatar.png"
          class="h-10 ms-6 rounded-full hover:ring-2 ring-[var(--orange)] cursor-pointer"
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
