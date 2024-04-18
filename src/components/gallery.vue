<script setup>
import { ref } from "vue";
import lightbox from "./lightbox.vue";
import cart from "./cart.vue";

const quantity = ref(0);
const addCart = ref(0);
const toggleCart = ref(false);

const emits = defineEmits(["addCart"]);

function addCartButton() {
  addCart.value = quantity.value;
  emits("addCart", addCart.value);
}
</script>

<template>
  <cart :quantity="addCart" v-if="toggleCart" />
  <div class="lg:flex lg:justify-center gap-28 lg:items-center">
    <lightbox />
    <div>
      <h1
        class="text-[var(--orange)] font-bold uppercase tracking-wide text-sm mb-2"
      >
        Sneaker Company
      </h1>
      <h2 class="text-2xl font-bold w-56 mb-3 lg:mb-6">
        Fall Limited Edition Sneakers
      </h2>
      <p class="text-[#a1a1a1] max-w-96 mb-5">
        These low-profile sneakers are your perfect casual wear companion.
        Featuring a durable rubber outer sole, they’ll withstand everything the
        weather can offer.
      </p>
      <div class="flex justify-between mb-6 lg:flex-col">
        <div class="flex items-center">
          <p class="text-2xl font-bold me-3">$125.00</p>
          <a class="bg-[#ff7d1a33] text-sm px-2 rounded-md">50%</a>
        </div>
        <del class="text-[#a1a1a1]">$250.00</del>
      </div>
      <div class="lg:flex lg:justify-between">
        <div
          class="quantity flex w-full h-12 lg:w-32 bg-[var(--color-background-mute)] rounded-md justify-between items-center mb-3"
        >
          <button @click="[quantity > 0 ? quantity-- : (quantity = 0)]">
            <svg width="12" height="4" class="m-5 fill-[var(--orange)] hover:fill-[var(--orange-dark)]" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M11.357 3.332A.641.641 0 0 0 12 2.69V.643A.641.641 0 0 0 11.357 0H.643A.641.641 0 0 0 0 .643v2.046c0 .357.287.643.643.643h10.714Z" id="a"/></defs><use fill-rule="nonzero" xlink:href="#a"/></svg>
          </button>
          <p class="light:text-black font-bold">{{ quantity }}</p>
          <button @click="quantity++">
            <svg width="12" height="12" class="m-5 fill-[var(--orange)] hover:fill-[var(--orange-dark)]" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M12 7.023V4.977a.641.641 0 0 0-.643-.643h-3.69V.643A.641.641 0 0 0 7.022 0H4.977a.641.641 0 0 0-.643.643v3.69H.643A.641.641 0 0 0 0 4.978v2.046c0 .356.287.643.643.643h3.69v3.691c0 .356.288.643.644.643h2.046a.641.641 0 0 0 .643-.643v-3.69h3.691A.641.641 0 0 0 12 7.022Z" id="b"/></defs><use fill-rule="nonzero" xlink:href="#b"/></svg>
          </button>
        </div>
        <button
          @click="addCartButton()"
          class="w-80 shadow-2xl lg:w-60 h-12 w-full flex justify-center items-center bg-[var(--orange)] text-white rounded-md hover:bg-[var(--orange-dark)]"
        >
          <p class="m-3 text-lg">
            <svg width="22" height="20" class="inline me-2 -mt-1 fill-white" xmlns="http://www.w3.org/2000/svg"><path d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z" fill-rule="nonzero"/></svg>
            Add to cart
          </p>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
