<script setup>
import { ref } from "vue";

let toggle = ref(false);

</script>

<template>
  <div class="flex">
    <button class="lg:hidden" @click="toggle = !toggle, openMenu()">
      <img src="/images/icon-menu.svg" alt="menu" />
    </button>
    <nav class="hidden lg:block ms-8">
      <a
        href="#"
        class="me-3 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent font-bold hover:border-b-4 border-[var(--orange)] pb-7"
        id="collection"
        >Collection</a
      >
      <a
        href="#"
        class="me-3 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent font-bold hover:border-b-4 border-[var(--orange)] pb-7"
        id="men"
        >Men</a
      >
      <a
        href="#"
        class="me-3 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent font-bold hover:border-b-4 border-[var(--orange)] pb-7"
        id="women"
        >Women</a
      >
      <a
        href="#"
        class="me-3 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent font-bold hover:border-b-4 border-[var(--orange)] pb-7"
        id="about"
        >About</a
      >
      <a
        href="#"
        class="me-3 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent font-bold hover:border-b-4 border-[var(--orange)] pb-7"
        id="contact"
        >Contact</a
      >
    </nav>
    <div v-if="toggle" class="fixed h-full w-full top-0 left-0 bg-[#00000090] z-30">
      <div class="bg-[var(--color-background)] w-60 h-full fixed top-0 left-0 transition">
        <button class="mt-10 ms-8 mb-12" @click="toggle = !toggle, closeMenu()">
          <svg width="14" height="15" xmlns="http://www.w3.org/2000/svg"><path d="m11.596.782 2.122 2.122L9.12 7.499l4.597 4.597-2.122 2.122L7 9.62l-4.595 4.597-2.122-2.122L4.878 7.5.282 2.904 2.404.782l4.595 4.596L11.596.782Z" fill="#69707D" class="hover:fill-[--orange]" fill-rule="evenodd"/></svg>          
        </button>
        <nav class="flex flex-col">
          <a
            href="#"
            class="mb-2 ms-8 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent hover:border-b w-fit font-bold border-[var(--orange)]"
            id="collection"
            >Collection</a
          >
          <a
            href="#"
            class="mb-2 ms-8 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent hover:border-b w-fit font-bold border-[var(--orange)]"
            id="men"
            >Men</a
          >
          <a
            href="#"
            class="mb-2 ms-8 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent hover:border-b w-fit font-bold border-[var(--orange)]"
            id="women"
            >Women</a
          >
          <a
            href="#"
            class="mb-2 ms-8 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent hover:border-b w-fit font-bold border-[var(--orange)]"
            id="about"
            >About</a
          >
          <a
            href="#"
            class="mb-2 ms-8 text-[#a1a1a1] hover:text-black dark:hover:text-white hover:bg-transparent hover:border-b w-fit font-bold border-[var(--orange)]"
            id="contact"
            >Contact</a
          >
        </nav>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
