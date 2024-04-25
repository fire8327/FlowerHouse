<template>
    <div class="flex items-center justify-center gap-6 max-lg:flex-col w-full">
        <img src="/images/cart/hero.webp" alt="" class="object-cover aspect-video lg:w-1/3 rounded-xl">
        <div class="flex flex-col gap-4 lg:w-1/3">
            <p class="text-2xl font-Comfortaa">Наименование товара</p>
            <p class="text-xl font-semibold">Цена ₽</p>      
            <div class="flex items-center justify-center gap-6 px-4 py-1.5 grow rounded-xl border border-[#665E5E]">
                <button class="text-2xl">-</button>
                <p>0</p>
                <button class="text-2xl">+</button>
            </div>    
            <button type="button" class="px-4 py-2 border border-[#569E0B] text-[#569E0B] rounded-full shrink-0 w-full">Удалить товар</button>
        </div>    
    </div>
</template>

<script setup>

</script>