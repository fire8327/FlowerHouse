<template>
    <footer class="grid-container py-6 mt-10">
        <div class="flex flex-col gap-4">
            <div class="flex items-center max-md:flex-col md:justify-between max-md:gap-8">
                <div class="flex flex-col gap-4">
                    <NuxtLink to="/">
                        <img src="/images/header/logo.png" alt="" class="w-36"> 
                    </NuxtLink>                    
                </div>
                <div class="flex items-start gap-4 xl:gap-8">
                    <div class="flex flex-col gap-4 text-lg">
                        <p class="text-[#569E0B]/70 font-Comfortaa font-semibold">Адрес</p>   
                        <p>Уфа, ул Пархоменко, 156г <br> пн—сб с 12:00 — 20:00</p>
                    </div>
                    <div class="flex flex-col gap-4 text-lg">
                        <p class="text-[#569E0B]/70 font-Comfortaa font-semibold">Контакты</p>   
                        <div class="flex items-center gap-4">
                            <NuxtLink to="/" class="transition-all duration-500 hover:text-[#569E0B]/70">
                                <Icon class="text-2xl" name="simple-icons:telegram"/>
                            </NuxtLink>
                            <NuxtLink to="/" class="transition-all duration-500 hover:text-[#569E0B]/70">
                                <Icon class="text-2xl" name="bi:whatsapp"/>
                            </NuxtLink>
                        </div>
                    </div>
                </div>
            </div>
            <div class="w-full h-0.5 bg-[#457453] rounded-full"></div>
            <p class="text-center text-base">© 2024 Flower House</p>
        </div>
    </footer>
</template>

<script setup>

</script>