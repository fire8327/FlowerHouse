<template>
    <div class="flex flex-col gap-4 w-full col-span-full">
        <div class="w-full relative md:h-[300px]">
            <img src="/images/contacts/hero.webp" alt="" class="object-cover h-full w-full">
            <div class="absolute inset-0 flex items-center justify-center z-[2]">
                <div class="relative w-fit p-6 overflow-hidden rounded-xl">
                    <p class="text-4xl text-white font-Comfortaa z-[1] relative">Контакты</p>
                    <div class="absolute inset-0 backdrop-blur-md"></div>
                </div>
            </div>
        </div>
        <div class="flex items-center gap-2 font-Comfortaa text-lg wrapper mx-auto w-full px-[15px] sm:px-5">
            <NuxtLink to="/" class="relative after:absolute after:w-0 after:h-px after:bg-[#665E5E] after:bottom-0 after:left-0 after:transition-all after:duration-500 hover:after:w-full">Главная</NuxtLink>
            <p>/</p>
            <p>Контакты</p>
        </div>
    </div>
    <div class="flex flex-col gap-6 text-xl">
        <p><span class="font-Comfortaa text-[#569E0B]/70">Часы работы:</span> пн—сб с 10:00 — 20:00</p>
        <div class="flex items-center gap-2">
            <p class="font-Comfortaa text-[#569E0B]/70">Мы в соцсетях:</p>
            <NuxtLink to="https://t.me/Gruzinochkaa" target="_blank" class="transition-all duration-500 hover:text-[#569E0B]/70">
                <Icon class="text-2xl" name="simple-icons:telegram"/>
            </NuxtLink>
            <NuxtLink to="/" target="_blank" class="transition-all duration-500 hover:text-[#569E0B]/70">
                <Icon class="text-2xl" name="bi:whatsapp"/>
            </NuxtLink>
        </div>
        <p><span class="font-Comfortaa text-[#569E0B]/70">Адрес:</span> Москва, ул Пушкина, д. 1</p>
        <iframe class="w-full h-[400px] rounded-xl" src="https://yandex.ru/map-widget/v1/?um=constructor%3Aca9938ebdc9acd66703b7f498d6b34e78c9910b76fcde25026bdbe728a855ad7&amp;source=constructor" frameborder="0"></iframe>
    </div>
    <div class="flex flex-col gap-6 items-center text-center">
        <p class="font-Comfortaa text-[#569E0B]/70 text-4xl">Доставка</p>
        <p class="md:w-2/3 lg:w-1/2 text-xl">
            Доставка осуществляется через сервис Яндекс такси.
            Вы вызываете курьера в любое удобное для вас время, мы упаковываем растение и передаем ему.
        </p>
    </div>
</template>

<script setup>

</script>