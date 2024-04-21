<template>
    <header class="w-full py-4 grid-container border-b-2 border-[#457453] relative">
        <div class="flex items-center justify-between">
            <NuxtLink to="/">
                <img src="/images/header/logo.png" alt="" class="w-36"> 
            </NuxtLink>
            <nav class="flex items-center gap-8 text-xl bg-white max-lg:absolute max-lg:flex-col max-lg:w-full max-lg:py-8 max-lg:left-0 z-[4] duration-500 transition-all" :class="isMenuShow ? 'max-lg:top-[calc(100%+1.5px)]' : 'max-lg:top-0 max-lg:-translate-y-full'">
                <form class="relative">
                    <input type="text" class="w-64 rounded-full border border-[#569E0B]/70 py-0.5 pl-4 pr-10 focus:outline-none">
                    <button class="absolute top-1/2 -translate-y-1/2 right-2">
                        <Icon class="text-[28px] text-[#569E0B]/70" name="ic:baseline-search"/>
                    </button>
                </form>
                <NuxtLink to="/">Главная</NuxtLink>
                <NuxtLink to="/">Каталог</NuxtLink>
                <NuxtLink to="/">Услуги</NuxtLink>
                <NuxtLink to="/">Контакты</NuxtLink>
                <div class="flex items-center gap-4">
                    <NuxtLink to="/">
                        <Icon class="text-[28px] text-[#569E0B]/70" name="material-symbols:shopping-cart-rounded"/>
                    </NuxtLink>
                    <NuxtLink to="/">
                        <Icon class="text-[28px] text-[#569E0B]/70" name="material-symbols:account-circle"/>
                    </NuxtLink>
                </div>
            </nav>
            <div class="w-full inset-0 bg-black/70 fixed top-24 z-[3] transition-all duration-500 lg:hidden" :class="isMenuShow ? 'max-lg:top-32' : 'max-xl:top-0 max-xl:-translate-y-full'"></div>
            <button class="lg:hidden cursor-pointer" @click="isMenuShow = !isMenuShow">
                <Icon class="text-[28px] text-[#569E0B]/70" name="ph:list-bold"/>
            </button>
        </div>
    </header>
</template>

<script setup>
    /* открытие мобильного меню */
    const isMenuShow = ref(false) 
</script>