<template>
    <Swiper :space-between="20" :loop="true" :modules="[SwiperAutoplay, SwiperPagination]" :autoplay="{delay: 3500}" :pagination="{clickable: true}" :slidesPerView="1" class="w-full col-span-full">
        <SwiperSlide class="relative !h-fit">
            <img src="/images/hero/1.webp" alt="" class="object-cover aspect-video max-md:aspect-[9/16]">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 py-10 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-2/3 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Очарование природы</p>
                    <p class="opacity-80 text-lg z-[1]">Приветствуют вас зеленые оазисы нашей гостиницы! Здесь каждое растение находит свой дом, обеспечивая комфорт и уют как для них, так и для наших гостей. Мы с гордостью поддерживаем экосистему, где каждое зеленое создание процветает благодаря заботе и вниманию. Наш дом становится их домом, а уход за растениями - нашим приоритетом, создавая гармонию и радость для всех, кто здесь останавливается.</p>
                    <NuxtLink to="/" class="z-[1] px-4 py-2 rounded-xl mx-auto bg-[#569E0B] hover:bg-[#665E5E] transition-all duration-500">Перейти в каталог</NuxtLink>
                </div>
            </div>
        </SwiperSlide>
        <SwiperSlide class="relative !h-fit">
            <img src="/images/hero/2.webp" alt="" class="object-cover aspect-video max-md:aspect-[9/16]">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 py-10 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-2/3 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Погружение в зеленые объятия</p>
                    <p class="opacity-80 text-lg z-[1]">В нашей гостинице для растений каждая зеленая душа находит свое идеальное место, где она может процветать в соответствии со своей природой. Наше внимание к деталям и забота о каждом растении позволяют им чувствовать себя как дома, а наши гости наслаждаются уютом и спокойствием этого зеленого уголка.</p>
                    <NuxtLink to="/" class="z-[1] px-4 py-2 rounded-xl mx-auto bg-[#569E0B] hover:bg-[#665E5E] transition-all duration-500">Перейти в каталог</NuxtLink>
                </div>
            </div>
        </SwiperSlide>
        <SwiperSlide class="relative !h-fit">
            <img src="/images/hero/3.webp" alt="" class="object-cover aspect-video max-md:aspect-[9/16]">
            <div class="absolute inset-0 bg-black/30"></div>
            <div class="absolute inset-0 py-10 px-4 flex justify-center items-center text-white">
                <div class="flex flex-col relative gap-6 w-full md:w-2/3 lg:w-1/3 p-4 lg:p-6 rounded-2xl overflow-hidden">
                    <div class="absolute inset-0 backdrop-blur-sm"></div>
                    <p class="text-2xl font-Comfortaa z-[1]">Создайте свой зеленый уголок</p>
                    <p class="opacity-80 text-lg z-[1]">Ваш дом для растений начинается здесь. От ярких, солнечных окон, наполняющих пространство светом, до тщательно подобранной системы полива, обеспечивающей растения влагой в нужном объеме. Каждое растение становится частью обширного экосистемы, придающей жизнь нашему дому и наполняющей его живым, дыханием природы.</p>
                    <NuxtLink to="/" class="z-[1] px-4 py-2 rounded-xl mx-auto bg-[#569E0B] hover:bg-[#665E5E] transition-all duration-500">Перейти в каталог</NuxtLink>
                </div>
            </div>
        </SwiperSlide>
    </Swiper>
    <div class="flex flex-col gap-6">
        <p class="text-3xl font-Comfortaa text-[#569E0B]/70">Наши преимущества</p>
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <div class="flex flex-col gap-6 rounded-xl shadow-[0px_0px_13px_-7px_black] p-4">
                <div class="flex items-center gap-4">
                    <p class="text-lg font-Comfortaa">Опытный персонал</p>
                    <Icon class="text-2xl text-[#569E0B]/70" name="icon-park-solid:personal-collection"/>
                </div>
                <p class="text-lg">Обеспечивает высокий уровень профессионализма и надежности в предоставлении услуг, что создает комфорт и уверенность у клиентов.</p>
            </div>
            <div class="flex flex-col gap-6 rounded-xl shadow-[0px_0px_13px_-7px_black] p-4">
                <div class="flex items-center gap-4">
                    <p class="text-lg font-Comfortaa">Качественные фотографии</p>
                    <Icon class="text-2xl text-[#569E0B]/70" name="material-symbols:image-outline"/>
                </div>
                <p class="text-lg">Сайт предоставляет качественные фотографии каждого растения, чтобы пользователи могли увидеть их во всей красе.</p>
            </div>
            <div class="flex flex-col gap-6 rounded-xl shadow-[0px_0px_13px_-7px_black] p-4">
                <div class="flex items-center gap-4">
                    <p class="text-lg font-Comfortaa">Экономия времени и заботы</p>
                    <Icon class="text-2xl text-[#569E0B]/70" name="material-symbols:alarm-on-outline-rounded"/>
                </div>
                <p class="text-lg">Предоставление растений в аренду включает в себя обслуживание и уход за ними, что освобождает арендатора от необходимости самостоятельно заботиться о растениях.</p>
            </div>
        </div>
    </div>    
</template>

<script setup>

</script>