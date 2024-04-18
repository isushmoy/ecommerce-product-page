<script setup>
import { ref } from "vue";

const pressed = ref(false);
const currentIndex = ref(0);

const product_src = [
  "/images/image-product-1.jpg",
  "/images/image-product-2.jpg",
  "/images/image-product-3.jpg",
  "/images/image-product-4.jpg",
];
const product_thumb_src = [
  "/images/image-product-1-thumbnail.jpg",
  "/images/image-product-2-thumbnail.jpg",
  "/images/image-product-3-thumbnail.jpg",
  "/images/image-product-4-thumbnail.jpg",
];

// default product
const defPro = ref(product_src[currentIndex.value]);
const defThumb = ref(product_thumb_src[currentIndex.value]);

// product change function
function changePro(index) {
  if(index < 0){
    index = 3;
  }
  currentIndex.value = index;
  defPro.value = product_src[currentIndex.value];
  defThumb.value = product_thumb_src[currentIndex.value];
}
</script>

<template>
  <div class="mb-5">
    <div class="relative">
      <button @click="pressed = !pressed">
        <button class="absolute left-3 top-1/2 -translate-y-1/2 rotate-180 lg:hidden opacity-70 hover:opacity-80" @click="changePro((currentIndex - 1) % product_src.length)">
          <div class="bg-white px-3 py-2.5 rounded-full">
            <img src="/public/images/icon-next.svg" class="w-2.5" alt="icon-next">
          </div>
        </button>
        <img :src="defPro" class="w-96 rounded-lg lg:rounded-xl lg:mb-6 cursor-auto lg:cursor-pointer" alt="product" />
        <button class="absolute right-3 top-1/2 -translate-y-1/2 lg:hidden opacity-70 hover:opacity-80" @click="changePro((currentIndex + 1) % product_src.length)">
          <div class="bg-white px-3 py-2.5 rounded-full">
            <img src="/images/icon-next.svg" class="w-2.5" alt="icon-next">
          </div>
        </button>
      </button>
    </div>
    <div class="thumbs hidden lg:block w-96 lg:flex lg:justify-between">
      <div v-for="(product, index) in product_thumb_src" :key="index">
        <button @click="changePro(index)">
          <img
            :src="product"
            class="w-20 rounded-xl hover:opacity-80"
            :class="[
              product == defThumb
                ? 'opacity-70 ring-2 ring-[var(--orange)]'
                : 'opacity-100',
            ]"
            :alt="'product-' + (index + 1) + '-thumb'"
          />
        </button>
      </div>
    </div>
  </div>
  <div v-if="pressed" class="hidden lg:block">
    <div
      class="fixed top-0 left-0 h-full w-full bg-[#00000090] !flex flex-col justify-center items-center"
    >
      <div class="w-[30rem] flex justify-end mb-4">
          <button @click="pressed = !pressed">

            <svg width="14" height="15" xmlns="http://www.w3.org/2000/svg"><path d="m11.596.782 2.122 2.122L9.12 7.499l4.597 4.597-2.122 2.122L7 9.62l-4.595 4.597-2.122-2.122L4.878 7.5.282 2.904 2.404.782l4.595 4.596L11.596.782Z" fill="#69707D" class="hover:fill-[--orange]" fill-rule="evenodd"/></svg>          
          </button>
      </div>
      <div>
        <button class="relative">
          <button class="absolute -ms-4 left-0 top-1/2 -translate-y-1/2 rotate-180 opacity-90 hover:opacity-100" @click="changePro((currentIndex - 1) % product_src.length)">
          <div class="bg-white px-3 py-2.5 rounded-full">
            <img src="/images/icon-next.svg" class="w-2.5" alt="icon-next">
          </div>
        </button>
          <img
            :src="defPro"
            class="w-[30rem] lg:rounded-xl mb-6"
            alt="product"
          />
          <button class="absolute -me-4 right-0 top-1/2 -translate-y-1/2 opacity-90 hover:opacity-100" @click="changePro((currentIndex + 1) % product_src.length)">
          <div class="bg-white px-3 py-2.5 rounded-full">
            <img src="/images/icon-next.svg" class="w-2.5" alt="icon-next">
          </div>
        </button>
        </button>
      </div>
      <div class="thumbs hidden lg:block w-96 lg:flex lg:justify-between">
        <div v-for="(product, index) in product_thumb_src" :key="index">
          <button @click="changePro(index)">
            <img
              :src="product"
              class="w-20 rounded-xl hover:opacity-80"
              :class="[
                product == defThumb
                  ? 'opacity-70 ring-2 ring-[var(--orange)]'
                  : 'opacity-100',
              ]"
              :alt="'product-' + (index + 1) + '-thumb'"
            />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
