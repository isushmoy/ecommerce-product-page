<script setup>

const props = defineProps(['quantity']);

</script>

<template>
    <div class="flex justify-center content-center">
        <div class="absolute top-16 lg:top-12 lg:right-0 z-20 w-80 h-52 bg-[var(--color-background)] rounded-lg shadow-2xl">
            <div class="title p-4">
                <p class="font-bold">Cart</p>
            </div>
            <div class="divider h-px bg-[var(--color-border)]"></div>
            <div class="body text-[#a1a1a1] font-bold text-center p-5">
                <div v-if="props.quantity">
                    <div class="flex justify-between items-center">
                        <div>
                            <img src="/images/image-product-1-thumbnail.jpg" class="w-10 rounded" alt="product">
                        </div>
                        <div>
                            <h3 class="text-sm text-start">Fall Limited Edition Sneakers</h3>
                            <p class="text-sm text-start">$125.00 x <span>{{ props.quantity }} <strong class="text-black dark:text-white ms-1">${{ props.quantity * 125.00 }}.00</strong></span></p>
                        </div>
                        <div>
                            <slot>
                            </slot>
                        </div>
                    </div>
                    <button class="bg-[--orange] w-full h-12 mt-4 text-sm text-white rounded-lg hover:bg-[var(--orange-dark)]">Checkout</button>
                </div>
                <p class="mt-6" v-else>Your cart is empty</p>
            </div>
        </div>
    </div>
</template>

<style scoped></style>