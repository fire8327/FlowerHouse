<template>
     <div class="flex flex-col gap-6">
        <div class="overflow-hidden rounded-xl">
            <img src="https://static.tildacdn.com/stor6135-3938-4736-b038-313639336661/93178138.jpg" alt="" class="transition-all duration-500 hover:scale-125">
        </div>
        <p class="text-2xl font-Comfortaa">Керамический горшок «Серый камень»</p>
        <p class="text-xl font-semibold">3 500₽</p>
        <div class="flex items-center gap-2 max-md:flex-col text-lg">
            <div class="flex items-center justify-center gap-6 px-4 py-1.5 grow rounded-xl border border-[#665E5E]">
                <button class="text-2xl" @click="minusCount">-</button>
                <p>{{ cardCount }}</p>
                <button class="text-2xl" @click="plusCount">+</button>
            </div>    
            <button class="md:w-3/5 px-4 py-2 text-center bg-[#569E0B] transition-all duration-500 hover:bg-[#665E5E] text-white rounded-xl">В корзину</button>
        </div>
    </div>
</template>

<script setup>
    /* управление количеством */
    const cardCount = ref(1)

    const plusCount = () => {
        cardCount.value++
    }
    const minusCount = () => {
        if (cardCount.value > 1) {
            cardCount.value--
        }
    }
</script>