<template>
    <div class="flex items-center justify-center gap-6 max-lg:flex-col w-full">
        <img :src="props.products.img" alt="" class="object-cover aspect-[7/10] lg:w-1/4 rounded-xl">
        <div class="flex flex-col gap-4 lg:w-1/3">
            <p class="text-2xl font-Comfortaa">{{ props.products.title }}</p>
            <p class="text-xl font-semibold">{{ props.products.price.toLocaleString() }} ₽</p>      
            <div class="flex items-center justify-center gap-6 px-4 py-1.5 w-[160px] rounded-xl border border-[#665E5E]">
                <button @click="plusCard" class="text-2xl">-</button>
                <p>{{ props.count }}</p>
                <button @click="minusCard" class="text-2xl">+</button>
            </div>    
            <button type="button" class="px-4 py-2 border border-[#569E0B] text-[#569E0B] rounded-full shrink-0 w-[160px]">Удалить товар</button>
        </div>    
    </div>
</template>

<script setup>
    /* props */
    const props = defineProps({
        id: Number,
        count: String,
        products: Object
    })

    /* управление количеством */
    const plusCard = () => {
        props.count++
    }
    const minusCard = () => {
        if (props.count > 1) {
            props.count--
        }
    }
</script>