<template>
    <header class="w-full py-4 grid-container border-b-2 border-[#569E0B] relative">
        <div class="flex items-center justify-between">
            <NuxtLink to="/">
                <img src="/images/header/logo.png" alt="" class="w-36"> 
            </NuxtLink>
            <nav class="flex items-center gap-8 text-xl bg-white max-lg:absolute max-lg:flex-col max-lg:w-full max-lg:py-8 max-lg:left-0 z-[4] duration-500 transition-all" :class="isMenuShow ? 'max-lg:top-[calc(100%+1.5px)]' : 'max-lg:top-0 max-lg:-translate-y-full'">
                <NuxtLink to="/">Главная</NuxtLink>
                <NuxtLink to="/catalog">Каталог</NuxtLink>
                <NuxtLink to="/services">Услуги</NuxtLink>
                <NuxtLink to="/contacts">Контакты</NuxtLink>
                <NuxtLink to="/" v-if="role == 'admin'">Админ панель</NuxtLink>
                <div class="flex items-center gap-4">
                    <NuxtLink to="/" v-if="authenticated">
                        <Icon class="text-[28px] text-[#569E0B]/70" name="material-symbols:shopping-cart-rounded"/>
                    </NuxtLink>
                    <NuxtLink v-if="role == 'admin'" :to="authenticated ? '/admin' : '/auth'">
                        <Icon class="text-[28px] text-[#569E0B]/70" name="material-symbols:account-circle"/>
                    </NuxtLink>
                    <NuxtLink v-else :to="authenticated ? '/profile' : '/auth'">
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


    /* закрытие мобильного меню */
    const nuxtApp = useNuxtApp()
    nuxtApp.hook('page:start', () => {
        isMenuShow.value = false
    })
    

    /* проверка входа */
    const { authenticated, role } = storeToRefs(useUserStore())
</script>